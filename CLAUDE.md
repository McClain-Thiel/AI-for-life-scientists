# reveal.js Presentation — 3Blue1Brown Style

## Project Overview

A reveal.js-based presentation framework styled after 3Blue1Brown's aesthetic: dark backgrounds, vibrant accent colors, mathematical clarity, and smooth animations. Slides are written in HTML and run directly in the browser — no build step required for basic usage.

## Stack

- **reveal.js** — slide framework (via CDN or local install)
- **Animate.css** — pre-built CSS animations (via CDN)
- **KaTeX** — LaTeX math rendering (renders in Computer Modern out of the box)
- **Computer Modern web font** — matches KaTeX/Manim typography for body + headings
- **JetBrains Mono** — code blocks
- **Manim videos** — embed as `<video>` tags for 3B1B-style math animations

## Project Structure

```
presentation/
├── CLAUDE.md              ← this file
├── index.html             ← main presentation file (edit this)
├── assets/
│   ├── videos/            ← drop Manim-exported .mp4 files here
│   ├── images/            ← any static images
│   └── custom.css         ← your style overrides
└── README.md
```

## Getting Started

### Option A — CDN (no install, just open index.html)
Everything loads from CDN. Just open `index.html` in a browser.

### Option B — Local install
```bash
npm install reveal.js
```
Then swap CDN links for local paths.

## The index.html Template

Create `index.html` with this structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Your Presentation Title</title>

  <!-- reveal.js -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js/dist/reveal.css" />
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js/dist/theme/black.css" />

  <!-- Animate.css -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css" />

  <!-- Computer Modern (LaTeX / Manim font) -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/dreampulse/computer-modern-web-font@master/fonts.css" />

  <!-- JetBrains Mono for code -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fontsource/jetbrains-mono@5.0.20/index.css" />

  <!-- KaTeX (math rendering) -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.css" />

  <!-- Your overrides -->
  <link rel="stylesheet" href="assets/custom.css" />
</head>

<body>
  <div class="reveal">
    <div class="slides">

      <!-- SLIDE 1: Title -->
      <section>
        <h1>Your Title Here</h1>
        <p class="subtitle">A subtitle or author name</p>
      </section>

      <!-- SLIDE 2: Fragmented bullet reveal -->
      <section>
        <h2>Key Ideas</h2>
        <ul>
          <li class="fragment">First point appears on keypress</li>
          <li class="fragment">Then this one</li>
          <li class="fragment">Then this one</li>
        </ul>
      </section>

      <!-- SLIDE 3: Math with KaTeX -->
      <section>
        <h2>A Beautiful Equation</h2>
        <p>The Fourier Transform:</p>
        <div class="katex-display">$$\hat{f}(\xi) = \int_{-\infty}^{\infty} f(x)\, e^{-2\pi i x \xi}\, dx$$</div>
      </section>

      <!-- SLIDE 4: Embedded Manim video -->
      <section>
        <h2>Animation</h2>
        <video data-autoplay loop muted>
          <source src="assets/videos/your_animation.mp4" type="video/mp4" />
        </video>
      </section>

      <!-- SLIDE 5: Two-column layout -->
      <section>
        <h2>Side by Side</h2>
        <div class="two-col">
          <div class="col">
            <p>Left column text or code</p>
          </div>
          <div class="col">
            <p>Right column content</p>
          </div>
        </div>
      </section>

      <!-- SLIDE 6: Vertical stack (sub-slides) -->
      <section>
        <section>
          <h2>Parent Slide</h2>
          <p>Press down arrow to go deeper</p>
        </section>
        <section>
          <h2>Sub-slide</h2>
          <p>Useful for drilling into a topic</p>
        </section>
      </section>

    </div>
  </div>

  <!-- reveal.js -->
  <script src="https://cdn.jsdelivr.net/npm/reveal.js/dist/reveal.js"></script>

  <!-- KaTeX -->
  <script src="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/contrib/auto-render.min.js"></script>

  <script>
    // Initialize reveal.js
    Reveal.initialize({
      hash: true,                  // URL updates on slide change
      slideNumber: true,
      transition: 'fade',          // fade | slide | convex | concave | zoom | none
      transitionSpeed: 'slow',
      backgroundTransition: 'fade',
      controls: true,
      progress: true,
      center: true,
      width: 1280,
      height: 720,
    });

    // Render KaTeX math
    renderMathInElement(document.body, {
      delimiters: [
        { left: '$$', right: '$$', display: true },
        { left: '$', right: '$', display: false },
      ]
    });
  </script>
</body>
</html>
```

## The custom.css File

Create `assets/custom.css`:

```css
/* ─── Authentic Manim / 3B1B Palette ─── */
/* Colors sourced from manim.constants — the exact values Grant uses. */
:root {
  --background:    #000000;   /* true black, like Manim scenes */
  --surface:       #111111;
  --blue:          #58C4DD;   /* Manim BLUE */
  --blue-d:        #29ABCA;
  --blue-b:        #9CDCEB;
  --teal:          #5CD0B3;
  --green:         #83C167;
  --yellow:        #FFF1B5;   /* mellow yellow — on-screen headline color */
  --yellow-bright: #FFFF00;
  --gold:          #F0AC5F;
  --red:           #FC6255;
  --maroon:        #C55F73;
  --purple:        #9A72AC;
  --white:         #FFFFFF;
  --muted:         #888888;
}

