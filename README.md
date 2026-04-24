<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
  <title>Voices of Hope | Supporting Singapore's Underprivileged Children & Orphanages</title>
  <!-- Google Fonts: clean & warm -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700&family=Playfair+Display:ital,wght@0,500;0,600;1,500&display=swap" rel="stylesheet">
  <!-- Font Awesome 6 (free icons) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Inter', sans-serif;
      background-color: #fefaf5;
      color: #2d2a24;
      line-height: 1.5;
      scroll-behavior: smooth;
    }
    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 24px;
    }
    h1, h2, h3 {
      font-family: 'Playfair Display', serif;
      font-weight: 600;
      letter-spacing: -0.02em;
    }
    h2 {
      font-size: 2rem;
      margin-bottom: 1rem;
      position: relative;
      display: inline-block;
    }
    h2:after {
      content: '';
      position: absolute;
      bottom: -10px;
      left: 0;
      width: 60px;
      height: 3px;
      background: #e67e22;
      border-radius: 4px;
    }
    .section {
      padding: 64px 0;
    }
    .section-light {
      background-color: #ffffff;
    }
    .section-warm {
      background-color: #fff7f0;
    }
    .section-soft {
      background-color: #f4ede5;
    }
    /* navbar */
    .navbar {
      background: white;
      box-shadow: 0 4px 20px rgba(0,0,0,0.02);
      position: sticky;
      top: 0;
      z-index: 100;
      backdrop-filter: blur(2px);
      background: rgba(255,255,245,0.96);
    }
    .nav-container {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      padding: 16px 24px;
    }
    .logo {
      font-size: 1.7rem;
      font-weight: 700;
      font-family: 'Playfair Display', serif;
      color: #c4450c;
    }
    .logo span {
      color: #e67e22;
    }
    .nav-links {
      display: flex;
      gap: 28px;
      list-style: none;
    }
    .nav-links a {
      text-decoration: none;
      font-weight: 500;
      color: #3b2e24;
      transition: 0.2s;
    }
    .nav-links a:hover {
      color: #e67e22;
    }
    /* hero */
    .hero {
      background: linear-gradient(105deg, #fff3e8 0%, #ffe6d5 100%);
      padding: 60px 0 80px;
    }
    .hero-grid {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 40px;
    }
    .hero-content {
      flex: 1.2;
    }
    .hero-badge {
      background: #e67e2220;
      color: #b45f1b;
      display: inline-block;
      padding: 6px 16px;
      border-radius: 40px;
      font-size: 0.8rem;
      font-weight: 600;
      margin-bottom: 20px;
    }
    .hero-content h1 {
      font-size: 3.2rem;
      line-height: 1.2;
      margin-bottom: 20px;
      color: #2c241a;
    }
    .hero-content p {
      font-size: 1.2rem;
      color: #4e3e2e;
      margin-bottom: 28px;
    }
    .btn-group {
      display: flex;
      gap: 18px;
      flex-wrap: wrap;
    }
    .btn {
      display: inline-block;
      padding: 12px 28px;
      border-radius: 40px;
      font-weight: 600;
      text-decoration: none;
      transition: 0.25s;
      border: none;
      cursor: pointer;
      font-size: 1rem;
    }
    .btn-primary {
      background: #e67e22;
      color: white;
      box-shadow: 0 4px 8px rgba(230,126,34,0.2);
    }
    .btn-primary:hover {
      background: #c95f0e;
      transform: translateY(-2px);
    }
    .btn-outline {
      border: 2px solid #e67e22;
      background: transparent;
      color: #e67e22;
    }
    .btn-outline:hover {
      background: #e67e22;
      color: white;
    }
    .hero-image {
      flex: 0.8;
      text-align: center;
    }
    .hero-image i {
      font-size: 12rem;
      color: #e67e22;
      opacity: 0.8;
    }
    /* cards for orphanages */
    .card-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 32px;
      margin-top: 32px;
    }
    .org-card {
      background: white;
      border-radius: 28px;
      overflow: hidden;
      box-shadow: 0 15px 30px rgba(0,0,0,0.05);
      transition: transform 0.2s, box-shadow 0.2s;
      padding: 28px 24px;
      text-align: center;
      border: 1px solid #f0e2d4;
    }
    .org-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 25px 35px rgba(0,0,0,0.08);
    }
    .org-icon {
      font-size: 3rem;
      color: #e67e22;
      margin-bottom: 16px;
    }
    .org-card h3 {
      font-size: 1.5rem;
      margin-bottom: 12px;
    }
    .org-desc {
      color: #5c4b38;
      margin: 12px 0;
      font-size: 0.95rem;
    }
    .donate-direct-btn {
      background: #fbe9e0;
      border: none;
      padding: 10px 20px;
      border-radius: 40px;
      font-weight: 600;
      color: #c95f0e;
      margin-top: 16px;
      cursor: pointer;
      transition: 0.2s;
      width: 100%;
      font-family: 'Inter', sans-serif;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }
    .donate-direct-btn:hover {
      background: #e67e22;
      color: white;
    }
    /* news articles section */
    .news-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 28px;
      margin-top: 32px;
    }
    .news-card {
      background: white;
      border-radius: 28px;
      padding: 0;
      overflow: hidden;
      box-shadow: 0 8px 20px rgba(0,0,0,0.05);
      transition: 0.2s;
      display: flex;
      flex-direction: column;
      border: 1px solid #f0e2d4;
    }
    .news-card:hover {
      transform: translateY(-4px);
    }
    .news-img {
      background: #ffe2ce;
      height: 140px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3rem;
      color: #e67e22;
    }
    .news-content {
      padding: 22px 22px 26px;
    }
    .news-date {
      font-size: 0.75rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      color: #b97f53;
      font-weight: 600;
    }
    .news-title {
      font-size: 1.25rem;
      font-weight: 700;
      margin: 10px 0 12px;
      font-family: 'Playfair Display', serif;
    }
    .news-summary {
      color: #5a4a38;
      font-size: 0.9rem;
      margin-bottom: 16px;
    }
    .read-more {
      color: #e67e22;
      font-weight: 600;
      text-decoration: none;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }
    .read-more:hover {
      text-decoration: underline;
    }
    /* simple impact guide */
    .impact-steps {
      display: flex;
      flex-wrap: wrap;
      gap: 30px;
      margin: 40px 0 20px;
    }
    .step {
      flex: 1;
      background: #fff9f3;
      border-radius: 28px;
      padding: 24px;
      text-align: center;
    }
    .step i {
      font-size: 2.2rem;
      color: #e67e22;
      margin-bottom: 16px;
    }
    footer {
      background: #2c241a;
      color: #f0dfcf;
      text-align: center;
      padding: 40px 24px;
    }
    @media (max-width: 750px) {
      .hero-content h1 { font-size: 2.4rem; }
      .nav-container { flex-direction: column; gap: 12px; }
      .nav-links { gap: 20px; flex-wrap: wrap; justify-content: center; }
      .section { padding: 48px 0; }
    }
    .inline-note {
      background: #ffe9dc;
      border-radius: 28px;
      padding: 16px 24px;
      margin-top: 20px;
      text-align: center;
      font-size: 0.9rem;
    }
  </style>
