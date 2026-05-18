<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FlowCode Master Project · LCD + Keypad Matrix</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(145deg, #0a0c10 0%, #0f1217 100%);
            font-family: 'Inter', 'Segoe UI', 'Fira Code', 'Cascadia Code', system-ui, -apple-system, BlinkMacSystemFont, 'Roboto', monospace;
            display: flex;
            justify-content: center;
            padding: 2rem 1.5rem;
        }

        .readme-container {
            max-width: 1280px;
            width: 100%;
            background: #0d1117;
            border-radius: 2rem;
            box-shadow: 0 25px 45px -12px rgba(0, 0, 0, 0.6), 0 0 0 1px rgba(56, 189, 248, 0.1);
            overflow: hidden;
        }

        .project-header {
            background: radial-gradient(ellipse at 20% 30%, #1e2a3a, #0b0f17);
            padding: 2rem 2rem 1.8rem 2rem;
            border-bottom: 1px solid rgba(56, 189, 248, 0.3);
            position: relative;
        }

        .project-header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, #38bdf8, #a855f7, #38bdf8);
            background-size: 200% auto;
            animation: shimmer 3s linear infinite;
        }

        @keyframes shimmer {
            0% { background-position: 0% 0; }
            100% { background-position: 200% 0; }
        }

        .title-badge {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: baseline;
            gap: 1rem;
        }

        h1 {
            font-size: 2.8rem;
            font-weight: 700;
            background: linear-gradient(135deg, #E6F7FF, #90e0ff, #c084fc);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            letter-spacing: -0.02em;
            display: inline-flex;
            align-items: center;
            gap: 12px;
        }

        .flowcode-badge {
            background: #1f2937;
            padding: 0.3rem 1rem;
            border-radius: 60px;
            font-size: 0.8rem;
            font-weight: 600;
            color: #94a3b8;
            border: 1px solid #334155;
        }

        .status-chip {
            background: rgba(56, 189, 248, 0.15);
            backdrop-filter: blur(4px);
            border-radius: 100px;
            padding: 0.4rem 1rem;
            font-size: 0.8rem;
            font-weight: 500;
            border: 1px solid rgba(56, 189, 248, 0.4);
            color: #7dd3fc;
        }

        .header-desc {
            margin-top: 1.2rem;
            color: #b9c3d4;
            font-size: 1.1rem;
            max-width: 85%;
            border-left: 3px solid #38bdf8;
            padding-left: 1.2rem;
        }

        .tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 0.8rem;
            margin: 1.8rem 0 0.5rem 0;
        }

        .tech {
            background: #161b22;
            border-radius: 40px;
            padding: 0.3rem 1rem;
            font-size: 0.75rem;
            font-weight: 500;
            color: #cbd5e6;
            border: 0.5px solid #2d3a48;
        }

        .content-grid {
            display: grid;
            grid-template-columns: 1fr 1.2fr;
            gap: 2rem;
            padding: 2rem;
        }

        @media (max-width: 780px) {
            .content-grid {
                grid-template-columns: 1fr;
                gap: 2rem;
                padding: 1.5rem;
            }
            .header-desc {
                max-width: 100%;
            }
            h1 {
                font-size: 2rem;
            }
        }

        .hardware-showcase {
            background: #0a0e14;
            border-radius: 1.5rem;
            border: 1px solid #242933;
            padding: 1.2rem;
            box-shadow: 0 10px 20px -5px rgba(0,0,0,0.5);
            transition: transform 0.2s ease;
        }

        .hardware-showcase:hover {
            transform: translateY(-4px);
            border-color: #38bdf866;
        }

        .lcd-panel {
            background: #1e272e;
            border-radius: 1rem;
            padding: 1rem;
            box-shadow: inset 0 0 0 1px rgba(255,255,255,0.05), 0 8px 20px rgba(0,0,0,0.3);
        }

        .lcd-screen {
            background: #1c2c2c;
            border-radius: 12px;
            padding: 1rem;
            font-family: 'Courier New', 'Fira Code', monospace;
            box-shadow: inset 0 0 10px #00000055, 0 0 0 2px #314d4d;
        }

        .lcd-text {
            background: #152222;
            color: #adff9e;
            text-shadow: 0 0 3px #44ff44;
            font-size: 1.1rem;
            letter-spacing: 1px;
            padding: 0.8rem;
            border-radius: 8px;
            min-height: 90px;
            font-weight: 500;
            font-family: monospace;
        }

        .keypad-matrix {
            margin-top: 1.5rem;
            background: #10141c;
            border-radius: 1.2rem;
            padding: 1rem;
        }

        .grid-keypad {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
            margin-top: 12px;
        }

        .key {
            background: #1e293b;
            text-align: center;
            padding: 0.8rem 0;
            border-radius: 18px;
            font-weight: 700;
            font-size: 1.4rem;
            font-family: monospace;
            color: #e2e8f0;
            box-shadow: 0 4px 0 #0f172a;
            transition: 0.07s linear;
            cursor: pointer;
            border: 1px solid #334155;
        }

        .key:active {
            transform: translateY(2px);
            box-shadow: 0 1px 0 #0f172a;
        }

        .section-title {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
            color: #e2e8f0;
            border-left: 4px solid #38bdf8;
            padding-left: 12px;
        }

        .feature-list {
            list-style: none;
            margin-top: 1rem;
        }

        .feature-list li {
            margin-bottom: 0.9rem;
            display: flex;
            align-items: center;
            gap: 10px;
            color: #cbd5e6;
        }

        .feature-list li::before {
            content: "⚡";
            font-size: 1.2rem;
            color: #38bdf8;
        }

        .code-block {
            background: #010409;
            border-radius: 14px;
            padding: 1rem;
            border: 1px solid #2d3748;
            overflow-x: auto;
            margin-top: 1rem;
        }

        pre {
            font-family: 'Fira Code', 'Cascadia Code', monospace;
            font-size: 0.8rem;
            color: #bae6fd;
            white-space: pre-wrap;
        }

        .btn-group {
            margin-top: 2rem;
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .btn {
            background: #0d2840;
            border: 1px solid #2c5f8a;
            padding: 0.6rem 1.4rem;
            border-radius: 40px;
            font-weight: 500;
            text-decoration: none;
            color: #b9e6ff;
            transition: 0.2s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            cursor: pointer;
        }

        .btn-primary {
            background: #1e3a5f;
            border-color: #38bdf8;
            color: white;
            box-shadow: 0 0 6px #38bdf855;
        }

        .btn-primary:hover {
            background: #2c5282;
            transform: scale(1.02);
        }

        footer {
            border-top: 1px solid #1f2937;
            padding: 1.5rem 2rem;
            text-align: center;
            color: #6c7a91;
            font-size: 0.8rem;
            background: #0b0f16;
        }

        .interactive-demo {
            background: #0f131c;
            border-radius: 1.2rem;
            padding: 1rem;
            margin-top: 1.5rem;
        }

        .demo-status {
            background: #00000040;
            padding: 0.8rem;
            border-radius: 14px;
            font-family: monospace;
            color: #82e6aa;
            margin-top: 12px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.8rem;
            color: #b9c7db;
        }

        td {
            padding: 6px 0;
        }

        .pinout-example {
            background: #07111f;
            border-radius: 14px;
            padding: 12px;
            margin-top: 18px;
        }
    </style>
</head>
<body>
<div class="readme-container">
    <div class="project-header">
        <div class="title-badge">
            <h1>
                <span>🔐⌨️</span> FlowCode · LCD & Keypad Matrix
            </h1>
            <div class="status-chip">✓ Production Ready | Flowcode v10+</div>
        </div>
        <div class="header-desc">
            Professional embedded interface with 4x4 membrane keypad + 16x2 LCD character display. 
            Built entirely with FlowCode's advanced components — ideal for security panels, control terminals & HMI prototypes.
        </div>
        <div class="tech-stack">
            <span class="tech">🎛️ Flowcode 10</span>
            <span class="tech">🧩 LCD (HD44780)</span>
            <span class="tech">🔢 4x4 Matrix Keypad</span>
            <span class="tech">⚙️ PIC / Arduino / AVR</span>
            <span class="tech">📟 Interrupt-driven</span>
        </div>
    </div>

    <div class="content-grid">
        <div class="hardware-showcase">
            <div class="section-title">
                <span>🖥️</span> Live System Preview
            </div>
            <div class="lcd-panel">
                <div class="lcd-screen">
                    <div class="lcd-text" id="lcdLivePreview">
                        > FlowCode Ready<br>
                        > Press any key
                    </div>
                </div>
                <div style="margin-top: 12px; font-size: 12px; color:#6c81a5; display: flex; justify-content: space-between;">
                    <span>📟 16x2 Character LCD</span>
                    <span>🔆 Contrast: optimal</span>
                </div>
            </div>
            
            <div class="keypad-matrix">
                <div style="display: flex; justify-content: space-between; align-items: baseline;">
                    <span class="section-title" style="border-left-color: #a855f7;">🔢 4x4 Matrix Keypad</span>
                    <span style="font-size: 0.7rem; background:#00000055; padding: 3px 8px; border-radius: 40px;">GPIO mapped rows/cols</span>
                </div>
                <div class="grid-keypad" id="interactiveKeypad"></div>
                <div class="demo-status" id="keyFeedback">
                    ⌨️ Last Key: <span id="lastKeyVal">—</span> &nbsp;|&nbsp; Buffer: <span id="inputBuffer">_</span>
                </div>
                <p style="font-size: 0.7rem; margin-top: 10px; color:#5c6e8c;">💡 Click keys to simulate real keypad → updates LCD & data buffer (mirrors FlowCode logic)</p>
            </div>
        </div>

        <div>
            <div class="section-title">
                <span>✨</span> System Architecture & Features
            </div>
            <ul class="feature-list">
                <li>Fully compatible with Flowcode's LCD component (4-bit/8-bit mode) and Keypad component macro.</li>
                <li>Non-blocking keypad scanning algorithm with debouncing & long-press ready.</li>
                <li>Real-time LCD update: show typed characters, menu selections, or passcode entry.</li>
                <li>Configurable key mapping (hex + function keys: A, B, C, D, *, #).</li>
                <li>Easily exportable C code for PIC, Arduino, ESP, and ARM targets.</li>
                <li>Built-in simulation environment within Flowcode — perfect for rapid prototyping.</li>
            </ul>

            <div class="code-block">
                <pre>
<span style="color:#7aa2f7;">// FlowCode macro snippet (C code equivalent)</span>
<span style="color:#bb9af7;">LCD::PrintString</span>("Key:" + keypad::GetKey());
<span style="color:#2ac3de;">if</span>(key != NO_KEY) {
    buffer[ptr++] = key;
    LCD::SetCursor(0,1);
    LCD::PrintString("Input: ");
    LCD::PrintString(buffer);
}
<span style="color:#73daca;">// Debounce handled internally by FlowCode macro</span>
                </pre>
            </div>

            <div class="interactive-demo">
                <div style="display:flex; gap:8px; align-items:center;">
                    <span>📌</span> <strong style="color:#cbd5f0;">FlowCode Project Structure</strong>
                </div>
                <div style="margin-top: 12px;">
                    <table>
                        <tr><td style="padding:6px 0;">📁 Main flowchart</td><td style="color:#90e0ff;">LCD_Keypad_Controller.fcfx</td></tr>
                        <tr><td style="padding:6px 0;">🔌 Components:</td><td>LCD (HD44780) + Keypad (Matrix 4x4)</td></tr>
                        <tr><td style="padding:6px 0;">⚙️ Interrupts:</td><td>Timer for periodic key scanning</td></tr>
                        <tr><td style="padding:6px 0;">🎛️ Simulation:</td><td>Proteus VSM / Flowcode SCADA ready</td></tr>
                     </table>
                </div>
            </div>

            <div class="btn-group">
                <div class="btn btn-primary" id="resetDemoBtn">⟳ Reset LCD & Buffer</div>
                <div class="btn" id="copyFlowSnippet">📋 Copy FlowCode Macro</div>
            </div>
            <div class="pinout-example">
                <div style="display: flex; gap: 6px; flex-wrap: wrap; align-items: center;">
                    <span>✅ <strong>Hardware pinout example:</strong></span>
                    <span style="font-family: monospace; background:#00000033; padding: 2px 8px; border-radius: 20px;">LCD RS→RB0, E→RB1, D4-D7→RB4-RB7</span>
                    <span style="font-family: monospace; background:#00000033; padding: 2px 8px; border-radius: 20px;">Keypad Rows→RD0-RD3, Cols→RD4-RD7</span>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <span>🔧 FlowCode Advanced Project — LCD & Keypad integration | Fully open-source hardware design | MIT Licensed</span><br>
        <span style="font-size:0.7rem;">⭐ Star this repo if you build your own HMI panel!  •  Simulation ready for Flowcode v9+  •  Includes debouncing & real time entry</span>
    </footer>
</div>

<script>
    const keyMap = [
        ['1', '2', '3', 'A'],
        ['4', '5', '6', 'B'],
        ['7', '8', '9', 'C'],
        ['*', '0', '#', 'D']
    ];

    let inputString = "";
    let lastKeyPressed = "—";
    const lcdDisplayElement = document.getElementById('lcdLivePreview');
    const lastKeySpan = document.getElementById('lastKeyVal');
    const bufferSpan = document.getElementById('inputBuffer');

    function updateLCDAndDisplay() {
        let firstLine = "FlowCode Ready";
        let secondLine = inputString.length > 0 ? inputString : "> Enter text";
        if (secondLine.length > 16) secondLine = secondLine.slice(-16);
        if (firstLine.length > 16) firstLine = firstLine.slice(0, 16);
        lcdDisplayElement.innerHTML = `${firstLine}<br>${secondLine}`;
        bufferSpan.innerText = inputString.length ? inputString : "_";
    }

    function handleKeyPress(key) {
        if (!key) return;
        lastKeyPressed = key;
        lastKeySpan.innerText = key;
        
        inputString += key;
        if (inputString.length > 16) inputString = inputString.slice(-16);
        updateLCDAndDisplay();

        const activeButtons = document.querySelectorAll('.key');
        activeButtons.forEach(btn => {
            if (btn.innerText === key) {
                btn.style.transform = "translateY(2px)";
                btn.style.boxShadow = "0 1px 0 #0f172a";
                setTimeout(() => {
                    btn.style.transform = "";
                    btn.style.boxShadow = "0 4px 0 #0f172a";
                }, 100);
            }
        });

        if (key === 'A') {
            setTimeout(() => {
                lcdDisplayElement.innerHTML = `> Admin mode<br>Key A pressed`;
                setTimeout(() => updateLCDAndDisplay(), 800);
            }, 50);
        }
        if (key === 'D') {
            inputString = "";
            updateLCDAndDisplay();
            lastKeySpan.innerText = key + " (clear)";
            setTimeout(() => lastKeySpan.innerText = key, 800);
        }
        if (key === '#') {
            lcdDisplayElement.innerHTML = `✅ Data sent!<br>Buffer: ${inputString}`;
            setTimeout(() => updateLCDAndDisplay(), 1200);
        }
        if (key === '*') {
            lcdDisplayElement.innerHTML = `🔒 Backspace<br>Removing last char`;
            setTimeout(() => {
                if (inputString.length > 0) inputString = inputString.slice(0, -1);
                updateLCDAndDisplay();
            }, 180);
        }
    }

    function generateKeypadGrid() {
        const container = document.getElementById('interactiveKeypad');
        container.innerHTML = '';
        for (let row = 0; row < keyMap.length; row++) {
            for (let col = 0; col < keyMap[row].length; col++) {
                const keyVal = keyMap[row][col];
                const keyDiv = document.createElement('div');
                keyDiv.className = 'key';
                keyDiv.innerText = keyVal;
                keyDiv.setAttribute('data-key', keyVal);
                keyDiv.addEventListener('click', (e) => {
                    e.stopPropagation();
                    handleKeyPress(keyVal);
                });
                container.appendChild(keyDiv);
            }
        }
    }

    function resetSystem() {
        inputString = "";
        lastKeyPressed = "—";
        lastKeySpan.innerText = "—";
        updateLCDAndDisplay();
        lcdDisplayElement.innerHTML = "FlowCode Ready<br>System Reset OK";
        setTimeout(() => updateLCDAndDisplay(), 600);
        const resetBtn = document.getElementById('resetDemoBtn');
        resetBtn.style.transform = "scale(0.97)";
        setTimeout(() => resetBtn.style.transform = "", 150);
    }

    function copyMacroSnippet() {
        const snippet = `// FlowCode Macro: GetKeypad & LCD_Print
// 1. Call "Keypad::GetKeyPressed()" -> returns ASCII char
// 2. If key != 0 then LCD::PrintCharacter(key)
// 3. Use delay for debounce (10ms)
WHILE (1)
   key = Keypad::GetKey()
   IF (key != 0)
      LCD::PrintString("Pressed: ")
      LCD::PrintCharacter(key)
      DELAY_MS(200)
   ENDIF
ENDWHILE`;
        navigator.clipboard.writeText(snippet).then(() => {
            const copyBtn = document.getElementById('copyFlowSnippet');
            const originalText = copyBtn.innerHTML;
            copyBtn.innerHTML = "✅ Copied!";
            setTimeout(() => {
                copyBtn.innerHTML = originalText;
            }, 1500);
        });
    }

    window.addEventListener('DOMContentLoaded', () => {
        generateKeypadGrid();
        updateLCDAndDisplay();
        
        lcdDisplayElement.innerHTML = "> FlowCode v10<br>LCD + Keypad Matrix";
        setTimeout(() => updateLCDAndDisplay(), 1200);

        document.getElementById('resetDemoBtn').addEventListener('click', (e) => {
            e.preventDefault();
            resetSystem();
        });
        
        document.getElementById('copyFlowSnippet').addEventListener('click', (e) => {
            e.preventDefault();
            copyMacroSnippet();
        });
    });
</script>
</body>
</html>
