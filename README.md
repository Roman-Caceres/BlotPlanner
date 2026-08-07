# Western Blot Membrane Cut Planner

Plan where to cut a western blot membrane so a single transfer can serve several antibodies — and find
out before you cut when it won't work.

**→ [Open the planner](https://roman-caceres.github.io/BlotPlanner/)**

Works in any browser, on desktop or phone. Nothing to install, no account, no sign-in. **Your experiment
never leaves your browser** — targets, weights and calibration measurements are computed locally and stored
only in your own browser.

## What it does

Enter your target proteins by observed molecular weight. The tool places them against a
Bio-Rad Precision Plus Dual Color ladder, works out where to score the membrane, and gives you each
cut in millimetres from the top of the resolving gel — plus a landmark you can actually use at the
bench, like *"1.6 mm above the 75 kDa band"*.

It also tells you when the plan is a bad idea:

- two targets too close to separate at your chosen clearance
- a cut that would pass through a band
- strips too thin to handle without curling
- targets outside the gel's resolving range
- positions extrapolated beyond your calibration
- same-host primaries sharing a strip, where one secondary would light up both

> **Ladder:** this assumes a **Bio-Rad Precision Plus Protein Dual Color** standard (#1610374). If you run a
> different ladder the band sizes will not match and the positions will be wrong — including the rows in the
> calibration table. Support for other ladders is planned;
> [tell me which one you use](https://github.com/Roman-Caceres/BlotPlanner/issues) and it moves up the list.

## Three sources for band positions, worst to best

1. **Model** — a semi-log construction from conventional resolving ranges. A starting estimate.
2. **Bio-Rad chart** — Rf values from Bio-Rad's published Criterion Tris-HCl migration chart. Real
   vendor data, but for *unstained* standards on *precast midi* gels.
3. **Calibrated** — a least-squares fit to ladder distances you measure off your own Ponceau, with R²
   and residuals reported. **The only mode grounded in the membrane you are about to cut.**

The tool always shows which one is in use and refuses to present an extrapolated position as reliable.

## Loading controls

22 presets grouped by subcellular fraction — whole cell/cytoplasmic, cytoskeletal, nuclear,
mitochondrial, plasma membrane — so you don't pair a cytoplasmic control with a nuclear prep. Every
molecular weight was read from that antibody's own Cell Signaling datasheet and carries its catalog
number, so you can check any of them.

## Install it on your phone

- **Android / Chrome:** menu → *Install app*
- **iPhone / Safari:** Share → *Add to Home Screen*

It then opens fullscreen and works offline.

## Run it yourself

Download `index.html` and open it — the whole tool is one self-contained file that works with no
internet connection. For the installable version with offline caching, serve the folder over http:

```bash
python -m http.server 8765
```

## Found something wrong?

Please [open an issue](https://github.com/Roman-Caceres/BlotPlanner/issues/new/choose). There are templates
for three things:

- **A number looks wrong** — the most useful report this tool can get. Every value carries a source, so a
  disagreement gets settled against the datasheet rather than argued.
- **Something is broken** — crashes, layout problems, anything that misbehaves.
- **Support my ladder** — tell me which standard you run and it moves up the list.

## Privacy

Your experiment stays in your browser. There is no server, no account and no tracking of your work. The
hosted site may count anonymous page views — a visit and nothing else, no IP address and no cookies — so I
can tell whether anyone is using it. That never runs on a downloaded copy or offline. If you'd rather not be
counted, download `index.html` and open it directly; it's the complete tool and makes no network requests at
all.

## Licence

© Roman Caceres. **Free to use for research.** Not currently released under an open-source licence, so the
code is not offered for redistribution or reuse — if you want to build on it, or need it under a specific
licence for your institution, [ask](https://github.com/Roman-Caceres/BlotPlanner/issues) and we'll sort it out.

## For research use only

A planning aid, not a measurement. Provided as-is without warranty of any kind; no liability is
accepted for experimental loss arising from its use. **Verify every cut position against your own
stained membrane before scoring it.**

Bio-Rad, Precision Plus Protein, Cell Signaling Technology and all product names are trademarks of
their respective owners. This tool is independent and is not endorsed by, affiliated with, or
produced in partnership with any of them.
