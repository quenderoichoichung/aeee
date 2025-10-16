<!doctype html>
<html lang="vi">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>TanLoc Executor</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    :root {
      --primary: #8b5cf6;
      --primary-dark: #7c3aed;
      --primary-light: #a78bfa;
      --secondary: #06b6d4;
      --secondary-dark: #0891b2;
      --accent: #f59e0b;
      --accent-alt: #10b981;
      --dark: #0f172a;
      --darker: #0a0f1c;
      --light: #f8fafc;
      --glass-bg: rgba(15, 23, 42, 0.7);
      --glass-border: rgba(255, 255, 255, 0.1);
      --glass-highlight: rgba(255, 255, 255, 0.05);
      --success: #10b981;
      --error: #ef4444;
      --warning: #f59e0b;
      --info: #3b82f6;
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    body {
      font-family: 'Poppins', system-ui, sans-serif;
      background: linear-gradient(135deg, var(--darker), var(--dark)), 
                  url("https://i.pinimg.com/originals/a6/c5/dc/a6c5dc5ff0620933cf6a7e76fec0e0b2.jpg") no-repeat center center fixed;
      background-size: cover;
      background-blend-mode: overlay;
      color: var(--light);
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
      padding: 28px;
      position: relative;
      overflow-x: hidden;
    }
    
    body::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at 20% 80%, rgba(139, 92, 246, 0.15) 0%, transparent 50%),
                  radial-gradient(circle at 80% 20%, rgba(6, 182, 212, 0.1) 0%, transparent 50%);
      z-index: 0;
      pointer-events: none;
    }
    
    .container {
      width: 100%;
      max-width: 900px;
      z-index: 1;
      display: flex;
      flex-direction: column;
      gap: 28px;
    }
    
    .avatar {
      display: flex;
      justify-content: center;
      position: relative;
    }
    
    .avatar::before {
      content: '';
      position: absolute;
      width: 110px;
      height: 110px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      z-index: -1;
      filter: blur(15px);
      opacity: 0.6;
      animation: pulse 4s infinite ease-in-out;
    }
    
    .avatar img {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      border: 3px solid rgba(255, 255, 255, 0.2);
      box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
      transition: all 0.3s ease;
    }
    
    .avatar img:hover {
      transform: scale(1.05);
      box-shadow: 0 10px 30px rgba(139, 92, 246, 0.4);
    }
    
    .panel {
      padding: 24px;
      border-radius: 20px;
      background: var(--glass-bg);
      backdrop-filter: blur(20px);
      border: 1px solid var(--glass-border);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3),
                  inset 0 1px 0 rgba(255, 255, 255, 0.1);
      animation: fadeIn 0.5s ease;
      position: relative;
      overflow: hidden;
    }
    
    .panel::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--primary-light), transparent);
    }
    
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    @keyframes pulse {
      0%, 100% { transform: scale(1); opacity: 0.6; }
      50% { transform: scale(1.05); opacity: 0.8; }
    }
    
    .title {
      text-align: center;
      font-weight: 700;
      margin-bottom: 20px;
      color: var(--light);
      font-size: 22px;
      letter-spacing: 0.5px;
      position: relative;
      display: inline-block;
      width: 100%;
    }
    
    .title::after {
      content: '';
      position: absolute;
      bottom: -8px;
      left: 50%;
      transform: translateX(-50%);
      width: 60px;
      height: 3px;
      background: linear-gradient(90deg, var(--primary), var(--secondary));
      border-radius: 3px;
    }
    
    .exec-list {
      display: flex;
      flex-direction: column;
      gap: 14px;
    }
    
    .exec-btn {
      padding: 16px 20px;
      border-radius: 14px;
      font-weight: 600;
      font-size: 16px;
      text-align: center;
      color: var(--light);
      text-decoration: none;
      transition: all 0.4s ease;
      box-shadow: 0 6px 15px rgba(0, 0, 0, 0.3);
      display: block;
      width: 100%;
      position: relative;
      overflow: hidden;
      border: none;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
    }
    
    .exec-btn::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
      transition: left 0.6s ease;
    }
    
    .exec-btn:hover::before {
      left: 100%;
    }
    
    .exec-btn:hover {
      transform: translateY(-5px);
      box-shadow: 0 12px 20px rgba(0, 0, 0, 0.4);
    }
    
    .exec-btn:active {
      transform: translateY(-2px);
    }
    
    .delta {
      background: linear-gradient(135deg, #6366f1, var(--primary));
    }
    
    .codex {
      background: linear-gradient(135deg, var(--primary), var(--secondary));
    }
    
    .ronix {
      background: linear-gradient(135deg, var(--secondary), #0ea5e9);
    }
    
    .krnl {
      background: linear-gradient(135deg, #1e293b, var(--primary-dark));
    }
    
    .overlay {
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.7);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 9999;
      backdrop-filter: blur(8px);
    }
    
    .popup {
      background: var(--glass-bg);
      padding: 24px;
      border-radius: 18px;
      backdrop-filter: blur(25px);
      display: flex;
      flex-direction: column;
      gap: 16px;
      min-width: 300px;
      text-align: center;
      animation: scaleIn 0.35s ease;
      position: relative;
      border: 2px solid transparent;
      background-clip: padding-box;
    }
    
    .popup::before {
      content: '';
      position: absolute;
      top: -2px;
      left: -2px;
      right: -2px;
      bottom: -2px;
      background: linear-gradient(45deg, #000000, #3b82f6, #8b5cf6, #000000, #3b82f6, #8b5cf6);
      background-size: 400% 400%;
      border-radius: 20px;
      z-index: -1;
      animation: borderAnimation 3s ease infinite;
    }
    
    @keyframes scaleIn {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }
    
    @keyframes borderAnimation {
      0%, 100% {
        background-position: 0% 50%;
      }
      50% {
        background-position: 100% 50%;
      }
    }
    
    .popup h3 {
      font-size: 18px;
      color: var(--light);
      font-weight: 600;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }
    
    .scripts {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 20px;
    }
    
    .script-card {
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid transparent;
      border-radius: 16px;
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 12px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
      transition: all 0.4s cubic-bezier(0.215, 0.61, 0.355, 1);
      position: relative;
      overflow: hidden;
      backdrop-filter: blur(10px);
    }
    
    .script-card::before {
      content: '';
      position: absolute;
      top: -2px;
      left: -2px;
      right: -2px;
      bottom: -2px;
      background: linear-gradient(45deg, 
        transparent, 
        transparent, 
        #0ea5e9, 
        #8b5cf6, 
        #1e293b,
        transparent, 
        transparent);
      background-size: 400% 400%;
      border-radius: 18px;
      z-index: -1;
      opacity: 0;
      transition: opacity 0.4s ease;
      animation: none;
    }
    
    .script-card:hover::before {
      opacity: 1;
      animation: borderGlow 3s linear infinite;
    }
    
    @keyframes borderGlow {
      0%, 100% {
        background-position: 0% 50%;
      }
      50% {
        background-position: 100% 50%;
      }
    }
    
    .script-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5);
      background: rgba(255, 255, 255, 0.08);
      border-color: rgba(139, 92, 246, 0.3);
    }
    
    .script-title {
      font-weight: 600;
      font-size: 16px;
      color: var(--light);
      display: flex;
      align-items: center;
      gap: 8px;
    }
    
    .script-desc {
      font-size: 13px;
      color: #cbd5e1;
      line-height: 1.4;
    }
    
    .btn-row {
      display: flex;
      gap: 10px;
      margin-top: auto;
    }
    
    .copy-btn {
      flex: 1;
      padding: 10px 14px;
      border: 0;
      border-radius: 10px;
      cursor: pointer;
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      font-weight: 600;
      font-size: 14px;
      color: var(--light);
      transition: all 0.3s ease;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }
    
    .copy-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
    }
    
    .delete-btn {
      background: var(--error);
      color: var(--light);
      border: none;
      border-radius: 10px;
      padding: 10px 14px;
      cursor: pointer;
      font-weight: 600;
      font-size: 14px;
      transition: all 0.3s ease;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }
    
    .delete-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 12px rgba(239, 68, 68, 0.4);
    }
    
    .admin-btn {
      position: fixed;
      bottom: 25px;
      right: 25px;
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      color: var(--light);
      font-weight: 700;
      font-size: 20px;
      border: 0;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
      cursor: pointer;
      z-index: 9999;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.4s ease;
    }
    
    .admin-btn:hover {
      transform: scale(1.1) rotate(90deg);
      box-shadow: 0 10px 25px rgba(139, 92, 246, 0.5);
    }
    
    .admin-panel {
      position: fixed;
      bottom: 95px;
      right: 25px;
      background: var(--glass-bg);
      border: 1px solid var(--glass-border);
      border-radius: 16px;
      padding: 20px;
      display: none;
      flex-direction: column;
      gap: 16px;
      width: 320px;
      max-height: 70vh;
      overflow-y: auto;
      z-index: 9998;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
      backdrop-filter: blur(20px);
    }
    
    .admin-panel input, .admin-panel textarea {
      width: 100%;
      padding: 10px 12px;
      border-radius: 8px;
      border: 1px solid var(--glass-border);
      background: rgba(15, 23, 42, 0.8);
      color: var(--light);
      font-size: 14px;
      transition: all 0.3s ease;
    }
    
    .admin-panel input:focus, .admin-panel textarea:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 2px rgba(139, 92, 246, 0.3);
    }
    
    .admin-panel h4 {
      color: var(--primary-light);
      font-size: 15px;
      font-weight: 600;
      margin-top: 10px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    
    .admin-panel button {
      padding: 10px 14px;
      border-radius: 8px;
      border: 0;
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      font-weight: 600;
      color: var(--light);
      cursor: pointer;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }
    
    .admin-panel button:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
    }
    
    .toast {
      position: fixed;
      bottom: 25px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(15, 23, 42, 0.9);
      color: white;
      padding: 14px 28px;
      border-radius: 12px;
      z-index: 10000;
      opacity: 0;
      transition: opacity 0.3s ease, transform 0.3s ease;
      backdrop-filter: blur(15px);
      border: 1px solid var(--glass-border);
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: 500;
      max-width: 90%;
    }
    
    .toast.show {
      opacity: 1;
      transform: translateX(-50%) translateY(-10px);
    }
    
    .toast.success {
      background: rgba(16, 185, 129, 0.9);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }
    
    .toast.error {
      background: rgba(239, 68, 68, 0.9);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }
    
    .toast.warning {
      background: rgba(245, 158, 11, 0.9);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }
    
    .toast.info {
      background: rgba(59, 130, 246, 0.9);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }
    
    .confirm-dialog {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.7);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 10001;
      backdrop-filter: blur(8px);
    }
    
    .confirm-content {
      background: var(--glass-bg);
      padding: 28px;
      border-radius: 18px;
      backdrop-filter: blur(20px);
      border: 1px solid var(--glass-border);
      box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
      max-width: 380px;
      text-align: center;
    }
    
    .confirm-buttons {
      display: flex;
      gap: 12px;
      margin-top: 22px;
      justify-content: center;
    }
    
    .confirm-buttons button {
      padding: 10px 22px;
      border-radius: 10px;
      border: none;
      cursor: pointer;
      font-weight: 600;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }
    
    .confirm-yes {
      background: var(--error);
      color: white;
    }
    
    .confirm-yes:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 12px rgba(239, 68, 68, 0.4);
    }
    
    .confirm-no {
      background: var(--success);
      color: white;
    }
    
    .confirm-no:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 12px rgba(16, 185, 129, 0.4);
    }
    
    @media (max-width: 768px) {
      .container {
        gap: 20px;
      }
      
      .panel {
        padding: 18px;
      }
      
      .scripts {
        grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
        gap: 14px;
      }
      
      .admin-panel {
        width: calc(100vw - 40px);
        right: 20px;
      }
    }
    
    @media (max-width: 480px) {
      body {
        padding: 20px;
      }
      
      .scripts {
        grid-template-columns: 1fr;
      }
      
      .exec-btn {
        padding: 14px 16px;
        font-size: 15px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="avatar">
      <img src="https://i.pinimg.com/originals/82/9b/74/829b74c0e393c4c47907f2dfffc64fc2.gif" alt="Avatar">
    </div>
    
    <div class="panel">
      <div class="title"><i class="fas fa-rocket"></i> Executor</div>
      <div class="exec-list">
        <a href="javascript:void(0)" class="exec-btn delta" onclick="openPopup('delta-popup')">
          <i class="fas fa-bolt"></i> Delta X
        </a>
        <a href="javascript:void(0)" class="exec-btn codex" onclick="openPopup('codex-popup')">
          <i class="fas fa-code"></i> Codex
        </a>
        <a href="javascript:void(0)" class="exec-btn ronix" onclick="openPopup('ronix-popup')">
          <i class="fas fa-star"></i> Ronix
        </a>
        <a href="javascript:void(0)" class="exec-btn krnl" onclick="openPopup('krnl-popup')">
          <i class="fas fa-shield-alt"></i> KRNL
        </a>
      </div>
    </div>

    <div class="panel">
      <div class="title"><i class="fas fa-scroll"></i> SCRIPTS</div>
      <div class="scripts" id="script-list"></div>
    </div>
  </div>
  
  <!-- Popups -->
  <div class="overlay" id="delta-popup" onclick="closeOverlay(event,'delta-popup')">
    <div class="popup">
      <h3><i class="fas fa-bolt"></i> Delta</h3>
      <a id="delta-global" href="#" class="exec-btn delta" onclick="downloadFile('delta-global')">
        <i class="fas fa-download"></i> Delta Global
      </a>
      <a id="delta-vng" href="#" class="exec-btn delta" onclick="downloadFile('delta-vng')">
        <i class="fas fa-download"></i> Delta VNG
      </a>
    </div>
  </div>
  
  <div class="overlay" id="codex-popup" onclick="closeOverlay(event,'codex-popup')">
    <div class="popup">
      <h3><i class="fas fa-code"></i> Codex</h3>
      <a id="codex-global" href="#" class="exec-btn codex" onclick="downloadFile('codex-global')">
        <i class="fas fa-download"></i> Codex Global
      </a>
      <a id="codex-vng" href="#" class="exec-btn codex" onclick="downloadFile('codex-vng')">
        <i class="fas fa-download"></i> Codex VNG
      </a>
    </div>
  </div>
  
  <div class="overlay" id="ronix-popup" onclick="closeOverlay(event,'ronix-popup')">
    <div class="popup">
      <h3><i class="fas fa-star"></i> Ronix</h3>
      <a id="ronix-global" href="#" class="exec-btn ronix" onclick="downloadFile('ronix-global')">
        <i class="fas fa-download"></i> Ronix Global
      </a>
      <a id="ronix-vng" href="#" class="exec-btn ronix" onclick="downloadFile('ronix-vng')">
        <i class="fas fa-download"></i> Ronix VNG
      </a>
    </div>
  </div>
  
  <div class="overlay" id="krnl-popup" onclick="closeOverlay(event,'krnl-popup')">
    <div class="popup">
      <h3><i class="fas fa-shield-alt"></i> KRNL</h3>
      <a id="krnl-global" href="#" class="exec-btn krnl" onclick="downloadFile('krnl-global')">
        <i class="fas fa-download"></i> KRNL Global
      </a>
      <a id="krnl-vng" href="#" class="exec-btn krnl" onclick="downloadFile('krnl-vng')">
        <i class="fas fa-download"></i> KRNL VNG
      </a>
    </div>
  </div>
  
  <!-- Toast and Confirm -->
  <div class="toast" id="toast"></div>
  
  <div class="confirm-dialog" id="confirm-dialog">
    <div class="confirm-content">
      <h3 id="confirm-message"><i class="fas fa-exclamation-triangle"></i> Bạn có chắc muốn xóa script này?</h3>
      <div class="confirm-buttons">
        <button class="confirm-yes" id="confirm-yes">
          <i class="fas fa-check"></i> Có
        </button>
        <button class="confirm-no" id="confirm-no">
          <i class="fas fa-times"></i> Không
        </button>
      </div>
    </div>
  </div>
  
  <!-- Admin Panel -->
  <button class="admin-btn" onclick="openAdmin()">
    <i class="fas fa-cogs"></i>
  </button>
  
  <div class="admin-panel" id="admin-panel">
    <input type="password" id="admin-pass" placeholder="Nhập mật khẩu">
    <button onclick="checkPass()">
      <i class="fas fa-sign-in-alt"></i> Login
    </button>
    <div id="admin-content" style="display:none">
      <h4><i class="fas fa-link"></i> Cập nhật link client</h4>
      <input id="link-delta-global" placeholder="Delta Global link">
      <input id="link-delta-vng" placeholder="Delta VNG link">
      <input id="link-codex-global" placeholder="Codex Global link">
      <input id="link-codex-vng" placeholder="Codex VNG link">
      <input id="link-ronix-global" placeholder="Ronix Global link">
      <input id="link-ronix-vng" placeholder="Ronix VNG link">
      <input id="link-krnl-global" placeholder="KRNL Global link">
      <input id="link-krnl-vng" placeholder="KRNL VNG link">
      <button onclick="updateLinks()">
        <i class="fas fa-save"></i> Lưu link
      </button>

      <h4><i class="fas fa-plus-circle"></i> Thêm script</h4>
      <input id="script-name" placeholder="Tên script">
      <input id="script-desc" placeholder="Mô tả script">
      <textarea id="script-code" rows="3" placeholder="Code script"></textarea>
      <button onclick="addScript()">
        <i class="fas fa-plus"></i> Thêm script
      </button>
    </div>
  </div>

  <script>
    const BIN_ID = "68cea7b443b1c97be9494d4d";
    const API_KEY = "$2a$10$4wv3SZr7FOegcPB2LBHuUObqAHVOVY0Xp/1HxhHP0BWfnXGvslZKa";
    const BASE_URL = `https://api.jsonbin.io/v3/b/${BIN_ID}`;
    let isAdmin = false;
    let currentDeleteIndex = null;

    // Hàm hiển thị thông báo toast
    function showToast(message, type = 'info') {
      const toast = document.getElementById('toast');
      
      // Thêm icon tương ứng với loại thông báo
      let icon = 'info-circle';
      if (type === 'success') icon = 'check-circle';
      if (type === 'error') icon = 'exclamation-circle';
      if (type === 'warning') icon = 'exclamation-triangle';
      
      toast.innerHTML = `<i class="fas fa-${icon}"></i> ${message}`;
      toast.className = 'toast ' + type;
      toast.classList.add('show');
      
      setTimeout(() => {
        toast.classList.remove('show');
      }, 3000);
    }
    
    function showConfirm(message, callback) {
      const dialog = document.getElementById('confirm-dialog');
      document.getElementById('confirm-message').innerHTML = `<i class="fas fa-exclamation-triangle"></i> ${message}`;
      dialog.style.display = 'flex';
      
      document.getElementById('confirm-yes').onclick = function() {
        dialog.style.display = 'none';
        callback(true);
      };
      
      document.getElementById('confirm-no').onclick = function() {
        dialog.style.display = 'none';
        callback(false);
      };
    }

    async function fetchData(){
      try {
        let res = await fetch(BASE_URL, { headers: { "X-Master-Key": API_KEY }});
        let data = await res.json();
        return data.record || {};
      } catch (e) {
        console.error("Error fetching data:", e);
        showToast("Lỗi khi tải dữ liệu", "error");
        return {};
      }
    }
    
    async function saveData(record){
      try {
        await fetch(BASE_URL, {
          method: "PUT",
          headers: {
            "Content-Type": "application/json",
            "X-Master-Key": API_KEY
          },
          body: JSON.stringify(record)
        });
        return true;
      } catch (e) {
        console.error("Error saving data:", e);
        showToast("Lỗi khi lưu dữ liệu", "error");
        return false;
      }
    }

    function openPopup(id){
      document.getElementById(id).style.display = "flex";
    }
    
    function closeOverlay(e, id){
      if(e.target.classList.contains('overlay')){
        document.getElementById(id).style.display = "none";
      }
    }

    function openAdmin(){
      let p = document.getElementById("admin-panel");
      p.style.display = p.style.display === "flex" ? "none" : "flex";
    }
    
    function checkPass(){
      if(document.getElementById("admin-pass").value === "1153021372365275216"){
        isAdmin = true;
        document.getElementById("admin-pass").style.display = "none";
        document.querySelector("#admin-panel button").style.display = "none";
        document.getElementById("admin-content").style.display = "block";
        loadData();
        showToast("Đăng nhập admin thành công", "success");
      } else {
        showToast("Mật khẩu không đúng", "error");
      }
    }

    // Hàm tải file executor
    function downloadFile(type) {
      const linkElement = document.getElementById(type);
      const fileUrl = linkElement.getAttribute('data-url');
      
      if (!fileUrl || fileUrl === "#") {
        showToast("Đang update", "error");
        return;
      }
      
      // Tạo một thẻ a ẩn để tải file
      const downloadLink = document.createElement('a');
      downloadLink.href = fileUrl;
      
      // Xác định tên file dựa trên loại executor
      let fileName = "";
      switch(type) {
        case 'delta-global': fileName = "Delta-Global.exe"; break;
        case 'delta-vng': fileName = "Delta-VNG.exe"; break;
        case 'codex-global': fileName = "Codex-Global.exe"; break;
        case 'codex-vng': fileName = "Codex-VNG.exe"; break;
        case 'ronix-global': fileName = "Ronix-Global.exe"; break;
        case 'ronix-vng': fileName = "Ronix-VNG.exe"; break;
        case 'krnl-global': fileName = "KRNL-Global.exe"; break;
        case 'krnl-vng': fileName = "KRNL-VNG.exe"; break;
        default: fileName = "executor.exe";
      }
      
      downloadLink.download = fileName;
      document.body.appendChild(downloadLink);
      downloadLink.click();
      document.body.removeChild(downloadLink);
      
      // Đóng popup sau khi nhấn
      closeOverlay({target: {classList: ['overlay']}}, getPopupId(type));
    }
    
    // Hàm lấy ID popup từ type
    function getPopupId(type) {
      if (type.includes('delta')) return 'delta-popup';
      if (type.includes('codex')) return 'codex-popup';
      if (type.includes('ronix')) return 'ronix-popup';
      if (type.includes('krnl')) return 'krnl-popup';
      return '';
    }

    async function updateLinks(){
      let r = await fetchData();
      r.links = {
        delta_global: document.getElementById("link-delta-global").value,
        delta_vng: document.getElementById("link-delta-vng").value,
        codex_global: document.getElementById("link-codex-global").value,
        codex_vng: document.getElementById("link-codex-vng").value,
        ronix_global: document.getElementById("link-ronix-global").value,
        ronix_vng: document.getElementById("link-ronix-vng").value,
        krnl_global: document.getElementById("link-krnl-global").value,
        krnl_vng: document.getElementById("link-krnl-vng").value,
      };
      const success = await saveData(r);
      if (success) {
        loadData();
        showToast("Đã cập nhật link thành công", "success");
      }
    }

    async function addScript(){
      let name = document.getElementById("script-name").value.trim();
      let desc = document.getElementById("script-desc").value.trim();
      let code = document.getElementById("script-code").value;
      if(!name || !code){
        showToast("Vui lòng nhập tên và code script", "warning");
        return;
      }
      
      let r = await fetchData();
      if(!r.scripts) r.scripts = [];
      r.scripts.push({name, desc, code});
      
      const success = await saveData(r);
      if (success) {
        loadData();
        showToast("Đã thêm script thành công", "success");
        document.getElementById("script-name").value = "";
        document.getElementById("script-desc").value = "";
        document.getElementById("script-code").value = "";
      }
    }

    async function deleteScript(index){
      showConfirm("Bạn có chắc muốn xóa script này?", async function(confirmed) {
        if (!confirmed) return;
        
        let r = await fetchData();
        if(r.scripts && r.scripts.length > index){
          r.scripts.splice(index, 1);
          const success = await saveData(r);
          if (success) {
            loadData();
            showToast("Đã xóa script thành công", "success");
          }
        }
      });
    }

    function escapeHtml(str) {
      return String(str || "").replace(/[&<>"']/g, function(m) {
        return {
          '&': '&amp;',
          '<': '&lt;',
          '>': '&gt;',
          '"': '&quot;',
          "'": '&#39;'
        }[m];
      });
    }

    function renderScripts(scripts){
      let list = document.getElementById("script-list");
      list.innerHTML = "";
      
      if (!scripts || scripts.length === 0) {
        list.innerHTML = '<div class="script-card"><div class="script-desc" style="text-align:center"><i class="fas fa-code"></i><br>Chưa có script nào. Đăng nhập admin để thêm script.</div></div>';
        return;
      }
      
      scripts.forEach((s, i) => {
        let card = document.createElement("div");
        card.className = "script-card";
        card.innerHTML = `
          <div class="script-title"><i class="fas fa-file-code"></i> ${escapeHtml(s.name)}</div>
          <div class="script-desc">${escapeHtml(s.desc || "Không có mô tả")}</div>
          <div class="btn-row">
            <button class="copy-btn"><i class="fas fa-copy"></i> Copy</button>
            ${isAdmin ? '<button class="delete-btn"><i class="fas fa-trash"></i> Xóa</button>' : ""}
          </div>`;
        
        let copyBtn = card.querySelector(".copy-btn");
        copyBtn.onclick = function(){
          navigator.clipboard.writeText(s.code || "").then(() => {
            showToast("Đã sao chép script", "success");
          }).catch(err => {
            console.error("Copy failed:", err);
            showToast("Lỗi khi sao chép", "error");
          });
        };
        
        if(isAdmin){
          let delBtn = card.querySelector(".delete-btn");
          delBtn.onclick = function(){ deleteScript(i) };
        }
        
        list.appendChild(card);
      });
    }

    async function loadData(){
      let r = await fetchData();
      if(r.links){
        // Cập nhật data-url thay vì href trực tiếp
        document.getElementById("delta-global").setAttribute('data-url', r.links.delta_global || "#");
        document.getElementById("delta-vng").setAttribute('data-url', r.links.delta_vng || "#");
        document.getElementById("codex-global").setAttribute('data-url', r.links.codex_global || "#");
        document.getElementById("codex-vng").setAttribute('data-url', r.links.codex_vng || "#");
        document.getElementById("ronix-global").setAttribute('data-url', r.links.ronix_global || "#");
        document.getElementById("ronix-vng").setAttribute('data-url', r.links.ronix_vng || "#");
        document.getElementById("krnl-global").setAttribute('data-url', r.links.krnl_global || "#");
        document.getElementById("krnl-vng").setAttribute('data-url', r.links.krnl_vng || "#");
        
        if(isAdmin){
          document.getElementById("link-delta-global").value = r.links.delta_global || "";
          document.getElementById("link-delta-vng").value = r.links.delta_vng || "";
          document.getElementById("link-codex-global").value = r.links.codex_global || "";
          document.getElementById("link-codex-vng").value = r.links.codex_vng || "";
          document.getElementById("link-ronix-global").value = r.links.ronix_global || "";
          document.getElementById("link-ronix-vng").value = r.links.ronix_vng || "";
          document.getElementById("link-krnl-global").value = r.links.krnl_global || "";
          document.getElementById("link-krnl-vng").value = r.links.krnl_vng || "";
        }
      }
      
      if(r.scripts){
        renderScripts(r.scripts);
      } else {
        renderScripts([]);
      }
    }
    
    // Initialize
    loadData();
    
    // Close admin panel when clicking outside
    document.addEventListener('click', function(event) {
      const adminPanel = document.getElementById('admin-panel');
      const adminBtn = document.querySelector('.admin-btn');
      
      if (adminPanel.style.display === 'flex' && 
          !adminPanel.contains(event.target) && 
          !adminBtn.contains(event.target)) {
        adminPanel.style.display = 'none';
      }
    });
  </script>
</body>
</html>
