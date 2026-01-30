<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <title>Python Browser OS - Virtual Desktop & IDE</title>
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script>
    <script src="https://cdn.jsdelivr.net/pyodide/v0.23.4/full/pyodide.js"></script>

    <style>
        :root {
            --bg-darker: #0f0f0f;
            --bg-main: #1e1e1e;
            --bg-sidebar: #252526;
            --bg-activity: #333333;
            --border-color: #3c3c3c;
            --text-main: #cccccc;
            --text-bright: #ffffff;
            --accent: #007acc;
            --accent-hover: #118ad4;
            --vdg-bg: #1e1e2e;
            --win-header: #333333;
            --win-border: #444444;
        }

        body { 
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif; 
            display: flex; 
            height: 100vh; 
            margin: 0; 
            background: var(--bg-main); 
            color: var(--text-main); 
            overflow: hidden; 
        }

        /* Layout Structure */
        #activity-bar {
            width: 50px;
            background: var(--bg-activity);
            display: flex;
            flex-direction: column;
            align-items: center;
            padding-top: 15px;
            gap: 20px;
            z-index: 10;
        }

        .activity-icon {
            cursor: pointer;
            opacity: 0.6;
            transition: 0.2s;
            font-size: 24px;
        }
        .activity-icon.active { opacity: 1; color: var(--accent); }

        #sidebar {
            width: 260px;
            background: var(--bg-sidebar);
            border-right: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
        }

        #main-editor {
            flex: 1;
            display: flex;
            flex-direction: column;
            min-width: 0;
        }

        #vdg-container {
            display: none; /* Desktop view */
            flex: 1;
            background: var(--vdg-bg);
            background-image: radial-gradient(circle, #33334d 1px, transparent 1px);
            background-size: 30px 30px;
            position: relative;
            overflow: hidden;
        }

        #vdg-container.active { display: block; }

        /* File Tree */
        .sidebar-header {
            padding: 10px 15px;
            font-size: 11px;
            text-transform: uppercase;
            font-weight: bold;
            letter-spacing: 1px;
            display: flex;
            justify-content: space-between;
        }

        #file-list {
            list-style: none;
            padding: 0;
            margin: 0;
            overflow-y: auto;
        }

        .file-item {
            padding: 5px 20px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 13px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .file-item:hover { background: #2a2d2e; }
        .file-item.active { background: #37373d; color: white; }

        /* Tabs */
        #tabs {
            height: 35px;
            background: var(--bg-darker);
            display: flex;
            overflow-x: auto;
        }

        .tab {
            padding: 0 15px;
            height: 100%;
            display: flex;
            align-items: center;
            background: var(--bg-sidebar);
            border-right: 1px solid var(--border-color);
            cursor: pointer;
            font-size: 12px;
            min-width: 100px;
            max-width: 200px;
        }

        .tab.active { background: var(--bg-main); color: white; border-top: 1px solid var(--accent); }

        /* Code Input */
        #editor-container {
            flex: 1;
            position: relative;
        }

        #code-input {
            width: 100%;
            height: 100%;
            background: transparent;
            color: #d4d4d4;
            border: none;
            padding: 15px;
            font-family: 'Consolas', 'Monaco', monospace;
            font-size: 14px;
            resize: none;
            outline: none;
            tab-size: 4;
            box-sizing: border-box;
        }

        /* Bottom Panel - Console */
        #bottom-panel {
            height: 200px;
            border-top: 1px solid var(--border-color);
            background: var(--bg-darker);
            display: flex;
            flex-direction: column;
        }

        #terminal-header {
            padding: 5px 15px;
            font-size: 11px;
            background: var(--bg-sidebar);
            display: flex;
            gap: 20px;
        }

        #output {
            flex: 1;
            padding: 10px;
            font-family: 'Consolas', monospace;
            font-size: 12px;
            overflow-y: auto;
            white-space: pre-wrap;
            color: #ccc;
        }

        /* Virtual Desktop Components */
        .vd-window {
            position: absolute;
            background: #1e1e1e;
            border: 1px solid var(--win-border);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            display: flex;
            flex-direction: column;
            border-radius: 6px;
            overflow: hidden;
            min-width: 200px;
            min-height: 150px;
        }

        .win-header {
            background: var(--win-header);
            padding: 8px 12px;
            cursor: move;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 13px;
            user-select: none;
        }

        .win-close {
            color: #ff5f56;
            cursor: pointer;
            font-weight: bold;
        }

        .win-content {
            flex: 1;
            position: relative;
            background: #000;
        }

        canvas.win-canvas {
            display: block;
            width: 100%;
            height: 100%;
        }

        #vdg-taskbar {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            height: 40px;
            background: rgba(0,0,0,0.85);
            backdrop-filter: blur(10px);
            display: flex;
            align-items: center;
            padding: 0 10px;
            gap: 10px;
            z-index: 9999;
        }

        #vdg-clock {
            margin-left: auto;
            font-size: 13px;
            padding-right: 10px;
        }

        .run-btn {
            position: fixed;
            bottom: 220px;
            right: 30px;
            width: 50px;
            height: 50px;
            border-radius: 25px;
            background: var(--accent);
            color: white;
            border: none;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            z-index: 100;
        }

        .run-btn:hover { background: var(--accent-hover); transform: scale(1.05); }

    </style>
