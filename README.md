<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>مريم أشرف عبدالسميع | Front-End Developer & Marketer</title>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  
  :root {
    --primary: #a855f7;
    --primary-dark: #9333ea;
    --accent: #ec4899;
    --dark: #0f172a;
    --darker: #020617;
    --light: #f8fafc;
    --gray: #94a3b8;
    --card: #1e293b;
    --success: #10b981;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Cairo', sans-serif;
    background: var(--darker);
    color: var(--light);
    overflow-x: hidden;
    line-height: 1.7;
  }

  /* ===== شريط التنقل ===== */
  nav {
    position: fixed;
    top: 0; right: 0; left: 0;
    padding: 1.2rem 5%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    z-index: 1000;
    transition: 0.3s;
    backdrop-filter: blur(10px);
  }
  nav.scrolled {
    background: rgba(2, 6, 23, 0.9);
    box-shadow: 0 4px 30px rgba(0,0,0,0.3);
    padding: 0.8rem 5%;
  }
  .logo {
    font-size: 1.6rem;
    font-weight: 900;
    background: linear-gradient(135deg, var(--primary), var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }
  .nav-links a {
    color: var(--light);
    text-decoration: none;
    font-weight: 600;
    position: relative;
    transition: 0.3s;
  }
  .nav-links a::after {
    content: '';
    position: absolute;
    bottom: -5px; right: 0;
    width: 0; height: 2px;
    background: linear-gradient(90deg, var(--primary), var(--accent));
    transition: 0.3s;
  }
  .nav-links a:hover::after { width: 100%; }
  .nav-links a:hover { color: var(--primary); }

  .menu-toggle {
    display: none;
    font-size: 1.8rem;
    background: none;
    border: none;
    color: var(--light);
    cursor: pointer;
  }

  /* ===== قسم الهيرو ===== */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0 5%;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute;
    width: 500px; height: 500px;
    background: radial-gradient(circle, rgba(168,85,247,0.3), transparent 70%);
    top: -100px; left: -100px;
    border-radius: 50%;
    animation: float 8s ease-in-out infinite;
  }
  .hero::after {
    content: '';
    position: absolute;
    width: 400px; height: 400px;
    background: radial-gradient(circle, rgba(236,72,153,0.25), transparent 70%);
    bottom: -50px; right: -50px;
    border-radius: 50%;
    animation: float 10s ease-in-out infinite reverse;
  }
  @keyframes float {
    0%, 100% { transform: translate(0, 0); }
    50% { transform: translate(30px, -30px); }
  }

  .hero-content {
    text-align: center;
    z-index: 2;
    max-width: 850px;
  }
  .hero-badge {
    display: inline-block;
    padding: 0.5rem 1.2rem;
    background: rgba(168,85,247,0.15);
    border: 1px solid rgba(168,85,247,0.4);
    border-radius: 50px;
    color: var(--primary);
    font-size: 0.9rem;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.8s ease;
  }
  .hero h1 {
    font-size: clamp(2rem, 5vw, 3.5rem);
    font-weight: 900;
    line-height: 1.25;
    margin-bottom: 1rem;
    animation: fadeUp 0.8s ease 0.2s backwards;
  }
  .hero h1 span {
    background: linear-gradient(135deg, var(--primary), var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .hero .tagline {
    font-size: 1.3rem;
    color: var(--primary);
    font-weight: 700;
    margin-bottom: 0.8rem;
    animation: fadeUp 0.8s ease 0.3s backwards;
  }
  .hero p {
    font-size: 1.15rem;
    color: var(--gray);
    margin-bottom: 2.5rem;
    animation: fadeUp 0.8s ease 0.4s backwards;
  }
  .hero-btns {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
    animation: fadeUp 0.8s ease 0.6s backwards;
  }
  .btn {
    padding: 0.9rem 2rem;
    border-radius: 50px;
    text-decoration: none;
    font-weight: 700;
    font-size: 1rem;
    transition: 0.3s;
    cursor: pointer;
    border: none;
    font-family: inherit;
    display: inline-block;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--primary), var(--accent));
    color: white;
    box-shadow: 0 10px 30px rgba(168,85,247,0.4);
  }
  .btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 15px 40px rgba(168,85,247,0.6);
  }
  .btn-outline {
    background: transparent;
    color: var(--light);
    border: 2px solid var(--primary);
  }
  .btn-outline:hover {
    background: var(--primary);
    transform: translateY(-3px);
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ===== الأقسام العامة ===== */
  section { padding: 6rem 5%; }
  .section-title {
    text-align: center;
    margin-bottom: 4rem;
  }
  .section-title h2 {
    font-size: clamp(1.8rem, 4vw, 2.8rem);
    font-weight: 900;
    margin-bottom: 0.5rem;
  }
  .section-title h2 span {
    background: linear-gradient(135deg, var(--primary), var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .section-title p { color: var(--gray); }

  /* ===== نبذة عني ===== */
  .about-content {
    max-width: 1000px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1.5fr;
    gap: 3rem;
    align-items: center;
  }
  
  /* تنسيق الصورة الشخصية */
  .about-img-container {
    display: flex;
    justify-content: center;
  }
  .about-img {
    width: 100%;
    max-width: 320px;
    aspect-ratio: 1;
    border-radius: 50%;
    object-fit: cover;
    object-position: center;
    border: 5px solid var(--dark);
    box-shadow: 0 0 0 5px var(--primary), 0 20px 40px rgba(168,85,247,0.4);
    transition: 0.4s;
  }
  .about-img:hover {
    transform: scale(1.03);
    box-shadow: 0 0 0 5px var(--accent), 0 20px 50px rgba(236,72,153,0.5);
  }

  .about-text h3 {
    font-size: 1.8rem;
    margin-bottom: 1rem;
  }
  .about-text p {
    color: var(--gray);
    margin-bottom: 1.5rem;
  }

  /* تنسيق المهارات المحدث */
  .skills-container {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }
  .skill-category {
    background: rgba(255, 255, 255, 0.02);
    padding: 1.2rem;
    border-radius: 15px;
    border: 1px solid rgba(255, 255, 255, 0.05);
  }
  .skill-category h4 {
    font-size: 1.1rem;
    margin-bottom: 1rem;
    color: var(--light);
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  .skills-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.7rem;
  }
  .skill-tag {
    padding: 0.4rem 1rem;
    border-radius: 50px;
    font-size: 0.85rem;
    transition: 0.3s;
  }
  /* مهارات البرمجة */
  .skill-tag.dev {
    background: rgba(168,85,247,0.1);
    border: 1px solid rgba(168,85,247,0.3);
    color: var(--primary);
  }
  .skill-tag.dev:hover {
    background: var(--primary);
    color: white;
    transform: translateY(-3px);
  }
  /* مهارات التسويق */
  .skill-tag.marketing {
    background: rgba(16,185,129,0.1);
    border: 1px solid rgba(16,185,129,0.3);
    color: var(--success);
  }
  .skill-tag.marketing:hover {
    background: var(--success);
    color: white;
    transform: translateY(-3px);
  }

  /* ===== الخدمات ===== */
  .services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
    max-width: 1100px;
    margin: 0 auto;
  }
  .service-card {
    background: var(--card);
    padding: 2.5rem 2rem;
    border-radius: 20px;
    border: 1px solid rgba(255,255,255,0.05);
    transition: 0.4s;
    position: relative;
    overflow: hidden;
  }
  .service-card::before {
    content: '';
    position: absolute;
    top: 0; right: 0;
    width: 100%; height: 3px;
    background: linear-gradient(90deg, var(--primary), var(--accent));
    transform: scaleX(0);
    transform-origin: right;
    transition: 0.4s;
  }
  .service-card:hover::before { transform: scaleX(1); }
  .service-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 20px 50px rgba(0,0,0,0.4);
  }
  .service-icon {
    font-size: 3rem;
    margin-bottom: 1rem;
    display: block;
  }
  .service-card h3 {
    font-size: 1.4rem;
    margin-bottom: 0.8rem;
  }
  .service-card p {
    color: var(--gray);
    font-size: 0.95rem;
  }

  /* ===== الأعمال ===== */
  .works-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    max-width: 1100px;
    margin: 0 auto;
  }
  .work-card {
    border-radius: 20px;
    overflow: hidden;
    position: relative;
    aspect-ratio: 4/3;
    cursor: pointer;
    transition: 0.4s;
  }
  .work-card:hover { transform: scale(1.03); }
  .work-img {
    width: 100%; height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 5rem;
    transition: 0.4s;
  }
  .work-card:nth-child(1) .work-img { background: linear-gradient(135deg, #a855f7, #8b5cf6); }
  .work-card:nth-child(2) .work-img { background: linear-gradient(135deg, #ec4899, #f43f5e); }
  .work-card:nth-child(3) .work-img { background: linear-gradient(135deg, #06b6d4, #0ea5e9); }
  .work-card:nth-child(4) .work-img { background: linear-gradient(135deg, #f59e0b, #ef4444); }
  .work-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(2,6,23,0.95), transparent);
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 1.5rem;
    opacity: 0;
    transition: 0.4s;
  }
  .work-card:hover .work-overlay { opacity: 1; }
  .work-overlay h3 { font-size: 1.3rem; margin-bottom: 0.3rem; }
  .work-overlay p { color: var(--gray); font-size: 0.9rem; }

  /* ===== تواصل ===== */
  .contact-grid {
    max-width: 900px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
  }
  .contact-card {
    background: var(--card);
    padding: 2rem;
    border-radius: 20px;
    text-align: center;
    text-decoration: none;
    color: var(--light);
    transition: 0.4s;
    border: 1px solid rgba(255,255,255,0.05);
    word-break: break-word;
  }
  .contact-card:hover {
    transform: translateY(-8px);
    border-color: var(--primary);
    box-shadow: 0 20px 40px rgba(168,85,247,0.2);
  }
  .contact-card .icon {
    font-size: 2.5rem;
    margin-bottom: 1rem;
    display: block;
  }
  .contact-card h4 { margin-bottom: 0.3rem; }
  .contact-card p { color: var(--gray); font-size: 0.9rem; }

  /* ===== الفوتر ===== */
  footer {
    text-align: center;
    padding: 2rem 5%;
    border-top: 1px solid rgba(255,255,255,0.05);
    color: var(--gray);
    font-size: 0.9rem;
  }
  footer span {
    background: linear-gradient(135deg, var(--primary), var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    font-weight: 700;
  }

  /* ===== الموبايل ===== */
  @media (max-width: 768px) {
    .menu-toggle { display: block; }
    .nav-links {
      position: fixed;
      top: 0; right: -100%;
      width: 70%; height: 100vh;
      background: var(--darker);
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: 2.5rem;
      transition: 0.4s;
      box-shadow: -10px 0 40px rgba(0,0,0,0.5);
    }
    .nav-links.active { right: 0; }
    .about-content { grid-template-columns: 1fr; text-align: center; }
    .about-img-container { margin-bottom: 2rem; }
    .skills-list { justify-content: center; }
    section { padding: 4rem 5%; }
  }
</style>
</head>
<body>

<!-- شريط التنقل -->
<nav id="navbar">
  <div class="logo">Maryam.</div>
  <ul class="nav-links" id="navLinks">
    <li><a href="#home">الرئيسية</a></li>
    <li><a href="#about">نبذة عني</a></li>
    <li><a href="#services">الخدمات</a></li>
    <li><a href="#works">الأعمال</a></li>
    <li><a href="#contact">تواصل</a></li>
  </ul>
  <button class="menu-toggle" id="menuToggle">☰</button>
</nav>

<!-- الهيرو -->
<section class="hero" id="home">
  <div class="hero-content">
    <span class="hero-badge">👋 أهلاً بك في ملفي الشخصي</span>
    <h1>أنا <span>مريم أشرف عبدالسميع</span></h1>
    <div class="tagline">Front-End Developer & Digital Marketer 💻📈</div>
    <p>أدمج بين قوة البرمجة وإبداع التسويق لصناعة واجهات مستخدم احترافية وبناء حضور رقمي مميز.</p>
    <div class="hero-btns">
      <a href="#works" class="btn btn-primary">شاهد أعمالي</a>
      <a href="#contact" class="btn btn-outline">تواصل معي</a>
    </div>
  </div>
</section>

<!-- نبذة عني -->
<section id="about">
  <div class="section-title">
    <h2>نبذة <span>عني</span></h2>
    <p>تعرّفي على قصتي ومهاراتي</p>
  </div>
  <div class="about-content">
    <div class="about-img-container">
      <!-- الصورة مدمجة هنا مباشرة (Base64) -->
      <img src="data:image/jpeg;base64,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SgDgBdogJP1xQQy98stCdSiN0NsxWW5jrKgmIzwjAE3ghwxTgRjyQCiYxYgqyChBDCKU0Vs3SRR5oQ3NRC4D8bfgiwAMGizThQQyoAQTjKtjCL7yDQSFL0kPpOR1PDN04CQEGXIKkFgzQcEzywADhCrSyx74f1Z3gxArCapk32H+Q078suqgijXdo5SzSrjPIwAQzwgQ6JBx/JX/AAbgsMkKsNzrh1UBszoxD/EN8LHflA41agxAIw8+U6gm3YAr67DU2SkCOvMTEELiDS5QXRuoCSvrf51FzwISp+sw8YQWAHrpADD3DgZsAo8eWFhNxkVeo0Nn90+rj8xnbhxsI61y08og8Yo7dgAH5Tsx/O9GMiTP1dlwTf3b5AEYvDfNlXuKwE8n1CwsA4IE8WBUAjrhy+SgYCUYZ8sYci1pEUIEiKXz/wC+54cPGPKagoFJDIHGOrStHk+KvQhllwti2BHBGUFwcAnLto4U8ycKPALuG8g1CMIAEAPu3iBo8OGQD7/IUKHkvIEpWfBHIto6WIBINkiHOMH6gbKNMNPANg4rilWQ0aagsyk57wt3ssC0TfrWo3+orycBETDD6BMmIGIJCGMk9opx9BDf7mbRr68w4IMfjkKMW0DIKHHNDrJkC5bGvgGEjMONoy7fr+kck9x5YRBCLIPzOLHFHTSSpEHMDspsI3ze9xMogpmKItwVC4ySXQTSVUOFdTZ8TJOKH5dCorJwFPHPiC33GHlVAApsiIGemLWcVKvrkjIlGKkuFPILALBEBONiTUEANtI/8NwUhkDQHHgo/wD1xzx52L0IIIJwDyMCD6KKFz1x3z/xz5yCOGP6J6Jx50D/xAAC/9oADAMBAAIAAwAAABD88/sVUU888sNL+Nf323333333233333303333333vrNr7/wB999v7Xzt9/wD/AN898u89/wB99999999999999/8Aff8A3333yLb47773331Jb/7f/wD3vzfymr77d99999999999999DT919998iSC+++++999CS/wDv67/v/wD+7v8A/wBfffffffffffffc4w0w/4+fbQggkvvjgkvf4ghv2mv+w8892vxffffffffffffXfQ05314yw4qgCgrigslnvvvggvuikpny7/+993dffffffffffff2R363ywwgggAjvqgjgoggvv/AJqob/8Aj/7DDF999d999999791597T99jLDDCCASSyiC+uCCC++/wDv/wDfcsd1MV33333k33Wndn3mF3d3/s+N0cI45K46qJL6oIIrb77/AL//AD8ww9/fffeQoUefy0YYRcn5jCuMO+ywjDEMsgggvogv1vv/APe/v8otNX33331x/ecfU13f9v8A/wCnvTOGVg/fPlvnngsnvv4ov3/+/wDeusX33332EHif/vNTTjcY7Tz2hKU6LL777476oIIb78pf+/8A/wD4l83dffffQVV42e6heyCoe4sK1PkpBAhltrvMgjgggv8A/wD73/fvrzLzP9999Jj/AG/Qe9WU2qb9wBeS9jRSBkstPgnvkggv/wB/v++b/sN3v33339QMP8U+f1+d8V+MTypnn9H76opLapLIIY7u/wD/AP8Av/8A/d/d9999NbLj/wC2xS9v91Xa/oxUF5aXtrgggvunigsr35/5t/33v/ffXbfWtNa0bWJymIJNn+YVv/KTeMsogglvvvqggO//AP8A/wD+/wD/AN99999iaU0jUyfFKuMAKif5O1fPRtuiiCCKC+uCiOv7/wDfx/8A/wD/AP8AX331PG31CryqOsAkUu5Ksch1jhXoZ+8oIIpZooL/AP8A3/8AduH+03333l/XWkURR3qMht87bKHGEZdcEtP38MIJ7qIIL/8Avxx//wBf1fffff8AkmnMFrXjG8OhdJNovlX6MamkIvKMIIY4oIL/ALP/APwUf+f9fffffRdluiQeBzUPCwNZTw7LwAuXQ41zwnusoggv77/84a0f/f8A3332X2vcWkWWCI3KyZxTZ9m/WX0GMdfMOLIIII7/AP37BPp/x9/5199ouBr/ABtceGD7g1vHN4FBEWq3awwwzwggvggv6/8A/wB/hvv5/wCTbUV6uNR+aeIWpaP6hn9lcc7JZZDzw3+x6ggmsv8A/wDp/wCb9fXfTYRDB3GfnoZy9zc9KbAxwM7gNGJVnf78lqowkogv/wC/3021nn0EVuYNofwO4hG38Cwrz0qGoTVqXWzqnv8Af/8A7jgggP8Af+/33kG3FGUFLgzOvTWJKFDfCJ8Gy6MMjDftW/Q/f/8A/wDsoqjv/wD/AF95B/iFxAWRymxnHfx2bToWv0fAHYjFEHQ4O59b/wD/AP74777+t/f+3v8ABSNAqMYFH3f6nA690lFBIMAMY5XC5GtBW2r/AP8A77/77/8A/wD/APfsU1AREsMlPd+ADRjqhZ6J3iYFDrGJNZJoImf3n/8A++++/wD/APv/AP8AwxrZ4aKc7l70OjTRm3QtaH5RLJj5c4nBfoxqvr/f/wCrL/8A/wD/APlCzkt3oXwH6kG2NTKJi4N2++Z0cZbmH37oM3KB+ftGNPL/APfv/nH95lMz47a+oxJdf33zGj7j8SBnV+155j/I0Pl/VlDlLA/3/wD7FBqOSQzq5iUyzQaiVmhxLHgMVUHmlzX/AMW179s79908/E1f/wDg4Nip1VIKTl11VFtpWNlfb/dYJ2LozR3nlJrUoEhRKptyd9/fmybQScjQoXN1rfHFhI3dddvozBoHUW1CutTV15D+IVfrDxR97/nXDyvFvXt9t59zVrkgrXbVDTzWG4n0b6dXjpYehpMBrVztSA/639b/AFAFZF/wbXV3Z20QTwUv0RtoGAVmYd3B71ExcPUS4r8Xc/6n9/57S2w6YXXdXbQxTRSzIhKAR/8AtYJH4QQFEXMMn1Y79eUr3uH98f7ZlVclUnk8cUd8LeGtuAb/AAXOL3t8+tVeeJp5dFov7l0z/hLvrhEDZ5J9N1BTPow33flXTsK6Mf8A7XQ8fZZwkv7xe5rV+fDv6paXXEdYJWbZU5x15hbBBdxwpOkuL0TraZNeUtfy5V7+S6nxAWzV39f7SWBfdXf9RNaUrUL8nDJ/qJCvZwAV1z50I3Ws7xHPVzw08yWO3SSQX3Sd4dfaJwFuMSORBmVgQrvsS8c8KLPK3awxr7gi8x/0v/Qb94XaTed+29OCULOwD/zqn9zZfoBqoVQJBVb3xNI8Hkz8+Rf41HGWzQrK0LzrziU/F2AF2fUiBkslx4KeU9/P+lf/AHt0WHIeFN8ffXGm1c3KR6JA9F+MHYSXWQPobvofvlNfafU23fPuDldXAv8AHLv5Fxp5x5nFXNYCPrN4zwFDoBz1dBXg1HhiN65l9HfYpM394Df7HXFRltpBndKtyhKZ/Fk78liXatokXJbATgKIyjL79FIqVwXrCPfuLhnZFr89vFzknd/79l3fxj6hB7Uu6e7OzIiU7Q8Eoa8Nra3HuH/NbL9RPX1XX7FpltVNxN6lMxuOX+ETRHDSKleN4cIrGzHqnrz/AL696wVY0908S0TZTae4XHEkk36IrHsiBCW65Bl5dJDgDdy0g0x3++9x9/1wITDY08yTNV5I2BpMqhRVMQWWq3SFEPLtE6Mqohw9m8z3737N3p6xw27z/wBUXTLH6vG0OUoN28jYkmnWT59jHL0b/vC9A8dKJ9jX4HFt0lmXp/Pms6keM/TSJv8Ax4ht5HBv12RPizn3DvTk7GQT3EokNO2xtXLpa70oY09AbjZ+ADgVFUfPdvvnhvIPb33m6LyWKPL8+kmhVNKXBIwEaAhrFcWSWvXf9HNn7hO0G15EaPPvznvvGn49BMLKuhRfDrmtpFPH0nUYuTv6kE5R15xFTspdBcB9/nWHTzn9oHRrl333FtJJSPQ3LXH6SQNi5mo4d7d5/So0pnpmbxHbR/ZO9JC7tbZ8SSRqgc5OTpZb6Z8OZk+4Q/nYsEgumZkSwGdBOeF3nZBLURNFBEKxSx9EFIA7/wBVBOyzxirFMaTEAY+qu6gEN1/654aHfFbTMLWvW4jxXWRpwojt98h5Pc2Y6T/qIXTTTzcz8vA6fV6T2acb/sUc9tI0X9z9qX8uVRDh7KjhzfyNIwZSb1zc6dWKMDwcK3ZeePGEb19FY+PlPbfzBJD1qYdRNW2uIka3aYVd42bZW7fmcWAfzVxFixvhn/SUWf8AWdUyKcnEPNkWDLJJpk1izUdPEr/oqWVUz8N/55wKN94CEJ38KH0OOOPz/wDfdA9cBjhifdihfiBed9h9D/cB/8QAPBEAAQQABAUCAwcEAQMEAwAAAQACAxEEECExBRIgQVETYSIwcTJAQlKBkbEjYnKhFCRQwTM0YIJTc9H/2gAIAQIBAT8A+VpaH30ZaXlfzryr7qfvNf8AaD9z7fcb+40f+xHoKr/tAzH/AMCP/wAHAs0vS916XuvS916XuvS2+JekPzIxf3L0v7l6fuvTPkL03ey9N3svTcix/hSWxpcWnTwLTfiaHNFgiwVyu8H5Z+7RDc/MvK1ZWANYVrfyuc39nEK1IRt0110fugFadVKlSNhWRuFee+WENPxTPExcP/uLRNK716N/vcQ+K+oDoIRCpVWdplNx0w/NEw/sSE919Iyv7kVp1MFNrppDqpHoxeJjhxsJLwG8ha7yLQIIu/nf/b7iwEuz3NdAyGRzIzJAXEo3/wDKe90ZLasFYLmGEg5t+QI5D7pfyGCgTmM6yGd9Bye5cSbcLT4P8ilw93NhIvYV94PyLyG2b54m907F+Go4mXzS9eT85XrSfmKE8l/aKGJk9k3FDu1Ne1wsHImhlxe/TjF9yuDyVzxnxYH3G+k/IYNegbJ8jWfVOkL/ALR08Kh4XIPNJ4A2N5XY0QzBIqlHiK0cP1UlXfbLig/psPuVw9/JiWE9zX7/AHe+topo6JJORvudk99DXW1zFAlWrQKrLUnIK0x9ZcSH9Af5Jji2RnsUw8zWnyMzlf3dosjKs5HW8+Anut3RylFtd0HUrtDpjfS4kLwkhHaihoSsC/mwzNdrGQzHy7+YCQbC53eVzFcxXOVdtcfdHMDRc9bKnvKOitA2rzHjLFfHg5h35UDQFrhMlse36Hqr5d/OKLgNyt2urNotOdQUEfO4kovITyScgayGVbHJ+sT2+WlWTS4c708Q0eQR9yORy1v5MkrWfVOeXmyozYPuiEAmkWjqSCmvLRonOKGpQboqTFtkcqT6EjwDQsrDktlYW7cyaeZoOQ+4X8t8/Zn7rlPdEJpXKCQU6RuwVOIJormK1RQRdoimodOKHLiX/wCSYSKcFA62Ejz/ADrkPuFZVmehzg0WU97nmu3hAIkLU901tFXbaBUcXcp7iFsSECrvSlym1RyagUMigse3/qPqAmk3SwLrgb9Mh9wv5EkoZpuUXOedSgroK+Y7qkNCFsi91JzkUQuUZcwzsoHo4jQkYfZAHUn2XDJWkPb3B/lD5x+VLLy6D7SAtbBXqimjJwy5SjoSMgi4BErfIhWmnox2HmkktjPhAHdDBTuoloaNVhOHysk9Rzw36fMsZD5U0vp6d1q4kk5FBNw7juQEIG/mKbE0ItCdo5OKkjJ1GQysWhk45BN1y0pFFRE8xHzr6qz5eVpcewRJcbO6Azijqj36XCxStBFgcEY3BG1QQRIyA8oWU0ouXMgbVFNcWoS+QmuB+aOtjK1KxBqFyAzhjJ+I7Drkb3GVoJzGk6Ck6I9lqmhxTYgN1yhVpXRrkXIkrXymSkaOQNi/nnKAh45xt2OWLP8ASryUfbKKMvPsmSh7nNbXK3RX1vYBqM+UrlJRaR1UrCtV5QATInv1pf8AH0uwnY1gJAaSPKw3rSs52t5QdrO6Af3afl10CZ2NxfoMNQt1efzIAAADYZYs6MaiooXPJ7AblY3ECFgYzRzlgL9N/wBcggCdghGUWkLlJRbygk6AKbHMuoxze5UTw8XkVdK8uZX0AJrHmqH0TcOe5TYWCtLKseFj5vTwz6NE/D+6gjMszGD8RATWhjQ0bAIIgHcLkYU5pB+XxWf0MNyA/HJp+i4Jh+TDGQ7vOh9hkViTcn0ChgLzZ2U8rIIiTsOyfI+WQvduVh4vShYO+5yY21emdrH471nljT8AP7lYWB07wBoBuUII2MDGigiCFeVonO8pMRGz3KwnrYg8x+Fg/wBoChkTlxiQARMvySuERh+Jc78rf5RytBFPb3HyY29yuKz+rjZB2b8I/RYRnp4WBvhgyJ87KOIyvLyKbaJbGwkkBoCxeKM8hP4R9lcPwxll53fYb/sp4TWlxW2lLZXlxLE+lFyA05/8KKMyvaxu5Kw8DIYgxv75StvVHo3XK7wUIXFYzExw/wBOPV/d3hYPCvxDuY6MG58qNjWNDWigO3TxKQPxb/7QAuDM5YpX+XV+2QCIQ2RQ1FJwo1lr46WNsp5ppPhPcXSEk7uJ/dN+yAPCKq7Q0XEcZzu9Fh0G58lQwvme1jdyoImwsDANkRaaKCrW8gnGgSTosXN60r3nvsPAXC8NytMrhq7QfRVkGp0TXdlOBEwu7DsoZhNIGNBsr0ADqUAG7ZYvE+jEXfiOjVhsO7FTUTpu4qONjGhrRQHQETQJUji+R7z+IkrhzOXCR+9nM75FNUosA5a+elooALFEjDTf/rd/CYLOgsqM3Ewju0Zd6XEMX6Q9Nh+IjX2CAcSK1vYLBYUYdlkfG7c5HshmFxOcR4flB1eaWGidiJgwChepTWhoAaKoKlWVri0vKxjO5NrhDOZ8j/AoJ2hzxUxnmPgaNWBw4hgaK+Ii3dWNfyYWZ39v8oKFvLFGPDQm9BOmRF2OpjK1O+WKF4aYeY3fwo2mjQWFdzYWA+WNRNLFYkYeMnTmOytz7JNm1w3CctTPFk/ZzPbI58Vn5sVyjZgr9VwiCo3SndxofQZDK8sfL6mJd4b8I/RcNi9PCs01d8RT9suIzmKHkaac/wDhcPh9XECxo34j0Vnxd9YdrfzPCjZcjB5cMrzK3zeKceiNl6nN45mOHkEJ7xoxqwJrBYe/yBSysjifI86BTTPnkc936eywGFMx5nD4G/7PVuBk5waC49hae500xP4nO/lQRCKJjBs0AdOJmEMMj/A0UDDNOxh/E7VAAABPRWLn9Wdzu2wXDIPSw/Md369fGpKdC36lYD48XCK/F0lAUM5RqDmBZC0GmZWHhZNi44zer/i/RPaAwBo0C4qagY3y9YWB00nKP1PgKNjI2NY0UAOg9HEZTHg5D3Pw/uuGQ8+LZY0b8WZytcXn+JkIP9xXCINXy1/a3Jyx83pQEA/E/QLCQ+vOxlaXZ+gQAAoZDp4s7mxhb+UALhEd4thI2BRQHXKPh+hzi1f0SO5I3u8NJWDfy4zDkfnH+07YriLzJPHG3do/2VhMOIIg3d51cencnIorjDxyxx33tcGiqOSXyaH6dL3tYxznbAWVJI6aZzju47LDQiGBjPA1+uROgWPm9Wc0fhboFwmDlidKd37fQdegWMPNjMQT+dcJFzyHwzorpI+E5w/aP06OIu5cFOfLa/dQv5Z4T4e3+Vi8SIIi7vsAuHwPszyaudsq6e+bvsriL+bFO9gAsFGI8LC3+2/316eMTlsTYgdXn/QXC8P6uIBI0ZrkdAsVJ6UD3XrsPqVHG572sbuSAo2NjY1rdgKB6KzKlozyny8rhLa9Q+yv5PJ75QjUno4mwyYKYewP7JjLcsLhZpy1+IJ5R9kHugB1VorQKcaY4nYCymNM+Kr870NBXQVjpRNiXuuwDQ+gXCouTDB1avN5FcScHOZGO2pXDoB64d+UWhmOh1UUxpc41uSuHt5GSJt1rkBqOusozXQ6iCFBw7DRPLw0k9rVdTtkNl3yxryzDSEbkUuFx8+LB7NBPRSxMnpQSP8ADSmjmIAG5oKNoYxjBs0AZd1OQ6eQ+9ftosC0f1He9LspsQWvEMdGUi/Zo8lOHIxpMznSE0NaF/RYmV7pGQxuIO7iPHhAU0C7ob5zaRP/AMSog0NBWCNxuI2JyG+ZyHSDRtNcDkTSrz8h24ycEFxN39JjPLlweOvWd9Ah0cWfWGDfzOH+lw5pkxcQPY3m4hrSfAULi5oJ72Vg21CPclTSCON7z2Frh0f9N05+3IbJThh4eaQgAm1C5zGiQi5ZjbAewUc0nrOaZbZGLeaG57BQzudNiC8n4S0NZ9R/Kwkj3iQvdbvUIrtp4WJNQSn+0qV7u10uGD/pgT3JyGRzrIqxmDRWpVdI6DvkVoDZXEtXRhcLFYd3u89PFRzOjb7ErhjB673eGVnincuGlP8AaUyQLDCoY/8AELExerC9l1YWHOIjibG6H4mirsUU/D+qxwkdZcK07fRHBsLo3+o8OaCL8goYGMNdTnVzcwHgpuBAPOJHepzcxcVBhmQg0SSSSXHc2sa6sNKfZPlZWgWBFYWL3FoIZHM5HI5MbZvKlRC1CtDp7q1acLWPNzD2auHisKw+b6eIuvEewaFwsACZ3kgZ8R/9pIPNKON3YFMFMZ9BlWVgKF5nmLrIY0/DkVxJxGDlP0/lWXOsqBobFG3wwLfoGRQRzAN6ICgK6qCpWQuYKwi4BF6slWsZriHfQLBisNEP7egrHFzsXJ4FBcOoQE+XK8seR6IB/MmzxghrShs3PEySGVkLDV6ud4CM9tljYTT3hke/YalYdkbIw2MfCNPrkSuLGsIR5cFh4vUmjYO7lVABDbOvkRt05v2+VS5QuQLlA7ZFqxI/rSDwVBpDH/iEMrynJM8pv8Z0WDbUDB7ZHcLjHMYY2tuy5QQSNlZY3cOiWOI2942af2TImYjEF/L/AE2N5WDYE90AAKGfGHVDGP71wtgMr3gVyt/lDfqPR8Ka3mNfNPRiXn/kSf5FRj+kz/EIIZFP15vqohyxsHhoTdXBHcLiJr0v1UWs8Q7cwWtJ75nve2Itbybki7Kw+K54HySUOU05PxUrYRO5jfTNWz8VHunS8vpxxNaS4WBsAPKgxUjppIJWgPaLFbEJ+MxAcS3COcyzTrqwsNK6aMPLOW9lxh3/AKI+q4U0CKR3l1Zgq8rV5nJjaHzCcyipQDI4+XFNADG/TonPLDIfDSm/EQ293BBM3K/EuJ1zxewKwfxYmL65TSEWxgt7h+g9ysRE2DCNYNS5/wARXEOUYXk8loCtkETC78LQPdYWB/qyTv0e/YflCmf6sogbtXM/6eP1TaGi4k10mIiY0WS1YaBuHiDR9SfdWq1VZ3mEVr46T1hOV5v0C5vUmZ/kMxljncuGkWH+KeP6oBM7ruVxG3TNHhqwLKxDPGqPetEMHiWklmLIJNm2p+EMmHbGX/ENQd7K9CSWSOSUim/ZaPPkqbD4x83qMkYBs0HWgsO3EBrjM9pcTpWwCw0EkbpnyEFz32K8I0mxNExl78oH0RNmkCrWuVdJVnx1nII5u26JzUUh8NKwzf8AqIr7uHTxZ9YWvLgFw0XPfhpTdk1AaLHuP/LIHYBYAXP9GnMp0jGi3OAHugbA136HuXLogAFXZDInpdt8odBQ3zxxLcM/yaCwDS/FQi9BZ6eLAmOJvly4awB0jvoEBohlidcZL9Vw6jK72agpHvawljC4+AsVxXGAloZ6X1GqMr53XLMfqbKhmxEVCGcfTm//AKsLjsVKS1+HJr8TdleVKlWZICPS75JQyOZq0MuKPpsTPJJXCoamkf4bWZy4u/8Aqwt8NJ/dcPb/AEOY/icUM5W/15XHayuGcjpJK8BY6Qsw7q5hYoOA2Kws5laS4VRFe48ri7pgyJscZdZJPw2i+E/bjLT35Tv+htYczOlj9KD4eYWav/ZUEkbzPy/hfR/QBf8AIfJiIxRprnUB3B2KvVA/KKOpC5vkFDMoJwzx8nNiS29hS4c2oC78zszlxEh+KcfygBYZtRsHt/KIyBTyx0r2HfmK4ZEWPlvwFKwSRubZHuDRUMjop2in85cA7nFfDqopmTMa9hsEWFJhsPK4OfE1xGxIWjQBoAudjecYdpPM8GQjvvYWBgcwczg8dgHHsiHKgENeoDoGpyPWUMygiu6cQ1pJ2AtPe573vFcxcsPGWQsadw0dBT7mxF9nv1TMqVKYVI5/gkhcJkc8TOcfCtYnDiYAhz2uHh1Aoh8MjS5hYGgtsHcf+SsNiSIWeqTznY1XMOyiixOIPNIXAc9kH22AChw8UIpjflnNvda+PkFNzKGTlxCUsw5aN36fosHhS7EsF6A276DoKx0/pYd1Gi74QuHxudKXHZv/AJTbGVolSTtM5adrXCg3+sGnS2qswxnxfCNd1avIZEdBGd5s26rRyKagijohkVj8SXzuaDo3RcJgMcJe77T/AOFd1kMuKSOlma1o0bp+pWEgEMLW99z9UGhEWuRUAsQC2eX/ACK4TiIIhIHvDSa3TXscAWuBvwiqVKsx0jK+hx0KZoOkqsym75uQKKxEoiie/wABYWA4idja0Jtx9kAAABmFjMR6MJLftnQLAQFzvWft+H3PlMu1uqVLEYWOZpsuafIJWO4fPhzzfbj7OXMVBjJ8NJzxvryOxWBx8WMZbdHDdvTSHRWV9L+yAVjO8xk7ZDdDIod8uLYj4mxN1oWVwmEtiMrt37fRFVk97ImFzzQAsol+NxBcTysB/YeFF6Q5WNIA2ATWBDboIDhRFjuFxThhhuaEfB3HhFYeWWGVskZpwWCxjcVCHDRw+03wcqtUrVq1eVq1fSdX5V0HoKG4QOR2Q3KnmZDG57u3+ysPC/GYkl2125NAAAGw2ylxUbNAeY+AnY6U3QDVJK+QU5xI8ZWVhcVdMefocj0EAggjQrinDTA/nj/9Nx/YpoICwMkkBErP1HkeFDMyaMPadChnWWvXXZEgBM8oqvbI5FHMruMypcRHG4N3cfwjUqXDYnFvuT4GDYbqGKOGMRsFDupMZGzQW4qTEySaE0PAyo7hUqyGhtYafnHKftAfv1SRtkY5jhbTuFjsM7DyBlEt3bXdCOVwq6CwWLbhHhodbD9oeECCLGx+RSAVIZOJcaQGiGpX65HqKO6kmjjFveAE3FGXSGMu/uPwhBkrh8b9+zdKTY2N+y0BSzxx+58BPlfLe9L0pe0bl6M3/wCNy9KQbtIXIiKyrJjiw2FDMJWX3G/ViYGTxlp33afBWIZMyZzHXY3ULGjU7rhuN5X+g86H7J+RatWi9WU0VqVv0HptYjiOGg0LuZ3gIO4jjPst9Fh2PdQcOw8Z5nXI78ztVpk6PmsFxrwE3Dwg3yBUBsKVKlSLGncBOw8ZG1J2D8ORwjh3C/4rvZf8V+1BMimjcCKQN9XEMH67OZg+MD909r+b/wALlDW6brhuMM0YZJ9sD9x0noJyATna0g++gnonmjhjL3uoLEcQxWLkEWHBAJoVuVguGR4cB0lPk/0Mig2sqzrppd0RmBXXxLAkkzxb18YXq601htCV8XK/npwKweKbiYg4aHYjrJVHOkWoFa+cjniMRHh43PedAp58Rjp2irJNNb2CwOBjwsdbvP2ndFfLpEZkWgTfXj8GYHmVg+A7+ya+MDmc3VQ46SGdkjBpsR5ChmZNG17Doc7RKvsEBkbJzIvpbujsuJyOfiXMcdG7BcFiZzSSV8Q0HT2KG3SUegbZFdwiimk9PdSNa5jmuFg7hYtoZiJGDZriAoALK4VNIMS9l6OB/wBIoHZEp2+RR2JQ2HQdxl//xAA1EQABBAAEBQMDAQcFAQAAAAABAAIDEQQQITESIEFRYRMwcSIyQIEjM0JikaGxBRRQUnI0/9oACAEDAQE/ANvcv8y/bKCsct/nH8W0P+NNflDlOR98IZH8w/k6AI/hnmv8UZHM/wDEjOvxryv8msh7triVq1xLiXEuJWrVhWFavRNFmrCIINHfIn3hz7e2fdGeJr1ie4af6hUmj3hyj3evNatXlXlVyWptWQu/kr+ir3xmPeK35Tyjmdrh2Hs8j8MchQ9ko89ezBA+XDyUNeKwiK/HPsFXqPeGQCwkjfQYA8BYiv8AcSf+vz3ezueYZNWGP1OHSv8ACxI4Z36ZH80ocrInu2CGF7uQgZ5KEMf/AFXox9WBGGPo1HDsO1o4dwGiLS3cVkBeWAoPeT2X+os1a/8AQ5H8w8rWFyYzh1A1X1q3drTeK7rmpPg0tpQFdMsEfqcsW3ijdW1X+ceRjeI+FEwH4VKhm9mVZHKk9gPyiKWDP7Q/CeLa5EUSOSvyDys0aFG2mj+6vOhuUKKkjB1VI5jKVlgGlg79dvm0TosS3hmd51/4CkB9Q+EBoAigLOXDxalcUbBZcAtwCuGwnMLUQgMijqoxw4hh/mR6rGt1a75HIayP5QaXGgEARIy9EMrpVxG1ipvTZQ6qOIuIJTWoN1Tow9tFEcJIytDKiHjwQiKKxY4oj41/Pihc8+ExgYAApRqD1BTUE5DoU5rHn6m2mgdE0ClYtEqdvXkOW7WnuFNrG6+ycKPMfaPux4fq/wDogegQaVIyqsoPcBwhRsfvxFNoOAJCLd19KagupKc5PRVhHOMh0TdeieAdCpBR81yH2j7rGOeaao42xi93LVNagpXW1qFBwPRS4gjRn9VDHZLiSqDgEWC0GgC0JKRkCJFJ6cL2R0ytFQH9kPBRCxIqV3z+Taihc/XZqa1rBQCDbQaN1shZKkaDGQENkIwXJjK6UAmbLqnPA0Q43EBoJTMA8Auk0oHROdr4ypHTMrD6sN91+ixbDbSOo9jf3xlBCX6n7VsKCGpVCsrVpjxasAnVcbQbvZMAcwEbEIikXEqDCum114epUMEUYHC0X1PVY2RrID/NoE685AigibUEkbRTjRteswHez0pT4pjmhobdDc9Oe/wYIS/U/aFQaAB02yFDVE6p+Ka3Qao4p3/UJ07ztog87klMpzSE0dFhMSGfszt0T3tIRNlYanNFaAaUnhoY7iOlLFTGZ+gpo0aFwrhy4bT9CgrJOQUrRX47fqc0dygA0UNAiSUEVPLZLQcqzY7hNqkUyV7dOiEoKgx8sQAoFS4uXEE2aHYLhoLhKOiJ7K9N1J9TguAoNoIhaJzQ4C16J6OTmObv7h9gm1AB6zETkFPLTeG9TzxvOyKIRTXvA1NqKcWL0TXtcAVJMxg3T5nOdoUX+SrvIo2jWXD3VDsqFVSkhB+3Q9kRXMb9uRpBDcsKLl+BnLKIx5OwT2OAaXbus8l8jJC40crXEEXjuvUJ2Vq0EMyqVjorTpWMC/3AuqTcO6hZAU5ja7hJshEAbG/fEQw8PqvH1n7QeiJJJJywg1cfgZTTBg03WGiMzy95sA6+Vi/ub8ZkqwrVoa7KPCOH1ONJ7S00ch4RFoAKrVLhpAI5ElOlYN3I4gfwhGSR3XLCs4pm2NBr/RSP4I3P7BOJJJPU5WuJX7RWBjD5eI7N1X+oyl0oYNmj+5zwwqIeSVLOGChuo2OmfQ3O5TWtYwNbsFNIHyuN6bA5ONclLCYcMaHOH1H+ynmbCyzv0C9VxeXOQIIQFIKkN1XI2IlT+nCK3crJ88mAZfG8/CxzqiA7nmB9km1g4+DDsrd2pU7uKeU93HOSURMDW7gIAuPclYeERMrqdysXP6bA29XJp7omuXCxB7+Iiw3/ACnv4GlxOylldI6zlE6rGVoILyVxN7hGZo21UDHSfW7boFPO2JtD7ugTnFxJO/LhG1AD31WPdb2N7C109q8yUBbgO5TRwtaB0FI/c75y1BR1NlYODhHG4anYKSRsbS4qSQyPLjzAWVAzgYGjYLGTWeAdN0crQe4bKFxkeG9SpGGNhcSNF6x6BFxOpOWHh9V/gbqaVsEfTwE9znuLideUBAcLWjsFinXM7xplZPK3nJUIuaMfzBONUnCnuHk54WDjPG4aDbyiRSxE5lcKP0jYc+Ej4pbOzQpHNiYSU5xJs78uAZbnv7bLHuprGdzaG2VG1CwRsWJl9WQ9hpXNh28U8Y8oqQ2833KOYzHMTlBpNF/7CeQXaqYVLJ/6OUEJkfXTqqDXADosVPdxt26+xg2AQg9yVjpDxhgOw5QsKzghaO+qxcnHM7sNEMsLHxScXRqxLuCIm6vTnwQHqE9gnO0OW6rIDnKJrNppwPlMYbLisV/9EvbiUcbpHho3TWNiaGtWKmEdgH6j7AFkDuUAGRjoAFK/jeXdzyUoY/Uka3p1UrgxjndgibQygZ6cbR+pWLk4pavRumV1y4Fv0SHuViBUT/jPfmad/Yle5kDn9Q1AkmybKwI/aOPZqmlDGh39AnOLiSd/YwjOKdvjVYt/DA7zpzYCKrkPwFjpKDWD5KpBYWPikvo3VTSenG53XojyXlawQqBp7krGH9kR1NIInk3zbm7bkYOJzR3KnbcElj+HLCNDYnOPU/4U8xleew29n/T2avd+ix77exvYXmMmgucAOpTGNjYANgFK8vkc7oToMgsOzgjHc6lY2S3BvQK+UnKAEQRj+ULGXwAX15LQ5BkU7bkwjbxEfyntuN48FQRGV4HTqsVK0ARMH0jf2sG3hgHk2sQ7ime7zX9OXAx28vP8OyxclREDrpkN1C3ilaP1Kc8NBPQBOcXOce5yvlCBqNgHYLFn7fnO8hyBcRydyYMhuJjva6T3UNFNOyMFkY16+0BZA7lEiOE/ytXXlgaI4WAddSsW+5a7DILDfTbu6nk/Z139hu4TjQU54i3t7AQzI5ASCCFJi5XtDSaFa0gj7OHbxTNWMfwwkdzXLE3ilYPKJom053E4nuc2io2Dxqpz9oyZGC3jcab/AJQIJrgAZShY0MdI7psjqTnH97PkJ9lyn0LRkeauUjm3Ps4QfU4+Fjn36f68hWDbchPYLEENjcRlaaLIHcqQUSApjbkxpe8NHUrEO+oNbsAgZX8LASnjiJZtHHunsbwD6KLvtT4wGRho31Jrsp2tbwBo04Qb72ov3jPlRsb1WL/ekeMj+GM+nJhR9LisWbePDeTUrCmg8rEn6B5OcIuVnyizupP3jlE7ge1xClEb3FwfoelJsnA4FuyE54XN4W0TaOIJIPCNqRnJFFoqqpSSOfv/AEUIuVqYxxKxH75/zXOBkNeQnM1XuYb7D8rFfvTyWsOP2d+ViT9ozw1es3wnuHdONl1d8rze0RMr+IjVDLCt4p2jwUAAApDb3HyeakEeU+3SrODSMKfWV3LCAIGhYn7/ANM8PfGfhGF9WRSKGUTWhj5CLrYeUI6LHur6W25TF7nW7fIrAgmY/wDkqV4Ywk9BkTyhDOjkT7dlWrOQKi/dM+FLXqPrvys0jYK6KY3K7PA0JHE7AKWVrmuF9M7THP2aeqLnxRgE/U4klE2TkVgG299b8KxjiGNbe5V6eyFRRNDkPuxMuJvgJ/3u+czkLFKT73fKOWHGjtNEaDX+Bk0RtDS+zfQdlJDTw1vXZNiYXlgcQ7v0QZfG55NDQnckqSFojD2EkdbQw8dC52h3UKVgjfwh1rAD94fAWNJ4mDwiec8hP4ATLDWjwj9xPJGLe0eUdNfGRywv2n5U2kbvjJjf4naNCif6krj0DapYazNxeCSqfI9wHU2pXt4Wxs2HXuUwcDDKfhvyisIQyGR5NC1NKZXlxVeyAuPzned845G7quFjj4PLhxczQpLEbvhHPDGo/wBVO4+m9CgjPGauLZNlAkLuH6aql6gY1zWXbuvhRyYcR8Lmus70pXREj0wQOtqZ7XNja3ZoyL3em1nQG8iqVchy1Q5KyPuRgF7B5Cld+yef5Ty4EXP8NKxpqNHIqBo9AKf7P1GVoINJNAEquQDK/ZGY9ylWWHFyt8Kc1C/zQ5cCQHvJ7LFv4g0FHIJmkLB4U+jQT3yY1pdRdQUODgIvi4/hBrY2/QwfA0T44pPviU2HgaLbKBfQ5BEn2uqHvg54Not5PiljHlzGDzy4Ftsee5WKI9SuwRzafoYB2WKDmsbxdSsOzikbsaN13U0XAQB1WBazieXOqgOtINk6PBvupeAMdxza0dLpSMcGxX1bY/Ur0WsjdZFkC76VuMz7F5D3RkM8O2oge6xJ+sDsOXDEthaO9lTOuRx88gDg0OHYLFScbGfKY7hcDQUjWujc76Q3hsV3T43RuLXDUJssjAQ15AOXC93D6pAoU3wsRIHO+kjzWVo++NeQUcryGQyAJICADGtZrwgKR3E9x88opkddWhHkjNtDe4CxrAwxgDKKX0z9rSPItDgkYeEh5JDqUsNvdwVwj+ye+GIDho/TuPKfI951P6ZEq/YGZ9kcg5MKwGUOOzVPMPSdpWlDlwzOOUdhqsU4CMAblHKsmQuMdhYsk+kTvqhnbtNdtlWfX3DzAchzGYWFhDYmkjU6rHS8UnA3Zv8AnlwbGsjs7n/Cnl9SQu6dFfJEeKNp8LGwzPLC1hKLHNJDmkFVlft0gPePKFEzje1qllEURN69FZPXkgjEjxf2jdYqQAem3c7o7ckU7oyNGkdiLWHxcUun2u7ZSwxyt4XC+xWJwz4Ha6tOxzKCv2AqzHtnmwUVtL3aXoFjXt4msbs3f55GtLiABZK4WYaIULcU6OY25zT3JVnlBIIIWExnqVG/7uh75SNY9ha/YqeAwvq7B2Pt1yj2LQ54o3SPDApXtw8XnYBEmySbyjwsj9aoJuCiH3ElMijYfpaAjlisLX1sHyOQZAkGwVg8WJWU77x/dOIJpThryWO26KSNzHFp9s8h6chzHsMic8E7AdToEyaCBpDbcepUkj5H2dSo8I9xt2gUeHjZ0s5WrVq10WJg4DYGhRyGbXFrg4bhQSeoC8HXr4QkjabqypoTM0kinbhEEGiOWvYFAcozHK2N7zTWkowcAHqPDT23KLmA/S2/JRe525UOEll1qm9ymwMiBpCVg3eF6sX/AHb/AFXqM6EFF6GVjXJ7Q5pBU0XA+unTIZ2opDG4Hp1CiMZjBH9VI4kCtlicOXMEjRr1yrnrIDnHNFhZZaNUO5RbhILs+o5S4qR2jaY3sFqgEyUR6tYL7nVOxeIdvIUXOcbJJztCRw/iKGIeOtpuL7tQxTT3X+5b5RxLO5Uk0L20br4R0RGVZ4abgdwk/Sf7IFobqi4ucAdlioQx3E3br4yrn2F5gKsxyxxue4NaLKiwsMDeOUg11Knxj5DTdG/5Q5rVquSyrVolX7GFnFCNw+ChFoC5yDGusAWFPCYn1uOh5wETzjO1FE+V4a0KJkeHj0PlxWJxL5nX/D0GW2V818h9g8g2UEvqt4SfqH91wvJ4WlOw7XxlripGFji08uyvnoroOTCgNiJA1JWNe76W3ohydQgdkNQChkNXe4QLRyOYJaQQdQoDxMDjuQFPoAsbGz0A6tQcxvl1HON8v//EAEIQAAEDAgMEBgYKAgICAgMBAAEAAgMEERIhMQUQIEETMDJRYXEiQFJigZEUIyQzQlBTcqGxFTRDgmDB0eFjoPDx/9oACAEBAAE/Av8A9la471jZ7QXSR+235rpov1G/NdND+o35rpov1G/NdPD+qz5r6RB+qz5rp4f1WfNdPB+qz5rpYv1G/NdJH7bfmsTfaH/i21qkxRBjTYu/pYz3rEsSxLEsSxLEsSxLGsaxrpHd5XSv9or6RL+o75r6VN+s/wCa+m1X67vmhtGrH/O5f5Ss/VX+Wrf1P4X+ZrO9vyX+Zqvc+S/zdV7LF/m5/wBNi/zkn6IX+cP6P8obcb+j/KG3If03L/Mwl4AafinbTpWOwvJB8l/lKL9T+F/kKP8AWC+m0n67PmhUQHSVnz/8Ar6jp6hzuXLdf1e6urq6urquPpRO9qMLErq6utmmZ1IwyfDy/Ptpz9FTHvdkifX6j0qWkf4EcGzqT6RNn2W5lD8+2rUdLUFo0bl6jdXV1frO1s/9kn972NL3Bo1Ko6UU0IZz/EfH8+qpuhge/wAMvNONz1llhWFYVZWWELCrdZSelTVTPdvv2NR59O4ft/P9t1HpNhHLM+qWVt9up2d9+5vtMI3UdM6onawfHyTGNY0NaMgPz5zgxpcdAFUSmWV7zzPqFvUaN2GqiPipmls0jfeK2ZR/R4Lntu1/P9sT4KfANXf1x69ZbhI6qAEysA1xKKhx17pXdkZ/H/wDadR01S7uGQ4tfUyN54qcP6RpbyUFQ7m1Agj8+rp+hpnu56BHP1o9RQ0rmD0tSAUIm2uotLfn22qi72xD8OvEPXNmUfTzYndhuqq24frh+Eel5KO7o+lBy7lD2L9/5694YxzjoAp5TLK955niHrHPfHG6R4a0ZlUsAp4WsHx81UtxU8re9pWzXY6NzVTfd/nu2J8EAZzf/XGPWHjnv2PSYW9O4Zns7jmtl+j07SeZVP8AiH57tSfpql3cMhxDqWxvdo0oU0x/ChRv5uQoj7a+gt9oo0I5Er6Ew/iK+gD2yjRO9pGkl8EYpB+A8RF2lBUFL9ImA/CO0gABYb5G56KHI/nlbN0NM9/PkibniZwjNMpZnfh+abRgdrNNiw6NCtlohZeSyVrDcW/NYuRVkWqydGw8kaOE6ZKSkkbpnvCwHHYKhphTwgfiObt50TgmJun53tyfNsQ5ZnjjGXAKYAXmfgHdzTaiCPKOH4o1z/YX0yXuamVLubU2aIrA06FEFrlkrW8t2aITTfJDWxWpRO45KSFj9QpKZ4zb6QQWzoGPm6Q/hGQ4XIJv505wa0k6BVUxmne88zxs7I3NY57rNCwiHTN/f3LonuNyvo5RicmDCdFj9xNbcdhdBUB125L0sPphFvchcIeCvyWiPetc07Naq1lki1aFSQMkHc7vVGXQ1LWu55cJ0TUw/nW1p+jpsPN6PGNAmtLnABOcGfVR/wDZyihyTItF0dkIm+yuiZ7KwBBoVlZOi5hHPzWiGfmj3LVWV14o7tU4c1exRaDZRyB44Haoc0zU/nW15+kqi3k3LqfuBa31hGfgoI7kXTGZK263EU5iI5FHIoZoIoWVk08lzI3HPNPTDdqDnNcCExwcLobnao5JiGn5xPIIoXv7gpHYnE8Y1VKwOkxHRma7Ty7vVLHz6oyNHNGZq7SIRbYrJ3nuB3EK2SBu23NXsU5t0Mla4UcmFyaQ4XCCk1R1QTNPzjbU2GFkftZ9QztBAFlGXe0VG25ULfRHUSTBq+skQp10be5WRCc0ojuWouslztdFApzSCHBEXsVdFqacrLmVTyWy5K6kR3MP5xXUTatgGKxHNf4Afr/wv8A39c/Jf4Bv65+S/wAA39c/Jf4Fv65+S/wTf1z8l/gR+v8AwnbEwAu6bQdymFqGEeSgzKj7I45prZBMZi1Qs1Fyur7rJ7O5EFBFXVk3uQyNt1kTmjomGwTDkn6BclyTeX/gNcMMQb3FU5TOyOKV1gs3FRjCLLEpJWjO6fXsaSBmqeUyC6G97OYVuYVuY3NKKIuhmNzx6Xmr5LuUbvR8lfExN3BD/wAA2g36t6os3WQ4pblyjbbNEqepazI/AKYyPaHE5YrKIHCWW56qFuFoQ3kJzbZhEZZb7Zoaq/pLmiLo6JuYUGqBwkhN3BM7P5++QN81U/WMcqF9pbIcRbmipHOChpRLG979XaeCdTOa/CbeaiiaAEEOAhEYcuS52Ry3aORK1K5JwTeSYdUXJvPezn+fOffIIxpwQGCr+KZpxFOCqR6Ka9+AMbyTI87lAbhwvbcIoG4QVkdSmHNaK2IJib/6T1GdPJXyWib+eOcG6ouL/JWVk9qqWWkDlE7E0bsQWMIOQR3OYHarAFbcBuHDI3mjquavmtUMt3eiPSTVJoVEbsZ5bx2kPzp81sm5lWJzKtveMipWYgQqOTtMOrVLUBuiMsrnKNsiFwmv32VlbgCPA5twnA5oFOQT9QVdc05NKfooT6ACb+dkgDNPeXeStvurpzs07VVF43NlHk5Ma6QpkLGcs1dE21ICZM0u9E3Q66cWzVrO3B3JHRHLJBOPNBE6KA/2mpvPc383c8NRudVbge62a+kNKc9x0Cz5p4xMIVEb4kZApqrDfAE9xIdjuTyVE1/Rn2b5Jjst91i33V1fhkFwiOR5bjk5NKd37rapq5/FRdspq5oJn5s6XuVuAlOcnux5NQjDQjcpzbFBOHRS3b+IqSbWxVD0RicHanVPp2dJZrrhNbYAJnBZDXdZWVtw4Jm80cijmLpq81zTSuZXLyUOcw8kNU44SP8A+5q3pKPn+aEgJ0hcgOApxTziNgmtDRverqZl1PGbBwGSbE7KxUMeAIBDg6YufhaPircEsrWpvC/ROGoQ7kCBkUTmimELmjqVD98xc07PLuKPJDtfmbn2RJOvESnkpjbDgcvxI8key4KEck0bigVfJP5BNAG9zw1STG2Sjbd4J4nKR1itCjmnHJX0Kbk7wRyCPZaVGfrmq+TSijbJA5j8ye/Dw33EooZlDgOpVs0ezbuR1KbYO+KCG7RY0HX3YrJ03d8056aOZUIz4nnJWxvR7ldO1RyTdNE4/V/FSdgeag+9afBA+iuaztZcymnl+YPfhCzPAUViRci6+iaFdXWJGRYu7NOvbRWLuWqdE4fJPecR+CgkxNQO610Wpqc6wTn33AXN0VGLDgKKkKYywVS0izgibXRK5oahO0Y3xuVIRcBRy4L5aoVOmSNU4WTJnlMax/pXKA/L3vDQiSTc8JKJ3WCxDksTu4rEe4q0p0YhTE9p/wAkKeIfhupPQsWhSlrwHKEi4Uik++con4HeBTTvO57rlEgJgLs3JpsmDEUOAoldpyATmgixUgIcW9y5Iapqju4l/f8A0jm8lAZqyt3pmWaY9zXpjsTQfy5+0HSTGKnANu086BZnU8JRKunO5c1HS83/ACTWNboOMxMzyVyx5BRN2KX715R0UMpbk7RNcgUU42Cc9xNmhNb37gLpotwlPKjGW4qqZliV01thiPwT+z4laNy1QaGtQV1jQeU157lS36O/5btHaWK8MJ83KkhEMTR8+Epx3OdyGqhhwZntdVVR/iQPoWTx6Z8kIzZYclifFpmO5Q1Mb+efcgUW3Ukea+CaCU1tuJzl2nIb5R6DlhJcVa5CawuJJCwItC/6otv+EhCPxWAoNzzTJYQ0DEmua7Q/lRIaCSbBV+0+kvHD2eZ71Stx1EY8UOElEpzrKmht6bterc3E0hZtdYqSPEgS3tBC1kRqCmxZpk8kXazCiqGPGRTs9w4Lq6JT3k5BRtwjfjaOaklFiFZqBHIbsldGSydMukKDpShfxWO3JdLJyTKqdvNR1zT2gmuDhcfk0srImF7zYBVu0JKk2GUfd/8AO7Zo+0X7hwlEolU8fSOxHQdbUxX9IbnNxM71gKcwhDI+aKczm02KhqZ8ViLrp2/iyQer7rq6LlPUBo/9KKR2pGa6WQrpD3lYzuyWW7kiVmV0awBYgOSxSHRBsntJsMp5oxDm8oBg71dvcE1zm6Gyjqj+MfFa/kckjI2F7zYBVta+qk7mDQb9lD0pChwEolVdSImePJbLa4UuJ2rzi66aLC69skDYrD7yt76t7/8ACIaeaMYvu1WJ1/RTJj+IIStOhWMIytHNPqcRwsWDO5Nyh4K6xAK+eiy80HeCvuPmiGq3gi3vK9EIuzyCY1zkAGrGnP71yz+SHhuzUdQ5nO6imbJ5/kW1K3pn9Gw+g3+TwbJHoPPjwEpxU8wY0lNxVVQ0Hmf4TQGgAaDriARZPpz+HRZtTrEKwVgN1kSBks0fAKzeaI97+UIx/wDa9FqMgQd//iuhroiSroa6IrLdms1gK6NYWBOei5F18mqNuG/M96cbIO71ianOHehO3kUJTe91FW+380CCLj1/aW0MLTFGczqeHZgtT/HfdOKllDRclVFSZD4LZ8OCzjq7+uvO6rbazkXWOiMjBrdOmj8UKhqdNi5rHywrpHtF8PyRq7nJnzWOR2p+CHeruWEXzV2gLNCyuhiX/ZWCAC+CsVa269k5yLj/APSN/wD6WAlNGFTVDI/NGomc66L3nVybivYEptM2wQgZ3BVUjIvRa0Yk2aVp1VPtHo++3cmV1K//AJB8UCDoQfWyQNVWVWCMn5KRxc4k8NCLU7PLcUSpZWtaSSqqoMh8FRwdK+57ITPvG+fXndO6LAQXIhSDJYL2WGyDcr7shlyTomnMH4IRDRYbItvoujK6L3guif3ropRyVpO9YTfVNDhyTc9botF+1/CA8d5dZYig027lhA0RkjbqQE6uYOy26fUyv528uCiZimB9nNBGzWknkE95e9zjzO+6bI4aOITK+rZ/yn45pm2XjtsB8lFtSmk1Jb5rX1aqq46duebjo1N6R3pSH0jy7lXzY5SOTeEZlQDDG0eCuiVPK2NtyqiofKfDuUbHSvDW6lMibExrByUX3rfPic9rBdzgApNq0rOzd3kpNtSnsRgfyjtSt/U/hN2rWt/5L+apNsMlIZKMJ7+SlqYImFzpBZHbhxG0Qsv83/8Ag/lO2nVzOwx2b5JsbjnK8vPjoir5ZpybonDVQnIgrCR5K4WIWRcgckCLprrWR9LkujHksVvFYx3FAMuV0Y5K3irIIuWZRbbUp08MY1sn1vsBPqJn6u49nMtEXd53bQkwwYfaPFdXKDlQ7QdTmzyTH/SgrKefsPz7vVK2sZSx31cdAqNr55XTyG/cp5uiic75JxueGAXlYPFN0CJU87Ym3KmndK65TlRU3QsxHtn+FzU03Rui8XjhqqtlMy515BT1Ms7rvd8N194WqyCYHSOwtUUDYm2HxO7K1yclU1OM4W9n+1TSiRuE6hW0XJc0HEL0HeBRaVhcrFWWFx5rA72lgarKyLBZZDmjiOiu/uC9P2F6Y9kLH4uKqJejZfmdFm43J6mBmCJg8N20n3nDfZbwk7mH0k/tIZhRvN1s7aJfaKY58nd/qU8zIY3PdyU00lTKXO1OipouiiYxbVk9Jsfx4qBt5xuqJ2QtudeQU0rpHYnIqhptJXjyC1R1VTNjnJGg0UbsUbHd4G+edkEZe5VE755C9x324Buo6Xoo7ntHVELCqqoxnC3s/wB7g4tNwqeUSMuirDVWXRiyuRrmrg8ldZcGXBbvWSMl9FYnVSPjiZiKke6R5cephZjlY3vO4Kofjnkd3u4homdpEII5OTStmVhnjLH9tv8AI9R2jWmolsOw3RbOhxS4vZWi2g7FVP8ADLi2a3MuVTUshZ48gpJXSOLnbqSmM77nsjVEdyCrZMEdubt1Ab0cH7dznBoJJyCr6s1EmXZGiJ3AIlX4Nm0vSP6Rwybp5orAStoVGfRN/wCyO4qGUxPBCa4OAIRITUUb9yDnK+4ELPkFY96tuyWabG9ykDW+iNeZQapHshZicppnzPufgOq2czFPf2Rukdgikd3NPBe53FOyao951QKo6gwTNf8ANMc17Q5uh6/a1ZYdAw69pWWzmYYMXtFXUxxTSH3jxRStp6cHmdApJXSOLnHPdFE6V4aFFG2KMMby3OIbck5BTymV5cd1FtSOKJkT2nLmo5opGYmPBC2hXGY4GdgfyihmVZF3DGx0j2sbqVFE2GJrByRcqqqMUfidE5HgppOjbnogQ4XC0QPije/aVkFrqEGqyDCVgd7KEMjk2m7yhC0KZ2HJuqDBzU0zIm4ipp3zPufgOr2Yz6t7u8oLaRw0b/Gw3uKaN7symbzuatkVWsB829dWVLaaEu5/hCc4vcXE5lFQNwQsHuoo6k8TnF2u4Ak2Cp6foGe8dUdEFW1GM9G3Qa+e4rNRuey9nEX13PTcuPY9NrMfJqITrAEqqnM8pdy5cVyVHI+M+iU2sB7QQkjdoQrBWWY5IfuQb3BRQcyg0Kytue6wVuZUrmxtLnaBVE7pn3OnIdZRsw08Y8L/ADQC2y70IWeJO9uZ3k5IJu8rkmqKQxyh41BUbw9jXDQjrHODWlxOQVZVGpmLuX4RuYLvaPHceyfLqaCmwjpXjP8AChmU9VdR0TcDe0f4HAENx1HCN0TDJI1o5lRRiONrByCK2pUYWdENTr5cNlbeQiFR4yHekVZ3tFVhOJjPC6oGNNOzyQA7uAI2ROJ3hur6jpZMLT6Lf56xjcTmjvKY227azr1TW9zNzymiw3v4u9Bcz5rY82OEs5tP8dZtaruegYf3b6QXqIv3bzqfPgO+gpOkON/ZH8opiqZ2xNLjryCc5znFxOZ4Oe89ob+W4btjwYpXSH8KKe9jGlx5BTSmWRzzz4LKytuCKKpYsMTfHNCNVDsVRIfG3yWznfZYz5qwWEKy5q6kPLdtGp6OPAO07+utoGYqlnhmgN1c7FVzHxt8kVqepJTU3VHU+a2VN0dU0e1l1dbU/R4SfxHsokk3O+i/2Y/PcGKXKWQe8eByCpKZ08luXMrCGANAyCtdPwxgudoFUTGaQu5chw80Nztw3jdQRdDTNHPUrUras9gIRzzPUHexuJ7W95TWNa1SvwRyP7ggtk503/YpmnAdFrmslWTdNO53Ll1gWymenI7w3vdic93eSnHJRjfyQQ14Cmpm6Nxa4Ecio342Nd3i/UzSsiYXvOSrKp1RJc6chwUf+zF5pgzRdZVWVTN+7ffPdDE6V4a1U8LIWhgCkCGirarpnYW9gfzwlDc1O03DTgo4+knYPHNBXsC46BTy9LK955nq9nRYp8R/CFqtqvwwtj9o/wBILY/3T/3Jmp4JTyQW0Zuipj3uy67ZTbQF3e7dMcMMh907naoab3bm8IQ0RQWzH46Rnhl1DnNY0ucbAKurXVL/AHBoOGl/2Iv3JqLLquFquXc42CHZKY0k2CoqQU8efaOqZ2k9bQqrDoWn93EUOAcAWyY+2/4IlbRmwQYRq/8ApHhvwhbPgIhv7W7aEvSVLu5uSC2R2JPNN7XBqbq5W0Z+kntybl11FHhpoh4f3u2gcNHL5bvxcGp4Smjed2xZMpGfHqNp1vTP6Jh9AfzxRG0jD7wTBZt0962j/tHyCOScb5J2gWzaPC0SvGf4VyUSr6sQNsO2Vqb8RQ3hHVDeFRM6OnYPim5lV8mOoNtG5dXG0ve1o5lAhrA0cgppOihkkPILXPdsnsyeaHJHdK7luqZuhhc7nyR60C5ATBhaB3Ddtc/Zbd7hub3pyCKGSG8ocB3bMkwVTPHLj2rW9Czomdt38BDv4+k9ADdtD/Zd5BOKZqqKl6R4e7sj+ShqndlPmbBEXuUsrpZC92p4yhvGqcgjugbjexvedxd0cb3dwRPV7Niu5z+7JBtltiX0GRDnmd+yey/zQ5LmnFHM7tpzYpQwaN/vrqRuKoiHvb9sn0IR7xT9E3IbxxNHFE7C8HuKabgHv4XENaSeSqJTPM955lHcOGNt2t8gqqboYy75KRxe4uOpT+0mDJUI+rarZp9g250VZUmeT3Rp1DkNOI7tmsxTX9kLmq+S0IZ7R/rqwFSxdFC1vzQVXN01S93LQb9kj6k+aCCkPLdPJ0UTn9yJLiSeu2Y29UD3A79sn6yIe6U/RFN792iHABxt1VA/HSxnwt8uHasuCjd72SHUNeRCz9oW0nHCzxO6UZhN0VE30B5Lmtp1mL6lhy/F1L9EOE679lttE53eUNVXyYpreyLdXQw9JOO5ue7aE3Q0ru92QQ37Nbanaggibm+7ak93CIcsz1+yW+lK7w3BbXN6u3c0JyO8Z9YNVsh/1T29x4dtv9KFnmUeMZldwW02fUsPc7dLoohdzQqdtmhV9V0LLDtHqn8PNHTfTMwU8Y8EMrnuTzicXd56ughwQ3Ors921ZsdRg5M/tDfRNtTx+W4nLdI8Rsc48gpHl73OPM9fslv1Uh97ftJ162XwsE7UIbteEDqAtkvtOW+03h2ub1Vu5oRQR4aZuKeMeKbqtof6r/huk0VBFikv3J8rIIsTlNM6WQuPVP4SuS5qJuORje8o5CyqnYKd3vZdXTRdLMxvzVgFLKIonyHkESXOLjzN941UIwxt8uDastmNi78z6hssWpB+476k3qZz75Tu0hpuHAOqo34amE+PDtT/AHJPhu04tnt+uPg1DIKsF6WXyRQBc4NCpYREz+yq6r6eSw7DdOrdqOE6IJy2azFUA9wR1Vefu2/Hq9mwWYZDz03bYmyZCOeZQG+BuKZg8U1qmn+ubAztfi8Bvq5elne7ly9QoG2pIvLfIbyPPvFO1V0OvYbOBQzAPBtYWq3eQ3Hi2YPvT5bps4ZB7pTiqCkIHSOGZW0KrCOhZ8erK7+IJ62Uz6uR/ebJoVW/FO/wy6qNhe9rRzKYwNaGjktBcqol6ed8necvLg2c29U1VtV9Ggy7buytkxkiSZ2rjurpOjpnnmch6jSi1NF+0bnGzXeSJ13D1GGrHRR/tHBtR+Orf4ZI8ezDlKPLcMyv8dA2S+ZVZVthZhb2kSSbnqymo5HeNwTtFSR9HSR+SxWaT3BHv6rZUWKRz+5ALacvR0rhzdlw7MkiZKS91u5V9QKicYdBkFTw9FCxncFZbZk9KOP4n1GMWjYPAbpzaCU+4U7RBDgHW4jvOQUr8T3O5k9Rs19pS32huLsAt+IqprmRgtZm5Pc5zruNz1jk1EX4RqmMxyMb3lHkFVOwwO8ckeq2fD0dO3vOe7bMmKZkfsj+1beVpbyVDH0tXEPG/wAt9fJjq5D42+XqEYu9o8UEFXnDRzn3VIck0br7h6jNfopLeyViv1DJCx7XDUFN2nTYMbsneyqitfMThyHXP0Q3P7943bOjx1F/ZF07IqvPYb8eqgZjkY3vKAy3TydLUSv73cDWg66WV7hbEjvJI/uFt0jsDHO7gnG5J3WRFlFDJK7CwXKdBTQZSOL3+y1NbBNiDWFrrXGd0VDTN6MSy8zZre9Pw43YdL5cdMLzxfuCA3bXP2GT4J+qCO4D1Ovg6Cpe3lqEOMmyGfXu1G88OyGejK/4IDE5VpvUO8Muq2Yy9RfuCCrZOjppne6hxbHZhpb+0d20n4aOXytwQwumeGhTyMpI+hi7f4nJzcge9RsNPC6V+TnCzB/7VLB00zW8uaqphckaD0Y//Z6ihF6qH9yG7bTvsn/cLnvHqm1aPp4cTe2z+UMuImyAuh1xR7fA7e1bOjtQt8blBikdie4956rZLLRvf3ndtmS0UbPad/XEFRtwU8bfd3bad9Sxve7ghaKOkMh7ZTiXOJJzKiq3xtsGt8CRopJHyOxPdcqmYIKN0jsi/wDpEPnks1vkE6lYwhjphj7hmqmlNPhu8XPJUtOHsklePRaFJg6R2Ds8k2njZAJJgfS037OH2uNaBYltx32eP96Gm4eoHlxbV2dhJniGX4ghwXWH1AoangPBStw00LfcCqfQgkPunq6FmGlj8r7trvvUtb7Lf74oW4pGN7ymCw3bbd6cTfDfRRdJUNHdmtrSfWtiGjRvgpjI6P3j/C2hLeXox2WZIWo6TF/yyfwtnwXe6ofo3+1ITUzvech39wVG4SR1DQLNDbBRsA+sdoOXeVNd+zWvOuJOBba/du2WPtQ8iiiFtzSnHid4HqB463ZGZkg+LP8A4Ttd4b6iUzThdubmQEBYBbRNqV/j1VlG3Cxo7hurnYqyc+9b5cWzmY6yL5obtrOvVeTRv2U4Cp8wtptcKt5PPcIhGMUvwbzKoqloqccptll4KR0LJHOa7G4n4BVctNN0b+k0HZQqYH0RZjDD3KOWHopIm4R3F/NMlgpqd0ePE52uFHBPFGAY221udFUVMDImRM9PD8k5znOLjru2R/sn9m5y20688Q7mIoDcOvd1FfFGypkwG4/r1R+iHFdUoxVEI98ILa33DR3u6qAYp4h7w3HJOdikee9x4tjt+0k9zFfdXuxVcvnvDi0gtOYTtodI200LXeOi+kW+7jazx1KLiTcnq9j/AH8h91YlJItpH7V5MCt6kdOPaNZ0DMLe27+EU5ZrNYisSxK/Wv5IcRWzG4q2Hzvu2ufQiHieqoG3q4vA33VLsMEju5pQ4tij74+W+oOKeU+8eqpoDM617AalTdFg9BlvSyPeOLYp9OU+SllRcqt2Kql87eszStijc92gU0zppXPdzR4bLCrLNYliV1fqHajjK2KL1w8Gndtc+lEPPqtlNvU37m7tpuw0M/lZDi2MPqZD7ysuSf2j59U6PoqZsV7Ofm89wUj8Ry0GQ4tk6THyUiJWr3u73H1na1Vjf0LTk3Xz6yyss1iWJXV+B2u6+66ur7thj7S8+5u2t9+39vVbJydK7wCBW2nWovN4Q4tjj7Lf3zukNo3+RRPHBSt6Pp5smch3qMMnbN9UGhrbhbOibJLmMm5qqq+le8BuXHspn1Dz7yczNPAAN/VbcFfU9BCbdo5BE9fZYVYq5WNYgsSxBFyur8OwW+lMfAbtpkfSj5DqtksvHKfeCAW3n/VQt95BX38zu2VlRs8yjIFM/wCpl/aeOCPpJWN7ytpyem2FvZYEGGGhLfxP1vyRw0tDl2pOaLAyO7u07QcezDhpf+xRfdV8lo8PfuHqxIAJKrar6RMXcuXqllhWFWVlhVuAWuLjJbI+j9G8wtcPavu2iftciv1OzARTebju2+762Bvgd43N7Tt1AT9Di3VB+yy/tPGxxY4OGoTqsOd0nRNx96p2vqapuI3zzVZWfXFoa0huic8uNyc+PZrB9FZdGNoW0JMVQ4chl6pz4Nr1VmiFpzPa/INhf68n70VX/wC3N59Vs8WpIt22n3riO5o3jXcznuomfZYf2rowq1v2ab9qtx00PTShl7KPDSQyv/G7Ji59RThzaePyRkKe7E9x8fV5pWwxOe7kFLI6R7nu1P5Bsf0aT/sUHXVWb1Ev7juHUUrcMEQ90IraLsVbOfe3sRTOe6mFqeH9g3bQP2SXyR3WTNn1Du4eBKmgkhNnttuZDLL2GkoxVFOQSC3uKc5zs3G6DHONmtJT6edgu6NwCKse7gxKNwETR4BTP9F/l6tbdtepxP6EHIa+f5AFs7/Sj+KZiDlP97J+49S3MhMyaB4IqZ2KWQ97jvZojom6IKPsN8hu2ofsrvMb6RobFNPzaPRWN+LFiN1V2k2c17tclTwGeVrAq2UB3QR5MZ/aoProZYX6clgPSYOd7KpeYD0MeVtT3rZdQ+Rzon55KsjEdRI0aXUVWykjbHgudXIbTjcQOgzW0KgYeiDQD+LdzCvZVB+pf1l+pGqDTZVU4ghc/wCXmnEuJJ1P5Ds9n2KDyRapM3u8z1NOLzxD3huqXYIJXdzDwN0TtE3RRi8jB4jftc/ZwO928KnhdNK1g+K2lO2zYGaDVbKaGxSypzsTnHvK2QM5Spj9fIR7RTnFxuTcrZzRBFJO/LuU0hlkc/vO6Fv0eLp3do/d/wDyibndGLyMHvBPcqqUWwDXnwX9RbquncMltWp6Sboxoz+/yKkypoR7gTjkUdep2e29VHu2m7DQ1H7bfPhfogqUXqIf3jftjsRDx3xxvleGtCfOymYYoTn+J/8A8K91B6Oy3nwO6i+poZJDzTs1BALdLLlGP5VVVOnNhkwaDdR0/TzAHsjNyrp+lmy7Lcgrq6ps54/NVUnRD3isznuLlmVb1FqOpTjc+pHrigm+jG0e6E53oP8AI9Vslt6gnubu20+1FbveOF3LdQC9XD+7ftg5xDz3MaXODRzTaemZF0fT2v2iOaOy4ndidVbGRFsTfw6nxVDIJKaWnJztko6WV8mDCR3+CrqllmwRdlqoqPpvrHdgfyqigmmd98yw0Hcv8f0N3zObhA0HNFRD6Ps97+b99lRnDNiPIFTSGWQuO4u7kAAr+pN9QPqRTBd7B4hOepfuJT7p3nj2OPvneQQK2+76uBviShwHtDdssXrY/jv2v98z9vACRzRN1cg3CdUzOFjITu6eUADGbBdNL7ZTp5XDCXG259VM+MMJyA4nOQyCvfddZqxVuuPZ9QPVnqKYXqYf3BHVVFxTSHw6rZuUDz7ya5bdfeeJvcz+0Nw13fjO7Y7b1V+5pV921T9q/wCo4j1Nt7imhOQBWFWHqL+z6gfU9mtxVjPC5Rju3RbQfamI8R1N1R5UzfG6YVtd2Kuk8LBDc1BDn57tjD6yQ+CG7aRvWSfDhO9lNPILtjKc1zTZwseG6vuK1KAWH1STl6gfU9jsJnkeOTUwkjNbXI6NgHtK3U0rbU8X7UyNVb8dVM73yhuCCbpu2KMpj5Ibq43q5fPhZTzy9lhTNm/qSfAJlPAzsx595zRuiGuFnNBHipKCF3YJafmFJRTszw4h3jiNymst6qE/tD1A+p7Gi+pfJ3u/rdtZ31rG9zepAULB0bB3BTP6KGR3stJRzKG8Llu2K36h597fVH7RL+477qnqY49Ygfe5plXHL+Pe+LG9pxkAcl0ZGj/miJRyafiumDb4srKesgf/AMWLx3jdbfZW9SCd2/UD1h46FpjpYh7v9qxVc/HVSfLjCCjF3sHeQg7CVtWW1BL72XUbIH2MfuKCIyU5+tk/cUVQMjklIf7JT43BzwB2dd8NO/omESkG3mEXzR9qO472r6TCRfEjLM/sR2He5SxydE9z5TpoMkwnopT5bujfhDrZE2VY1jBFGOQz9a/EfUD6lEzHIxvebJjbAJ7g1hPcE/NxPeeoCpBeoi80/NbYdamhZ3uJQ49lj7FF8VeyMikd6bvNFU4ge1rmWZK3+VJlEYW5ySOuU4WNkNQhVU2gkCxNdoVhF72F+9OexupU9XBgc0G9wmRfYXm2pv8AJBpJATG4Y3QPIu03U8kDQbWfIfxd266xcVvUW+oHrTw7MZjq2eGaBB0W0H4KV/jl1N1sxt5nHuamR8ytuvvUMZ7LP7Q49mf6UPkiEWJ/aPnupTTXLZm6/i7kBDC/GH3syymifgE/J5O9kj2G7TZOrpy21/ii5xOZ3fTG9DgDTpZRQ4YhOT+MZKWSmuTJn4KaQSPyaGgaBEolZq5CHqYR0Kb6gdw9Q2PFcSuPkmYRotsyWETPir9QAtkx3Eh8bLRbRk6SsmPvW+SbxBUOVHB+xNN08eiU7U7gbG6iNDIOzgd5qe3RRRcsWqq6bo5sMYNiOGxOgUFK2N0b3m/o3smyYWAPH4rqSpbhIjjAvz5qywhYFhO5vqZT9E31A9ceDZ8JbSssczmQuzqtrSB1Rb2RuHUbOZ0dI09+aklwwvf3BONyShxBUf8AqQfsCabJ8noO8kSr7o3Na8FzcQ7kJdn6gEFB73ysey5wnQ6qoZAZ4XvHou1VZS9CQQfRO5lPFFB0suZIyCwdHTBrdXD0nKapvbDyCLnO1Prb+SHqJQ6w74I+klYzvKYGDROAzceSmf0kr3956loLnADmo2Wja3uC2vJ0VGWj8ZtuHHRj7LD+wJ+icfRd5HhZI6N12lMrsTfrS7yGiw9I1vYbH4+kVO+F+GEFx8s0aZrA5znYrez/AO0+eIta8HPuIunyOecz19uud2/Uigh1h3bJgxyPeeQyRaWqrnLKR19TkOq2dF0lS3ubmsQvZbcmx1AZ7I/tDqKT/Vh/YFa6lZYO8iiFbhumyua0tbz5pjnNNwbep232VuoGp9SKCHWOTVs+mEVOwWz1KODmtqTh82AaN4Lq/DsmHDCX83f0pXsjY555C6mkM0r3nmdwVuEFQP8AssP7AmSWKmIMbv2njAKDbev8imepHr9nRCSqbfstzKkqeTU6Uhrnu5J+ZJOp333BDfBCZJGtV7ABvJbXqcMYgBzObtwarbrLCVZywKwCpf8AWh/YrIj0HZ8inDfZYUAPyF/YTfyHZ8BZDjP41hW0pxdsTOWZV+Ib9mU3omQ89FUPZTxueeSkkdLI57tSUM0Bx3VHY0UH7Vib3oyAA+S+hy+CfFIztN/JZToEPyCKMyysjHMrAA1rRyUrmxROkPJPJe4uPNW4hugi6WQN5c0HZBrdAtr1fSSdE05N1890fDhKDE0MGrbqB1KTnGGlC1stN2ElCNYAp6D8UfyRBB/I35uQ9SO4dZsiK73y92QQaStqyek2Icsz1A3UVH0cV3auW0aoU0dm9t2m+PTdZYRwXV1FUSRHLTuVPPHOMsnd28N3VVGJhibk/wDtOaWkg6/kXNDdf1IdXa6pYm01Oxh15+akqQ0E8gpJDI9zjzPGEFQw+l0rhkNFNVCOMyPOX9qonfPIXuQWE9ybGbIADqWvLTcFUtY2f0XZP/tWtwVlGJm4m9tEFpIPHf1l59Apu+3qQ4zwbPixzYrZNWBzltCWw6IfHcd9t1t0EXSO8OaxNay+jGqpdU1T8o3YR2QmbNqXatsnUj4tW9aCQbhUdYJm4Hdv+1beGlV9DjGNvaH88dlYrNX9WkOibvv6iUOMob6OnbT0zcWupU1TZrncgnuL3lx1O+29lPK/Ribs6Q6kBN2fENSSmQRsFgFhCwqyc0FVVHg9NunWhxBBBzVFV9Oyx7Y33TRcraVFh+tjH7h1NgsK0V/U3ZlDcTwnqzuKHGUN1FA8vEmHIaJ/SkZ6Kqn6R1m9kbrK26Ghlfr6IUVFCzlcrCrcZF1WUnRnG3TrYpHRvDmnNU07Khlx8QrXRFkxOaC03VdSGCS47B06uwWFWPcr9e91kOC3AetKHGUFSU3SHE/Jn9ozsa30BYBVVcZfRacv7V0AgCdFFQSv7XohQ0sUWgzVt9lZWVlbfZOYHCxVXTGF/unraaodBIHD4hQSMkjD2q11eycSSnQNfGWO5qpp3QSlp+B66wWFW6slHMoDcfUyhxtjfIbNF0KWOL714v3J1WB2Anyvf2nboonOOQuodnuObzZR08UfZarcNupmY2RhaVPC6J5afh1tBWGB9ndgq99FgVgi5VVM2pjI58ipI3RuLXDMeo2VuMlPKA9WKHCKaS1z6I8VaFve7+AjO+1m+iO4b7XVNs0n0pfko4mMFmtt6lUwCZlufJSNcxxB63ZVZ/wv/wCpTnLEtUBYLaVGJWY29sfyj6ndXV1dX3j1Y7go6SZ/K3mvosEecj/gjUNaLRMA8U57nH0jfghppJdBl3qCkji0Fz3oZc100Q1eEa2n9tfT6b2l/kKfvK+nU3tptXTH/kCbLEdHjddXV1fqKym6Vtx2kQQesBsqCtE7MLu2EGrRXTrLaVHb66MZcx6jfddXV97u5AerspppOy34qLZsQ+8ffwCdJSQZNYLqSrkfp6I8OFkN8y4AJhpIuReU7aB5MARrZjzTpZHauKz4Lq6DimzPGjim1s4/Gm7Rdzam10R8EJmO0csaxLEsSxK6urhVtNi9NoR6yKV8Uge3UKmqWzxBw+KeVdYbpwbbDZV9GaeTLsHT1cbiUFf1KCimlztYd5UdBBHrmfFS1FPGMvSPgpKqV987Dw4LKw6+6urrEQunl9ooVMvtFfTJV9Lk9pfS5e9fTpl/kZ/Bf5CbwTtozeC6XE7PraSpdTyX5cwo3CVoeDkUBdBFSQCaNzX81UQPgkLHeqnc4+pwwSzOsxqg2cyPN2blK9kQu9ymqnSZDJvBbdf1i6ujvsmu5Hrdn1nQuwO7B/hYsslZXCxKtpRUx+8NCntLHEHUeqDeR1B6mlonTek7Jn9qNrY2YY22CqalsI73dye9z3Xcc/yOy0WRTT39bs2vtaKQ/tKcX3QuUBZF2a2jQ9K3pGD0hr4+qEoepUVBjtJJpyHesKqqkQCw7ZTiXEknfkifyIhAoHrdnVvSjo3n0h/O45oMCcto0diZWDLn11t54iOu2fQ9J9bIPR5DvVlVVAgjvz5BOc5zi52p/IbcZCah1jHFrgQcwqKsE8efaGoTbi6L0VhvkVtCj6B2JvYPqGp4yL9Zs6i+kPxO7A/lBoGieWsaXHQKpmM0hcfh+VEIFA9ZFM+GQPbqoKlk8OJvxG8KcMkBY7RVNO6CQtPw3HfdX4LK29ybutxOG/8A/8QALBAAAgEDAwMDBAMBAQEAAAAAAAERECExIEFRYXGBMJGhULHB8EDR8eFgoP/aAAgBAQABPyH/AOlboD/bP84f4suR8c/xRdj4I0OH7U/xJ/kROx7ITv6An/2Ern/yvMda2DZvJ8kiRL0DkuRBf7Yv+yEnHuRK/tGCBJ3+yFxPYL/iBGf4At/5hbnus6cbpzuVeUWrzcSGBCZCZ/2E4U4D9JpvCj9fbSUsuXlHYh2okkkmkk0kkkkmkkkkkkkk1JckyZMlgZBLRsovLPD69H09v23qP1J9Kdc+Ad8OsEUk/ZgRJJJWX16dm3/I9M+jJOkJJJ9HHb8SqTLLIS6s3rb8n14ufuodzA97fqJ2dxAiRI0Gh3kMkTJ9BvB67URO1srd/P1+Rp+Sx+jAkqLVA6EDVNxa3TZOahwYEsvwInkZL68+2GG/BkIc9TpFVqQyawNNUaGiI13a4+9iFmPvEAnd6Fx9fjnXfgN1dGJCPQgVIEE14aManWi2YIIL4l60T9etB/htUCPTisUnSJqezLzIk4ThSJDW/wBeuXcvIx5NvS7uBKFWNcEaWhqqa0ShMN4TEryGjpE/XZtWSe5jeld6QQR67VWqPOi1G71Pgs8EIMnmbMPKN9dZs034M8DXpYlYI0r04o0QO0KzDGwkbcyu5H6UoFs4sNauPrseu58NSyLbTFI039NEUBUkNk9nNEg1yQXCIvYZeSxH1yyH+O1LLRG1YpFWV8YZPLGUoF4klKZLoXcqIEsrvcUaDfAC+PiI4bi2/guPTEBxj3kboKSISUJEkkFkJv7iQP65drCO5j2N6llkEVR4KTEulzYbqb4FpCPgb3R8Db5F2GW66/2WHxAs9RXYKTBWwyBrj7F887iGWr2wKcpYaOE/khzDV6rlV27LuObyHUkka7sfYGh53Gn62lfYe4Orrk86FpT3Eva7ss2yLyJv/Ybt8sjWHZ7iRsSLFo6ksr7nkEKEmcCW6JUswZPEPBe2HyjBG3yKNsMTd4HU3+RK/wAoXd0OsbfmOSSay2HbcxEmP1pg0Ibfg3Bj0cvTGyFEfbdhJMbb3I7iWUXCfuSt/oa6MtriWe7ItofY3WNzjkyb9gpRgKbRXKR3RaDf4JluuPuJpJ33OF+BvDbYk8CTgJc+x/IimPYc1VSx9mSte31qzXcjxuNL1rCugtK7EctwnSwmLBIkRKG0pQScIdISGGLjBIRAecZHXSg03ZQthJNrqQhNbGLMDNKdpzwQ04eH9xWQ8kuENWZe8FxeHw0WK7rKohITZyNHmP7gsfWYidn/AL9BYJ37wjgkAVCwoECQgirQgp3wyVwXW4gtemRVsQNdMVlJFTwxV3wy6Z8MvblfI6SHkSJFvTGrdGLSUIgnnkyOdzJoxfWGr32MbuW3NXouTuOOG92w2m2WklVvYUCFqlDqIG0GoYNt3GWCWSlCD+RUx8jauJaez2HLAc5nCEvuoSltzI+Ge4uNS9lkWcDGMDky8HMbD6xHLyl2Q6urPni62+3gclNil29bLIsi321JHkSNhHYS8oWcxJdTyQ0kbt0K45LNhotwMicUiEJDgxEJuNy13IaSsZZCkEINIWwrW/bl7x9YeeVlQnXfWt73qzC825x00orA2L7dVWRCSXJsiJCVQkMjkQqUuhJWsxrNMufUc1DXcYSVIymGRDOPsQS4Hl2RbZOha3qK6C+0eH5fXGMdHDTTI2wtG0fHqqodclu2SB3DQUysjJweyT1CeKIGiKcg7PeQ1CG0nuWOhbcQkkZOBS/Ajb/0SS9GJrsZMsZDgNcmAtx/YuS+tsY6z9NyITCi0Td+whbOxkFjuSgSnT9yc4IFVqGFyJdBtBO9wgngzdDXA0ch2FDu2HKbjA+a/ZGdxYKTJNnJwIx7eWShFjoPKfWmMdbMrh3IUSoLw3HtRVaYli1C1tKx+NBhAS34Dwi2wltBi2iY2yMOLhGHP+DmwYnAk2Iy3IvK3+5EMu4gXkfoyLHuK47lPrTq7F/7pxTIyGmdiv8AcawTEyaISg+cJy7IT2lk5Q3lkAkJoZLIR3nJ3BFyfcu8GIz2BujZjmryu4j3sx89RiWG3afYg2t3ME5Hu1v9aaovlvB07gJhuMvJxfgW0hMaNy9kQxqXKLfhJFhCEVEGOjRGzvyQ1Itb3GoW8dVwJfeRK6fgcpJ7HuUL+UfAJU9goj93Fe3sK4tYMPrSrD7BPlliiQNCGSnI5YbMCxoWE3C2HFLG3hTJkaogRotC6QTJKR5QqILCagmkxJH2E7EJ7io8k2nk2Mb0S4E1bgWX9YnTFnVglIpHYcTDnKEvER5Wm7F8h1DRWM5J1FOymJSsYGSCCNCJpAiCUveNOhsQmj+iJKJ3kuNlb7DOUnv90SlofQQ0nX8DpaELly9xmw2O31dR14GbLUJDQ2OtHKuZmcYY3NQvFyeLysdUSuSYhl5HokzWXtcfk8l0pkRahkYkQTJoiNyS9AmqFtQ2WBYMj3Mku/3FWU+Bwkn1lDlD9uYXyibBh228k5b6GIc2+412XJd/qyla98i3MjQIW41vmFZQIi1iMlkFJPo5B2N2EhDkDKvrdyBNkWtqkEUWUQIkYLq5cqs2Y/YZHmbkL2TE5bWUe45UNkMfhCxc/k2vdrlq5sFjxY9l8h4p6rxcth1+qIJbLQrKhFWoMKthEJXd2NsR8i2b3IuNhnEl+g00ZDEQ0EhoQkOxL2Ky34E06LLN3hCOLitVlzljgGyGOxyKV+NmLM8p3N4WSGFyia5HYRx7oGci4+R/d9TV1scyEqTSab1kRk53GNUUUStm/sXJtn+RE9i5RMughQrliVDaGb6lckRXY0G/BsVIrgI6o1jwxFIxNk7GPgIQ7h/wDqZvYkNe3fKEvPn2H8v5EzdbC+ooTqN7uiG6JpMJ2UXOSBoggyhBvn7kk3IKslsjstYDyqGpROI1NgIcV6V15YwJHYtDpJtfAjiWwpJRvmgza0kGkYbl+/1Ijjk5PZixaWHYi/iBSVtuOg1anaYG4O/1BHU2Q2yW9J617QFJEBlhaQ7kkbdC4lk+GKIroCzyEErgQ78OkmNAgsEXGItvA2uRckTY8+LQYtkRyOcB2Y+B9yzJa7kWEJ5yJG6BOD5bEPkhA6xpEFmJPOThOSAkOMSIWF9PkTzsqCFVugwatQvQgmf1H+MTYZ3djZroFePU7mzKWYQoOVkU6DaLbjP2CK5Li2hMTpTJXjYWzuN4o6CGTjAyV0KrFojsoiQ5osx6P8HA9kkobewztPDsEcVvAloiLGkTsGfUZO097fT6P+EMoMTmfOhj1GyUthDHdfZ+RXC0iSayWeRtYLGEEMW7sP5gyLWboYl70LkNYe+YLV2lnaw/AWkIkTESORo/tVdwwO9ijDxG26KY8it0IhM9S1S9yS3GsKRjsNu8O5kll/TXYFhW/RCQq8T1Oqo1SBpEsLTM2/BJI2TqlhOzPMKDzQZcxvoJue9ltUNzZJBAYppDcPI2sWghCJGxCJcawsiwhsyJc3BjVk7jsqiBkCNiU3dyNhiT60jcmREBQLDJEwUiErZQYTf0pdZCltj1aa83/g8r34EFVuleIAxdzjpV+gpjuht7YfySLWc2/obJNGeE45H7pRKfQv4z+RolLn3LOiBhMVUTFUjQw3Gd9JJkdk0G1N7F6RBchd5Y3/gace7kcl2kI6unkHC+RtyYlwEKtGeUEYouqERkr6NueUxzmU7c+tEvWRVY1YQzI461kn0VpFdZOjG2n5ZFYsJrJsW855EIc+RUzujYx284FMlcFcimJ0swHJnsm4tKsvgW4SHvuOoKbP8AJO24luMIcYCETMSdxLV8iTsHxAxvHSlY6iX2NjCS7skcBH+2ZjeIJpE1h/Q4FKls54P9+tZekSqkbrXJmw6i5mfuGSST6LUoty78HNQxpnF4sNP8DVu7CyZewnK4lDUIcJcgSEdt/AisHa4slB1hHLREZI299jcwdK8FuXcfGkTwds7saim22WxZ2CSLvcm+L9SDVwx1jgUMG5YGnYk2qQcq25ikh3CFu6F+FPl9yNoJI2yxPZPfYtUE4MPbh9C3MX/Sk1ZRI3UW4ZcxHsBBUIheCfUgcGUpizlZ4Dkx3N4FBFjKb3Gs8sSJS/BPZPhEvaUuhJoG5WT2/sU5UkugZ5fUWbR2NhcZvzgJeg0WDDkRiDK5F7cvgmUJ3Q9hpstiYkJpQrnLEKy34GpFz7nBcG3yPwLyzwIgJmPuJq6pGAgSRIPZinC9gQmSnv8Az/tREtMY+WJGxiAfwWngRV7ygNkk+hBBGgiIsu4uBz6jXEbEIYUvqNa7LtkSpwZzibGJbfrI+Fr7iJs8LIjChN+wnqJjoiG4Ywl8WQyPnqTcQLC8LyJKwb3EtnIZ2uZeSYoLF3gS9TMMXJ15nhkVle3R+R81IWmISF0Z2IYJJLZGQBGSSb2ZAWk4V3yJf1CdTq7lYROIvwSr9QKFCnxYL5WdHP8ALWy0ED42csaBLbvr+alGmSLfttRbfn6vg+K9KKRoRCkaTp2EqONhL7BIrdCK4PLMhNRFhNG4Sq18sMKUCXJPtJgS9yRwm/aRssSnSDzdwlu8OxLveTIDgDAOIGEn4PJHG7E3Gbn+Q09k5bu2f7OFkd1OyLZY4GcujZPmEoPaZMb8GS+YkTp+HhwRkMQfjnEUmPs9xNJKcr+MndKssjX2wwvCIVe2u++iRYF1EcMg6BpfCRIXbYEvXDYBXfL5IakyrLduDPG9FvkkoPrcM8fAYfaIXSfgoA11mTtTZdxOcGJOH5YsXU1Z4o2MBI37GDuyRP4IXdm5HexOwge5ZWuOT4OuHuwW0PsRYJad/cJLE0m82E3Y7KRjk9ibJkkMlIiTEK33IfZCWnaMIBPJ1Yyw9rES5bpNFNJTz9oggt0XhaETRcsjabQmuDbfsJFd4s/4koC7Za8uf+HNke5jGNvL09uBYrpQfX9lyTXtsuBpstyzNn2DYgSd/Yp6c13849vPjYiYpmRu5BDbKQL6pbN9XuDLGQSZY50qV+RKn8xJQLTW5F3cwu+x/QCRIQ5sJuRRrjmcgxfuJOEJNhnBZIuJ/A0Vj7ogeZ8SWRHyHculeSbt9qh0iNoZibYlqSIOmakHSM93SaSQDUoYols1uLYYtk01uhx+rl/4TW7bOXwXqmQnC2RyolfuW87RLQ6dioknL9wN7Oy4GOHJ/wC1FgmlcjxOtC91Vx2MLl8F2U8LhCd6Kb0nLcEcn7bpTaQ23CWRjmWhi+6GjlxZRhYjclfc77GVyIAgJNW+TCXdiaHchxdocFgT6EdRpcCbcNpgfZ/wSZmyFt9lyxiOfgVHogR0uRGR1bIo6K41dyPeNLsmLC4a5JUnuhgE7v8AAG0k23CRIu959RE5Wu87HyOiYaDq6ZO7g6iWxs7hN+BCSSWShDQWY9pdholnSva1EdkiWzwp/wA0kOfYQth2UVJn7yBeEIiE+zl+B5qw1brlD+5TwOdOojb8mcxgZV1ci3ESKDuzOBidxTCXPghLAlCfBbfLLsIaTAhyke9h7Z2XLNtfgWh6pDmv3sIRzu+BYo3RJWEG85k6reRODIVYTlMaZKJT9eXuMvTgUDG7sftYUJZOTzomLI7l/MEnJhiY7vfhGCTdy+TImhkS2eDBcKkGNO251lChrdDveNaghucIpnRnIYRitT3Y3ZDnC2/7DNtt5dTGQe+TZlM/XBNITYl63FxYaeZ4Iugr7Doa8OPP7G2gOvkDefApkMeDbqbS/Y9CKxdO+whl2fy12kWqvb4EzXFk3TGwWncT+Res0OduRkkJktjbIRwaDuH0RdyHoYrNDCWl0SkS24SFQtc/8CRQTKXruaEGmEiRCETyhKBrCQHgwJiaYxFlf9M0pZskpZ2Dl6DHRiVxgk3cWzGSsPkzw8wS3gUNri4iLlf2EmRksCkjpE97EXEzR2GznIx/UAzWk8CI9JHVuT5U+6PaUbsI3MVImE3EtXA3GCN21mDtNefUgxIls2obdAwjrcptAyS95DWasyxuapXecHsuRAS8Eoy3cHR4N1DL60S+gzOiY7xCfbRDyxCH7tZoiorG1S2OSkrlr8heR2k8k7raJ7BOqNrhiImXbZgZuwrdXPqOS5QvcQiS2UewkdAL5GbWgLmlRYVWxDaSaV3su71NkCz68UbIN0UhQWr6qssQhIs1esuRMfJeYa3MyZUyWx1lzFpCsEZUiFZIXdjIYbaRmSVh0jSmouHWV7nkYQJhQfA7SafImUEo48KPf57UctsfD6hHk72UEjoR+IMLKImiu2zfQqBZEkfKEgYv/ik+ipPwJ1HpktuWxvQzolidA+9ocUQEsoR9JEKm76hUsb23slR0ZuLBG103DuxVcpl5GOUCs99joSI0myCNhCUkrJCXm+y67LtcE1pJLLjJSZk23LLnU9HaqT6aaLhF7iRhTwTJvvd0liR0mHYlqjG6VsNljyZFkNeBCfCvd6MPhPnoYfL4h0QxZAtYEgdb963N0G5Yq67+Op3DT5dOyZfa77uR0ZAgktkDbChOVQQqcf3diGhDV3hDb8D/APmgYtMjYy4jYJPLGm/QhrM77DIa1+rDWiB4IMa+aIiuP+aP0XRWOsl8COm/2jZF6IWA4psRNhLVZliWLGMjI67n7fQWIQlssGz/APsydFvbCvFNHuqfxTuBkciEiW3CRaG34dBJCSoN/W78a2bphpjuiywsaGV7KLEuufAhRaEjY6JcSn3T42EklCLO4dHxBjY6Skm3sTI+5wD3T2XfcuTojQ6otRz+4R33D3ZJlyYRk60ImxsOjG4b6GV8L6D8ub9Y9COj33BYJ3CwJRiQhYgReZhwuR5s3snPw9Oo22M5by9ffVyx+tG9MDkRqXmgjvAfmj0SToy9wG0oITvDjuKWbZd2IeO0PuGRBYXvGL4ZHeyTbby/RehyTdwI4MXsIhTgvyOEncXIah9kIkOQ3Ri5mBaGY2veddxLF2CwnudXWbplyXAlLHv8ILYkyEKfTC4LBf5jC5fA7S57a8TCtgS06DooocJJIS13WPbbd23L0vU+J4O7ooN2+BCqn3EZEA0zpLLl7vW7GPgVPLT4LH7CQjuxWQlzLjQyDQ6MR7D9hC/CJ++lo0JG34P+HUPhE6j3v2gRmnhOo3G5LMyLAtArA8hhFLZZfGv59DCltVXQrWq6Zk9zIib/AIB6HqY2c/RPcxpd8ER7vChCLodgxa6qLfbLdx5UtuX6L0I6gaiPLz5NgsQtDcBRkDZNeqHoOXlJ8NMFWXRsQ6PRYWq/RDS+R+1LgYBa6KEKBKdsy5fHotcNZUVFkWCxHZ99qUjt9xvR0euYtbwyWK/zQohCmuZdSZ9g2SUt7z1kTcBF7iEohbC+EYhGxckZuNwJSxKNDriJevffSx7OGjWorKdEiQJbsabn2SXsWr/oIWzudTWjwAufbt0XJMufRxEbVdkFkTKEK3W9+bjXOEb9hrLLH7nOmNCQpKN522OxHK7PyqRB42isiOPJBgjmMiTH6iIERc37BI2EftCQxXNumcGBsQyJE6XV+vEaf3C3oRtjX09svwXMy/oMbF/mMT+0jjiSxy+Bw938UXoNjvSYY6YUYZD+EUQQhlV2Q3G6vRAkN2WZ7EJCEYsJvJcUbm8iUUWUXUgfCDdjIyGnf2i9VVR1AI2p7P8AAtDcuEJCG6pPoo7U1720/C+ymGqRnJ82FCA9/s6E73bFTpdhf37jrVa2XVk5UDoYIzTODHMaRd6LbzY30MjQpIr3t7EQRPv1wQKrle6lpLhCHm92/a4lA+p1fR2L1I0e4HuxKnWJnyNeYQLC0ZI9Lok0zvxTokPJpDTpQqeyorRfsiAf+ATsi/t3n0F6aJEzSYYxGJgQcETwNbJMsWPBuRogZBBmTUhbkJIRCYyElLGNv6DGjtW4mTgJ+S4VCl/Iy/1j3vTjSiI0pBwzLzdTd9xZEhuqUenwJqeV9rRCltXsG2Hq80ai2IImTU5jY3+FZDkyW3di9PdPcXyEjL6bxRGd3J+R9UjJuWy3qaIrKaxhd3Rix7PzkglEyXFmp2kX4tfevkgbZnvRYLwvQoEtaVzph9oR0q+yPAupbGxISPU4FGrurSPhSTNkv3Hr8fvdDHRMHsOD5nshqcZl0XpNCZYkRC9Jhmb0OlKjYYQpabxDegxYLn5fmkPO077hJXCRY4HAKk+QkQXqsofh/A6gIiEQId8K97aIMIT1pqyRpdv2JyknXvZhEy2DuuLiT88ukUS9JqqQ17qMbY3InkfgKEbm2bUxqZA3jdCkkDspOvJHZaGLlCM34JIluSU1gTzRDbDH7EubufeinN0SMp9hTZDrLFhLuxUnT4BxsILrG1E7N/6FReF/DUiB/tJYEiDqw+S9EKML1KKJDyTofH5eFjStTdMjcggj02YgqXoThxR2ciyiJ/lIIvMgc2h7PRRNQ/70cuWLuxYWiYnqhHfK/wAUyTPyDqiu7y+DdWXWQxZLN0Fd7fIb3k3QxAS1egwLoMUNwe5HLsm1En13tptdYldHBco6tkIY0sReuu8BUYu4hjXO8YMvGx1DWM3Hr7KfsJncEfYPRFzI6bJRq/YKqyI+4e7JQzJbEJy1uDDcwzdjr8Dr2CJIbsvZCCVtqx9WIFdVMcoZAeNiWYy7sjLkUqcRazrJ5PsNg5ES+fxFDZcxfxZ1yd0bdR5QxjY7rZFuYloj1F7+ulhxTcthj7AyT5QIfo94yeSK9p6OjyqhLxWdZ6VrhdT8t1lnFlbwyyPfZguovCFnwOSO03uG4cvALHpXpAoab1vhf2Pyq/I2RYmS7MRJ06ViG81MIyQC9fFamk008CvPAaIbjkapR/Aa2oXc2F640iLcJE/5JCSnU6qTSW7OiYiDo5+Bp2IDw/gWIksNRFn0RBGCgUiwuN/vnCLOqzh0ExyWnGTvliZz76q5MWneEwp2HVs8fIPuIt4e9zt5IPs6H5J2+o5GWd2TBHyiCEXEJ9z5Y2uP08F6Civkvq4IElSSfRnVnFhIWhllmJ5T7pdA0TsNG6PRtTrj94WB4SdQx7vVNzz5q7Tj7Ukj6MlMgmFcg87j9EsYmm3luk0WdUi9h+Y7bjHKJ3U/pYpOq9OdF+teaxbo5Gm7Yg0m5NZSUJ+pinXQdGKRPj4riPML0v0gg2OpS+B2Tpu9uIR1A+9odyNCMBFPEiecGya6Mt6kSuAjCFMmy/wUERrnVOnZ6mfWTNg3suKGNEEEOBoW70yRGtPoRDZJJJNM55dOzEdqsnTM8mkq5+ZxpKnfX4iDUM+g0t5b0UuCGgMqsoVD0q6q11iDXHSZvgDoqQSP1Y0w/wB1RgfoQNETpLKVXTRmAwMSMzok7W/MVxpTx+euKIhwyvdkyklFwTOuwsiL/lQmHH2iQnUk7WnBkvxNdiymhuc6LpwKgBnCc8VeibnfgODHwSZZJJbC0zrepaUub92S423fdkj9F1gajEGCISHWGLkk9a5DpJLx0CGk8FJOmTcRKG/wIgRFyHfshriE0T+MQqe5ecgc3fvFY0dB9CsAh7iQtKNzRBkov2Mn4wEuXWdF/e4SCOR3+0f8IhZQsVehCSlsds2y9NLpGl64GtEiZOpAhojdJK6wTyAaSPNxsl8P2qWpEsW4/AnCJOA73omMcDAhJfR/cuJTdyepssMlHkIpanmBIMlJ3whTbxhnfA7vNt6N6We+fyY6CDOEb1kbokR6iw0ckj2cVn03pirWpqrQsM5/EQuoUxUehHfin5NjpVBU2h5MqbX0/IiSndYxGhDZveZZyytTzHI5uepDRFPEhuWdYWYifTehUQsiVMY3zD2JbL9Z6IIIIIo0QRpVxLvLhS2JGToWpVUnj77WpJlJg6SEKR/iTA5XNn3qk8KWKVKnxAZL9w4ZgnLJl7Drts/2PZLPdk2DwlJ1fxFEqbTRyQ+C5Ix+tqCB3DkaZ9NCqsoVipGbp10+g9Ua4I0EjrP7hhPL/wBpGITJJ0I0Fu4E6EiLUdTV81W5mbtSyQkL4+1RKVyiq1Q40tm9zNXMyQQxZdzcoy+hxIDjcb5Qy2EyMWHdFFlxuseRjSWeRaJd7q9i541koRDWUcErdBsScXVDZEuCNnQ29GSaJo6LRiGUs8DD5ShOoeXLJb/gP0HkXofIfkQrjSf2kdExaEdffvCY/kD8G9UhTPS6wK+RWSpDwn7Doz5EsZd3CF3omh2mPA5q7sY7sUNmt5PyPrTN2ZqijxGmCRbV7aBjG3LY0hnKfcENi73m9miBLII1LUqJaYR4sXT9eNiIGtDox6mMQn7DY9kM3d0dELR2u2xWJlz+AKqwqOJGOfu1fyP2IpOGbJCT/wCYe4x4Sl3ywNJvljMn5z8ISEYi+KdYQdESC4j2ojgRJIWbsDbG2XRCI6AkWp0voVVTMn5hjG3dsj1XRaC0MYtbKCEthHwX6cfaHR0VbU/YiTcn+E9riIrtdRWRAemir5lcaBoRHyCn/g3LL/cOu2LyixwOHe1CQlRbhvkbPKYmJE02xcwhbfnnJd+BlLsca0+BkDKF43n7G7FhcImBjcC+PSkkuQRrgVGsx5/hJHqYxakOuivkc7EFM/yo6p02QJWyDmUiBZRsX9JU7fl8ECHlf6vowjIa0tyxKmNPlED13GyFUYlSJa3Ci1kRQlxS5Lqx2QqmZITFMsLeYhGh+i0M+j/inpfoo0S7Dhq33HR1VJp3x9qHMf8AqTGVMQhX6IhAkqMTjTMYkbG6p0tRsMhRvD3g2Al3EUaWP0nh/wCUY6LU+3w9hCJrGOX7oG06PUgvcm+SJn6mWqW9C3ei39lXyJTxBPgehhsbZNAXOPuP7qNnSSaKhI4wZBGZZj0GP0Vcaycv0o1l6L1qn+sGWSuckPsoQ6oVEi81lBWTrF9yq0yPuCHd8glHeDHSRsznXOF8m4heX5MaeQHbJ0Wkkk8+FBPWTql1SSaYiEZ5JJJJ1v0sjF9KdZC1oZA9SIeghaGjyc93TcdUKopxFfAv/BQeR8iWEIyFsp3N+IqTNJkjELLeQgkruHYVHcHjubz8J/oQfEh9yK8sz/ULWmj87P3RvVEigNDVSCCNDfoKu4ufov4RaHS9JqWqGvL7jlbJ1Nk/h6J08XyT87iXOn3iExUTuLFIGcvELwkd+kjCj5VpDRDTuXF4orCT9VbT3BN80fAvhbc+1ZfAuwmnasiQm7pPmaTy9ofUgbvS5bIwhQSTptpb1KirwJy/r/CL0FRjs9LVO37hqXAxW5I7f7j9xD0MWaOwp+wzYawf4yhVQnT9xyOCjM/rGkbWgxNv9liVZjrcYxldOGIrmJLIJKSp9mL4WLjSVpdRqUGKxmpv8IIZluEJXpdXtGZOXqNfwRihJpiiKzpWtu76HP0X6JegqPUxq0/aPGthL90h5G5qqtUQtZn+bUxK4GY1SaJkifv5JEKPkqOWrhJphej7x5hu39E5cNxRskBYSIFzuJ05vqSNSFWw9B0DM0zSnHGCVrKEKKhAQmTWiat+m6H9ox9CfRPWehjpNELmWyv5YqIHWSW8aC50RRgfdPZcahCOH7HwEpFVT7coFS9BV5KJXBOHh4LHaG6wZn0qqhsuH7l8JhpZajJeqFOkcKWKnSulaSXuJqlxm46yeUZCRSNxnkY3WTAiseu2x90w9F+gYha1ozohFuX3YJq/cdJlfkWsi7ZLa3hLLffsMeZblmBNYrQCT0FeQSt0yc8NlBmpK6v9h76nbDJ8PchCWVx5FTlj6dKOaOyanAkQkpTsKRLbqEnso4Q4lzfXVCEkseu2Ku491LNL0PW6i0uiqxbCEMXbaI9MpXAmtgHvt1kVmjdVz3ZJeRO3oQtkujw3NzDTAkfouxYWP9Kw3cbJpb2Yi5vEJO40pXn9FlBdnifkbhR8ftAt2+0PfA4vcx6DJJJJLEDaq0RR8GKN0u7KT679AMYtDLBCuIXczb2XIJPvejKMR3JFdI3dvmGVVoVCQS5h/wDlRbUkZJPBbQbXTMcE2rE+nFJE6QRRBFCqi+hIaXdaxR+o/QDHVVQuH8v3OrIlcjarfNW7ERSFR0m1XfgMJUOZ9jJM9kXEbokTpNCJK/RD7g8/Y7DZsNUdGMIR3FvRjRBFJ9aYdwv4R0IWljFpasf8xkRqEbHZfkZvUslkjY9QQzd37Cw0khH4Rt4pMxBqB0CcJ3mkyegaSbqjaFyQRI3eDrYltWPSfqTrY8N1Zj/BY6LSx6tiM12ldkKTuKYL3JKjpAqki1/DtH32T3fA+6ZTFkhMUaIRYQ2MOwnFGXd7sN//AGPbi67CSJ+iBtFWKt8ekxm4tLHqyoLRGiEiXsbG6y5ZnFaWMNaEIQx/djcITFwiEQEz3xRmxk0uJnQRuzAnSyK80yiBbOEYL1Q2ppqV1FNPLv8A1GhNQ/Wkb/iNKJrkXoMdG+ox1VJHxGPumaZcoLoyKqi7Ia3ef9Da2xHT1G23LpmE5EzEis1Jm/U2GeegtQQ3QshkQkBRcI7qkEUn+M2TSSaTZsV5ajI/TYx+geiTJJS3g2rE94gtalsb3eQY2RSCBBBbuzbeWRCkwuXCGP3eFwuBJE7DCF1InROhXjNYYoTl8AhRFIEQnyLIhp3RFYQ0yehAms+jI3onXB1LUKkdD9NjHQtWQhUet5XfJfNsWp18/wBRZGERRFCRZXjkOXWlkvsif8ONi8eUxfs8q+udS0yGhSbCBMRR5E2vm6CNTShKZVEkk6JJJJJrOqKWkFtWHNHR+ozOlaWZDUSbcJFlE15WKmI2uR8tyRYIFdXL0cn9xh/XELsdDdtgSERA01KHM09a4GvUc2SYYjuj16kCQoqxlBcrT9GP0G4lsOclRJJNZrtVa2lFtSBSXFR+qP0N1kX1We4bIpCG6X1fIlLqJbJSQLXuZPkYxQqnRAlIaHMTflcaZ9CDIjF10P2GKYwDoFRg0MCbt34HqisjZlD4sh1EelAFkWKO5Mg2GNReix6WSSR1lrZA/PYQpKfhInOssZWI0NISWRD/ADBBb6nkQgiuqyCKGFEp5J4lcsx6pJ04K/cQ3aU0SuOETkK5lIYs/cWuaIilyE8qlIbEEVgjTYGZRUbYRA6MdF6LHWWiaTnsXfpy4liXqzPD6bUUJ22RDwnCyKLHfcWhFEEa092ZiY3c6prOic12/R8k1WxktxKEpDCqFv1iK4yGtM6ZJrJNLqFSCCKmxWbgS0sfoOjGOsqMSbcJSWJXI8G4bQw12UdyBMySUsjbC2MSSEE6UiKSSSTSRsY27GQkOGvRWiGG/pgdMIkQ2EhAb8IT1ZJpJJOgMst2kSbcsSEMS3epsdF6ToWRG7JGUhDVuR300rk2a3XQ2wch7wIZJcPHfkV2n6Uf4gnf8GBLIvyJp4Y9CSSSTVimLs+R6T29NDWTWUbAf3XIyZZASQMuS/uOLYdX6k0ToEyQMIiYFd6mOqF6LOJeVkRjc/YQhlun8s2gB5lkEEDV7pZL13kwVAuiC7GWXklty5JJITCG5h35OXdzbzM633GMGQ5IkSJAiNRhfX26LGT6SGCwGaXZwyATCnLgmmoYwtHuvxV+tOhEiTek7gaidDGOi9JzL0/WEYbgQiF1tRBBOh2JrGtUklRIWIxIJYlyE4j2D6BC7ovbR4Jk5qlPA5RPpIQFu/mRNBRKOEWjPYVVb4C3MYfK9N+gqXQqMixBIncVJHRj9G6ty9l3IODmeEWKFst2TfZue5BBFDaQ/wCAms1kmh0GuBtPI3ROEeo+duhWMkLcNBBkZsgkxwyGqv050JDcCbjeyIRAxoWRPQ6p1ulJzb9gjKqIZlx/YdpgiswTIyP5bQwmxxWYxWD9GaI96h9huSVhTUtyexGw+s4DVI0xV0mkiQlTLNlFio0mhoi9Zoxj1sgSklksFu7wLjqxtRtu7q2n8gT9B0ao8ormsapJpIpNtWfAUJWJBTYZQJutx4Y1FHTarpI2N0QSo0IyRRUkQ1FETRj1Isv0J7C6STbuT0JZLdGNshkaX/DT0XERogaoMlZjbekqQ5mSmfp1biyGzhGbRkRZlln9ljoyasbJJEQJUYyiKoVVeYehjqqug79+rgQJJCSshrsIlsw9bOEST/DfoOipIiJGtLVJKsyXRGhUTJHDwnyIHa4GIQqgW1LGPjdyq5JoYmkCqIawkED0kxLU71//xAAtEAEAAgICAgICAgICAwEBAQEBABEhMRBBUWFxgSCRobFQwdHhMEDw8WCQcP/aAAgBAQABPxD/ANU/9A/9B/8A8zT/AMh/5n//AJ6//wCPqG/2ERUQfjEtj8yE1NSCv8Ry1LQSB8RogvhmjVwWypJ9oPJJKhviGgX4MH0P3/8Ayqk15SkYMjuzlntxuwwh7I+7Pmz7Ri8+LD3ZrzgMn7mUf8mAwFUtWfiel/bT+2Dc7z+YB7/mZNv8yPsfzJ2fvy4Qz7fwUO392f6Fhv8AHJAwYvaZWE6l0jVY/M9X99kPs+wE0/1FX/PokAC18BGCw0/GuJshMtS0ItHKDiWlpemPARaKznkwReXl4KLgvMt5h50PLDzTulSgJ54Ce5Ae4ApFuKS7jGR2f/VP8Tgut9PbEVWfcEWXLmIvAwSWfgs5X8Hi34HC0MshFXcVws5Z05a+fEi0AADQH+eewT+wlRw8JLlovAxeFhL4tYe0pKSsr5/Kvg4RWFiLOX0eWplm24AhaBxTs/F/9XP+EZAGe3BCDKq5lx4vca4vmyFvTO6qHW0PfGnU9ZHXRHsJ01i+opNT2geYGDDk5VNux7nEaibmz89v8/0Rn+qj1GeYx5Wpa6g3cF1A9cavuapljKIn4ReWEbaYUaSKHU8X+LxtUfnFx0WxqBql/RtsC8QboP8APXDCfoXH1v4qLgi5iy4/MYpdw8pXiBBAxMeJbCKe4k2QRLlRDPekEYEFMxSgwlnJEwYqviTjyAG92IQOCefq/wA/wU5/mLLfDwuKIvUDoJRwQuHFYuHaB3LKRikWXUKQRiWShWBggwWNMPwJf7aerRjkLXeq9f8A8A3vf6eLHhhdlxChVRd+IfPAQzAYDvjwynhmJM2IkLbm5lUl3DE7CH4ETqi91VLXt2hrrqMnYLJcuXL/AM0B1PddcVVavC+4xlgG4YEdbiWMASuSVKhyVxUJ4BSb4SdT1DkKypIsHa0LgMaor2UWGWlwhwf5kSF5IsvqLFrjOY94qUIEDzKlQ4Cvwxw31E4NMaZXHGZsgcBGO654uuVtKQB/L6l5Mq5lrMR8LljghCEP8ux1fBQuMban7eV98ZUSgAlQCMUvUqoTHKq4IReWNxIxXA3Eiyt1y3403lgVl3ee2w/GM+YVxs39pIkIQhD/ADB1vkxbeFixrzOybr3KlRhwCWNEIAdzERlhS59yyuPuMdT5iR4B3Hr/AAxWECLjATTXfiaOgn7mK6vVQphm/u+xDgQh/mN71+iWeYy+KBW2GIJRKXhUICKDllO+mo/bDbMeYOnkaqhsmeASnLyAhLLwFSkqxXwpNcZ8CMRQXxcIVgbMpcetQaWAppETY4YkTggVPWJcQ7Er8TxhDRgaA4VM+ImAoVR2rY1Uqf0w1wQh/lzKp/T5HOu2PDznfBLcKlVFgdOgLYmeVQPl3bNfwntjmrLrRMIRmJQO1lHKRUaJSzR19JuEybLH0QpbIO3UQ2eT0xqCnpe3xKGgl4ez5jsC00vl0xbCUTCsJKA9LWFDwxCnYRj+YuqPEY/WJJAGkSkmmbBG8KKoy9AhvGP+g4EJ9qebQIlNlKRTXcYQh/l9P/3fAxi5cS7Y4qVoO8BGKQs3D46hyi9tXyLP7Kf8SeVuswNRG8gYA2ag4pi5NvUdBt6aYV4LtfUKaPk8fMEYXq91/wAxFmNGpVwqfyQbV9ncXbC/YiA3fIg+XzYgMXZ/T7loGguXiMjqxTCMKN8GjApwiZHCMdQKp5RSUgysQVLfvuGalgh6xHVXe+CEP8tdmN+AWx4NoPB0cLw852+OGCfrB5WBouu3n1jzNk3KVWIjpEaapYfADSF9Fjtyrhrk6G0wmhzaibTO3KD2A0XE2N6YV9MQhmky7lVMm9xheOZCWTKhB6Nof9QU2rMvbwPmUe+AhZeJy2wkSi3L9YmLsP2RWNMqUBg2fHkSnjK3YaJCXngMdYd4gGdi9amwGLX08kP/AGT/AN0mofqeYRF75fw9TCWxm/R2vogtV6x5WZ9jKckzUOsUVUKGV5CGf0YDoTU3Me2PkSIYl7CBaBTvuNvZYwQEugRA5Mv/AGSmJANxUOqX/TEPQW/5GUMVvv4ZUQW+RSsbLY1r/tAhgNU9j7lDeKfDAHXJLPmYtcIjvIElkKQb45pjCz/vNz5P8QrxaonykzDwQ/yz3GYfO4Y8P7lcVBRo6AIs9zPptQlwLbbyrB00Kh5QJoiIu9wZtuV+C3ocG4OIWMLU7TCQRXEK/cCO3Yl1q06rcofNj9kKt0WfMxn4YFgNvySh8jPh4fcCeCh5JU7V3CCBqVcobWOzw8NZSA5Eah0gB5Dj6n8Dgh/ldY5Hz1HtJp8q2x4EvkUfIhtXZnmWa5OecOoRsKtekIA0nUzhaz+LHsZdktFX5eiHaYdPiaz+WpmAs0mn1KS4qpi6MB+xIoIwt4YslmmoYexeyNe3Q1/ohItJ81pgO6uGWihY7xGCgTYPjxG89AHyQVX4bVkcaws4MSU0/qaSZV/xMG92CfsiKTp4P8syELx1bKXcAh4TgL+HLa04vs0j8MpmFdaMDBAIfgofZfiZhqrVoYGeb7ZQZK1iAFCobUGWA9ytqtkAGuJGy3FdeGFr0Bdbji9qIQK04T2RzaHdQmJf/iSifBvzXmdTEsKxhK+YK4AVKRQS164rP3SEZttwj93DgsimvaKge+B/ll9Oj7NjDDf6831Ml/rxn+phZ8Fsh7kR+jpP2XNnqwfTUAStng/CgFXURI6UEX3wpcUgW8yrlnlELUMVDRnRURJackzDXfxG5ihK3KEEdTDjShLHFQ1/xEK6tvwxGCOS3IXCdalp2ViUD4We4YyjeDD5JbSaxtnS0wGRswPguOm9If3wcn+XUcUWHRCUzo5X4MQ0Dsb/AJmHw5cIoPCu0xGoZaEtRvswfdGh8vgg7UkTjdMcDDBHEJWhh6/C3o6GUgq2GGzGWylUf8Q1qCk8zE8iq/1Gtwbw/wDM0ldblj5MnfuXUM0zAC8Aj8I1arhQJRlIRXWqHtALPDM3FVFvywUQcKTxmO16/wDVr/CsUXBjPhqfpijBAgUBR+AixM3aaHUvDTEGXflljKuDD8xd9GXgiyeEuJyDFPJcKtquAMSEjFcMMGyFlh8wETYGZstjFS5MVRXiHZ1qvZLIrXPsTHGsvpuXAlpZ1hBWDa6jv6qWSiAoQkdZyl/JphqzoLYsXRk36SBTyRXw/wDcay3WOD/MKLkkefiiDIX0D6iv0Efkhog8iOzLTWRhrCXrMl7wfFM1IVLdGqldU2KbgcVpcVeEOoFVxmMZlYYLTRUcw4v+YWk04vxAhe1Sej/ZLqqqd+TTMG2TcBBc+pWGGH9SzRQ9HULI/H1ca5LgxHhEluGCErplh4wMbCyy7+4p1bvHvMIcH+VeDGICuiKFoaf+MILfsuI2kOvSAm3kBgYbGVR0sJSaxYaFlSBQNejxKWjvG2GAqXMAl6jEhuB2HUxpQNL/ALi5MNSeZoNkIJb4HkP+pZZBNp2eZkLaISKrzFnjxEA7yaCEFMG2vGZW03k+mJs3kYF1bKj7wc65/SOIDnUFxgDR8ZhD/MiT6qOzHM+j/lwHGGoUYm77B8EjjbDjyqZfgGAEzyrHogdbgf1DTgIZBOuAlsETxdCM37CAqcHFeSBR12RpD4fMtGlh8uyGJwLZ8QEPRb46YrM4b+DMBdM2eTczC7yRV5FRMApNeLIky7G8/CMCm7VjCbTXxFp4Uhyf5V1D0Xk6QRSvmFyHlCsRiduHwkRzVGFJt1hg5e2A5gh0vypEhzphtOGVg0SA7IJ1PRA4BcYFVFbZyIEkAXQXiOSaQ38QWaqwshDLeb8PkhGMq2dD2fcAEr38j1HegoHwyjIUcn1GUsq+fqNvpyfqPSyFKjuxOv4hTrpT9QVvJH+yP76Yf5d9UI2k+Pt+YYwQBALzHYoNpcMWiHTff9xxAo093pgnt1UIAlMx50+IBfOS8fMt0exmXzNUCMYcDxcXuPtHMODIlNnqKmKNtRMz1j18y4Vis/7DAOUp+zUCqdy9ryR+kCfyFSpTKIvw4ZqzonxqaE1/eGPoo/yQpLl/sIbCekACE8J8NMFMctIf5aubeoy/PR0QkOCsjv7iJUxDSVN3ivRHVg8A9sExa8jFC6aStALb8B3KgnvYSL6rMt7Knipl2Fd2bqfV+TQJTudBxKOAKgIBgTvgjTcZlHR8koYmHD8wqIsYrATTCQ5KyGXKLwwfRKdrWR+I20q0eyDbKuz/ABGAXRHwf+4FQAonocS7aaI/a/3EaNo49pKUrog/ytxX2dCMq9rDhomBhOYX5vPhKuPakrJCxGdG4wsUXY/MC/y4+mVcnpraQ62qvsQBYNcHgshaEBFIFSCZeJSCoXDKIyX6idmdDXibk7gwwS93co6f+zX8yhPbCWtvIO/lgty+AQXoaKieVMvkUaiwvf8ASFtsvnsMFYVaj2S5C6LohnRf0IRc6b9SgEG1jQ/yjsQS4v8A52UcHmUGWU+XwQ0Z3XAR+o4z2IgrWiL9wDbXtFQFGNV0zKRKyyvy1pZSS1xlTBcdLgq69YwviPq5V1AxGiGiu1BlWVz2NS3xl3BigAMXEVeGX3XXfiEkc8DZFIvWP5jh0OFOx7mgGh3FfyuaY1F5B9sv61Z/BlLi03Q+iWVYsD51Gt1RbfJgUANsw0f5IPXpl7L9dHGYOCxBDJfpRDZksxbNcVQrojN+iq+doS3s6+oYJBuG2wRw0qZjwy+mC3dymFpt14ILoGAUygy8ZfEVZEbKyOegmsq+azbKGORdRAaeGAAMPURVtisrQ8WDuEF703nepcD1leTUJ2GxKaqU7+e4yenTV2wMY2Xf3lGGSrpeq0hkAJRezcR+B/jaAZeiOqlrDMEoGeDxwTzMA1gFunURwUjMv1EhLMH6QbBgPjZBK0VH7n/XbOYIVDCYe4NqLJZu6jV/nLEJVUeYqV55X+iZMqz7YLzv8HiPS4CY1CMThQo5FrEl8WdZhKtPZIHENy4pXhvqZfWlGwEO6B5Y1qQfoIhE32IPavP3/wARre5XF9wjFunlB2iIqt2RxRc6H1D/AB9mcqCu8vcCBwy5UY3PeD6mMS/1BNsCKIRphhG2S3BFCxbQXl3AsH7orTfcpBeH6zcyRFNXYZis1dBAu8mDwkwcBWSGhFL9RUMOxgP7YRQAAucUEpAh1Es7jBCtwYcOUkQYbcEIBtubaCmEiS6EuKTXUG8YsXecwsCusNO4+5qKuhjQ1n7UPVi2vQNzHMKFeibRqCuuzUwrkKyVviiqV8hNGn5H+JSp/YYmS1h5pmeXITZI5VX4ud7V0EMqo9qGo/Zgd7UafzDhyOi/5YfLHypom1pfuptsaPpgPXZ+qsjoU7gbtEKxpZfx7gNHjwQyojOXDEXU30CW9A1NDL0HzMonKsNEwg81UCyf9sOx3LtgVDcyqH27iU9N2RJvt56mgyWb6PMVSyr1X/bCCqD8wxLYOXPqJA+KexIbo5nvE9mbiuleDyMGlBdns/xqhuH9cM71E2y2QMBWP4IEDhSk4dpWikUBbK86+7+0Jn3gzERMWXwTALHZDosUYWszUkF/UY3R29QHCrSvFxNt5H/UNM/g/MHEGZZxPgmHPkLUpPc2KXgDxGAgv9jDkHgWCSsKZc/JmiKrgIJpebBFXKfFR6VtwhXwT0IC1n61i/qHgmGW3bCg2V8fBHYhRIq6qsS8oaRwp7Q0aV6fH+MUBVwRnPH9QmdQdjtOAgjKDgcy45VAeWU5D5/pOFuBi/w3DPrf6GE27VHupcHiZgDRcov1XMQshS9HxA7Q+CIOQwf5h/6Uzlb2VK7IPc9yi8RN8UEDMYldmoivJRAtdYhpkXZnzvW/1FsFF11Aqg0UrEqsAt1nHRELOPuooo+YlNLB2JX6YBKxfZCoiHQwzrGu3B7lYqQg60Ph/wAU4AS1AHbNOha/SeIFAs/QygAQQIyqUSyC97BJtOL0e/l4Uii/jXGvzB6emAMiufH/AGijoK/8wCA68TAs8sMSpRT2XhcsVpmPSCDiLFciX9T2dnySkJU8aAoJYcGU0jF5mAcmIIZG+zDCZKvEdIQx2CzKs151a/wQkkdILNFHlloRV7pHJh6LEsyga3LLlXzgJnx9ARevZbi4W/u4gA2bRgdg902wDed8kQvDAW66T/DAGJaf0T5THUirNcv+0hDiGuFz1QrK32oeULFjD/4THEMfPuCBRvcfAg0aPuWBjmA3K68fFSxpUC14epegERBLropVsQYqG9xDhPmdfuPpLHkg8MpBgHc7c2NxT1ntdIU129B/ctor3lCDuWeQtYULYK0sLaj7rRL2GYVYtQNZGZYVEmYRpKyLFlsgZiAz9LLAB9bgAlidVEgfekEBH0EuW5W1SNGZrLV1GUhNiQdY3/3ccsQsTsf8Gbi+UaLa3/P5QsueuYhiVHh4OBK2YXlhXVZX4wIow/8AiCQSxme1uzt4j4m1mnJDK7BdJEZWXbOYCvFiAFr6ZfqNrt7FT+ILKD47lhkp5jnk8aQNDvu2B5ZfiPkmLWMBntgmcJ1EoBU7/wBErV0Lpv3GxgzDs7bX1RGAHkaD4Iy1YlsfqXkpTVv+iIsi+kbhPkWf5gDWvjdQulVkCf8AUd3R4WXWBbntJgC7ZwzR9HGo0QLZXYQMvPnUI/oQbNN0A2+iKrnwFKPciWgMKV+iLdrKcrFNIptP+0oDeSQmNt/2f4J7zb1otxgIxeYo82D9EFEcOIpV3NMMljqAf5of4EzoFRlYv4hzXIgYKRju5PzJgnEUDAZAN47ItJ/mkWOjStELKvglCaNdl+IwCfafcvtDum/t7jEI3QmgrzCdCPmwsXviiAAF/kX6uY7UjXlnuI1X61+5WBvY7PmKs2HRnDDsZ9uX9sWUBVIGWK57rOCb1AWeKNBb/JMiGEgsUFLMAFW12x3KTWcQEzh+CdU3tdQYSeRjF3hDwOit0y2JU2tJ9kBogzlr0OoQC3xB7WE3cZw+b0gSpmLZbPmrIXQGwgmffRDgisHB/wC4oCrRMWJoO1i9sWLO5gLflK4L4IYYwAyxuKmwRaNbHi35gENSpX4CoIEHq77xpWdBjqnfglUEFPGWbfo3t+iMPcgX7JBSEWsEFkFNAVPmLp8wuI+iKFR4MEnBAAMCIRW7CJCD222xpC3sj0Tu/wDnzGd5Cnh+p2pfUbb2Ro/ohG7cVgshi0nmtGglurMF9xuIqkW9VBTw7lGUX5IlhNC+PRK1JVamxjYyqG1vtZfkRE+CmL9EGY6BDeVPlY6PkiiO5P3UFHEAmVgngYuVdsT/ANCLpnZYfEdswFPGGPEqw2+4l6+9mH2Dsh/H/t0+j2y29Ape/URigp7WLGMNxxO237i8FMJALcVCQZVttR8eqDYefxggQIECHJUpgiLCB5WoWXS6ZR+olfPd/pmJhZuVU8P1iXFUxv1Ap1a37qZCEuPMcIfF2PqUTXwGYwyLKB7l2HzXRC1q+KSjsfOD+I3XgLsuBKtXSrt9ksER7LhhComtP6nce9+UcyekTf7gEgXtBagcKOMp/qAo3vVRhqg23KJJqMw2grVRmWwB+/0jgNsFRF4ju3MDW3JZCzy/o/mK5qvlVlhc8MQFmL50QYiliyejKNlmfA0H0cAhTuI215b+kxqXVR/MqjzylxpZ9H+iHBoWJkT/ANZAWrvc8sH9EL+2ZY8F57ovDGHGNgniIuCsn8o4L4I7dH4iXWKZ4Dywoce07FLrWsIcHBN+ADCWh8Ov2hAdXWwda+iNt+lUxUsDdgtPgKXgCZdb7MPNfmfuigh7gCnZpVPUHxKiCxn4lu8za9TAUxQnqKWVdD4JkCfh1cHStyPETEUf0+IJWLbXcSZVXUsTemZainLQQyQ/CGo3X8bIxbt6QGlegyimPMwYzC29KjkBfO5tDxs0rAqBfvMQtGf3TMYO4uLw8uJUUrlWCMrclFdwWPh1EVKHwYWiFe2FEcKisSdsAgksgPiSXDa/ttl8LEsARXmWC5vvqLSMjqbXzbp5lyyBkf1j/wCpiJg/7n0RfirX9PqAwdaB7xEvdKK+Vyy+FJcw5uWEdAik9MM9qNqWh6Eeoqqpiv8A/gJjEKlP13WHJG9WOLlwMheLB+AhZAeYUWRqBhgUe49VtQi9s/jNsPLKOC89imDEDy2zQEWDaNIdsO0j/TzErAoLESCtiCK+lZ8wHPAhDvFoX7uU4hV/MvgBW7u2CWjBciN6xUx4C7zHs3x4iCwMMquAMbpQDCW/IbATAEqxEp/MEyl5wY+SYew2FCoBTu+/0Rk3eGlH2scd+hINQwb35b6JaN5lYARqLHiuDoQ3Ss75S2FpRjgieM7w05DAXrKAcMGLwCyWPdiYM3wlInYkDm6tj4f+ko7Fjt1COVRh11MAENn5WVimHl/WRdPL4ByYZjUIsuIwbUt6ro0PBHCFdvuu5sSxgt6ljz9Z7fcI5K/nTgmB0K7+oS2kno6g4DkiXOpSGME7WK3RDXUoQWrQTFIA+R6gPESLAqWsEUGL8K8vFVSrGArg562C14y5CIpEDhvlrbUVqR3jVBBpvNSmbfRE0FHlNTIr2JWLZeKSh1dS6vNpi4FmGtBcVp2KlmRfZbKNj7VuIo7ecy4AAeJTxbFddsJqU6Oj4I68N3wtLKwdDoIKnUTF64CHC/h0/A2wXDYmSrF/AaIVwcFsVgHcwIGtSq7qN1oYmD6ZSkCsrOKcolibJUBB7+T/ANA+wFV0BFihAPPtxlbM+2EQBlSnDY/qI8uGUJWw9E0DDXtYjf8AWDwcLAUY9j4ytIQNAHUsVGTbfIdnhdHfElvIXoCGBIyeT2lDRA7mQcQLRZlrwkCiHMLmeZvjJdcHql4m7ZzMwhl2TauuFEVWoQDa6Gv3AotlG+pRsSj2Ry5dKf0wHyWfMMUC26ljMkrfuXgWxgPUdtmD4P5mO1AVZX8yoCn4v+2FYotT1BWg+TRMC056hIIPLgnQKy9ejxFKFUCdjHf4CPnAYDTA/BUCBAhZFo8faYoMVFG1+xFUvW91mC/uBuWoNQy1XFtYCHeH7g/RxeZkeleJG4RsXyiANPN2P/n1TQi66SeTlIV3+FMEexlrESzH+I1H1y4XLxKYxX3ryxon6oeA4eRsdOxYSZ3dm2ptC/Xi8TBV0Wg0cG71B+zeSYVNamvnxGr5B7CVJYW6A56Toh5oxIbYaFlCG1pr+xmpA1AJ9fmEIVFVbV/BGYrbK2nZfZBQD7Cz7JbVBx1CGwBIqyBeO5Rsq95gh2/tjwXLwLcq0UDxGtv73BWF9xJPmv8A1DaiV4URVPoE623llPUF+j3AxRmCwadrwRwlHAaEMcLF4CVCKePJpn4MtlJwTPuzAsIlRMSrbXCSsGpqYuoYhtZ9tNyWd3n/AMy4gziph1W1YWIEvq/aWxDVsY1zav7eV4Jo/LLKqA+A4R6MDasr8SsnXgcBpQZlRbeDRf6JdyqMUECXMiDwMoNyinngUMUQAXUXKMwYgzPl/wD7oN3FTKyOgIhnD4BjtqFWeuB5ShtmDwdmfkJjDumoKL3RkYHEv2NQ7AiGlUXy3/UoRg8EqKQ6S3MexX1BwBE1UHINAxHmdDyxfIe1lJ8W+V8EFrQLUiNcLGVAgHfDBc8zfbQolBnLJ6FQG7hiWI3v+iCsHBs8EbK25ZVebiWTYVuVQ+GH9cXmhGIsPwUP/Icp1WgI11L/ABJ7jcanur+2IUDggEMv6I128wjFAhlBDzxWgOxbJv1yuZdBRzEXbf7YMwZkpSwxZimIlWYlT6SbEVuOpeMIT5lWAh+oFBKjZfBCsebdhXUKolqYZ2jUTSoDt8sT/wBhADsVb2qVQ2pKMACAAEGaLZbHJv0eI/eDcbF2B/3Au2oyXqnh2QHC/gQJXDnEGmwP2qC1QQ+BRMRHuMfuNZqEpA7WEFHB7io/lgB3BQcPmEF1BbjuUKksfMmV+15f+Rd+zh30nUvYq5eT9Z4FYlqJD6AP0xIvFfOy68Bee4nV8UB6CAZM2Nj/AOXgiMnFdrwZdEqQjEEgQ0np4y2HiUsmaw5RLOPHfoLRMjzN6IxGWh4OiLHFHiQ0IlbgEQQFyEXegQgkJ9f0ARZ50/BJo0M9EDma4H/NmkWqOYLDATMrApvsm5iMeQ/E5ghTDX6yrBwZWxT+ARSLM9ZrUBRCEzDa+YaS5cYSBVvmVkVUf/DLWUb8zn/xj9H2RxnqyNq8BMPkf0y9EAaz0z00f04xiR0CYZa8i/EeD2wARwERGUWz/o9sPF0dPjlwRBYKhJK9TMuCnxPGcPB0c9LCaKmGoLtiE1V/SIvCS2YVAjWoZ3uBUTbv3rBWAA+ppiE+aoiVZa5X28BlxXkwwUIXs95iJsArKe+MfEoVYAtYoa1peMRxaLGVwHriiOuXjxvy5WTCLQV+o2wfypKHmbTbwuNqlZzCKeiXmKY4tEoih8BDlHIpC9q4mIhvpf8A4aWN+10DtZSrV6RFF4fd/wCjKJdEO7MH/wC7LjKzKhNDMo5an2vQ7UtrVt32LFoQgubQWq9BFsZg/ptw1BbCMUofDJKKhAzBfM2Zqw3EfLP8pgHLKBjwCbIGQ8aBFbcXBiCoRaYx0zeFo5K3fwiDgMIDeAhYJT4f9oq66WStShTtmsUe9n4TUlw6X6XaVBH8A4p4Vyo2BSM/pGuJPu//ACjr9E+LFsIBjEXEVH3swjYYtRbjxKY0EgoQZcCiW1b4eP8AwP1MvQEW5MnmlhFbjV1w1RuakEBquiUN3+1DAd8JYTtRPYwC1XAEUpJ1/wAIvHwy2iwzuronvhLgcazP5Yy6XplMfZNngzOTcMZgxczG8f3sEaJVNovrI8CcLCLNo8D5SriuBCypuvkYgFIjuwPmNwV8xxqHyiOmo2qx1YCsVvix6Ik4QK3Og12UbRXASoQEr8BuAdy6Ni/mBgp7H9YjbMarxgG0s20QVmNgI4pFFlrU3IhUdcRyQl+qH+H/AMD1BTZoZqBoiwwTvglzVy4vB2XFdagBvM6DO4/nG2EA7f6io68vdIfOqC4VNINd184ypSo2q7XiovNKn93CYl5XiCI8TSjqHeWUV98zipgtrM+chOAMuKxhhfEz3DEKbC+N7YEeh9ARSMo9ngiY7VT2wVG9uOK/SWhRLwd5+EeJoCvlSSkqWr2sW4nmVAgcBN8HEYDNwBD7hgMA/Soif/jmXDsOkRfM4mgIdS84gGz24L8SgogTJQKIe+fczaiMh+T3kw+LOZgzuLi4VB0jL91K/ZDC9Q02iv1KEu4jOBa6/wCN8EaRroOAJ0Aq7L6EunWPQ6D0Q464ON0xD8wiYisYCBsYjEGblxfOh8LmarAUHgJqb+56IiVgntzFxE3KjXBYr54GCLFXcNvjZDyYLzNPEkuhm/6w/wDw8wdnUC2cEVXtx8SwZmXHHritnvghy/gTG92/0rl1hPnf6MoWHaWH1FEfOzaYiAPmOCotxmTKQu3lZrPETZEn7XNfZfgX+J5lU9AtiVuVDx1JQwYpVsXi5TiC/tP2JRCh9hSyUlI0RqUS17dsr+WIQvIaAC2Xhpd6fa9v4Go55GcFmEXEmWRKfCKEa2Wr7YEuknfzL+yDOo3yLjKlROCAFq0ERwp/KyQWVQLWA+U1vHGFyivtzed0qI3v8EcE9N78vARNSyPawCJUYfkY8GeCv4GoXBAytfsxmPJI4WKtXiIrCSpQWtruPhVgl6xqMDgo3GosIqX9qX4rrUU+HLAWTNWArH0S+R0qIRR/rxSOPpBBzKuq4ZWiGiQH3MXLHh6JvPJCDwyj4YH1TpODHVZQPTuGzhYA3U+JeDKE1vhtF7i4HcY81KifoI1NEVqGoyKvn/NjgDuDEEL25G3fgmquqngrXw4l/tweiKwai8ED8XgLgmJP9ul6mSJ4R/3bM0+41BAAEaILbMGo+FSMRAABz44LFj/ZLpcmT0fxIDiRAPlGCxbcH4Ui7MAQNFH6xUt21T8GHPB2ONKavuDHPx+sytE2u2HF8eL4SJFTggqvJBm4rPTiG3kyQo8CeVR8shJ89fQuZfUP2lIQ6xNRiXLLKOAhlXKty/B0THSZuqr4eKHiCPtVkyLlSNmowxQMf1E5zn7YnAc/fDL4YIeDBMaaj9OOgUo7S/Rw6h8z45iONy2lo3ABGuacQudxyebzLM8sEiXOF/bv8a4ut+43CViXINSo41LYEtTSz8ZQfN0Qntf9MsIenNCMAwb+4cUMft0CWYn10Og9EOB+Bws1fPAoeGCn1wf1l2PZH+cgBz+qWChCgP1FEUIHpyx9JYY1G6jnEDGW5iPIoCru+MzAQgAARjcv59CL6qH2r5HvYH7gV+lDaRbX9ELqb4v4ZXyQ9zv8qxDPECOPbY6l4EZp3/C1Mh8QYt3XcMscBvMXEvLHBdwlQgxuPidzFlWOLvxKz8HU27gWvaRjNwIR+7ofKIrCH/8AYAxUSzAYhTQAgLdBEPn3IXyPxKj7l/BuOiJcuFsigtRyx+cSxT+U6JhJhPXzapLdI5hZogeeLCSjgLUfKH8Eqam/P9M0lBKSVWYZ1sXiwBFgvDdHl+0EYlQVUBaxjG/6fI8kx+JxaBMGCAQxeV+wwalYlzf885YR4JcAcx9H3LKIwIF4A4o/Co4ncGUXs76zHR3Rj7L/AASLCu3UWOpXNAZfBkr+7ZcL3LT7ymobZRSArtAExzH0uuAVC/zJpHS9VAjiwMNgxWPGMHwy+t/CTFyFwKhYfFjMogPOItTeGOYioIcBXYj9yoE4eiVWLI9BNU6B8YIqBwK/Fh1U2M/n6xLV07kMqCGTUXyYxzK/MJXuWlTRwQQPF/zEICrR+mLjPmJl2/mFSzBwjbU20MqTcI8MHMuO+KIP8CJsUL8h/ANQ+7E6GibfhWZc92/rJLjkLXioXRKklZe8aXj9sW+8ptWCEPxONFxYiQvKmWrEAZpFSob1FSPcBcBkD7VnEKaHH4JZRkL9wwXUsT3C3uUzxKKnlEqODBGxrf8AidG4NXOfHChE+4bgnzIsWA+kVD8zewgDAqe3aEO404e3BG1mKjDmuQBU+sSp1MQlwIRhVL9QCoHnd/OE/mdBBQQKmSNiUo2cs+o74a4xUJePiQAFQeeRT0i+AuNmCv7XFzXFhmLAW7D9mB6hJxyPBgoX9zR1p2jKg4O/weOpoZafXF2owAo7JmDJi2BwOJp/4XMCA6GiHHOD7bZbqAorMTcrfcoxiYWokqMzUqgoY2O73jnTVlAwcRUvAgQpSzb5Y6JZfjhhjL5p9Mk4nj8AuOIF7lcBKjwS6j/fMoHgVFYfnYDQO2VB5YYOISk9y2dPDw6lwa/AJeTPRBgcpVTU8t4J0PiU8/gsZcdGhfMSq0WCKIVDz6LKSpRKlSvxCMrp5agwQwSkNagLLIMR9uoYDHrrPtHCXAbJRZbC+cEDLng6h21i5cYYmUUwPm0+LzA3QKJRE0BbHsrP48IFERuYcQNuB+ov6PbBXVELfe/cgQ4cl+lx9idfKuURiqA8swmoN6Zipx40HlYzTRlj/CxRr/ejtQzJiHw27Ydr1F6SClvBxHzCVMypQykE03NdYgErnb/cYvTZggTCEFsqyyh4xL4fM3UdzLiYqMVwYD4luUER0wcIV3znIJMv3xcWXKZoXmXV1ChRyVA/B3DkmkY8TeZRiXTdRpmJ+0dwrpt74yykkCtsq7BH6SllW7iGHsj/ALl2sfMccC2X/Yd+8IYwjQX60m33L4IsEW0MNWeINEt0Z+nICEjBIfLCZs3vh71noHlh4z769fMeyqU7aGr+2GotljrQ8BB5i3rGLw4HoDH+ggV1O2VzU7xF8K36lcRWIVoATs0Tx1xpwsHiBxmG+LYvuXcTuUyuGyFTdevxt76BN9sNcZU13zTCsd8LxFH4H/i1ZoeIoQSIgUHZHZMhIoL6YDKyl9s9MyV8T/8AXiYACZIsMSY5qaZahmg+jM0QRq2Vr+GQU1wYYzd+UtgT/wDBeYmZXZLIAy6IKOqi7kkhxW1YnPVNveHjKcOdPR6eHsxaVLUnoJSzMu2tBS8E5bT5Yt6zV+HfgjZk0FbUdxVizEp5VlEI/p3/AFFYniP2lNb/AKp8aZqg+OGocVM1UeOuMQLeK4JgfD8VxUtoLTb9mYV2YZrFKe5XgvoRlttggVKmvxHKY/HwlPK0IUEdR3BeJa64qik1gyfltHBpa/qUINbuDT5CWs6I1B8kVnTbEzCN39xnMJ4YP9q47j4fFwDcStv+fahCGuiHUohlvB3wz9EVxyKSZeYGsKfY/gYSvX6nnB9TA7kh6D/sBKAfltYxMyBL1Zl9u2XQ6zfR8SHVsZPlEfiiJ30SikJzp8V68RpQxL/L4tlUdyiQ3Kn3NStxPc7lbjiBDfFkeT9/gwEBRSOkZTMMP+1FlRo1Ut7qdBtgGXLDCBO8cU/gTqdflWl6IBu7VZXHmOyNg9TcLT5M+2oRRQL4oqCxv9mzYal0agy6li5mnUWS56jcbeqD7hCFH6QqODieHKPwIWxjO53DSNQ718G5gEpDY9f95mMys6lcy0IcBSX6CoE0FrFiWMmvDC1EjYPiAaJlWD4JbqCt3oy9+XBEbQAqjpCgSrAqiImvCWw020GqFL8q+Zm6ttEe5CFXAe/KIjukhYSxvH8qRrK/FNOLZtQTCKRJbcvUvlfXL0cvHW+Xb+Dw6l7uY9Lsy17gmY8yl+oiWb4x+FcWjNhwwir2lEQHqKtxY4i5mYkBeG+5ahbO4ZIr+EMvMyBcKxEmGdMKbbmJr2jlnrGwcSCqcArGZ3+5GXuY4JWCf/PVBC7LiJuz+DqV54NcMBsYWnUCUNFGVQf5GomBrRazPUPKYYIuXcqblhARTwz+YEFI0DibYUP3cbPXFYuCieoEKjHzUvqFws4oolvwX0Mr8jPP39mGapVVZa+JqIqYFsh5CRErLJZBOMVywxyTLyowZqXFK45Li192fpYSIxnKzBa2moCwsMQ8ruG2uLV+IllsAvU1PCfphkQX9fq1DRkZggzDUJ8M4Swx+xXf2iUVwQWloYlX3KlIhXp3OHDtfJN2ffFxYwagdITu0QxbzN8aI+qKiow6iSuFxGGmUXK9Q4eRDqXjl/jSiS/L0R171uugRBRHmWRlMe0RPUusIlDTc7BBYF7hFIMvh40x/TbEModxllhgbg0VwrRqEn7T9pALQo1LLlP5zOiZjWeLzBzB65f7Qg1PPA/pQtQjDI8SohS0H6h4qXSf1F82P2xYsHg1GG5XqO0C4Z8X1SEyjvBPn27YtxrgsW2GTuahVAwL/wBnTcUpxB+AotE3B4IuI8kIF38M+f45omtGogYR5iWxKYkqO+KiISxQ1MNki+8gjcKATcBW5rLIvEy+KFHPE1hm4uwcbS7y7+TNC9kHd/7lKS44cQsjjgqKqJqEWmXVX8jBIk7mS4uLDDYvPqIhkkAIKva/UDDlxeINS5U32Z1PL0vbmiF7lLsG6FINvKHaasW8xi64dRpmxrX+BEu2I0CyvxHoqBcQA9zJCXGb0cBA/C8E+4R0wSH4AaZR/v6RlotVMqsbTbh1OuKtlRjBB4bxHUJcR3Vw3CdjcENCa6ZiLqJrKEWylDxS+BdxCFlmoCxAvFyg98Pcr0xjXh4gzdQukD+aaQ5MmQJw6l5HRCzGc/8AMQbi0KNAf3Y33KjpA47hN6U+O4wXIA0smOPpZwRVABFKO4OG4HU9/wA3UVi4eKsGozCzU9uhUxXPn4TaAuXm/MYxZcpYEBOCMWLwGGHC/wBkGHxyHdZGgMrAhf14xWLPfXAickjwMStw4dYOGNog1E3EO4zHhSVjR4GwqIsFsnzAvLDCBKMEf0U/oQDUG5dhBCLH1NsdanVb9ZUIIwR9v/aMcalsrT1AV9kUCuM37cLfUwSB/XHepUrEK8cBKKxr4SJ3cC2pCqPFzNLrPmlYfn4ODG/LaovA9wYDqVB8Zf5lFrEWVxgezcCNEsObuuHDilgcKxYsGDM3CfzCZ8c4tgHOusZzGML1zXLrlIIcJEjCclcEqJEgY5x7/wDqMIGMYN1WC3Lo95m3UtD1HUasZlVEJz3/ALKIWXgj1uOZmIeUav7gzBzSf2hMwHtM0s5Bcz3qCoAxSqrtN0EulTAPXi5Ek1qqvtjFxFe2XBnlwJl6v/ZcG2oVY95/vGVysLRZeY/EDqGpTAzH8TDBjl8occdzCcNNTGvPQlvxf+Al+OHghM8JE/A54HghEY9I8A4MM9cXUWkNNR6UxZIHmv7IC5tfiOoXCklW33KplFhMKh1uv6LjRK8kV10j8cRBt+BF+iDD4n2n/FjRFzsFfIivF6mIJBkaAMsWlRYX6YdWO2/gZVKglU0Ch8riIkWxZ9CL9zktlnR7S/iGvLTGCiDawggUGGm0csEPKdcqW2E/JBV1W/4jk8LwEpLJcHi/fCxajyUsWEN/NBfg4fN3g7hjHhOBS9y4/MdQOGAYwhwmIw8NkuMZaaZiRmxH8ZskMOcQbC7+38HCltQf3HRUzN7QD7mHD+gIhF0C/qf/AKuaefkzFXzoaUGDyhBq9L9cAVuczMcyqiImY5sVu5SRR52ReNSsuhDz0gftLGfYMZ+J6ZP5uo2V19tLVZYA7jIWVYHgylZTlooGz6EGJeAZVjU8wZYyXJgj/JL9szgABE8kT9tRQob7Y8EZjzL9y4PG/nMwiGMVcggLkhNf3FEqQ6lfHzFoiWUVdrlj6iR1wzB+KFzUZgqNQQ4GMuVK/EHDHcJinu77TDnSs3FBdp+4EXMCZ0sN3/EatxG7gmOLD/WUudVAI0k/I5trtYnFDfEw+OYUZj+/5yDQOiW3B/8AymozPFBLU7PMVNVnQO1l4YwZ5ILJYC9RfGUPy3HdQiJiIQ6jfnBLY5YMz2Q5OWfrhioi/q9yu5Fq7VgiGfoH6TQsysj9AmSZZg2zxMscQcDKgVyy06jCHGhmEsgraBgPRGTIqfcNxxw8XLIevy1mJcCkYohxUDKvlCEeRDGYjO4T+aDGvSZv+WiXBTBWo8MUUxAL3KYuPf8AEkdodz0/lELMZU/gESfNqADO3YrQblqyvzn/AFDBuLR/WDtXoJqJcu3v0ERWyvbC29jqMw5U1X2i/cbob8GnXOJogTUQZj9Tq+4VcrqaCClQYsx/hc6fRcapXR8HmOSqWrMExN5hl6cLfiDMVL4oRZSgeYkW4L43BwbvE/kxFyhV7WNAjDqMDEo/8DxMXuYcDmfg3lJrhh4YkEyPkhL8/wBJBEu7LfhRLcTDDDU0rgcz2ePHb/tR7TzT9faN5aBkho+I8+WBQQOvs/UMkMN8YcW5Q/XF4LZjAF8Ul6gg+ggwqzPQI5vBkvdwQkZGA2qx1tKDSJjCMBWH18S0BISHiEEaIG9Ah1FC9eI4OH+xoRK2zPESlGLZvaLFctmjRGrc79eYZbb3MpfFyk9ZlPNgJVRcxep4IEJpDiMoSK01ti5i2RmZV1ycY7fx0hvgjSJM4hH8HSXs/GwZVmf5wEoRoKi2Cf2o4JpNCXiEDcuXiojcEQeJm2Ss/wDjgJtNIJGRFShdu8EMbofrmgWQ2z1k39uIkze4MfX3QpGik7W1gqU2JST0Z1fEFvFG0Ez3/LFaXWTjE3UGuI1LISLoRGW/FxQIxvndiW8wwcOtiIgMBK5WZ9wmGUkOBxEJ8nELoncWM3GLxrceolPLiM0qG4fh8cYrjSaQ8kOHWOUj7jN+m5ekQ0Sk/sqjRlzaO6miKXNqgwIOLv0EZxOpN33DPgLxRy6ugEFvqC+jf3iElEMS31/92xMPBXiPgiomD8APzwo6g1KZKhiICxxxl5lraYEMwfuUslguoHxCV+BFEcx1wcEAhFJUzsD9sAojwpGpmubTUzH8E98SGuCOZ9QlvnkbIcMP4ViGZeS1h3kh1UP/ALuWgYiQObYmeCpeCXqVMuf/AMojB8wRGh+uN5cyXgeRtQ2BFf8AlMhcZ1NENHj9IyspqiEsj5zEio6pW7Yvw0ubQGDTGWhjLiTSNsQQiawcspQgdC2FCY4xKr8SnjiuAhggYlwKqMf/AGSBgizZH3HjXB8Tadwzz1zXwR7jxfHlxeYMEDhiZWNTeaQfLiEqpmD2zr9ZYtJ7T4cXmZQcWtkQuxH3mMpjU7p/jwIFsIOGwvbYatgKu56CaGKnj+AqI8Sx1EEGZ7yqfy0IhXqjf7UHFp7/ANN4JlEsb/8A5sDsnibC/wD0IWXZf2zZKsE1slhxLOorAiOYd24Hg8JcHgnuMf8A4fia16iH0lmOVj88HBGk3+Dx2mh+DLjwE7Q0kvEsqX44CUqWSZp/AioikuEAMvmSYqW2uKai54KGeDfP6uo1WP0WEVPaV++Me5gRUZiPlAxCHf8A58K4Z7M/v4OczwMnVyP7JUFfvtF7uDc70dWhfJE6/CP+ZaWBD5v/AKMpU5LEaFoRbGv/AEP6skW01ReCLmDbFYjCxIkSWhFYTSVx9yrBHgCuAnUYLeFCJpeovQA5vEtqBPUqprEWowMfg749zXl1ByW+GIROCwhuEKCOelh/MxCxHg3CAuI/WoaiUzcooaGIXB3FmCISW0nzSGrSAxun95kyyjgM1Y7BDhuLYEmtNzMEG6t55cX8kG4kJgGRiMVrmaPh85aYXQ7n/ddMuAnXgfFTCWGlr9DLBobV/wBrAoBdva/8UYAFh6/rM7pwBe0sAUQCK4iMfiWSyXFgcGYss4vMIcnUwJcV1NA8s7NylRrxx1LrcLmaKlVUbjuCcMHjpO45nljGK3EMxBB+CTYl+6VF3VEAPAUQqsI9AJlsUflXAZlLIROBSxx0qEaryT4LLOTPpUPRqbcbniKkZqzBlXuv+3LtIC1UPzyv7lq5mwtxVeRijD8Nm1LfASh0wPCRpOkLfUJWQABsgAumEGCdqlYMPmOh57RDJJRq0mSk59GwhJ2YPbGca3ewQwlqNY7y6iYy7jVyxLUG5VAxzKJSUlJUWo8v64p3wY4CNVDca7oQ77P4LiXwOeNpeaZ4gksh55u44cHmOSPxH5jNuQ7gw4I2yFvpM50Ee0b7tRFCqSYSDTKxEt4UCqjsW/Nr7cWvUTQIX7VwDFLBeAs13DWMe3+6l9czPU6//wAMBloJcbCW9PFafAQWhujtkpfzF4RYZ4YDV1QGURealcyuFPV3Y1UB8oBdlysVSlzBMg1mE69BAI6ueMdJUXkgNIrNMtj7y5bwHXDNyvUOe5girTFVspeATXCzOuKlarh5n1wQzAlxYizFBedxHkQoggmmuSlXTIEqR0H7jAuHMAwbHg4tO7jEIzS2xtq+uMVokpFsL4YdkSM1NkVk0JXyY0oLcqPd7/3KCIauKFr0ywMqqs+xFpJj9qku5a8DUNSmPfQolkqNkW4IzkBQXQdsFjKsA9Qx2x4KShtjeiHVRELXvL2wcFtsY7IgsSEX+oLVaXF4iLiRL/Bu5cuahA/Lc6EVE8iChxf5/KY6l1K3nnU0mLHiduCdxjnqMfCcCrfgVLgYLQmdAniX7dyhRJS4eCaKn1Eu4weYXK1cDKT/AGtEbuh98UWKna/kW4aEtGVxCCl9sVu1Nq1tRnyf6Iqr2rFKxtmVZztX+yGuuhXM8KUZZ2TJxBUxhAopc93VCjRmt3bO0MstR+qp5DywgcccHS/9EpBadKoZUnvNyuV+ItiDPQJTOsyuXj53xXAGOKgF4msWAmYtx+4rFQONz5gZfwPCyea1DXGIw3BH74utcHN4DCdJZCqKdqzfC5iIsALaNBAgxY/BGUyd8XiAzmX3BohZlis0NRwQ7zLCHyUqi4x+ilT/AJZ8UGYwHISoCV1AJQjJsh8h/wByGKZYS51DuJpobH5jQt7Ebj3WWDGisdB9LFcNaN6lUskqWdqtPkyWb1V/TrKvkEWoiksoXH8AzGfMThOBxBdkVRHU6EzLFgwcAwPLwRmdCGE3KMQ2RiBoBB4HC1Mxm3EsvEvOJ3Pcshw55lw+OWbPGnBHRNJmjxNal1NZSgdx/fyQ7MUvEqHcxcKzxgI3q8yhzAdkL9OoAqniL2dyWiHCgnFmKK4Ynev64JGVwqNj/ciKwRfAuBAhk18wPjzW9LdETUKjTsfM+EG8yyCcY3DhxMMRjlMkO3ASkSxPiB6nzm24BAOA2Y2ymMzE9mKH4jO4meE8T6ldXwR/HZyzxFhHMHAhwYm5aLDiSp0drcWGoQU3a9uYlyjadEuYjl4naN23liERdL+iALeqUKXf7S4JjhD7qKI0ZYtbl+NShwpYLmFDxAu3X8hPTGmlSlZXJGkhVrfJupVxgSrriy42OGY1UeQgeH8LqXfC3DUWJH3sgLYcLNN8Vtmo8N8f3HiyLN+O8cGb/DrwOGmVL0QE3vp0IfSTbHmrU9rRHHoo9qxq1yQscWIwLGAN5ngbZVNMA6CHcNaeOshRLpTBADyTqEdjbiNE3CvUCUblnpMWKW2EyQW6icHuYHEphxFcfZ4y8s8dkIRncXDBkIwmJUSDLIPFwZapcXceXh8MCCoJRGMFue64uZlURYQ5vcUyhhjlQ58prBhL4qICjOj751T1CWNH3r0Rbtgt7iuVCB+A0ff1m2G2ygv4h8y1GzSsQW9V1EPEsOKhWIg6ghFWoswIn6UiGEwc2AmO0ojCildRVhnWy+yH22xaB1G7gMxDnUeCHASq3ElfgnFynhgy+Mk9wIJNxIGJ1azQQSp6JTgwQgSO98MY+oQ/DpBJcHnFLNZrDf4BAn2nwdsRmHD0KjKibrboi4W1PbBJTh3CHxwJgh4Ic1Lem7g6bhHgwQrPefUlTFb+CIwRt1FgLQxS0pOwRhfaKH8QZ1my396gYbplXD1Uz0SplgG1h122Cxh31tEwQGkdkpOdTfCSu2blTN8Wx4HW+ccYrgmubhHLOzMJcF4APQ1+uIlzuXUdxjlBxf6jEhBlY4Or4MK4OeeuBxO4MXGBFGv5LZj10HlhlhCfM6JSe/ESrcIquDsmrATE1MQPYdQf615j3KJFVVXteFSvmWE3Rx1JbcEDBiXEEXLTOOvKkAuAW/8ArgdIZ2MQMQLQfB6MTrVJseMgiuKcXAzAuVyuZd3x64olcVFoikXgljGL7hORBzGniCy79ruDhfiJAzNuDuGCuO47jzcxx1m8cIQYsWOoqYMIMVEQAO1jBFfn5WGkC/gS8I5TO4TglIEcYZS8zKKxDWzlrz/UG+Ou/phbbX0dQiqUJBU0EygfbHCE0RqI6ixhEFPEIQoHxAJqKriHFoYP6+GPHWE2Jw+Zi8xbqeVBG1DySkvMWXlwLjX4D5l8MEvMah8RwoJUuXfBAqe60ENsPBQXwazCLEuZquCMJc1wvPvHEwgswdxjwacNTH9fq9SF1iZFivj6hJSYKgVhjDyYwNZWGYh2mcvHggkStFa10drKvGC3RDFMeIHk+2pxVyypbfF8nfDbmpSMaaqxIYsf0Iq40hmWIgF4FkkoUdjTGJLIrMMVKNMuN0o1G86UwhZcuPC+LHivjA4JUAlcrAvapKF8wxOyehLnwjxvJDEXPJDU85zFjGVmEKLMG4MsikpHyCbFWgO1h/RepI3qey6CW7EpmMZtwQSoHUrGy0sEqk3wZQDMd5gCYwQG5oSpVcYlkKRjulNjFH4+My8QeHLGGHMfAtg0jL9gBXw8I2zK0j07Rme0c3nF16wMeGEWMuXuKfJPO/cG6IB4343L8MY3Lh2lhNwdyoiQhwst3WoRIy/H1FatwRmnC2Xx6lcBiBEjy7TygwbgwYvHSPHF+q2uYTMwgX4AICKk/wBpR4AaOiYXcVRSegi9s9wJHCmAoKJUmuRcqXi0yJTLZDXCksjRLTgs9QHheCKasvn0yiKgd0MSSxSWqoqTVCOkjh1j4vKmEXjM1K74VG+pYgen4n/Zx21ULS7JSytErg2SoFQJUqHDiWJ24JamIhVLEX8RvgjguDvhf4uPx+8UNQa4kMLgszfvrr0QK3etAIEya6H/AKRKALKkd9sItTQFswI7DcnLXbMoZEHNSAQMpz0gTQIGKnLPU+JhLY1FJZBgJS41vhSDEwXXqkMO19ku9LgoXY3NynDw+SFNe3RJJjm6eGLYuCB3LEdAZdpqIOG4DqHtKEqVCNeQlVDE+IoZUvi1q/MNcViLiL1w7lr4uHK6jwuOikfLUJZjBy/0GvllCzuNh9EtO6GMPgJT0/VqH0QG5ZjdBEgfmoMAHvaAOoBwBAynPXGOLIpBlI/p8kEFdukRxwvAz4QZaS0GHzBCG2Jj+NA3QgImRGCrbj29bgQDvg+DEN3gmblTbFliosslwebcWpa5eOdkT2hXTB5LlrdEVXGtOYoQtTQfllyMqpSs3KsvcOHNSp5PH3CuSXNRR/AazePhVCSk6AtizN9M810H8m2LudIP5u2WSqq7Xg9ZGgNsus7g2/MPgnghHpBl1CBwkOIyzeWiy8SJj5ozeFip10jHuXxctrkJQhwMH7TSc6I+Sd3KQRiOvNbjSomRpJmLyQOFl74z+CPA5Sl3MIEslCTgIikIRgXFYJiHLrgdvGEHEGLjg1GMWLOk1mMMiFdBKpDyqn9Q3b/T9BmU7tVUY93sUr1KgQer34SFiHeUtRfbDf2EW4v8Cw876UL6n8U+Y1B+bIEfVGZ4E9MoMx4KT58lIseB4QceniEDSqSYeSLLly5cu9xbCN+iWJsSO2Nr9UIwIGkTQYXla9QVSLib+ZYiXKIOc+eGFy5c6ly+Py5mVxahCND5ZQjRMZ6OOyPGIKijOoppB4rHDUYvKlsHv+3Z59KMUgh1mwTQ+Nt+2NUirtcsYpcZAWlv/REyodiiWfCEQAvpP5ToWZcHyljMv5hxKipEo/rXMSo+twVHvxSYtv0hF/fQog80PPPdDzwl5cVA0KY+4H3QhThIXxcHgYpeBFnh9MXXUO+RsI12xwVxGZSAciMaMRfF7SuGVuWxnuHGRl8OYt8LLiJbFeBEAviMlbZYECpqYJSGf4sYM8h4DVSscMWMoR9f/RtlNVs9H6mlDyhD5YCI2yrHzuLwZE6gHdssNAlnvimYfhbB5XBQCZ7IdDMkp8MNoq+ZoZCMlijFPqVt0MYzgljRmWymn8TFaJ30IIloWx3zcHgYPuYS2+iQA2G0SxjCIFS8ogv08LteSZQ6vr6kjrhmeoc3n8SxeFi8iWQ/LKogKfZl4Iloi/AUjKlPMIS/UTi/HFS0x46B8qAm2qb+In/xaABKpPj7+TixWCd4miL+YjtlkeQhwnBnM+OHi4DjMHWY15lpLcLEsYrjlqqYz9yEWZPJBB9LFkFJYnF2cBLhLghBgVL+0jNMQ2QAFhnbQwAjwlg+J8RZ7CsIk8xYJ45r8GMWO0WLAWUQAzubYiqTEnUX1OuHE8A8N8zwGGWMLgRJWSX/AIkhcL7fa9sdXD34Pcuvbt69EYRgKSupmK24XiJyHCSp7SUzHUeKiPNwZcaSU+I8Lw3TyQ6GTxA/jEyV8PALj4eXi88hruKUsPr+9mNqTrZaWEWrARGqWvARBRKRpI31PaJE5cOLIosYWPKXUcZ4lj/PKgEEdytRxpmEEJeKcXwCVUDzGHBtbu2/Z9Q4AAUAUAeCXXG8gYKCco5V4CWOliPcVSBxUeCXFiYhM8pUolYicNcW8DrEHhE1GowTghDZRqKUfvEFNjpmpuL3HefxIBcGDEppIdDAbrnrUKVcStyhc5UuYp/YQxH8C4xVw8gyyyBUCGkFGO9sKQjgwGjKnlSJLzFYw9QgVUfEGcRRjra9/LGENDRE9GH5Hy+iOtvBKyxBH6wT3TDcWMWXFxmdxlbuHUsNQLlRTUZX4Z4ROCmDLjRFKdRlTCWxyXndpmlMRGZiZiYnmURqG4RQiDiAYRIWsB1/QIthlmPpEZcKT0kRLGOCif8AXzYcFirOnCywISVVAiohWDRCuWcu3ACu+mUFsJ9y48a3ngy54YmIpQG/qGGVEAwAYAhhWEdBH8q9dYxBFsysLlsWXw0SrwcpwcN8Yvig8LE4TE0wgeuEzTiEKIhxl0zfJMpn9pw6F/DFSYYmGK3Lg+fxBNgM/Q7Gb3k8jxxNx5JlElGv0+nzCLV564JWZazgQwUbYJ3DiFDlThK0ojKGZJctg8FCGEHj/9k=" alt="مريم أشرف عبدالسميع" class="about-img">
    </div>
    <div class="about-text">
      <h3>مطورة واجهات أمامية ومسوقة رقمية</h3>
      <p>أنا مريم أشرف عبدالسميع، خريجة (Class of 2027). أمتلك شغفاً مزدوجاً؛ الأول في كتابة الأكواد وبناء واجهات الويب (Front-End)، والثاني في فهم سلوك المستخدم والتسويق الرقمي (Digital Marketing). هذا المزيج الفريد يمكنني من بناء منتجات رقمية لا تبدو رائعة فحسب، بل تصل أيضاً إلى الجمهور المستهدف بفعالية.</p>
      
      <!-- قسم المهارات المحدث -->
      <div class="skills-container">
        <!-- مهارات البرمجة -->
        <div class="skill-category">
          <h4>💻 مهارات البرمجة (Programming)</h4>
          <div class="skills-list">
            <span class="skill-tag dev">HTML5</span>
            <span class="skill-tag dev">CSS3</span>
            <span class="skill-tag dev">JavaScript</span>
            <span class="skill-tag dev">React.js</span>
            <span class="skill-tag dev">Responsive Design</span>
            <span class="skill-tag dev">Git & GitHub</span>
          </div>
        </div>
        
        <!-- مهارات التسويق -->
        <div class="skill-category">
          <h4>📈 مهارات التسويق (Marketing Skills)</h4>
          <div class="skills-list">
            <span class="skill-tag marketing">SEO</span>
            <span class="skill-tag marketing">Social Media Marketing</span>
            <span class="skill-tag marketing">Content Creation</span>
            <span class="skill-tag marketing">Google Analytics</span>
            <span class="skill-tag marketing">Email Marketing</span>
            <span class="skill-tag marketing">Copywriting</span>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- الخدمات -->
<section id="services">
  <div class="section-title">
    <h2>ما <span>أقدمه</span></h2>
    <p>حلول برمجية وتسويقية متكاملة</p>
  </div>
  <div class="services-grid">
    <div class="service-card">
      <span class="service-icon">💻</span>
      <h3>تطوير المواقع</h3>
      <p>بناء مواقع سريعة ومتجاوبة بأحدث تقنيات الـ Front-End وأفضل ممارسات الويب.</p>
    </div>
    <div class="service-card">
      <span class="service-icon">📱</span>
      <h3>تصميم واجهات UI/UX</h3>
      <p>تحويل التصاميم إلى واجهات جذابة وسهلة الاستخدام تركز على تجربة المستخدم.</p>
    </div>
    <div class="service-card">
      <span class="service-icon">📈</span>
      <h3>التسويق الرقمي</h3>
      <p>وضع استراتيجيات تسويقية، تحسين محركات البحث (SEO)، وإدارة حسابات السوشيال ميديا.</p>
    </div>
  </div>
</section>

<!-- الأعمال -->
<section id="works">
  <div class="section-title">
    <h2>أعمالي <span>المميزة</span></h2>
    <p>مشاريع قمت بتطويرها</p>
  </div>
  <div class="works-grid">
    <div class="work-card">
      <div class="work-img">🛍️</div>
      <div class="work-overlay">
        <h3>متجر إلكتروني</h3>
        <p>واجهة متجر متكاملة بـ React مع حملة تسويقية</p>
      </div>
    </div>
    <div class="work-card">
      <div class="work-img">📊</div>
      <div class="work-overlay">
        <h3>لوحة تحكم</h3>
        <p>Dashboard تفاعلي لتحليل بيانات التسويق</p>
      </div>
    </div>
    <div class="work-card">
      <div class="work-img">🍔</div>
      <div class="work-overlay">
        <h3>موقع مطعم</h3>
        <p>تصميم عصري + استراتيجية SEO محلية</p>
      </div>
    </div>
    <div class="work-card">
      <div class="work-img">💼</div>
      <div class="work-overlay">
        <h3>موقع شركة</h3>
        <p>صفحة هبوط احترافية عالية التحويل</p>
      </div>
    </div>
  </div>
</section>

<!-- تواصل -->
<section id="contact">
  <div class="section-title">
    <h2>تواصل <span>معي</span></h2>
    <p>أنا هنا لخدمتك، لا تترددي في التواصل</p>
  </div>
  <div class="contact-grid">
    <a href="mailto:you@email.com" class="contact-card">
      <span class="icon">✉️</span>
      <h4>البريد الإلكتروني</h4>
      <p>you@email.com</p>
    </a>
    <a href="tel:+201000000000" class="contact-card">
      <span class="icon">📞</span>
      <h4>الهاتف</h4>
      <p>+20 100 000 0000</p>
    </a>
    <a href="#" class="contact-card">
      <span class="icon">💼</span>
      <h4>LinkedIn</h4>
      <p>linkedin.com/in/maryam</p>
    </a>
    <a href="#" class="contact-card">
      <span class="icon">🐙</span>
      <h4>GitHub</h4>
      <p>github.com/maryam</p>
    </a>
  </div>
</section>

<footer>
  صُنع بـ ❤️ بواسطة <span>مريم أشرف عبدالسميع</span> — © 2026 جميع الحقوق محفوظة
</footer>

<script>
  // شريط التنقل عند التمرير
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 50);
  });

  // قائمة الموبايل
  const menuToggle = document.getElementById('menuToggle');
  const navLinks = document.getElementById('navLinks');
  menuToggle.addEventListener('click', () => {
    navLinks.classList.toggle('active');
    menuToggle.textContent = navLinks.classList.contains('active') ? '✕' : '☰';
  });

  // إغلاق القائمة عند النقر على رابط
  document.querySelectorAll('.nav-links a').forEach(link => {
    link.addEventListener('click', () => {
      navLinks.classList.remove('active');
      menuToggle.textContent = '☰';
    });
  });

  // ظهور العناصر عند التمرير
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = '1';
        entry.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.service-card, .work-card, .contact-card').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(30px)';
    el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
    observer.observe(el);
  });
</script>

</body>
</html>
