<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Tăng Tương Tác</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@700;900&family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: #f5f7fa;
      --text: #333;
      --box: #ffffff;
    }
    body.dark-mode {
      --bg: #1e1e1e;
      --text: #f0f0f0;
      --box: #2a2a2a;
    }
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Roboto', sans-serif;
      background: var(--bg);
      color: var(--text);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      transition: background 0.3s, color 0.3s;
    }
    .poster {
      width: 100%;
      max-width: 800px;
      background: var(--box);
      border-radius: 15px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
      overflow: hidden;
      position: relative;
    }
    .header {
      background: linear-gradient(135deg, #667eea, #764ba2);
      color: white;
      padding: 30px;
      text-align: center;
      position: relative;
    }
    .header h1 {
      font-family: 'Montserrat', sans-serif;
      font-size: 2.5rem;
      font-weight: 900;
      text-transform: uppercase;
      letter-spacing: 2px;
    }
    .toggle-darkmode {
      position: absolute;
      top: 15px;
      right: 20px;
      background: white;
      color: black;
      padding: 5px 10px;
      border-radius: 20px;
      font-size: 0.8rem;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0,0,0,0.2);
      font-weight: bold;
    }
    body.dark-mode .toggle-darkmode {
      background: #444;
      color: white;
    }
    .contact-links {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      padding: 20px;
      gap: 20px;
    }
    .contact-box {
      background: #f1f1f1;
      padding: 15px;
      border-radius: 10px;
      text-align: center;
      flex: 1;
      min-width: 140px;
      box-shadow: 0 3px 10px rgba(0,0,0,0.1);
    }
    body.dark-mode .contact-box {
      background: #333;
    }
    .contact-box img,
    .contact-box svg {
      width: 36px;
      height: 36px;
      margin-bottom: 8px;
    }
    .contact-box a {
      display: block;
      text-decoration: none;
      font-weight: bold;
      color: var(--text);
      font-size: 1rem;
      word-break: break-word;
    }
    .social-section {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
      padding: 20px;
      gap: 20px;
    }
    .social-card {
      flex: 1;
      min-width: 200px;
      background: var(--box);
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
      transition: transform 0.3s ease;
    }
    .social-card:hover {
      transform: translateY(-5px);
    }
    .social-card h2 {
      font-family: 'Montserrat', sans-serif;
      color: #fff;
      padding: 10px;
      margin: -20px -20px 20px -20px;
      font-size: 1.5rem;
      text-align: center;
    }
    .tiktok { background: linear-gradient(135deg, #25F4EE, #000000); }
    .facebook { background: linear-gradient(135deg, #1877F2, #0A48A3); }
    .instagram {
      background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888);
    }
    .social-card ul {
      list-style: none;
    }
    .social-card li {
      padding: 8px 0;
      font-size: 1.1rem;
      padding-left: 25px;
      position: relative;
    }
    .social-card li:before {
      content: '✓';
      position: absolute;
      left: 0;
      color: #4CAF50;
      font-weight: bold;
    }
    .guarantee {
      text-align: center;
      padding: 20px;
      margin: 20px;
      font-style: italic;
      font-size: 1.2rem;
      font-weight: bold;
      background: rgba(255,255,255,0.7);
      border-radius: 10px;
      border: 2px dashed #ff0000;
      color: #ff0000;
      cursor: pointer;
      transition: background 0.3s;
    }
    body.dark-mode .guarantee {
      background: rgba(50, 50, 50, 0.7);
    }
    .guarantee:hover {
      background: rgba(255, 230, 230, 0.8);
    }

    /* Popup Zalo/Facebook + nút đóng */
    .popup-buttons {
      position: fixed;
      bottom: 20px;
      right: 20px;
      z-index: 9999;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .popup-buttons a {
      background: white;
      width: 52px;
      height: 52px;
      border-radius: 50%;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
      display: flex;
      align-items: center;
      justify-content: center;
      transition: 0.2s ease;
    }
    .popup-buttons a:hover {
      transform: scale(1.1);
    }
    @media (max-width: 768px) {
      .header h1 {
        font-size: 1.8rem;
      }
      .social-card {
        min-width: 100%;
      }
      .contact-links {
        flex-direction: column;
        gap: 10px;
      }
    }
  </style>
</head>
<body>
  <div class="poster">
    <div class="header">
      <h1>Tăng Tương Tác</h1>
      <div class="toggle-darkmode" onclick="toggleDarkMode()">🌙 Chế độ tối</div>
    </div>

    <div id="contact-links" class="contact-links">
      <div class="contact-box">
        <img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Icon_of_Zalo.svg" alt="Zalo icon">
        <a href="https://zalo.me/0772597477" target="_blank">Zalo: 0772597477</a>
      </div>
      <div class="contact-box">
        <svg xmlns="http://www.w3.org/2000/svg" fill="#1877F2" viewBox="0 0 24 24">
          <path d="M22.675 0h-21.35C.595 0 0 .595 0 1.326v21.348C0 23.405.595 24 
            1.326 24h11.495v-9.294H9.691V11.01h3.13V8.41c0-3.1 
            1.894-4.788 4.659-4.788 1.325 0 2.464.099 2.795.143v3.24l-1.918.001c-1.504 
            0-1.796.715-1.796 1.763v2.31h3.587l-.467 3.696h-3.12V24h6.116C23.405 24 
            24 23.405 24 22.674V1.326C24 .595 23.405 0 22.675 0z"/>
        </svg>
        <a href="https://www.facebook.com/share/1CCLwi5Ay6/" target="_blank">Facebook: Dũng Hoàng (Cún)</a>
      </div>
    </div>

    <div class="social-section">
      <div class="social-card tiktok">
        <h2>TikTok</h2>
        <ul>
          <li>Follow</li>
          <li>Tim</li>
          <li>View</li>
          <li>Chia sẻ</li>
          <li>Yêu thích</li>
        </ul>
      </div>
      <div class="social-card facebook">
        <h2>Facebook</h2>
        <ul>
          <li>Theo dõi & fanpage</li>
          <li>Like</li>
          <li>Thành viên nhóm</li>
        </ul>
      </div>
      <div class="social-card instagram">
        <h2>Instagram</h2>
        <ul>
          <li>Follow</li>
          <li>Tìm</li>
          <li>View Reels</li>
        </ul>
      </div>
    </div>

    <div class="guarantee">Cam kết - uy tín - chất lượng - nhanh chóng</div>
    <div class="guarantee" onclick="scrollToContact()">Nhấn để liên hệ tư vấn giá bên trên</div>
  </div>

  <!-- Nút Zalo & Facebook góc phải + nút đóng -->
  <div class="popup-buttons" id="popupChat">
    <a href="https://zalo.me/0772597477" target="_blank" title="Zalo">
      <img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Icon_of_Zalo.svg" alt="Zalo" style="width: 28px; height: 28px;">
    </a>
    <a href="https://www.facebook.com/share/1CCLwi5Ay6/" target="_blank" title="Facebook">
      <svg xmlns="http://www.w3.org/2000/svg" width="26" height="26" viewBox="0 0 24 24" fill="#1877F2">
        <path d="M22.675 0h-21.35C.595 0 0 .595 0 1.326v21.348C0 23.405.595 24 
          1.326 24h11.495v-9.294H9.691V11.01h3.13V8.41c0-3.1 
          1.894-4.788 4.659-4.788 1.325 0 2.464.099 2.795.143v3.24l-1.918.001c-1.504 
          0-1.796.715-1.796 1.763v2.31h3.587l-.467 3.696h-3.12V24h6.116C23.405 24 
          24 23.405 24 22.674V1.326C24 .595 23.405 0 22.675 0z"/>
      </svg>
    </a>
    <a href="javascript:void(0)" onclick="closePopup()" title="Đóng" style="background:#ff4444;color:white;font-size:20px;font-weight:bold;">&times;</a>
  </div>

  <script>
    function scrollToContact() {
      const section = document.getElementById("contact-links");
      section.scrollIntoView({ behavior: "smooth" });
    }
    function toggleDarkMode() {
      document.body.classList.toggle("dark-mode");
      const btn = document.querySelector(".toggle-darkmode");
      btn.textContent = document.body.classList.contains("dark-mode") ? "☀️ Chế độ sáng" : "🌙 Chế độ tối";
    }
    function closePopup() {
      const popup = document.getElementById("popupChat");
      popup.style.display = "none";
    }

    // Gửi tin nhắn tự động (mẫu gọi API - cần backend riêng)
    function sendMessageAPI() {
      fetch("https://your-api.com/send-message", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          phone: "0772597477",
          message: "Bạn vừa truy cập trang web, cần hỗ trợ gì không?"
        })
      })
      .then(res => res.json())
      .then(data => console.log("Đã gửi:", data))
      .catch(err => console.error("Lỗi gửi:", err));
    }

    // Kích hoạt gửi tin nhắn tự động khi người dùng vào
    // window.onload = sendMessageAPI;
  </script>
</body>
</html>
