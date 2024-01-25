


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>NEC College - Subject Results</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      padding: 0;
      background-color:skyblue;
    }

    #header {
      background-color:darkviolet;
      color: #fff;
      text-align: center;
      padding: 10px;
    }

    .container {
      text-align: center;
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
      width: 80%;
      max-width: 600px;
      margin: 20px auto;
    }

    h2 {
      color: #007BFF;
    }

    form {
      margin-bottom: 20px;
    }

    label {
      margin-right: 10px;
    }

    input {
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 5px;
      margin-bottom: 10px;
      width: 60%;
    }

    button {
      padding: 10px 15px;
      background-color: #007BFF;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background-color: #0056b3;
    }

    #result {
      margin-top: 20px;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
      border: 2px solid #007BFF;
      background-color: #87CEEB;
    }

    th, td {
      border: 2px solid #007BFF;
      padding: 8px;
      text-align: left;
      font-size: 14px;
      background-color: #87CEEB;
    }

    th {
      background-color: #007BFF;
      color: #fff;
    }

    tr:nth-child(even) {
      background-color: #f9f9f9;
    }

    tr:nth-child(odd) {
      background-color: #e6e6e6;
    }

    tr:hover {
      background-color: #d4d4d4;
    }

    #logo {
      max-width: 100%;
      height: auto;
      margin-bottom: 20px;
    }
  </style>
</head>
<body>

  <div id="header">
    <h1>NARASARAOPETA ENGINEERING COLLEGE (Autonomous)</h1>
    <p style="color:white;">Kotappakonda Rd, Narasaraopeta, Andhra Pradesh 522601
</p>
  </div>
  

  <div class="container">
    <img src="C:\Users\Administrator\Downloads\Nec.png.jpg" alt="NEC College Logo" id="logo">
    <h2>NEC College - IT Results(2-1) Semister</h2>
    <form id="resultForm">
      <label for="rollNumber">Enter HT Number :</label>
      <input type="text" id="rollNumber" name="rollNumber" required>
      <button type="button" onclick="generateResults()">Get Results</button>
    </form>
    <div id="result"></div>
  </div>

  <script>
    function generateResults() {
      var rollNumberInput = document.getElementById("rollNumber");
      var rollNumber = rollNumberInput.value.toUpperCase();

      if (!isValidRollNumber(rollNumber)) {
        alert("Invalid roll number format. Please enter a valid roll number within the range 22471A1201 - 22471A1270.");
        return;
      }

      var subjects = ["COI", "JAVA", "DATA STRUCTURES", "FEWT", "CO", "MFCS", "DS-LAB", "DATA STRUCTURE-LAB", "JAVALAB", "FEWT-LAB"];
      var resultContainer = document.getElementById("result");

      resultContainer.innerHTML = "";

      var tableHTML = "<h3>Results for Roll Number " + rollNumber + "</h3>";
      tableHTML += "<table><tr><th>Subject</th><th>Grades</th><th>Points</th><th>Credits</th></tr>";

      for (var i = 0; i < subjects.length; i++) {
        var subjectResult = Math.floor(Math.random() * 11);
        var grade = calculateGrade(subjectResult);

        var credits = i === 0 ? 0 : subjectResult > 5 ? (i < 5 ? 3 : 1.5) : 0;

        var bgColor = i % 2 === 0 ? '#e6e6e6' : '#f9f9f9';

        tableHTML += "<tr style='background-color:" + bgColor + "'>";
        tableHTML += "<td>" + subjects[i] + "</td>";
        tableHTML += "<td>" + grade + "</td>";
        tableHTML += "<td>" + subjectResult + " points</td>";
        tableHTML += "<td>" + credits + " credits</td>";
        tableHTML += "</tr>";
      }

      tableHTML += "</table>";
      resultContainer.innerHTML += tableHTML;
    }

    function isValidRollNumber(rollNumber) {
      var rollNumberPattern = /^22471A12(0[1-9]|[1-6]\d|70)$/;
      return rollNumberPattern.test(rollNumber);
    }

    function calculateGrade(points) {
      if (points === 10) return 'A+';
      else if (points === 9) return 'A';
      else if (points === 8) return 'B';
      else if (points === 7) return 'C';
      else if (points === 6) return 'D';
      else if (points === 5) return 'D';
      else return 'F';
    }
  </script>
</body>
  <div class="container">
    <h1> Contact US </h1> <!-- Existing content -->

    <!-- Contact details -->
    <p style="color:green"> For More queries </p>
    <div id="contactDetails">
      <p>Email: <a href="mailto:yalamandap6@gmail.com">nrtec@gmail.com</a></p>
      <p>Phone: 6301932724</p>
    </div>
  </div>
</html>
