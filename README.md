# How rectifier diode C<sub>jc</sub> affects the LLC gain curve

An interactive explainer showing why an LLC resonant converter's gain can rise again at high switching frequency, so the output can no longer be regulated by raising frequency. The cause is the rectifier diode's junction capacitance (C<sub>jc</sub>).

**▶ Live app:** https://warayutmachima007-hash.github.io/llc-cjc-gain-curve/

[![Demo video](media/preview.jpg)](media/llc-cjc-demo.mp4)

*Click the image to watch the 47-second walkthrough (`media/llc-cjc-demo.mp4`).*

## What it shows

- **The converter and its AC equivalent circuit.** Both drawings update live as you change C<sub>jc</sub> and the load.
- **The gain curve vs F<sub>s</sub>/F<sub>R</sub>.** You can sweep C<sub>jc</sub> (0–5 nF) and the load (100 Ω – 10 kΩ).
- **One toggle per parasitic:** L<sub>lks</sub>, C<sub>TR</sub> and C<sub>jc</sub>. Toggling them shows that **only C<sub>jc</sub>** makes the gain rise with frequency.
- **Readouts from the paper's equations:** F<sub>R</sub> (eq. 3), the F<sub>R</sub> shift from L<sub>lks</sub> (eq. 4), the gain at F<sub>R</sub> (eq. 6) and the extra resonance F<sub>JC</sub> (eq. 9).
- **Load-step simulation:** a behavioural, averaged simulation with frequency control. Load steps from 100 Ω to a light load and back. With C<sub>jc</sub>, the controller raises f<sub>s</sub> past the gain minimum, the gain rises instead of falling, and V<sub>O</sub> runs away while f<sub>s</sub> pins at its limit. This is the regulation failure the paper describes. (The controller, lag and limits are illustrative, not from the paper.)
- **The paper's four fixes:** dummy load, limiting F<sub>s,max</sub>, rectifier type, and low-Q design.

## Source

B.-H. Lee, M.-Y. Kim, C.-E. Kim, K.-B. Park, G.-W. Moon, "Analysis of LLC Resonant Converter Considering Effects of Parasitic Components," *IEEE INTELEC 2009*, Incheon. [doi:10.1109/INTLEC.2009.5351740](https://doi.org/10.1109/INTLEC.2009.5351740)

The parameter values (Table 1, PDP column), equations and conclusions come from the paper. The circuit drawings, code and curves are an independent re-implementation, not reproductions of the paper's figures. The paper itself is not included in this repository.

**Reproduction note.** With these values, the model matches the paper's Fig. 13(b) within about ±0.04. To match, the plotted C<sub>jc</sub> has to enter the model as C<sub>jc</sub>·(N<sub>S</sub>/N<sub>P</sub>)², without the center-tap factor of 2 in eq. (12). The paper doesn't say which value its figures use. The app page gives the details.

## Tech

A single self-contained `index.html` with vanilla JS. [Chart.js](https://www.chartjs.org/) (MIT) is loaded from cdnjs, and there is no build step.

---

Personal project, views my own. Built with help from Claude.
