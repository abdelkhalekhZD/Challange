<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AK - Kickboxing Story</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: #000;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
        }
        
        .video-container {
            width: 100%;
            max-width: 400px;
            aspect-ratio: 9/16;
            background: #000;
            position: relative;
            overflow: hidden;
        }
        
        /* Animated background */
        .bg-layer {
            position: absolute;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 30%, rgba(139,0,0,0.4) 0%, transparent 50%),
                radial-gradient(circle at 80% 70%, rgba(220,20,60,0.3) 0%, transparent 50%),
                linear-gradient(180deg, #000 0%, #1a0000 50%, #000 100%);
            animation: bgShift 8s ease-in-out infinite;
        }
        
        @keyframes bgShift {
            0%, 100% { transform: scale(1) rotate(0deg); opacity: 1; }
            50% { transform: scale(1.1) rotate(2deg); opacity: 0.9; }
        }
        
        /* Particles/dust effect */
        .particle {
            position: absolute;
            background: rgba(255,255,255,0.6);
            border-radius: 50%;
            animation: float-particle linear infinite;
        }
        
        .particle:nth-child(1) { width: 3px; height: 3px; left: 10%; animation-duration: 4s; animation-delay: 0s; }
        .particle:nth-child(2) { width: 2px; height: 2px; left: 25%; animation-duration: 5s; animation-delay: 0.5s; }
        .particle:nth-child(3) { width: 4px; height: 4px; left: 40%; animation-duration: 6s; animation-delay: 1s; }
        .particle:nth-child(4) { width: 2px; height: 2px; left: 60%; animation-duration: 5.5s; animation-delay: 1.5s; }
        .particle:nth-child(5) { width: 3px; height: 3px; left: 75%; animation-duration: 4.5s; animation-delay: 2s; }
        .particle:nth-child(6) { width: 2px; height: 2px; left: 90%; animation-duration: 5s; animation-delay: 2.5s; }
        
        @keyframes float-particle {
            0% { 
                transform: translateY(100vh) translateX(0);
                opacity: 0;
            }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { 
                transform: translateY(-20px) translateX(30px);
                opacity: 0;
            }
        }
        
        /* Impact flash effect */
        .flash {
            position: absolute;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(255,0,0,0.6) 0%, transparent 60%);
            opacity: 0;
            animation: impact 3s ease-in-out infinite;
        }
        
        @keyframes impact {
            0%, 90%, 100% { opacity: 0; transform: scale(0.8); }
            5% { opacity: 1; transform: scale(1.2); }
            10% { opacity: 0; transform: scale(1.5); }
        }
        
        /* Scan lines */
        .scanlines {
            position: absolute;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                0deg,
                transparent,
                transparent 2px,
                rgba(255,255,255,0.03) 2px,
                rgba(255,255,255,0.03) 4px
            );
            pointer-events: none;
            animation: scan 0.5s linear infinite;
        }
        
        @keyframes scan {
            0% { transform: translateY(0); }
            100% { transform: translateY(4px); }
        }
        
        /* Main content */
        .content {
            position: relative;
            z-index: 10;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: 50px 30px;
        }
        
        /* Top section - AK Logo */
        .logo-section {
            text-align: center;
            animation: slideDown 1s ease-out;
        }
        
        @keyframes slideDown {
            from { transform: translateY(-100px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        .ak-logo {
            font-size: 120px;
            font-weight: 900;
            color: #fff;
            font-family: 'Impact', sans-serif;
            letter-spacing: -5px;
            line-height: 1;
            text-shadow: 
                0 0 20px rgba(255,0,0,0.8),
                0 0 40px rgba(255,0,0,0.5),
                5px 5px 0 rgba(0,0,0,0.8);
            animation: pulse-logo 2s ease-in-out infinite;
            position: relative;
        }
        
        .ak-logo::before {
            content: 'AK';
            position: absolute;
            left: 0;
            top: 0;
            color: #ff0000;
            z-index: -1;
            animation: glitch 3s infinite;
        }
        
        @keyframes glitch {
            0%, 90%, 100% { transform: translate(0); opacity: 0; }
            92% { transform: translate(-3px, 2px); opacity: 0.8; }
            94% { transform: translate(2px, -2px); opacity: 0.8; }
            96% { transform: translate(-2px, 2px); opacity: 0.8; }
        }
        
        @keyframes pulse-logo {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        
        .tagline {
            font-size: 18px;
            color: #ff3333;
            font-weight: 700;
            letter-spacing: 8px;
            margin-top: 10px;
            text-transform: uppercase;
            animation: fadeIn 2s ease-out;
        }
        
        /* Center - Animated gloves */
        .center-section {
            display: flex;
            justify-content: center;
            align-items: center;
            flex: 1;
        }
        
        .gloves-container {
            position: relative;
            width: 200px;
            height: 200px;
        }
        
        .glove {
            font-size: 100px;
            position: absolute;
            filter: drop-shadow(0 0 20px rgba(255,0,0,0.8));
        }
        
        .glove-left {
            left: -20px;
            top: 50%;
            transform: translateY(-50%) rotate(-15deg);
            animation: punch-left 2s ease-in-out infinite;
        }
        
        .glove-right {
            right: -20px;
            top: 50%;
            transform: translateY(-50%) rotate(15deg) scaleX(-1);
            animation: punch-right 2s ease-in-out infinite;
            animation-delay: 1s;
        }
        
        @keyframes punch-left {
            0%, 100% { transform: translateY(-50%) translateX(0) rotate(-15deg); opacity: 1; }
            30% { transform: translateY(-50%) translateX(60px) rotate(0deg) scale(1.3); opacity: 0.7; }
            35% { opacity: 0; }
            40%, 100% { transform: translateY(-50%) translateX(0) rotate(-15deg); opacity: 1; }
        }
        
        @keyframes punch-right {
            0%, 100% { transform: translateY(-50%) translateX(0) rotate(15deg) scaleX(-1); opacity: 1; }
            30% { transform: translateY(-50%) translateX(-60px) rotate(0deg) scaleX(-1.3); opacity: 0.7; }
            35% { opacity: 0; }
            40%, 100% { transform: translateY(-50%) translateX(0) rotate(15deg) scaleX(-1); opacity: 1; }
        }
        
        /* Bottom section */
        .bottom-section {
            animation: slideUp 1s ease-out;
        }
        
        @keyframes slideUp {
            from { transform: translateY(100px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        .quotes-section {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-bottom: 25px;
        }
        
        .quote-box {
            background: rgba(255,0,0,0.1);
            border-left: 4px solid #ff0000;
            padding: 15px 20px;
            text-align: left;
            backdrop-filter: blur(5px);
            animation: fadeInStat 1s ease-out backwards;
        }
        
        .quote-box:nth-child(1) { animation-delay: 0.2s; }
        .quote-box:nth-child(2) { animation-delay: 0.4s; }
        .quote-box:nth-child(3) { animation-delay: 0.6s; }
        
        .quote-text {
            font-size: 18px;
            font-weight: 900;
            color: #fff;
            letter-spacing: 2px;
            font-family: 'Impact', sans-serif;
        }
        
        .motto {
            text-align: center;
            font-size: 22px;
            font-weight: 900;
            color: #fff;
            text-transform: uppercase;
            letter-spacing: 3px;
            padding: 18px;
            background: linear-gradient(90deg, transparent, rgba(255,0,0,0.3), transparent);
            border-top: 2px solid #ff0000;
            border-bottom: 2px solid #ff0000;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.8);
            animation: slideText 2s ease-in-out infinite;
        }
        
        @keyframes fadeInStat {
            from { opacity: 0; transform: translateX(-30px); }
            to { opacity: 1; transform: translateX(0); }
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>
    <div class="video-container">
        <div class="bg-layer"></div>
        
        <div class="particle"></div>
        <div class="particle"></div>
        <div class="particle"></div>
        <div class="particle"></div>
        <div class="particle"></div>
        <div class="particle"></div>
        
        <div class="flash"></div>
        <div class="scanlines"></div>
        
        <div class="content">
            <div class="logo-section">
                <div class="ak-logo">AK</div>
                <div class="tagline">ALWAYS KNOCKING</div>
            </div>
            
            <div class="center-section">
                <div class="gloves-container">
                    <div class="glove glove-left">🥊</div>
                    <div class="glove glove-right">🥊</div>
                </div>
            </div>
            
            <div class="bottom-section">
                <div class="quotes-section">
                    <div class="quote-box">
                        <span class="quote-text">"TRAIN HARD"</span>
                    </div>
                    <div class="quote-box">
                        <span class="quote-text">"FIGHT SMART"</span>
                    </div>
                    <div class="quote-box">
                        <span class="quote-text">"NEVER QUIT"</span>
                    </div>
                </div>
                
                <div class="motto">GRIND IN SILENCE</div>
                
                <div class="social-section">
                    <a href="https://www.instagram.com/a.khalek_dev" target="_blank" class="social-btn instagram">
                        <span class="icon">📱</span>
                        <span class="text">Instagram</span>
                    </a>
                    <a href="https://wa.me/212718699021" target="_blank" class="social-btn whatsapp">
                        <span class="icon">💬</span>
                        <span class="text">WhatsApp</span>
                    </a>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