</head>
<body>

    <div id="activity-bar">
        <div class="activity-icon active" id="btn-editor" title="Editor">📝</div>
        <div class="activity-icon" id="btn-vdg" title="Virtual Desktop">🖥️</div>
        <div class="activity-icon" style="margin-top:auto; padding-bottom:15px;" title="Settings">⚙️</div>
    </div>

    <div id="sidebar">
        <div class="sidebar-header">
            <span>Explorer</span>
            <span style="cursor:pointer" onclick="createNewFile()">+</span>
        </div>
        <ul id="file-list"></ul>
    </div>

    <div id="main-editor">
        <div id="tabs"></div>
        <div id="editor-container">
            <textarea id="code-input" spellcheck="false" placeholder="# Start writing Python..."></textarea>
            <button class="run-btn" id="run-script" title="Run Script">▶</button>
        </div>
        <div id="bottom-panel">
            <div id="terminal-header">
                <span style="border-bottom: 1px solid var(--accent)">TERMINAL</span>
                <span>OUTPUT</span>
            </div>
            <div id="output">Initializing Pyodide System...</div>
        </div>
    </div>

    <div id="vdg-container">
        <div id="vdg-windows"></div>
        <div id="vdg-taskbar">
            <div style="font-weight:bold; color:var(--accent); cursor:pointer">PYTHON OS</div>
            <div id="vdg-clock">12:00 PM</div>
        </div>
    </div>

    <script>
        /**
         * GLOBAL STATE & VFS
         */
        let pyodide;
        let currentFile = 'main.py';
        let files = JSON.parse(localStorage.getItem('pvos_vfs')) || {
            'main.py': '# Multi-Window Python Graphics Demo\nimport js_bridge\nimport time\n\ndef main():\n    # Create a new window\n    win = js_bridge.create_window("Graphics Demo", 400, 300)\n    \n    # Draw something\n    win.fill_rect(50, 50, 100, 100, "red")\n    win.draw_text(60, 80, "Hello OS!", "white", "20px Arial")\n    \n    # Another window\n    win2 = js_bridge.create_window("Sub Process", 300, 200)\n    win2.fill_rect(0, 0, 300, 200, "#222")\n    \n    for i in range(10):\n        win2.clear()\n        win2.fill_rect(10 + (i*20), 50, 40, 40, "cyan")\n        time.sleep(0.5)\n\nmain()',
            'utils.py': 'def greet(name):\n    return f"Hello, {name}!"'
        };

        const vdg = document.getElementById('vdg-windows');
        const output = document.getElementById('output');
        const editor = document.getElementById('code-input');

        /**
         * WINDOW MANAGER (JavaScript Side)
         */
        const WindowManager = {
            windows: {},
            nextId: 1,

            create(title, width, height, pid) {
                const id = `win_${this.nextId++}`;
                const win = document.createElement('div');
                win.className = 'vd-window';
                win.id = id;
                win.style.width = width + 'px';
                win.style.height = height + 'px';
                win.style.left = (50 + (this.nextId * 20)) + 'px';
                win.style.top = (50 + (this.nextId * 20)) + 'px';
                win.style.zIndex = 1000 + this.nextId;

                win.innerHTML = `
                    <div class="win-header">
                        <span class="win-title">${title}</span>
                        <span class="win-close" onclick="WindowManager.close('${id}')">✕</span>
                    </div>
                    <div class="win-content">
                        <canvas class="win-canvas" width="${width}" height="${height - 35}"></canvas>
                    </div>
                `;

                this.makeDraggable(win);
                vdg.appendChild(win);
                
                const canvas = win.querySelector('canvas');
                const ctx = canvas.getContext('2d');

                this.windows[id] = { el: win, ctx, canvas, pid };
                return id;
            },

            close(id) {
                if (this.windows[id]) {
                    this.windows[id].el.remove();
                    delete this.windows[id];
                }
            },

            drawRect(id, x, y, w, h, color) {
                const win = this.windows[id];
                if (!win) return;
                win.ctx.fillStyle = color;
                win.ctx.fillRect(x, y, w, h);
            },

            drawText(id, x, y, text, color, font) {
                const win = this.windows[id];
                if (!win) return;
                win.ctx.fillStyle = color;
                win.ctx.font = font || "14px sans-serif";
                win.ctx.fillText(text, x, y);
            },

            clear(id) {
                const win = this.windows[id];
                if (!win) return;
                win.ctx.clearRect(0, 0, win.canvas.width, win.canvas.height);
            },

            makeDraggable(win) {
                let pos1 = 0, pos2 = 0, pos3 = 0, pos4 = 0;
                const header = win.querySelector('.win-header');
                
                header.onmousedown = (e) => {
                    e.preventDefault();
                    pos3 = e.clientX;
                    pos4 = e.clientY;
                    document.onmouseup = closeDragElement;
                    document.onmousemove = elementDrag;
                    // Bring to front
                    Object.values(this.windows).forEach(w => w.el.style.zIndex = 1000);
                    win.style.zIndex = 2000;
                };

                function elementDrag(e) {
                    e.preventDefault();
                    pos1 = pos3 - e.clientX;
                    pos2 = pos4 - e.clientY;
                    pos3 = e.clientX;
                    pos4 = e.clientY;
                    win.style.top = (win.offsetTop - pos2) + "px";
                    win.style.left = (win.offsetLeft - pos1) + "px";
                }

                function closeDragElement() {
                    document.onmouseup = null;
                    document.onmousemove = null;
                }
            }
        };

        /**
         * PYODIDE & RUNTIME BRIDGE
         */
        async function initPyodide() {
            try {
                pyodide = await loadPyodide();
                output.innerText = "--- Python OS Kernel Loaded ---\nReady for execution.\n";
                
                // Expose JS Bridge to Python
                pyodide.registerJsModule("js_bridge", {
                    create_window: (title, w, h) => {
                        const winId = WindowManager.create(title, w, h, 1);
                        // Return an object that mirrors the window functions
                        return {
                            id: winId,
                            fill_rect: (x, y, w, h, color) => WindowManager.drawRect(winId, x, y, w, h, color),
                            draw_text: (x, y, txt, col, f) => WindowManager.drawText(winId, x, y, txt, col, f),
                            clear: () => WindowManager.clear(winId),
                            close: () => WindowManager.close(winId)
                        };
                    },
                    print_to_console: (msg) => {
                        output.innerText += msg + "\n";
                    }
                });

            } catch (err) {
                output.innerText = "Error loading Pyodide: " + err;
            }
        }

        async function runPython() {
            if (!pyodide) return;
            const code = editor.value;
            output.innerText = ">>> Running script...\n";
            
            try {
                // Sync VFS to Pyodide
                for (const [name, content] of Object.entries(files)) {
                    pyodide.FS.writeFile(name, content);
                }

                await pyodide.runPythonAsync(code);
                output.innerText += "\n--- Process Finished ---\n";
            } catch (err) {
                output.innerText += "\n[Runtime Error]: " + err + "\n";
            }
        }

        /**
         * UI CONTROLS
         */
        function updateFileList() {
            const list = document.getElementById('file-list');
            list.innerHTML = '';
            Object.keys(files).forEach(filename => {
                const li = document.createElement('li');
                li.className = `file-item ${filename === currentFile ? 'active' : ''}`;
                li.innerHTML = `<span>📄</span> ${filename}`;
                li.onclick = () => switchFile(filename);
                list.appendChild(li);
            });
            localStorage.setItem('pvos_vfs', JSON.stringify(files));
        }

        function switchFile(filename) {
            files[currentFile] = editor.value;
            currentFile = filename;
            editor.value = files[filename];
            updateFileList();
            updateTabs();
        }

        function createNewFile() {
            const name = prompt("Enter filename (e.g. app.py):");
            if (name && !files[name]) {
                files[name] = "# New Python Script";
                switchFile(name);
            }
        }

        function updateTabs() {
            const tabs = document.getElementById('tabs');
            tabs.innerHTML = '';
            // Only show active file tab for now
            const tab = document.createElement('div');
            tab.className = 'tab active';
            tab.innerText = currentFile;
            tabs.appendChild(tab);
        }

        // View Toggling
        document.getElementById('btn-editor').onclick = () => {
            document.getElementById('main-editor').style.display = 'flex';
            document.getElementById('vdg-container').classList.remove('active');
            document.getElementById('btn-editor').classList.add('active');
            document.getElementById('btn-vdg').classList.remove('active');
        };

        document.getElementById('btn-vdg').onclick = () => {
            document.getElementById('main-editor').style.display = 'none';
            document.getElementById('vdg-container').classList.add('active');
            document.getElementById('btn-vdg').classList.add('active');
            document.getElementById('btn-editor').classList.remove('active');
        };

        document.getElementById('run-script').onclick = runPython;

        // Clock
        function updateClock() {
            const now = new Date();
            document.getElementById('vdg-clock').innerText = now.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });
        }

        // Init
        window.onload = () => {
            editor.value = files[currentFile];
            updateFileList();
            updateTabs();
            initPyodide();
            setInterval(updateClock, 1000);
        };

        // Tab support in textarea
        editor.onkeydown = function(e) {
            if (e.key === 'Tab') {
                e.preventDefault();
                const start = this.selectionStart;
                const end = this.selectionEnd;
                this.value = this.value.substring(0, start) + "    " + this.value.substring(end);
                this.selectionStart = this.selectionEnd = start + 4;
            }
        };

    </script>
</body>
</html>
