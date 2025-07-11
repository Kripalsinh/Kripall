<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Village Cricket Team</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary: #1b5e20;
      --accent: #ffc107;
      --accent2: #43a047;
      --bg: #f4f8f6;
      --white: #fff;
      --gray: #e0e0e0;
      --text: #222;
      --muted: #666;
      --radius: 18px;
      --shadow: 0 4px 24px rgba(27,94,32,0.11);
      --shadow-hover: 0 8px 32px rgba(27,94,32,0.18);
      --gradient: linear-gradient(120deg, #e8f5e9 60%, #fff 100%);
      --gradient-accent: linear-gradient(90deg, #1b5e20 0%, #43a047 100%);
      --transition: 0.18s cubic-bezier(.4,0,.2,1);
    }
    html, body {
      margin: 0;
      padding: 0;
      background: var(--bg);
      font-family: 'Inter', Arial, sans-serif;
      color: var(--text);
      scroll-behavior: smooth;
    }
    a { color: var(--primary); text-decoration: none; }
    /* Navbar */
    .navbar {
      background: var(--white);
      box-shadow: 0 1px 0 var(--gray);
      position: sticky;
      top: 0;
      z-index: 10;
      animation: fadeInDown 0.7s;
    }
    @keyframes fadeInDown {
      from { opacity: 0; transform: translateY(-30px);}
      to { opacity: 1; transform: translateY(0);}
    }
    .navbar-inner {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 24px;
      height: 68px;
    }
    .nav-logo {
      font-size: 1.5em;
      font-weight: 800;
      color: var(--primary);
      letter-spacing: 1px;
      display: flex;
      align-items: center;
      gap: 10px;
      animation: fadeInLeft 1s;
    }
    @keyframes fadeInLeft {
      from { opacity: 0; transform: translateX(-30px);}
      to { opacity: 1; transform: translateX(0);}
    }
    .nav-links {
      display: flex;
      gap: 28px;
      align-items: center;
    }
    .nav-link {
      font-weight: 600;
      color: var(--primary);
      font-size: 1.05em;
      padding: 6px 10px;
      border-radius: 8px;
      transition: background var(--transition), color var(--transition);
      position: relative;
      overflow: hidden;
    }
    .nav-link:after {
      content: "";
      display: block;
      position: absolute;
      left: 0; right: 0; bottom: 0;
      height: 3px;
      background: var(--accent);
      border-radius: 2px;
      transform: scaleX(0);
      transition: transform var(--transition);
    }
    .nav-link:hover, .nav-link.active {
      background: var(--accent);
      color: var(--primary);
    }
    .nav-link:hover:after, .nav-link.active:after {
      transform: scaleX(1);
    }
    .nav-toggle {
      display: none;
      background: none;
      border: none;
      font-size: 2em;
      color: var(--primary);
      cursor: pointer;
    }
    /* Home Section */
    .home-section {
      background: var(--gradient);
      padding: 64px 0 32px 0;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    .home-section::before {
      content: "";
      position: absolute;
      left: -80px; top: -80px;
      width: 220px; height: 220px;
      background: var(--accent2);
      opacity: 0.08;
      border-radius: 50%;
      z-index: 0;
      animation: float 6s infinite alternate;
    }
    .home-banner {
      width: 100%;
      max-width: 420px;
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      margin: 0 auto 24px auto;
      display: block;
      animation: fadeInUp 1.2s;
    }
    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(40px);}
      to { opacity: 1; transform: translateY(0);}
    }
    .home-title {
      font-size: 2.5em;
      font-weight: 900;
      color: var(--primary);
      margin-bottom: 10px;
      letter-spacing: -1px;
      text-shadow: 0 2px 8px #1b5e2011;
      animation: fadeIn 1.2s;
    }
    @keyframes fadeIn {
      from { opacity: 0;}
      to { opacity: 1;}
    }
    .home-desc {
      color: var(--muted);
      font-size: 1.15em;
      max-width: 600px;
      margin: 0 auto 0 auto;
      animation: fadeIn 1.5s;
    }
    /* Section Titles */
    .section-title {
      font-size: 1.7em;
      font-weight: 800;
      color: var(--primary);
      margin: 48px 0 18px 0;
      text-align: center;
      letter-spacing: -1px;
      text-shadow: 0 2px 8px #1b5e2011;
      animation: fadeIn 1s;
    }
    /* Match History */
    .match-table-wrap {
      max-width: 900px;
      margin: 0 auto 0 auto;
      overflow-x: auto;
      animation: fadeInUp 1s;
    }
    .match-table {
      width: 100%;
      border-collapse: collapse;
      background: var(--white);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      overflow: hidden;
    }
    .match-table th, .match-table td {
      padding: 14px 10px;
      text-align: center;
      font-size: 1.05em;
    }
    .match-table th {
      background: #e8f5e9;
      color: var(--primary);
      font-weight: 700;
    }
    .match-table tr:not(:last-child) td {
      border-bottom: 1px solid var(--gray);
    }
    .match-table td.winner {
      color: var(--accent);
      font-weight: 700;
      animation: winnerPulse 1.5s infinite alternate;
    }
    @keyframes winnerPulse {
      0% { color: var(--accent);}
      100% { color: var(--accent2);}
    }
    /* Upcoming Matches */
    .upcoming-matches {
      max-width: 900px;
      margin: 24px auto 0 auto;
      background: var(--white);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 24px 18px;
      animation: fadeInUp 1.2s;
    }
    .upcoming-title {
      font-size: 1.2em;
      font-weight: 700;
      color: var(--primary);
      margin-bottom: 10px;
      text-align: center;
    }
    .upcoming-list {
      display: flex;
      flex-direction: column;
      gap: 12px;
      align-items: center;
    }
    .upcoming-item {
      background: #e8f5e9;
      border-radius: 10px;
      padding: 10px 18px;
      color: var(--primary);
      font-weight: 600;
      font-size: 1.05em;
      box-shadow: 0 1px 4px #1b5e2011;
      display: flex;
      gap: 18px;
      align-items: center;
      min-width: 220px;
      animation: fadeIn 1.2s;
    }
    .upcoming-date {
      color: var(--accent2);
      font-weight: 700;
      margin-right: 8px;
    }
    /* Gallery */
    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 18px;
      max-width: 900px;
      margin: 0 auto;
      animation: fadeInUp 1.2s;
    }
    .gallery-img {
      width: 100%;
      aspect-ratio: 4/3;
      object-fit: cover;
      border-radius: 12px;
      box-shadow: 0 2px 8px #1b5e2011;
      cursor: pointer;
      transition: transform 0.18s, box-shadow 0.18s;
      filter: grayscale(0.1) brightness(0.98);
    }
    .gallery-img:hover {
      transform: scale(1.06) rotate(-2deg);
      box-shadow: var(--shadow-hover);
      filter: none;
    }
    /* Lightbox */
    .lightbox {
      display: none;
      position: fixed;
      z-index: 1000;
      left: 0; top: 0; right: 0; bottom: 0;
      background: rgba(0,0,0,0.85);
      align-items: center;
      justify-content: center;
      animation: fadeIn 0.5s;
    }
    .lightbox.active {
      display: flex;
    }
    .lightbox-img {
      max-width: 96vw;
      max-height: 90vh;
      border-radius: 12px;
      box-shadow: 0 8px 32px #0008;
      background: #fff;
      animation: fadeInUp 0.7s;
    }
    .lightbox-close {
      position: absolute;
      top: 32px;
      right: 48px;
      font-size: 2.5em;
      color: #fff;
      background: none;
      border: none;
      cursor: pointer;
      z-index: 1100;
      transition: color 0.18s;
    }
    .lightbox-close:hover {
      color: var(--accent);
    }
    /* Players List */
    .players-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 22px;
      max-width: 1000px;
      margin: 0 auto;
      animation: fadeInUp 1.2s;
    }
    .player-card {
      background: var(--white);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 18px 12px 18px 12px;
      display: flex;
      flex-direction: column;
      align-items: center;
      transition: box-shadow var(--transition), transform var(--transition);
      cursor: pointer;
      position: relative;
      animation: fadeInUp 1.2s;
    }
    .player-card:hover {
      box-shadow: var(--shadow-hover);
      transform: translateY(-4px) scale(1.04);
    }
    .player-img {
      width: 90px;
      height: 90px;
      border-radius: 50%;
      object-fit: cover;
      margin-bottom: 10px;
      border: 3px solid var(--accent);
      background: #e8f5e9;
      transition: border 0.18s;
    }
    .player-card:hover .player-img {
      border: 3px solid var(--accent2);
    }
    .player-name {
      font-size: 1.1em;
      font-weight: 700;
      color: var(--primary);
      margin-bottom: 2px;
    }
    .player-role {
      color: var(--accent);
      font-size: 1em;
      font-weight: 600;
      margin-bottom: 6px;
    }
    .player-records-btn {
      background: var(--accent2);
      color: #fff;
      border: none;
      border-radius: 8px;
      font-size: 0.98em;
      font-weight: 600;
      padding: 7px 18px;
      cursor: pointer;
      margin-top: 8px;
      transition: background 0.18s;
      box-shadow: 0 1px 4px #1b5e2011;
    }
    .player-records-btn:hover {
      background: var(--primary);
    }
    /* Player Modal */
    .player-modal {
      display: none;
      position: fixed;
      z-index: 1200;
      left: 0; top: 0; right: 0; bottom: 0;
      background: rgba(0,0,0,0.85);
      align-items: center;
      justify-content: center;
      animation: fadeIn 0.5s;
    }
    .player-modal.active {
      display: flex;
    }
    .player-modal-content {
      background: var(--white);
      border-radius: 18px;
      box-shadow: 0 8px 32px #0008;
      padding: 38px 32px 32px 32px;
      min-width: 320px;
      max-width: 95vw;
      position: relative;
      text-align: center;
      animation: fadeInUp 0.5s;
    }
    .player-modal-close {
      position: absolute;
      top: 18px;
      right: 24px;
      font-size: 2em;
      color: var(--primary);
      background: none;
      border: none;
      cursor: pointer;
      z-index: 1100;
      transition: color 0.18s;
    }
    .player-modal-close:hover {
      color: var(--accent2);
    }
    .player-modal-img {
      width: 110px;
      height: 110px;
      border-radius: 50%;
      object-fit: cover;
      margin-bottom: 10px;
      border: 3px solid var(--accent);
      background: #e8f5e9;
      transition: border 0.18s;
    }
    .player-modal-name {
      font-size: 1.3em;
      font-weight: 800;
      color: var(--primary);
      margin-bottom: 2px;
    }
    .player-modal-role {
      color: var(--accent2);
      font-size: 1.1em;
      font-weight: 600;
      margin-bottom: 10px;
    }
    .player-modal-records {
      text-align: left;
      margin: 0 auto;
      max-width: 320px;
      color: var(--text);
      font-size: 1.08em;
    }
    .player-modal-records li {
      margin-bottom: 6px;
      border-bottom: 1px solid #e0e0e0;
      padding-bottom: 4px;
      font-weight: 500;
    }
    /* Achievements Section */
    .achievements-section {
      max-width: 900px;
      margin: 48px auto 0 auto;
      background: var(--white);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 38px 28px 28px 28px;
      text-align: center;
      animation: fadeInUp 1.2s;
    }
    .achievements-title {
      font-size: 1.3em;
      font-weight: 700;
      color: var(--primary);
      margin-bottom: 10px;
    }
    .achievements-list {
      display: flex;
      flex-wrap: wrap;
      gap: 24px;
      justify-content: center;
      margin-top: 18px;
    }
    .achievement-card {
      background: #e8f5e9;
      border-radius: 12px;
      padding: 18px 24px;
      color: var(--primary);
      font-weight: 700;
      font-size: 1.08em;
      min-width: 180px;
      box-shadow: 0 1px 4px #1b5e2011;
      display: flex;
      flex-direction: column;
      align-items: center;
      animation: fadeInUp 1.2s;
      transition: box-shadow 0.18s, transform 0.18s;
    }
    .achievement-card:hover {
      box-shadow: var(--shadow-hover);
      transform: scale(1.04);
    }
    .achievement-icon {
      font-size: 2em;
      color: var(--accent2);
      margin-bottom: 8px;
      animation: bounce 1.5s infinite alternate;
    }
    @keyframes bounce {
      0% { transform: translateY(0);}
      100% { transform: translateY(-10px);}
    }
    /* About */
    .about-section {
      max-width: 900px;
      margin: 0 auto;
      background: var(--white);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 38px 28px 28px 28px;
      margin-top: 38px;
      margin-bottom: 38px;
      text-align: center;
      animation: fadeInUp 1.2s;
    }
    .about-title {
      font-size: 1.3em;
      font-weight: 700;
      color: var(--primary);
      margin-bottom: 10px;
    }
    .about-desc {
      color: var(--muted);
      font-size: 1.1em;
      margin-bottom: 0;
    }
    /* Contact */
    .contact-section {
      max-width: 600px;
      margin: 0 auto 38px auto;
      background: var(--white);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 38px 28px 28px 28px;
      text-align: center;
      animation: fadeInUp 1.2s;
    }
    .contact-title {
      font-size: 1.2em;
      font-weight: 700;
      color: var(--primary);
      margin-bottom: 10px;
    }
    .contact-form input, .contact-form textarea {
      width: 100%;
      border-radius: 8px;
      border: 1.5px solid var(--gray);
      padding: 12px 14px;
      font-size: 1em;
      margin-bottom: 12px;
      background: #f8fafc;
      color: var(--text);
      outline: none;
      transition: border 0.15s;
    }
    .contact-form input:focus, .contact-form textarea:focus {
      border-color: var(--primary);
    }
    .contact-form button {
      background: var(--primary);
      color: #fff;
      border: none;
      border-radius: 8px;
      font-size: 1.08em;
      font-weight: 700;
      padding: 12px 38px;
      cursor: pointer;
      margin-top: 8px;
      transition: background 0.18s;
      box-shadow: 0 1px 4px #1b5e2011;
    }
    .contact-form button:hover {
      background: var(--accent2);
    }
    .contact-details {
      color: var(--muted);
      font-size: 1.08em;
      margin-top: 18px;
    }
    /* Footer */
    .footer {
      background: var(--primary);
      color: #fff;
      padding: 38px 0 18px 0;
      font-size: 1em;
      margin-top: 0;
      text-align: center;
      letter-spacing: 1px;
      animation: fadeInUp 1.2s;
    }
    .footer-social {
      display: flex;
      gap: 18px;
      justify-content: center;
      margin-top: 12px;
    }
    .footer-social a {
      color: #fff;
      font-size: 1.3em;
      transition: color 0.18s;
    }
    .footer-social a:hover {
      color: var(--accent);
    }
    .footer-bottom {
      color: #e0e0e0;
      font-size: 0.98em;
      margin-top: 18px;
    }
    /* Responsive */
    @media (max-width: 900px) {
      .navbar-inner, .home-section, .section-card, .about-section, .contact-section, .achievements-section {
        padding-left: 8px;
        padding-right: 8px;
      }
      .hero-inner, .section-card-row, .players-grid, .gallery-grid, .achievements-list {
        gap: 12px;
      }
    }
    @media (max-width: 700px) {
      .navbar-inner {
        flex-direction: column;
        height: auto;
        gap: 8px;
        padding: 0 8px;
      }
      .nav-links {
        flex-direction: column;
        gap: 0;
        width: 100%;
        display: none;
        background: var(--white);
        border-radius: 0 0 12px 12px;
        box-shadow: 0 2px 8px #1b5e2011;
        margin-top: 8px;
      }
      .nav-links.open {
        display: flex;
      }
      .nav-toggle {
        display: block;
      }
    }
  </style>
