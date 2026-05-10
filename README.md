<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wadoud Hub | إبداع يتخطى الحدود</title>
    <style>
        :root { --primary: linear-gradient(135deg, #4facfe 0%, #a944ff 100%); --bg: #0b0f19; --card: #161b2a; --text: #ffffff; --accent: #4facfe; }
        body { font-family: sans-serif; background: var(--bg); color: var(--text); margin: 0; text-align: center; }
        header { display: flex; align-items: center; justify-content: center; gap: 15px; padding: 20px; background: rgba(0,0,0,0.3); border-bottom: 1px solid #333; position: sticky; top: 0; z-index: 100; backdrop-filter: blur(10px); }
        header img { height: 50px; }
        header h1 { font-size: 1.6rem; font-weight: bold; color: var(--accent); margin: 0; cursor: pointer; }
        .page { display: none; padding: 40px 15px; max-width: 1000px; margin: 0 auto; }
        .page.active { display: block; animation: fadeIn 0.5s ease; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(15px); } to { opacity: 1; transform: translateY(0); } }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; padding: 10px; }
        .card { background: var(--card); padding: 30px; border-radius: 20px; border: 1px solid #333; cursor: pointer; transition: 0.3s; }
        .card:hover { border-color: #a944ff; transform: translateY(-5px); }
        .btn-back { display: inline-block; margin-bottom: 20px; color: var(--accent); cursor: pointer; font-weight: bold; }
        .form-container { max-width: 500px; margin: 0 auto; background: var(--card); padding: 30px; border-radius: 20px; border: 1px solid #444; text-align: right; }
        input, textarea { width: 100%; padding: 12px; margin: 10px 0; border-radius: 10px; border: 1px solid #333; background: #0b0f19; color: white; box-sizing: border-box; }
        .btn-send { width: 100%; padding: 15px; border-radius: 10px; border: none; background: var(--primary); color: white; font-weight: bold; cursor: pointer; margin-top: 10px; }
        footer { padding: 40px; font-size: 0.8rem; color: #444; border-top: 1px solid #333; margin-top: 50px; }
    </style>
</head>
<body>
    <!-- رأس الصفحة مع الشعار -->
    <header>
        <img src="logo.png" alt="<img width="464" height="464" alt="1778390838425(1)" src="https://github.com/user-attachments/assets/441254e9-d2f7-40b4-ae91-fa10da39eecd" />
">
        <h1 onclick="showPage('home')">Wadoud Hub</h1>
    </header>

    <div id="home" class="page active">
        <h1>إبداع يتخطى الحدود</h1>
        <p style="color:#94a3b8">مركزك الشامل للتصميم والطباعة بالجزائر</p>
        <div class="grid">
            <div class="card" onclick="showPage('presentations')"><h3>العروض التقديمية</h3><p>تصاميم احترافية مخصصة</p></div>
            <div class="card" onclick="showPage('pod')"><h3>الطباعة عند الطلب</h3><p>تيشيرتات بتصاميم حصرية</p></div>
            <div class="card" onclick="showPage('ads')"><h3>الخدمات الإعلانية</h3><p>صناعة ونشر المحتوى</p></div>
        </div>
    </div>

    <!-- باقي الصفحات كما هي -->
    <div id="presentations" class="page">
        <div class="btn-back" onclick="showPage('home')">← العودة</div>
        <h2>قسم العروض التقديمية</h2>
        <div class="grid">
            <div class="card" onclick="openOrder('تصميم عرض تقديمي خاص')"><h3>طلب تصميم خاص</h3><p>اضغط لبدء الطلب</p></div>
        </div>
    </div>
    <div id="pod" class="page">
        <div class="btn-back" onclick="showPage('home')">← العودة</div>
        <h2>قسم الطباعة</h2>
        <div class="grid">
            <div class="card" onclick="openOrder('طلب تيشيرت مخصص')"><h3>صمم تيشيرتك الخاص</h3><p>اضغط لبدء الطلب</p></div>
        </div>
    </div>
    <div id="ads" class="page">
        <div class="btn-back" onclick="showPage('home')">← العودة</div>
        <h2>الخدمات الإعلانية</h2>
        <div class="grid">
            <div class="card" onclick="openOrder('تصميم إعلان')"><h3>طلب تصميم إعلان</h3><p>اضغط لبدء الطلب</p></div>
        </div>
    </div>
    <div id="order-page" class="page">
        <div class="btn-back" onclick="showPage('home')">← إلغاء</div>
        <div class="form-container">
            <label>الاسم الكامل</label><input type="text" id="user-name" placeholder="اسمك الكريم">
            <label>الخدمة</label><input type="text" id="service-name" readonly style="color:#4facfe">
            <label>التفاصيل</label><textarea id="order-details" rows="4" placeholder="اشرح لنا فكرتك..."></textarea>
            <button class="btn-send" onclick="sendToWhatsApp()">إرسال عبر واتساب</button>
        </div>
    </div>
    <footer>© 2026 Wadoud Hub - جميع الحقوق محفوظة</footer>
    <script>
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            document.getElementById(pageId).classList.add('active');
            window.scrollTo(0,0);
        }
        function openOrder(service) {
            document.getElementById('service-name').value = service;
            showPage('order-page');
        }
        function sendToWhatsApp() {
            const name = document.getElementById('user-name').value;
            const service = document.getElementById('service-name').value;
            const details = document.getElementById('order-details').value;
            if(!name) { alert("اكتب اسمك"); return; }
            const myNumber = "231794839615"; 
            const message = `مرحباً Wadoud Hub،
الاسم: ${name}
الخدمة: ${service}
التفاصيل: ${details}`;
            window.open(`https://wa.me/${myNumber}?text=${encodeURIComponent(message)}`);
        }
    </script>
</body>
</html>
