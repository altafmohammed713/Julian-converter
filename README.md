# Julian-converter
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Julian Date Converter</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      margin: 0;
      padding: 0;
      background: #f0f4f8;
      color: #333;
    }

    header {
      background: #1e88e5;
      color: white;
      padding: 20px;
      text-align: center;
      animation: fadeIn 1s ease-in-out;
    }

    main {
      padding: 20px;
      max-width: 800px;
      margin: auto;
    }

    section {
      margin-bottom: 40px;
    }

    input, button {
      padding: 10px;
      margin: 5px 0;
      width: 100%;
      max-width: 300px;
    }

    button {
      background-color: #1e88e5;
      color: white;
      border: none;
      cursor: pointer;
      transition: background 0.3s;
    }

    button:hover {
      background-color: #1565c0;
    }

    .bookmark-links a {
      display: inline-block;
      margin: 5px 10px;
      color: #1e88e5;
      text-decoration: none;
    }

    .contact-form {
      display: flex;
      flex-direction: column;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    footer {
      text-align: center;
      padding: 20px;
      background: #ddd;
      font-size: 14px;
    }
  </style>
</head>
<body>
  <header>
    <h1>Julian Date Converter Tool</h1>
  </header>

  <main>
    <section id="converter">
      <h2>Convert to Julian Date</h2>
      <input type="date" id="gregDate" />
      <button onclick="convertToJulian()">Convert</button>
      <p id="julianResult"></p>
    </section>

    <section class="bookmark-links">
      <h2>Bookmarks</h2>
      <a href="#" target="_blank">Bookmark 1</a>
      <a href="#" target="_blank">Bookmark 2</a>
      <!-- Replace # with actual URLs -->
    </section>

    <section id="contact">
      <h2>Contact Me</h2>
      <form class="contact-form" onsubmit="alert('Thanks for your message!'); return false;">
        <input type="text" placeholder="Your Name" required />
        <input type="email" placeholder="Your Email" required />
        <textarea placeholder="Your Message" rows="5" required></textarea>
        <button type="submit">Send</button>
      </form>
    </section>
  </main>

  <footer>
    &copy; 2025 Julian Date Converter. All rights reserved.
  </footer>

  <script>
    function convertToJulian() {
      const dateInput = document.getElementById('gregDate').value;
      if (!dateInput) {
        document.getElementById('julianResult').innerText = 'Please select a date.';
        return;
      }
      const date = new Date(dateInput);
      const start = new Date(date.getFullYear(), 0, 0);
      const diff = date - start + ((start.getTimezoneOffset() - date.getTimezoneOffset()) * 60 * 1000);
      const day = Math.floor(diff / (1000 * 60 * 60 * 24));
      const julianDate = `${date.getFullYear()}${day.toString().padStart(3, '0')}`;
      document.getElementById('julianResult').innerText = `Julian Date: ${julianDate}`;
    }
  </script>
</body>
</html>
