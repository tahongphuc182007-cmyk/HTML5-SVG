<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title> SVG Demo </title>
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
    <h1>SVG Demo </h1>
    <p style="text-align: center; color: #555; font-size: 1.1rem;"></p>

    <!-- ==================== 1-3, 5-9, 11-14 giữ nguyên ==================== -->
    <section>
      <h2>1. Hình cơ bản</h2>
      <div class="row">
        <div class="box">
          <svg viewBox="0 0 200 120">
            <rect x="8" y="8" width="84" height="104" rx="6" fill="#ffe082" stroke="#b27b00" stroke-width="2"/>
            <circle cx="140" cy="40" r="28" fill="#90caf9" stroke="#0d47a1" stroke-width="2"/>
            <line x1="120" y1="80" x2="180" y2="100" stroke="#6d4c41" stroke-width="3" stroke-linecap="round"/>
            <polygon points="120,10 160,60 100,60" fill="#aed581" stroke="#558b2f" stroke-width="2"/>
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
              <linearGradient id="g1"><stop offset="0%" stop-color="#ff8a80"/><stop offset="100%" stop-color="#ffcc80"/></linearGradient>
              <filter id="f1"><feGaussianBlur stdDeviation="3"/><feOffset dx="2" dy="2" result="o"/><feBlend in2="o"/></filter>
            </defs>
            <rect x="12" y="12" width="216" height="96" rx="12" fill="url(#g1)" filter="url(#f1)"/>
            <text x="24" y="70" font-size="18" fill="#4e342e">Gradient + Blur</text>
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
              <animate attributeName="cx" from="40" to="160" dur="1.6s" repeatCount="indefinite"/>
              <animate attributeName="fill" values="#4fc3f7;#81c784;#ffb74d;#4fc3f7" dur="4s" repeatCount="indefinite"/>
            </circle>
            <rect x="40" y="15" width="120" height="30" rx="6" fill="#e0e0e0" class="btn"/>
            <style>.btn{transition:0.25s}.btn:hover{transform:scale(1.06);fill:#c8e6c9}</style>
          </svg>
        </div>
      </div>
    </section>

    <!-- ==================== 4. Tương tác JavaScript (ĐÃ NÂNG CẤP SIÊU ĐẸP) ==================== -->
    <section>
      <h2>4. Tương tác JavaScript</h2>
      <div class="row">
        <div class="box">
          <svg id="interactiveSvg" viewBox="0 0 320 140" style="background:#f8f9fa; border-radius:16px;">
            <defs>
              <radialGradient id="glow">
                <stop offset="0%" stop-color="#fff"/>
                <stop offset="100%" stop-color="#ff9800"/>
              </radialGradient>
            </defs>
            <rect x="10" y="20" width="130" height="100" rx="16" fill="#fff3e0" stroke="#ff6d00" stroke-width="3"/>
            <text x="75" y="70" text-anchor="middle" font-size="14" font-weight="600" fill="#d84315">Hover me!</text>

            <g id="magicDot">
              <circle cx="230" cy="70" r="28" fill="#ff5722" opacity="0.9"/>
              <circle cx="230" cy="70" r="38" fill="url(#glow)" opacity="0.4"/>
              <circle cx="230" cy="70" r="12" fill="#fff" opacity="0.6">
                <animate attributeName="r" values="12;16;12" dur="2s" repeatCount="indefinite"/>
              </circle>
            </g>

            <text id="txt" x="230" y="115" text-anchor="middle" font-size="13" fill="#555" font-weight="500">
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
            <rect width="100%" height="100%" fill="#fafafa"/>
            <path id="p" d="M20 80" fill="none" stroke="#1976d2" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
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
            <rect x="10" y="10" width="340" height="100" rx="12" fill="#e3f2fd" stroke="#0d47a1"/>
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
            <path id="curve" d="M30,100 Q200,20 370,100" fill="none"/>
            <path d="M30,100 Q200,20 370,100" fill="none" stroke="#eee" stroke-width="2"/>
            <text font-size="22" font-weight="600" fill="#d81b60">
              <textPath href="#curve" startOffset="8%">Chữ cong theo path cực đẹp ♥</textPath>
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
              <marker id="arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto">
                <path d="M0,0 L0,6 L9,3 z" fill="#f44336"/>
              </marker>
              <marker id="dot" markerWidth="8" markerHeight="8" refX="4" refY="4">
                <circle cx="4" cy="4" r="3" fill="#4caf50"/>
              </marker>
            </defs>
            <line x1="40" y1="40" x2="360" y2="40" stroke="#666" stroke-width="4" marker-end="url(#arrow)"/>
            <polyline points="40,80 140,100 240,60 360,100" stroke="#1976d2" stroke-width="5" fill="none"
                      marker-start="url(#dot)" marker-mid="url(#dot)" marker-end="url(#arrow)"/>
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
              <pattern id="grid" width="40" height="40" patternUnits="userSpaceOnUse">
                <rect width="40" height="40" fill="#e8f5e8"/>
                <circle cx="10" cy="10" r="4" fill="#81c784"/>
                <circle cx="30" cy="30" r="4" fill="#81c784"/>
              </pattern>
              <pattern id="stripes" width="12" height="12" patternTransform="rotate(45)">
                <rect width="6" height="12" fill="#ff9800"/>
              </pattern>
            </defs>
            <rect x="20" y="20" width="160" height="120" fill="url(#grid)" rx="12"/>
            <rect x="220" y="20" width="160" height="120" fill="url(#stripes)" rx="12"/>
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
                <path d="M220,50 C180,10 130,30 130,70 C130,120 220,160 220,160 C220,160 310,120 310,70 C310,30 260,10 220,50"/>
              </clipPath>
              <linearGradient id="loveGrad">
                <stop offset="0%" stop-color="#fff"/>
                <stop offset="100%" stop-color="#e0e0e0"/>
              </linearGradient>
              <mask id="loveMask">
                <rect width="100%" height="100%" fill="#fff"/>
                <text x="50%" y="58%" font-size="68" font-weight="900" text-anchor="middle" fill="black" font-family="system-ui">LOVE</text>
                <text x="50%" y="58%" font-size="68" font-weight="900" text-anchor="middle" fill="url(#loveGrad)" opacity="0.4">LOVE</text>
              </mask>
              <filter id="glow">
                <feGaussianBlur stdDeviation="8" result="coloredBlur"/>
                <feMerge>
                  <feMergeNode in="coloredBlur"/>
                  <feMergeNode in="coloredBlur"/>
                  <feMergeNode in="coloredBlur"/>
                </feMerge>
              </filter>
            </defs>
            <g filter="url(#glow)">
              <image href="https://picsum.photos/600/400?random=1" x="30" y="20" width="180" height="140" clip-path="url(#heartClip)" preserveAspectRatio="xMidYMid slice"/>
            </g>
            <image href="https://picsum.photos/600/400?random=2" x="230" y="20" width="180" height="140" mask="url(#loveMask)" preserveAspectRatio="xMidYMid slice"/>
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
              <path fill="currentColor" d="M12,21.35L10.55,20.03C5.4,15.36 2,12.27 2,8.5C2,5.41 4.42,3 7.5,3 9.24,3 10.91,3.81 12,5.08 13.09,3.81 14.76,3 16.5,3 19.58,3 22,5.41 22,8.5 22,12.27 18.6,15.36 13.45,20.03L12,21.35Z"/>
            </symbol>
            <symbol id="star" viewBox="0 0 24 24">
              <path fill="currentColor" d="M12,17.27L18.18,21 16.54,13.97 22,9.24 14.81,8.62 12,2 9.19,8.62 2,9.24 7.45,13.97 5.82,21 12,17.27Z"/>
            </symbol>
          </svg>
          <div style="display: flex; gap: 30px; justify-content: center">
            <svg width="60" height="60" fill="#e91e63"><use href="#heart"/></svg>
            <svg width="60" height="60" fill="#ff9800"><use href="#star"/></svg>
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
              <feGaussianBlur stdDeviation="10" result="blur"/>
              <feColorMatrix in="blur" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 19 -9" result="goo"/>
              <feComposite in="SourceGraphic" in2="goo" operator="atop"/>
            </filter>
            <g filter="url(#goo)" transform="translate(80,50)">
              <circle cx="40" cy="40" r="30" fill="#ff6ec4"/>
              <circle cx="100" cy="40" r="30" fill="#4fc3f7">
                <animate attributeName="cx" values="100;160;100" dur="4s" repeatCount="indefinite"/>
              </circle>
              <circle cx="200" cy="40" r="30" fill="#96fbc4"/>
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
              <animate attributeName="height" to="120" dur="1s" begin="0.2s" fill="freeze"/>
              <animate attributeName="y" to="40" dur="1s" begin="0.2s" fill="freeze"/>
            </rect>
            <rect x="110" y="160" width="40" height="0" fill="#2196f3">
              <animate attributeName="height" to="80" dur="1s" begin="0.5s" fill="freeze"/>
              <animate attributeName="y" to="80" dur="1s" begin="0.5s" fill="freeze"/>
            </rect>
            <rect x="180" y="160" width="40" height="0" fill="#ff9800">
              <animate attributeName="height" to="150" dur="1s" begin="0.8s" fill="freeze"/>
              <animate attributeName="y" to="10" dur="1s" begin="0.8s" fill="freeze"/>
            </rect>
            <rect x="250" y="160" width="40" height="0" fill="#e91e63">
              <animate attributeName="height" to="100" dur="1s" begin="1.1s" fill="freeze"/>
              <animate attributeName="y" to="60" dur="1s" begin="1.1s" fill="freeze"/>
            </rect>
          </svg>
        </div>
      </div>
    </section>

    <section>
      <h2>14. Nút Like kiểu X/Twitter</h2>
      <div class="row">
        <div class="box" style="text-align: center">
          <button id="likeBtn" style="background:none;border:none;cursor:pointer">
            <svg width="100" height="100" viewBox="0 0 24 24">
              <path id="heartPath" fill="#ccc" d="M12,21.35L10.55,20.03C5.4,15.36 2,12.27 2,8.5C2,5.41 4.42,3 7.5,3 9.24,3 10.91,3.81 12,5.08 13.09,3.81 14.76,3 16.5,3 19.58,3 22,5.41 22,8.5 22,12.27 18.6,15.36 13.45,20.03L12,21.35Z"/>
            </svg>
          </button>
        </div>
      </div>
    </section>

    <!-- ==================== 15. Dark / Light Mode (NÂNG CẤP ĐỈNH CAO) ==================== -->
    <section>
      <h2>15. Dark / Light Mode</h2>
      <div style="text-align: center; padding: 30px 0;">
        <button id="themeToggle" style="
          padding: 16px 32px;
          font-size: 17px;
          font-weight: 600;
          border: 2px solid #1976d2;
          border-radius: 50px;
          background: transparent;
          color: var(--text);
          cursor: pointer;
          display: inline-flex;
          align-items: center;
          gap: 14px;
          transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
          box-shadow: 0 6px 20px rgba(25,118,210,0.25);
        ">
          <span id="sunIcon">Chế độ sáng</span>
          <span id="moonIcon" style="display:none">Chế độ tối</span>
          <svg id="toggleIcon" width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
            <circle cx="12" cy="12" r="5"/>
            <path d="M12 1v2m0 18v2M4.22 4.22l1.42 1.42m12.72 12.72l1.42 1.42M1 12h2m18 0h2M4.22 19.78l1.42-1.42m12.72-12.72l1.42-1.42"/>
          </svg>
        </button>
        <p style="margin-top:16px; font-size:15px; opacity:0.75;">
          Tự động theo hệ thống • Lưu trạng thái vĩnh viễn
        </p>
      </div>
    </section>

    <script>
      // === 4. Tương tác JS – Nâng cấp đỉnh cao ===
      const dotGroup = document.getElementById("magicDot");
      const txt = document.getElementById("txt");
      const colors = ["#ff5722", "#e91e63", "#9c27b0", "#3f51b5", "#00bcd4", "#ff9800"];

      dotGroup.style.cursor = "pointer";
      dotGroup.addEventListener("click", () => {
        const color = colors[Math.floor(Math.random() * colors.length)];
        dotGroup.children[0].setAttribute("fill", color);
        txt.textContent = `Màu: ${color.toUpperCase()}`;
        dotGroup.style.transform = "scale(1.4)";
        setTimeout(() => dotGroup.style.transform = "scale(1)", 300);
      });

      document.getElementById("btnReset").addEventListener("click", () => {
        dotGroup.children[0].setAttribute("fill", "#ff5722");
        txt.textContent = "Click vào chấm cam kìa!";
      });

      // === Vẽ tự do ===
      const drawSvg = document.getElementById("drawArea"), path = document.getElementById("p");
      let d = "", drawing = false;
      const getPoint = (e) => {
        const t = drawSvg.createSVGPoint();
        t.x = e.clientX; t.y = e.clientY;
        return t.matrixTransform(drawSvg.getScreenCTM().inverse());
      };
      drawSvg?.addEventListener("pointerdown", (e) => {
        drawSvg.setPointerCapture(e.pointerId);
        drawing = true;
        const p = getPoint(e);
        d = `M${p.x} ${p.y}`;
        path.setAttribute("d", d);
      });
      drawSvg?.addEventListener("pointermove", (e) => {
        if (!drawing) return;
        const p = getPoint(e);
        d += ` L${p.x} ${p.y}`;
        path.setAttribute("d", d);
      });
      drawSvg?.addEventListener("pointerup", () => drawing = false);
      document.getElementById("clear")?.addEventListener("click", () => {
        d = "M20 80";
        path.setAttribute("d", d);
      });

      // === Nút Like burst ===
      let liked = false;
      document.getElementById("likeBtn").addEventListener("click", () => {
        const h = document.getElementById("heartPath");
        if (!liked) {
          h.setAttribute("fill", "#e91e63");
          h.style.transform = "scale(1.4)";
          h.style.transition = "0.4s";
          setTimeout(() => h.style.transform = "scale(1)", 400);
          for (let i = 0; i < 12; i++) {
            const c = document.createElementNS("http://www.w3.org/2000/svg", "circle");
            c.setAttribute("cx", 50); c.setAttribute("cy", 50); c.setAttribute("r", 4);
            c.setAttribute("fill", "#e91e63");
            likeBtn.querySelector("svg").appendChild(c);
            const a = i * 30, v = 4 + Math.random() * 4;
            c.innerHTML = `<animate attributeName="cx" from="50" to="${50 + v * Math.cos(a * Math.PI / 180) * 10}" dur="0.8s" fill="freeze"/>
                           <animate attributeName="cy" from="50" to="${50 + v * Math.sin(a * Math.PI / 180) * 10}" dur="0.8s" fill="freeze"/>
                           <animate attributeName="opacity" from="1" to="0" dur="0.8s" begin="0.2s"/>`;
            setTimeout(() => c.remove(), 1000);
          }
        } else h.setAttribute("fill", "#ccc");
        liked = !liked;
      });

      // === Dark Mode Toggle – Đỉnh cao UX ===
      const body = document.body;
      const themeToggle = document.getElementById("themeToggle");
      const sunIcon = document.getElementById("sunIcon");
      const moonIcon = document.getElementById("moonIcon");
      const toggleIcon = document.getElementById("toggleIcon");

      const setDark = () => {
        body.classList.add("dark");
        sunIcon.style.display = "none";
        moonIcon.style.display = "inline";
        toggleIcon.innerHTML = '<path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>';
        localStorage.setItem("theme", "dark");
      };

      const setLight = () => {
        body.classList.remove("dark");
        sunIcon.style.display = "inline";
        moonIcon.style.display = "none";
        toggleIcon.innerHTML = '<circle cx="12" cy="12" r="5"/><path d="M12 1v2m0 18v2M4.22 4.22l1.42 1.42m12.72 12.72l1.42 1.42M1 12h2m18 0h2M4.22 19.78l1.42-1.42m12.72-12.72l1.42-1.42"/>';
        localStorage.setItem("theme", "light");
      };

      if (localStorage.getItem("theme") === "dark" || 
          (!localStorage.getItem("theme") && window.matchMedia("(prefers-color-scheme: dark)").matches)) {
        setDark();
      } else {
        setLight();
      }

      themeToggle.addEventListener("click", () => {
        body.classList.contains("dark") ? setLight() : setDark();
      });
    </script>
  </body>
</html>
