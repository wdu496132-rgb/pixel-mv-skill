# pixel-mv-skill

**Pixel-art music videos, generated entirely in code — an open-source skill for AI coding agents.**

An open-source skill in the Agent Skills (`SKILL.md`) format that teaches an AI coding agent how to produce a complete pixel-art MV from a song: a low-resolution pixel canvas upscaled with integer scaling, checkerboard-dithered gradients, lyric-driven semantic storyboarding on the real vocal timeline, a library of 16 pixel transitions, and an effects master switch — rendered to 1920×1080 MP4 with GSAP + Puppeteer + FFmpeg.

## What it does

- **Real pixel art, not a filter.** Scenes are drawn pixel by pixel on a small logical canvas (e.g. 480×270) and upscaled ×4 with `image-rendering: pixelated`; gradients use checkerboard dithering, text is rendered to a tiny offscreen canvas and blown up to get true pixel letterforms
- **Semantic storyboarding.** Every lyric line gets its own matching scene, cut on the song's real timestamps — the visuals follow what the words mean
- **Effects, turned all the way up.** Petal / stardust / neon-rain particles, climax screen shake, flashes, water shimmer and lens glow — all behind one master switch
- **16 pixel transitions.** Pixel dissolve, checkerboard wipe, blinds, circle / heart / star iris, glitch, push-pull, mosaic pass-through, water ripple… a whole video with zero hard cuts and no transition repeated back-to-back
- **Dual-timeline narrative template.** SIDE A (the past) / SIDE B (the present), a keepsake motif, and a music-player UI opening and ending
- **Automatic duration.** 16:9, 1920×1080, 30 fps; the length follows the audio, never a fixed guess

## Case study

**Tanya Chua — 《红色高跟鞋》 (Red High Heels):** 27 lyric lines, each with its own semantic scene. Two verified renders: v1 (52.7 MB) and the multi-transition cut (46.4 MB) — 16 transition types across 23 edit points, zero hard cuts. Both passed automated checks (0 errors) and human frame review at the opening and climax.

Companion skills by the same author: [interactive-mv-skill](https://github.com/wdu496132-rgb/interactive-mv-skill) — interactive web MVs with branching endings — and [cartoon_mv](https://github.com/wdu496132-rgb/cartoon_mv) — pure-code 2D cartoon MVs. Together they cover the interactive, cartoon and pixel-art styles of code-generated music video.

## Hard-won lessons baked in

- **Verify the audio before anything.** A file named after one song can actually contain another — always transcribe a sample and check before storyboarding (this skill was bitten by exactly that)
- **Integer scaling only.** Non-integer scaling or smooth interpolation destroys the pixel look instantly
- **Characters step at 8–12 fps while the camera moves at 30 fps** — that mismatch *is* the retro feel
- **Never reuse a transition twice in a row**, and stamp every cut with a named transition, not a default fade

## Install

Clone this repo into your agent's skills directory, e.g. for Muse:

```bash
git clone https://github.com/wdu496132-rgb/pixel-mv-skill ~/workspace/custom-skills/pixel-mv
```

`SKILL.md` follows the open Agent Skills format used by Muse, Claude Code, Codex and other compatible agents. Then just say: *"Make a pixel-art MV for this song"* and attach the MP3.

## Files

- `SKILL.md` — the skill itself: full production spec (technique, art rules, narrative structure, transition library, inputs)
- `skill.yaml` — skill metadata
- `LICENSE` — MIT License

## License

MIT © 2026 Du Wei ([@wdu496132-rgb](https://github.com/wdu496132-rgb))

---

## 中文说明

一个可复用的开源 Skill：**用纯代码制作像素风音乐 MV**（低分辨率像素画布 + GSAP + Puppeteer + FFmpeg）。

- **像素风画面**：逻辑低分辨率画布（如 480×270）整数放大到 1920×1080，人物/建筑/云全部用像素块手拼，渐变用棋盘格抖动——像素感是画出来的，不是滤镜
- **语义分镜**：歌词逐句配画，画面跟着歌词意思走，按真实演唱时间轴卡点
- **花里胡哨特效**：粒子（花瓣/星尘/霓虹雨）、高潮震屏、闪光、水面波光、镜头光晕，一键全开
- **16 种像素转场库**：像素溶解、棋盘擦除、百叶窗、圆形/心形/星形 iris、故障 glitch、推拉、马赛克穿越、水波纹……全片零硬切，同种不连用
- **双线叙事模板**：SIDE A 过去 / SIDE B 现在 + 信物隐喻 + 播放器 UI 开场结尾
- **自动时长**：默认 16:9 横屏 1920×1080 30fps，时长随音频自动确定

**实测案例：** 蔡健雅《红色高跟鞋》——27 句歌词逐句配画，v1 成片 52.7MB、多转场版 46.4MB（16 种转场、23 个切换点零硬切），自动检查 0 errors 并人工抽检通过。

**安装：** 把本仓库放到 Muse 的 custom skills 目录（见上方英文命令），之后说"用 pixel_mv 给这首歌做个像素风 MV"并附上 MP3 即可开工。

**许可证：** MIT
