# ONLINE-LEARNING-PLATFORM


MINI PROJECT REPORT

ON


 Online Learning Platform 



Submitted by
RAJA SANJAY CH
NC.SC.U4CSE25230




For
23CSE113-User Interface Design

II Semester B.Tech. CSE




School of Computing
Amrita Vishwa Vidyapeetham, Nagercoil
 
Index



Sl.
No.	Chapter Name	Page No.
1.	Introduction	
2.	Problem Statement	
3.	Objectives	
4.	System Design	
5.	Modules of project	
6.	Code	
7.	Output Screenshots	
8.	Application of the project	
9.	Limitations of the project	
10.	GitHub link of the project	






























1.	Introduction  

EduLearn is a simple educational platform developed using HTML, CSS, and JavaScript. This project aims to provide students with a basic online learning environment where they can access study materials, attempt quizzes, and view recorded classes.
The platform is designed with a user-friendly interface and focuses on demonstrating fundamental concepts of user interface design and web development.
The application runs entirely on the client side (front-end only) — no server or database is required. All features are implemented using core web technologies taught in the 23CSE113 User Interface Design course.

2.	Problem Statement

Many students face difficulty in accessing structured learning materials and practicing concepts in one place. Existing platforms are often complex or require login systems, backend servers, and internet connectivity.
This project solves the problem by creating a simple, lightweight educational platform that provides essential learning features without requiring any backend system or database. The entire application runs in a single HTML file.

3.	Objectives

The main objectives of this mini project are:
•	To design a simple and clean educational platform using HTML, CSS and JavaScript
•	To implement interactive UI navigation using JavaScript DOM manipulation
•	To provide learning resources such as e-books and recorded video lectures
•	To create a quiz and mock test system with instant result display
•	To implement a basic login system using JavaScript form validation
•	To demonstrate front-end web development concepts from the UID syllabus

4.	System Design

The system is designed using three core web technologies:
•	HTML5 – Used to create the structure and content of the platform (nav, sections, forms, video)
•	CSS3 – Used for styling, layout, colour scheme and hover effects
•	JavaScript – Used for all interactive behaviour — section switching, login validation, quiz checking

The application uses a single-page layout with multiple sections that are shown or hidden based on user navigation. The showSection() JavaScript function controls which section is visible at any time by manipulating the CSS display property through classList.

4.1	Architecture

The project follows a simple single-file front-end architecture:
•	One HTML file contains all structure, styles, and scripts
•	Navigation is handled by JavaScript event handlers (onclick)
•	Sections use CSS class toggling (active / display:none) to show/hide
•	No external libraries, frameworks, or backend systems are used










5. Modules of Project

Module	Description	Technology
Login Module	User authentication with username and password validation	HTML + JavaScript
E-Books Module	Displays list of study materials for students	HTML + CSS
Mock Test Module	MCQ test with radio buttons and submit evaluation	HTML + JavaScript
Quiz Module	Instant feedback quiz with button-based options	HTML + JavaScript
Classes Module	Embedded video player for recorded lectures	HTML5 Video

5.1 Login Module

The Login Module allows students to enter a username and password. JavaScript reads the input values using document.getElementById() and checks them against hardcoded credentials (username: student, password: 1234). A success or failure message is displayed in a paragraph element using innerHTML.

5.2 E-Books Module

The E-Books Module displays a list of available study materials as styled card elements. Each card represents a resource such as a PDF or reference book. The cards are styled using CSS with box-shadow and border-radius for a clean look.

5.3 Mock Test Module

The Mock Test Module presents a multiple-choice question using HTML radio buttons. When the student clicks Submit, the checkMock() JavaScript function checks if the correct radio button is selected and displays the result message accordingly.

5.4 Quiz Module

The Quiz Module provides a quick quiz with three button options. Each button calls the quizAnswer() JavaScript function with a true or false argument. The function immediately shows Correct or Wrong Answer in the result paragraph using DOM manipulation.

5.5 Classes Module

The Classes Module uses the HTML5 <video> element with the controls attribute to display embedded video lectures. Each class card contains a video player and a title. Video source files can be linked using the src attribute of the <source> tag.

 
6.	Code

The complete source code of the project is given below. The entire application is built in a single HTML file.

  index.html
<!DOCTYPE html>
<html>
<head>
<title>EduLearn Platform</title>
<style>
body { font-family: Arial; margin: 0; background: whitesmoke; }
header { background: darkslategray; color: white; padding: 15px; text-align: center; }
nav { background: slategray; padding: 10px; text-align: center; }
nav button {
 

 padding: 10px 20px; margin: 5px; border: none;
  background: dodgerblue; color: white; cursor: pointer;
}
nav button:hover { background: steelblue; }
.section { display: none; padding: 20px; }
.active  { display: block; }
.card {
  background: white; padding: 20px; margin: 15px;
  border-radius: 8px; box-shadow: 0 0 10px lightgray;
}
input { padding: 8px; margin: 5px; }
button { padding: 10px; }
.quiz-option { display: block; margin: 5px 0; }
</style>
</head>
<body>
<header>
  <h1>EduLearn - Online Learning Platform</h1>
