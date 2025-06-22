# moriyah1025.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1"/>
  <title>Moriyah’s Babysitting Services</title>
  <style>
    body { margin:0; padding:0; font-family:Arial,sans-serif; background:#fff0f6; color:#333; }
    header, footer { background:#ffb6c1; text-align:center; padding:20px; }
    header h1, footer p { color:#fff; margin:0; }
    nav a { color:#fff; margin:0 10px; font-weight:bold; text-decoration:none; }
    main { max-width:800px; margin:auto; padding:20px; }
    section { margin-bottom:40px; }
    h2 { color:#c71585; }
    img.responsive { width:100%; border-radius:8px; margin-top:15px; }
    .logo { max-width:100px; display:block; margin:20px auto; }
    .pricing button {
      background:#ff85a1; color:#fff; border:none; padding:10px 20px;
      margin:5px; border-radius:5px; cursor:pointer; font-size:1em;
    }
    .pricing button:hover { background:#ff6699; }
    form { display:flex; flex-direction:column; }
    form label { margin-bottom:10px; }
    form input { padding:8px; font-size:1em; border:1px solid #ccc; border-radius:4px; width:100%; }
    form button {
      background:#ff85a1; color:#fff; border:none; padding:12px;
      border-radius:5px; font-size:1.1em; cursor:pointer;
    }
    form button:hover { background:#ff6699; }
    .chatbot { position:fixed; bottom:20px; right:20px; width:300px; }
    .chatbox { border:2px solid #ff85a1; background:#fff; border-radius:8px; display:flex; flex-direction:column; height:400px; }
    .chat-header { background:#ffb6c1; color:#fff; text-align:center; padding:10px; font-weight:bold; }
    .chat-messages { flex:1; padding:10px; overflow-y:auto; }
    .chat-controls { display:flex; }
    .chat-controls input { flex:1; padding:8px; border:none; border-top:1px solid #eee; }
    .chat-controls button { padding:8px 12px; background:#ff85a1; border:none; color:#fff; cursor:pointer; }
    .chat-controls button:hover { background:#ff6699; }
  </style>
</head>
<body>

  <header>
    <h1>Moriyah’s Babysitting Services</h1>
    <nav>
      <a href="#about">About Me</a>
      <a href="#philosophy">Philosophy</a>
      <a href="#services">Pricing</a>
      <a href="#schedule">Schedule</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main>
    <section id="about">
      <h2>About Me</h2>
      <p>Hi, I’m <strong>Moriyah</strong>, I’m 15. I’ve babysat at my church and serve as a camp counselor each year.</p>
      <img src="https://via.placeholder.com/700x400?text=Babysitting+Action" alt="Babysitting in action" class="responsive">
    </section>

    <section id="philosophy">
      <h2>My Philosophy</h2>
      <p>I believe every child deserves a safe, fun, and caring environment. I’m committed to building trust with families and ensuring peace of mind for parents.</p>
    </section>

    <section id="services">
      <h2>Services & Pricing</h2>
      <div class="pricing">
        <button onclick="chooseTime(1)">1 hour • $20</button>
        <button onclick="chooseTime(2)">2 hours • $40</button>
        <button onclick="chooseTime(3)">3 hours • $60</button>
        <button onclick="chooseTime(4)">4 hours • $80</button>
        <button onclick="chooseTime('overnight')">Overnight • $120+</button>
      </div>
    </section>

    <section id="schedule">
      <h2>Schedule a Session</h2>
      <form id="schedule-form">
        <label>Phone Number*<input type="tel" name="phone" required></label>
        <label>Email*<input type="email" name="email" required></label>
        <label># of Kids*<input type="number" name="kidsCount" min="1" required></label>
        <label>Kids' Names*<input type="text" name="kidNames" required></label>
        <label>Address*<input type="text" name="address" required></label>
        <input type="hidden" name="hours" id="hours" value="1">
        <button type="submit">Request & Pay</button>
      </form>
      <p>🧾 After submitting, pay via Cash App: <strong>$MoriyahMartin</strong> (include hours booked.)</p>
    </section>

    <section id="contact">
      <h2>Contact Us Here</h2>
      <p>Email: <a href="mailto:moriyahlaurynne@gmail.com">moriyahlaurynne@gmail.com</a></p>
    </section>
  </main>

  <footer>
    <img src="https://via.placeholder.com/100x100?text=Moriyah+Logo" class="logo" alt="Moriyah logo">
    <p>&copy; 2025 Moriyah’s Babysitting Services</p>
  </footer>

  <div class="chatbot">
    <div class="chatbox">
      <div class="chat-header">Olivia</div>
      <div class="chat-messages" id="chat-messages"></div>
      <div class="chat-controls">
        <input id="chat-input" placeholder="Ask me anything!" />
        <button onclick="sendChat()">Send</button>
      </div>
    </div>
  </div>

  <script>
    function chooseTime(h) {
      document.getElementById('hours').value = h;
      document.getElementById('schedule-form').scrollIntoView({ behavior: 'smooth' });
    }
    document.getElementById('schedule-form').onsubmit = function(e) {
      e.preventDefault();
      alert('Thanks! Your request is submitted. Please pay via Cash App.');
      this.reset();
    };
    function sendChat() {
      const inp = document.getElementById('chat-input');
      const text = inp.value.trim();
      if (!text) return;
      const msgs = document.getElementById('chat-messages');
      msgs.innerHTML += '<div><strong>You:</strong> ' + text + '</div>';
      setTimeout(() => {
        let resp = "Happy to help! Ask about booking, pricing, or my experience.";
        if (/price|cost/.test(text.toLowerCase())) resp = "My rate is $20/hr. Choose your hours above.";
        if (/experience|background/.test(text.toLowerCase())) resp = "I’ve babysat at church & am a camp counselor yearly.";
        if (/schedule|book/.test(text.toLowerCase())) resp = "Fill the form above, then pay via Cash App: $MoriyahMartin.";
        msgs.innerHTML += '<div><strong>Olivia:</strong> ' + resp + '</div>';
        msgs.scrollTop = msgs.scrollHeight;
      }, 500);
      inp.value = '';
    }
  </script>
</body>
</html>
