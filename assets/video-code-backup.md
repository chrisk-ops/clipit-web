# Video Code Backup

Paste each block back into index.html to restore the video exactly as it was.

---

## 1. CSS — after `/* ─── PHONE MOCKUP ─── */` block, before `/* ─── ABOUT ─── */`

```css
/* ─── VIDEO REPLAY ─── */
.video-wrap { position: relative; display: inline-block; }
.replay-btn {
  position: absolute; bottom: 0; right: -36px;
  display: flex; align-items: center; justify-content: center;
  width: 36px; height: 36px;
  background: transparent; border: none; border-radius: 50%; padding: 0;
  color: var(--navy); cursor: pointer;
  visibility: hidden; opacity: 0; transition: opacity .2s;
}
.replay-btn:hover { opacity: 0.8; }
.replay-btn.visible { visibility: visible; opacity: 0.45; }
.play-btn {
  position: absolute; bottom: 0; right: -36px;
  display: flex; align-items: center; justify-content: center;
  width: 36px; height: 36px;
  background: transparent; border: none; border-radius: 50%; padding: 0;
  color: var(--navy); cursor: pointer;
  visibility: hidden; opacity: 0; transition: opacity .2s;
}
.play-btn:hover { opacity: 0.7; }
.play-btn.visible { visibility: visible; opacity: 1; }
@media (min-width: 901px) { .play-btn { display: none; } }
```

---

## 2. CSS — inside `@media (max-width: 900px)` block, in the hero section comments

```css
  /* video before text on mobile - reset desktop order */
  .hero-phone { order: unset; }
  .hero-text { order: unset; }
```

---

## 3. HTML — inside `<div class="hero-inner">`, before `<div class="hero-text">`

```html
    <div class="hero-phone">
      <div class="video-wrap">
        <video id="demo-video" muted playsinline preload="metadata" style="max-width:100%;max-height:560px;border-radius:50px;">
          <source src="assets/demo.mp4" type="video/mp4">
        </video>
        <button class="replay-btn" id="replay-btn" onclick="replayDemo()" aria-label="Replay demo">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
            <path d="M3 12a9 9 0 1 0 9-9 9.75 9.75 0 0 0-6.74 2.74L3 8"/>
            <polyline points="3 3 3 8 8 8"/>
          </svg>
        </button>
        <button class="play-btn visible" id="play-btn" onclick="playDemo()" aria-label="Play demo">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
            <polygon points="5 3 19 12 5 21 5 3"/>
          </svg>
        </button>
      </div>
    </div>
```

---

## 4. JS — inside the main `<script>` block, after the form/scroll logic

```js
  // ─── DEMO VIDEO ───
  var demoVideo = document.getElementById('demo-video');
  var replayBtn = document.getElementById('replay-btn');
  var playBtn = document.getElementById('play-btn');
  if (demoVideo) {
    demoVideo.addEventListener('loadedmetadata', function() {
      demoVideo.currentTime = 0.001;
    });
    demoVideo.addEventListener('ended', function() {
      replayBtn.classList.add('visible');
    });
    if (window.innerWidth > 900) {
      demoVideo.play();
    }
  }
  function playDemo() {
    demoVideo.play();
    playBtn.classList.remove('visible');
  }
  function replayDemo() {
    replayBtn.classList.remove('visible');
    demoVideo.currentTime = 0;
    demoVideo.play();
  }
```
