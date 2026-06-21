<!-- 终端风格 CSS 注入 -->
<style>
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

/* 终端容器 */
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
}
.terminal-content {
    padding: 15px;
}
.terminal-prompt::before { content: "root@xinhuan:~# "; color: #ff5f6d; }
.terminal-cursor {
    display: inline-block;
    width: 8px;
    height: 16px;
    background: #00ff41;
    animation: blink 1s infinite;
    vertical-align: middle;
}
@keyframes blink { 0%,50% { opacity: 1; } 51%,100% { opacity: 0; } }

/* 进度条 */
.progress-bar {
    display: inline-block;
    width: 200px;
    height: 12px;
    border: 1px solid #00ff41;
    background: #001100;
    position: relative;
    margin: 0 10px;
}
.progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #003300 0%, #00ff41 100%);
    transition: width 2s ease;
}

/* 卡片网格 */
.card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 15px;
    margin: 15px 0;
}
.terminal-card {
    border: 1px solid #00ff41;
    background: rgba(0, 30, 0, 0.3);
    padding: 10px;
}
.card-title {
    color: #00ffff;
    border-bottom: 1px dashed #00ff41;
    padding-bottom: 5px;
    margin-bottom: 10px;
}
</style>

<!-- ASCII 启动画面 -->
<pre class="terminal-window">
┌─────────────────────────────────────────────────────────────┐
│                    SYSTEM BOOT SEQUENCE                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ██╗  ██╗██╗  ██╗██╗   ██╗ █████╗ ███╗   ██╗               │
│  ╚██╗██╔╝██║  ██║██║   ██║██╔══██╗████╗  ██║               │
│   ╚███╔╝ ███████║██║   ██║███████║██╔██╗ ██║               │
│   ██╔██╗ ██╔══██║██║   ██║██╔══██║██║╚██╗██║               │
│  ██╔╝ ██╗██║  ██║╚██████╔╝██║  ██║██║ ╚████║               │
│  ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═══╝               │
│                                                             │
│  > INITIALIZING NEURAL NETWORKS... DONE                    │
│  > LOADING LLM MODELS... DONE                              │
│  > CONNECTING TO GITHUB API... DONE                        │
│  > SYSTEM READY                                             │
│                                                             │
│  USER: XINHUAN-HS                                           │
│  CLEARANCE: ROOT                                            │
│  LAST LOGIN: 2026-06-21 10:00:00 UTC                       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
</pre>

## <div class="terminal-prompt">核心能力扫描 [CAPABILITY_SCAN]</div>

<div class="card-grid">
<div class="terminal-card">
<div class="card-title">>> AI/ML ENGINE</div>
<pre>
[████████████████████] 100% LLM Training
[██████████████████░░]  95% RLHF Tuning
[████████████████████] 100% Multi-Agent Systems
[███████████████████░]  98% Model Deployment
</pre>
</div>

<div class="terminal-card">
<div class="card-title">>> SYSTEM ARCHITECTURE</div>
<pre>
[████████████████████] 100% Distributed DB
[████████████████████] 100% Vector DB (RAG)
[███████████████████░]  97% Knowledge Graphs
[████████████████████] 100% Cloud Infrastructure
</pre>
</div>
</div>

## <div class="terminal-prompt">实时系统监控 [SYSTEM_MONITOR]</div>

<div class="terminal-window">
<div class="terminal-header">[ ACTIVE_PROCESSES ]</div>
<div class="terminal-content">

<!-- GitHub Stats 终端化 -->
<div class="card-grid">
<div class="terminal-card">
<div class="card-title">>> CONTRIBUTION STATS</div>
<img src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=XINHUAN-HS&theme=transparent&background=000000&border_color=00ff41&title_color=00ffff&text_color=00ff41" width="100%"/>
</div>

<div class="terminal-card">
<div class="card-title">>> LANGUAGE DISTRIBUTION</div>
<img src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=XINHUAN-HS&theme=transparent&background=000000&border_color=00ff41&title_color=00ffff&text_color=00ff41" width="100%"/>
</div>

<div class="terminal-card">
<div class="card-title">>> COMMIT ACTIVITY</div>
<img src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=XINHUAN-HS&theme=transparent&background=000000&border_color=00ff41&title_color=00ffff&text_color=00ff41" width="100%"/>
</div>
</div>

</div>
</div>

## <div class="terminal-prompt">神经网络活动图 [NEURAL_ACTIVITY]</div>

<div class="terminal-window">
<div class="terminal-header">[ CONTRIBUTION_GRAPH ]</div>
<div class="terminal-content" align="center">

<!-- 贪吃蛇动画终端化 -->
<img src="https://raw.githubusercontent.com/platane/platane/output/github-contribution-grid-snake-dark.svg" width="100%" style="border: 1px solid #00ff41; filter: hue-rotate(90deg) saturate(2);"/>

<pre>
> ANALYZING PATTERN...
> DETECTED: REGULAR COMMIT CYCLES
> PREDICTION: HIGH ACTIVITY IN Q3 2026
> STATUS: OPTIMAL
</pre>
</div>
</div>

## <div class="terminal-prompt">仓库索引 [REPOSITORY_INDEX]</div>

<div class="terminal-window">
<div class="terminal-header">[ ls -la ~/projects/ ]</div>
<div class="terminal-content">

| 仓库 | 描述 | 状态 | 星标 |
|:----:|:-----|:----:|:----:|
| [XINHUAN-HS](https://github.com/XINHUAN-HS/XINHUAN-HS) | 核心配置档案 | `ACTIVE` | ★ 42 |
| [XinHuanNewTab](https://github.com/XINHUAN-HS/XinHuanNewTab) | 新标签页系统 | `STABLE` | ★ 18 |
| [XinHuanToolKit](https://github.com/XINHUAN-HS/XinHuanToolKit) | 开发工具包 | `DEV` | ★ 31 |

</div>
</div>

## <div class="terminal-prompt">系统诊断 [DIAGNOSTICS]</div>

<pre class="terminal-window">
> ping github.com
64 bytes from github.com: seq=1 ttl=56 time=12.3 ms
64 bytes from github.com: seq=2 ttl=56 time=11.9 ms

> whoami
root@xinhuan-hs

> uptime
10:00:00 up 365 days, load average: 0.42, 0.38, 0.41

> free -h
              total        used        free
Mem:           32G          12G         20G
Swap:          8G           0G          8G

> echo $PHILOSOPHY
"心尘随风落,幻影逐云流"

> <span class="terminal-cursor"></span>
</pre>

---

<div align="center">
  <img src="https://komarev.com/ghpvc/?username=XINHUAN-HS&label=PROFILE+VIEWS&color=00ff41&style=for-the-badge&bg=000000" />
</div>

<pre align="center" style="border: 1px solid #00ff41; padding: 10px; display: inline-block;">
┌──────────────────────────────────────────┐
│  > CONNECTION TERMINATED                 │
│  > SESSION CLOSED                        │
│  > SYSTEM HIBERNATING...                 │
└──────────────────────────────────────────┘
</pre>