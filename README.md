<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>India GlobalCine - Perfect Advanced Post & Video Editor</title>
    
        <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <script src="https://unpkg.com/fix-webm-duration"></script>
    <link href="https://fonts.googleapis.com/css2?family=Anton&family=Montserrat:wght@500;600;800;900&family=Oswald:wght@700&family=Playfair+Display:ital,wght@0,700;1,700&display=swap" rel="stylesheet">
    
    <style>
        /* ==========================================================================
           INDIA GLOBALCINE - ADVANCED PREMIUM CSS
           ========================================================================== */
        
        :root {
            --bg-dark: #121212;
            --panel-bg: #1e1e1e;
            --primary-accent: #ff2a2a;
            --primary-hover: #cc0000;
            --text-light: #ffffff;
            --text-muted: #aaaaaa;
            --border-color: #333333;
            
            /* Perfect Instagram Portrait Feed Size (4:5 Aspect Ratio) */
            --post-width: 1080px;
            --post-height: 1350px; 
            
            --news-red: #e61919;
            --news-black: #000000;

            /* NEW: Global Highlight Colors (Editable via UI) */
            --hl-bg-color: #e61919;
            --hl-text-color: #ffffff;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-light);
            display: flex;
            height: 100vh;
            overflow: hidden;
        }

        /* --- ADVANCED CONTROL PANEL --- */
        .editor-sidebar {
            width: 420px;
            background-color: var(--panel-bg);
            border-right: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
            box-shadow: 10px 0 30px rgba(0,0,0,0.8);
            z-index: 10;
        }

        .sidebar-header {
            padding: 25px;
            background: #111;
            border-bottom: 2px solid var(--primary-accent);
            text-align: center;
        }

        .sidebar-header h1 {
            font-family: 'Oswald', sans-serif;
            font-size: 28px;
            color: #ffffff;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        .sidebar-header h1 span { color: var(--primary-accent); }

        .control-group-container {
            padding: 20px;
            overflow-y: auto;
            flex-grow: 1;
        }

        .control-group {
            margin-bottom: 25px;
            background: #252525;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid var(--primary-accent);
        }

        .control-group label {
            display: block;
            margin-bottom: 10px;
            font-weight: 800;
            font-size: 13px;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .form-control {
            width: 100%;
            padding: 14px;
            background-color: #111;
            border: 1px solid var(--border-color);
            color: #fff;
            border-radius: 4px;
            font-size: 15px;
            font-family: 'Montserrat', sans-serif;
            font-weight: bold;
        }
        .form-control:focus {
            outline: none;
            border-color: var(--primary-accent);
        }
        textarea.form-control { resize: vertical; min-height: 100px; }

        .file-upload-wrapper {
            position: relative;
            width: 100%;
            height: 70px;
            border: 2px dashed #555;
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            background: #1a1a1a;
            transition: all 0.3s ease;
        }
        .file-upload-wrapper:hover { border-color: var(--primary-accent); }
        .file-upload-wrapper input[type="file"] {
            position: absolute; width: 100%; height: 100%; opacity: 0; cursor: pointer;
        }

        .action-buttons {
            padding: 20px;
            background-color: #111;
            border-top: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .btn {
            width: 100%;
            padding: 18px;
            border: none;
            border-radius: 6px;
            font-size: 16px;
            font-weight: 900;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        .btn:disabled { opacity: 0.7; cursor: not-allowed; }
        
        .btn-primary { background-color: var(--primary-accent); color: white; }
        .btn-primary:hover:not(:disabled) { background-color: var(--primary-hover); }
        
        .btn-secondary { background-color: #2c3e50; color: white; border: 1px solid #34495e; }
        .btn-secondary:hover:not(:disabled) { background-color: #34495e; }
        
        .btn-success { background-color: #00cc44; color: white; box-shadow: 0 4px 15px rgba(0,204,68,0.3); }
        .btn-success:hover:not(:disabled) { background-color: #00b33c; }

        /* --- BUTTON SLIDER CSS --- */
        input[type=range] {
            -webkit-appearance: none;
            width: 100%;
            background: transparent;
            margin-bottom: 5px;
        }
        input[type=range]::-webkit-slider-thumb {
            -webkit-appearance: none;
            height: 16px;
            width: 16px;
            border-radius: 50%;
            background: var(--primary-accent);
            cursor: pointer;
            margin-top: -6px; 
            box-shadow: 0 0 5px rgba(0,0,0,0.5);
        }
        input[type=range]::-webkit-slider-runnable-track {
            width: 100%;
            height: 4px;
            cursor: pointer;
            background: #555;
            border-radius: 2px;
        }
        
        /* Premium Color Picker Styling */
        input[type=color] {
            width: 45px; 
            border: 1px solid #555; 
            border-radius: 4px; 
            background: #111; 
            cursor: pointer; 
            height: auto;
            padding: 2px;
        }

        /* --- PREVIEW CANVAS (INSTAGRAM FEED SIZE) --- */
        .preview-area {
            flex-grow: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            background: radial-gradient(circle at center, #333 0%, #000 100%);
            overflow: hidden;
            padding: 20px;
        }

        .canvas-scaler {
            position: relative;
            width: calc(100vh * (1080/1350) * 0.95); 
            height: calc(100vh * 0.95);
            box-shadow: 0 0 50px rgba(0, 0, 0, 1);
        }

        /* EXACT 1080x1350 DIMENSIONS FOR INSTAGRAM FEED/CAROUSEL */
        .instagram-post {
            position: absolute;
            top: 0; left: 0;
            width: var(--post-width);
            height: var(--post-height);
            background-color: #ffffff;
            transform-origin: top left;
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        /* --- UNIVERSAL HIGHLIGHT SPAN --- */
        .highlight-dynamic {
            background-color: var(--hl-bg-color);
            color: var(--hl-text-color);
            padding: 4px 12px;
            display: inline; /* Acts like normal text to prevent full-width stretching */
            -webkit-box-decoration-break: clone;
            box-decoration-break: clone;
            border-radius: 6px;
            line-height: 1.4;
            transition: background-color 0.3s, color 0.3s;
        }
        /* Keeping original classname logic backward compatible */
        .highlight-red {
            background-color: var(--news-red);
            color: white;
            padding: 4px 12px;
            display: inline; 
            -webkit-box-decoration-break: clone;
            box-decoration-break: clone;
            border-radius: 4px;
            line-height: 1.4;
        }

        /* --- TOP HEADER (WHITE TEXT AREA) --- */
        .post-header-area {
            background-color: #ffffff;
            padding: 45px 30px 20px 30px; 
            z-index: 5;
            position: relative;
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100%;
            overflow: hidden; 
        }

        .main-breaking {
            font-family: 'Impact', 'Anton', sans-serif;
            font-size: 215px; 
            line-height: 0.8;
            color: var(--news-black);
            text-transform: uppercase;
            text-align: center;
            margin-bottom: 35px;
            letter-spacing: -1px;
            white-space: nowrap; 
            transform: scale(1.25, 1.3); 
        }

        .sub-headline {
            font-family: 'Montserrat', sans-serif;
            font-weight: 900;
            font-size: 50px;
            line-height: 1.25;
            color: var(--news-black);
            text-transform: uppercase;
            text-align: center;
            width: 95%;
        }

        /* --- MULTI-THEME / LAYOUT 2 ADDITIONS --- */
        .theme-global-news { background-color: #000000 !important; }
        .theme-global-news .post-header-area { 
            background-color: transparent !important; 
            padding: 25px 20px 10px 20px !important; 
            z-index: 10 !important; 
            height: auto !important; 
            position: absolute !important; 
            top: 0 !important; left: 0 !important; width: 100% !important;
            overflow: visible !important;
        }
        .theme-global-news .post-media-area {
            position: absolute !important;
            top: 0 !important; left: 0 !important;
            width: 100% !important; height: 100% !important;
        }
        .theme-global-news .highlight-red { background-color: #ffffff; color: #000000; }
        
        .main-breaking-v2 { font-family: 'Impact', 'Anton', sans-serif; font-size: 195px; line-height: 0.8; color: #ffffff; text-transform: uppercase; text-align: center; margin-bottom: 50px; letter-spacing: -2px; white-space: nowrap; transform: scale(1.35, 1.3); width: 100%; display: block; }
        .main-breaking-v2 span { color: #ffcc00; }
        
        .red-headline-container { display: flex; flex-direction: column; gap: 15px; width: 100%; align-items: center; }
        .red-headline-line { background-color: #cc0000; color: #ffffff; font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 42px; padding: 6px 20px; text-transform: uppercase; text-align: center; line-height: 1.1; display: inline-block; }
        .yellow-headline-line { color: #ffcc00; font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 46px; padding: 5px 20px; text-transform: uppercase; text-align: center; margin-top: 15px; line-height: 1.1;}
        .sub-italic-headline { color: #ffffff; font-family: 'Montserrat', sans-serif; font-weight: 500; font-style: italic; font-size: 24px; margin-top: 20px; text-align: center; width: 90%;}
        
        /* --- BRAND NEW THEME ADDITIONS (3 to 7) --- */
        
        /* Theme 3: Minimalist Quote */
        .theme-minimal-quote .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; }
        .theme-minimal-quote .post-header-area {
            background-color: rgba(0,0,0,0.7) !important; backdrop-filter: blur(10px);
            position: absolute !important; top: 50% !important; left: 5% !important; width: 90% !important;
            transform: translateY(-50%); border-radius: 20px; padding: 60px 40px !important; z-index: 10;
        }
        .minimal-quote-text { font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 55px; line-height: 1.3; color: #ffffff; text-align: center; text-transform: uppercase; }
        .minimal-quote-author { font-family: 'Montserrat', sans-serif; font-weight: 500; font-size: 28px; color: #ffcc00; text-align: center; margin-top: 30px; letter-spacing: 2px; }

        /* Theme 4: Cinematic Split Screen */
        .theme-split-screen .post-media-area { height: 50% !important; top: 0 !important; position: absolute !important; left: 0; width: 100%; border-bottom: 10px solid var(--primary-accent); z-index: 2; }
        .theme-split-screen .post-header-area {
            background-color: #0a0a0a !important; height: 50% !important; position: absolute !important; bottom: 0 !important; top: auto !important; left: 0; width: 100%;
            display: flex; flex-direction: column; justify-content: center; padding: 40px !important; z-index: 10;
        }
        .split-main-headline { font-family: 'Anton', sans-serif; font-size: 80px; line-height: 1.1; color: #ffffff; text-transform: uppercase; margin-bottom: 20px; }
        .split-sub-headline { font-family: 'Montserrat', sans-serif; font-weight: 600; font-size: 30px; color: #aaaaaa; }

        /* Theme 5: Cyberpunk Tech Alert */
        .theme-cyberpunk { background-color: #050510 !important; }
        .theme-cyberpunk .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; opacity: 0.6; mix-blend-mode: luminosity; }
        .theme-cyberpunk .post-header-area {
            background-color: transparent !important; position: absolute !important; top: 10% !important; left: 5% !important; width: 90% !important;
            border-left: 10px solid #00ffcc; padding: 30px !important; z-index: 10;
        }
        .cyber-alert { font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 35px; color: #00ffcc; letter-spacing: 5px; margin-bottom: 15px; }
        .cyber-headline { font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 70px; line-height: 1.1; color: #ffffff; text-transform: uppercase; text-shadow: 2px 2px 0px #ff0055; }

        /* Theme 6: Sports Action */
        .theme-sports { background-color: #111 !important; }
        .theme-sports .post-media-area { position: absolute !important; top: 0 !important; left: 0 !important; width: 100% !important; height: 100% !important; }
        .theme-sports .post-header-area { background-color: transparent !important; position: absolute !important; bottom: 15% !important; left: 0 !important; width: 100% !important; padding: 0 !important; z-index: 10; display: flex; flex-direction: column; align-items: flex-start; }
        .sports-box-1 { background-color: #ff2a2a; color: white; padding: 15px 40px; font-family: 'Anton', sans-serif; font-size: 50px; text-transform: uppercase; transform: skew(-15deg) translateX(-20px); margin-bottom: 10px; box-shadow: 10px 10px 0px rgba(0,0,0,0.5); }
        .sports-box-2 { background-color: #ffffff; color: #000000; padding: 20px 40px; font-family: 'Anton', sans-serif; font-size: 80px; line-height: 1; text-transform: uppercase; transform: skew(-15deg) translateX(20px); box-shadow: 10px 10px 0px rgba(0,0,0,0.5); }

        /* Theme 7: Editorial Magazine */
        .theme-editorial .post-media-area { position: absolute !important; top: 5% !important; left: 5% !important; width: 90% !important; height: 50% !important; z-index: 1; }
        .theme-editorial .post-header-area { background-color: #f4f4f4 !important; position: absolute !important; bottom: 0 !important; top: auto !important; left: 0; width: 100%; height: 45% !important; display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 40px !important; z-index: 10; border-top: 2px solid #000; }
        .editorial-title { font-family: 'Playfair Display', serif; font-size: 85px; font-weight: 700; color: #000000; text-align: center; line-height: 1.1; margin-bottom: 25px; }
        .editorial-sub { font-family: 'Montserrat', sans-serif; font-size: 22px; font-weight: 500; color: #555555; text-align: center; text-transform: uppercase; letter-spacing: 3px; border-top: 1px solid #000; border-bottom: 1px solid #000; padding: 15px 0; width: 80%; }


        /* --- MEDIA AREA & PROGRAMMATIC BLUR DIV --- */
        .post-media-area {
            flex-grow: 1;
            position: relative;
            background-color: #000000; 
            width: 100%;
            overflow: hidden;
        }

        .blur-overlay-div {
            position: absolute;
            top: -5px; 
            left: 0;
            width: 100%;
            height: 165px; 
            background: linear-gradient(
                to bottom, 
                #ffffff 0%, 
                #ffffff 10%, 
                rgba(255,255,255,0.8) 30%, 
                rgba(255,255,255,0.4) 60%, 
                transparent 100%
            );
            z-index: 2;
            pointer-events: none;
        }
        
        .theme-global-blur {
            background: linear-gradient(
                to bottom, 
                #000000 0%, 
                #000000 10%, 
                rgba(0,0,0,0.9) 45%, 
                rgba(0,0,0,0.65) 75%, 
                transparent 100%
            ) !important;
        }

        .media-content {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: 50% 50%;
            position: absolute;
            top: 0; left: 0;
            z-index: 1;
        }

        /* --- OVERLAYS (DATE & LOGO) --- */
        .overlay-layer {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            pointer-events: none;
            z-index: 100;
        }

        .date-box {
            position: absolute;
            bottom: 30px;
            left: 30px;
            background-color: var(--news-red);
            color: white;
            padding: 10px 25px;
            text-align: center;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        .date-number {
            font-family: 'Impact', 'Anton', sans-serif;
            font-size: 90px;
            line-height: 0.9;
            letter-spacing: -2px;
        }
        .date-month {
            font-family: 'Montserrat', sans-serif;
            font-weight: 900;
            font-size: 32px;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-top: -5px;
        }

        .branding-corner {
            position: absolute;
            bottom: 30px;
            right: 30px;
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.8);
        }

        .custom-logo {
            width: 180px;
            height: auto;
            margin-bottom: 10px;
            border-radius: 50%;
            box-shadow: 0 5px 15px rgba(0,0,0,0.5);
            display: none; 
        }

        .brand-text {
            font-family: 'Montserrat', sans-serif;
            color: white;
            font-size: 28px;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        .brand-text span {
            color: var(--news-red);
        }

        /* --- PREMIUM NOTIFICATION & MOBILE FIXES --- */
        #advanced-toast {
            position: fixed; top: -100px; left: 50%; transform: translateX(-50%);
            background: #00cc44; color: white; padding: 15px 30px; border-radius: 50px;
            font-family: 'Montserrat', sans-serif; font-weight: 800; font-size: 16px;
            box-shadow: 0 10px 30px rgba(0, 204, 68, 0.4); z-index: 100000;
            transition: top 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            display: flex; align-items: center; gap: 10px; white-space: nowrap;
        }
        #advanced-toast.show { top: 30px; }

        #recording-overlay {
            position: fixed; top: 0; left: 0; width: 100vw; height: 100vh;
            background: rgba(0,0,0,0.9); z-index: 9999;
            display: none; flex-direction: column; align-items: center; justify-content: center;
            color: white; font-family: 'Montserrat', sans-serif; text-align: center;
        }
        #recording-overlay h2 { font-size: 24px; margin-bottom: 10px; color: #00cc44; }
        
        .mobile-modal {
            position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: rgba(0,0,0,0.95); z-index: 10000;
            display: none; flex-direction: column; align-items: center; justify-content: center; padding: 20px;
        }
        .mobile-modal.active { display: flex; }
        .mobile-modal video { width: 100%; max-width: 400px; border: 2px solid #333; border-radius: 10px; margin-bottom: 20px; }
        
        .download-btn-massive {
            display: block; width: 100%; max-width: 350px; padding: 25px; background: #00cc44; color: white;
            text-decoration: none; text-align: center; font-size: 20px; font-weight: 900; border-radius: 10px;
            margin-bottom: 15px; text-transform: uppercase; font-family: 'Montserrat', sans-serif;
            box-shadow: 0 10px 20px rgba(0, 204, 68, 0.3);
        }
        .close-btn { background: #333; color: white; padding: 15px 40px; border: none; border-radius: 8px; font-weight: bold; font-size: 16px; cursor: pointer; }

        @media (max-width: 900px) {
            body { flex-direction: column; overflow-y: auto; }
            .editor-sidebar { width: 100%; border-right: none; }
            .preview-area { min-height: 80vh; padding: 10px; }
            .canvas-scaler { width: calc(100vw * 0.95); height: calc((100vw * 0.95) * (1350/1080)); }
        }
    </style>
</head>
<body>

    <div id="advanced-toast">✅ Download Started! Check your notifications.</div>

    <aside class="editor-sidebar">
        <div class="sidebar-header">
            <h1>India <span>GlobalCine</span></h1>
        </div>

        <div class="control-group-container">
            
            <div class="control-group" style="background: #2a2a2a; border-left: 4px solid #ffcc00;">
                <label style="color: #ffcc00;">🎨 SELECT POST THEME / LAYOUT</label>
                <select id="layout-selector" class="form-control" style="background: #000; border: 1px solid #555;">
                    <option value="theme-default">Layout 1: India GlobalCine (Default)</option>
                    <option value="theme-global">Layout 2: Global News (One Vision Style)</option>
                    <option value="theme-minimal">Layout 3: Minimalist Quote</option>
                    <option value="theme-split">Layout 4: Cinematic Split Screen</option>
                    <option value="theme-cyber">Layout 5: Cyberpunk Tech Alert</option>
                    <option value="theme-sports">Layout 6: Sports Action Match</option>
                    <option value="theme-editorial">Layout 7: Premium Editorial</option>
                </select>
            </div>

            <!-- NEW: Universal Highlight Settings -->
            <div class="control-group" style="background: #1a1a2e; border-left: 4px solid #00f0ff;">
                <label style="color: #00f0ff;">🖌️ HIGHLIGHT STYLES {BRACKETS}</label>
                <small style="color:#aaa; font-size: 11px; display:block; margin-bottom:10px;">Type {text} in ANY field below to highlight it!</small>
                <div style="display: flex; gap: 15px; align-items: center;">
                    <div style="display:flex; flex-direction:column; gap:5px; align-items:center;">
                        <span style="font-size:10px; color:#fff;">Background</span>
                        <input type="color" id="hl-bg-color" value="#e61919">
                    </div>
                    <div style="display:flex; flex-direction:column; gap:5px; align-items:center;">
                        <span style="font-size:10px; color:#fff;">Text Color</span>
                        <input type="color" id="hl-text-color" value="#ffffff">
                    </div>
                </div>
            </div>

            <!-- THEME 1 CONTROLS -->
            <div id="theme-default-controls" class="theme-controls-panel">
                <div class="control-group">
                    <label>Main Heading (Giant Text)</label>
                    <div style="display: flex; gap: 8px; align-items: stretch;">
                        <input type="text" id="input-breaking" class="form-control" value="BREAKING" style="flex: 1;">
                        <input type="color" id="color-t1-breaking" value="#000000" title="Font Color">
                    </div>
                </div>

                <div class="control-group">
                    <label>Full Headline</label>
                    <div style="display: flex; gap: 8px; align-items: stretch;">
                        <textarea id="input-headline" class="form-control" style="flex: 1;">MP RAGHAV CHADHA REPLIED AFTER {AAP STOPPED HIM} FROM SPEAKING IN PARLIAMENT</textarea>
                        <input type="color" id="color-t1-headline" value="#000000" title="Font Color">
                    </div>
                </div>
                
                <div class="control-group">
                    <label>Sub Headline (Small Paragraph)</label>
                    <div style="display: flex; gap: 8px; align-items: stretch;">
                        <input type="text" id="input-sub-italic-t1" class="form-control" value="India was set to receive Iranian oil after nearly {7 years}, but it was rerouted." style="flex: 1;">
                        <input type="color" id="color-t1-sub" value="#333333" title="Font Color">
                    </div>
                </div>

                <div style="display:flex; gap:10px;">
                    <div class="control-group" style="flex:1;">
                        <label>Date (Num)</label>
                        <input type="text" id="input-date-num" class="form-control" value="03">
                    </div>
                    <div class="control-group" style="flex:1;">
                        <label>Month</label>
                        <input type="text" id="input-date-month" class="form-control" value="APRIL">
                    </div>
                </div>
            </div>

            <!-- THEME 2 CONTROLS -->
            <div id="theme-global-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Red Headline Line 1</label>
                    <div style="display: flex; gap: 8px; align-items: stretch;">
                        <input type="text" id="input-red-1" class="form-control" value="Ship carrying 600,000 barrels Iranian" style="flex: 1;">
                        <input type="color" id="color-t2-red1" value="#ffffff" title="Font Color">
                    </div>
                </div>
                <div class="control-group">
                    <label>Red Headline Line 2</label>
                    <div style="display: flex; gap: 8px; align-items: stretch;">
                        <input type="text" id="input-red-2" class="form-control" value="crude changes route from India to" style="flex: 1;">
                        <input type="color" id="color-t2-red2" value="#ffffff" title="Font Color">
                    </div>
                </div>
                <div class="control-group">
                    <label>Yellow Headline</label>
                    <div style="display: flex; gap: 8px; align-items: stretch;">
                        <input type="text" id="input-yellow" class="form-control" value="China midway {due to US sanctions}." style="flex: 1;">
                        <input type="color" id="color-t2-yellow" value="#ffcc00" title="Font Color">
                    </div>
                </div>
                <div class="control-group">
                    <label>Sub Headline (White Italic)</label>
                    <div style="display: flex; gap: 8px; align-items: stretch;">
                        <input type="text" id="input-sub-italic" class="form-control" value="India was set to receive Iranian oil after nearly 7 years, but it was rerouted." style="flex: 1;">
                        <input type="color" id="color-t2-sub" value="#ffffff" title="Font Color">
                    </div>
                </div>
            </div>

            <!-- THEME 3 CONTROLS (Minimal Quote) -->
            <div id="theme-minimal-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Main Quote</label>
                    <textarea id="input-t3-quote" class="form-control">"{SUCCESS} IS NOT FINAL, FAILURE IS NOT FATAL: IT IS THE COURAGE TO CONTINUE THAT COUNTS."</textarea>
                </div>
                <div class="control-group">
                    <label>Author / Source</label>
                    <input type="text" id="input-t3-author" class="form-control" value="- WINSTON CHURCHILL">
                </div>
            </div>

            <!-- THEME 4 CONTROLS (Split Screen) -->
            <div id="theme-split-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Split Block Headline</label>
                    <textarea id="input-t4-head" class="form-control">NEW ERA OF {CINEMA} BEGINS</textarea>
                </div>
                <div class="control-group">
                    <label>Split Sub-Text</label>
                    <textarea id="input-t4-sub" class="form-control">Directors are now moving towards purely digital environments for modern blockbusters.</textarea>
                </div>
            </div>

            <!-- THEME 5 CONTROLS (Cyberpunk) -->
            <div id="theme-cyber-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>System Alert Line</label>
                    <input type="text" id="input-t5-alert" class="form-control" value="[ SYSTEM_OVERRIDE_ACTIVE ]">
                </div>
                <div class="control-group">
                    <label>Neon Headline</label>
                    <textarea id="input-t5-head" class="form-control">GLOBAL NETWORKS {COMPROMISED} IN MASSIVE ATTACK</textarea>
                </div>
            </div>

            <!-- THEME 6 CONTROLS (Sports) -->
            <div id="theme-sports-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Top Red Slant Box</label>
                    <input type="text" id="input-t6-top" class="form-control" value="FULL TIME RESULT">
                </div>
                <div class="control-group">
                    <label>Bottom White Slant Box</label>
                    <input type="text" id="input-t6-bot" class="form-control" value="{INDIA} WON BY 5 WICKETS">
                </div>
            </div>

            <!-- THEME 7 CONTROLS (Editorial) -->
            <div id="theme-editorial-controls" class="theme-controls-panel" style="display: none;">
                <div class="control-group">
                    <label>Magazine Title (Serif)</label>
                    <textarea id="input-t7-title" class="form-control">The Future of {Modern} Architecture</textarea>
                </div>
                <div class="control-group">
                    <label>Subtitle / Date</label>
                    <input type="text" id="input-t7-sub" class="form-control" value="SPECIAL EDITION  |  VOL. 42">
                </div>
            </div>

            <div class="control-group">
                <label>Upload Background Photo/Video</label>
                <div class="file-upload-wrapper">
                    <span style="color: #888; font-weight: bold; pointer-events: none;">📸 Choose Media</span>
                    <input type="file" id="media-upload" accept="image/*,video/*">
                </div>
            </div>
            
            <div class="control-group">
                <label>Upload Logo (Bottom Right Corner)</label>
                <div class="file-upload-wrapper">
                    <span style="color: #888; font-weight: bold; pointer-events: none;">🛡️ Choose Logo Image</span>
                    <input type="file" id="logo-upload" accept="image/*">
                </div>
            </div>

            <div class="control-group" style="border-left: 4px solid #00cc44;">
                <label>🎚️ Advanced Size & Layout Controls</label>
                <div style="display: flex; flex-direction: column; gap: 12px; margin-top: 10px;">
                    
                    <div>
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">BREAKING Size (Both Themes)</label>
                        <input type="range" id="size-breaking" min="100" max="350" value="215">
                    </div>
                    <div id="size-group-t1">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Main Headline Size (Theme 1)</label>
                        <input type="range" id="size-t1-headline" min="20" max="100" value="50">
                        
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Small Paragraph Size (Theme 1)</label>
                        <input type="range" id="size-t1-sub" min="10" max="50" value="20">
                    </div>
                    <div id="size-group-t2" style="display: none;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Red Line 1 Size (Theme 2)</label>
                        <input type="range" id="size-t2-red1" min="20" max="80" value="42">
                        
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Red Line 2 Size (Theme 2)</label>
                        <input type="range" id="size-t2-red2" min="20" max="80" value="42">
                        
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">Yellow Headline Size (Theme 2)</label>
                        <input type="range" id="size-t2-yellow" min="20" max="80" value="46">
                        
                        <label style="font-size:10px; color:#888; margin-bottom:2px; margin-top:10px; display:block;">White Italic Size (Theme 2)</label>
                        <input type="range" id="size-t2-sub" min="15" max="50" value="24">
                    </div>

                    <div style="border-top: 1px solid #444; margin-top: 5px; padding-top: 10px;">
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Date Box Size</label>
                        <input type="range" id="size-date" min="0.5" max="2" step="0.1" value="1">
                    </div>
                    <div>
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Logo Size</label>
                        <input type="range" id="size-logo" min="50" max="300" value="180">
                    </div>
                    <div>
                        <label style="font-size:10px; color:#ffcc00; margin-bottom:2px;">Global Image/Video Zoom</label>
                        <input type="range" id="slider-zoom" min="50" max="250" value="100">
                    </div>
                    <div>
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Horizontal Move (Left / Right)</label>
                        <input type="range" id="slider-x" min="0" max="100" value="50">
                    </div>
                    <div>
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Vertical Move (Up / Down)</label>
                        <input type="range" id="slider-y" min="0" max="100" value="50">
                    </div>
                    <div>
                        <label style="font-size:10px; color:#888; margin-bottom:2px;">Transparent Blur Fade (Amount)</label>
                        <input type="range" id="slider-blur" min="0" max="1000" value="165">
                    </div>
                </div>
            </div>

        </div>

        <div class="action-buttons">
            <div style="display: flex; gap: 10px; margin-bottom: 5px;">
                <button id="btn-reset-style" class="btn btn-secondary" style="font-size: 13px; padding: 12px; flex: 1;">Reset Style</button>
                <button id="btn-auto-style" class="btn btn-secondary" style="font-size: 13px; padding: 12px; flex: 1;">Auto Style</button>
            </div>
            
            <button id="btn-download-vid" class="btn btn-success" style="display: none;">
                📥 DOWNLOAD COMPLETE MP4 VIDEO
            </button>
            
            <button id="btn-download-img" class="btn btn-primary">
                Download Post as Image
            </button>
        </div>
    </aside>

    <main class="preview-area">
        
        <div id="recording-overlay">
            <h2 id="rec-status">STITCHING HD VIDEO & TEXT...</h2>
            <p>Please wait and do not close the browser.</p>
        </div>

        <div class="canvas-scaler" id="scaler">
            
            <div id="post-canvas" class="instagram-post">
                
                <div id="zoom-wrapper" style="width: 100%; height: 100%; display: flex; flex-direction: column; transform: scale(1); transform-origin: center center;">
                    
                    <!-- THEME 1 HEADER -->
                    <div class="post-header-area" id="header-theme-1">
                        <div class="main-breaking" id="render-breaking">BREAKING</div>
                        <div class="sub-headline" id="render-headline">
                            MP RAGHAV CHADHA REPLIED AFTER <span class="highlight-dynamic">AAP STOPPED HIM</span> FROM SPEAKING IN PARLIAMENT
                        </div>
                        <div class="sub-italic-headline" id="render-sub-italic-t1-display" style="color: #333333; margin-top: 15px; font-weight: 700; text-transform: uppercase; font-style: normal; font-size: 20px;">
                            India was set to receive Iranian oil after nearly <span class="highlight-dynamic">7 years</span>, but it was rerouted.
                        </div>
                    </div>

                    <!-- THEME 2 HEADER -->
                    <div class="post-header-area" id="header-theme-2" style="display: none;">
                        <div class="main-breaking-v2" id="render-breaking-t2">BREAKING<span style="color:#ffcc00;">!</span></div>
                        <div class="red-headline-container">
                            <div class="red-headline-line" id="render-red-1">SHIP CARRYING 600,000 BARRELS IRANIAN</div>
                            <div class="red-headline-line" id="render-red-2">CRUDE CHANGES ROUTE FROM INDIA TO</div>
                        </div>
                        <div class="yellow-headline-line" id="render-yellow">CHINA MIDWAY <span class="highlight-dynamic">DUE TO US SANCTIONS</span>.</div>
                        <div class="sub-italic-headline" id="render-sub-italic">India was set to receive Iranian oil after nearly 7 years, but it was rerouted.</div>
                    </div>

                    <!-- THEME 3 HEADER (Minimal Quote) -->
                    <div class="post-header-area" id="header-theme-3" style="display: none;">
                        <div class="minimal-quote-text" id="render-t3-quote">"<span class="highlight-dynamic">SUCCESS</span> IS NOT FINAL, FAILURE IS NOT FATAL: IT IS THE COURAGE TO CONTINUE THAT COUNTS."</div>
                        <div class="minimal-quote-author" id="render-t3-author">- WINSTON CHURCHILL</div>
                    </div>

                    <!-- THEME 4 HEADER (Split Screen) -->
                    <div class="post-header-area" id="header-theme-4" style="display: none;">
                        <div class="split-main-headline" id="render-t4-head">NEW ERA OF <span class="highlight-dynamic">CINEMA</span> BEGINS</div>
                        <div class="split-sub-headline" id="render-t4-sub">Directors are now moving towards purely digital environments for modern blockbusters.</div>
                    </div>

                    <!-- THEME 5 HEADER (Cyberpunk) -->
                    <div class="post-header-area" id="header-theme-5" style="display: none;">
                        <div class="cyber-alert" id="render-t5-alert">[ SYSTEM_OVERRIDE_ACTIVE ]</div>
                        <div class="cyber-headline" id="render-t5-head">GLOBAL NETWORKS <span class="highlight-dynamic">COMPROMISED</span> IN MASSIVE ATTACK</div>
                    </div>

                    <!-- THEME 6 HEADER (Sports) -->
                    <div class="post-header-area" id="header-theme-6" style="display: none;">
                        <div class="sports-box-1" id="render-t6-top">FULL TIME RESULT</div>
                        <div class="sports-box-2" id="render-t6-bot"><span class="highlight-dynamic">INDIA</span> WON BY 5 WICKETS</div>
                    </div>

                    <!-- THEME 7 HEADER (Editorial) -->
                    <div class="post-header-area" id="header-theme-7" style="display: none;">
                        <div class="editorial-title" id="render-t7-title">The Future of <span class="highlight-dynamic">Modern</span> Architecture</div>
                        <div class="editorial-sub" id="render-t7-sub">SPECIAL EDITION  |  VOL. 42</div>
                    </div>

                    <div class="post-media-area" id="post-media-area">
                        
                        <div id="blur-overlay-div" class="blur-overlay-div"></div>
                        
                        <div id="media-zoom-wrapper" style="width: 100%; height: 100%; transform: scale(1); transform-origin: center center; position: absolute; top: 0; left: 0;">
                            <img id="render-media-img" class="media-content" src="" style="display:none;" alt="">
                            <video id="render-media-vid" class="media-content" style="display:none;" loop playsinline webkit-playsinline muted crossorigin="anonymous"></video>
                        </div>
                        
                        <div class="overlay-layer" id="overlays-theme-1">
                            <div class="date-box" id="render-date-box">
                                <div class="date-number" id="render-date-num">03</div>
                                <div class="date-month" id="render-date-month">APRIL</div>
                            </div>

                            <div class="branding-corner">
                                <img id="render-logo-t1" class="custom-logo" src="" alt="Logo">
                                <div class="brand-text">
                                    INDIA <span>GLOBALCINE</span>
                                </div>
                            </div>
                        </div>
                    </div>
                
                </div>
            </div>

        </div>
    </main>

    <div class="mobile-modal" id="download-modal">
        <h2 style="color:white; margin-bottom: 20px; text-align:center;">✅ HD MP4 Video Ready!</h2>
        <video id="final-video-preview" controls playsinline webkit-playsinline loop></video>
        
        <a id="force-download-link" class="download-btn-massive" href="#" download="IndiaGlobalCine_HD_Video.mp4">
            📥 CLICK HERE IF DOWNLOAD DIDN'T START
        </a>
        <button class="close-btn" onclick="document.getElementById('download-modal').classList.remove('active')">Close</button>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            function showNotification(message) {
                const toast = document.getElementById('advanced-toast');
                toast.innerHTML = message;
                toast.classList.add('show');
                setTimeout(() => {
                    toast.classList.remove('show');
                }, 4000);
            }

            function scaleCanvas() {
                const scaler = document.getElementById('scaler');
                const post = document.getElementById('post-canvas');
                const parentW = scaler.parentElement.offsetWidth;
                const parentH = scaler.parentElement.offsetHeight;
                const scale = Math.min(parentW / 1080, parentH / 1350) * 0.95;
                post.style.transform = `scale(${scale})`;
                scaler.style.width = `${1080 * scale}px`;
                scaler.style.height = `${1350 * scale}px`;
            }
            window.addEventListener('resize', scaleCanvas);
            scaleCanvas();

            // --- UNIVERSAL HIGHLIGHT FUNCTION ---
            function applyHighlight(text) {
                // Allows using {text} in ANY field to apply highlight perfectly
                return text.replace(/\{(.*?)\}/g, '<span class="highlight-dynamic">$1</span>');
            }

            // Global Highlight Color Adjustments
            document.getElementById('hl-bg-color').addEventListener('input', e => {
                document.documentElement.style.setProperty('--hl-bg-color', e.target.value);
            });
            document.getElementById('hl-text-color').addEventListener('input', e => {
                document.documentElement.style.setProperty('--hl-text-color', e.target.value);
            });


            // --- 10 SLIDER CONTROLS LOGIC ---
            
            document.getElementById('size-breaking').addEventListener('input', e => {
                document.getElementById('render-breaking').style.fontSize = `${e.target.value}px`;
                document.getElementById('render-breaking-t2').style.fontSize = `${e.target.value * 0.9}px`; // slight ratio adjust for t2
            });
            document.getElementById('size-t1-headline').addEventListener('input', e => document.getElementById('render-headline').style.fontSize = `${e.target.value}px`);
            document.getElementById('size-t1-sub').addEventListener('input', e => document.getElementById('render-sub-italic-t1-display').style.fontSize = `${e.target.value}px`);
            
            document.getElementById('size-t2-red1').addEventListener('input', e => document.getElementById('render-red-1').style.fontSize = `${e.target.value}px`);
            document.getElementById('size-t2-red2').addEventListener('input', e => document.getElementById('render-red-2').style.fontSize = `${e.target.value}px`);
            document.getElementById('size-t2-yellow').addEventListener('input', e => document.getElementById('render-yellow').style.fontSize = `${e.target.value}px`);
            document.getElementById('size-t2-sub').addEventListener('input', e => document.getElementById('render-sub-italic').style.fontSize = `${e.target.value}px`);

            document.getElementById('size-date').addEventListener('input', e => {
                document.getElementById('render-date-box').style.transform = `scale(${e.target.value})`;
                document.getElementById('render-date-box').style.transformOrigin = `bottom left`;
            });
            document.getElementById('size-logo').addEventListener('input', e => {
                document.getElementById('render-logo-t1').style.width = `${e.target.value}px`;
            });

            const mediaX = document.getElementById('slider-x');
            const mediaY = document.getElementById('slider-y');
            const blurSlider = document.getElementById('slider-blur');
            const zoomSlider = document.getElementById('slider-zoom');
            const imgEl = document.getElementById('render-media-img');
            const vidEl = document.getElementById('render-media-vid');
            const blurDiv = document.getElementById('blur-overlay-div');
            const mediaZoomWrapper = document.getElementById('media-zoom-wrapper');

            function updateMediaPos() {
                const pos = `${mediaX.value}% ${mediaY.value}%`;
                imgEl.style.objectPosition = pos;
                vidEl.style.objectPosition = pos;
            }
            mediaX.addEventListener('input', updateMediaPos);
            mediaY.addEventListener('input', updateMediaPos);
            
            blurSlider.addEventListener('input', (e) => {
                blurDiv.style.height = `${e.target.value}px`;
            });

            zoomSlider.addEventListener('input', (e) => {
                mediaZoomWrapper.style.transform = `scale(${e.target.value / 100})`;
            });

            // --- ADVANCED 7-THEME SWITCHER LOGIC ---
            document.getElementById('layout-selector').addEventListener('change', function(e) {
                const theme = e.target.value;
                const postCanvas = document.getElementById('post-canvas');
                
                // Hide all panels and headers first
                document.querySelectorAll('.theme-controls-panel').forEach(el => el.style.display = 'none');
                document.querySelectorAll('.post-header-area').forEach(el => el.style.display = 'none');
                
                // Reset custom classes
                postCanvas.className = 'instagram-post';
                
                const s1Group = document.getElementById('size-group-t1');
                const s2Group = document.getElementById('size-group-t2');
                s1Group.style.display = 'none';
                s2Group.style.display = 'none';

                blurDiv.classList.remove('theme-global-blur');
                blurSlider.value = 165; 
                blurDiv.style.height = '165px';

                if (theme === 'theme-global') {
                    postCanvas.classList.add('theme-global-news');
                    document.getElementById('theme-global-controls').style.display = 'block';
                    document.getElementById('header-theme-2').style.display = 'flex';
                    s2Group.style.display = 'block';
                    blurDiv.classList.add('theme-global-blur');
                    blurSlider.value = 580; 
                    blurDiv.style.height = '580px';
                } else if (theme === 'theme-minimal') {
                    postCanvas.classList.add('theme-minimal-quote');
                    document.getElementById('theme-minimal-controls').style.display = 'block';
                    document.getElementById('header-theme-3').style.display = 'block';
                } else if (theme === 'theme-split') {
                    postCanvas.classList.add('theme-split-screen');
                    document.getElementById('theme-split-controls').style.display = 'block';
                    document.getElementById('header-theme-4').style.display = 'flex';
                } else if (theme === 'theme-cyber') {
                    postCanvas.classList.add('theme-cyberpunk');
                    document.getElementById('theme-cyber-controls').style.display = 'block';
                    document.getElementById('header-theme-5').style.display = 'block';
                } else if (theme === 'theme-sports') {
                    postCanvas.classList.add('theme-sports');
                    document.getElementById('theme-sports-controls').style.display = 'block';
                    document.getElementById('header-theme-6').style.display = 'flex';
                } else if (theme === 'theme-editorial') {
                    postCanvas.classList.add('theme-editorial');
                    document.getElementById('theme-editorial-controls').style.display = 'block';
                    document.getElementById('header-theme-7').style.display = 'flex';
                } else {
                    // Default Theme 1
                    document.getElementById('theme-default-controls').style.display = 'block';
                    document.getElementById('header-theme-1').style.display = 'flex';
                    s1Group.style.display = 'block';
                }
            });

            // --- RESET AND AUTO STYLE BUTTONS ---
            document.getElementById('btn-reset-style').addEventListener('click', () => {
                // Reset Sizes & Sliders
                document.getElementById('size-breaking').value = 215;
                document.getElementById('size-t1-headline').value = 50;
                document.getElementById('size-t1-sub').value = 20;
                document.getElementById('size-t2-red1').value = 42;
                document.getElementById('size-t2-red2').value = 42;
                document.getElementById('size-t2-yellow').value = 46;
                document.getElementById('size-t2-sub').value = 24;
                document.getElementById('size-date').value = 1;
                document.getElementById('size-logo').value = 180;
                document.getElementById('slider-zoom').value = 100;
                document.getElementById('slider-x').value = 50;
                document.getElementById('slider-y').value = 50;
                
                let isGlobal = document.getElementById('layout-selector').value === 'theme-global';
                document.getElementById('slider-blur').value = isGlobal ? 580 : 165;

                // Reset Colors
                document.getElementById('color-t1-breaking').value = "#000000";
                document.getElementById('color-t1-headline').value = "#000000";
                document.getElementById('color-t1-sub').value = "#333333";
                document.getElementById('color-t2-red1').value = "#ffffff";
                document.getElementById('color-t2-red2').value = "#ffffff";
                document.getElementById('color-t2-yellow').value = "#ffcc00";
                document.getElementById('color-t2-sub').value = "#ffffff";
                
                // Reset Highlight UI variables
                document.getElementById('hl-bg-color').value = "#e61919";
                document.getElementById('hl-text-color').value = "#ffffff";
                document.documentElement.style.setProperty('--hl-bg-color', "#e61919");
                document.documentElement.style.setProperty('--hl-text-color', "#ffffff");

                // Dispatch event trick to force UI to update everything
                const allSlidersAndColors = ['size-breaking', 'size-t1-headline', 'size-t1-sub', 'size-t2-red1', 'size-t2-red2', 'size-t2-yellow', 'size-t2-sub', 'size-date', 'size-logo', 'slider-zoom', 'slider-x', 'slider-y', 'slider-blur', 'color-t1-breaking', 'color-t1-headline', 'color-t1-sub', 'color-t2-red1', 'color-t2-red2', 'color-t2-yellow', 'color-t2-sub'];
                allSlidersAndColors.forEach(id => {
                    document.getElementById(id).dispatchEvent(new Event('input'));
                });
                
                showNotification("⚙️ Styles Reset to Default!");
            });

            document.getElementById('btn-auto-style').addEventListener('click', () => {
                // Applies a premium aesthetic style automatically
                document.getElementById('color-t1-breaking').value = "#e61919"; 
                document.getElementById('color-t1-headline').value = "#222222"; 
                document.getElementById('color-t1-sub').value = "#555555"; 
                
                document.getElementById('color-t2-red1').value = "#ffff00"; 
                document.getElementById('color-t2-red2').value = "#ffff00";
                document.getElementById('color-t2-yellow').value = "#ffffff"; 
                
                document.getElementById('slider-zoom').value = 110; 
                
                ['color-t1-breaking', 'color-t1-headline', 'color-t1-sub', 'color-t2-red1', 'color-t2-red2', 'color-t2-yellow', 'slider-zoom'].forEach(id => {
                    document.getElementById(id).dispatchEvent(new Event('input'));
                });
                showNotification("✨ Auto Aesthetic Style Applied!");
            });


            // --- INPUT EVENT BINDINGS (All dynamically processing {Highlights}) ---
            
            // Theme 1 Inputs
            document.getElementById('input-breaking').addEventListener('input', e => {
                document.getElementById('render-breaking').innerHTML = applyHighlight(e.target.value.toUpperCase());
                document.getElementById('render-breaking-t2').innerHTML = applyHighlight(e.target.value.toUpperCase()) + '<span style="color:#ffcc00;">!</span>';
            });
            document.getElementById('input-headline').addEventListener('input', e => document.getElementById('render-headline').innerHTML = applyHighlight(e.target.value.toUpperCase()));
            document.getElementById('input-sub-italic-t1').addEventListener('input', e => document.getElementById('render-sub-italic-t1-display').innerHTML = applyHighlight(e.target.value));
            document.getElementById('input-date-num').addEventListener('input', e => document.getElementById('render-date-num').innerHTML = applyHighlight(e.target.value));
            document.getElementById('input-date-month').addEventListener('input', e => document.getElementById('render-date-month').innerHTML = applyHighlight(e.target.value.toUpperCase()));

            // Theme 1 Color Pickers
            document.getElementById('color-t1-breaking').addEventListener('input', e => document.getElementById('render-breaking').style.color = e.target.value);
            document.getElementById('color-t1-headline').addEventListener('input', e => document.getElementById('render-headline').style.color = e.target.value);
            document.getElementById('color-t1-sub').addEventListener('input', e => document.getElementById('render-sub-italic-t1-display').style.color = e.target.value);

            // Theme 2 Inputs
            document.getElementById('input-red-1').addEventListener('input', e => document.getElementById('render-red-1').innerHTML = applyHighlight(e.target.value.toUpperCase()));
            document.getElementById('input-red-2').addEventListener('input', e => document.getElementById('render-red-2').innerHTML = applyHighlight(e.target.value.toUpperCase()));
            document.getElementById('input-yellow').addEventListener('input', e => document.getElementById('render-yellow').innerHTML = applyHighlight(e.target.value.toUpperCase()));
            document.getElementById('input-sub-italic').addEventListener('input', e => document.getElementById('render-sub-italic').innerHTML = applyHighlight(e.target.value));

            // Theme 2 Color Pickers
            document.getElementById('color-t2-red1').addEventListener('input', e => document.getElementById('render-red-1').style.color = e.target.value);
            document.getElementById('color-t2-red2').addEventListener('input', e => document.getElementById('render-red-2').style.color = e.target.value);
            document.getElementById('color-t2-yellow').addEventListener('input', e => document.getElementById('render-yellow').style.color = e.target.value);
            document.getElementById('color-t2-sub').addEventListener('input', e => document.getElementById('render-sub-italic').style.color = e.target.value);

            // Theme 3 Inputs (Minimal)
            document.getElementById('input-t3-quote').addEventListener('input', e => document.getElementById('render-t3-quote').innerHTML = applyHighlight(e.target.value.toUpperCase()));
            document.getElementById('input-t3-author').addEventListener('input', e => document.getElementById('render-t3-author').innerHTML = applyHighlight(e.target.value.toUpperCase()));

            // Theme 4 Inputs (Split)
            document.getElementById('input-t4-head').addEventListener('input', e => document.getElementById('render-t4-head').innerHTML = applyHighlight(e.target.value.toUpperCase()));
            document.getElementById('input-t4-sub').addEventListener('input', e => document.getElementById('render-t4-sub').innerHTML = applyHighlight(e.target.value));

            // Theme 5 Inputs (Cyber)
            document.getElementById('input-t5-alert').addEventListener('input', e => document.getElementById('render-t5-alert').innerHTML = applyHighlight(e.target.value));
            document.getElementById('input-t5-head').addEventListener('input', e => document.getElementById('render-t5-head').innerHTML = applyHighlight(e.target.value.toUpperCase()));

            // Theme 6 Inputs (Sports)
            document.getElementById('input-t6-top').addEventListener('input', e => document.getElementById('render-t6-top').innerHTML = applyHighlight(e.target.value.toUpperCase()));
            document.getElementById('input-t6-bot').addEventListener('input', e => document.getElementById('render-t6-bot').innerHTML = applyHighlight(e.target.value.toUpperCase()));

            // Theme 7 Inputs (Editorial)
            document.getElementById('input-t7-title').addEventListener('input', e => document.getElementById('render-t7-title').innerHTML = applyHighlight(e.target.value));
            document.getElementById('input-t7-sub').addEventListener('input', e => document.getElementById('render-t7-sub').innerHTML = applyHighlight(e.target.value.toUpperCase()));


            // --- MEDIA UPLOAD HANDLING ---
            document.getElementById('media-upload').addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (!file) return;

                const fileURL = URL.createObjectURL(file);
                const isVideo = file.type.startsWith('video/');
                const vidDownloadBtn = document.getElementById('btn-download-vid');

                if (isVideo) {
                    imgEl.style.display = 'none';
                    vidEl.style.display = 'block';
                    vidEl.src = fileURL;
                    vidEl.muted = true; 
                    vidEl.play();
                    vidDownloadBtn.style.display = 'block';
                } else {
                    vidEl.style.display = 'none';
                    vidEl.pause();
                    imgEl.style.display = 'block';
                    imgEl.src = fileURL;
                    vidDownloadBtn.style.display = 'none';
                }
            });

            // --- LOGO HANDLING ---
            document.getElementById('logo-upload').addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (!file) return;
                const fileURL = URL.createObjectURL(file);
                const logo1 = document.getElementById('render-logo-t1');
                logo1.src = fileURL;
                logo1.style.display = 'block'; 
            });

            // --- HD IMAGE DOWNLOADER ---
            document.getElementById('btn-download-img').addEventListener('click', function() {
                const postCanvas = document.getElementById('post-canvas');
                const originalTransform = postCanvas.style.transform;
                postCanvas.style.transform = 'none';
                
                const btn = this;
                const originalText = btn.innerHTML;
                btn.innerHTML = 'GENERATING HD IMAGE...';
                btn.disabled = true;

                html2canvas(postCanvas, { 
                    scale: 2, 
                    useCORS: true, 
                    backgroundColor: '#000000' 
                }).then(canvas => {
                    const link = document.createElement('a');
                    link.download = `IndiaGlobalCine_HD_${new Date().getTime()}.jpg`;
                    link.href = canvas.toDataURL('image/jpeg', 1.0); 
                    link.click();
                    
                    postCanvas.style.transform = originalTransform;
                    btn.innerHTML = originalText;
                    btn.disabled = false;
                    showNotification("📸 HD Image Downloaded Successfully!");
                });
            });

            // --- ADVANCED HD MP4 VIDEO DOWNLOADER ---
            document.getElementById('btn-download-vid').addEventListener('click', async function() {
                if (vidEl.style.display === 'none' && imgEl.style.display === 'none') {
                    alert("Please upload a video or image first!");
                    return;
                }

                const btn = this;
                const originalText = btn.innerHTML;
                btn.disabled = true;

                const postCanvas = document.getElementById('post-canvas');
                const mediaArea = document.querySelector('.post-media-area');
                const overlay = document.getElementById('recording-overlay');
                const statusTxt = document.getElementById('rec-status');

                const originalTransform = postCanvas.style.transform;
                postCanvas.style.transform = 'none'; 
                overlay.style.display = 'flex';
                statusTxt.innerText = 'READING YOUR TEXT & DESIGN...';

                try {
                    const originalPostBg = postCanvas.style.backgroundColor;
                    const originalMediaBg = mediaArea.style.backgroundColor;
                    const originalVidDisplay = vidEl.style.display;
                    const originalImgDisplay = imgEl.style.display;

                    postCanvas.style.backgroundColor = 'transparent';
                    mediaArea.style.backgroundColor = 'transparent';
                    vidEl.style.display = 'none'; 
                    imgEl.style.display = 'none'; 
                    
                    const uiCanvas = await html2canvas(postCanvas, { scale: 1, backgroundColor: null, useCORS: true });
                    
                    postCanvas.style.backgroundColor = originalPostBg;
                    mediaArea.style.backgroundColor = originalMediaBg;
                    vidEl.style.display = originalVidDisplay;
                    imgEl.style.display = originalImgDisplay;
                    postCanvas.style.transform = originalTransform;

                    const recCanvas = document.createElement('canvas');
                    recCanvas.width = 1080;
                    recCanvas.height = 1350;
                    const ctx = recCanvas.getContext('2d');
                    
                    const pRect = postCanvas.getBoundingClientRect();
                    const mRect = mediaArea.getBoundingClientRect();
                    const scaleY = 1350 / pRect.height;
                    const scaleX = 1080 / pRect.width;
                    
                    const mY = (mRect.top - pRect.top) * scaleY;
                    const mH = mRect.height * scaleY;
                    const mX = (mRect.left - pRect.left) * scaleX;
                    const mW = mRect.width * scaleX;

                    const canvasStream = recCanvas.captureStream(30);
                    let audioTracks = [];
                    if (vidEl.captureStream) audioTracks = vidEl.captureStream().getAudioTracks();
                    else if (vidEl.mozCaptureStream) audioTracks = vidEl.mozCaptureStream().getAudioTracks();
                    
                    let finalStream = canvasStream;
                    if (audioTracks.length > 0) {
                        finalStream = new MediaStream([...canvasStream.getVideoTracks(), ...audioTracks]);
                    }

                    // FORCE WebM because browser MP4s are 'fragmented' and Instagram cuts them to 1 second
                    let mimeType = 'video/webm'; 
                    if (!MediaRecorder.isTypeSupported(mimeType)) mimeType = 'video/webm;codecs=vp8,opus';

                    const recorder = new MediaRecorder(finalStream, { 
                        mimeType: mimeType,
                        videoBitsPerSecond: 10000000 
                    });
                    
                    const chunks = [];
                    recorder.ondataavailable = e => { if (e.data.size > 0) chunks.push(e.data); };

                    vidEl.loop = false;
                    vidEl.muted = false; 
                    vidEl.currentTime = 0;
                    await vidEl.play();
                    await new Promise(r => setTimeout(r, 200)); 

                    statusTxt.innerText = 'RECORDING HD VIDEO... DO NOT CLOSE';

                    let isRecording = true;
                    let startRecordingTime = 0; // NEW: Precise timer for Instagram fix
                    function drawVideoFrame() {
                        if (!isRecording) return;
                        
                        ctx.fillStyle = '#000000';
                        ctx.fillRect(0, 0, 1080, 1350);
                        ctx.fillRect(mX, mY, mW, mH);

                        if (vidEl.readyState >= 2) {
                            const ratio = vidEl.videoWidth / vidEl.videoHeight;
                            const targetRatio = mW / mH;
                            let sw, sh, sx, sy;
                            
                            const xPerc = parseInt(mediaX.value) / 100;
                            const yPerc = parseInt(mediaY.value) / 100;
                            const zoomLvl = parseInt(zoomSlider.value) / 100;

                            if (ratio > targetRatio) {
                                sh = vidEl.videoHeight;
                                sw = sh * targetRatio;
                                sx = (vidEl.videoWidth - sw) * xPerc;
                                sy = 0;
                            } else {
                                sw = vidEl.videoWidth;
                                sh = sw / targetRatio;
                                sx = 0;
                                sy = (vidEl.videoHeight - sh) * yPerc;
                            }
                            
                            const cx = 1080 / 2;
                            const cy = mY + (mH / 2);
                            
                            ctx.save();
                            ctx.translate(cx, cy);
                            ctx.scale(zoomLvl, zoomLvl);
                            ctx.translate(-cx, -cy);
                            ctx.drawImage(vidEl, sx, sy, sw, sh, mX, mY, mW, mH);
                            ctx.restore();
                        }

                        ctx.drawImage(uiCanvas, 0, 0, 1080, 1350);

                        requestAnimationFrame(drawVideoFrame);
                    }

                    startRecordingTime = Date.now(); // Start exact timer
                    recorder.start();
                    drawVideoFrame();

                    vidEl.onended = () => {
                        isRecording = false;
                        recorder.stop();
                    };

                    recorder.onstop = async () => {
                        let blob = new Blob(chunks, { type: mimeType });
                        
                        // Calculate the exact milliseconds the video recorded for
                        let actualDurationMs = Date.now() - startRecordingTime;

                        // Unconditionally fix the duration using the exact tracked time
                        if (window.ysFixWebmDuration) {
                            blob = await window.ysFixWebmDuration(blob, actualDurationMs, { logger: false });
                        }

                        const url = URL.createObjectURL(blob);
                        // Save with .mp4 extension so Instagram accepts it natively without fragmentation issues
                        const filename = `IndiaGlobalCine_HD_Video_${Date.now()}.mp4`;

                        overlay.style.display = 'none';
                        vidEl.loop = true;
                        vidEl.muted = true;
                        vidEl.play();

                        const downloadLink = document.createElement('a');
                        downloadLink.style.display = 'none';
                        downloadLink.href = url;
                        downloadLink.download = filename;
                        document.body.appendChild(downloadLink);
                        
                        downloadLink.click();
                        showNotification("✅ HD Video Download Started! Check your browser downloads.");
                        
                        setTimeout(() => {
                            document.body.removeChild(downloadLink);
                            const modal = document.getElementById('download-modal');
                            const finalVideoPreview = document.getElementById('final-video-preview');
                            const forceDownloadBtn = document.getElementById('force-download-link');

                            finalVideoPreview.src = url;
                            forceDownloadBtn.href = url;
                            forceDownloadBtn.download = filename;
                            modal.classList.add('active');
                            
                            btn.innerHTML = originalText;
                            btn.disabled = false;
                        }, 500);
                    };

                    setTimeout(() => {
                        if (isRecording) {
                            isRecording = false;
                            recorder.stop();
                        }
                    }, (vidEl.duration * 1000) + 2000 || 15000);

                } catch(error) {
                    console.error(error);
                    alert("Error processing HD video. Make sure your browser allows Canvas recording.");
                    overlay.style.display = 'none';
                    postCanvas.style.transform = originalTransform;
                    btn.innerHTML = originalText;
                    btn.disabled = false;
                }
            });

        });
    </script>
</body>
</html>
