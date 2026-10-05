# Happy Colors 快樂認色

A Cantonese colour-learning game for toddlers aged 2–4 (best in landscape on an iPhone or iPad). It is one page (index.html) with inline CSS and JS, and has no external or copyrighted assets. The characters are SVG drawn in code, the sound effects are synthesised with Web Audio, and the voice lines are pre-recorded clips in `audio/`.

Play it: https://julianzhumin.github.io/happy-colours/

## How it plays

1. **開始**: the start screen.
2. **Intro**: the 8 colour characters (紅 黃 藍 綠 灰 黑 白 啡) come in one at a time. Each pops in with its own boing, squeak or pop, then says its colour in Cantonese and then in English (「紅色」 … "Red").
3. **Quiz** (one question per colour: all 8 colours, each exactly once, in random order; no fixed round count): all 8 stand in a row, in a new random order every question. A replay never starts with the colour the previous game ended on.
   - A narrator (a grown-up voice, different from the toys) says the colour twice, slowly, with a short pause. Then the characters grow to show it's time to tap.
   - **Right one**: it raises a hand and shouts an excited "Yeah!", with a burst of hand-claps, a "woo-hoo" whistle, and soap bubbles in its own colour floating around the screen (about 2 s).
   - **A miss** is a wrong tap or 7 s with no tap. On a wrong tap, the tapped character shakes its head and waves both hands side to side ("no-no"), with a soft, low "buzzer" sound and no words; a silent miss has no sound. Everyone shrinks back.
     - First miss: the same colour is asked again, with the characters in the same places.
     - Second miss: a **hint**. The right character grows a little, steps forward and says 「我係藍色」 then "I am blue", then stands still. Only it can be tapped now; taps on the others are ignored.
       - Tapped: the normal "Yeah!" celebration, then the next colour.
       - Not tapped within 7 s: a cartoon pointing hand comes and taps it, and it quietly disappears (no words, no sounds, no celebration). Then the next colour comes, and that character is back in the row with the others.
   - Phones that support vibration (Android) also buzz briefly on a wrong tap; iPhone Safari can't vibrate.
4. **Byebye**: everyone waves.
5. **Parent screen**: 「再玩過」 (top right) asks 「再玩過？」 before restarting from the intro. Press and hold it for 1.5 s to restart straight away. 「完」 goes back to the start screen.

Reduce-motion is honoured: fades instead of shakes, jumps and hand-waving, and a few bubbles that fade in place instead of flying, and the hint hand appears in place instead of travelling. Every button and character has a Cantonese accessibility label.

## Voice clips

- Narrator (the questions, `*-slow.mp3`): edge-tts `zh-HK-HiuMaanNeural`, an adult female voice, at −40% with natural pitch. If a question clip can't load, the phone's zh-HK voice reads it at natural pitch.
- Toys, Cantonese: `zh-HK-HiuGaaiNeural`: colour names at −10% (`red.mp3` …) and the hint 「我係X色」 (`*-me.mp3`) at −10%.
- Toys, English: `en-US-AnaNeural` (a child voice): colour names (`*-en.mp3`, "Red!" … "Brown!"; Gray is "Gray." because "Gray!" sounds like "great"), the hint "I am red" (`*-iam.mp3`), Yeah ("Yeah!!" at +50 Hz) and Byebye. English names use US spelling, like "Happy Colors".
- `uhoh.mp3` (「呃哦」) and `hello.mp3` are still in `audio/` but are no longer played or cached (since v7 and v8).
- Clips are trimmed, normalised to about −16 LUFS, and encoded as 48 kbps mono MP3.
- If a clip can't load, the phone's own voice reads that line instead (zh-HK for Cantonese, an English voice for English), so no line is ever skipped.

## Sound effects

Every sound effect (boing, squeak, pop, the claps, the "woo-hoo" whistle, the buzzer and the others) is synthesised live with the Web Audio API in `index.html`, made from oscillators and generated white noise. No sample files are used, so there is nothing to license. The pointing hand is an original inline SVG drawing.

## Offline and updates

`sw.js` caches the page, icons and all clips. Bump `CACHE` in sw.js and `APP_VERSION` in index.html together on each release.

Add `?speed=4` to the address to make all waits and animations faster (used by the tests).

## v10e — bilingual screen text

Every Chinese line on screen now has its English directly below: the captions during the intro, quiz and hint
(「紅色」 / Red, 「我係紅色」 / I am red), 「做得好好！」 / Well done!, 「拜拜！」 / Bye bye!, the start and end
screens, the 再玩過 dialog and the portrait hint 「打橫部機，會更好玩！」 / "Turn the phone sideways — it's more fun!".
Gameplay and voice are unchanged.

## v10f — hub exit + mic release on leave

「返學樂園」 / Back to AstraGarten on No (and Done) navigates to 星星學樂園.
Leaving the tab/page at any point fully releases SpeechRecognition / mic (pagehide, beforeunload, unload, visibility hidden).

## v10g — Color Genies wording

The color characters are now 顏色精靈 / Color Genies (was 顏色公仔 / color friends) in the start-screen note and button aria-labels (e.g. 「紅色精靈」). Gameplay and voice are unchanged.
