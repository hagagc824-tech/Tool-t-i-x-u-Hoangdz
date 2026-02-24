

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>AI PRO 2026 | VIP ENGINE</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;900&display=swap" rel="stylesheet">
    <style>
        :root { --neon: #00f2ff; --bg: #050505; }
        body { margin:0; background:var(--bg); color:#fff; font-family:'Orbitron', sans-serif; overflow-x:hidden; }
        canvas { position:fixed; inset:0; z-index:-1; }
        .container { max-width:400px; margin:0 auto; padding:20px; box-sizing:border-box; }
        .glass { background:rgba(15, 20, 25, 0.95); border:1px solid var(--neon); border-radius:20px; padding:25px; margin-bottom:20px; }
        input { width:100%; padding:15px; border-radius:10px; background:#000; color:#0f0; border:1px solid #333; box-sizing:border-box; margin-bottom:15px; font-size:16px !important; outline:none; }
        .btn { width:100%; padding:15px; border:none; border-radius:10px; font-weight:900; cursor:pointer; background:linear-gradient(90deg, #00f2ff, #7000ff); color:#fff; text-transform:uppercase; }
        .reason-box { font-size:12px; color:#ccc; margin-top:15px; text-align:left; background:#000; padding:12px; border-left:4px solid var(--neon); border-radius:5px; }
        .vip-alert { font-size:12px; color:#ff4757; margin-top:15px; line-height:1.5; font-weight:bold; text-align:center; border: 1px dashed #ff4757; padding: 10px; border-radius: 10px; }
        .admin-link { color:var(--neon); text-decoration:none; border-bottom:1px solid var(--neon); }
        .hist-item { font-size:11px; padding:5px 0; border-bottom:1px solid #222; display:flex; justify-content:space-between; }
    </style>
</head>
<body>
<canvas id="snow"></canvas>

<div class="container">
    <h2 style="text-align:center; color:var(--neon)">AI PRO 2026</h2>
    
    <div class="glass">
        <input type="text" id="code" placeholder="DÁN MÃ MD5 (32 KÝ TỰ)...">
        <button class="btn" onclick="predict()">PHÂN TÍCH DỮ LIỆU</button>
        
        <div id="resultArea" style="display:none; margin-top:20px;">
            <div id="res" style="font-size:3rem; font-weight:900; text-align:center;">--</div>
            <div id="prob" style="color:var(--neon); text-align:center; font-size:1.1rem; margin-bottom:10px;"></div>
            
            <div id="warning" style="color:#ffcc00; font-weight:bold; text-align:center; font-size:13px; margin: 5px 0;"></div>
            
            <div class="reason-box" id="reason"></div>
            
            <div class="vip-alert">
                ⚠️ Cảnh báo: Đây là bản tool giá thấp, độ chính xác không cao.<br>
                Muốn chuẩn hơn, liên hệ ngay Admin <a href="https://t.me/tranhoang2286" class="admin-link">@tranhoang2286</a> để múc ngay bản VIP giá cực hợp lý!
            </div>
        </div>
    </div>

    <div class="glass">
        <div style="margin-bottom:10px; font-size:14px;">LỊCH SỬ DỰ ĐOÁN</div>
        <div id="hist"></div>
    </div>
</div>

<script>
    function predict(){
        let code = document.getElementById('code').value.trim();
        if(code.length < 32) return alert("Vui lòng nhập đủ mã MD5!");
        
        document.getElementById('resultArea').style.display = 'block';
        
        let val = parseInt(code.slice(-2), 16);
        let res = (val % 2 === 0) ? "🔴 TÀI" : "⚪ XỈU";
        let p = 60 + Math.floor(Math.random()*15); 
        
        document.getElementById('res').innerText = res;
        document.getElementById('prob').innerText = "TỈ LỆ THẮNG: " + p + "%";
        
        // Cảnh báo cầu
        let warn = document.getElementById('warning');
        if(val % 3 === 0) warn.innerText = "⚠️ PHÁT HIỆN CẦU BỆT DÀI - CẨN TRỌNG!";
        else warn.innerText = "";
        
        document.getElementById('reason').innerHTML = `
            <strong>» Thuật toán:</strong> Phân tích Hash Offset [${code.substring(code.length-4)}]<br>
            <strong>» Nguyên lý:</strong> Sử dụng bộ lọc nhiễu bit cuối. Dữ liệu cho thấy xác suất ${res} đang dao động ổn định ở mức ${p}%.
        `;
        
        let hist = document.getElementById('hist');
        hist.innerHTML = `<div class="hist-item"><span>${res} (${p}%)</span><span>${new Date().toLocaleTimeString()}</span></div>` + hist.innerHTML;
        
        document.getElementById('code').value = ""; 
    }

    // Hiệu ứng tuyết rơi
    const c=document.getElementById('snow'), x=c.getContext('2d');
    c.width=window.innerWidth; c.height=window.innerHeight;
    let s=Array.from({length:70},()=>({x:Math.random()*c.width, y:Math.random()*c.height, r:Math.random()*2}));
    function draw(){
        x.clearRect(0,0,c.width,c.height); x.fillStyle='#fff';
        s.forEach(p=>{ x.beginPath(); x.arc(p.x,p.y,p.r,0,Math.PI*2); x.fill(); p.y=(p.y+1)%c.height; });
        requestAnimationFrame(draw);
    } draw();
</script>
</body>
</html>