</header>
<nav>
  <button onclick="showSection('login')">Login</button>
  <button onclick="showSection('ebooks')">E-Books</button>
  <button onclick="showSection('mocktest')">Mock Test</button>
  <button onclick="showSection('quiz')">Quiz</button>
  <button onclick="showSection('classes')">Classes</button>
</nav>

<!-- LOGIN -->
<div id="login" class="section active">
  <div class="card">
    <h2>Student Login</h2>
    <input type="text" id="username" placeholder="Username"><br>
    <input type="password" id="password" placeholder="Password"><br>
    <button onclick="login()">Login</button>
    <p id="loginMsg"></p>
  </div>
</div>

<!-- EBOOKS -->
<div id="ebooks" class="section">
  <h2>Available E-Books</h2>
  <div class="card">Physics Fundamentals PDF</div>
  <div class="card">Java Programming Basics</div>
  <div class="card">Mathematics for Engineers</div>
</div>

<!-- MOCK TEST -->
<div id="mocktest" class="section">
  <h2>Mock Test</h2>
  <div class="card">
    <p>1. Java is a ______ language.</p>
    <input type="radio" name="q1">Low level<br>
    <input type="radio" name="q1" id="correct">Object Oriented<br>
    <input type="radio" name="q1">Machine language<br><br>
    <button onclick="checkMock()">Submit</button>
    <p id="mockResult"></p>
  </div>
</div>




<!-- QUIZ -->
<div id="quiz" class="section">
  <h2>Quick Quiz</h2>
  <div class="card">
    <p>HTML stands for?</p>
    <button class="quiz-option" onclick="quizAnswer(false)">
      Hyper Trainer Marking Language</button>
    <button class="quiz-option" onclick="quizAnswer(true)">
      Hyper Text Markup Language</button>
    <button class="quiz-option" onclick="quizAnswer(false)">
      Hyper Text Marketing Language</button>
    <p id="quizResult"></p>
  </div>
</div>

<!-- CLASSES -->
<div id="classes" class="section">
  <h2>Recorded Classes</h2>
  <div class="card">
    <p>Java OOP Concepts</p>
    <video width="300" controls>
      <source src="" type="video/mp4">
    </video>
  </div>
  <div class="card">
    <p>Modern Physics Lecture</p>
    <video width="300" controls>
      <source src="" type="video/mp4">
    </video>
  </div>
</div>

<script>
function showSection(id) {
  var sections = document.querySelectorAll(".section");
  sections.forEach(sec => { sec.classList.remove("active"); });
  document.getElementById(id).classList.add("active");
}
function login() {
  var user = document.getElementById("username").value;
  var pass = document.getElementById("password").value;
  if (user == "student" && pass == "1234") {
    document.getElementById("loginMsg").innerHTML = "Login Successful";
  } else {
    document.getElementById("loginMsg").innerHTML = "Invalid Login";
  }
}
function checkMock() {
  var correct = document.getElementById("correct");
  if (correct.checked) {
    document.getElementById("mockResult").innerHTML = "Correct Answer!";
  } else {
    document.getElementById("mockResult").innerHTML = "Wrong Answer";
  }
}
function quizAnswer(ans) {
  if (ans) {
 
   document.getElementById("quizResult").innerHTML = "Correct!";
  } else {
    document.getElementById("quizResult").innerHTML = "Wrong Answer!";
  }
}
</script>
</body>
</html>
 
7.	Output Screenshots

The following screenshots show the working output of each module in the EduLearn platform.

•	Screenshot 1: Login Page – Input fields for username and password with Login button
•	Screenshot 2: Login Success – Message displayed as 'Login Successful' after correct credentials
•	Screenshot 3: E-Books Section – List of study material cards displayed
•	Screenshot 4: Mock Test Section – Radio button MCQ with Submit and result message
•	Screenshot 5: Quiz Section – Three button options with instant correct/wrong feedback
•	Screenshot 6: Classes Section – Video player cards for recorded lectures

[ Add your screenshots here ]

8.	Application of the Project

EduLearn can be applied and extended in the following real-world scenarios:
•	Useful for school and college students to access basic learning materials in one place
•	Can be used as a prototype for a full-scale educational platform with backend integration
•	Helps beginners understand front-end web development concepts
•	Can be extended to include more subjects, more questions, and real video content
•	Useful as a demonstration project for UI/UX design principles
•	Can be hosted on GitHub Pages for free public access

9.	Limitations of the Project

The following limitations exist in the current version of EduLearn:
•	No database integration — user data and scores are not stored permanently
•	Static login credentials — hardcoded in JavaScript, not secure for real use
•	Limited number of quiz and mock test questions
•	No real-time user tracking or progress monitoring
•	Video files are not included — only placeholder source tags are used
•	No responsive design — layout is not optimised for mobile devices
•	No back-end — cannot support multiple users or user accounts




--- End of Mini Project Report ---
