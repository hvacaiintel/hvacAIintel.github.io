<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>HVAC AI Intel — The Intelligence Layer for Modern Climate Control</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=IBM+Plex+Mono:wght@400;500&family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>
  :root {
    --bg: #060c14;
    --bg2: #0b1422;
    --bg3: #0f1d30;
    --accent: #00d4ff;
    --accent2: #ff6b35;
    --accent3: #7fff4f;
    --text: #e8f4fd;
    --text-muted: #7a9bb5;
    --border: rgba(0, 212, 255, 0.15);
    --card: rgba(11, 20, 34, 0.8);
    --glow: rgba(0, 212, 255, 0.08);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Outfit', sans-serif;
    background: var(--bg);
    color: var(--text);
    overflow-x: hidden;
    line-height: 1.6;
  }

  /* === NOISE OVERLAY === */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: 0.4;
  }

  /* === NAV === */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 18px 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: rgba(6, 12, 20, 0.85);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
  }

  .nav-logo {
    display: flex;
    align-items: center;
    gap: 12px;
    text-decoration: none;
  }

  .nav-logo-icon {
    width: 36px; height: 36px;
    background: linear-gradient(135deg, var(--accent), #0077a8);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-family: 'IBM Plex Mono', monospace;
    font-size: 13px;
    font-weight: 500;
    color: #000;
    letter-spacing: -1px;
  }

  .nav-logo-text {
    font-family: 'DM Serif Display', serif;
    font-size: 18px;
    color: var(--text);
    letter-spacing: 0.02em;
  }

  .nav-logo-text span { color: var(--accent); }

  .nav-links {
    display: flex;
    align-items: center;
    gap: 32px;
    list-style: none;
  }

  .nav-links a {
    color: var(--text-muted);
    text-decoration: none;
    font-size: 13px;
    font-weight: 500;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--accent); }

  .nav-cta {
    background: var(--accent);
    color: #000 !important;
    padding: 8px 20px;
    border-radius: 6px;
    font-weight: 600 !important;
    transition: all 0.2s !important;
  }

  .nav-cta:hover {
    background: #00b8d9 !important;
    color: #000 !important;
    transform: translateY(-1px);
    box-shadow: 0 4px 20px rgba(0, 212, 255, 0.4);
  }

  /* === HERO === */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 120px 40px 80px;
    position: relative;
    text-align: center;
    overflow: hidden;
  }

  .hero-grid {
    position: absolute;
    inset: 0;
    background-image: 
      linear-gradient(rgba(0, 212, 255, 0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0, 212, 255, 0.04) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 80% 60% at 50% 50%, black, transparent);
  }

  .hero-orb1 {
    position: absolute;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(0, 212, 255, 0.12) 0%, transparent 70%);
    top: -100px; left: -100px;
    pointer-events: none;
  }

  .hero-orb2 {
    position: absolute;
    width: 500px; height: 500px;
    background: radial-gradient(circle, rgba(255, 107, 53, 0.08) 0%, transparent 70%);
    bottom: -50px; right: -50px;
    pointer-events: none;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    border: 1px solid var(--border);
    background: rgba(0, 212, 255, 0.06);
    padding: 6px 16px;
    border-radius: 100px;
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 28px;
    position: relative;
  }

  .hero-badge::before {
    content: '';
    width: 6px; height: 6px;
    background: var(--accent3);
    border-radius: 50%;
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.8); }
  }

  .hero h1 {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(42px, 7vw, 90px);
    line-height: 1.05;
    color: var(--text);
    margin-bottom: 10px;
    position: relative;
    letter-spacing: -0.02em;
  }

  .hero h1 em {
    font-style: italic;
    color: var(--accent);
  }

  .hero-sub {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(22px, 3.5vw, 42px);
    color: var(--text-muted);
    margin-bottom: 24px;
    font-style: italic;
  }

  .hero-desc {
    max-width: 620px;
    font-size: 16px;
    color: var(--text-muted);
    line-height: 1.7;
    margin-bottom: 44px;
    position: relative;
  }

  .hero-actions {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    justify-content: center;
    position: relative;
  }

  .btn-primary {
    background: var(--accent);
    color: #000;
    padding: 14px 32px;
    border-radius: 8px;
    font-weight: 600;
    font-size: 15px;
    text-decoration: none;
    transition: all 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 8px;
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 30px rgba(0, 212, 255, 0.4);
    background: #00e5ff;
  }

  .btn-secondary {
    background: transparent;
    color: var(--text);
    padding: 14px 32px;
    border-radius: 8px;
    font-weight: 500;
    font-size: 15px;
    text-decoration: none;
    border: 1px solid var(--border);
    transition: all 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 8px;
  }

  .btn-secondary:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(0, 212, 255, 0.05);
  }

  .hero-stats {
    display: flex;
    gap: 48px;
    margin-top: 64px;
    padding-top: 48px;
    border-top: 1px solid var(--border);
    position: relative;
    flex-wrap: wrap;
    justify-content: center;
  }

  .stat {
    text-align: center;
  }

  .stat-number {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 32px;
    color: var(--accent);
    font-weight: 500;
    display: block;
  }

  .stat-label {
    font-size: 12px;
    color: var(--text-muted);
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  /* === SECTIONS === */
  section {
    padding: 96px 40px;
    position: relative;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
  }

  .section-eyebrow {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 12px;
    display: block;
  }

  .section-title {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(28px, 4vw, 48px);
    color: var(--text);
    line-height: 1.15;
    margin-bottom: 16px;
  }

  .section-desc {
    font-size: 16px;
    color: var(--text-muted);
    max-width: 580px;
    line-height: 1.7;
  }

  .section-header {
    margin-bottom: 60px;
  }

  /* === ROADMAP / PILLARS === */
  .pillars {
    background: var(--bg2);
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
  }

  .pillars-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2px;
    background: var(--border);
    border-radius: 16px;
    overflow: hidden;
  }

  .pillar-card {
    background: var(--bg2);
    padding: 40px;
    position: relative;
    transition: background 0.3s;
  }

  .pillar-card:hover { background: var(--bg3); }

  .pillar-num {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.15em;
    margin-bottom: 20px;
    display: block;
  }

  .pillar-icon {
    width: 48px; height: 48px;
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 22px;
    margin-bottom: 20px;
    position: relative;
  }

  .pillar-icon.blue { background: rgba(0, 212, 255, 0.12); }
  .pillar-icon.orange { background: rgba(255, 107, 53, 0.12); }
  .pillar-icon.green { background: rgba(127, 255, 79, 0.12); }

  .pillar-card h3 {
    font-family: 'DM Serif Display', serif;
    font-size: 22px;
    color: var(--text);
    margin-bottom: 10px;
  }

  .pillar-card p {
    font-size: 14px;
    color: var(--text-muted);
    line-height: 1.7;
  }

  .pillar-tag {
    display: inline-block;
    margin-top: 20px;
    font-family: 'IBM Plex Mono', monospace;
    font-size: 10px;
    padding: 4px 10px;
    border-radius: 4px;
    color: var(--accent);
    border: 1px solid rgba(0, 212, 255, 0.2);
    background: rgba(0, 212, 255, 0.04);
  }

  /* === YOUTUBE SECTION === */
  .youtube-section {
    background: var(--bg);
  }

  .yt-header {
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    margin-bottom: 48px;
    flex-wrap: wrap;
    gap: 20px;
  }

  .yt-channel-link {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: #ff0000;
    color: #fff;
    padding: 10px 20px;
    border-radius: 8px;
    text-decoration: none;
    font-weight: 600;
    font-size: 14px;
    transition: all 0.2s;
    white-space: nowrap;
  }

  .yt-channel-link:hover {
    background: #cc0000;
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(255, 0, 0, 0.3);
  }

  .yt-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 24px;
    margin-bottom: 40px;
  }

  .yt-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    transition: all 0.3s;
    cursor: pointer;
    text-decoration: none;
    color: inherit;
    display: block;
  }

  .yt-card:hover {
    border-color: rgba(0, 212, 255, 0.35);
    transform: translateY(-4px);
    box-shadow: 0 16px 40px rgba(0, 0, 0, 0.4), 0 0 0 1px rgba(0, 212, 255, 0.15);
  }

  .yt-thumb {
    width: 100%;
    aspect-ratio: 16/9;
    background: var(--bg3);
    position: relative;
    overflow: hidden;
  }

  .yt-thumb img {
    width: 100%; height: 100%;
    object-fit: cover;
    transition: transform 0.4s;
  }

  .yt-card:hover .yt-thumb img { transform: scale(1.04); }

  .yt-play {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(0, 0, 0, 0.3);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .yt-card:hover .yt-play { opacity: 1; }

  .yt-play-btn {
    width: 56px; height: 56px;
    background: rgba(255, 0, 0, 0.9);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    color: #fff;
    font-size: 22px;
  }

  .yt-info {
    padding: 20px;
  }

  .yt-info h4 {
    font-size: 15px;
    font-weight: 600;
    color: var(--text);
    line-height: 1.4;
    margin-bottom: 8px;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }

  .yt-meta {
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 12px;
    color: var(--text-muted);
    font-family: 'IBM Plex Mono', monospace;
  }

  .yt-tag {
    padding: 2px 8px;
    background: rgba(0, 212, 255, 0.08);
    border: 1px solid rgba(0, 212, 255, 0.15);
    border-radius: 4px;
    font-size: 10px;
    color: var(--accent);
  }

  .yt-loading {
    text-align: center;
    padding: 60px 20px;
    color: var(--text-muted);
    font-family: 'IBM Plex Mono', monospace;
    font-size: 13px;
  }

  .yt-loading-spinner {
    width: 32px; height: 32px;
    border: 2px solid var(--border);
    border-top-color: var(--accent);
    border-radius: 50%;
    animation: spin 0.8s linear infinite;
    margin: 0 auto 16px;
  }

  @keyframes spin { to { transform: rotate(360deg); } }

  .yt-placeholder-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 24px;
  }

  .yt-placeholder-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
  }

  .yt-placeholder-thumb {
    width: 100%;
    aspect-ratio: 16/9;
    background: linear-gradient(135deg, #0b1422, #0f1d30);
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    gap: 12px;
    color: var(--text-muted);
    font-size: 13px;
    font-family: 'IBM Plex Mono', monospace;
    padding: 20px;
    text-align: center;
  }

  .yt-placeholder-thumb .yt-icon {
    font-size: 32px;
    opacity: 0.4;
  }

  .yt-placeholder-info {
    padding: 20px;
  }

  .yt-placeholder-title {
    height: 14px;
    background: var(--bg3);
    border-radius: 4px;
    margin-bottom: 8px;
    width: 85%;
  }

  .yt-placeholder-title2 {
    height: 14px;
    background: var(--bg3);
    border-radius: 4px;
    margin-bottom: 16px;
    width: 65%;
  }

  .yt-placeholder-meta {
    height: 10px;
    background: var(--bg3);
    border-radius: 4px;
    width: 50%;
  }

  /* === KNOWLEDGE SECTION === */
  .knowledge-section {
    background: var(--bg2);
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
  }

  .knowledge-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
    gap: 20px;
  }

  .knowledge-card {
    background: var(--bg);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 32px;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }

  .knowledge-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .knowledge-card:hover {
    border-color: rgba(0, 212, 255, 0.3);
    transform: translateY(-3px);
    box-shadow: 0 12px 40px rgba(0, 0, 0, 0.3);
  }

  .knowledge-card:hover::before { opacity: 1; }

  .knowledge-icon {
    font-size: 28px;
    margin-bottom: 16px;
    display: block;
  }

  .knowledge-card h3 {
    font-family: 'DM Serif Display', serif;
    font-size: 20px;
    color: var(--text);
    margin-bottom: 10px;
  }

  .knowledge-card p {
    font-size: 14px;
    color: var(--text-muted);
    line-height: 1.7;
    margin-bottom: 20px;
  }

  .knowledge-topics {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .topic-tag {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 10px;
    padding: 3px 9px;
    border-radius: 4px;
    background: rgba(0, 212, 255, 0.06);
    border: 1px solid rgba(0, 212, 255, 0.12);
    color: var(--text-muted);
    transition: all 0.2s;
  }

  .topic-tag:hover {
    background: rgba(0, 212, 255, 0.12);
    color: var(--accent);
    border-color: rgba(0, 212, 255, 0.25);
  }

  /* AI CHAT WIDGET */
  .ai-chat-section {
    background: var(--bg);
  }

  .ai-chat-wrapper {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 20px;
    overflow: hidden;
    max-width: 760px;
    margin: 0 auto;
  }

  .ai-chat-header {
    padding: 20px 28px;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 12px;
    background: var(--bg3);
  }

  .ai-chat-header-dot {
    width: 10px; height: 10px;
    border-radius: 50%;
    background: var(--accent3);
    animation: pulse 2s ease-in-out infinite;
  }

  .ai-chat-header-title {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 13px;
    color: var(--text-muted);
  }

  .ai-chat-header-title strong {
    color: var(--accent);
    font-weight: 500;
  }

  .chat-messages {
    padding: 28px;
    min-height: 200px;
    max-height: 360px;
    overflow-y: auto;
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .chat-messages::-webkit-scrollbar { width: 4px; }
  .chat-messages::-webkit-scrollbar-track { background: transparent; }
  .chat-messages::-webkit-scrollbar-thumb { background: var(--border); border-radius: 2px; }

  .msg {
    display: flex;
    gap: 12px;
    animation: fadeIn 0.3s ease;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(8px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .msg.user { flex-direction: row-reverse; }

  .msg-avatar {
    width: 32px; height: 32px;
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 14px;
    flex-shrink: 0;
  }

  .msg.ai .msg-avatar { background: rgba(0, 212, 255, 0.12); }
  .msg.user .msg-avatar { background: rgba(255, 107, 53, 0.12); }

  .msg-bubble {
    max-width: 75%;
    padding: 12px 18px;
    border-radius: 12px;
    font-size: 14px;
    line-height: 1.6;
  }

  .msg.ai .msg-bubble {
    background: var(--bg3);
    color: var(--text);
    border: 1px solid var(--border);
    border-top-left-radius: 4px;
  }

  .msg.user .msg-bubble {
    background: rgba(0, 212, 255, 0.1);
    color: var(--text);
    border: 1px solid rgba(0, 212, 255, 0.2);
    border-top-right-radius: 4px;
    text-align: right;
  }

  .chat-input-area {
    padding: 20px 28px;
    border-top: 1px solid var(--border);
    display: flex;
    gap: 12px;
    align-items: center;
    background: var(--bg3);
  }

  .chat-input {
    flex: 1;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px 18px;
    color: var(--text);
    font-family: 'Outfit', sans-serif;
    font-size: 14px;
    outline: none;
    transition: border-color 0.2s;
  }

  .chat-input:focus { border-color: rgba(0, 212, 255, 0.4); }
  .chat-input::placeholder { color: var(--text-muted); }

  .chat-send {
    background: var(--accent);
    color: #000;
    border: none;
    border-radius: 10px;
    padding: 12px 22px;
    font-family: 'Outfit', sans-serif;
    font-weight: 600;
    font-size: 14px;
    cursor: pointer;
    transition: all 0.2s;
    display: flex;
    align-items: center;
    gap: 8px;
    white-space: nowrap;
  }

  .chat-send:hover:not(:disabled) {
    background: #00e5ff;
    transform: translateY(-1px);
    box-shadow: 0 4px 16px rgba(0, 212, 255, 0.35);
  }

  .chat-send:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }

  .suggested-qs {
    padding: 0 28px 20px;
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .suggested-q {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    padding: 6px 12px;
    border: 1px solid var(--border);
    border-radius: 6px;
    color: var(--text-muted);
    background: transparent;
    cursor: pointer;
    transition: all 0.2s;
    text-align: left;
  }

  .suggested-q:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(0, 212, 255, 0.05);
  }

  /* === ABOUT === */
  .about-section {
    background: var(--bg2);
    border-top: 1px solid var(--border);
  }

  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: center;
  }

  @media (max-width: 768px) {
    .about-grid { grid-template-columns: 1fr; gap: 40px; }
  }

  .about-visual {
    position: relative;
  }

  .about-card {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 40px;
    position: relative;
    overflow: hidden;
  }

  .about-card::after {
    content: '';
    position: absolute;
    bottom: -40px; right: -40px;
    width: 200px; height: 200px;
    background: radial-gradient(circle, rgba(0, 212, 255, 0.08), transparent 70%);
    pointer-events: none;
  }

  .about-avatar {
    width: 72px; height: 72px;
    border-radius: 16px;
    background: linear-gradient(135deg, var(--accent), #0077a8);
    display: flex; align-items: center; justify-content: center;
    font-size: 30px;
    margin-bottom: 20px;
  }

  .about-name {
    font-family: 'DM Serif Display', serif;
    font-size: 24px;
    color: var(--text);
    margin-bottom: 4px;
  }

  .about-role {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--accent);
    margin-bottom: 20px;
  }

  .about-bio {
    font-size: 14px;
    color: var(--text-muted);
    line-height: 1.7;
    margin-bottom: 24px;
  }

  .about-badges {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .about-badge {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 10px;
    padding: 4px 10px;
    border-radius: 5px;
    border: 1px solid rgba(127, 255, 79, 0.2);
    background: rgba(127, 255, 79, 0.06);
    color: var(--accent3);
  }

  .about-content h2 {
    font-family: 'DM Serif Display', serif;
    font-size: 38px;
    color: var(--text);
    line-height: 1.2;
    margin-bottom: 20px;
  }

  .about-content p {
    font-size: 15px;
    color: var(--text-muted);
    line-height: 1.8;
    margin-bottom: 16px;
  }

  /* === FOOTER === */
  footer {
    background: var(--bg2);
    border-top: 1px solid var(--border);
    padding: 60px 40px 40px;
  }

  .footer-inner {
    max-width: 1200px;
    margin: 0 auto;
  }

  .footer-top {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    flex-wrap: wrap;
    gap: 40px;
    margin-bottom: 48px;
    padding-bottom: 48px;
    border-bottom: 1px solid var(--border);
  }

  .footer-brand p {
    font-size: 13px;
    color: var(--text-muted);
    max-width: 280px;
    line-height: 1.7;
    margin-top: 12px;
  }

  .footer-links h4 {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .footer-links ul { list-style: none; }

  .footer-links li {
    margin-bottom: 10px;
  }

  .footer-links a {
    color: var(--text-muted);
    text-decoration: none;
    font-size: 14px;
    transition: color 0.2s;
  }

  .footer-links a:hover { color: var(--accent); }

  .footer-bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 16px;
  }

  .footer-copy {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: var(--text-muted);
  }

  .footer-social {
    display: flex;
    gap: 12px;
  }

  .social-link {
    width: 36px; height: 36px;
    border: 1px solid var(--border);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    color: var(--text-muted);
    text-decoration: none;
    font-size: 14px;
    transition: all 0.2s;
  }

  .social-link:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(0, 212, 255, 0.05);
  }

  /* === TYPING CURSOR === */
  .typing::after {
    content: '|';
    animation: blink 1s infinite;
    color: var(--accent);
  }
  @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

  /* === SCROLLBAR === */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }

  /* === RESPONSIVE === */
  @media (max-width: 768px) {
    nav { padding: 14px 20px; }
    .nav-links { display: none; }
    section { padding: 64px 20px; }
    .hero { padding: 100px 20px 60px; }
    .hero-stats { gap: 28px; }
    footer { padding: 40px 20px; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">
    <div class="nav-logo-icon">AI</div>
    <span class="nav-logo-text">HVAC<span>AI</span>Intel</span>
  </a>
  <ul class="nav-links">
    <li><a href="#pillars">Roadmap</a></li>
    <li><a href="#videos">Videos</a></li>
    <li><a href="#knowledge">Knowledge</a></li>
    <li><a href="#ask-ai">Ask AI</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="https://www.youtube.com/channel/UCOLrk1nHdHxeZrcKtERo-ow" target="_blank" class="nav-cta">▶ Subscribe</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-grid"></div>
  <div class="hero-orb1"></div>
  <div class="hero-orb2"></div>

  <div class="hero-badge">
    @hvacAIintel · Society AI HVAC Encyclopedia Winner
  </div>

  <h1>The <em>Intelligence</em><br>Layer for Climate</h1>
  <p class="hero-sub">Where Neural Networks Meet HVAC Engineering</p>

  <p class="hero-desc">
    Bridging 20+ years of VRV/VRF systems, psychrometrics, and UAE climate engineering with cutting-edge AI — to build the digital future of HVAC design, energy efficiency, and automation.
  </p>

  <div class="hero-actions">
    <a href="#knowledge" class="btn-primary">
      <span>🧠</span> Explore Knowledge Base
    </a>
    <a href="https://www.youtube.com/channel/UCOLrk1nHdHxeZrcKtERo-ow" target="_blank" class="btn-secondary">
      <span>▶</span> Watch on YouTube
    </a>
  </div>

  <div class="hero-stats">
    <div class="stat">
      <span class="stat-number">20+</span>
      <span class="stat-label">Years Experience</span>
    </div>
    <div class="stat">
      <span class="stat-number">VRV/VRF</span>
      <span class="stat-label">Specialist</span>
    </div>
    <div class="stat">
      <span class="stat-number">UAE</span>
      <span class="stat-label">Climate Expert</span>
    </div>
    <div class="stat">
      <span class="stat-number">AI</span>
      <span class="stat-label">Powered Tools</span>
    </div>
  </div>
</section>

<!-- PILLARS -->
<section class="pillars" id="pillars">
  <div class="container">
    <div class="section-header">
      <span class="section-eyebrow">// Digitization Roadmap</span>
      <h2 class="section-title">From Mechanical to Intelligent</h2>
      <p class="section-desc">A structured pathway from traditional HVAC to AI-driven autonomous climate control systems.</p>
    </div>

    <div class="pillars-grid">
      <div class="pillar-card">
        <span class="pillar-num">01 — FOUNDATION</span>
        <div class="pillar-icon blue">📡</div>
        <h3>Data Ingestion & IoT</h3>
        <p>Move beyond manual logs. Digitize physical variables — Temperature, Flow, Static Pressure — using Modbus, BACnet, and IoT Gateways for real-time AI processing.</p>
        <span class="pillar-tag">BACnet · Modbus · MQTT</span>
      </div>
      <div class="pillar-card">
        <span class="pillar-num">02 — INTELLIGENCE</span>
        <div class="pillar-icon orange">🧠</div>
        <h3>Predictive Analytics</h3>
        <p>Apply Computer Vision and Neural Networks to vibration and sensor data. Stop reacting to failures — start predicting compressor and motor breakdowns before they happen.</p>
        <span class="pillar-tag">Neural Nets · Computer Vision · ML</span>
      </div>
      <div class="pillar-card">
        <span class="pillar-num">03 — OPTIMIZATION</span>
        <div class="pillar-icon green">⚡</div>
        <h3>Cognitive Efficiency</h3>
        <p>Move from fixed setpoints to autonomous logic. Use Reinforcement Learning to continuously balance occupant comfort with deep energy decarbonisation at scale.</p>
        <span class="pillar-tag">Reinforcement Learning · ASHRAE 90.1</span>
      </div>
    </div>
  </div>
</section>

<!-- YOUTUBE SECTION -->
<section class="youtube-section" id="videos">
  <div class="container">
    <div class="yt-header">
      <div>
        <span class="section-eyebrow">// YouTube Channel</span>
        <h2 class="section-title">Latest Videos</h2>
        <p class="section-desc">Deep dives into HVAC engineering, AI integration, and UAE-specific climate design.</p>
      </div>
      <a href="https://www.youtube.com/channel/UCOLrk1nHdHxeZrcKtERo-ow" target="_blank" class="yt-channel-link">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M19.59 6.69a4.83 4.83 0 01-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 01-2.88 2.5 2.89 2.89 0 01-2.89-2.89 2.89 2.89 0 012.89-2.89c.28 0 .54.04.79.1V9.01a6.33 6.33 0 00-.79-.05 6.34 6.34 0 00-6.34 6.34 6.34 6.34 0 006.34 6.34 6.34 6.34 0 006.33-6.34l-.01-8.16a8.16 8.16 0 004.77 1.52V5.21a4.85 4.85 0 01-1-.52z"/></svg>
        Subscribe on YouTube
      </a>
    </div>

    <div id="yt-container">
      <!-- Placeholder cards shown while API loads -->
      <div class="yt-placeholder-grid" id="yt-placeholders">
        <div class="yt-placeholder-card">
          <div class="yt-placeholder-thumb">
            <div class="yt-icon">▶</div>
            <span>Loading videos from<br>HVAC AI Intel channel...</span>
          </div>
          <div class="yt-placeholder-info">
            <div class="yt-placeholder-title"></div>
            <div class="yt-placeholder-title2"></div>
            <div class="yt-placeholder-meta"></div>
          </div>
        </div>
        <div class="yt-placeholder-card">
          <div class="yt-placeholder-thumb">
            <div class="yt-icon">▶</div>
            <span>Loading videos from<br>HVAC AI Intel channel...</span>
          </div>
          <div class="yt-placeholder-info">
            <div class="yt-placeholder-title"></div>
            <div class="yt-placeholder-title2"></div>
            <div class="yt-placeholder-meta"></div>
          </div>
        </div>
        <div class="yt-placeholder-card">
          <div class="yt-placeholder-thumb">
            <div class="yt-icon">▶</div>
            <span>Loading videos from<br>HVAC AI Intel channel...</span>
          </div>
          <div class="yt-placeholder-info">
            <div class="yt-placeholder-title"></div>
            <div class="yt-placeholder-title2"></div>
            <div class="yt-placeholder-meta"></div>
          </div>
        </div>
      </div>
      <div class="yt-grid" id="yt-grid" style="display:none;"></div>
      <div id="yt-fallback" style="display:none; text-align:center; padding:32px 0;">
        <p style="color:var(--text-muted); font-size:14px; margin-bottom:20px;">Visit our YouTube channel for the latest HVAC AI videos and tutorials.</p>
        <a href="https://www.youtube.com/channel/UCOLrk1nHdHxeZrcKtERo-ow" target="_blank" class="btn-primary" style="display:inline-flex;">
          ▶ &nbsp; View All Videos on YouTube
        </a>
      </div>
    </div>
  </div>
</section>

<!-- KNOWLEDGE SECTION -->
<section class="knowledge-section" id="knowledge">
  <div class="container">
    <div class="section-header">
      <span class="section-eyebrow">// Knowledge Base</span>
      <h2 class="section-title">HVAC Intelligence Library</h2>
      <p class="section-desc">Specialist knowledge spanning VRV/VRF systems, psychrometrics, UAE climate engineering, and AI integration — built from 20+ years in the field.</p>
    </div>

    <div class="knowledge-grid">
      <div class="knowledge-card">
        <span class="knowledge-icon">🌡️</span>
        <h3>Psychrometrics & Coil Science</h3>
        <p>First-principles approach to moist air properties, enthalpy calculations, coil re-rating from dry to wet operation, and dehumidification strategies for extreme humidity climates.</p>
        <div class="knowledge-topics">
          <span class="topic-tag">Wet Bulb</span>
          <span class="topic-tag">Enthalpy</span>
          <span class="topic-tag">Coil Selection</span>
          <span class="topic-tag">SHR</span>
          <span class="topic-tag">Dew Point</span>
        </div>
      </div>

      <div class="knowledge-card">
        <span class="knowledge-icon">❄️</span>
        <h3>VRV/VRF System Design</h3>
        <p>Advanced design principles for Daikin VRV and VRF multi-split systems, including piping rules, outdoor/indoor unit selection, R-32 compliance, and system capacity validation for UAE conditions.</p>
        <div class="knowledge-topics">
          <span class="topic-tag">Daikin VRV</span>
          <span class="topic-tag">R-32</span>
          <span class="topic-tag">ODU/IDU</span>
          <span class="topic-tag">Piping Design</span>
          <span class="topic-tag">BRC Controllers</span>
        </div>
      </div>

      <div class="knowledge-card">
        <span class="knowledge-icon">🏙️</span>
        <h3>UAE Climate Engineering</h3>
        <p>Design strategies tuned for Dubai and GCC conditions — extreme summer temperatures, high latent loads, sandstorm resilience, and ASHRAE 90.1 / Estidama compliance for energy optimisation.</p>
        <div class="knowledge-topics">
          <span class="topic-tag">Dubai Climate</span>
          <span class="topic-tag">Estidama</span>
          <span class="topic-tag">ASHRAE 90.1</span>
          <span class="topic-tag">Latent Load</span>
          <span class="topic-tag">GCC</span>
        </div>
      </div>

      <div class="knowledge-card">
        <span class="knowledge-icon">🤖</span>
        <h3>AI in HVAC Engineering</h3>
        <p>Practical AI application layer: building RAG knowledge bases for HVAC retrieval, LLM-assisted energy audits, neural network fault detection, and prompt engineering for technical HVAC queries.</p>
        <div class="knowledge-topics">
          <span class="topic-tag">RAG</span>
          <span class="topic-tag">LLM</span>
          <span class="topic-tag">Fault Detection</span>
          <span class="topic-tag">Claude API</span>
          <span class="topic-tag">AI Agents</span>
        </div>
      </div>

      <div class="knowledge-card">
        <span class="knowledge-icon">⚡</span>
        <h3>Energy Auditing & Optimisation</h3>
        <p>Systematic energy audit methodology for commercial HVAC systems — baseline assessment, EUI benchmarking, retro-commissioning diagnostics, and AI-assisted recommendation engines.</p>
        <div class="knowledge-topics">
          <span class="topic-tag">EUI</span>
          <span class="topic-tag">Retro-commissioning</span>
          <span class="topic-tag">Chiller Plant</span>
          <span class="topic-tag">IPMVP</span>
          <span class="topic-tag">DEWA</span>
        </div>
      </div>

      <div class="knowledge-card">
        <span class="knowledge-icon">🔧</span>
        <h3>DX Systems & Process Cooling</h3>
        <p>Direct expansion system design including DX chillers with BPHE, EXV kits, buffer tank sizing, refrigerant piping for process cooling — from first principles to commissioning.</p>
        <div class="knowledge-topics">
          <span class="topic-tag">DX Chiller</span>
          <span class="topic-tag">BPHE</span>
          <span class="topic-tag">EXV</span>
          <span class="topic-tag">Buffer Tank</span>
          <span class="topic-tag">Process Cooling</span>
        </div>
      </div>

      <div class="knowledge-card">
        <span class="knowledge-icon">📡</span>
        <h3>IoT & BMS Integration</h3>
        <p>Connecting physical HVAC plant to digital intelligence — sensor selection, Modbus/BACnet protocols, edge computing at the gateway layer, and cloud analytics dashboards for real-time monitoring.</p>
        <div class="knowledge-topics">
          <span class="topic-tag">BACnet</span>
          <span class="topic-tag">Modbus</span>
          <span class="topic-tag">BMS</span>
          <span class="topic-tag">MQTT</span>
          <span class="topic-tag">Edge AI</span>
        </div>
      </div>

      <div class="knowledge-card">
        <span class="knowledge-icon">📊</span>
        <h3>Data-Driven HVAC Design</h3>
        <p>Leveraging AI tools for automated load calculations, equipment selection optimisation, compliance checking against ASHRAE/ISO standards, and dynamic simulation for UAE summer design days.</p>
        <div class="knowledge-topics">
          <span class="topic-tag">Load Calc</span>
          <span class="topic-tag">CLTD/CLF</span>
          <span class="topic-tag">EnergyPlus</span>
          <span class="topic-tag">Design Day</span>
          <span class="topic-tag">Simulation</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ASK AI SECTION -->
<section class="ai-chat-section" id="ask-ai">
  <div class="container">
    <div class="section-header" style="text-align:center; max-width: 560px; margin: 0 auto 48px;">
      <span class="section-eyebrow">// AI Assistant</span>
      <h2 class="section-title">Ask an HVAC Intelligence Question</h2>
      <p class="section-desc" style="margin: 0 auto;">Get instant expert-level answers on psychrometrics, VRV/VRF design, UAE climate engineering, or AI in HVAC.</p>
    </div>

    <div class="ai-chat-wrapper">
      <div class="ai-chat-header">
        <div class="ai-chat-header-dot"></div>
        <span class="ai-chat-header-title"><strong>HVAC AI Intel</strong> · Powered by Claude · UAE Specialist Mode</span>
      </div>

      <div class="chat-messages" id="chat-messages">
        <div class="msg ai">
          <div class="msg-avatar">🤖</div>
          <div class="msg-bubble">
            Salaam! I'm the HVAC AI Intel assistant — trained on UAE climate engineering, VRV/VRF systems, psychrometrics, and AI-driven HVAC design. What technical challenge can I help you solve today?
          </div>
        </div>
      </div>

      <div class="suggested-qs" id="suggested-qs">
        <button class="suggested-q" onclick="sendSuggested(this)">What's the ideal SHR for Dubai commercial spaces?</button>
        <button class="suggested-q" onclick="sendSuggested(this)">How does R-32 affect Daikin VRV piping design?</button>
        <button class="suggested-q" onclick="sendSuggested(this)">Explain wet bulb depression in UAE summer</button>
        <button class="suggested-q" onclick="sendSuggested(this)">How can AI improve HVAC energy audits?</button>
      </div>

      <div class="chat-input-area">
        <input class="chat-input" id="chat-input" type="text" placeholder="Ask about psychrometrics, VRV/VRF, UAE climate, AI integration..." />
        <button class="chat-send" id="chat-send" onclick="sendMessage()">
          Send ➤
        </button>
      </div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section class="about-section" id="about">
  <div class="container">
    <div class="about-grid">
      <div class="about-visual">
        <div class="about-card">
          <div class="about-avatar">👷</div>
          <div class="about-name">Utpal Joshi</div>
          <div class="about-role">// Daikin Consulting Sales Director · Dubai, UAE</div>
          <p class="about-bio">
            20+ years in HVAC engineering across the UAE, UK, US, and Australia. Deep specialist in VRV/VRF systems, psychrometrics, coil selection, and GCC climate engineering. Recognised as Society AI HVAC Encyclopedia Winner. Currently bridging traditional HVAC expertise with AI-powered tools and education.
          </p>
          <div class="about-badges">
            <span class="about-badge">Society AI Winner</span>
            <span class="about-badge">Daikin Specialist</span>
            <span class="about-badge">VRV/VRF Expert</span>
            <span class="about-badge">UAE Climate</span>
            <span class="about-badge">ASHRAE</span>
            <span class="about-badge">MEP Consulting</span>
          </div>
        </div>
      </div>

      <div class="about-content">
        <span class="section-eyebrow">// About the Creator</span>
        <h2>Engineering Meets Artificial Intelligence</h2>
        <p>HVAC AI Intel was born from a simple belief: the HVAC industry is decades behind on digital transformation, and AI is the accelerant that can close that gap — fast.</p>
        <p>With a career spanning Daikin sales and consulting, MEP engineering projects across the GCC, and deep specialisation in the UAE's unique climate challenges, this platform translates real-world engineering complexity into accessible AI-powered tools and education.</p>
        <p>Whether you're an MEP engineer in Dubai, an energy auditor in Riyadh, or an HVAC consultant anywhere — HVAC AI Intel exists to give you the intelligence layer your practice deserves.</p>
        <div style="margin-top: 32px; display: flex; gap: 16px; flex-wrap: wrap;">
          <a href="https://www.youtube.com/channel/UCOLrk1nHdHxeZrcKtERo-ow" target="_blank" class="btn-primary">▶ YouTube Channel</a>
          <a href="https://github.com/hvacaiintel/hvacAIintel.github.io" target="_blank" class="btn-secondary">⚡ GitHub</a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div class="footer-top">
      <div class="footer-brand">
        <a href="#" class="nav-logo" style="margin-bottom:12px; display:inline-flex;">
          <div class="nav-logo-icon">AI</div>
          <span class="nav-logo-text">HVAC<span>AI</span>Intel</span>
        </a>
        <p>The intelligence layer for modern climate control. Bridging 20+ years of HVAC engineering with AI-powered tools and education for MEP professionals worldwide.</p>
      </div>

      <div class="footer-links">
        <h4>Platform</h4>
        <ul>
          <li><a href="#pillars">Digitization Roadmap</a></li>
          <li><a href="#knowledge">Knowledge Base</a></li>
          <li><a href="#ask-ai">AI Assistant</a></li>
          <li><a href="#videos">Video Library</a></li>
        </ul>
      </div>

      <div class="footer-links">
        <h4>Specialisms</h4>
        <ul>
          <li><a href="#knowledge">VRV/VRF Systems</a></li>
          <li><a href="#knowledge">Psychrometrics</a></li>
          <li><a href="#knowledge">UAE Climate Design</a></li>
          <li><a href="#knowledge">Energy Auditing</a></li>
        </ul>
      </div>

      <div class="footer-links">
        <h4>Connect</h4>
        <ul>
          <li><a href="https://www.youtube.com/channel/UCOLrk1nHdHxeZrcKtERo-ow" target="_blank">YouTube</a></li>
          <li><a href="https://github.com/hvacaiintel/hvacAIintel.github.io" target="_blank">GitHub</a></li>
          <li><a href="https://hvacaiintel.github.io/" target="_blank">Live Site</a></li>
        </ul>
      </div>
    </div>

    <div class="footer-bottom">
      <span class="footer-copy">© 2026 HVAC AI Intel · @hvacAIintel · Dubai, UAE</span>
      <div class="footer-social">
        <a href="https://www.youtube.com/channel/UCOLrk1nHdHxeZrcKtERo-ow" target="_blank" class="social-link" title="YouTube">▶</a>
        <a href="https://github.com/hvacaiintel/hvacAIintel.github.io" target="_blank" class="social-link" title="GitHub">⚡</a>
      </div>
    </div>
  </div>
</footer>

<script>
// =====================
// YOUTUBE VIDEO LOADER
// =====================
const CHANNEL_ID = 'UCOLrk1nHdHxeZrcKtERo-ow';
const CHANNEL_URL = 'https://www.youtube.com/channel/' + CHANNEL_ID;

// Hardcoded representative videos - in production replace with actual video IDs from your channel
// These are placeholder entries; the AI will attempt to describe what videos you might have
const FALLBACK_VIDEOS = [
  {
    id: null,
    title: 'VRV/VRF System Design for UAE Climate — A Complete Guide',
    thumb: null,
    tag: 'VRV/VRF Design'
  },
  {
    id: null,
    title: 'Psychrometric Chart Explained: Dubai Summer Conditions',
    thumb: null,
    tag: 'Psychrometrics'
  },
  {
    id: null,
    title: 'AI-Powered HVAC Energy Audit Tool — Live Demo',
    thumb: null,
    tag: 'AI Tools'
  }
];

async function loadYouTubeVideos() {
  try {
    const response = await fetch("https://api.anthropic.com/v1/messages", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({
        model: "claude-sonnet-4-20250514",
        max_tokens: 1000,
        tools: [{ type: "web_search_20250305", name: "web_search" }],
        messages: [{
          role: "user",
          content: `Search for the YouTube channel @hvacAIintel or channel ID UCOLrk1nHdHxeZrcKtERo-ow and list their published videos with video IDs. Return ONLY a JSON array like: [{"id":"VIDEO_ID","title":"Video Title","published":"2025-01-01"}]. If no videos found or channel is new with no public videos, return []. No other text.`
        }]
      })
    });

    const data = await response.json();
    const textContent = data.content
      .filter(b => b.type === 'text')
      .map(b => b.text)
      .join('');

    let videos = [];
    const jsonMatch = textContent.match(/\[[\s\S]*?\]/);
    if (jsonMatch) {
      try { videos = JSON.parse(jsonMatch[0]); } catch(e) { videos = []; }
    }

    renderVideos(videos);
  } catch(e) {
    showFallback();
  }
}

function renderVideos(videos) {
  const placeholders = document.getElementById('yt-placeholders');
  const grid = document.getElementById('yt-grid');
  const fallback = document.getElementById('yt-fallback');

  placeholders.style.display = 'none';

  if (!videos || videos.length === 0) {
    showFallback();
    return;
  }

  grid.style.display = 'grid';
  grid.innerHTML = videos.slice(0, 6).map(v => {
    const thumbUrl = v.id 
      ? `https://img.youtube.com/vi/${v.id}/maxresdefault.jpg`
      : null;
    const videoUrl = v.id ? `https://www.youtube.com/watch?v=${v.id}` : CHANNEL_URL;
    const date = v.published ? new Date(v.published).toLocaleDateString('en-GB', { year:'numeric', month:'short', day:'numeric' }) : '';

    return `
      <a href="${videoUrl}" target="_blank" class="yt-card">
        <div class="yt-thumb">
          ${thumbUrl 
            ? `<img src="${thumbUrl}" alt="${v.title}" onerror="this.style.display='none';this.nextElementSibling.style.display='flex';" />`
            : ''}
          <div style="display:${thumbUrl?'none':'flex'}; width:100%; height:100%; background:linear-gradient(135deg,#0b1422,#0f1d30); align-items:center; justify-content:center; flex-direction:column; gap:10px; color:var(--text-muted); font-size:12px; padding:20px; text-align:center;">
            <span style="font-size:32px; opacity:0.5">▶</span>
            <span>HVAC AI Intel</span>
          </div>
          <div class="yt-play"><div class="yt-play-btn">▶</div></div>
        </div>
        <div class="yt-info">
          <h4>${v.title}</h4>
          <div class="yt-meta">
            <span>${date}</span>
            ${v.tag ? `<span class="yt-tag">${v.tag}</span>` : ''}
          </div>
        </div>
      </a>
    `;
  }).join('');
}

function showFallback() {
  document.getElementById('yt-placeholders').style.display = 'none';
  document.getElementById('yt-fallback').style.display = 'block';
}

// =====================
// AI CHAT
// =====================
const SYSTEM_PROMPT = `You are the HVAC AI Intel assistant, created by Utpal Joshi — a Daikin Consulting Sales Director and HVAC specialist based in Dubai with 20+ years of experience. You are a specialist in:
- VRV/VRF systems (especially Daikin), R-32, ODU/IDU selection, piping design
- Psychrometrics: wet bulb, enthalpy, SHR, coil re-rating, dehumidification
- UAE and GCC climate engineering: extreme heat, high latent loads, DEWA, Estidama, ASHRAE 90.1
- AI in HVAC: RAG knowledge bases, LLM-assisted energy audits, fault detection, Claude API tools
- Energy auditing: EUI benchmarking, retro-commissioning, IPMVP
- DX systems, process cooling, BPHE, EXV kits, buffer tanks

Answer with depth, accuracy, and confidence. Reference UAE-specific conditions (Dubai design day: ~45°C DB, ~30°C WB) where relevant. Keep responses focused, expert-level, and practical. Format clearly with short paragraphs. Max 250 words per response.`;

let chatHistory = [];

async function sendMessage() {
  const input = document.getElementById('chat-input');
  const sendBtn = document.getElementById('chat-send');
  const msg = input.value.trim();
  if (!msg || sendBtn.disabled) return;

  input.value = '';
  sendBtn.disabled = true;
  document.getElementById('suggested-qs').style.display = 'none';

  appendMessage('user', msg);
  chatHistory.push({ role: 'user', content: msg });

  const thinkingId = appendMessage('ai', '...', true);

  try {
    const response = await fetch("https://api.anthropic.com/v1/messages", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({
        model: "claude-sonnet-4-20250514",
        max_tokens: 1000,
        system: SYSTEM_PROMPT,
        messages: chatHistory
      })
    });

    const data = await response.json();
    const reply = data.content?.[0]?.text || "I apologise, I couldn't generate a response. Please try again.";

    removeMessage(thinkingId);
    appendMessage('ai', reply);
    chatHistory.push({ role: 'assistant', content: reply });

  } catch(e) {
    removeMessage(thinkingId);
    appendMessage('ai', 'Connection error. Please check your network and try again.');
  }

  sendBtn.disabled = false;
  input.focus();
}

function appendMessage(role, text, isTyping = false) {
  const container = document.getElementById('chat-messages');
  const id = 'msg-' + Date.now();
  const avatar = role === 'ai' ? '🤖' : '👤';

  const div = document.createElement('div');
  div.className = `msg ${role}`;
  div.id = id;
  div.innerHTML = `
    <div class="msg-avatar">${avatar}</div>
    <div class="msg-bubble${isTyping ? ' typing' : ''}">${isTyping ? 'Thinking' : text.replace(/\n/g, '<br>')}</div>
  `;

  container.appendChild(div);
  container.scrollTop = container.scrollHeight;
  return id;
}

function removeMessage(id) {
  const el = document.getElementById(id);
  if (el) el.remove();
}

function sendSuggested(btn) {
  document.getElementById('chat-input').value = btn.textContent;
  sendMessage();
}

document.getElementById('chat-input').addEventListener('keydown', e => {
  if (e.key === 'Enter') sendMessage();
});

// Init
loadYouTubeVideos();
</script>
</body>
</html>
