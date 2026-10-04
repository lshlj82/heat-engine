# Engines and Refrigerators, Interactively

An interactive, single-page web demo of heat engines and refrigerators: the Carnot limit on efficiency and why entropy imposes it, the Carnot cycle, the Curzon–Ahlborn engine at maximum power, refrigerators and their coefficient of performance, why no machine can beat Carnot, and the real Otto and Stirling cycles.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee** (Statistical Physics 1, Chapter 4, Engines and Refrigerators, Sections 4.1 to 4.3). It follows the demos for Chapter 3 (temperature, entropy, pressure, and chemical potential).

## What's inside

**Heat engines and the Carnot limit.** An energy-and-entropy flow diagram for an engine or a refrigerator between two reservoirs. Set the temperatures and the efficiency (or COP) as a share of its limit; the diagram shows Q<sub>h</sub>, Q<sub>c</sub>, and W, the entropy taken in and given out, and the net entropy created. Push past 100% of the limit and the page shows the entropy going negative: forbidden by the second law.

**The Carnot cycle and maximum power.** The derivation of e = 1 − T<sub>c</sub>/T<sub>h</sub> for an ideal gas (Problem 4.5), and the Curzon–Ahlborn "endoreversible" engine (Problem 4.6): a chart of power and efficiency against the working temperature, with the maximum power at T<sub>hw</sub> = ½(T<sub>h</sub> + √(T<sub>h</sub>T<sub>c</sub>)) and efficiency 1 − √(T<sub>c</sub>/T<sub>h</sub>). For a coal-fired steam turbine between 600 °C and 25 °C this gives 41.6%, close to the real 40%, against Carnot's 65.9%.

**Refrigerators.** COP = Q<sub>c</sub>/W ≤ T<sub>c</sub>/(T<sub>h</sub> − T<sub>c</sub>) (5.9 for a kitchen refrigerator), with notes on air conditioners and open refrigerator doors (Problems 4.7 and 4.8). A diagram for Problem 4.16 lets you claim an engine efficiency above Carnot's and shows how, driving a Carnot refrigerator, it would pump heat from cold to hot with no work input. Includes the history from Carnot to Clausius and Boltzmann.

**Real heat engines.** An animated cycle explorer for the Carnot, Otto, and Stirling cycles, with a PV diagram (net work shaded), the cylinder and what it is in contact with at each step, and a table of heat and work per step for one mole. Adjust temperatures, compression ratios, and the working gas (f = 3 or 5), and switch the Stirling engine's regenerator on or off. The Otto efficiency 1 − (V<sub>2</sub>/V<sub>1</sub>)<sup>γ−1</sup> (Problem 4.18) and the Stirling efficiency with and without a regenerator (Problem 4.21) are compared with the Carnot efficiency between the cycle's extreme temperatures. The Diesel engine is described in the text.

## Running it

There is nothing to build or install. The whole demo is one self-contained file, `index.html`, with all CSS and JavaScript inline.

Open it locally by double-clicking `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Publishing with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the demo will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical notes

- Plain HTML, CSS, and vanilla JavaScript drawn on `<canvas>`. No frameworks, no build step.
- The cycle explorer computes each step for one mole of ideal gas, with volumes in liters and pressures in kilopascals. The efficiency from its table (net work over heat taken in, not counting heat stored and returned by a regenerator) matches the textbook formulas exactly in every case, and each cycle returns ΔU = 0.
- The Curzon–Ahlborn chart assumes equal conductances K for both heat transfers and equal times for both, as in the problem; the working temperature ranges from (T<sub>h</sub> + T<sub>c</sub>)/2, where no work is done, up to T<sub>h</sub>, where no heat flows.
- The adiabatic exponent is γ = (f + 2)/f, which gives 7/5 for air.
- The animation pauses when scrolled off screen and starts paused when the system asks for reduced motion.
- Long equations wrap on narrow screens.
- Equations are typeset with [MathJax 3](https://www.mathjax.org/) (SVG output, loaded from cdnjs), so they need no extra web fonts.
- The only other external resources are the Newsreader and Instrument Sans fonts from Google Fonts, with system font fallbacks if they fail to load.
- Opening the page requires an internet connection for MathJax; offline, the equations appear as raw TeX.
- Supports light and dark mode via `prefers-color-scheme`, and is responsive down to phone widths.

## Caveats

- All cycles are idealized: quasistatic, frictionless, and with an ideal gas whose f does not change with temperature.
- The Otto cycle starts at an intake temperature of 300 K, and its peak temperature is raised automatically if it would fall below the temperature after compression.

## Credits

- Demo: Claude Opus 5.5
- Physics content and examples: lecture notes by Sang Hoon Lee
- The lecture follows Daniel V. Schroeder, *An Introduction to Thermal Physics* (Sections 4.1 to 4.3 and Problems 4.5 to 4.8, 4.16 to 4.18, and 4.21).
- Curzon–Ahlborn engine: F. L. Curzon and B. Ahlborn, "Efficiency of a Carnot engine at maximum power output," *American Journal of Physics* 43, 22–24 (1975).

## License

No license has been chosen yet. Add a `LICENSE` file (for example, MIT or CC BY 4.0) before sharing or reusing this project publicly, and confirm that any use of the lecture material is permitted by its author.
