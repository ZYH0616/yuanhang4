<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>远航 Overseas - 出海即增长，全球新蓝海</title>
    <!-- 引入 Font Awesome 6 免费版 -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com">
    <style>
        :root {
            --primary-deep: #1e3c72;
            --primary-bright: #2563eb;
            --cta-gradient: linear-gradient(135deg, #4f8bf5, #6ba0ff);
            --bg-light: #f9fafb;
            --text-main: #1f2937;
            --text-muted: #6b7280;
            --white: #ffffff;
            --radius-lg: 24px;
            --radius-md: 16px;
            --glass: rgba(255, 255, 255, 0.75);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, "SF Pro Text", sans-serif;
        }

        body {
            background-color: var(--bg-light);
            color: var(--text-main);
            overflow-x: hidden;
            line-height: 1.5;
        }

        /* 顶部提示条 */
        .demo-notice {
            background: #e5e7eb;
            text-align: center;
            padding: 8px;
            font-size: 13px;
            color: var(--primary-deep);
            position: relative;
            z-index: 1001;
        }

        /* 导航栏 - 毛玻璃效果 */
        nav {
            position: fixed;
            top: 35px; /* 避开提示条 */
            left: 0;
            width: 100%;
            height: 70px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 8%;
            background: var(--glass);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            z-index: 1000;
            border-bottom: 1px solid rgba(255, 255, 255, 0.3);
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 22px;
            font-weight: 800;
            color: var(--primary-deep);
            cursor: pointer;
        }

        .nav-links {
            display: flex;
            align-items: center;
            gap: 32px;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-main);
            font-size: 15px;
            font-weight: 500;
            padding: 8px 0;
            position: relative;
            transition: 0.3s;
        }

        .nav-links a:hover { color: var(--primary-bright); }
        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary-bright);
            transition: width 0.3s;
        }
        .nav-links a:hover::after { width: 100%; }

        .btn-login {
            background: linear-gradient(135deg, var(--primary-bright), #60a5fa);
            color: white;
            padding: 10px 24px;
            border-radius: 50px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(37, 99, 235, 0.2);
            transition: 0.3s;
        }

        .btn-login:hover { transform: translateY(-2px); filter: brightness(1.1); }

        /* 英雄区 */
        .hero {
            padding: 180px 8% 80px;
            display: grid;
            grid-template-columns: 1.2fr 0.8fr;
            align-items: center;
            background: radial-gradient(circle at 80% 20%, rgba(37, 99, 235, 0.08), transparent 40%);
            min-height: 90vh;
        }

        .hero-text h1 {
            font-size: 56px;
            letter-spacing: -1px;
            margin-bottom: 24px;
            background: linear-gradient(to right, #1e3c72, #2563eb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-text p {
            font-size: 18px;
            color: var(--text-muted);
            max-width: 500px;
            margin-bottom: 40px;
        }

        /* 垂直堆叠卡片 */
        .hero-stats {
            position: relative;
            display: flex;
            flex-direction: column;
            gap: 20px;
            align-items: flex-end;
        }

        .earth-bg {
            position: absolute;
            font-size: 400px;
            color: rgba(37, 99, 235, 0.04);
            right: -50px;
            top: 50%;
            transform: translateY(-50%);
            z-index: -1;
        }

        .stat-card {
            background: var(--white);
            padding: 24px 40px;
            border-radius: var(--radius-md);
            box-shadow: 0 10px 25px rgba(0,0,0,0.03);
            border: 1px solid rgba(0,0,0,0.05);
            width: 260px;
            transition: 0.3s;
            cursor: pointer;
        }
        .stat-card:hover { transform: translateX(-10px); box-shadow: 0 15px 30px rgba(0,0,0,0.08); }
        .stat-card h3 { color: var(--primary-bright); font-size: 28px; margin-bottom: 4px; }
        .stat-card p { color: var(--text-muted); font-size: 14px; }

        /* 政策快讯轮播 */
        .ticker-wrap {
            margin: 0 8% 80px;
            background: #f3f4f6;
            padding: 15px 30px;
            border-radius: 50px;
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .ticker-content {
            flex: 1;
            display: flex;
            justify-content: space-between;
        }

        .news-item {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 14px;
            cursor: pointer;
            padding: 5px 15px;
            border-right: 1px solid #e5e7eb;
        }
        .news-item:last-child { border-right: none; }
        .news-item i { color: var(--primary-bright); }
        .badge-new {
            background: #fee2e2;
            color: #ef4444;
            font-size: 10px;
            padding: 2px 6px;
            border-radius: 4px;
            font-weight: bold;
        }

        .arrow-btn {
            background: none;
            border: none;
            color: var(--text-muted);
            cursor: pointer;
            padding: 5px;
            transition: 0.2s;
        }
        .arrow-btn:hover { color: var(--primary-bright); }

        /* 服务区域 */
        .section-header {
            text-align: center;
            margin-bottom: 50px;
        }
        .section-header h2 {
            font-size: 32px;
            color: var(--primary-deep);
            position: relative;
            display: inline-block;
            padding-bottom: 10px;
        }
        .section-header h2::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 20%;
            width: 60%;
            height: 4px;
            background: var(--primary-bright);
            border-radius: 2px;
        }

        .services-grid {
            padding: 0 8% 100px;
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 30px;
        }

        .service-card {
            background: var(--white);
            padding: 40px;
            border-radius: var(--radius-lg);
            transition: all 0.4s ease;
            cursor: pointer;
            border: 1px solid transparent;
        }

        .service-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.1);
            border-color: rgba(37, 99, 235, 0.1);
        }

        .icon-box {
            width: 60px;
            height: 60px;
            background: #eff6ff;
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 25px;
            font-size: 24px;
            color: var(--primary-bright);
        }

        .service-card h4 { font-size: 20px; margin-bottom: 15px; }
        .service-card p { color: var(--text-muted); font-size: 15px; margin-bottom: 25px; }
        .learn-more {
            color: var(--primary-bright);
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        /* CTA 区域 - 浅蓝色调 */
        .cta-container {
            margin: 0 8% 100px;
            background: var(--cta-gradient);
            padding: 80px 40px;
            border-radius: 32px;
            text-align: center;
            color: white;
            box-shadow: 0 20px 40px rgba(79, 139, 245, 0.3);
        }

        .cta-container h2 { font-size: 38px; margin-bottom: 12px; }
        .cta-container p { font-size: 18px; margin-bottom: 40px; opacity: 0.9; }

        .ai-box {
            max-width: 700px;
            margin: 0 auto;
            position: relative;
        }

        .ai-input {
            width: 100%;
            padding: 24px 80px 24px 35px;
            border-radius: 100px;
            border: 2px solid rgba(255,255,255,0.3);
            background: rgba(255,255,255,0.2);
            backdrop-filter: blur(10px);
            color: white;
            font-size: 16px;
            outline: none;
            transition: 0.3s;
        }
        .ai-input::placeholder { color: rgba(255,255,255,0.7); }
        .ai-input:focus {
            background: rgba(255,255,255,0.3);
            border-color: white;
        }

        .send-btn {
            position: absolute;
            right: 12px;
            top: 50%;
            transform: translateY(-50%);
            width: 52px;
            height: 52px;
            background: white;
            color: var(--primary-bright);
            border: none;
            border-radius: 50%;
            cursor: pointer;
            transition: 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
        }
        .send-btn:hover { transform: translateY(-50%) scale(1.15); box-shadow: 0 5px 15px rgba(0,0,0,0.1); }

        /* 页脚 */
        footer {
            padding: 60px 8%;
            border-top: 1px solid #e5e7eb;
            display: flex;
            justify-content: space-between;
            color: var(--text-muted);
            font-size: 14px;
        }
        .footer-nav { display: flex; gap: 30px; }
        .footer-nav span { cursor: pointer; transition: 0.2s; }
        .footer-nav span:hover { color: var(--primary-bright); }

        /* 响应式调整 */
        @media (max-width: 800px) {
            nav { padding: 0 5%; }
            .nav-links { display: none; }
            .hero { grid-template-columns: 1fr; text-align: center; padding-top: 140px; }
            .hero-text h1 { font-size: 38px; }
            .hero-stats { align-items: center; margin-top: 50px; }
            .ticker-wrap { flex-direction: column; border-radius: 20px; }
            .ticker-content { flex-direction: column; gap: 15px; width: 100%; }
            .news-item { border-right: none; border-bottom: 1px solid #ddd; padding: 10px 0; }
            .services-grid { grid-template-columns: 1fr; }
            .cta-container h2 { font-size: 28px; }
        }
    </style>
</head>
<body>

    <div class="demo-notice">
        <i class="fa-solid fa-wand-magic-sparkles"></i> 高保真原型 · 点击任何元素体验演示交互
    </div>

    <!-- 导航栏 -->
    <nav>
        <div class="logo" onclick="tap('品牌首页')">
            <i class="fa-solid fa-ship"></i>
            <span>远航 · Overseas</span>
        </div>
        <div class="nav-links">
            <a href="#" onclick="tap('消息中心')">消息</a>
            <a href="#" onclick="tap('行业报告')">报告</a>
            <a href="#" onclick="tap('全球快讯')">快讯</a>
            <a href="#" onclick="tap('出海指南')">指南</a>
            <button class="btn-login" onclick="tap('一键登录系统')">一键登录</button>
        </div>
    </nav>

    <!-- 英雄区 -->
    <header class="hero">
        <div class="hero-text">
            <h1>出海即增长<br>全球新蓝海</h1>
            <p>一站式海外市场拓展方案，从合规、支付到本地营销，我们陪您稳健落地，抢占全球增长先机。</p>
            <button class="btn-login" style="padding: 15px 40px; font-size: 16px;" onclick="tap('开始免费咨询')">开始远航</button>
        </div>
        
        <div class="hero-stats">
            <i class="fa-solid fa-earth-asia earth-bg"></i>
            <div class="stat-card" onclick="tap('海外案例看板')">
                <h3>200+</h3>
                <p>海外成功落地案例</p>
            </div>
            <div class="stat-card" onclick="tap('全球服务网络')">
                <h3>50+ 个</h3>
                <p>重点业务覆盖国家</p>
            </div>
            <div class="stat-card" onclick="tap('GMV 统计详情')">
                <h3>$5B+</h3>
                <p>助力年度总 GMV</p>
            </div>
        </div>
    </header>

    <!-- 政策快讯轮播栏 -->
    <section class="ticker-wrap">
        <button class="arrow-btn" onclick="tap('切换上一条快讯')"><i class="fa-solid fa-chevron-left"></i></button>
        <div class="ticker-content">
            <div class="news-item" onclick="tap('越南合规法案详情')">
                <i class="fa-solid fa-bullhorn"></i>
                <span>越南新数据合规法正式生效</span>
                <span class="badge-new">NEW</span>
            </div>
            <div class="news-item" onclick="tap('泰国税收政策详情')">
                <i class="fa-solid fa-chart-line"></i>
                <span>泰国税收优惠政策更新</span>
                <span class="badge-new">NEW</span>
            </div>
            <div class="news-item" onclick="tap('欧盟碳关税详情')">
                <i class="fa-solid fa-leaf"></i>
                <span>欧盟碳关税(CBAM)指南发布</span>
                <span class="badge-new">NEW</span>
            </div>
        </div>
        <button class="arrow-btn" onclick="tap('切换下一条快讯')"><i class="fa-solid fa-chevron-right"></i></button>
    </section>

    <!-- 核心服务功能区 -->
    <div class="section-header">
        <h2>核心服务功能</h2>
    </div>

    <section class="services-grid">
        <!-- 卡片 1 -->
        <a href="0.1.html" style="text-decoration: none; color: inherit;">
          <div class="service-card" data-service="商务翻译">
        <i class="fas fa-language service-icon"></i>
        <h3>商务翻译</h3>
        <p>文本/语音翻译，支持阿语/俄语/泰语方言，超拟人语音合成</p>
        <span class="card-tag">了解更多 <i class="fas fa-arrow-right"></i></span>
        </div>
        </a>
        <!-- 卡片 2 -->
        <a href="0.2.html" style="text-decoration: none; color: inherit;">
          <div class="service-card" data-service="AI营销">
        <i class="fas fa-robot service-icon"></i>
        <h3>AI营销</h3>
        <p>超拟人语音、文案生成、视频脚本、文化适配</p>
        <span class="card-tag">了解更多 <i class="fas fa-arrow-right"></i></span>
        </div>
         </a>
        <!-- 卡片 3 -->
        <a href="0.3.html" style="text-decoration: none; color: inherit;">
    <div class="service-card" data-service="合规风控">
        <i class="fas fa-gavel service-icon"></i>
        <h3>合规风控</h3>
        <p>合同审查、法律库、风险预警、政策更新</p>
        <span class="card-tag">了解更多 <i class="fas fa-arrow-right"></i></span>
    </div>
</a>
    </section>

    <!-- CTA 区域 -->
    <section class="cta-container">
        <h2>准备远航？</h2>
        <p>立即获取您想要的全球化拓展信息</p>
        <div class="ai-box">
            <input type="text" class="ai-input" placeholder="请输入您的问题，例如：如何快速在德国注册商标？">
            <button class="send-btn" onclick="tap('AI 咨询提交')">
                <i class="fa-solid fa-arrow-up"></i>
            </button>
        </div>
    </section>

    <!-- 页脚 -->
    <footer>
        <div>© 2024 远航 Overseas. 出海即增长，全球新蓝海。</div>
        <div class="footer-nav">
            <span onclick="tap('查看隐私政策')">隐私政策</span>
            <span onclick="tap('查看法律条款')">法律条款</span>
            <span onclick="tap('联系我们')">联系我们</span>
        </div>
    </footer>

    <script>
        // 通用点击交互反馈
        function tap(name) {
            alert("【交互演示】\n您点击了：" + name + "\n(该功能仅作为原型展示，真实环境将跳转至相应模块)");
        }

        // 处理输入框的回车事件
        document.querySelector('.ai-input').addEventListener('keypress', function (e) {
            if (e.key === 'Enter') {
                tap('AI 咨询提交: ' + this.value);
            }
        });
    </script>
</body>
</html>
