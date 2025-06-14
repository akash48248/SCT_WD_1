Project Title:
Interactive Fixed Navigation Menu

Description:
This project creates a fixed-position navigation menu that stays visible on all pages. It changes style or color when the user scrolls and highlights items on hover. The menu is responsive, user-friendly, and enhances site navigation with smooth transitions and modern design.



<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Interactive Fixed Navigation Menu</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
    }

    nav {
      position: fixed;
      top: 0;
      width: 100%;
      background: transparent;
      padding: 15px 30px;
      transition: background 0.3s, box-shadow 0.3s;
      z-index: 1000;
    }

    nav.scrolled {
      background-color: #333;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
    }

    nav ul {
      list-style: none;
      display: flex;
      justify-content: center;
    }

    nav ul li {
      margin: 0 20px;
    }

    nav ul li a {
      text-decoration: none;
      color: white;
      font-size: 18px;
      padding: 5px 10px;
      transition: color 0.3s, background 0.3s;
    }

    nav ul li a:hover {
      background-color: white;
      color: #333;
      border-radius: 5px;
    }

    header {
      height: 100vh;
      background: url('https://via.placeholder.com/1200x400') no-repeat center center/cover;
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2em;
    }

    section {
      padding: 60px;
      background: #f4f4f4;
    }
  </style>
</head>
<body>

  <nav id="navbar">
    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Services</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </nav>

  <header>
    <div>Welcome to Our Website</div>
  </header>

  <section>
    <h2>About Us</h2>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum ut feugiat sapien.</p>
  </section>

  <section>
    <h2>Services</h2>
    <p>Proin scelerisque, sapien nec elementum lacinia, nunc massa pulvinar magna.</p>
  </section>

  <section>
    <h2>Contact</h2>
    <p>Nullam finibus, velit ac feugiat imperdiet, libero nisi hendrerit leo, a tempus metus turpis non erat.</p>
  </section>

  <script>
    window.addEventListener('scroll', function () {
      const navbar = document.getElementById('navbar');
      if (window.scrollY > 50) {
        navbar.classList.add('scrolled');
      } else {
        navbar.classList.remove('scrolled');
      }
    });
  </script>

</body>
</html>
