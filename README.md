<html lang="vi">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>SVG Master Demo </title>
    <style>
      :root {
        --bg: #fafafa;
        --text: #1a1a1a;
        --card: white;
        --border: #e0e0e0;
      }
      @media (prefers-color-scheme: dark) {
        :root {
          --bg: #0d1117;
          --text: #e6edf3;
          --card: #161b22;
          --border: #30363d;
        }
      }
      .dark {
        --bg: #0d1117;
        --text: #e6edf3;
        --card: #161b22;
        --border: #30363d;
      }
      body {
        font-family: system-ui, -apple-system, sans-serif;
        margin: 0;
        padding: 20px;
        background: var(--bg);
        color: var(--text);
        line-height: 1.6;
        transition: background 0.4s, color 0.4s;
      }
      h1 {
        text-align: center;
        margin-bottom: 10px;
        font-size: 2.8rem;
        background: linear-gradient(90deg, #1976d2, #9c27b0);
        -webkit-background-clip: text;
        background-clip: text;
        color: transparent;
      }
      h2 {
        color: #1976d2;
        margin-top: 0;
      }
      section {
        margin: 40px 0;
        padding: 24px;
        background: var(--card);
        border: 1px solid var(--border);
        border-radius: 20px;
        box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        transition: all 0.4s;
      }
      section:hover {
        transform: translateY(-8px);
        box-shadow: 0 20px 50px rgba(0, 0, 0, 0.18);
      }
      .row {
        display: flex;
        flex-wrap: wrap;
        gap: 28px;
        align-items: flex-start;
      }
      .box {
        flex: 1 1 360px;
      }
      button {
        padding: 12px 20px;
        border: none;
        border-radius: 12px;
        background: #1976d2;
        color: white;
        cursor: pointer;
        font-weight: 600;
        transition: 0.3s;
      }
      button:hover {
        background: #1565c0;
        transform: translateY(-2px);
      }
      svg {
        max-width: 100%;
        height: auto;
        background: #fff;
        padding: 12px;
        border-radius: 16px;
        box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
      }
      .dark svg {
        background: #1e1e2e;
      }
    </style>
  </head>
  <body>
    <h1>SVG Master Demo </h1>
    <p style="text-align: center; color: #555; font-size: 1.1rem">

    </p>

    <!-- ==================== 1-3, 5-9, 11-14 giữ nguyên ==================== -->
    <section>
      <h2>1. Hình cơ bản</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 200 120">
            <rect
              x="8"
              y="8"
              width="84"
              height="104"
              rx="6"
              fill="#ffe082"
              stroke="#b27b00"
              stroke-width="2"
            />
            <circle
              cx="140"
              cy="40"
              r="28"
              fill="#90caf9"
              stroke="#0d47a1"
              stroke-width="2"
            />
            <line
              x1="120"
              y1="80"
              x2="180"
              y2="100"
              stroke="#6d4c41"
              stroke-width="3"
              stroke-linecap="round"
            />
            <polygon
              points="120,10 160,60 100,60"
              fill="#aed581"
              stroke="#558b2f"
              stroke-width="2"
            />
          </svg>
        </div>
        <div class="box"><p>rect • circle • line • polygon</p></div>
      </div>
    </section>

    <section>
      <h2>2. Gradient + Filter</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 240 120">
            <defs>
              <linearGradient id="g1">
                <stop offset="0%" stop-color="#ff8a80" />
                <stop offset="100%" stop-color="#ffcc80" />
              </linearGradient>
              <filter id="f1">
                <feGaussianBlur stdDeviation="3" />
                <feOffset dx="2" dy="2" result="o" />
                <feBlend in2="o" />
              </filter>
            </defs>
            <rect
              x="12"
              y="12"
              width="216"
              height="96"
              rx="12"
              fill="url(#g1)"
              filter="url(#f1)"
            />
            <text x="24" y="70" font-size="18" fill="#4e342e">
              Gradient + Blur
            </text>
          </svg>
        </div>
      </div>
    </section>

    <section>
      <h2>3. Animation SMIL + CSS</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 200 120">
            <circle cx="40" cy="60" r="18" fill="#4fc3f7">
              <animate
                attributeName="cx"
                from="40"
                to="160"
                dur="1.6s"
                repeatCount="indefinite"
              />
              <animate
                attributeName="fill"
                values="#4fc3f7;#81c784;#ffb74d;#4fc3f7"
                dur="4s"
                repeatCount="indefinite"
              />
            </circle>
            <rect
              x="40"
              y="15"
              width="120"
              height="30"
              rx="6"
              fill="#e0e0e0"
              class="btn"
            />
            <style>
              .btn {
                transition: 0.25s;
              }
              .btn:hover {
                transform: scale(1.06);
                fill: #c8e6c9;
              }
            </style>
          </svg>
        </div>
      </div>
    </section>

    <!-- ==================== 4. Tương tác JavaScript (ĐÃ NÂNG CẤP SIÊU ĐẸP) ==================== -->
    <section>
      <h2>4. Tương tác JavaScript</h2>
      <div class="row">
        <div class="box">
          <svg
            id="interactiveSvg"
            viewBox="0 0 320 140"
            style="background: #f8f9fa; border-radius: 16px"
          >
            <defs>
              <radialGradient id="glow">
                <stop offset="0%" stop-color="#fff" />
                <stop offset="100%" stop-color="#ff9800" />
              </radialGradient>
            </defs>
            <rect
              x="10"
              y="20"
              width="130"
              height="100"
              rx="16"
              fill="#fff3e0"
              stroke="#ff6d00"
              stroke-width="3"
            />
            <text
              x="75"
              y="70"
              text-anchor="middle"
              font-size="14"
              font-weight="600"
              fill="#d84315"
            >
              Hover me!
            </text>

            <g id="magicDot">
              <circle cx="230" cy="70" r="28" fill="#ff5722" opacity="0.9" />
              <circle cx="230" cy="70" r="38" fill="url(#glow)" opacity="0.4" />
              <circle cx="230" cy="70" r="12" fill="#fff" opacity="0.6">
                <animate
                  attributeName="r"
                  values="12;16;12"
                  dur="2s"
                  repeatCount="indefinite"
                />
              </circle>
            </g>

            <text
              id="txt"
              x="230"
              y="115"
              text-anchor="middle"
              font-size="13"
              fill="#555"
              font-weight="500"
            >
              Click vào chấm cam kìa!
            </text>
          </svg>
        </div>
        <div class="box">
          <button id="btnReset">Reset đẹp lung linh</button>
        </div>
      </div>
    </section>

    <!-- ==================== 5. Vẽ tự do (giữ nguyên) ==================== -->
    <section>
      <h2>5. Vẽ tự do bằng chuột</h2>
      <div class="row">
        <div class="box">
          <svg id="drawArea" viewBox="0 0 400 150">
            <rect width="100%" height="100%" fill="#fafafa" />
            <path
              id="p"
              d="M20 80"
              fill="none"
              stroke="#1976d2"
              stroke-width="3"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
          <p>Nhấn giữ và vẽ thoải mái!</p>
        </div>
        <div class="box"><button id="clear">Clear</button></div>
      </div>
    </section>

    <!-- ==================== 6-9 giữ nguyên ==================== -->
    <section>
      <h2>6. Responsive SVG</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 360 120" preserveAspectRatio="xMidYMid meet">
            <rect
              x="10"
              y="10"
              width="340"
              height="100"
              rx="12"
              fill="#e3f2fd"
              stroke="#0d47a1"
            />
            <text x="24" y="64" font-size="22">Responsive SVG</text>
          </svg>
        </div>
      </div>
    </section>

    <section>
      <h2>7. Text trên đường cong (textPath)</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 400 140">
            <path id="curve" d="M30,100 Q200,20 370,100" fill="none" />
            <path
              d="M30,100 Q200,20 370,100"
              fill="none"
              stroke="#eee"
              stroke-width="2"
            />
            <text font-size="22" font-weight="600" fill="#d81b60">
              <textPath href="#curve" startOffset="8%">
                Chữ cong theo path cực đẹp ♥
              </textPath>
            </text>
          </svg>
        </div>
      </div>
    </section>

    <section>
      <h2>8. Marker (mũi tên, chấm)</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 400 140">
            <defs>
              <marker
                id="arrow"
                markerWidth="10"
                markerHeight="10"
                refX="8"
                refY="3"
                orient="auto"
              >
                <path d="M0,0 L0,6 L9,3 z" fill="#f44336" />
              </marker>
              <marker
                id="dot"
                markerWidth="8"
                markerHeight="8"
                refX="4"
                refY="4"
              >
                <circle cx="4" cy="4" r="3" fill="#4caf50" />
              </marker>
            </defs>
            <line
              x1="40"
              y1="40"
              x2="360"
              y2="40"
              stroke="#666"
              stroke-width="4"
              marker-end="url(#arrow)"
            />
            <polyline
              points="40,80 140,100 240,60 360,100"
              stroke="#1976d2"
              stroke-width="5"
              fill="none"
              marker-start="url(#dot)"
              marker-mid="url(#dot)"
              marker-end="url(#arrow)"
            />
          </svg>
        </div>
      </div>
    </section>

    <section>
      <h2>9. Pattern (hình nền lặp)</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 400 160">
            <defs>
              <pattern
                id="grid"
                width="40"
                height="40"
                patternUnits="userSpaceOnUse"
              >
                <rect width="40" height="40" fill="#e8f5e8" />
                <circle cx="10" cy="10" r="4" fill="#81c784" />
                <circle cx="30" cy="30" r="4" fill="#81c784" />
              </pattern>
              <pattern
                id="stripes"
                width="12"
                height="12"
                patternTransform="rotate(45)"
              >
                <rect width="6" height="12" fill="#ff9800" />
              </pattern>
            </defs>
            <rect
              x="20"
              y="20"
              width="160"
              height="120"
              fill="url(#grid)"
              rx="12"
            />
            <rect
              x="220"
              y="20"
              width="160"
              height="120"
              fill="url(#stripes)"
              rx="12"
            />
          </svg>
        </div>
      </div>
    </section>

    <!-- ==================== 10. ClipPath & Mask (NÂNG CẤP SIÊU NGHỆ) ==================== -->
    <section>
      <h2>10. ClipPath & Mask</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 440 180">
            <defs>
              <clipPath id="heartClip">
                <path
                  d="M220,50 C180,10 130,30 130,70 C130,120 220,160 220,160 C220,160 310,120 310,70 C310,30 260,10 220,50"
                />
              </clipPath>
              <linearGradient id="loveGrad">
                <stop offset="0%" stop-color="#fff" />
                <stop offset="100%" stop-color="#e0e0e0" />
              </linearGradient>
              <mask id="loveMask">
                <rect width="100%" height="100%" fill="#fff" />
                <text
                  x="50%"
                  y="58%"
                  font-size="68"
                  font-weight="900"
                  text-anchor="middle"
                  fill="black"
                  font-family="system-ui"
                >
                  LOVE
                </text>
                <text
                  x="50%"
                  y="58%"
                  font-size="68"
                  font-weight="900"
                  text-anchor="middle"
                  fill="url(#loveGrad)"
                  opacity="0.4"
                >
                  LOVE
                </text>
              </mask>
              <filter id="glow">
                <feGaussianBlur stdDeviation="8" result="coloredBlur" />
                <feMerge>
                  <feMergeNode in="coloredBlur" />
                  <feMergeNode in="coloredBlur" />
                  <feMergeNode in="coloredBlur" />
                </feMerge>
              </filter>
            </defs>
            <g filter="url(#glow)">
              <image
                href="https://picsum.photos/600/400?random=1"
                x="30"
                y="20"
                width="180"
                height="140"
                clip-path="url(#heartClip)"
                preserveAspectRatio="xMidYMid slice"
              />
            </g>
            <image
              href="https://picsum.photos/600/400?random=2"
              x="230"
              y="20"
              width="180"
              height="140"
              mask="url(#loveMask)"
              preserveAspectRatio="xMidYMid slice"
            />
          </svg>
        </div>
      </div>
    </section>

    <!-- 11-14 giữ nguyên đẹp sẵn -->
    <section>
      <h2>11. Icon System (symbol + use)</h2>
      <div class="row">
        <div class="box">
          <svg style="display: none">
            <symbol id="heart" viewBox="0 0 24 24">
              <path
                fill="currentColor"
                d="M12,21.35L10.55,20.03C5.4,15.36 2,12.27 2,8.5C2,5.41 4.42,3 7.5,3 9.24,3 10.91,3.81 12,5.08 13.09,3.81 14.76,3 16.5,3 19.58,3 22,5.41 22,8.5 22,12.27 18.6,15.36 13.45,20.03L12,21.35Z"
              />
            </symbol>
            <symbol id="star" viewBox="0 0 24 24">
              <path
                fill="currentColor"
                d="M12,17.27L18.18,21 16.54,13.97 22,9.24 14.81,8.62 12,2 9.19,8.62 2,9.24 7.45,13.97 5.82,21 12,17.27Z"
              />
            </symbol>
          </svg>
          <div style="display: flex; gap: 30px; justify-content: center">
            <svg width="60" height="60" fill="#e91e63">
              <use href="#heart" />
            </svg>
            <svg width="60" height="60" fill="#ff9800">
              <use href="#star" />
            </svg>
          </div>
        </div>
      </div>
    </section>

    <section>
      <h2>12. Gooey Effect (hot trend)</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 400 200" style="background: #000">
            <filter id="goo">
              <feGaussianBlur stdDeviation="10" result="blur" />
              <feColorMatrix
                in="blur"
                values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 19 -9"
                result="goo"
              />
              <feComposite in="SourceGraphic" in2="goo" operator="atop" />
            </filter>
            <g filter="url(#goo)" transform="translate(80,50)">
              <circle cx="40" cy="40" r="30" fill="#ff6ec4" />
              <circle cx="100" cy="40" r="30" fill="#4fc3f7">
                <animate
                  attributeName="cx"
                  values="100;160;100"
                  dur="4s"
                  repeatCount="indefinite"
                />
              </circle>
              <circle cx="200" cy="40" r="30" fill="#96fbc4" />
            </g>
          </svg>
        </div>
      </div>
    </section>

    <section>
      <h2>13. Biểu đồ cột động</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 400 200">
            <rect x="40" y="160" width="40" height="0" fill="#4caf50">
              <animate
                attributeName="height"
                to="120"
                dur="1s"
                begin="0.2s"
                fill="freeze"
              />
              <animate
                attributeName="y"
                to="40"
                dur="1s"
                begin="0.2s"
                fill="freeze"
              />
            </rect>
            <rect x="110" y="160" width="40" height="0" fill="#2196f3">
              <animate
                attributeName="height"
                to="80"
                dur="1s"
                begin="0.5s"
                fill="freeze"
              />
              <animate
                attributeName="y"
                to="80"
                dur="1s"
                begin="0.5s"
                fill="freeze"
              />
            </rect>
            <rect x="180" y="160" width="40" height="0" fill="#ff9800">
              <animate
                attributeName="height"
                to="150"
                dur="1s"
                begin="0.8s"
                fill="freeze"
              />
              <animate
                attributeName="y"
                to="10"
                dur="1s"
                begin="0.8s"
                fill="freeze"
              />
            </rect>
            <rect x="250" y="160" width="40" height="0" fill="#e91e63">
              <animate
                attributeName="height"
                to="100"
                dur="1s"
                begin="1.1s"
                fill="freeze"
              />
              <animate
                attributeName="y"
                to="60"
                dur="1s"
                begin="1.1s"
                fill="freeze"
              />
            </rect>
          </svg>
        </div>
      </div>
    </section>

    <section>
      <h2>14. Nút Like kiểu X/Twitter</h2>
      <div class="row">
        <div class="box" style="text-align: center">
          <button
            id="likeBtn"
            style="background: none; border: none; cursor: pointer"
          >
            <svg width="100" height="100" viewBox="0 0 24 24">
              <path
                id="heartPath"
                fill="#ccc"
                d="M12,21.35L10.55,20.03C5.4,15.36 2,12.27 2,8.5C2,5.41 4.42,3 7.5,3 9.24,3 10.91,3.81 12,5.08 13.09,3.81 14.76,3 16.5,3 19.58,3 22,5.41 22,8.5 22,12.27 18.6,15.36 13.45,20.03L12,21.35Z"
              />
            </svg>
          </button>
        </div>
      </div>
    </section>

    <!-- ==================== 15. Dark / Light Mode (NÂNG CẤP ĐỈNH CAO) ==================== -->
    <section>
     <!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>SVG Master 2025 - Perfect Final</title>
<style>
  :root{--bg:#fafafa;--text:#111;--card:#fff;--glass:rgba(255,255,255,0.1);}
  .dark{--bg:#0b0e17;--text:#e0e7ff;--card:#1a1f2e;--glass:rgba(10,15,40,0.7);}

  body{
    margin:0;padding:20px;background:var(--bg);color:var(--text);
    font-family:system-ui,-apple-system,sans-serif;
    min-height:100vh;transition:background 1s ease;
    perspective:2000px;overflow:hidden;
  }
  h1{
    text-align:center;font-size:3.6rem;margin:30px 0;
    background:linear-gradient(90deg,#8b5cf6,#ec4899,#f59e0b,#10b981,#06b6d4);
    -webkit-background-clip:text;background-clip:text;color:transparent;
  }
  section{
    margin:80px auto;max-width:1000px;padding:50px;background:var(--card);
    border-radius:32px;box-shadow:0 20px 70px rgba(0,0,0,.25);
    text-align:center;position:relative;overflow:hidden;
  }

  /* ==================== PHẦN 15 – HOÀN HẢO 100% ==================== */
  .glass-card{
    width:440px;height:260px;margin:40px auto;position:relative;
    cursor:pointer;
  }
  .glass{
    position:absolute;inset:0;border-radius:38px;
    backdrop-filter:blur(30px);-webkit-backdrop-filter:blur(30px);
    background:var(--glass);border:1px solid rgba(255,255,255,.2);
    box-shadow:0 40px 100px rgba(0,0,0,.5);
  }

  .card{
    width:100%;height:100%;position:relative;
    transform-style:preserve-3d;
    transition:transform 1.6s cubic-bezier(.68,-0.55,.27,1.55);
  }
  .card.flipped{transform:rotateY(180deg);}

  .face{
    position:absolute;inset:0;border-radius:38px;
    backface-visibility:hidden;
    display:flex;flex-direction:column;align-items:center;justify-content:center;gap:30px;
  }
  .front{
    background:linear-gradient(135deg,#ffeaa7,#74b9ff);
  }
  .back{
    background:linear-gradient(135deg,#1e1b4b,#0f172a);
    transform:rotateY(180deg);
  }

  /* QUAN TRỌNG: Nội dung không bị lật ngược */
  .content{
    backface-visibility:hidden;
  }
  .card.flipped .content{
    transform:rotateY(180deg);
  }

  .sun-moon{width:120px;height:120px;}
  .greeting{
    font-size:42px;font-weight:900;letter-spacing:2px;
    opacity:0;transform:translateY(30px);
    transition:all 1.2s ease;
  }
  .greeting.show{opacity:1;transform:none;}

  /* Mưa sao băng */
  .shooting-stars{
    position:fixed;inset:0;pointer-events:none;z-index:1;
    opacity:0;transition:opacity 1.5s;
  }
  .dark .shooting-stars{opacity:1;}
  .meteor{
    position:absolute;width:2px;height:2px;background:#fff;
    box-shadow:0 0 12px #fff;
  }
  .meteor::before{
    content:'';position:absolute;top:0;left:0;
    width:160px;height:2px;
    background:linear-gradient(90deg,#fff,transparent);
    transform:rotate(-45deg);transform-origin:left;
    animation:meteor 4s linear infinite;
  }
  @keyframes meteor{
    0%{transform:translateX(-300px) translateY(-100px) rotate(-45deg);opacity:0;}
    15%{opacity:1;}
    100%{transform:translateX(200vw) translateY(200vh) rotate(-45deg);opacity:0;}
  }

  .particles span{
    position:absolute;width:12px;height:12px;border-radius:50%;
    pointer-events:none;opacity:0;
    animation:particle 1.5s ease-out forwards;
  }
  @keyframes particle{to{transform:translate(var(--x),var(--y)) scale(0);opacity:0;}}
</style>
</head>
<body>

<h1>SVG Master 2025</h1>
<p style="text-align:center;font-size:1.5rem;opacity:.9;margin-bottom:80px;">
  Bản đẹp nhất Việt Nam – Good Morning luôn hiện trước!
</p>

<section>
  <h2>15. Dark / Light Mode – Perfect Final</h2>

  <div class="glass-card" id="toggle">
    <div class="glass"></div>
    <div class="card" id="card">
      <!-- MẶT SÁNG – HIỆN TRƯỚC -->
      <div class="face front">
        <div class="content">
          <svg class="sun-moon" viewBox="0 0 100 100">
            <circle cx="50" cy="50" r="30" fill="#fbbf24"/>
            <g stroke="#fbbf24" stroke-width="7" stroke-linecap="round">
              <line x1="50" y1="8" x2="50" y2="0"/>
              <line x1="50" y1="92" x2="50" y2="100"/>
              <line x1="8" y1="50" x2="0" y2="50"/>
              <line x1="92" y1="50" x2="100" y2="50"/>
              <line x1="22" y1="22" x2="14" y2="14"/>
              <line x1="78" y1="78" x2="86" y2="86"/>
              <line x1="22" y1="78" x2="14" y2="86"/>
              <line x1="78" y1="22" x2="86" y2="14"/>
            </g>
          </svg>
          <div class="greeting" id="morning">Good Morning!</div>
        </div>
      </div>

      <!-- MẶT TỐI -->
      <div class="face back">
        <div class="content">
          <svg class="sun-moon" viewBox="0 0 100 100">
            <path d="M52,15 A37,37 0 1,1 70,85 A47,47 0 0,0 52,15 Z" fill="#e0e0e0"/>
          </svg>
          <div class="greeting" id="night">Good Night!</div>
        </div>
      </div>
    </div>
  </div>

  <p style="font-size:21px;opacity:.9;margin-top:40px;">
    Good Morning luôn hiện trước • Chữ & icon không bao giờ ngược • Mưa sao băng cực đẹp
  </p>

  <div class="particles" id="particles"></div>
  <div class="shooting-stars" id="stars"></div>
</section>

<script>

const body = document.body;
const card = document.getElementById('card');
const morning = document.getElementById('morning');
const night = document.getElementById('night');
const toggle = document.getElementById('toggle');
const particles = document.getElementById('particles');
const stars = document.getElementById('stars');

// Mưa sao băng
function startMeteors(){
  if(!body.classList.contains('dark')){stars.innerHTML='';return;}
  setInterval(()=>{
    const m = document.createElement('div');
    m.className='meteor';
    m.style.left = Math.random()*100 + 'vw';
    m.style.top = Math.random()*40 + 'vh';
    m.style.animationDuration = (Math.random()*3 + 3)+'s';
    stars.appendChild(m);
    setTimeout(()=>m.remove(),8000);
  },1200);
}

// Particle
function spark(x,y){
  for(let i=0;i<40;i++){
    const p = document.createElement('span');
    const a = Math.PI*2*i/40;
    const v = 7+Math.random()*10;
    p.style.left=x+'px'; p.style.top=y+'px';
    p.style.setProperty('--x',Math.cos(a)*v*70+'px');
    p.style.setProperty('--y',Math.sin(a)*v*70+'px');
    p.style.background = body.classList.contains('dark')?'#93c5fd':'#fbbf24';
    particles.appendChild(p);
    setTimeout(()=>p.remove(),1800);
  }
}

// Áp dụng theme
function setTheme(dark){
  if(dark){
    body.classList.add('dark');
    card.classList.add('flipped');
    night.classList.add('show');
    morning.classList.remove('show');
    startMeteors();
  }else{
    body.classList.remove('dark');
    card.classList.remove('flipped');
    morning.classList.add('show');
    night.classList.remove('show');
    stars.innerHTML='';
  }
}

// ƯU TIÊN GOOD MORNING HIỆN TRƯỚC (dù hệ thống dark)
const saved = localStorage.getItem('theme');
const isDark = saved === 'dark';

setTheme(isDark);
setTimeout(()=> isDark ? night.classList.add('show') : morning.classList.add('show'), 100);

toggle.addEventListener('click',(e)=>{
  const rect = toggle.getBoundingClientRect();
  spark(e.clientX-rect.left, e.clientY-rect.top);
  
  const willDark = !body.classList.contains('dark');
  setTheme(willDark);
  localStorage.setItem('theme', willDark?'dark':'light');
});
</script>
</body>
</html>
