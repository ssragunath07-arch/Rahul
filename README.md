<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gradient Animated Portfolio</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Poppins',sans-serif;
}

body{
  color:white;
  overflow-x:hidden;
}

/* 🌈 Animated Gradient Background */
body::before{
  content:"";
  position:fixed;
  top:0;
  left:0;
  width:100%;
  height:100%;
  background:linear-gradient(-45deg,#ff0066,#3a86ff,#8338ec,#06d6a0);
  background-size:400% 400%;
  animation:gradientMove 10s ease infinite;
  z-index:-1;
}

@keyframes gradientMove{
  0%{background-position:0% 50%;}
  50%{background-position:100% 50%;}
  100%{background-position:0% 50%;}
}

/* Navbar */
nav{
  display:flex;
  justify-content:space-between;
  align-items:center;
  padding:20px 10%;
  backdrop-filter:blur(10px);
  background:rgba(0,0,0,0.2);
  position:fixed;
  width:100%;
  top:0;
}

nav h2{
  font-weight:700;
}

nav ul{
  list-style:none;
  display:flex;
}

nav ul li{
  margin-left:25px;
}

nav ul li a{
  text-decoration:none;
  color:white;
  transition:0.3s;
}

nav ul li a:hover{
  color:#00f7ff;
}

/* Hero Section */
.hero{
  height:100vh;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  text-align:center;
  padding:0 20px;
}

.hero h1{
  font-size:3rem;
}

.hero span{
  color:#00f7ff;
}

.hero p{
  margin:15px 0;
  font-size:1.2rem;
}

.btn{
  padding:12px 30px;
  border:none;
  border-radius:30px;
  cursor:pointer;
  background:white;
  color:#333;
  font-weight:600;
  transition:0.3s;
}

.btn:hover{
  background:#00f7ff;
  transform:scale(1.05);
}

/* Sections */
section{
  padding:100px 10%;
}

.glass{
  background:rgba(255,255,255,0.1);
  backdrop-filter:blur(15px);
  border-radius:20px;
  padding:40px;
  margin:20px 0;
  transition:0.4s;
}

.glass:hover{
  transform:translateY(-10px);
}

/* Projects */
.projects{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
  gap:20px;
}

/* Footer */
footer{
  text-align:center;
  padding:20px;
  background:rgba(0,0,0,0.3);
  margin-top:50px;
}

/* Responsive */
@media(max-width:768px){
  nav ul{
    display:none;
  }
  .hero h1{
    font-size:2rem;
  }
}
</style>
</head>
<body>

<nav>
  <h2>MyPortfolio</h2>
  <ul>
    <li><a href="#about">About</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<section class="hero">
  <h1>Hello, I'm <span id="typing"></span></h1>
  <p>Creative Developer • UI Designer • Freelancer</p>
  <button class="btn" onclick="scrollToSection('projects')">View Work</button>
</section>

<section id="about">
  <div class="glass">
    <h2>About Me</h2>
    <p>I build modern, responsive, and visually stunning websites using HTML, CSS, and JavaScript. I love smooth animations and interactive UI design.</p>
  </div>
</section>

<section id="projects">
  <h2 style="text-align:center;margin-bottom:30px;">Projects</h2>
  <div class="projects">
    <div class="glass">
      <h3>Project One</h3>
      <p>Animated Landing Page</p>
    </div>
    <div class="glass">
      <h3>Project Two</h3>
      <p>Interactive Web App</p>
    </div>
    <div class="glass">
      <h3>Project Three</h3>
      <p>Creative UI Design</p>
    </div>
  </div>
</section>

<section id="contact">
  <div class="glass">
    <h2>Contact Me</h2>
    <input type="text" placeholder="Your Name" style="width:100%;padding:10px;margin:10px 0;border-radius:8px;border:none;">
    <input type="email" placeholder="Your Email" style="width:100%;padding:10px;margin:10px 0;border-radius:8px;border:none;">
    <textarea rows="4" placeholder="Message" style="width:100%;padding:10px;margin:10px 0;border-radius:8px;border:none;"></textarea>
    <button class="btn">Send Message</button>
  </div>
</section>

<footer>
  © 2026 Gradient Portfolio | Designed with ❤️
</footer>

<script>
// Typing Animation
const words = ["John Doe","Web Developer","Creative Designer"];
let i = 0, j = 0, currentWord = "", isDeleting = false;

function typeEffect(){
  currentWord = words[i];
  if(!isDeleting){
    document.getElementById("typing").textContent = currentWord.substring(0,j++);
    if(j > currentWord.length){
      isDeleting = true;
      setTimeout(typeEffect,1000);
      return;
    }
  } else {
    document.getElementById("typing").textContent = currentWord.substring(0,j--);
    if(j < 0){
      isDeleting = false;
      i = (i+1)%words.length;
    }
  }
  setTimeout(typeEffect,100);
}

typeEffect();

function scrollToSection(id){
  document.getElementById(id).scrollIntoView({behavior:"smooth"});
}
</script>

</body>
</html>