/* ─── Base overrides ─── */
.reveal {
  background-color: var(--background);
  font-family: 'Computer Modern Serif', 'Latin Modern Roman', Georgia, serif;
  color: var(--white);
  font-weight: 400;
}

.reveal h1, .reveal h2, .reveal h3 {
  color: var(--blue);
  font-family: 'Computer Modern Serif', 'Latin Modern Roman', Georgia, serif;
  font-weight: 400;        /* CM looks best un-bolded */
  text-transform: none;
}

.reveal p, .reveal li {
  font-size: 1.15rem;
  line-height: 1.7;
  color: var(--white);
}

.reveal .subtitle {
  color: var(--muted);
  font-size: 1.2rem;
  font-style: italic;
}

/* ─── Math — KaTeX renders in Computer Modern already, so math matches body ─── */
.katex-display {
  color: var(--yellow);
  margin: 1.8rem 0;
  font-size: 1.4rem;
}

/* ─── Two-column layout ─── */
.two-col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
  text-align: left;
}

/* ─── Video slides ─── */
.reveal video {
  max-width: 80%;
  border-radius: 8px;
  box-shadow: 0 0 40px rgba(79, 195, 247, 0.3);
}

/* ─── Fragment animations ─── */
.reveal .fragment {
  transition: opacity 0.4s ease, transform 0.4s ease;
}
.reveal .fragment.visible {
  opacity: 1;
  transform: translateY(0);
}
.reveal .fragment:not(.visible) {
  opacity: 0;
  transform: translateY(10px);
}

/* ─── Progress bar ─── */
.reveal .progress {
  color: var(--blue);
}

/* ─── Code blocks ─── */
.reveal pre code {
  background: #0a0a0a;
  border: 1px solid #222;
  border-radius: 4px;
  font-family: 'JetBrains Mono', Menlo, monospace;
  font-size: 0.85rem;
  line-height: 1.5;
}
```

## Key reveal.js Concepts

### Navigation
| Key | Action |
|-----|--------|
| `→` / `Space` | Next slide |
| `↓` | Sub-slide (vertical stack) |
| `F` | Fullscreen |
| `S` | Speaker notes view |
| `?` | All keyboard shortcuts |

### Fragments (progressive reveal)
```html
<!-- Simple reveal -->
<p class="fragment">Appears on keypress</p>

<!-- With animation -->
<p class="fragment fade-up">Slides up</p>
<p class="fragment highlight-blue">Highlights blue</p>

<!-- Ordered -->
<p class="fragment" data-fragment-index="2">Second</p>
<p class="fragment" data-fragment-index="1">First</p>
```

### Speaker Notes
```html
<section>
  <h2>My Slide</h2>
  <aside class="notes">
    These notes only show in the presenter view (press S).
    Add timing cues, talking points, etc.
  </aside>
</section>
```

### Backgrounds per slide
```html
<section data-background-color="#1a1a2e">...</section>
<section data-background-image="assets/images/bg.png" data-background-opacity="0.3">...</section>
<section data-background-video="assets/videos/loop.mp4" data-background-video-loop>...</section>
```

## Exporting / Sharing

### As a website
- Push the whole folder to GitHub, enable GitHub Pages → instant URL
- Or drag to Netlify / Vercel

### As a PDF
1. Open `index.html?print-pdf` in Chrome
2. File → Print → Save as PDF
3. Set layout to Landscape, no margins

### As a video (screen record)
- Use QuickTime (Mac) or OBS to record yourself presenting

## Embedding Manim Videos

Export from Manim:
```python
# At end of your Manim scene
self.wait(1)
# Run: manim -pql scene.py MyScene
# Outputs to media/videos/scene/...
```

Copy the `.mp4` to `assets/videos/` then embed:
```html
<section data-background-video="assets/videos/my_animation.mp4"
         data-background-video-loop
         data-background-opacity="1">
  <!-- optionally overlay text -->
</section>
```

Or inline:
```html
<video data-autoplay loop muted playsinline>
  <source src="assets/videos/my_animation.mp4" type="video/mp4" />
</video>
```

## Tips for the 3B1B Aesthetic

1. **True black background** — `#000000` matches Manim scenes. The eye locks onto colored shapes, not the frame.
2. **Computer Modern everywhere** — body, headings, and math all in the same LaTeX font. No sans/serif mix. This is the single strongest visual cue.
3. **One accent color per concept** — Manim BLUE `#58C4DD` for definitions, YELLOW `#FFF1B5` for key results, GREEN `#83C167` for examples, RED `#FC6255` for warnings.
4. **Large, sparse text** — don't cram slides. One idea per slide.
5. **Fade transitions only** — `transition: 'fade'` beats slides/zoom. No horizontal/vertical slide motion; 3B1B never does that.
6. **Math big and centered** — `font-size: 1.4rem+` on KaTeX display blocks, colored yellow for emphasis.
7. **Embed Manim for anything animated** — don't try to CSS-animate math diagrams. The whole point of the aesthetic is that the diagrams come from Manim.
8. **No bold** — Computer Modern doesn't have a great bold weight on the web. Use color for emphasis instead.
