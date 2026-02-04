# super-duper-spoon
This is a game called LOCK IN created by a 11 year old girl
[LOCK IN.html](https://github.com/user-attachments/files/25064104/LOCK.IN.html)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LOCK IN - Ultimate Battle Arena</title>
    <script src="https://accounts.google.com/gsi/client" async defer></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Impact', 'Arial Black', sans-serif;
            background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
            background-attachment: fixed;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            padding: 20px 0;
            color: white;
            overflow-y: auto;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                radial-gradient(circle at 20% 30%, rgba(121, 40, 202, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 70%, rgba(255, 0, 128, 0.1) 0%, transparent 50%);
            pointer-events: none;
            animation: pulseBackground 10s ease-in-out infinite;
        }

        @keyframes pulseBackground {
            0%, 100% { opacity: 0.5; }
            50% { opacity: 1; }
        }

        .game-wrapper {
            text-align: center;
            max-width: 1600px;
            width: 100%;
            margin: 20px auto;
            position: relative;
            z-index: 1;
        }

        .title {
            font-size: 6em;
            margin-bottom: 5px;
            text-shadow: 
                6px 6px 0px rgba(255, 0, 0, 0.5),
                -6px -6px 0px rgba(0, 255, 255, 0.5),
                0 0 40px rgba(121, 40, 202, 0.8);
            letter-spacing: 20px;
            animation: glitch 3s infinite, titleGlow 2s ease-in-out infinite;
            color: #fff;
        }

        @keyframes titleGlow {
            0%, 100% { filter: drop-shadow(0 0 20px rgba(121, 40, 202, 0.8)); }
            50% { filter: drop-shadow(0 0 40px rgba(255, 0, 128, 1)); }
        }

        @keyframes glitch {
            0%, 100% { text-shadow: 6px 6px 0px rgba(255, 0, 0, 0.5), -6px -6px 0px rgba(0, 255, 255, 0.5); }
            25% { text-shadow: -6px 6px 0px rgba(255, 0, 0, 0.5), 6px -6px 0px rgba(0, 255, 255, 0.5); }
            50% { text-shadow: 6px -6px 0px rgba(255, 0, 0, 0.5), -6px 6px 0px rgba(0, 255, 255, 0.5); }
            75% { text-shadow: -6px -6px 0px rgba(255, 0, 0, 0.5), 6px 6px 0px rgba(0, 255, 255, 0.5); }
        }

        .subtitle {
            font-size: 1.8em;
            letter-spacing: 10px;
            margin-bottom: 40px;
            opacity: 0.9;
            text-shadow: 0 0 20px rgba(255, 255, 255, 0.5);
            animation: subtitleFloat 3s ease-in-out infinite;
        }

        @keyframes subtitleFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        @keyframes badgePulse {
            0%, 100% { transform: scale(1); box-shadow: 0 0 20px rgba(255, 0, 128, 0.5); }
            50% { transform: scale(1.05); box-shadow: 0 0 30px rgba(255, 0, 128, 0.8); }
        }

        .screen {
            background: linear-gradient(135deg, rgba(0, 0, 0, 0.95) 0%, rgba(30, 20, 60, 0.95) 100%);
            padding: 60px;
            border-radius: 30px;
            border: 6px solid transparent;
            background-clip: padding-box;
            position: relative;
            max-width: 1000px;
            margin: 0 auto;
            box-shadow: 
                0 0 80px rgba(121, 40, 202, 0.6),
                inset 0 0 60px rgba(121, 40, 202, 0.1);
            display: none;
        }

        .screen::before {
            content: '';
            position: absolute;
            top: -6px;
            left: -6px;
            right: -6px;
            bottom: -6px;
            background: linear-gradient(45deg, #ff0080, #7928ca, #00ffff, #ff0080);
            border-radius: 30px;
            z-index: -1;
            animation: borderRotate 4s linear infinite;
            background-size: 400% 400%;
        }

        @keyframes borderRotate {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .screen.active {
            display: block;
            animation: screenFadeIn 0.5s ease-out;
        }

        @keyframes screenFadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        .screen h2 {
            font-size: 3.5em;
            margin-bottom: 50px;
            background: linear-gradient(90deg, #ff0080, #7928ca, #00ffff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            filter: drop-shadow(0 0 30px rgba(121, 40, 202, 0.8));
        }

        .menu-buttons {
            display: flex;
            flex-direction: column;
            gap: 30px;
            max-width: 700px;
            margin: 0 auto;
        }

        .menu-btn {
            padding: 35px 60px;
            background: linear-gradient(135deg, #7928ca, #ff0080);
            border: 5px solid transparent;
            border-radius: 25px;
            color: white;
            font-weight: bold;
            font-size: 2.2em;
            cursor: pointer;
            transition: all 0.4s ease;
            letter-spacing: 4px;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(121, 40, 202, 0.4);
        }

        .menu-btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.3);
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .menu-btn:hover::before {
            width: 400px;
            height: 400px;
        }

        .menu-btn:hover {
            transform: translateY(-5px) scale(1.05);
            border-color: #00ffff;
            box-shadow: 
                0 15px 60px rgba(0, 255, 255, 0.6),
                0 0 40px rgba(255, 0, 128, 0.4);
        }

        .player-count-btn {
            padding: 50px;
            background: linear-gradient(135deg, #00ffff, #7928ca, #ff0080);
            font-size: 3.5em;
            background-size: 200% 200%;
            animation: gradientShift 3s ease infinite;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .character-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 25px;
            margin: 50px 0;
        }

        .character-card {
            background: linear-gradient(135deg, rgba(121, 40, 202, 0.4), rgba(255, 0, 128, 0.4));
            padding: 35px;
            border: 5px solid transparent;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.4s ease;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        .character-card:hover {
            transform: translateY(-15px);
            border-color: #00ffff;
            box-shadow: 0 20px 60px rgba(0, 255, 255, 0.4);
        }

        .character-card h3 {
            font-size: 2.2em;
            margin-bottom: 20px;
            text-shadow: 0 0 20px rgba(255, 255, 255, 0.8);
        }

        .character-card .stats {
            font-size: 1.1em;
            line-height: 2;
            text-align: left;
        }

        .current-player-indicator {
            font-size: 3em;
            margin-bottom: 40px;
            padding: 30px;
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
            border-radius: 20px;
            border: 5px solid;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
        }

        .p1-indicator { border-color: #00ffff; color: #00ffff; text-shadow: 0 0 30px #00ffff; }
        .p2-indicator { border-color: #ff0080; color: #ff0080; text-shadow: 0 0 30px #ff0080; }
        .p3-indicator { border-color: #00ff00; color: #00ff00; text-shadow: 0 0 30px #00ff00; }
        .p4-indicator { border-color: #ffff00; color: #ffff00; text-shadow: 0 0 30px #ffff00; }

        .selections-display {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            margin-top: 40px;
            padding: 30px;
            background: rgba(0, 0, 0, 0.6);
            border-radius: 20px;
        }

        .selection-box {
            padding: 25px;
            border-radius: 15px;
            border: 4px solid;
            min-height: 120px;
            background: linear-gradient(135deg, rgba(0, 0, 0, 0.6), rgba(30, 30, 60, 0.6));
            transition: all 0.3s ease;
        }

        .selection-box.p1 { border-color: #00ffff; }
        .selection-box.p2 { border-color: #ff0080; }
        .selection-box.p3 { border-color: #00ff00; }
        .selection-box.p4 { border-color: #ffff00; }

        #gameCanvas {
            border: 8px solid transparent;
            border-radius: 10px;
            box-shadow: 0 0 80px rgba(121, 40, 202, 0.8);
            display: none;
            margin: 0 auto;
            background: #0a0a0a;
        }

        .game-hud {
            display: none;
            margin-top: 25px;
        }

        .hud-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin-bottom: 20px;
        }

        .player-hud {
            background: linear-gradient(135deg, rgba(0, 0, 0, 0.95), rgba(20, 20, 40, 0.95));
            padding: 18px;
            border-radius: 15px;
            border: 4px solid;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
        }

        .player1-hud { border-color: #00ffff; }
        .player2-hud { border-color: #ff0080; }
        .player3-hud { border-color: #00ff00; }
        .player4-hud { border-color: #ffff00; }

        .hud-name {
            font-size: 1.1em;
            font-weight: bold;
            margin-bottom: 8px;
        }

        .health-bar-container {
            background: rgba(0, 0, 0, 0.8);
            height: 18px;
            border-radius: 10px;
            overflow: hidden;
            margin: 8px 0;
            position: relative;
            border: 2px solid rgba(255, 255, 255, 0.2);
        }

        .health-bar {
            height: 100%;
            transition: width 0.3s ease;
        }

        .health-text {
            position: absolute;
            width: 100%;
            text-align: center;
            line-height: 18px;
            font-weight: bold;
            font-size: 0.8em;
        }

        .game-over-screen {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: linear-gradient(135deg, rgba(0, 0, 0, 0.98), rgba(30, 20, 60, 0.98));
            padding: 70px 120px;
            border-radius: 40px;
            border: 8px solid #ffd700;
            display: none;
            z-index: 1000;
            text-align: center;
            box-shadow: 0 0 100px rgba(255, 215, 0, 0.8);
        }

        .game-over-screen.show { 
            display: block;
            animation: gameOverAppear 0.6s ease-out;
        }

        @keyframes gameOverAppear {
            from { opacity: 0; transform: translate(-50%, -50%) scale(0.8); }
            to { opacity: 1; transform: translate(-50%, -50%) scale(1); }
        }

        .winner-text {
            font-size: 5em;
            margin-bottom: 30px;
            animation: winner-pulse 1.5s infinite;
            text-shadow: 0 0 40px currentColor;
        }

        @keyframes winner-pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        .return-menu-btn {
            padding: 25px 60px;
            background: linear-gradient(135deg, #7928ca, #ff0080);
            border: 4px solid #fff;
            border-radius: 20px;
            color: white;
            font-weight: bold;
            font-size: 1.6em;
            cursor: pointer;
            margin: 15px;
            transition: all 0.3s ease;
        }

        .return-menu-btn:hover {
            transform: scale(1.1) translateY(-5px);
        }

        .back-btn {
            padding: 18px 40px;
            background: linear-gradient(135deg, #555, #333);
            border: 3px solid #888;
            border-radius: 15px;
            color: white;
            font-weight: bold;
            font-size: 1.3em;
            cursor: pointer;
            margin-top: 30px;
            transition: all 0.3s ease;
        }

        .back-btn:hover {
            transform: scale(1.05);
            border-color: #fff;
        }

        .language-btn {
            padding: 25px 20px;
            background: linear-gradient(135deg, rgba(121, 40, 202, 0.6), rgba(255, 0, 128, 0.6));
            border: 4px solid transparent;
            border-radius: 15px;
            color: white;
            font-weight: bold;
            font-size: 1.4em;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
        }

        .language-btn:hover {
            transform: translateY(-5px) scale(1.05);
            border-color: #00ffff;
            box-shadow: 0 10px 40px rgba(0, 255, 255, 0.5);
        }

        .hidden { display: none; }

        .sound-toggle {
            position: fixed;
            top: 20px;
            left: 20px;
            padding: 15px 25px;
            background: rgba(0, 0, 0, 0.7);
            border: 3px solid #7928ca;
            border-radius: 15px;
            color: white;
            font-size: 1.5em;
            cursor: pointer;
            z-index: 9999;
            transition: all 0.3s ease;
        }

        .sound-toggle:hover {
            background: rgba(121, 40, 202, 0.9);
            transform: scale(1.1);
        }

        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 20px 30px;
            background: linear-gradient(135deg, rgba(121, 40, 202, 0.95), rgba(255, 0, 128, 0.95));
            border: 3px solid #00ffff;
            border-radius: 15px;
            color: white;
            font-size: 1.2em;
            z-index: 10000;
            box-shadow: 0 10px 40px rgba(0, 255, 255, 0.5);
            animation: slideIn 0.5s ease-out;
        }

        @keyframes slideIn {
            from { transform: translateX(400px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        .kill-feed {
            position: fixed;
            top: 80px;
            right: 20px;
            width: 300px;
            z-index: 100;
        }

        .kill-message {
            background: rgba(0, 0, 0, 0.85);
            border-left: 4px solid #ff0080;
            padding: 12px 18px;
            margin-bottom: 8px;
            border-radius: 8px;
            font-size: 0.95em;
            animation: slideIn 0.3s ease-out;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
        }

        .power-up {
            position: absolute;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            animation: powerUpFloat 2s ease-in-out infinite;
            box-shadow: 0 0 20px currentColor;
        }

        @keyframes powerUpFloat {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-10px) rotate(180deg); }
        }

        .ultimate-ready {
            animation: ultimateGlow 1s ease-in-out infinite;
        }

        @keyframes ultimateGlow {
            0%, 100% { box-shadow: 0 0 20px #ffd700; }
            50% { box-shadow: 0 0 40px #ffd700, 0 0 60px #ff0080; }
        }

        .combo-text {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 4em;
            font-weight: bold;
            color: #ffff00;
            text-shadow: 0 0 30px #ffff00, 0 0 60px #ff0000;
            pointer-events: none;
            z-index: 9998;
            animation: comboShow 1.5s ease-out forwards;
        }

        @keyframes comboShow {
            0% { opacity: 0; transform: translate(-50%, -50%) scale(0.5); }
            20% { opacity: 1; transform: translate(-50%, -50%) scale(1.5); }
            80% { opacity: 1; transform: translate(-50%, -50%) scale(1.2); }
            100% { opacity: 0; transform: translate(-50%, -50%) scale(0.8) translateY(-100px); }
        }
    </style>
</head>
<body>
    <div class="sound-toggle" onclick="toggleSound()" title="Toggle Sound Effects">🔊</div>
    <div id="killFeed" class="kill-feed"></div>
    
    <div class="game-wrapper">
        <h1 class="title">LOCK IN</h1>
        <div class="subtitle">ULTIMATE BATTLE ARENA</div>
        <div style="display: inline-block; background: linear-gradient(135deg, #ff0080, #7928ca); padding: 8px 20px; border-radius: 20px; font-size: 0.9em; letter-spacing: 3px; margin-bottom: 30px; animation: badgePulse 2s ease-in-out infinite; box-shadow: 0 0 20px rgba(255, 0, 128, 0.5);">
            ⚡ ENHANCED EDITION v2.0 ⚡
        </div>
        
        <!-- Language Selection Screen -->
        <div class="screen active" id="languageScreen">
            <h2>SELECT LANGUAGE / 選擇語言 / 选择语言</h2>
            <div class="language-grid" style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; max-width: 900px; margin: 0 auto;">
                <button class="language-btn" onclick="setLanguage('en')">
                    🇬🇧 English
                </button>
                <button class="language-btn" onclick="setLanguage('zh-TW')">
                    🇹🇼 繁體中文
                </button>
                <button class="language-btn" onclick="setLanguage('zh-CN')">
                    🇨🇳 简体中文
                </button>
                <button class="language-btn" onclick="setLanguage('es')">
                    🇪🇸 Español
                </button>
                <button class="language-btn" onclick="setLanguage('fr')">
                    🇫🇷 Français
                </button>
                <button class="language-btn" onclick="setLanguage('de')">
                    🇩🇪 Deutsch
                </button>
                <button class="language-btn" onclick="setLanguage('ja')">
                    🇯🇵 日本語
                </button>
                <button class="language-btn" onclick="setLanguage('ko')">
                    🇰🇷 한국어
                </button>
                <button class="language-btn" onclick="setLanguage('pt')">
                    🇵🇹 Português
                </button>
                <button class="language-btn" onclick="setLanguage('ru')">
                    🇷🇺 Русский
                </button>
                <button class="language-btn" onclick="setLanguage('it')">
                    🇮🇹 Italiano
                </button>
                <button class="language-btn" onclick="setLanguage('ar')">
                    🇸🇦 العربية
                </button>
                <button class="language-btn" onclick="setLanguage('hi')">
                    🇮🇳 हिन्दी
                </button>
                <button class="language-btn" onclick="setLanguage('th')">
                    🇹🇭 ภาษาไทย
                </button>
                <button class="language-btn" onclick="setLanguage('vi')">
                    🇻🇳 Tiếng Việt
                </button>
            </div>
        </div>

        <!-- Main Menu -->
        <div class="screen" id="mainMenu">
            <h2 id="mainMenuTitle">MAIN MENU</h2>
            <div class="menu-buttons">
                <button class="menu-btn" onclick="showPlayerCountSelect()"><span id="battleArenaText">BATTLE ARENA</span></button>
                <button class="menu-btn" onclick="showCartRaceSelect()"><span id="cartRacingText">CART RACING</span></button>
            </div>
            <button class="back-btn" onclick="backToLanguageSelect()" style="margin-top: 40px;">🌍 CHANGE LANGUAGE</button>
        </div>

        <!-- Player Count Selection -->
        <div class="screen" id="playerCountScreen">
            <h2 id="selectPlayerCountTitle">SELECT PLAYER COUNT</h2>
            <div class="menu-buttons">
                <button class="menu-btn player-count-btn" onclick="setPlayerCount(2)">2 <span id="playersText1">PLAYERS</span></button>
                <button class="menu-btn player-count-btn" onclick="setPlayerCount(3)">3 <span id="playersText2">PLAYERS</span></button>
                <button class="menu-btn player-count-btn" onclick="setPlayerCount(4)">4 <span id="playersText3">PLAYERS</span></button>
                <div style="display: flex; gap: 20px; justify-content: center; margin-top: 30px;">
                    <button class="back-btn" onclick="showMainMenu()"><span id="backText1">◀ BACK</span></button>
                    <button class="back-btn" onclick="backToLanguageSelect()">🌍 MAIN PAGE</button>
                </div>
            </div>
        </div>

        <!-- Cart Race Player Count -->
        <div class="screen" id="cartPlayerCountScreen">
            <h2 id="cartRacingTitle">CART RACING - SELECT PLAYERS</h2>
            <div class="menu-buttons">
                <button class="menu-btn player-count-btn" onclick="startCartRace(2)">2 <span id="playersText4">PLAYERS</span></button>
                <button class="menu-btn player-count-btn" onclick="startCartRace(3)">3 <span id="playersText5">PLAYERS</span></button>
                <button class="menu-btn player-count-btn" onclick="startCartRace(4)">4 <span id="playersText6">PLAYERS</span></button>
                <div style="display: flex; gap: 20px; justify-content: center; margin-top: 30px;">
                    <button class="back-btn" onclick="showMainMenu()"><span id="backText2">◀ BACK</span></button>
                    <button class="back-btn" onclick="backToLanguageSelect()">🌍 MAIN PAGE</button>
                </div>
            </div>
        </div>

        <!-- Nickname Entry Screen -->
        <div class="screen" id="nicknameScreen">
            <div class="current-player-indicator" id="nicknamePlayerIndicator">
                PLAYER 1 - ENTER YOUR NICKNAME
            </div>
            <div style="margin: 40px 0;">
                <input type="text" id="nicknameInput" 
                       placeholder="Enter nickname..." 
                       maxlength="12"
                       style="padding: 20px 30px; font-size: 2em; border-radius: 15px; 
                              border: 4px solid #7928ca; background: rgba(0,0,0,0.7); 
                              color: white; text-align: center; font-family: Impact; 
                              letter-spacing: 2px; width: 500px;"
                       onkeypress="if(event.key==='Enter') submitNickname()">
            </div>
            <button class="menu-btn" onclick="submitNickname()" style="font-size: 1.5em; padding: 20px 60px;">
                <span id="confirmText">CONFIRM</span>
            </button>
            <div class="selections-display" id="nicknameDisplay" style="margin-top: 30px;"></div>
            <div style="display: flex; gap: 20px; justify-content: center; margin-top: 30px;">
                <button class="back-btn" onclick="backToPlayerCount()"><span id="backText3">◀ BACK</span></button>
                <button class="back-btn" onclick="backToLanguageSelect()">🌍 MAIN PAGE</button>
            </div>
        </div>

        <!-- Character Selection Screen -->
        <div class="screen" id="characterSelectScreen">
            <div class="current-player-indicator" id="currentPlayerIndicator">
                PLAYER 1 - SELECT YOUR CHARACTER
            </div>
            <div class="character-grid" id="characterGrid"></div>
            <div class="selections-display" id="selectionsDisplay"></div>
            <div style="display: flex; gap: 20px; justify-content: center; margin-top: 30px;">
                <button class="back-btn" onclick="backToNickname()"><span id="backText4">◀ BACK</span></button>
                <button class="back-btn" onclick="backToLanguageSelect()">🌍 MAIN PAGE</button>
            </div>
        </div>

        <!-- Game Canvas -->
        <canvas id="gameCanvas" width="1400" height="800"></canvas>

        <!-- Game HUD -->
        <div class="game-hud" id="gameHud">
            <div class="hud-grid" id="hudGrid"></div>
            <div style="background: rgba(0,0,0,0.7); padding: 10px; border-radius: 10px; font-size: 0.85em;" id="controlsDisplay"></div>
        </div>

        <!-- Game Over Screen -->
        <div class="game-over-screen" id="gameOverScreen">
            <div class="winner-text" id="winnerText">PLAYER 1 WINS!</div>
            <div id="finalStats" style="font-size: 1.5em; margin: 20px 0;"></div>
            <button class="return-menu-btn" onclick="returnToMainMenu()"><span id="mainMenuBtnText">MAIN MENU</span></button>
            <button class="return-menu-btn" onclick="backToLanguageSelect()" style="background: linear-gradient(135deg, #555, #333);">🌍 CHANGE LANGUAGE</button>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const keys = {};

        let gameMode = 'battle';
        let playerCount = 2;
        let currentSelectingPlayer = 1;
        let selectedChars = [];
        let playerNicknames = [];
        let gameActive = false;
        let obstacles = [];
        let bushes = [];
        let particles = [];
        let players = [];
        let staticBackgroundCanvas = null;
        let currentLanguage = 'en';

        // ENHANCED FEATURES
        let soundEnabled = true;
        let powerUps = [];
        let killFeedMessages = [];
        let comboCount = 0;
        let lastKillTime = 0;
        let gameStartTime = 0;

        // Translation data
        const translations = {
            en: {
                mainMenu: 'MAIN MENU',
                battleArena: 'BATTLE ARENA',
                cartRacing: 'CART RACING',
                selectPlayerCount: 'SELECT PLAYER COUNT',
                players: 'PLAYERS',
                back: 'BACK',
                enterNickname: 'ENTER YOUR NICKNAME',
                confirm: 'CONFIRM',
                selectCharacter: 'SELECT YOUR CHARACTER',
                startBattle: 'START BATTLE!',
                mainMenuBtn: 'MAIN MENU',
                wins: 'WINS',
                finalStandings: 'FINAL STANDINGS',
                kills: 'Kills',
                controls: 'CONTROLS',
                completeLaps: 'COMPLETE 3 LAPS!',
                raceResults: 'RACE RESULTS',
                finished: 'FINISHED',
                racing: 'Racing...',
                lap: 'Lap',
                balancedFighter: 'Balanced fighter',
                speedDemon: 'Speed demon',
                heavyTank: 'Heavy tank',
                stealthAssassin: 'Stealth assassin',
                electricWarrior: 'Electric warrior',
                pyroSpecialist: 'Pyro specialist',
                damage: 'Damage'
            },
            'zh-TW': {
                mainMenu: '主選單',
                battleArena: '戰鬥競技場',
                cartRacing: '卡丁車競速',
                selectPlayerCount: '選擇玩家數量',
                players: '位玩家',
                back: '返回',
                enterNickname: '輸入您的暱稱',
                confirm: '確認',
                selectCharacter: '選擇您的角色',
                startBattle: '開始戰鬥！',
                mainMenuBtn: '主選單',
                wins: '獲勝',
                finalStandings: '最終排名',
                kills: '擊殺數',
                controls: '操作方式',
                completeLaps: '完成3圈！',
                raceResults: '比賽結果',
                finished: '完成',
                racing: '競速中...',
                lap: '圈數',
                balancedFighter: '平衡型戰士',
                speedDemon: '速度惡魔',
                heavyTank: '重型坦克',
                stealthAssassin: '隱形刺客',
                electricWarrior: '電擊戰士',
                pyroSpecialist: '火焰專家'
            },
            'zh-CN': {
                mainMenu: '主菜单',
                battleArena: '战斗竞技场',
                cartRacing: '卡丁车竞速',
                selectPlayerCount: '选择玩家数量',
                players: '位玩家',
                back: '返回',
                enterNickname: '输入您的昵称',
                confirm: '确认',
                selectCharacter: '选择您的角色',
                startBattle: '开始战斗！',
                mainMenuBtn: '主菜单',
                wins: '获胜',
                finalStandings: '最终排名',
                kills: '击杀数',
                controls: '操作方式',
                completeLaps: '完成3圈！',
                raceResults: '比赛结果',
                finished: '完成',
                racing: '竞速中...',
                lap: '圈数',
                balancedFighter: '平衡型战士',
                speedDemon: '速度恶魔',
                heavyTank: '重型坦克',
                stealthAssassin: '隐形刺客',
                electricWarrior: '电击战士',
                pyroSpecialist: '火焰专家'
            },
            es: {
                mainMenu: 'MENÚ PRINCIPAL',
                battleArena: 'ARENA DE BATALLA',
                cartRacing: 'CARRERA DE KARTS',
                selectPlayerCount: 'SELECCIONAR JUGADORES',
                players: 'JUGADORES',
                back: 'ATRÁS',
                enterNickname: 'INGRESA TU APODO',
                confirm: 'CONFIRMAR',
                selectCharacter: 'SELECCIONA TU PERSONAJE',
                startBattle: '¡COMENZAR BATALLA!',
                mainMenuBtn: 'MENÚ PRINCIPAL',
                wins: 'GANA',
                finalStandings: 'CLASIFICACIÓN FINAL',
                kills: 'Eliminaciones',
                controls: 'CONTROLES',
                completeLaps: '¡COMPLETA 3 VUELTAS!',
                raceResults: 'RESULTADOS',
                finished: 'TERMINADO',
                racing: 'Corriendo...',
                lap: 'Vuelta',
                balancedFighter: 'Luchador equilibrado',
                speedDemon: 'Demonio veloz',
                heavyTank: 'Tanque pesado',
                stealthAssassin: 'Asesino sigiloso',
                electricWarrior: 'Guerrero eléctrico',
                pyroSpecialist: 'Especialista en fuego'
            },
            fr: {
                mainMenu: 'MENU PRINCIPAL',
                battleArena: 'ARÈNE DE COMBAT',
                cartRacing: 'COURSE DE KARTS',
                selectPlayerCount: 'NOMBRE DE JOUEURS',
                players: 'JOUEURS',
                back: 'RETOUR',
                enterNickname: 'ENTREZ VOTRE PSEUDO',
                confirm: 'CONFIRMER',
                selectCharacter: 'CHOISISSEZ VOTRE PERSONNAGE',
                startBattle: 'COMMENCER!',
                mainMenuBtn: 'MENU PRINCIPAL',
                wins: 'GAGNE',
                finalStandings: 'CLASSEMENT FINAL',
                kills: 'Éliminations',
                controls: 'CONTRÔLES',
                completeLaps: 'COMPLÉTEZ 3 TOURS!',
                raceResults: 'RÉSULTATS',
                finished: 'TERMINÉ',
                racing: 'Course...',
                lap: 'Tour',
                balancedFighter: 'Combattant équilibré',
                speedDemon: 'Démon de vitesse',
                heavyTank: 'Tank lourd',
                stealthAssassin: 'Assassin furtif',
                electricWarrior: 'Guerrier électrique',
                pyroSpecialist: 'Spécialiste du feu'
            },
            de: {
                mainMenu: 'HAUPTMENÜ',
                battleArena: 'KAMPFARENA',
                cartRacing: 'KARTRENNEN',
                selectPlayerCount: 'SPIELERZAHL',
                players: 'SPIELER',
                back: 'ZURÜCK',
                enterNickname: 'SPITZNAME EINGEBEN',
                confirm: 'BESTÄTIGEN',
                selectCharacter: 'CHARAKTER WÄHLEN',
                startBattle: 'KAMPF STARTEN!',
                mainMenuBtn: 'HAUPTMENÜ',
                wins: 'GEWINNT',
                finalStandings: 'ENDSTAND',
                kills: 'Abschüsse',
                controls: 'STEUERUNG',
                completeLaps: '3 RUNDEN ABSOLVIEREN!',
                raceResults: 'ERGEBNISSE',
                finished: 'FERTIG',
                racing: 'Rennen...',
                lap: 'Runde',
                balancedFighter: 'Ausgewogener Kämpfer',
                speedDemon: 'Geschwindigkeitsdämon',
                heavyTank: 'Schwerer Panzer',
                stealthAssassin: 'Heimlicher Attentäter',
                electricWarrior: 'Elektrokrieger',
                pyroSpecialist: 'Feuerspezialist'
            },
            ja: {
                mainMenu: 'メインメニュー',
                battleArena: 'バトルアリーナ',
                cartRacing: 'カートレース',
                selectPlayerCount: 'プレイヤー数選択',
                players: 'プレイヤー',
                back: '戻る',
                enterNickname: 'ニックネームを入力',
                confirm: '確認',
                selectCharacter: 'キャラクター選択',
                startBattle: 'バトル開始！',
                mainMenuBtn: 'メインメニュー',
                wins: '勝利',
                finalStandings: '最終順位',
                kills: 'キル数',
                controls: '操作方法',
                completeLaps: '3周完走！',
                raceResults: 'レース結果',
                finished: '完了',
                racing: 'レース中...',
                lap: '周',
                balancedFighter: 'バランス型ファイター',
                speedDemon: 'スピードデーモン',
                heavyTank: 'ヘビータンク',
                stealthAssassin: 'ステルスアサシン',
                electricWarrior: '電撃ウォリアー',
                pyroSpecialist: '炎の専門家'
            },
            ko: {
                mainMenu: '메인 메뉴',
                battleArena: '배틀 아레나',
                cartRacing: '카트 레이싱',
                selectPlayerCount: '플레이어 수 선택',
                players: '플레이어',
                back: '뒤로',
                enterNickname: '닉네임 입력',
                confirm: '확인',
                selectCharacter: '캐릭터 선택',
                startBattle: '전투 시작!',
                mainMenuBtn: '메인 메뉴',
                wins: '승리',
                finalStandings: '최종 순위',
                kills: '킬',
                controls: '조작법',
                completeLaps: '3바퀴 완주!',
                raceResults: '레이스 결과',
                finished: '완료',
                racing: '레이싱 중...',
                lap: '랩',
                balancedFighter: '균형잡힌 파이터',
                speedDemon: '스피드 데몬',
                heavyTank: '중전차',
                stealthAssassin: '은신 암살자',
                electricWarrior: '전기 전사',
                pyroSpecialist: '화염 전문가'
            },
            pt: {
                mainMenu: 'MENU PRINCIPAL',
                battleArena: 'ARENA DE BATALHA',
                cartRacing: 'CORRIDA DE KARTS',
                selectPlayerCount: 'NÚMERO DE JOGADORES',
                players: 'JOGADORES',
                back: 'VOLTAR',
                enterNickname: 'DIGITE SEU APELIDO',
                confirm: 'CONFIRMAR',
                selectCharacter: 'ESCOLHA SEU PERSONAGEM',
                startBattle: 'INICIAR BATALHA!',
                mainMenuBtn: 'MENU PRINCIPAL',
                wins: 'VENCE',
                finalStandings: 'CLASSIFICAÇÃO FINAL',
                kills: 'Abates',
                controls: 'CONTROLES',
                completeLaps: 'COMPLETE 3 VOLTAS!',
                raceResults: 'RESULTADOS',
                finished: 'TERMINADO',
                racing: 'Correndo...',
                lap: 'Volta',
                balancedFighter: 'Lutador equilibrado',
                speedDemon: 'Demônio da velocidade',
                heavyTank: 'Tanque pesado',
                stealthAssassin: 'Assassino furtivo',
                electricWarrior: 'Guerreiro elétrico',
                pyroSpecialist: 'Especialista em fogo'
            },
            ru: {
                mainMenu: 'ГЛАВНОЕ МЕНЮ',
                battleArena: 'БОЕВАЯ АРЕНА',
                cartRacing: 'КАРТИНГ',
                selectPlayerCount: 'ВЫБОР ИГРОКОВ',
                players: 'ИГРОКОВ',
                back: 'НАЗАД',
                enterNickname: 'ВВЕДИТЕ НИКНЕЙМ',
                confirm: 'ПОДТВЕРДИТЬ',
                selectCharacter: 'ВЫБЕРИТЕ ПЕРСОНАЖА',
                startBattle: 'НАЧАТЬ БОЙ!',
                mainMenuBtn: 'ГЛАВНОЕ МЕНЮ',
                wins: 'ПОБЕЖДАЕТ',
                finalStandings: 'ИТОГОВЫЕ РЕЗУЛЬТАТЫ',
                kills: 'Убийства',
                controls: 'УПРАВЛЕНИЕ',
                completeLaps: 'ЗАВЕРШИТЕ 3 КРУГА!',
                raceResults: 'РЕЗУЛЬТАТЫ',
                finished: 'ФИНИШ',
                racing: 'Гонка...',
                lap: 'Круг',
                balancedFighter: 'Сбалансированный боец',
                speedDemon: 'Демон скорости',
                heavyTank: 'Тяжелый танк',
                stealthAssassin: 'Скрытный убийца',
                electricWarrior: 'Электрический воин',
                pyroSpecialist: 'Пиротехник'
            },
            it: {
                mainMenu: 'MENU PRINCIPALE',
                battleArena: 'ARENA DI BATTAGLIA',
                cartRacing: 'CORSA DI KART',
                selectPlayerCount: 'NUMERO GIOCATORI',
                players: 'GIOCATORI',
                back: 'INDIETRO',
                enterNickname: 'INSERISCI NICKNAME',
                confirm: 'CONFERMA',
                selectCharacter: 'SCEGLI PERSONAGGIO',
                startBattle: 'INIZIA BATTAGLIA!',
                mainMenuBtn: 'MENU PRINCIPALE',
                wins: 'VINCE',
                finalStandings: 'CLASSIFICA FINALE',
                kills: 'Uccisioni',
                controls: 'CONTROLLI',
                completeLaps: 'COMPLETA 3 GIRI!',
                raceResults: 'RISULTATI',
                finished: 'FINITO',
                racing: 'In corsa...',
                lap: 'Giro',
                balancedFighter: 'Combattente equilibrato',
                speedDemon: 'Demone della velocità',
                heavyTank: 'Carro pesante',
                stealthAssassin: 'Assassino furtivo',
                electricWarrior: 'Guerriero elettrico',
                pyroSpecialist: 'Specialista del fuoco'
            },
            ar: {
                mainMenu: 'القائمة الرئيسية',
                battleArena: 'ساحة المعركة',
                cartRacing: 'سباق الكارتات',
                selectPlayerCount: 'اختر عدد اللاعبين',
                players: 'لاعبين',
                back: 'رجوع',
                enterNickname: 'أدخل اسمك المستعار',
                confirm: 'تأكيد',
                selectCharacter: 'اختر شخصيتك',
                startBattle: 'ابدأ المعركة!',
                mainMenuBtn: 'القائمة الرئيسية',
                wins: 'يفوز',
                finalStandings: 'الترتيب النهائي',
                kills: 'القتلى',
                controls: 'التحكم',
                completeLaps: 'أكمل 3 لفات!',
                raceResults: 'نتائج السباق',
                finished: 'انتهى',
                racing: 'يسابق...',
                lap: 'لفة',
                balancedFighter: 'مقاتل متوازن',
                speedDemon: 'شيطان السرعة',
                heavyTank: 'دبابة ثقيلة',
                stealthAssassin: 'قاتل خفي',
                electricWarrior: 'محارب كهربائي',
                pyroSpecialist: 'متخصص النار'
            },
            hi: {
                mainMenu: 'मुख्य मेनू',
                battleArena: 'युद्ध क्षेत्र',
                cartRacing: 'कार्ट रेसिंग',
                selectPlayerCount: 'खिलाड़ी संख्या चुनें',
                players: 'खिलाड़ी',
                back: 'वापस',
                enterNickname: 'अपना उपनाम दर्ज करें',
                confirm: 'पुष्टि करें',
                selectCharacter: 'अपना चरित्र चुनें',
                startBattle: 'युद्ध शुरू करें!',
                mainMenuBtn: 'मुख्य मेनू',
                wins: 'जीतता है',
                finalStandings: 'अंतिम स्थिति',
                kills: 'हत्याएं',
                controls: 'नियंत्रण',
                completeLaps: '3 चक्कर पूरे करें!',
                raceResults: 'दौड़ परिणाम',
                finished: 'समाप्त',
                racing: 'दौड़ रहा है...',
                lap: 'चक्कर',
                balancedFighter: 'संतुलित लड़ाकू',
                speedDemon: 'गति राक्षस',
                heavyTank: 'भारी टैंक',
                stealthAssassin: 'गुप्त हत्यारा',
                electricWarrior: 'बिजली योद्धा',
                pyroSpecialist: 'आग विशेषज्ञ'
            },
            th: {
                mainMenu: 'เมนูหลัก',
                battleArena: 'สนามการต่อสู้',
                cartRacing: 'การแข่งรถ',
                selectPlayerCount: 'เลือกจำนวนผู้เล่น',
                players: 'ผู้เล่น',
                back: 'กลับ',
                enterNickname: 'ใส่ชื่อเล่นของคุณ',
                confirm: 'ยืนยัน',
                selectCharacter: 'เลือกตัวละครของคุณ',
                startBattle: 'เริ่มการต่อสู้!',
                mainMenuBtn: 'เมนูหลัก',
                wins: 'ชนะ',
                finalStandings: 'อันดับสุดท้าย',
                kills: 'การฆ่า',
                controls: 'การควบคุม',
                completeLaps: 'ทำ 3 รอบให้เสร็จ!',
                raceResults: 'ผลการแข่งขัน',
                finished: 'เสร็จสิ้น',
                racing: 'กำลังแข่ง...',
                lap: 'รอบ',
                balancedFighter: 'นักสู้สมดุล',
                speedDemon: 'ปีศาจความเร็ว',
                heavyTank: 'รถถังหนัก',
                stealthAssassin: 'นักฆ่าล่องหน',
                electricWarrior: 'นักรบไฟฟ้า',
                pyroSpecialist: 'ผู้เชี่ยวชาญไฟ'
            },
            vi: {
                mainMenu: 'MENU CHÍNH',
                battleArena: 'SÂN CHIẾN',
                cartRacing: 'ĐUA XE',
                selectPlayerCount: 'CHỌN SỐ NGƯỜI CHƠI',
                players: 'NGƯỜI CHƠI',
                back: 'QUAY LẠI',
                enterNickname: 'NHẬP BIỆT DANH',
                confirm: 'XÁC NHẬN',
                selectCharacter: 'CHỌN NHÂN VẬT',
                startBattle: 'BẮT ĐẦU CHIẾN ĐẤU!',
                mainMenuBtn: 'MENU CHÍNH',
                wins: 'THẮNG',
                finalStandings: 'BXH CUỐI CÙNG',
                kills: 'Giết',
                controls: 'ĐIỀU KHIỂN',
                completeLaps: 'HOÀN THÀNH 3 VÒNG!',
                raceResults: 'KẾT QUẢ',
                finished: 'HOÀN THÀNH',
                racing: 'Đang đua...',
                lap: 'Vòng',
                balancedFighter: 'Chiến binh cân bằng',
                speedDemon: 'Ác quỷ tốc độ',
                heavyTank: 'Xe tăng nặng',
                stealthAssassin: 'Sát thủ tàng hình',
                electricWarrior: 'Chiến binh điện',
                pyroSpecialist: 'Chuyên gia lửa',
                damage: 'Sát thương'
            }
        };

        function t(key) {
            return translations[currentLanguage][key] || translations['en'][key] || key;
        }

        function setLanguage(lang) {
            currentLanguage = lang;
            updateAllText();
            showScreen('mainMenu');
        }

        function updateAllText() {
            // Update main menu
            const mainTitle = document.getElementById('mainMenuTitle');
            if (mainTitle) mainTitle.textContent = t('mainMenu');
            
            const battleText = document.getElementById('battleArenaText');
            if (battleText) battleText.textContent = t('battleArena');
            
            const cartText = document.getElementById('cartRacingText');
            if (cartText) cartText.textContent = t('cartRacing');
            
            // Update player count screens
            const selectTitle = document.getElementById('selectPlayerCountTitle');
            if (selectTitle) selectTitle.textContent = t('selectPlayerCount');
            
            const cartTitle = document.getElementById('cartRacingTitle');
            if (cartTitle) cartTitle.textContent = t('cartRacing') + ' - ' + t('selectPlayerCount');
            
            // Update all "PLAYERS" text
            for (let i = 1; i <= 6; i++) {
                const playersText = document.getElementById('playersText' + i);
                if (playersText) playersText.textContent = t('players');
            }
            
            // Update all "BACK" buttons
            for (let i = 1; i <= 5; i++) {
                const backText = document.getElementById('backText' + i);
                if (backText) backText.textContent = t('back');
            }
            
            // Update confirm button
            const confirmText = document.getElementById('confirmText');
            if (confirmText) confirmText.textContent = t('confirm');
            
            // Update main menu button
            const mainMenuBtn = document.getElementById('mainMenuBtnText');
            if (mainMenuBtn) mainMenuBtn.textContent = t('mainMenuBtn');
        }

        function updateMainMenuText() {
            updateAllText();
        }

        function updateNicknameIndicator() {
            const indicator = document.getElementById('nicknamePlayerIndicator');
            indicator.textContent = `${playerNames[currentSelectingPlayer - 1]} - ${t('enterNickname')}`;
            indicator.className = 'current-player-indicator p' + currentSelectingPlayer + '-indicator';
        }

        function updateCurrentPlayerIndicator() {
            const indicator = document.getElementById('currentPlayerIndicator');
            const nickname = playerNicknames[currentSelectingPlayer - 1] || playerNames[currentSelectingPlayer - 1];
            indicator.textContent = `${nickname} - ${t('selectCharacter')}`;
            indicator.className = 'current-player-indicator p' + currentSelectingPlayer + '-indicator';
        }

        const characters = {
            vortex: { name: 'VORTEX', health: 5000, speed: 4.5, damage: 380, color: '#00ffff', descKey: 'balancedFighter' },
            blaze: { name: 'BLAZE', health: 4500, speed: 5.5, damage: 320, color: '#ff4400', descKey: 'speedDemon' },
            titan: { name: 'TITAN', health: 8000, speed: 2.8, damage: 650, color: '#ffaa00', descKey: 'heavyTank' },
            phantom: { name: 'PHANTOM', health: 3800, speed: 5, damage: 450, color: '#9900ff', descKey: 'stealthAssassin' },
            storm: { name: 'STORM', health: 5200, speed: 4, damage: 400, color: '#00ff88', descKey: 'electricWarrior' },
            inferno: { name: 'INFERNO', health: 4800, speed: 4.8, damage: 420, color: '#ff6600', descKey: 'pyroSpecialist' }
        };

        const playerColors = ['#00ffff', '#ff0080', '#00ff00', '#ffff00'];
        const playerNames = ['PLAYER 1', 'PLAYER 2', 'PLAYER 3', 'PLAYER 4'];

        // ===========================================
        // SOUND SYSTEM (Web Audio API)
        // ===========================================
        
        const audioContext = new (window.AudioContext || window.webkitAudioContext)();
        
        function playSound(type, volume = 0.3) {
            if (!soundEnabled) return;
            
            try {
                const oscillator = audioContext.createOscillator();
                const gainNode = audioContext.createGain();
                
                oscillator.connect(gainNode);
                gainNode.connect(audioContext.destination);
                
                gainNode.gain.value = volume;
                
                switch(type) {
                    case 'shoot':
                        oscillator.frequency.setValueAtTime(440, audioContext.currentTime);
                        oscillator.frequency.exponentialRampToValueAtTime(110, audioContext.currentTime + 0.1);
                        gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.1);
                        break;
                    case 'hit':
                        oscillator.frequency.setValueAtTime(200, audioContext.currentTime);
                        oscillator.frequency.exponentialRampToValueAtTime(50, audioContext.currentTime + 0.15);
                        oscillator.type = 'sawtooth';
                        break;
                    case 'kill':
                        oscillator.frequency.setValueAtTime(100, audioContext.currentTime);
                        oscillator.frequency.exponentialRampToValueAtTime(1000, audioContext.currentTime + 0.3);
                        gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.3);
                        break;
                    case 'powerup':
                        oscillator.frequency.setValueAtTime(523, audioContext.currentTime);
                        oscillator.frequency.setValueAtTime(659, audioContext.currentTime + 0.05);
                        oscillator.frequency.setValueAtTime(784, audioContext.currentTime + 0.1);
                        break;
                    case 'ultimate':
                        oscillator.frequency.setValueAtTime(880, audioContext.currentTime);
                        oscillator.frequency.setValueAtTime(1046, audioContext.currentTime + 0.1);
                        oscillator.type = 'triangle';
                        break;
                }
                
                oscillator.start(audioContext.currentTime);
                oscillator.stop(audioContext.currentTime + 0.3);
            } catch (e) {
                console.log('Audio error:', e);
            }
        }

        function toggleSound() {
            soundEnabled = !soundEnabled;
            document.querySelector('.sound-toggle').textContent = soundEnabled ? '🔊' : '🔇';
            showNotification(soundEnabled ? '🔊 Sound ON' : '🔇 Sound OFF');
        }

        // ===========================================
        // NOTIFICATION SYSTEM
        // ===========================================
        
        function showNotification(message) {
            const notif = document.createElement('div');
            notif.className = 'notification';
            notif.textContent = message;
            document.body.appendChild(notif);
            
            setTimeout(() => {
                notif.style.animation = 'slideIn 0.5s ease-in reverse';
                setTimeout(() => notif.remove(), 500);
            }, 2500);
        }

        // ===========================================
        // KILL FEED SYSTEM
        // ===========================================
        
        function addKillMessage(killer, victim) {
            const killFeed = document.getElementById('killFeed');
            if (!killFeed) return;
            
            const msg = document.createElement('div');
            msg.className = 'kill-message';
            msg.innerHTML = `<strong style="color: ${killer.color}">${killer.name}</strong> ☠️ <strong style="color: ${victim.color}">${victim.name}</strong>`;
            killFeed.insertBefore(msg, killFeed.firstChild);
            
            setTimeout(() => msg.remove(), 5000);
            
            while (killFeed.children.length > 5) {
                killFeed.lastChild.remove();
            }
        }

        // ===========================================
        // COMBO SYSTEM
        // ===========================================
        
        function checkCombo() {
            const now = Date.now();
            if (now - lastKillTime < 3000) {
                comboCount++;
                if (comboCount >= 2) {
                    showComboText(comboCount);
                }
            } else {
                comboCount = 1;
            }
            lastKillTime = now;
        }

        function showComboText(combo) {
            const comboTexts = ['', '', 'DOUBLE KILL!', 'TRIPLE KILL!', 'QUAD KILL!', 'MEGA KILL!', 'UNSTOPPABLE!', 'GODLIKE!'];
            const text = comboTexts[Math.min(combo, comboTexts.length - 1)] || 'LEGENDARY!';
            
            const comboEl = document.createElement('div');
            comboEl.className = 'combo-text';
            comboEl.textContent = text;
            document.body.appendChild(comboEl);
            
            playSound('ultimate', 0.5);
            
            setTimeout(() => comboEl.remove(), 1500);
        }

        // Menu Functions
        function showScreen(screenId) {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById(screenId).classList.add('active');
        }

        function showMainMenu() {
            showScreen('mainMenu');
        }

        function backToLanguageSelect() {
            showScreen('languageScreen');
        }

        function showPlayerCountSelect() {
            gameMode = 'battle';
            showScreen('playerCountScreen');
        }

        function showCartRaceSelect() {
            gameMode = 'race';
            showScreen('cartPlayerCountScreen');
        }

        function setPlayerCount(count) {
            playerCount = count;
            selectedChars = new Array(count).fill(null);
            playerNicknames = new Array(count).fill(null);
            currentSelectingPlayer = 1;
            showNicknameScreen();
        }

        function showNicknameScreen() {
            showScreen('nicknameScreen');
            updateNicknameIndicator();
            updateNicknameDisplay();
            document.getElementById('nicknameInput').value = '';
            document.getElementById('nicknameInput').focus();
        }

        function updateNicknameIndicator() {
            const indicator = document.getElementById('nicknamePlayerIndicator');
            indicator.textContent = `${playerNames[currentSelectingPlayer - 1]} - ENTER YOUR NICKNAME`;
            indicator.className = 'current-player-indicator p' + currentSelectingPlayer + '-indicator';
        }

        function updateNicknameDisplay() {
            const display = document.getElementById('nicknameDisplay');
            display.innerHTML = '';

            for (let i = 0; i < playerCount; i++) {
                const box = document.createElement('div');
                box.className = 'selection-box p' + (i + 1);
                
                if (playerNicknames[i]) {
                    box.innerHTML = `<strong>${playerNames[i]}</strong><br><div style="font-size: 1.5em; margin-top: 5px;">${playerNicknames[i]}</div>`;
                } else {
                    box.innerHTML = `<strong>${playerNames[i]}</strong><br><div style="opacity: 0.5; margin-top: 5px;">Waiting...</div>`;
                }
                display.appendChild(box);
            }
        }

        function submitNickname() {
            const input = document.getElementById('nicknameInput');
            const nickname = input.value.trim();
            
            if (nickname === '') {
                alert('Please enter a nickname!');
                return;
            }

            playerNicknames[currentSelectingPlayer - 1] = nickname;
            updateNicknameDisplay();

            if (currentSelectingPlayer < playerCount) {
                currentSelectingPlayer++;
                updateNicknameIndicator();
                input.value = '';
                input.focus();
            } else {
                if (gameMode === 'battle') {
                    currentSelectingPlayer = 1;
                    initCharacterSelect();
                    updateSelectionDisplay();
                    showScreen('characterSelectScreen');
                } else {
                    startCartRaceAfterNicknames();
                }
            }
        }

        function backToPlayerCount() {
            if (gameMode === 'battle') {
                showScreen('playerCountScreen');
            } else {
                showScreen('cartPlayerCountScreen');
            }
        }

        function backToNickname() {
            currentSelectingPlayer = 1;
            showNicknameScreen();
        }

        function initCharacterSelect() {
            const grid = document.getElementById('characterGrid');
            grid.innerHTML = '';

            Object.keys(characters).forEach(key => {
                const char = characters[key];
                const card = document.createElement('div');
                card.className = 'character-card';
                const desc = `${t(char.descKey)}\nHP: ${char.health} | ${t('damage')}: ${char.damage}`;
                card.innerHTML = `<h3>${char.name}</h3><div class="stats">${desc}</div>`;
                card.onclick = () => selectCharacter(key);
                grid.appendChild(card);
            });

            updateCurrentPlayerIndicator();
        }

        function updateCurrentPlayerIndicator() {
            const indicator = document.getElementById('currentPlayerIndicator');
            const nickname = playerNicknames[currentSelectingPlayer - 1] || playerNames[currentSelectingPlayer - 1];
            indicator.textContent = `${nickname} - SELECT YOUR CHARACTER`;
            indicator.className = 'current-player-indicator p' + currentSelectingPlayer + '-indicator';
        }

        function updateSelectionDisplay() {
            const display = document.getElementById('selectionsDisplay');
            display.innerHTML = '';

            for (let i = 0; i < playerCount; i++) {
                const box = document.createElement('div');
                box.className = 'selection-box p' + (i + 1);
                
                const nickname = playerNicknames[i] || playerNames[i];
                
                if (selectedChars[i]) {
                    const char = characters[selectedChars[i]];
                    box.innerHTML = `<strong>${nickname}</strong><br><div style="font-size: 1.2em; margin-top: 5px;">${char.name}</div>`;
                } else {
                    box.innerHTML = `<strong>${nickname}</strong><br><div style="opacity: 0.5; margin-top: 5px;">Selecting...</div>`;
                }
                
                display.appendChild(box);
            }
        }

        function selectCharacter(charKey) {
            selectedChars[currentSelectingPlayer - 1] = charKey;
            updateSelectionDisplay();

            if (currentSelectingPlayer < playerCount) {
                currentSelectingPlayer++;
                updateCurrentPlayerIndicator();
            } else {
                setTimeout(() => startBattle(), 500);
            }
        }

        // ===========================================
        // POWER-UP SYSTEM
        // ===========================================
        
        class PowerUp {
            constructor(x, y, type) {
                this.x = x;
                this.y = y;
                this.type = type;
                this.radius = 20;
                this.collected = false;
                this.bobOffset = Math.random() * Math.PI * 2;
                
                this.colors = {
                    speed: '#00ffff',
                    health: '#00ff00',
                    damage: '#ff0000',
                    shield: '#ffd700'
                };
                
                this.icons = {
                    speed: '⚡',
                    health: '❤️',
                    damage: '💥',
                    shield: '🛡️'
                };
            }

            update() {
                this.bobOffset += 0.05;
            }

            draw() {
                const bobY = Math.sin(this.bobOffset) * 5;
                
                ctx.shadowBlur = 20;
                ctx.shadowColor = this.colors[this.type];
                
                ctx.strokeStyle = this.colors[this.type];
                ctx.lineWidth = 3;
                ctx.beginPath();
                ctx.arc(this.x, this.y + bobY, this.radius, 0, Math.PI * 2);
                ctx.stroke();
                
                const gradient = ctx.createRadialGradient(
                    this.x, this.y + bobY, 0,
                    this.x, this.y + bobY, this.radius
                );
                gradient.addColorStop(0, this.colors[this.type]);
                gradient.addColorStop(1, 'transparent');
                ctx.fillStyle = gradient;
                ctx.beginPath();
                ctx.arc(this.x, this.y + bobY, this.radius, 0, Math.PI * 2);
                ctx.fill();
                
                ctx.shadowBlur = 0;
                
                ctx.font = '24px Arial';
                ctx.textAlign = 'center';
                ctx.textBaseline = 'middle';
                ctx.fillStyle = '#ffffff';
                ctx.fillText(this.icons[this.type], this.x, this.y + bobY);
            }

            checkCollision(player) {
                const dx = player.x + player.width / 2 - this.x;
                const dy = player.y + player.height / 2 - this.y;
                const distance = Math.sqrt(dx * dx + dy * dy);
                return distance < this.radius + 20;
            }

            applyEffect(player) {
                switch(this.type) {
                    case 'speed':
                        player.speedBoost = 2;
                        player.speedBoostTime = Date.now() + 5000;
                        showNotification(`⚡ ${player.nickname} - SPEED BOOST!`);
                        break;
                    case 'health':
                        player.health = Math.min(player.health + 1000, player.maxHealth);
                        showNotification(`❤️ ${player.nickname} - +1000 HP!`);
                        break;
                    case 'damage':
                        player.damageBoost = 1.5;
                        player.damageBoostTime = Date.now() + 5000;
                        showNotification(`💥 ${player.nickname} - DAMAGE BOOST!`);
                        break;
                    case 'shield':
                        player.shielded = true;
                        player.shieldTime = Date.now() + 5000;
                        showNotification(`🛡️ ${player.nickname} - SHIELD!`);
                        break;
                }
                playSound('powerup', 0.4);
            }
        }

        function spawnPowerUp() {
            if (powerUps.length >= 3 || !gameActive) return;
            
            const types = ['speed', 'health', 'damage', 'shield'];
            const type = types[Math.floor(Math.random() * types.length)];
            
            const x = 100 + Math.random() * (canvas.width - 200);
            const y = 100 + Math.random() * (canvas.height - 200);
            
            let clear = true;
            for (let obs of obstacles) {
                if (x > obs.x && x < obs.x + obs.width &&
                    y > obs.y && y < obs.y + obs.height) {
                    clear = false;
                    break;
                }
            }
            
            if (clear) {
                powerUps.push(new PowerUp(x, y, type));
            }
        }

        // FIXED: Static Bush class - NO SPINNING
        class Bush {
            constructor(x, y, radius) {
                this.x = x;
                this.y = y;
                this.radius = radius;
                this.breathe = Math.random() * Math.PI * 2;
                this.leafPositions = [];
                for (let i = 0; i < 12; i++) {
                    this.leafPositions.push({
                        angle: (Math.PI * 2 * i) / 12,
                        distance: 0.4 + Math.random() * 0.2
                    });
                }
            }

            draw() {
                this.breathe += 0.003;
                const breathAmount = 1 + Math.sin(this.breathe) * 0.02;

                // Shadow
                ctx.fillStyle = 'rgba(0, 0, 0, 0.4)';
                ctx.beginPath();
                ctx.ellipse(this.x, this.y + this.radius * 0.7, this.radius * 1.2, this.radius * 0.4, 0, 0, Math.PI * 2);
                ctx.fill();

                // Main body
                const gradient = ctx.createRadialGradient(
                    this.x - this.radius * 0.3, this.y - this.radius * 0.3, 0,
                    this.x, this.y, this.radius
                );
                gradient.addColorStop(0, '#7dc57d');
                gradient.addColorStop(0.5, '#5a9c5a');
                gradient.addColorStop(1, '#3a7a3a');
                ctx.fillStyle = gradient;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius * breathAmount, 0, Math.PI * 2);
                ctx.fill();

                // Leaf clusters - STATIC positions
                this.leafPositions.forEach((leaf, i) => {
                    const x = this.x + Math.cos(leaf.angle) * this.radius * leaf.distance;
                    const y = this.y + Math.sin(leaf.angle) * this.radius * leaf.distance;
                    const size = this.radius * 0.35;

                    const leafGrad = ctx.createRadialGradient(x - size * 0.3, y - size * 0.3, 0, x, y, size);
                    leafGrad.addColorStop(0, '#90d890');
                    leafGrad.addColorStop(0.7, '#6db56d');
                    leafGrad.addColorStop(1, '#5a9c5a');
                    ctx.fillStyle = leafGrad;
                    ctx.beginPath();
                    ctx.arc(x, y, size * breathAmount, 0, Math.PI * 2);
                    ctx.fill();
                });

                // Highlights
                for (let i = 0; i < 3; i++) {
                    const angle = (Math.PI * 2 * i) / 3 - Math.PI * 0.5;
                    const x = this.x + Math.cos(angle) * this.radius * 0.5;
                    const y = this.y + Math.sin(angle) * this.radius * 0.5;
                    
                    ctx.fillStyle = 'rgba(200, 255, 200, 0.4)';
                    ctx.beginPath();
                    ctx.arc(x, y, this.radius * 0.2, 0, Math.PI * 2);
                    ctx.fill();
                }
            }

            contains(x, y) {
                const dx = x - this.x;
                const dy = y - this.y;
                return Math.sqrt(dx * dx + dy * dy) < this.radius;
            }
        }

        // FIXED: Obstacle class with REALISTIC STONE appearance
        class Obstacle {
            constructor(x, y, width, height, type) {
                this.x = x;
                this.y = y;
                this.width = width;
                this.height = height;
                this.type = type;
                
                // Generate irregular stone shape
                if (type === 'rock') {
                    this.points = [];
                    const numPoints = 6 + Math.floor(Math.random() * 4);
                    for (let i = 0; i < numPoints; i++) {
                        const angle = (Math.PI * 2 * i) / numPoints;
                        const radius = Math.min(width, height) * (0.4 + Math.random() * 0.3);
                        this.points.push({
                            x: Math.cos(angle) * radius,
                            y: Math.sin(angle) * radius
                        });
                    }
                }
            }

            draw() {
                if (this.type === 'rock') {
                    const centerX = this.x + this.width / 2;
                    const centerY = this.y + this.height / 2;

                    // Stone shadow
                    ctx.fillStyle = 'rgba(0, 0, 0, 0.4)';
                    ctx.beginPath();
                    ctx.ellipse(centerX + 5, centerY + 8, this.width * 0.45, this.height * 0.3, 0, 0, Math.PI * 2);
                    ctx.fill();

                    // Stone body - irregular shape
                    const gradient = ctx.createRadialGradient(
                        centerX - this.width * 0.2, centerY - this.height * 0.2, 0,
                        centerX, centerY, Math.max(this.width, this.height) * 0.6
                    );
                    gradient.addColorStop(0, '#9a9a9a');
                    gradient.addColorStop(0.5, '#7a7a7a');
                    gradient.addColorStop(1, '#5a5a5a');
                    
                    ctx.fillStyle = gradient;
                    ctx.beginPath();
                    ctx.moveTo(centerX + this.points[0].x, centerY + this.points[0].y);
                    for (let i = 1; i < this.points.length; i++) {
                        ctx.lineTo(centerX + this.points[i].x, centerY + this.points[i].y);
                    }
                    ctx.closePath();
                    ctx.fill();

                    // Stone texture - cracks and details
                    ctx.strokeStyle = 'rgba(60, 60, 60, 0.5)';
                    ctx.lineWidth = 2;
                    ctx.stroke();

                    // Highlights on stone
                    ctx.fillStyle = 'rgba(160, 160, 160, 0.6)';
                    ctx.beginPath();
                    ctx.arc(centerX - this.width * 0.15, centerY - this.height * 0.15, this.width * 0.15, 0, Math.PI * 2);
                    ctx.fill();

                    ctx.fillStyle = 'rgba(140, 140, 140, 0.4)';
                    ctx.beginPath();
                    ctx.arc(centerX + this.width * 0.1, centerY + this.height * 0.1, this.width * 0.1, 0, Math.PI * 2);
                    ctx.fill();

                } else if (this.type === 'wall') {
                    // Brick wall
                    const gradient = ctx.createLinearGradient(this.x, this.y, this.x, this.y + this.height);
                    gradient.addColorStop(0, '#6a6a6a');
                    gradient.addColorStop(1, '#4a4a4a');
                    ctx.fillStyle = gradient;
                    ctx.fillRect(this.x, this.y, this.width, this.height);

                    // Brick pattern
                    ctx.strokeStyle = '#333';
                    ctx.lineWidth = 2;
                    const brickHeight = 20;
                    for (let y = 0; y < this.height; y += brickHeight) {
                        ctx.beginPath();
                        ctx.moveTo(this.x, this.y + y);
                        ctx.lineTo(this.x + this.width, this.y + y);
                        ctx.stroke();
                        
                        const offset = (y / brickHeight) % 2 === 0 ? 0 : this.width / 2;
                        for (let x = offset; x < this.width; x += this.width / 2) {
                            ctx.beginPath();
                            ctx.moveTo(this.x + x, this.y + y);
                            ctx.lineTo(this.x + x, this.y + y + brickHeight);
                            ctx.stroke();
                        }
                    }
                }
            }

            collidesWith(x, y, w, h) {
                return x < this.x + this.width &&
                       x + w > this.x &&
                       y < this.y + this.height &&
                       y + h > this.y;
            }
        }

        // FIXED: Generate STATIC background once
        function generateStaticBackground() {
            const offCanvas = document.createElement('canvas');
            offCanvas.width = canvas.width;
            offCanvas.height = canvas.height;
            const offCtx = offCanvas.getContext('2d');

            // Ground gradient
            const gradient = offCtx.createLinearGradient(0, 0, canvas.width, canvas.height);
            gradient.addColorStop(0, '#3a5a3a');
            gradient.addColorStop(0.5, '#2a4a2a');
            gradient.addColorStop(1, '#1a3a1a');
            offCtx.fillStyle = gradient;
            offCtx.fillRect(0, 0, canvas.width, canvas.height);

            // Dirt patches
            offCtx.fillStyle = 'rgba(60, 40, 20, 0.3)';
            for (let i = 0; i < 30; i++) {
                const x = Math.random() * canvas.width;
                const y = Math.random() * canvas.height;
                const size = 20 + Math.random() * 40;
                offCtx.beginPath();
                offCtx.ellipse(x, y, size, size * 0.6, Math.random() * Math.PI, 0, Math.PI * 2);
                offCtx.fill();
            }

            // STATIC grass - pre-rendered
            const grassTypes = [
                { color: 'rgba(50, 90, 50, 0.4)', width: 1, count: 800 },
                { color: 'rgba(80, 120, 80, 0.5)', width: 1.5, count: 600 },
                { color: 'rgba(120, 180, 120, 0.6)', width: 2, count: 400 }
            ];

            grassTypes.forEach(grass => {
                offCtx.strokeStyle = grass.color;
                offCtx.lineWidth = grass.width;
                for (let i = 0; i < grass.count; i++) {
                    const x = Math.random() * canvas.width;
                    const y = Math.random() * canvas.height;
                    const height = 4 + Math.random() * 10;
                    const bend = (Math.random() - 0.5) * 4;
                    
                    offCtx.beginPath();
                    offCtx.moveTo(x, y);
                    offCtx.quadraticCurveTo(x + bend, y - height * 0.5, x + bend * 2, y - height);
                    offCtx.stroke();
                }
            });

            // Flowers
            const flowers = ['rgba(255, 200, 50, 0.7)', 'rgba(200, 100, 255, 0.6)', 'rgba(255, 150, 150, 0.6)'];
            for (let i = 0; i < 50; i++) {
                offCtx.fillStyle = flowers[Math.floor(Math.random() * flowers.length)];
                offCtx.beginPath();
                offCtx.arc(Math.random() * canvas.width, Math.random() * canvas.height, 2 + Math.random() * 2, 0, Math.PI * 2);
                offCtx.fill();
            }

            staticBackgroundCanvas = offCanvas;
        }

        function generateTerrain() {
            obstacles = [];
            bushes = [];

            // Rocks
            for (let i = 0; i < 12; i++) {
                obstacles.push(new Obstacle(
                    100 + Math.random() * (canvas.width - 250),
                    100 + Math.random() * (canvas.height - 250),
                    40 + Math.random() * 40,
                    40 + Math.random() * 40,
                    'rock'
                ));
            }

            // Walls
            obstacles.push(new Obstacle(canvas.width / 2 - 30, 150, 60, 200, 'wall'));
            obstacles.push(new Obstacle(canvas.width / 2 - 30, canvas.height - 350, 60, 200, 'wall'));
            obstacles.push(new Obstacle(200, canvas.height / 2 - 30, 150, 60, 'wall'));
            obstacles.push(new Obstacle(canvas.width - 350, canvas.height / 2 - 30, 150, 60, 'wall'));

            // Bushes
            for (let i = 0; i < 15; i++) {
                bushes.push(new Bush(
                    80 + Math.random() * (canvas.width - 160),
                    80 + Math.random() * (canvas.height - 160),
                    35 + Math.random() * 25
                ));
            }
        }

        class Particle {
            constructor(x, y, color, size, vx, vy) {
                this.x = x;
                this.y = y;
                this.color = color;
                this.size = size;
                this.vx = vx;
                this.vy = vy;
                this.life = 1;
            }

            update() {
                this.x += this.vx;
                this.y += this.vy;
                this.life -= 0.02;
                this.size *= 0.96;
            }

            draw() {
                ctx.globalAlpha = this.life;
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
                ctx.globalAlpha = 1;
            }
        }

        function createExplosion(x, y, color, count = 20) {
            for (let i = 0; i < count; i++) {
                const angle = (Math.PI * 2 * i) / count;
                const speed = 2 + Math.random() * 3;
                particles.push(new Particle(
                    x, y, color, 3 + Math.random() * 3,
                    Math.cos(angle) * speed,
                    Math.sin(angle) * speed
                ));
            }
        }

        class Bullet {
            constructor(x, y, angle, damage, color, owner) {
                this.x = x;
                this.y = y;
                this.angle = angle;
                this.vx = Math.cos(angle) * 12;
                this.vy = Math.sin(angle) * 12;
                this.damage = damage;
                this.color = color;
                this.owner = owner;
                this.radius = 5;
                this.distance = 0;
                this.maxDistance = 400;
            }

            update() {
                this.x += this.vx;
                this.y += this.vy;
                this.distance += Math.sqrt(this.vx * this.vx + this.vy * this.vy);
            }

            draw() {
                ctx.fillStyle = this.color;
                ctx.shadowBlur = 15;
                ctx.shadowColor = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.fill();
                ctx.shadowBlur = 0;
                ctx.strokeStyle = '#fff';
                ctx.lineWidth = 2;
                ctx.stroke();
            }

            isExpired() {
                return this.distance > this.maxDistance ||
                       this.x < 0 || this.x > canvas.width ||
                       this.y < 0 || this.y > canvas.height;
            }

            hitsObstacle() {
                for (let obs of obstacles) {
                    if (this.x > obs.x && this.x < obs.x + obs.width &&
                        this.y > obs.y && this.y < obs.y + obs.height) {
                        return true;
                    }
                }
                return false;
            }
        }

        // FIXED: BattlePlayer with HUMANOID character design
        class BattlePlayer {
            constructor(x, y, charKey, controls, id, color) {
                const char = characters[charKey];
                this.x = x;
                this.y = y;
                this.width = 35;
                this.height = 50;
                this.char = char;
                this.speed = char.speed;
                this.baseSpeed = char.speed;
                this.health = char.health;
                this.maxHealth = char.health;
                this.damage = char.damage;
                this.baseDamage = char.damage;
                this.color = color;
                this.controls = controls;
                this.id = id;
                this.bullets = [];
                this.canShoot = true;
                this.angle = 0;
                this.kills = 0;
                this.alive = true;
                this.hidden = false;
                this.nickname = '';
                
                // Power-up effects
                this.speedBoost = 1;
                this.speedBoostTime = 0;
                this.damageBoost = 1;
                this.damageBoostTime = 0;
                this.shielded = false;
                this.shieldTime = 0;
            }

            updatePowerUps() {
                const now = Date.now();
                
                // Speed boost
                if (now > this.speedBoostTime) {
                    this.speedBoost = 1;
                } else {
                    this.speed = this.baseSpeed * this.speedBoost;
                }
                
                // Damage boost
                if (now > this.damageBoostTime) {
                    this.damageBoost = 1;
                }
                
                // Shield
                if (now > this.shieldTime) {
                    this.shielded = false;
                }
            }

            move() {
                const newPos = { x: this.x, y: this.y };
                
                const currentSpeed = this.baseSpeed * this.speedBoost;
                
                if (keys[this.controls.up]) newPos.y -= currentSpeed;
                if (keys[this.controls.down]) newPos.y += currentSpeed;
                if (keys[this.controls.left]) newPos.x -= currentSpeed;
                if (keys[this.controls.right]) newPos.x += this.speed;

                let canMove = true;
                for (let obs of obstacles) {
                    if (obs.collidesWith(newPos.x, newPos.y, this.width, this.height)) {
                        canMove = false;
                        break;
                    }
                }

                if (canMove) {
                    this.x = Math.max(0, Math.min(canvas.width - this.width, newPos.x));
                    this.y = Math.max(0, Math.min(canvas.height - this.height, newPos.y));
                }

                this.hidden = false;
                for (let bush of bushes) {
                    if (bush.contains(this.x + this.width / 2, this.y + this.height / 2)) {
                        this.hidden = true;
                        break;
                    }
                }
            }

            updateAngle(players) {
                let closestDist = Infinity;
                let closestPlayer = null;

                for (let p of players) {
                    if (p.id !== this.id && p.alive) {
                        const dx = (p.x + p.width / 2) - (this.x + this.width / 2);
                        const dy = (p.y + p.height / 2) - (this.y + this.height / 2);
                        const dist = Math.sqrt(dx * dx + dy * dy);
                        if (dist < closestDist) {
                            closestDist = dist;
                            closestPlayer = p;
                        }
                    }
                }

                if (closestPlayer) {
                    const dx = (closestPlayer.x + closestPlayer.width / 2) - (this.x + this.width / 2);
                    const dy = (closestPlayer.y + closestPlayer.height / 2) - (this.y + this.height / 2);
                    this.angle = Math.atan2(dy, dx);
                }
            }

            shoot() {
                if (keys[this.controls.shoot] && this.canShoot && gameActive && !this.hidden) {
                    const bulletDamage = this.baseDamage * this.damageBoost;
                    
                    this.bullets.push(new Bullet(
                        this.x + this.width / 2,
                        this.y + this.height / 2,
                        this.angle,
                        bulletDamage,
                        this.color,
                        this.id
                    ));

                    playSound('shoot', 0.2);
                    this.canShoot = false;
                    setTimeout(() => this.canShoot = true, 400);
                }
            }

            updateBullets(players) {
                this.bullets = this.bullets.filter(bullet => {
                    bullet.update();

                    if (bullet.hitsObstacle()) {
                        createExplosion(bullet.x, bullet.y, bullet.color, 10);
                        return false;
                    }

                    for (let p of players) {
                        if (p.id !== this.id && p.alive && !p.hidden &&
                            bullet.x > p.x && bullet.x < p.x + p.width &&
                            bullet.y > p.y && bullet.y < p.y + p.height) {
                            
                            // Apply damage (reduced if shielded)
                            const damage = p.shielded ? bullet.damage * 0.2 : bullet.damage;
                            p.health -= damage;
                            
                            createExplosion(bullet.x, bullet.y, bullet.color, 15);
                            playSound(p.shielded ? 'powerup' : 'hit', 0.3);
                            
                            if (p.health <= 0) {
                                p.alive = false;
                                this.kills++;
                                createExplosion(p.x + p.width / 2, p.y + p.height / 2, p.color, 40);
                                playSound('kill', 0.4);
                                
                                // Add to kill feed
                                addKillMessage(this, p);
                                checkCombo();
                                
                                showNotification(`💀 ${this.nickname} eliminated ${p.nickname}!`);
                            }
                            
                            return false;
                        }
                    }

                    return !bullet.isExpired();
                });
            }

            // FIXED: HUMANOID character drawing - NOT a dot!
            draw() {
                if (!this.alive) return;

                const alpha = this.hidden ? 0.3 : 1;
                ctx.globalAlpha = alpha;

                const centerX = this.x + this.width / 2;
                const centerY = this.y + this.height / 2;

                ctx.save();
                ctx.translate(centerX, centerY);

                // Body (torso)
                const bodyGradient = ctx.createLinearGradient(0, -10, 0, 15);
                bodyGradient.addColorStop(0, this.color);
                bodyGradient.addColorStop(1, this.adjustColor(this.color, -40));
                ctx.fillStyle = bodyGradient;
                ctx.fillRect(-8, -5, 16, 20);

                // Head
                const headGradient = ctx.createRadialGradient(0, -18, 2, 0, -18, 10);
                headGradient.addColorStop(0, this.adjustColor(this.color, 60));
                headGradient.addColorStop(1, this.adjustColor(this.color, 20));
                ctx.fillStyle = headGradient;
                ctx.beginPath();
                ctx.arc(0, -18, 10, 0, Math.PI * 2);
                ctx.fill();

                // Head outline
                ctx.strokeStyle = '#ffffff';
                ctx.lineWidth = 2;
                ctx.stroke();

                // Eyes
                ctx.fillStyle = '#ffffff';
                ctx.fillRect(-4, -20, 3, 3);
                ctx.fillRect(1, -20, 3, 3);

                // Pupils
                ctx.fillStyle = '#000';
                ctx.fillRect(-3, -19, 1, 1);
                ctx.fillRect(2, -19, 1, 1);

                // Arms
                ctx.strokeStyle = this.adjustColor(this.color, -20);
                ctx.lineWidth = 4;
                ctx.lineCap = 'round';
                
                // Left arm
                ctx.beginPath();
                ctx.moveTo(-8, -2);
                ctx.lineTo(-14, 8);
                ctx.stroke();
                
                // Right arm (pointing gun direction)
                ctx.beginPath();
                ctx.moveTo(8, -2);
                const armEndX = Math.cos(this.angle) * 16;
                const armEndY = Math.sin(this.angle) * 16;
                ctx.lineTo(armEndX, armEndY);
                ctx.stroke();

                // Legs
                ctx.strokeStyle = this.adjustColor(this.color, -30);
                ctx.lineWidth = 4;
                
                // Left leg
                ctx.beginPath();
                ctx.moveTo(-4, 15);
                ctx.lineTo(-6, 25);
                ctx.stroke();
                
                // Right leg
                ctx.beginPath();
                ctx.moveTo(4, 15);
                ctx.lineTo(6, 25);
                ctx.stroke();

                // Gun
                ctx.strokeStyle = '#333';
                ctx.lineWidth = 5;
                ctx.beginPath();
                ctx.moveTo(armEndX * 0.7, armEndY * 0.7);
                ctx.lineTo(Math.cos(this.angle) * 25, Math.sin(this.angle) * 25);
                ctx.stroke();

                // Gun barrel highlight
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.arc(Math.cos(this.angle) * 25, Math.sin(this.angle) * 25, 3, 0, Math.PI * 2);
                ctx.fill();

                ctx.restore();
                ctx.globalAlpha = 1;
                
                // Draw power-up effects
                if (this.speedBoost > 1) {
                    // Speed boost aura
                    ctx.strokeStyle = '#00ffff';
                    ctx.lineWidth = 3;
                    ctx.setLineDash([5, 5]);
                    ctx.beginPath();
                    ctx.arc(centerX, centerY, 30, 0, Math.PI * 2);
                    ctx.stroke();
                    ctx.setLineDash([]);
                }
                
                if (this.damageBoost > 1) {
                    // Damage boost aura
                    ctx.strokeStyle = '#ff0000';
                    ctx.lineWidth = 2;
                    ctx.beginPath();
                    ctx.arc(centerX, centerY, 35, 0, Math.PI * 2);
                    ctx.stroke();
                }
                
                if (this.shielded) {
                    // Shield bubble
                    ctx.strokeStyle = '#ffd700';
                    ctx.lineWidth = 3;
                    ctx.shadowBlur = 15;
                    ctx.shadowColor = '#ffd700';
                    ctx.beginPath();
                    ctx.arc(centerX, centerY, 40, 0, Math.PI * 2);
                    ctx.stroke();
                    ctx.shadowBlur = 0;
                }
            }

            adjustColor(color, amount) {
                const num = parseInt(color.replace('#', ''), 16);
                const r = Math.max(0, Math.min(255, (num >> 16) + amount));
                const g = Math.max(0, Math.min(255, ((num >> 8) & 0x00FF) + amount));
                const b = Math.max(0, Math.min(255, (num & 0x0000FF) + amount));
                return '#' + ((r << 16) | (g << 8) | b).toString(16).padStart(6, '0');
            }

            drawBullets() {
                this.bullets.forEach(bullet => bullet.draw());
            }
        }

        function startBattle() {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            canvas.style.display = 'block';
            document.getElementById('gameHud').style.display = 'block';

            // Generate static background ONCE
            generateStaticBackground();
            generateTerrain();

            const startPositions = [
                [100, 100],
                [canvas.width - 150, 100],
                [100, canvas.height - 150],
                [canvas.width - 150, canvas.height - 150]
            ];

            const controls = [
                { up: 'w', down: 's', left: 'a', right: 'd', shoot: 'q' },
                { up: 't', down: 'g', left: 'f', right: 'h', shoot: 'r' },
                { up: 'i', down: 'k', left: 'j', right: 'l', shoot: 'u' },
                { up: 'ArrowUp', down: 'ArrowDown', left: 'ArrowLeft', right: 'ArrowRight', shoot: 'Enter' }
            ];

            players = [];
            const hudGrid = document.getElementById('hudGrid');
            hudGrid.innerHTML = '';

            for (let i = 0; i < playerCount; i++) {
                players.push(new BattlePlayer(
                    startPositions[i][0],
                    startPositions[i][1],
                    selectedChars[i],
                    controls[i],
                    i + 1,
                    playerColors[i]
                ));

                const nickname = playerNicknames[i] || playerNames[i];
                const hud = document.createElement('div');
                hud.className = 'player-hud player' + (i + 1) + '-hud';
                hud.innerHTML = `
                    <div class="hud-name">${nickname}: ${characters[selectedChars[i]].name}</div>
                    <div class="health-bar-container">
                        <div class="health-bar" id="p${i + 1}Health" style="width: 100%; background: ${playerColors[i]};"></div>
                        <div class="health-text" id="p${i + 1}HealthText">${characters[selectedChars[i]].health}</div>
                    </div>
                    <div style="font-size: 0.8em;">Kills: <span id="p${i + 1}Kills">0</span></div>
                `;
                hudGrid.appendChild(hud);
            }

            const controlTexts = ['WASD + Q', 'TFGH + R', 'IJKL + U', 'Arrows + ENTER'];
            let controlsHTML = '<strong>CONTROLS: </strong>';
            for (let i = 0; i < playerCount; i++) {
                const nickname = playerNicknames[i] || playerNames[i];
                controlsHTML += `${nickname}: ${controlTexts[i]}${i < playerCount - 1 ? ' | ' : ''}`;
            }
            document.getElementById('controlsDisplay').innerHTML = controlsHTML;

            gameActive = true;
            particles = [];
            powerUps = [];
            comboCount = 0;
            gameStartTime = Date.now();
            
            // Show kill feed
            document.getElementById('killFeed').style.display = 'block';
            
            // Spawn power-ups periodically
            const powerUpInterval = setInterval(() => {
                if (gameActive) spawnPowerUp();
            }, 8000);
            
            // Initial power-ups
            setTimeout(() => spawnPowerUp(), 3000);
            setTimeout(() => spawnPowerUp(), 5000);
            
            // Store nickname on player
            players.forEach((p, i) => {
                p.nickname = playerNicknames[i] || playerNames[i];
            });
            
            showNotification('⚔️ BATTLE START! ⚔️');
            playSound('ultimate', 0.5);
            
            battleLoop();
        }

        function updateBattleHUD() {
            players.forEach((p, i) => {
                const idx = i + 1;
                document.getElementById(`p${idx}Health`).style.width = 
                    Math.max(0, (p.health / p.maxHealth) * 100) + '%';
                document.getElementById(`p${idx}HealthText`).textContent = 
                    Math.max(0, Math.round(p.health));
                document.getElementById(`p${idx}Kills`).textContent = p.kills;
                
                // Update power-up status
                let status = [];
                if (p.speedBoost > 1) status.push('⚡ SPEED');
                if (p.damageBoost > 1) status.push('💥 DAMAGE');
                if (p.shielded) status.push('🛡️ SHIELD');
                
                const statusEl = document.getElementById(`p${idx}Status`);
                if (statusEl) {
                    statusEl.textContent = status.join(' | ');
                    statusEl.style.color = status.length > 0 ? '#ffd700' : '#666';
                }
            });
        }

        function checkBattleGameOver() {
            const alivePlayers = players.filter(p => p.alive);
            
            if (alivePlayers.length === 1) {
                gameActive = false;
                setTimeout(() => showBattleGameOver(alivePlayers[0]), 1000);
            }
        }

        function showBattleGameOver(winner) {
            const winnerNickname = playerNicknames[winner.id - 1] || playerNames[winner.id - 1];
            document.getElementById('winnerText').textContent = `${winnerNickname} WINS!`;
            document.getElementById('winnerText').style.color = winner.color;
            
            // Play victory sound
            playSound('ultimate', 0.6);
            
            // Calculate game time
            const gameTime = Math.floor((Date.now() - gameStartTime) / 1000);
            const minutes = Math.floor(gameTime / 60);
            const seconds = gameTime % 60;
            
            let stats = `<div style="font-size: 0.8em; margin-bottom: 20px;">⏱️ Game Time: ${minutes}:${seconds.toString().padStart(2, '0')}</div>`;
            stats += '<div style="margin-bottom: 15px; font-size: 1.2em; color: #ffd700;">🏆 FINAL STANDINGS 🏆</div>';
            
            players.sort((a, b) => {
                if (a.alive && !b.alive) return -1;
                if (!a.alive && b.alive) return 1;
                return b.kills - a.kills;
            }).forEach((p, i) => {
                const nickname = playerNicknames[p.id - 1] || playerNames[p.id - 1];
                const medal = ['🥇', '🥈', '🥉', ''][i] || '';
                stats += `<div style="margin: 10px 0; font-size: 1.1em;">${medal} ${i + 1}. <strong style="color: ${p.color}">${nickname}</strong>: ${p.kills} kills</div>`;
            });
            
            document.getElementById('finalStats').innerHTML = stats;
            document.getElementById('gameOverScreen').classList.add('show');
            
            // Hide kill feed
            document.getElementById('killFeed').style.display = 'none';
            
            // Celebration notification
            showNotification(`🎉 ${winnerNickname} IS VICTORIOUS! 🎉`);
        }

        function battleLoop() {
            if (!gameActive) return;

            // Draw STATIC background (no random grass!)
            ctx.drawImage(staticBackgroundCanvas, 0, 0);

            obstacles.forEach(obs => obs.draw());
            bushes.forEach(bush => bush.draw());

            // Draw and update power-ups
            powerUps = powerUps.filter(powerUp => {
                if (powerUp.collected) return false;
                
                powerUp.update();
                powerUp.draw();
                
                // Check collision with players
                players.forEach(p => {
                    if (p.alive && powerUp.checkCollision(p)) {
                        powerUp.applyEffect(p);
                        powerUp.collected = true;
                    }
                });
                
                return !powerUp.collected;
            });

            particles = particles.filter(p => {
                p.update();
                p.draw();
                return p.life > 0;
            });

            players.forEach(p => {
                if (p.alive) {
                    p.move();
                    p.updateAngle(players);
                    p.shoot();
                    p.updateBullets(players);
                    p.updatePowerUps(); // Update power-up effects
                }
            });

            players.forEach(p => p.drawBullets());
            players.forEach(p => p.draw());

            updateBattleHUD();
            checkBattleGameOver();

            requestAnimationFrame(battleLoop);
        }

        // Cart Racing
        class RacerCart {
            constructor(x, y, controls, id, color, name) {
                this.x = x;
                this.y = y;
                this.width = 40;
                this.height = 60;
                this.speed = 0;
                this.maxSpeed = 8;
                this.acceleration = 0.3;
                this.friction = 0.95;
                this.angle = 0;
                this.turnSpeed = 0.08;
                this.controls = controls;
                this.id = id;
                this.color = color;
                this.name = name;
                this.lap = 0;
                this.checkpoints = [false, false, false];
                this.finished = false;
                this.finishTime = 0;
                this.finishPlace = 0;
            }

            move() {
                if (this.finished) return;

                if (keys[this.controls.up]) {
                    this.speed = Math.min(this.maxSpeed, this.speed + this.acceleration);
                }
                if (keys[this.controls.down]) {
                    this.speed = Math.max(-this.maxSpeed / 2, this.speed - this.acceleration);
                }

                if (keys[this.controls.left]) {
                    this.angle -= this.turnSpeed * (this.speed / this.maxSpeed);
                }
                if (keys[this.controls.right]) {
                    this.angle += this.turnSpeed * (this.speed / this.maxSpeed);
                }

                this.speed *= this.friction;

                this.x += Math.sin(this.angle) * this.speed;
                this.y -= Math.cos(this.angle) * this.speed;

                this.x = Math.max(50, Math.min(canvas.width - 50, this.x));
                this.y = Math.max(50, Math.min(canvas.height - 50, this.y));
            }

            draw() {
                ctx.save();
                ctx.translate(this.x, this.y);
                ctx.rotate(this.angle);

                // Shadow
                ctx.fillStyle = 'rgba(0, 0, 0, 0.4)';
                ctx.fillRect(-this.width / 2 + 3, -this.height / 2 + 3, this.width, this.height);

                // Body
                const gradient = ctx.createLinearGradient(0, -this.height / 2, 0, this.height / 2);
                gradient.addColorStop(0, this.color);
                gradient.addColorStop(0.5, '#ffffff');
                gradient.addColorStop(1, this.color);
                ctx.fillStyle = gradient;
                ctx.fillRect(-this.width / 2, -this.height / 2, this.width, this.height);

                ctx.strokeStyle = '#222';
                ctx.lineWidth = 3;
                ctx.strokeRect(-this.width / 2, -this.height / 2, this.width, this.height);

                // Wheels
                ctx.fillStyle = '#333';
                ctx.fillRect(-this.width / 2 - 5, -this.height / 2 + 5, 8, 15);
                ctx.fillRect(this.width / 2 - 3, -this.height / 2 + 5, 8, 15);
                ctx.fillRect(-this.width / 2 - 5, this.height / 2 - 20, 8, 15);
                ctx.fillRect(this.width / 2 - 3, this.height / 2 - 20, 8, 15);

                // Driver
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.arc(0, -5, 10, 0, Math.PI * 2);
                ctx.fill();

                ctx.restore();

                // Name
                ctx.fillStyle = this.color;
                ctx.font = 'bold 14px Arial';
                ctx.textAlign = 'center';
                ctx.fillText(this.name, this.x, this.y - 40);
            }
        }

        let racers = [];
        let checkpoints = [];
        let raceStartTime = 0;
        let finishOrder = [];

        function startCartRace(count) {
            playerCount = count;
            selectedChars = [];
            playerNicknames = new Array(count).fill(null);
            currentSelectingPlayer = 1;
            gameMode = 'race';
            showNicknameScreen();
        }

        function startCartRaceAfterNicknames() {
            const charKeys = Object.keys(characters);
            for (let i = 0; i < playerCount; i++) {
                selectedChars.push(charKeys[i % charKeys.length]);
            }

            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            canvas.style.display = 'block';
            document.getElementById('gameHud').style.display = 'block';

            const controls = [
                { up: 'w', down: 's', left: 'a', right: 'd' },
                { up: 't', down: 'g', left: 'f', right: 'h' },
                { up: 'i', down: 'k', left: 'j', right: 'l' },
                { up: 'ArrowUp', down: 'ArrowDown', left: 'ArrowLeft', right: 'ArrowRight' }
            ];

            racers = [];
            const startX = 200;
            const startY = canvas.height / 2;
            const spacing = 70;

            for (let i = 0; i < playerCount; i++) {
                const nickname = playerNicknames[i] || playerNames[i];
                racers.push(new RacerCart(
                    startX,
                    startY + (i - playerCount / 2) * spacing,
                    controls[i],
                    i + 1,
                    playerColors[i],
                    nickname
                ));
            }

            checkpoints = [
                { x: canvas.width / 2, y: 150, radius: 60, id: 0 },
                { x: canvas.width - 200, y: canvas.height / 2, radius: 60, id: 1 },
                { x: canvas.width / 2, y: canvas.height - 150, radius: 60, id: 2 },
            ];

            const hudGrid = document.getElementById('hudGrid');
            hudGrid.innerHTML = '';

            for (let i = 0; i < playerCount; i++) {
                const nickname = playerNicknames[i] || playerNames[i];
                const hud = document.createElement('div');
                hud.className = 'player-hud player' + (i + 1) + '-hud';
                hud.innerHTML = `
                    <div class="hud-name">${nickname}</div>
                    <div style="font-size: 1.2em; margin: 5px 0;">Lap: <span id="p${i + 1}Lap">0</span>/3</div>
                    <div style="font-size: 0.9em;" id="p${i + 1}Status">Racing...</div>
                `;
                hudGrid.appendChild(hud);
            }

            const controlTexts = ['WASD', 'TFGH', 'IJKL', 'Arrows'];
            let controlsHTML = '<div style="font-size: 1.1em;"><strong>COMPLETE 3 LAPS!</strong></div><div>';
            for (let i = 0; i < playerCount; i++) {
                const nickname = playerNicknames[i] || playerNames[i];
                controlsHTML += `${nickname}: ${controlTexts[i]}${i < playerCount - 1 ? ' | ' : ''}`;
            }
            controlsHTML += '</div>';
            document.getElementById('controlsDisplay').innerHTML = controlsHTML;

            gameActive = true;
            raceStartTime = Date.now();
            finishOrder = [];
            raceLoop();
        }

        function drawRaceTrack() {
            const gradient = ctx.createLinearGradient(0, 0, canvas.width, canvas.height);
            gradient.addColorStop(0, '#4a6a4a');
            gradient.addColorStop(1, '#2a4a2a');
            ctx.fillStyle = gradient;
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            // Track
            ctx.strokeStyle = '#888';
            ctx.lineWidth = 150;
            ctx.beginPath();
            ctx.moveTo(200, canvas.height / 2);
            ctx.lineTo(canvas.width / 2, 150);
            ctx.lineTo(canvas.width - 200, canvas.height / 2);
            ctx.lineTo(canvas.width / 2, canvas.height - 150);
            ctx.closePath();
            ctx.stroke();

            ctx.strokeStyle = '#aaa';
            ctx.lineWidth = 140;
            ctx.stroke();

            // Borders
            ctx.strokeStyle = '#fff';
            ctx.lineWidth = 4;
            ctx.stroke();

            // Center line
            ctx.strokeStyle = '#ff0';
            ctx.lineWidth = 4;
            ctx.setLineDash([30, 30]);
            ctx.stroke();
            ctx.setLineDash([]);

            // Checkpoints
            checkpoints.forEach((cp, i) => {
                const color = i === 0 ? '#0f0' : '#f60';
                ctx.fillStyle = i === 0 ? 'rgba(0,255,0,0.3)' : 'rgba(255,100,0,0.3)';
                ctx.beginPath();
                ctx.arc(cp.x, cp.y, cp.radius, 0, Math.PI * 2);
                ctx.fill();
                
                ctx.strokeStyle = color;
                ctx.lineWidth = 5;
                ctx.stroke();

                ctx.fillStyle = '#fff';
                ctx.font = 'bold 30px Impact';
                ctx.textAlign = 'center';
                ctx.fillText(i === 0 ? 'START' : 'CP' + i, cp.x, cp.y + 10);
            });
        }

        function updateRaceCheckpoints() {
            racers.forEach(racer => {
                if (racer.finished) return;

                checkpoints.forEach(cp => {
                    const dx = racer.x - cp.x;
                    const dy = racer.y - cp.y;
                    const dist = Math.sqrt(dx * dx + dy * dy);

                    if (dist < cp.radius) {
                        if (cp.id === 0) {
                            const allHit = racer.checkpoints.every(c => c);
                            if (allHit) {
                                racer.lap++;
                                racer.checkpoints = [false, false, false];
                                
                                if (racer.lap >= 3) {
                                    racer.finished = true;
                                    racer.finishTime = ((Date.now() - raceStartTime) / 1000).toFixed(2);
                                    racer.finishPlace = finishOrder.length + 1;
                                    finishOrder.push(racer);
                                }
                            }
                        } else {
                            racer.checkpoints[cp.id] = true;
                        }
                    }
                });
            });
        }

        function updateRaceHUD() {
            racers.forEach((racer, i) => {
                document.getElementById(`p${i + 1}Lap`).textContent = racer.lap;
                
                if (racer.finished) {
                    document.getElementById(`p${i + 1}Status`).innerHTML = 
                        `<strong>FINISHED #${racer.finishPlace}!</strong><br>${racer.finishTime}s`;
                } else {
                    const cpHit = racer.checkpoints.filter(c => c).length;
                    document.getElementById(`p${i + 1}Status`).textContent = `CP: ${cpHit}/2`;
                }
            });
        }

        function checkRaceGameOver() {
            if (racers.filter(r => r.finished).length === playerCount) {
                gameActive = false;
                setTimeout(() => showRaceGameOver(), 1000);
            }
        }

        function showRaceGameOver() {
            document.getElementById('winnerText').textContent = `${finishOrder[0].name} WINS!`;
            document.getElementById('winnerText').style.color = finishOrder[0].color;
            
            let stats = '<div>RACE RESULTS:</div>';
            finishOrder.forEach((racer, i) => {
                stats += `<div>${i + 1}. ${racer.name} - ${racer.finishTime}s</div>`;
            });
            document.getElementById('finalStats').innerHTML = stats;
            
            document.getElementById('gameOverScreen').classList.add('show');
        }

        function raceLoop() {
            if (!gameActive) return;

            drawRaceTrack();
            racers.forEach(r => r.move());
            updateRaceCheckpoints();
            racers.forEach(r => r.draw());
            updateRaceHUD();
            checkRaceGameOver();

            requestAnimationFrame(raceLoop);
        }

        function returnToMainMenu() {
            document.getElementById('gameOverScreen').classList.remove('show');
            document.getElementById('gameHud').style.display = 'none';
            document.getElementById('killFeed').style.display = 'none';
            canvas.style.display = 'none';
            showMainMenu();
            gameActive = false;
            staticBackgroundCanvas = null;
            powerUps = [];
            particles = [];
            comboCount = 0;
        }

        document.addEventListener('keydown', (e) => {
            keys[e.key] = true;
            
            if (document.activeElement.tagName === 'INPUT') return;
            
            if (['ArrowUp', 'ArrowDown', 'ArrowLeft', 'ArrowRight', ' ', 'w', 'a', 's', 'd', 
                 't', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'q', 'r', 'u', 'Enter'].includes(e.key)) {
                e.preventDefault();
            }
        });

        document.addEventListener('keyup', (e) => {
            keys[e.key] = false;
        });
    </script>
</body>
</html>
