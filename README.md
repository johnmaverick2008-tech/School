<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Automated Web Monitoring System</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f6f9;
      margin: 0;
      padding: 0;
    }
    header {
      background: #2c3e50;
      color: white;
      padding: 20px;
      text-align: center;
    }
    .container {
      width: 90%;
      margin: 20px auto;
    }
    .controls {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 15px;
      align-items: center;
    }
    .controls input, .controls select {
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .btn {
      background: #27ae60;
      color: white;
      border: none;
      padding: 10px 15px;
      cursor: pointer;
      border-radius: 5px;
    }
    .btn:hover {
      background: #2ecc71;
    }
    .log-box {
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0px 2px 5px rgba(0,0,0,0.1);
      margin-bottom: 25px;
    }
    h2 {
      background: #34495e;
      color: white;
      padding: 10px;
      border-radius: 5px;
      font-size: 18px;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 10px;
    }
    th, td {
      padding: 12px;
      border-bottom: 1px solid #ddd;
      text-align: left;
    }
    th {
      background: #2c3e50;
      color: white;
    }
    tr:hover {
      background: #f1f1f1;
    }
  </style>
</head>
<body>
  <header>
    <h1>Automated Web Monitoring System</h1>
    <p>Barretto Senior High School | S.Y. 2025–2026</p>
  </header>

  <div class="container">
    <!-- Input Controls -->
    <div class="controls">
      <input type="text" id="studentName" placeholder="Enter Student Name">
      <select id="gradeLevel">
        <option value="">Select Grade</option>
        <option value="Grade 11">Grade 11</option>
        <option value="Grade 12">Grade 12</option>
      </select>
      <select id="strand">
        <option value="">Select Strand</option>
        <option value="TVL - ICT">TVL - ICT</option>
        <option value="TVL - HE">TVL - HE</option>
        <option value="ABM">ABM</option>
        <option value="HUMSS - A">HUMSS - A</option>
        <option value="HUMSS - B">HUMSS - B</option>
        <option value="HUMSS - C">HUMSS - C</option>
        <option value="Tech Pro 11 - A">Tech Pro 11 - A</option>
        <option value="Tech Pro 11 - B">Tech Pro 11 - B</option>
        <option value="Acad - A">Acad - A</option>
        <option value="Acad - B">Acad - B</option>
        <option value="Acad - C">Acad - C</option>
      </select>
      <input type="text" id="signature" placeholder="Signature">
      <button class="btn" onclick="addLog()">SUBMIT LOG</button>
    </div>

    <!-- Section for logs -->
    <div id="logsContainer"></div>
  </div>

  <script>
    function addLog() {
      const studentName = document.getElementById("studentName").value || "Unknown";
      const gradeLevel = document.getElementById("gradeLevel").value || "N/A";
      const strand = document.getElementById("strand").value || "N/A";
      const signature = document.getElementById("signature").value || "N/A";
      const now = new Date();

      if (strand === "N/A") {
        alert("Please select a strand!");
        return;
      }

      const logsContainer = document.getElementById("logsContainer");
      let strandSection = document.getElementById("section-" + strand.replace(/\s+/g, '-'));

      // If no section exists for this strand, create one
      if (!strandSection) {
        strandSection = document.createElement("div");
        strandSection.classList.add("log-box");
        strandSection.id = "section-" + strand.replace(/\s+/g, '-');
        strandSection.innerHTML = `
          <h2>${strand}</h2>
          <table>
            <tr>
              <th>Date & Time</th>
              <th>Student</th>
              <th>Grade</th>
              <th>Strand</th>
              <th>Signature</th>
            </tr>
          </table>
        `;
        logsContainer.appendChild(strandSection);
      }

      // Add row to this strand's table
      const table = strandSection.querySelector("table");
      const row = table.insertRow(-1);
      row.insertCell(0).innerText = now.toLocaleString();
      row.insertCell(1).innerText = studentName;
      row.insertCell(2).innerText = gradeLevel;
      row.insertCell(3).innerText = strand;
      row.insertCell(4).innerText = signature;

      // Clear inputs
      document.getElementById("studentName").value = "";
      document.getElementById("gradeLevel").value = "";
      document.getElementById("strand").value = "";
      document.getElementById("signature").value = "";
    }
  </script>
</body>
</html>
