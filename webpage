<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CGPA Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #cca1e77e;
            margin: 0;
            padding: 20px;
        }
        h1 {
            color: #333333;
            text-align: center;
            margin-bottom: 20px;
        }
        h2 {
            color: #444;
            margin-bottom: 15px;
            text-align: center;
        }
        .logo-container {
            position: absolute;
            top: 10px;
            right: 10px;
            z-index: 1000; 
        }
        .logo-container img {
            width: 500px;  /
            height: auto; ;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        .dropdown-container {
            text-align: center;
            margin-bottom: 30px;
        }
        .semester {
            margin-bottom: 40px;
        }
        .subject-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            margin-bottom: 20px;
        }
        .subject-item {
            flex: 1 1 30%;
            margin: 10px;
            text-align: left;
            min-width: 250px;
        }
        select, button {
            padding: 10px;
            font-size: 16px;
            margin: 10px 0;
            border: 1px solid #000000;
            border-radius: 4px;
            width: 100%;
            box-sizing: border-box;
        }
        button {
            background-color: #28a75f;
            color: white;
            cursor: pointer;
            width: 100%;
        }
        button:hover {
            background-color: #218838;
        }
        #result {
            margin-top: 20px;
            font-size: 24px;
            font-weight: bold;
            text-align: center;
        }
    </style>
    <script>
        const semesters = [
            {
                name: "Semester 1",
                subjects: [
                    { name: "Communicative English", credit: 3 },
                    { name: "Engineering Chemistry", credit: 3 },
                    { name: "Matrices and Calculus", credit: 4 },
                    { name: "Engineering Physics", credit: 3 },
                    { name: "Problem Solving and Python Programming", credit: 3 },
                    { name: "Heritage of Tamils", credit: 1 },
                    { name: "Physics and Chemistry Laboratory", credit: 2 },
                    { name: "Problem Solving and Python Programming Laboratory", credit: 2 },
                    { name: "Communicative English Laboratory", credit: 1 }
                ]
            },
            {
                name: "Semester 2",
                subjects: [
                    { name: "Technical English", credit: 3 },
                    { name: "Statistics and Numerical Methods", credit: 4 },
                    { name: "Physics for Computer Science Engineers", credit: 3 },
                    { name: "Engineering Graphics", credit: 4 },
                    { name: "Programming in C", credit: 3 },
                    { name: "Tamils and Technology", credit: 1 },
                    { name: "Environmental Sciences and Sustainability", credit: 2 },
                    { name: "Technical English Laboratory", credit: 1 },
                    { name: "Programming in C Laboratory", credit: 2},
                    { name: "Engineering Practices Laboratory", credit: 2}
                ]
            },
            {
                name: "Semester 3",
                subjects: [
                    { name: "Digital Principals and Computer Organization", credit: 4 },
                    { name: "Foundations of Data Science", credit: 3},
                    { name: "Data Structures", credit: 3 },
                    { name: "Object Oriented Programming", credit: 3 },
                    { name: "Operating Systems", credit: 4 },
                    { name: "Data Structures Laboratory", credit: 2 },
                    { name: "Object Oriented Programming Laboratory", credit: 2 },
                    { name: "Data Science Laboratory", credit: 2 },
                    { name: "Quantitative Aptitude & Verbal Reasoning",credit:1}
                ]
            },
            {
                name: "Semester 4",
                subjects: [
                    { name: "Software Engineering", credit: 3 },
                    { name: "Design and Analysis of Algorithms", credit: 4},
                    { name: "Discrete Mathematics", credit: 4 },
                    { name: "Database Management Systems", credit: 3},
                    { name: "Java Programming", credit: 3 },
                    { name: "Database Management Systems Laboratory", credit: 2},
                    { name: "Java Programming Laboratory", credit: 2 },
                    { name: "Quantitative Aptitude & Behavioral Skills", credit: 1}
                ]
            },
            {
                name: "Semester 5",
                subjects: [
                    { name: "Compiler Design", credit: 4 },
                    { name: "Open Elective-I", credit: 3},
                    { name: "Computer Networks", credit: 4 },
                    { name: "Full Stack Programming", credit: 4 },
                    { name: "Professional Elective-I", credit: 3 },
                    { name: "Professional Elective-II", credit: 3 },
                    { name: "Quantitative Aptitude & Verbal Reasoning",credit:1}
                ]
            },
            {
                name: "Semester 6",
                subjects: [
                    { name: "Mobile Computing", credit: 3 },
                    { name: "Open Elective-II", credit: 3},
                    { name: "Cryptography and Cyber Security", credit: 4 },
                    { name: "Artificial Intelligence and Machine Learning", credit: 4 },
                    { name: "Professional Elective-III", credit: 3 },
                    { name: "Mobile Applications Development Lab", credit: 2 },
                    { name: "Quantitative Aptitude & Soft Skills",credit:1},
                    { name: "Mini Project", credit: 2}
                ]
            },
            {
                name: "Semester 7",
                subjects: [
                    { name: "Human Values and Ethics", credit: 2 },
                    { name: "Elective-Management", credit: 3},
                    { name: "Open Elective-III", credit: 3 },
                    { name: "Professional Elective-V", credit: 3 },
                    { name: "Professional Elective-VI", credit: 3 },
                    { name: "Internship",credit:1}
                ]
            },
            { 
                name: "Semester 8",
                subjects: [
                    { name: "Project Work", credit: 10 }
                ]
            },
        ];

        function populateSemesterOptions() {
            const semesterSelect = document.getElementById("semester-select");
            for (let i = 1; i <= semesters.length; i++) {
                let option = document.createElement("option");
                option.value = i;
                option.textContent = i + (i === 1 ? " Semester" : " Semesters");
                semesterSelect.appendChild(option);
            }
        }

        function displaySelectedSemesters() {
            const selectedSemesters = parseInt(document.getElementById("semester-select").value);
            const container = document.getElementById("semesters-container");
            container.innerHTML ="";

            for (let i = 0; i < selectedSemesters; i++) {
                let semesterDiv = document.createElement("div");
                semesterDiv.className = "semester";
                semesterDiv.innerHTML = `<h2>${semesters[i].name}</h2>`;

                let subjectGrid = document.createElement("div");
                subjectGrid.className = "subject-grid";

                semesters[i].subjects.forEach(subject => {
                    let subjectItem = document.createElement("div");
                    subjectItem.className = "subject-item";
                    subjectItem.innerHTML = `
                        <strong>${subject.name}</strong>
                        <select class="grade-select" data-semester-index="${i}">
                            <option value="">--Select Grade--</option>
                            <option value="10">O</option>
                            <option value="9">A+</option>
                            <option value="8">A</option>
                            <option value="7">B+</option>
                            <option value="6">B</option>
                            <option value="5">C</option>
                            <option value="0">F</option>
                        </select>
                    `;
                    subjectGrid.appendChild(subjectItem);
                });

                semesterDiv.appendChild(subjectGrid);
                container.appendChild(semesterDiv);
            }

            document.getElementById("calculate-button").style.display = "block";
        }

        function calculateOverallCGPA() {
        let totalGradePoints = 0;
        let totalCredits = 0;
        let hasFailed = false;

        const gradeSelects = document.querySelectorAll(".grade-select");

        gradeSelects.forEach(select => {
        const grade = parseFloat(select.value);
        const semesterIndex = parseInt(select.getAttribute("data-semester-index"));
        const subjectIndex = Array.from(select.parentElement.parentElement.children).indexOf(select.parentElement);
        const credit = semesters[semesterIndex].subjects[subjectIndex].credit;

        if (grade === 0) {
            hasFailed = true;  // Mark that there is a fail
        }

        if (!isNaN(grade)) {
            totalGradePoints += grade * credit;
            totalCredits += credit;
        }
        });

        if (hasFailed) {
        document.getElementById("result").textContent = "You have a failing grade. Your overall CGPA is: 0";
         } else if (totalCredits > 0) {
        let cgpa = (totalGradePoints / totalCredits).toFixed(2);
        document.getElementById("result").textContent = "Your overall CGPA is: " + cgpa;
        } else {
        document.getElementById("result").textContent = "Please enter grades.";
        }
}

        window.onload = () => {
            populateSemesterOptions();
            document.getElementById("semester-select").addEventListener("change", displaySelectedSemesters);
        };
    </script>
</head>
<body>
    <div class="container">
        <h1>Let's Calculate your CGPA</h1>
        <h2>by Pixel Pioneers of CSE-D</h2>
        <div class="logo-container">
            <img src="C:\Users\Poujitha\OneDrive\Pictures\The Backgrounds\Velammal_header.png" alt="Company Logo">
        </div>
        <div class="dropdown-container">
            <label for="semester-select">Select Number of Semesters:</label>
            <select id="semester-select">
                <option value="">--Select--</option>
            </select>
        </div>
        <div id="semesters-container"></div>
        <button id="calculate-button" style="display: none;" onclick="calculateOverallCGPA()">Calculate Overall CGPA</button>
        <p id="result"></p>
    </div>
</body>
</html>