</head>
<body>
  <!-- Navbar -->
  <nav class="navbar">
    <div class="navbar-inner">
      <span class="nav-logo"><i class="fa fa-cricket"></i>Village XI</span>
      <button class="nav-toggle" id="navToggle"><i class="fa fa-bars"></i></button>
      <div class="nav-links" id="navLinks">
        <a class="nav-link active" href="#home">Home</a>
        <a class="nav-link" href="#matches">Matches</a>
        <a class="nav-link" href="#upcoming">Upcoming</a>
        <a class="nav-link" href="#gallery">Gallery</a>
        <a class="nav-link" href="#players">Players</a>
        <a class="nav-link" href="#achievements">Achievements</a>
        <a class="nav-link" href="#about">About</a>
        <a class="nav-link" href="#contact">Contact</a>
      </div>
    </div>
  </nav>
  <!-- Home Section -->
  <section class="home-section" id="home">
    <img class="home-banner" src="https://images.unsplash.com/photo-1505843276877-5a8a82506e8e?auto=format&fit=crop&w=800&q=80" alt="Village Cricket Team">
    <div class="home-title">Welcome to Village XI Cricket Team</div>
    <div class="home-desc">
      We are a passionate group of cricketers from our village, playing together for the love of the game. From friendly matches to local tournaments, we strive for teamwork, sportsmanship, and fun!
    </div>
  </section>
  <!-- Match History -->
  <div class="section-title" id="matches">Match History</div>
  <div class="match-table-wrap">
    <table class="match-table">
      <thead>
        <tr>
          <th>Date</th>
          <th>Teams</th>
          <th>Scores</th>
          <th>Winner</th>
          <th>Venue</th>
          <th>Details</th>
        </tr>
      </thead>
      <tbody id="matchHistory">
        <!-- JS will render rows -->
      </tbody>
    </table>
  </div>
  <!-- Match Details Modal -->
  <div class="player-modal" id="matchModal">
    <div class="player-modal-content" id="matchModalContent">
      <button class="player-modal-close" id="matchModalClose">&times;</button>
      <!-- JS will fill content -->
    </div>
  </div>
  <!-- Upcoming Matches -->
  <div class="upcoming-matches" id="upcoming">
    <div class="upcoming-title"><i class="fa fa-calendar-alt"></i> Upcoming Matches</div>
    <div class="upcoming-list" id="upcomingList">
      <!-- JS will render upcoming matches -->
    </div>
  </div>
  <!-- Gallery -->
  <div class="section-title" id="gallery">Photo Gallery</div>
  <div class="gallery-grid" id="galleryGrid">
    <!-- JS will render images -->
  </div>
  <!-- Lightbox -->
  <div class="lightbox" id="lightbox">
    <button class="lightbox-close" id="lightboxClose">&times;</button>
    <img class="lightbox-img" id="lightboxImg" src="" alt="Gallery">
  </div>
  <!-- Players List -->
  <div class="section-title" id="players">Players</div>
  <div class="players-grid" id="playersGrid">
    <!-- JS will render players -->
  </div>
  <!-- Player Modal -->
  <div class="player-modal" id="playerModal">
    <div class="player-modal-content" id="playerModalContent">
      <button class="player-modal-close" id="playerModalClose">&times;</button>
      <!-- JS will fill content -->
    </div>
  </div>
  <!-- Achievements Section -->
  <div class="achievements-section" id="achievements">
    <div class="achievements-title">Team Achievements</div>
    <div class="achievements-list" id="achievementsList">
      <!-- JS will render achievements -->
    </div>
  </div>
  <!-- About Section -->
  <div class="about-section" id="about">
    <div class="about-title">About Village XI</div>
    <div class="about-desc">
      Village XI was formed in 2012 by a group of cricket enthusiasts in our village. Over the years, we have grown into a competitive team, winning several local tournaments and fostering young talent. Our biggest achievement was winning the District Cup in 2022. We believe in unity, discipline, and the spirit of cricket!
    </div>
  </div>
  <!-- Contact Section -->
  <div class="contact-section" id="contact">
    <div class="contact-title">Contact Us</div>
    <form class="contact-form" id="contactForm" autocomplete="off">
      <input type="text" id="contactName" placeholder="Your Name" required>
      <input type="email" id="contactEmail" placeholder="Your Email" required>
      <textarea id="contactMsg" placeholder="Your Message" required></textarea>
      <button type="submit">Send Message</button>
    </form>
    <div class="contact-details">
      <div><i class="fa fa-envelope"></i> villagexi@cricket.com</div>
      <div><i class="fa fa-phone"></i> +91 98765 43210</div>
      <div><i class="fa fa-map-marker-alt"></i> Village Ground, Main Road, Our Village</div>
    </div>
  </div>
  <!-- Footer -->
  <footer class="footer">
    <div>
      <div style="font-size:1.2em;font-weight:800;letter-spacing:1px;">Village XI Cricket Team</div>
      <div class="footer-social">
        <a href="#"><i class="fab fa-facebook-f"></i></a>
        <a href="#"><i class="fab fa-instagram"></i></a>
        <a href="#"><i class="fab fa-twitter"></i></a>
      </div>
      <div class="footer-bottom">
        &copy; 2024 Village XI. All Rights Reserved.
      </div>
    </div>
  </footer>
  <!-- FontAwesome for icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
  <script>
    // Navbar mobile toggle
    document.getElementById('navToggle').onclick = function() {
      document.getElementById('navLinks').classList.toggle('open');
    };
    document.querySelectorAll('.nav-link').forEach(link => {
      link.onclick = function() {
        document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
        this.classList.add('active');
        document.getElementById('navLinks').classList.remove('open');
      };
    });

    // Match History Data (add summary, best performers, playing11, playerPerformances)
    const matches = [
      {
        date: '2024-04-01',
        teams: 'Village XI vs City CC',
        scores: '145/8 vs 142/10',
        winner: 'Village XI',
        venue: 'Village Ground',
        summary: 'A thrilling match where Village XI defended a modest total. Rohit Sharma scored a crucial 65 runs.',
        bestPerformers: [
          { name: 'Rohit Sharma', role: 'Batsman', performance: '65 runs (MOM)' },
          { name: 'Suresh Singh', role: 'Bowler', performance: '3/28' }
        ],
        playing11: [
          'Rohit Sharma', 'Amit Kumar', 'Suresh Singh', 'Vikram Patel', 'Rahul Yadav', 'Manoj Verma',
          'Deepak Joshi', 'Anil Singh', 'Karan Mehta', 'Sunil Kumar', 'Ravi Chauhan'
        ],
        playerPerformances: [
          { name: 'Rohit Sharma', runs: 65, wickets: 0 },
          { name: 'Amit Kumar', runs: 22, wickets: 1 },
          { name: 'Suresh Singh', runs: 8, wickets: 3 },
          { name: 'Vikram Patel', runs: 18, wickets: 0 },
          { name: 'Rahul Yadav', runs: 12, wickets: 0 },
          { name: 'Manoj Verma', runs: 5, wickets: 2 },
          { name: 'Deepak Joshi', runs: 0, wickets: 1 },
          { name: 'Anil Singh', runs: 4, wickets: 1 },
          { name: 'Karan Mehta', runs: 6, wickets: 0 },
          { name: 'Sunil Kumar', runs: 3, wickets: 1 },
          { name: 'Ravi Chauhan', runs: 2, wickets: 0 }
        ]
      },
      {
        date: '2024-03-24',
        teams: 'Village XI vs River Runners',
        scores: '178/6 vs 180/7',
        winner: 'River Runners',
        venue: 'River Park',
        summary: 'A high-scoring game, but River Runners chased down the target in the last over.',
        bestPerformers: [
          { name: 'Amit Kumar', role: 'All-rounder', performance: '54 runs, 2 wickets' },
          { name: 'River Runners - S. Roy', role: 'Batsman', performance: '72 runs' }
        ],
        playing11: [
          'Rohit Sharma', 'Amit Kumar', 'Suresh Singh', 'Vikram Patel', 'Rahul Yadav', 'Manoj Verma',
          'Deepak Joshi', 'Anil Singh', 'Karan Mehta', 'Sunil Kumar', 'Ravi Chauhan'
        ],
        playerPerformances: [
          { name: 'Rohit Sharma', runs: 30, wickets: 0 },
          { name: 'Amit Kumar', runs: 54, wickets: 2 },
          { name: 'Suresh Singh', runs: 10, wickets: 1 },
          { name: 'Vikram Patel', runs: 28, wickets: 0 },
          { name: 'Rahul Yadav', runs: 15, wickets: 0 },
          { name: 'Manoj Verma', runs: 8, wickets: 1 },
          { name: 'Deepak Joshi', runs: 5, wickets: 1 },
          { name: 'Anil Singh', runs: 7, wickets: 0 },
          { name: 'Karan Mehta', runs: 12, wickets: 0 },
          { name: 'Sunil Kumar', runs: 6, wickets: 0 },
          { name: 'Ravi Chauhan', runs: 3, wickets: 0 }
        ]
      },
      {
        date: '2024-03-17',
        teams: 'Village XI vs Hilltopers',
        scores: '162/9 vs 160/10',
        winner: 'Village XI',
        venue: 'Hilltop Ground',
        summary: 'Village XI clinched a close win. Suresh Singh took 4 wickets.',
        bestPerformers: [
          { name: 'Suresh Singh', role: 'Bowler', performance: '4/19' },
          { name: 'Vikram Patel', role: 'Batsman', performance: '49 runs' }
        ],
        playing11: [
          'Rohit Sharma', 'Amit Kumar', 'Suresh Singh', 'Vikram Patel', 'Rahul Yadav', 'Manoj Verma',
          'Deepak Joshi', 'Anil Singh', 'Karan Mehta', 'Sunil Kumar', 'Ravi Chauhan'
        ],
        playerPerformances: [
          { name: 'Rohit Sharma', runs: 18, wickets: 0 },
          { name: 'Amit Kumar', runs: 27, wickets: 1 },
          { name: 'Suresh Singh', runs: 6, wickets: 4 },
          { name: 'Vikram Patel', runs: 49, wickets: 0 },
          { name: 'Rahul Yadav', runs: 20, wickets: 0 },
          { name: 'Manoj Verma', runs: 7, wickets: 2 },
          { name: 'Deepak Joshi', runs: 8, wickets: 1 },
          { name: 'Anil Singh', runs: 5, wickets: 1 },
          { name: 'Karan Mehta', runs: 10, wickets: 0 },
          { name: 'Sunil Kumar', runs: 6, wickets: 0 },
          { name: 'Ravi Chauhan', runs: 6, wickets: 0 }
        ]
      }
      // ...existing matches...
    ];
    function renderMatches() {
      const tbody = document.getElementById('matchHistory');
      tbody.innerHTML = '';
      matches.forEach((m, idx) => {
        tbody.innerHTML += `<tr>
          <td>${m.date}</td>
          <td>${m.teams}</td>
          <td>${m.scores}</td>
          <td class="winner">${m.winner}</td>
          <td>${m.venue}</td>
          <td><button style="background:var(--accent2);color:#fff;border:none;border-radius:6px;padding:5px 14px;cursor:pointer;font-weight:600;" onclick="showMatchModal(${idx})">View</button></td>
        </tr>`;
      });
    }
    renderMatches();

    // Match Modal
    function showMatchModal(idx) {
      const m = matches[idx];
      let performers = m.bestPerformers.map(bp => `<li><b>${bp.name}</b> (${bp.role}): ${bp.performance}</li>`).join('');
      let playing11 = m.playing11.map(p => `<li>${p}</li>`).join('');
      let perfRows = m.playerPerformances.map(pp =>
        `<tr>
          <td>${pp.name}</td>
          <td>${pp.runs}</td>
          <td>${pp.wickets}</td>
        </tr>`
      ).join('');
      document.getElementById('matchModalContent').innerHTML = `
        <button class="player-modal-close" id="matchModalClose">&times;</button>
        <div style="font-size:1.3em;font-weight:800;color:var(--primary);margin-bottom:6px;">${m.teams}</div>
        <div style="color:var(--accent2);font-weight:700;margin-bottom:8px;">${m.date} | ${m.venue}</div>
        <div style="margin-bottom:10px;"><b>Scores:</b> ${m.scores}</div>
        <div style="margin-bottom:10px;"><b>Summary:</b> ${m.summary}</div>
        <div style="margin-bottom:10px;"><b>Best Performers:</b><ul style="margin:6px 0 0 18px;">${performers}</ul></div>
        <div style="margin-bottom:10px;"><b>Playing XI:</b><ul style="margin:6px 0 0 18px;">${playing11}</ul></div>
        <div style="margin-bottom:10px;">
          <b>Player Performances:</b>
          <table style="width:100%;margin-top:6px;border-collapse:collapse;">
            <thead>
              <tr style="background:#e8f5e9;">
                <th style="padding:4px 8px;">Player</th>
                <th style="padding:4px 8px;">Runs</th>
                <th style="padding:4px 8px;">Wickets</th>
              </tr>
            </thead>
            <tbody>
              ${perfRows}
            </tbody>
          </table>
        </div>
      `;
      document.getElementById('matchModal').classList.add('active');
      document.getElementById('matchModalClose').onclick = function() {
        document.getElementById('matchModal').classList.remove('active');
      };
    }
    document.getElementById('matchModal').onclick = function(e) {
      if (e.target === this) this.classList.remove('active');
    };

    // Players Data (add description, all matches, performance)
    const players = [
      {
        name: "Rohit Sharma",
        photo: "https://randomuser.me/api/portraits/men/32.jpg",
        role: "Captain / Batsman",
        description: "Aggressive opener, inspirational leader, and the backbone of Village XI's batting lineup. Known for his calm under pressure and ability to anchor big chases.",
        stats: { matches: 45, runs: 1800, highest: 120, wickets: 8, bestBowling: "2/15", average: 44.1, strikeRate: 92.5, fifties: 14, hundreds: 3 },
        matchPerformances: [
          { match: "Village XI vs City CC (2024-04-01)", runs: 65, wickets: 0 },
          { match: "Village XI vs River Runners (2024-03-24)", runs: 30, wickets: 0 },
          { match: "Village XI vs Hilltopers (2024-03-17)", runs: 18, wickets: 0 }
        ]
      },
      {
        name: "Amit Kumar",
        photo: "https://randomuser.me/api/portraits/men/45.jpg",
        role: "All-rounder",
        description: "Dynamic all-rounder, reliable in the middle order and a handy medium pacer. Brings balance to the team with both bat and ball.",
        stats: { matches: 42, runs: 1200, highest: 88, wickets: 35, bestBowling: "4/22", average: 32.4, strikeRate: 85.2, fifties: 8, hundreds: 0 },
        matchPerformances: [
          { match: "Village XI vs City CC (2024-04-01)", runs: 22, wickets: 1 },
          { match: "Village XI vs River Runners (2024-03-24)", runs: 54, wickets: 2 },
          { match: "Village XI vs Hilltopers (2024-03-17)", runs: 27, wickets: 1 }
        ]
      },
      {
        name: "Suresh Singh",
        photo: "https://randomuser.me/api/portraits/men/55.jpg",
        role: "Bowler",
        description: "Strike bowler with a knack for breaking partnerships. His pace and swing make him a threat on any surface.",
        stats: { matches: 38, runs: 320, highest: 28, wickets: 54, bestBowling: "5/19", average: 8.4, strikeRate: 65.1, fifties: 0, hundreds: 0 },
        matchPerformances: [
          { match: "Village XI vs City CC (2024-04-01)", runs: 8, wickets: 3 },
          { match: "Village XI vs River Runners (2024-03-24)", runs: 10, wickets: 1 },
          { match: "Village XI vs Hilltopers (2024-03-17)", runs: 6, wickets: 4 }
        ]
      },
      {
        name: "Vikram Patel",
        photo: "https://randomuser.me/api/portraits/men/60.jpg",
        role: "Batsman",
        description: "Stylish right-hander, known for his elegant drives and consistency at the top order.",
        stats: { matches: 40, runs: 1350, highest: 101, wickets: 2, bestBowling: "1/10", average: 37.5, strikeRate: 88.7, fifties: 10, hundreds: 2 },
        matchPerformances: [
          { match: "Village XI vs City CC (2024-04-01)", runs: 18, wickets: 0 },
          { match: "Village XI vs River Runners (2024-03-24)", runs: 28, wickets: 0 },
          { match: "Village XI vs Hilltopers (2024-03-17)", runs: 49, wickets: 0 }
        ]
      },
      {
        name: "Rahul Yadav",
        photo: "https://randomuser.me/api/portraits/men/70.jpg",
        role: "Wicketkeeper",
        description: "Safe hands behind the stumps and a quick scorer in the lower order. Keeps the team energized.",
        stats: { matches: 36, runs: 900, highest: 76, wickets: 0, bestBowling: "-", average: 29.0, strikeRate: 80.3, fifties: 5, hundreds: 0 },
        matchPerformances: [
          { match: "Village XI vs City CC (2024-04-01)", runs: 12, wickets: 0 },
          { match: "Village XI vs River Runners (2024-03-24)", runs: 15, wickets: 0 },
          { match: "Village XI vs Hilltopers (2024-03-17)", runs: 20, wickets: 0 }
        ]
      },
      {
        name: "Manoj Verma",
        photo: "https://randomuser.me/api/portraits/men/80.jpg",
        role: "Bowler",
        description: "Economical bowler, often bowls in the death overs. Can swing the bat when needed.",
        stats: { matches: 28, runs: 210, highest: 19, wickets: 38, bestBowling: "4/12", average: 10.5, strikeRate: 70.2, fifties: 0, hundreds: 0 },
        matchPerformances: [
          { match: "Village XI vs City CC (2024-04-01)", runs: 5, wickets: 2 },
          { match: "Village XI vs River Runners (2024-03-24)", runs: 8, wickets: 1 },
          { match: "Village XI vs Hilltopers (2024-03-17)", runs: 7, wickets: 2 }
        ]
      }
    ];
    function renderPlayers() {
      const grid = document.getElementById('playersGrid');
      grid.innerHTML = '';
      players.forEach((p, idx) => {
        const card = document.createElement('div');
        card.className = 'player-card';
        card.innerHTML = `
          <img class="player-img" src="${p.photo}" alt="${p.name}">
          <div class="player-name">${p.name}</div>
          <div class="player-role">${p.role}</div>
          <button class="player-records-btn" onclick="showPlayerModal(${idx})">View Details</button>
        `;
        grid.appendChild(card);
      });
    }
    renderPlayers();

    // Player Modal (with more details, stats, all matches)
    function showPlayerModal(idx) {
      const p = players[idx];
      let stats = p.stats;
      let perfRows = p.matchPerformances.map(mp =>
        `<tr>
          <td>${mp.match}</td>
          <td>${mp.runs}</td>
          <td>${mp.wickets}</td>
        </tr>`
      ).join('');
      document.getElementById('playerModalContent').innerHTML = `
        <button class="player-modal-close" id="playerModalClose">&times;</button>
        <img class="player-modal-img" src="${p.photo}" alt="${p.name}">
        <div class="player-modal-name">${p.name}</div>
        <div class="player-modal-role">${p.role}</div>
        <div style="color:var(--muted);font-size:1.05em;margin-bottom:10px;">${p.description}</div>
        <ul class="player-modal-records">
          <li><b>Matches:</b> ${stats.matches}</li>
          <li><b>Total Runs:</b> ${stats.runs}</li>
          <li><b>Highest Score:</b> ${stats.highest}</li>
          <li><b>Batting Average:</b> ${stats.average}</li>
          <li><b>Strike Rate:</b> ${stats.strikeRate}</li>
          <li><b>50s/100s:</b> ${stats.fifties} / ${stats.hundreds}</li>
          <li><b>Wickets:</b> ${stats.wickets}</li>
          <li><b>Best Bowling:</b> ${stats.bestBowling}</li>
        </ul>
        <div style="margin:10px 0 4px 0;font-weight:700;color:var(--primary);">Recent Match Performances</div>
        <table style="width:100%;margin-top:6px;border-collapse:collapse;">
          <thead>
            <tr style="background:#e8f5e9;">
              <th style="padding:4px 8px;">Match</th>
              <th style="padding:4px 8px;">Runs</th>
              <th style="padding:4px 8px;">Wickets</th>
            </tr>
          </thead>
          <tbody>
            ${perfRows}
          </tbody>
        </table>
      `;
      document.getElementById('playerModal').classList.add('active');
      document.getElementById('playerModalClose').onclick = function() {
        document.getElementById('playerModal').classList.remove('active');
      };
    }
    document.getElementById('playerModal').onclick = function(e) {
      if (e.target === this) this.classList.remove('active');
    };

    // Achievements Data
    const achievements = [
      {icon: "fa-trophy", title: "District Cup Champions", desc: "Winners of District Cup 2022"},
      {icon: "fa-medal", title: "Best Team Spirit", desc: "Awarded for sportsmanship, 2021"},
      {icon: "fa-star", title: "Highest Run Scorer", desc: "Rohit Sharma - 1800 runs"},
      {icon: "fa-bowling-ball", title: "Best Bowler", desc: "Suresh Singh - 54 wickets"},
      {icon: "fa-users", title: "Community Service", desc: "Organized village cricket camp 2023"}
    ];
    function renderAchievements() {
      const list = document.getElementById('achievementsList');
      list.innerHTML = '';
      achievements.forEach(a => {
        list.innerHTML += `
          <div class="achievement-card">
            <span class="achievement-icon"><i class="fa ${a.icon}"></i></span>
            <div>${a.title}</div>
            <div style="color:var(--muted);font-size:0.98em;font-weight:400;margin-top:4px;">${a.desc}</div>
          </div>
        `;
      });
    }
    renderAchievements();

    // Contact Form
    document.getElementById('contactForm').onsubmit = function(e) {
      e.preventDefault();
      alert('Thank you for contacting us! We will get back to you soon.');
      this.reset();
    };
  </script>
</body>
</html>
