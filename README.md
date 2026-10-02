# Happy Colours 快樂認識

A Cantonese colour-learning game for toddlers aged 2–4 (best in landscape on an iPhone or iPad). It is one page (index.html) with inline CSS and JS, and has no external or copyrighted assets. The characters are SVG drawn in code, the sound effects are synthesised with Web Audio, and the voice lines are pre-recorded clips in `audio/`.

Play it: https://julianzhumin.github.io/happy-colours/

## How it plays

1. **開始**: the start screen.
2. **Intro**: the 7 colour characters (紅 黃 藍 綠 灰 黑 白) come in one at a time. Each pops in with its own boing, squeak or pop, then says its colour (「紅色」…).
3. **Quiz** (7 rounds, each colour once): all 7 stand in a row, in a new random order every question.
   - Each colour is said twice, slowly, with a short pause. Then the characters grow to show it's time to tap.
   - **Right one**: it raises a hand and says a cheerful "Hel-looo!".
   - **Wrong one**: it does a gentle head-shake and 「呃哦」 plays, everyone shrinks back, and the next colour comes. Phones that support vibration (Android) also buzz briefly; iPhone Safari can't vibrate.
4. **Byebye**: everyone waves.
5. **Parent screen**: 「再玩過」 (top right) asks 「再玩過？」 before restarting from the intro. Press and hold it for 1.5 s to restart straight away. 「完」 goes back to the start screen.

Reduce-motion is honoured (fades instead of shakes and jumps). Every button and character has a Cantonese accessibility label.

## Voice clips

- Cantonese: edge-tts `zh-HK-HiuGaaiNeural` (colours at −10%, slow quiz versions at −40%, 「呃哦」 at −20%).
- Hello and Byebye: `en-US-AnaNeural` (Hello is "Hel-lo!" at −50%, +30 Hz).
- Clips are trimmed, normalised to about −16 LUFS, and encoded as 48 kbps mono MP3.
- If a clip can't load, the phone's own zh-HK voice reads that line instead.

## Offline and updates

`sw.js` caches the page, icons and all clips. Bump `CACHE` in sw.js and `APP_VERSION` in index.html together on each release.

Add `?speed=4` to the address to make all waits and animations faster (used by the tests).
