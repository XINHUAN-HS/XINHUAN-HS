<!-- 终端风格 CSS 注入 + 交互逻辑 -->
<style>
/* 基础终端样式 */
body {
    background-color: #000 !important;
    color: #00ff41 !important;
    font-family: 'Courier New', monospace !important;
    margin: 0;
    padding: 10px;
    line-height: 1.2;
}
a { color: #00ffff; text-decoration: none; }
a:hover { text-decoration: underline; }
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: rgba(0,20,0,0.5); }
::-webkit-scrollbar-thumb { background: #00ff41; border-radius: 2px; }

/* 终端窗口容器 */
.terminal-window {
    border: 1px solid #00ff41;
    box-shadow: 0 0 15px rgba(0, 255, 65, 0.3);
    margin: 15px 0;
    background: rgba(0, 20, 0, 0.2);
}
.terminal-header {
    background: linear-gradient(90deg, #003300 0%, #006600 100%);
    padding: 5px 10px;
    font-size: 12px;
    border-bottom: 1px solid #00ff41;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.terminal-controls span {
    display: inline-block;
    width: 12px;
    height: 12px;
    border-radius: 50%;
    margin-left: 5px;
    cursor: pointer;
}
.control-close { background: #ff5f56; }
.control-minimize { background: #ffbd2e; }
.control-maximize { background: #27ca3f; }

/* 交互式命令按钮 */
.cmd-button {
    display: inline-block;
    background: transparent;
    border: 1px solid #00ff41;
    color: #00ff41;
    padding: 5px 10px;
    margin: 5px 5px 5px 0;
    cursor: pointer;
    font-family: 'Courier New', monospace;
    transition: all 0.3s;
}
.cmd-button:hover {
    background: #00ff41;
    color: #000;
    box-shadow: 0 0 10px #00ff41;
}
input[type="checkbox"] { display: none; }

/* 命令输出区域 */
.cmd-output {
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.5s ease-out;
    border-top: 1px dashed #004400;
    margin-top: 10px;
}
input[type="checkbox"]:checked ~ .cmd-output {
    max-height: 500px;
    padding-top: 10px;
}

/* ASCII 动画 */
.ascii-art {
    white-space: pre;
    font-size: 10px;
    line-height: 1;
    text-align: center;
    animation: glitch 3s infinite;
}
@keyframes glitch {
    0%, 100% { opacity: 1; transform: translateX(0); }
    95% { opacity: 1; }
    96% { opacity: 0.8; transform: translateX(-2px); }
    97% { opacity: 0.9; transform: translateX(2px); }
    98% { opacity: 0.8; transform: translateX(-1px); }
}
.loading-bar {
    display: inline-block;
    width: 200px;
    height: 10px;
    border: 1px solid #00ff41;
    background: repeating-linear-gradient(
        90deg,
        #00ff41 0px,
        #00ff41 5px,
        transparent 5px,
        transparent 10px
    );
    background-size: 200% 100%;
    animation: loading 1s linear infinite;
}
@keyframes loading {
    0% { background-position: 0% 0; }
    100% { background-position: 200% 0; }
}
</style>

<!-- ASCII 启动动画 -->
<pre class="ascii-art terminal-window" align="center">
  _____  _ __  __ ___            _     _ 
 / ____|/ _| \ \/ / | |          | |   | |
| (___ | |_   \  /  | | ___ _ __ | |__ | |
 \___ \|  _|   \/   | |/ _ \ '_ \| '_ \| |
 ____) | | |   | |  | |  __/ | | | |_) |_|
|_____/|_| |_|  |_|  |_|\___|_| |_|_.__/(_)
                                        
> INITIALIZING SYSTEM...
> LOADING KERNEL MODULES...
> MOUNTING FILE SYSTEMS...
> STARTING AI CORES...
</pre>

## <div class="terminal-prompt">交互式控制台 [INTERACTIVE_CONSOLE]</div>

<div class="terminal-window">
<div class="terminal-header">
    <span>root@xinhuan:~</span>
    <div class="terminal-controls">
        <span class="control-close"></span>
        <span class="control-minimize"></span>
        <span class="control-maximize"></span>
    </div>
</div>
<div class="terminal-content">

<!-- 可点击命令按钮 -->
<label for="cmd-help" class="cmd-button">help</label>
<input type="checkbox" id="cmd-help">
<div class="cmd-output">
<pre>
AVAILABLE COMMANDS:
  help      - Show this help message
  whoami    - Display current user
  ls        - List directory contents
  neofetch  - Display system info
  clear     - Clear terminal output
</pre>
</div>

<label for="cmd-neofetch" class="cmd-button">neofetch</label>
<input type="checkbox" id="cmd-neofetch">
<div class="cmd-output">
<pre>
OS: Terminal OS 3.0 x86_64
Host: XINHUAN-HS Neural Engine
Kernel: 6.1.0-ai-generic
Uptime: 365 days, 12 hours
Packages: 1337 (pip)
Shell: bash 5.2.0
Terminal: tty1
CPU: AMD EPYC 7B13 (16) @ 2.45GHz
GPU: NVIDIA A100-SXM4-80GB
Memory: 32768MiB / 131072MiB
</pre>
</div>

<label for="cmd-ls" class="cmd-button">ls ~/projects</label>
<input type="checkbox" id="cmd-ls">
<div class="cmd-output">
<pre>
total 12
drwxr-xr-x  XINHUAN-HS/          # Main Config
drwxr-xr-x  XinHuanNewTab/       # Browser Extension
drwxr-xr-x  XinHuanToolKit/      # Dev Toolkit
-rw-r--r--  README.md            # This file
</pre>
</div>

<label for="cmd-matrix" class="cmd-button">start matrix</label>
<input type="checkbox" id="cmd-matrix">
<div class="cmd-output" align="center">
<pre class="ascii-art">
01001000 01100101 01101100 01101100 01101111
00100000 01010111 01101111 01110010 01101100
01100100 00100001 00100000 01000001 01001001
</pre>
<div class="loading-bar"></div>
<span style="color:#00ffff;">> Establishing secure connection...</span>
</div>

</div>
</div>

## <div class="terminal-prompt">实时数据流 [DATA_STREAM]</div>

<div class="terminal-window">
<div class="terminal-header">[ TOP - 10:00:00 ]</div>
<div class="terminal-content">

<!-- GitHub Stats 终端化 -->
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 10px;">
<div class="terminal-card">
<div class="card-title">>> CPU USAGE (COMMITS)</div>
<img src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=XINHUAN-HS&theme=transparent&background=000000&border_color=00ff41&title_color=00ffff&text_color=00ff41" width="100%"/>
</div>

<div class="terminal-card">
<div class="card-title">>> MEMORY (LANGUAGES)</div>
<img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=XINHUAN-HS&theme=transparent&background=000000&border_color=00ff41&title_color=00ffff&text_color=00ff41" width="100%"/>
</div>
</div>

</div>
</div>

## <div class="terminal-prompt">神经网络可视化 [NEURAL_VISUALIZER]</div>

<div class="terminal-window">
<div class="terminal-header">[ CONTRIBUTION GRAPH ]</div>
<div class="terminal-content" align="center">

<!-- 贪吃蛇动画 + ASCII 覆盖 -->
<div style="position: relative;">
<img src="https://raw.githubusercontent.com/platane/platane/output/github-contribution-grid-snake-dark.svg" width="100%" style="filter: hue-rotate(90deg) saturate(2); opacity: 0.8;"/>
<pre class="ascii-art" style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); font-size: 8px; color: #00ff41; text-shadow: 0 0 5px #00ff41;">
    ╭────────────────────────╮
    │  NEURAL NETWORK ACTIVE │
    │  PATTERN RECOGNIZED    │
    ╰────────────────────────╯
</pre>
</div>

</div>
</div>

## <div class="terminal-prompt">系统日志 [SYSLOG]</div>

<pre class="terminal-window">
> tail -f /var/log/system.log

[Jun 21 09:59:01] INFO: User 'XINHUAN-HS' authenticated successfully
[Jun 21 09:59:15] DEBUG: Loading LLM model weights... 100%
[Jun 21 09:59:32] INFO: GitHub API sync completed
[Jun 21 10:00:00] WARN: High commit activity detected in repo 'XinHuanToolKit'
[Jun 21 10:00:05] INFO: System running at optimal performance
[Jun 21 10:00:10] DEBUG: Heartbeat signal sent to monitoring server

> <span class="terminal-cursor"></span>
</pre>

---

<div align="center">
  <img src="https://komarev.com/ghpvc/?username=XINHUAN-HS&label=PROFILE+VIEWS&color=00ff41&style=for-the-badge&bg=000000" />
</div>

<pre align="center" class="ascii-art">
┌──────────────────────────────────────────┐
│  > SYSTEM ENTERING LOW POWER MODE        │
│  > PRESS ANY KEY TO WAKE UP             │
│  > 心尘随风落,幻影逐云流                 │
└──────────────────────────────────────────┘
</pre>