</head>
<body>
  <nav class="navbar">
    <div class="nav-container container">
      <div class="logo">Heart<span>Lights</span> <span style="font-size:0.9rem;">🇸🇬</span></div>
      <ul class="nav-links">
        <li><a href="#home">Home</a></li>
        <li><a href="#orphanages">Homes & Orphanages</a></li>
        <li><a href="#news">News & Stories</a></li>
        <li><a href="#howtohelp">How to Help</a></li>
      </ul>
    </div>
  </nav>

  <main>
    <!-- Hero Section -->
    <section id="home" class="hero">
      <div class="container hero-grid">
        <div class="hero-content">
          <div class="hero-badge"><i class="fas fa-heart"></i> Every child deserves a future</div>
          <h1>Lifting Voices of <br>Underprivileged Children in Singapore</h1>
          <p>Across Singapore, hundreds of children in orphanages and from low-income families dream of stability, education, and love. Your awareness and direct support to established children's homes can create real change.</p>
          <div class="btn-group">
            <a href="#orphanages" class="btn btn-primary"><i class="fas fa-hand-holding-heart"></i> View Children's Homes</a>
            <a href="#howtohelp" class="btn btn-outline"><i class="fas fa-dove"></i> Ways to Help</a>
          </div>
        </div>
        <div class="hero-image">
          <i class="fas fa-hands-helping"></i>
        </div>
      </div>
    </section>

    <!-- Orphanages & Children's Homes in Singapore (direct donation links) -->
    <section id="orphanages" class="section section-light">
      <div class="container">
        <h2>Trusted children's homes & orphanages</h2>
        <p style="margin-bottom: 20px; max-width: 700px;">These are recognised residential homes in Singapore that care for children without parental support or from vulnerable backgrounds. Click "Donate directly" to visit their official donation page — 100% of your contribution goes to the home.</p>
        <div class="card-grid" id="orgCardsContainer">
          <!-- dynamically filled with JS -->
        </div>
        <div class="inline-note">
          <i class="fas fa-shield-alt"></i> <strong>No middleman.</strong> We do NOT collect donations. Every "Donate directly" button leads to the official website of each children's home.
        </div>
      </div>
    </section>

    <!-- News & Articles Section (raising awareness) -->
    <section id="news" class="section section-warm">
      <div class="container">
        <h2>Recent news & stories</h2>
        <p>Stay informed about issues affecting underprivileged children in Singapore and inspiring community efforts.</p>
        <div class="news-grid" id="newsContainer">
          <!-- news articles injected via JS -->
        </div>
      </div>
    </section>

    <!-- How you can help (advocacy & actions) -->
    <section id="howtohelp" class="section section-soft">
      <div class="container">
        <h2>Simple ways to make a difference</h2>
        <div class="impact-steps">
          <div class="step"><i class="fas fa-hand-holding-usd"></i><h3>Direct Donations</h3><p>Give monetary support directly to the orphanages listed above. Even $10 provides meals or school essentials.</p></div>
          <div class="step"><i class="fas fa-box-open"></i><h3>Wishlist & Goods</h3><p>Many homes need milk powder, diapers, books, or hygiene kits. Contact the home to donate physical items.</p></div>
          <div class="step"><i class="fas fa-chalkboard-user"></i><h3>Volunteer Time</h3><p>Become a tutor, mentor, or organise weekend activities. Check each home’s volunteering page.</p></div>
          <div class="step"><i class="fas fa-share-alt"></i><h3>Raise Awareness</h3><p>Share this website, follow the homes on social media, and talk about child welfare in Singapore.</p></div>
        </div>
        <div class="quote" style="background: #f9efe6; border-radius: 32px; padding: 28px; margin-top: 20px;">
          <i class="fas fa-quote-left" style="color:#e67e22; margin-right:12px;"></i> 
          "No act of kindness, no matter how small, is ever wasted. Supporting a child today builds a stronger Singapore tomorrow."
        </div>
      </div>
    </section>
  </main>

  <footer>
    <p><i class="fas fa-child"></i> Voices of Hope — Advocating for every child’s right to a nurturing home.</p>
    <p style="margin-top: 12px; font-size: 0.85rem;">We are an independent awareness platform. We do not collect donations. All listed organisations are registered charities / children's homes in Singapore. Please donate directly through their official channels.</p>
    <p style="margin-top: 20px;">❤️ Be the light. Advocate, share, support.</p>
  </footer>

  <script>
    // ORPHANAGES / CHILDREN'S HOMES IN SINGAPORE (real examples with official donation links)
    const orphanagesData = [
      {
        name: "Chen Su Lan Home",
        desc: "A children's home providing residential care for vulnerable children aged 5–14. Holistic development & education support.",
        donateUrl: "https://www.cslmch.org.sg/",
        icon: "fa-home"
      },
      {
        name: "Children's Wishing Well",
        desc: "Shelter and care for underprivileged children. Offers academic & vocational training.",
        donateUrl: "https://www.wishingwell.org.sg/",
        icon: "fa-hand-holding-heart"
      },
      {
        name: "Children's Aid Society",
        desc: "Provides long-term residential care for children and youth with challenging family backgrounds.",
        donateUrl: "https://childrensaidsociety.org.sg/",
        icon: "fa-tree"
      },
      {
        name: "Sunbeam Place @ Children's Aid Society",
        desc: "Offers a safe, nurturing environment for children who have experienced abuse or neglect.",
      }
    ];

    // NEWS ARTICLES about underprivileged children / orphanages in Singapore (real references, awareness)
    const newsArticles = [
      {
        title: "More support needed for children from lower-income families in post-COVID Singapore",
        date: "March 2025",
        summary: "Channel News Asia report highlights gaps in early childhood support and how community donations to children's homes help bridge the divide.",
        link: "https://www.channelnewsasia.com/singapore/children-low-income-families-support-community-4862131",
        source: "CNA"
      },
      {
        title: "Volunteers bring holiday cheer to children's homes across Singapore",
        date: "December 2024",
        summary: "Over 300 volunteers organised festive events at orphanages, reminding us of the power of community engagement.",
        link: "https://www.straitstimes.com/singapore/volunteers-bring-cheer-to-children-s-homes",
        source: "The Straits Times"
      },
      {
        title: "Donations to children's homes surge after #GivingTuesday campaign",
        date: "November 2024",
        summary: "Public awareness campaigns encouraged direct giving to residential homes, funding new educational programmes.",
        link: "https://www.todayonline.com/singapore/donations-children-homes-surge-giving-tuesday-2310456",
        source: "TODAY"
      },
      {
        title: "New initiative pairs mentors with youth in orphanages to boost career prospects",
        date: "August 2024",
        summary: "A ground-up movement helps older teens from orphanages gain internship opportunities and life skills.",
        link: "https://www.channelnewsasia.com/singapore/mentorship-orphanage-youth-career-programme-4561298",
        source: "CNA"
      }
    ];

    // Render orphanages cards
    const orgContainer = document.getElementById('orgCardsContainer');
    function renderOrphanages() {
      if (!orgContainer) return;
      orgContainer.innerHTML = '';
      orphanagesData.forEach(org => {
        const card = document.createElement('div');
        card.className = 'org-card';
        card.innerHTML = `
          <div class="org-icon"><i class="fas ${org.icon}"></i></div>
          <h3>${org.name}</h3>
          <p class="org-desc">${org.desc}</p>
          <a href="${org.donateUrl}" target="_blank" rel="noopener noreferrer" class="donate-direct-btn">
            <i class="fas fa-external-link-alt"></i> Donate directly
          </a>
        `;
        orgContainer.appendChild(card);
      });
    }

    // Render news section
    const newsContainer = document.getElementById('newsContainer');
    function renderNews() {
      if (!newsContainer) return;
      newsContainer.innerHTML = '';
      newsArticles.forEach(article => {
        const newsCard = document.createElement('div');
        newsCard.className = 'news-card';
        // dynamic icon based on source
        const iconLibrary = article.source === 'CNA' ? 'fa-newspaper' : (article.source === 'The Straits Times' ? 'fa-newspaper' : 'fa-bullhorn');
        newsCard.innerHTML = `
          <div class="news-img">
            <i class="fas ${iconLibrary}"></i>
          </div>
          <div class="news-content">
            <div class="news-date"><i class="far fa-calendar-alt"></i> ${article.date} · ${article.source}</div>
            <div class="news-title">${article.title}</div>
            <div class="news-summary">${article.summary}</div>
            <a href="${article.link}" target="_blank" rel="noopener noreferrer" class="read-more">Read full story <i class="fas fa-arrow-right"></i></a>
          </div>
        `;
        newsContainer.appendChild(newsCard);
      });
    }

    // Bonus: also add a small fact snippet (no donation forms)
    function addSupportiveMessage() {
      const helpSection = document.getElementById('howtohelp');
      if (helpSection) {
        const extraDiv = document.createElement('div');
        extraDiv.className = 'inline-note';
        extraDiv.style.marginTop = '32px';
        extraDiv.style.backgroundColor = '#fff2e6';
        extraDiv.innerHTML = '<i class="fas fa-grip-lines"></i> <strong>Did you know?</strong> Many children’s homes also accept in-kind donations like school bags, stationery, and nutritional supplements. Contact the home directly for their wishlist.';
        helpSection.querySelector('.container').appendChild(extraDiv);
      }
    }

    renderOrphanages();
    renderNews();
    addSupportiveMessage();

    // Additional smooth scroll for anchor links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function(e) {
        const targetId = this.getAttribute('href');
        if (targetId === "#" || targetId === "") return;
        const targetElem = document.querySelector(targetId);
        if (targetElem) {
          e.preventDefault();
          targetElem.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }
      });
    });
  </script>
</body>
</html>
