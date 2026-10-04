# Happy Colors 快樂認色

A Cantonese colour-learning game for toddlers aged 2–4 (best in landscape on an iPhone or iPad). It is one page (index.html) with inline CSS and JS, and has no external or copyrighted assets. The characters are SVG drawn in code, the sound effects are synthesised with Web Audio, and the voice lines are pre-recorded clips in `audio/`.

Play it: https://julianzhumin.github.io/happy-colours/

## How it plays

1. **開始**: the start screen.
2. **Intro**: the 7 colour characters (紅 黃 藍 綠 灰 黑 白) come in one at a time. Each pops in with its own boing, squeak or pop, then says its colour (「紅色」…).
3. **Quiz** (7 rounds, each colour once): all 7 stand in a row, in a new random order every question.
   - Each colour is said twice, slowly, with a short pause. Then the characters grow to show it's time to tap.
   - **Right one**: it raises a hand and shouts an excited "Yeah!", with a burst of hand-claps, a "woo-hoo" whistle, and soap bubbles in its own colour floating around the screen (about 2 s).
   - **Wrong one**: it shakes its head and waves both hands side to side ("no-no"), with a soft, low "buzzer" sound and no words. Everyone shrinks back. The same colour is then asked again with the characters in the same places (a second chance). A second wrong tap gets the same shake and buzzer, then a **hint**: the right character grows a little, steps forward and says 「我係紅色」 (its own colour), then stands still. Only it can be tapped now; taps on the others are ignored.
     - Tapped: the normal "Yeah!" celebration, then the next colour.
     - Not tapped within 7 s: a cartoon pointing hand comes and taps it, and it quietly disappears (no words, no sounds, no celebration). Then the next colour comes, and that character is back in the row with the others. Phones that support vibration (Android) also buzz briefly; iPhone Safari can't vibrate.
4. **Byebye**: everyone waves.
5. **Parent screen**: 「再玩過」 (top right) asks 「再玩過？」 before restarting from the intro. Press and hold it for 1.5 s to restart straight away. 「完」 goes back to the start screen.

Reduce-motion is honoured: fades instead of shakes, jumps and hand-waving, and a few bubbles that fade in place instead of flying, and the hint hand appears in place instead of travelling. Every button and character has a Cantonese accessibility label.

## Voice clips

- Cantonese: edge-tts `zh-HK-HiuGaaiNeural` (colours at −10%, slow quiz versions at −40%, hint lines 「我係X色」 (`*-me.mp3`) at −10%, like the colours). `uhoh.mp3` (「呃哦」) and `hello.mp3` are still in `audio/` but are no longer played or cached (since v7 and v8).
- Yeah and Byebye: `en-US-AnaNeural`. Yeah is "Yeah!!" at +50 Hz (0.5 s, rising from 410 Hz to 533 Hz).
- Clips are trimmed, normalised to about −16 LUFS, and encoded as 48 kbps mono MP3.
- If a clip can't load, the phone's own zh-HK voice reads that line instead.

## Sound effects

Every sound effect (boing, squeak, pop, the claps, the "woo-hoo" whistle, the buzzer and the others) is synthesised live with the Web Audio API in `index.html`, made from oscillators and generated white noise. No sample files are used, so there is nothing to license. The pointing hand is an original inline SVG drawing.

## Offline and updates

`sw.js` caches the page, icons and all clips. Bump `CACHE` in sw.js and `APP_VERSION` in index.html together on each release.

Add `?speed=4` to the address to make all waits and animations faster (used by the tests).
