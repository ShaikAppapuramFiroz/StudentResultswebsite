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
      background: linear-gradient(135deg, #6e45e2, #88d3ce);
      height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }

    #splash-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: #6e45e2;
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-size: 24px;
      z-index: 1000;
      opacity: 1;
      transition: opacity 1s ease-in-out;
    }

    #splash-screen img {
      max-width: 150px;
      margin-bottom: 20px;
      border: 1px;
      box-shadow: 8px 8px 15px black;
    }

    #splash-screen.hide {
      opacity: 0;
      visibility: hidden;
    }

    .spt {
      color: white;
      text-shadow: 1px 1px 2px black, 0 0 25px blue, 0 0 5px darkblue;
    }

    .container {
      text-align: center;
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
      width: 90%;
      max-width: 650px;
      margin: 10px auto;
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 1s ease, transform 1s ease;
    }

    .container.show {
      opacity: 1;
      transform: translateY(0);
    }

    #header {
      background-color: #4b0082;
      color: #fff;
      text-align: center;
      padding: 15px;
      border-radius: 10px 10px 0 0;
    }

    h2 {
      color: #4b0082;
      margin-bottom: 20px;
    }

    form {
      margin-bottom: 20px;
    }

    label {
      margin-right: 10px;
      font-weight: bold;
      color: #333;
    }

    input {
      padding: 10px;
      border: 2px solid #ddd;
      border-radius: 5px;
      margin-bottom: 10px;
      width: calc(100% - 24px); /* Adjust input width for padding */
      max-width: 400px; /* Ensure a maximum width for large screens */
      box-sizing: border-box;
      transition: border-color 0.3s;
    }

    input:focus {
      border-color: #4b0082;
    }

    button {
      padding: 5px 10px; /* Smaller padding for a smaller button */
      font-size: 14px; /* Smaller font size */
      background-color: #4b0082;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s, transform 0.2s;
    }

    button:hover {
      background-color: #370067;
      transform: scale(1.05);
    }

    #result {
      margin-top: 20px;
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 1s ease, transform 1s ease;
    }

    #result.show {
      opacity: 1;
      transform: translateY(0);
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
      background-color: #f0f0f0;
      border-radius: 5px;
      overflow: hidden;
    }

    th, td {
      border: 1px solid #ddd;
      padding: 12px;
      text-align: left;
      font-size: 16px;
      color: #333;
    }

    th {
      background-color: #4b0082;
      color: #fff;
    }

    tr:nth-child(even) {
      background-color: #fafafa;
    }

    tr:hover {
      background-color: #ddd;
    }

    #logo {
      max-width: 100px;
      height: auto;
      margin-bottom: 20px;
    }

    #contactDetails {
      margin-top: 20px;
      text-align: left;
      color: #4b0082;
    }

    #contactDetails a {
      color: #4b0082;
      text-decoration: none;
    }

    #contactDetails a:hover {
      text-decoration: underline;
    }

    @media (max-width: 768px) {
      body {
        padding: 20px;
      }

      #splash-screen img {
        max-width: 120px;
      }

      .container {
        padding: 15px;
      }

      h2 {
        font-size: 18px;
      }

      button {
        width: 50%;
      }

      table th, table td {
        font-size: 14px;
        padding: 10px;
      }
    }
  </style>
</head>
<body>

  <div id="splash-screen">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/21/Nec.png.jpg/220px-Nec.png.jpg" alt="NEC College Logo">
    <div class="spt">Welcome to NEC College Results</div>
  </div>

  <div class="container show">
    <div id="header">
      <h1>NARASARAOPETA ENGINEERING COLLEGE (Autonomous)</h1>
      <p style="color:white;">Kotappakonda Rd, Narasaraopeta, Andhra Pradesh 522601</p>
    </div>
    
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/21/Nec.png.jpg/220px-Nec.png.jpg" alt="NEC College Logo" id="logo">
    <h2>NEC College - IT (III-I) Semester Results</h2>
    <form id="resultForm">
      <label for="rollNumber">Enter HT Number:</label>
      <input type="text" id="rollNumber" name="rollNumber" required>
      <button type="button" onclick="generateResults()">Get Results</button>
    </form>
    <div id="result"></div>
  </div>

  <script>
    window.onload = function() {
      setTimeout(function() {
        document.getElementById('splash-screen').classList.add('hide');
      }, 1500);
    };

    function generateResults() {
      var rollNumberInput = document.getElementById("rollNumber");
      var rollNumber = rollNumberInput.value.toUpperCase();

      if (!isValidRollNumber(rollNumber)) {
        alert("Invalid roll number format. Please enter a valid roll number within the range 22471A1201 - 22471A1270.");
        return;
      }

      var subjects = ["EITK", "OS", "DWDM", "ACD", "AWT", "DM", "AWT-LAB", "OS & CN-LAB", "ENGLISH EMPLOYABILITY SKILLS", "CSP-LAB"];
      var resultContainer = document.getElementById("result");

      resultContainer.innerHTML = "";

      var tableHTML = "<h3>Results for Roll Number " + rollNumber + "</h3>";
      tableHTML += "<table><tr><th>Subject</th><th>Grades</th><th>Points</th><th>Credits</th></tr>";

      for (var i = 0; i < subjects.length; i++) {
        var subjectResult = Math.floor(Math.random() * 11);
        var grade = calculateGrade(subjectResult);

        var credits = i === 0 ? 0 : subjectResult > 5 ? (i < 5 ? 3 : 1.5) : 0;

        tableHTML += "<tr>";
        tableHTML += "<td>" + subjects[i] + "</td>";
        tableHTML += "<td>" + grade + "</td>";
        tableHTML += "<td>" + subjectResult + " points</td>";
        tableHTML += "<td>" + credits + " credits</td>";
        tableHTML += "</tr>";
      }

      tableHTML += "</table>";
      resultContainer.innerHTML += tableHTML;
      resultContainer.classList.add('show');

      // Add GPA calculation button
      var gpaText = document.createElement('p');
      gpaText.textContent = "Wanna know your GPA?";

      var gpaButton = document.createElement('button');
      gpaButton.textContent = "Calculate GPA";
      gpaButton.onclick = function() {
        
         window.location.href = "https://badripraveen.blogspot.com/p/hi.html";
        };

      resultContainer.appendChild(gpaText);
      resultContainer.appendChild(gpaButton);

      // Move contact details below the result
      var contactContainer = document.createElement('div');
      contactContainer.id = 'contactDetails';
      contactContainer.innerHTML = `
        <h3>Contact Us</h3>
        <p>Email: <a href="mailto:appapuramfiroz@gmail.com">nrtec@gmail.com</a></p>
        <p>Phone: 7416546101</p>
      `;
      resultContainer.appendChild(contactContainer);
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

    function calculateGPA() {
      var table = document.querySelector("#result table");
      var rows = table.querySelectorAll("tr");
      var totalPoints = 0;
      var totalCredits = 0;

      for (var i = 1; i < rows.length; i++) {
        var cells = rows[i].querySelectorAll("td");
        var points = parseFloat(cells[2].textContent);
        var credits = parseFloat(cells[3].textContent);

        totalPoints += points * credits;
        totalCredits += credits;
      }

      var gpa = totalPoints / totalCredits;
      alert("Your GPA is: " + gpa.toFixed(2));
    }
  </script>
</body>
</html>
