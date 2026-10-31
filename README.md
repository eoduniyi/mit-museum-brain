# mit-museum-brain
### thinking cells frozen and in motion

[![firebase hosting](https://img.shields.io/badge/firebase-hosting-orange.svg)](https://firebase.google.com/)
[![onnx webgl](https://img.shields.io/badge/onnx-runtime--web-blue.svg)](https://onnxruntime.ai/)
[![license: mit](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

a curatorial research platform and interactive installation developed for the **mit museum**, connecting archival museum photography, continuous biophysical feature tensors, edge-guided botanical diffusion priors, and kinetic cellular choreography.

developed for the **brain digital content open call** and **brain programmatic open call**, this repository serves as the public home for the interactive web application, companion research notebooks, and academic manuscripts.

---

## vision & purpose

while a physical museum exhibition does not inherently require a web application, an untainted, browser-based deployment represents the most portable, zero-configuration medium to:
1. **present the core ideas to curators, jurors, and visitors** with instantaneous live execution across kiosks, tablets, and desktop workstations.
2. **democratize computational curatorial tools**, allowing individuals and peer cultural institutions to ingest, filter, and choreograph their own historical archives.
3. **bridge frozen historical artifacts with continuous neural computation**, reimagining static vitrine specimens as active participants in generative cellular dynamics.

---

## system architecture

```
+---------------------------------------------------------------------------------------+
|                                    MIT-MUSEUM-BRAIN                                   |
+---------------------------+---------------------------+-------------------------------+
|  TIER 1: CORPUS PACKAGING |  TIER 2: FEATURE TENSORS  |  TIER 3: DIFFUSION & SHADERS  |
|  25 authentic specimens   |  affine luminance L(x,y)  |  64x64 onnx dino diffusion    |
|  384x384 lanczos crops    |  sobel gradient fields    |  anisotropic gray-scott pde   |
|  base64 zero-cors bundle  |  atkinson engraving plate |  isophote curl-noise flow     |
+---------------------------+---------------------------+-------------------------------+
                                            |
                                            v
+---------------------------------------------------------------------------------------+
|                         TIER 4: KINETIC ORBITAL CHOREOGRAPHY                          |
|         2-cell partner waltzes * 3-cell triad carousels * 4-cell quartet pinwheels    |
+---------------------------------------------------------------------------------------+
```

### 1. tier 1: untainted local corpus packaging
to guarantee offline kiosk compatibility without browser `file://` cors violations or canvas taint security exceptions, 25 authentic mit museum artifacts were preprocessed, center-cropped to $384\times 384$ pixels via lanczos filtering, and serialized into `museum_corpus_data.js` as base64 data uris. data uris inherit the document security context, ensuring instantaneous synchronous pixel ingestion.

### 2. tier 2: structural feature tensors
each specimen cell precomputes four structural fields:
- **dynamic-range normalized luminance**: perceptual luminance $L_0 = (0.299R + 0.587G + 0.114B)/255$, normalized across each specimen's dynamic range $[L_{\min}, L_{\max}]$.
- **sobel gradient vector field**: horizontal and vertical derivatives $(G_x, G_y)$ and edge magnitudes $E(x,y)$.
- **high-pass engraving plate**: strided local mean subtraction $\bar{L}_5(x,y)$ combined with atkinson error diffusion for crisp stippling under uneven museum vitrine lighting.

### 3. tier 3: diffusion workbench & cellular shaders
- **edge-guided dino diffusion**: runs ollin boer bohan's *dino diffusion* u-net via onnx runtime web (webgl), conditioned on $64\times 64$ sobel silhouette guidance.
- **four real-time cellular modes**:
  - `etch`: coarse-to-fine block sampling converging onto the atkinson plate.
  - `reaction`: anisotropic gray-scott reaction-diffusion solver modulated by object edge maps.
  - `flow`: curl-noise advection along incompressible isophote velocity fields $\vec{v} = (-G_y, G_x)$.
  - `halftone`: phase-shifted copperplate cross-hatching.

### 4. tier 4: kinetic orbital choreography
a 60 fps spring-physics simulation orchestrates the 25 cells across the $5\times 5$ grid into 2-cell partner waltzes, 3-cell triad carousels, and $2\times 2$ quartet pinwheels.

---

## repository structure

```
mit-museum-brain/
├── firebase.json                   # firebase hosting configuration and caching headers
├── .firebaserc                     # firebase project environment settings
├── .gitignore                      # clean git ignore rules
├── README.md                       # project documentation and submission brief
├── public/                         # web application home (firebase hosting root)
│   ├── index.html                  # primary interactive web application (5x5 matrix + workbench)
│   ├── benchmark.html              # performance benchmark harness (fps & latency metrics)
│   └── assets/                     # curated media, model weights, and corpus bundle
│       ├── museum_corpus_data.js   # base64 preprocessed 25-specimen data bundle
│       ├── network.onnx            # 8 mb dino diffusion u-net weights
│       └── *.jpg / *.png           # authentic high-resolution museum archival photographs
└── research/                       # academic research, notebooks, and proposals
    ├── notebooks/                  # computational exploration
    │   ├── mit_museum_thinking_machines.ipynb
    │   └── mit_museum_thinking_machines.html
    ├── papers/                     # peer-reviewed publication manuscripts
    │   ├── vitrified-synapses/     # 3-page theoretical framework (cryo-et & fluxons)
    │   │   ├── paper1.tex
    │   │   └── paper1.pdf
    │   └── thinking-cells-cga/     # ieee cg&a / acm interactions manuscript
    │       ├── thinking_machines_ieee_cga_paper.tex
    │       ├── thinking_machines_ieee_cga_paper.pdf
    │       └── thinking_machines_ieee_cga_paper.html
    └── proposals/                  # open call dossiers & curatorial documentation
        ├── liquid_synapse_program_proposal.md
        ├── paper_1_vitrified_superconducting_synapses.md
        ├── notes.md
        └── brain-pseudo-code.txt
```

---

## quick start

### option a: zero-dependency local launch
the application is engineered to run out of the box with zero npm packages or build steps:
```bash
# clone the repository
git clone https://github.com/viral-medialab/mit-museum-brain.git
cd mit-museum-brain

# open directly in any web browser
open public/index.html
```

### option b: local static server
```bash
# via python
python3 -m http.server 8080 -d public

# or via npx
npx serve public
```

### option c: firebase hosting
```bash
# install firebase cli if needed
npm install -g firebase-tools

# login and emulate locally
firebase serve

# deploy live to production
firebase deploy --only hosting
```

---

## curatorial specimens in the corpus

the 25 featured artifacts span cybernetics, robotics, computing history, scientific instrumentation, and contemporary media art at mit:

| slot | artifact name | year | accession / motif |
|---|---|---|---|
| 00 | edgerton milk drop coronet | 1957 | high-speed stroboscopic splash |
| 01 | edgerton lab notebook 304 | 1934 | circuit schematic & strobe calculations |
| 02 | edgerton bullet through apple | 1964 | 1/1,000,000 second microflash |
| 03 | edgerton in laboratory | 1940 | laboratory portrait with strobe banks |
| 04 | bush differential analyzer | 1931 | mechanical wheel-and-disc integrator |
| 05 | whirlwind i magnetic core memory | 1951 | 32x32 coincident-current core plane |
| 06 | tx-0 transistorized computer | 1956 | experimental direct-memory display |
| 07 | cadr lisp machine | 1979 | ai lab symbolic computing console |
| 08 | connection machine cm-2 | 1987 | 65,536-processor hypercube supercomputer |
| 09 | apollo guidance computer dsky | 1969 | raytheon-built core rope interface |
| 10 | apollo woven core rope memory | 1968 | hand-woven software ROM matrix |
| 11 | minsky confocal scanning microscope | 1957 | pinhole spatial filter apparatus |
| 12 | shannon theseus maze-solving mouse | 1952 | electromechanical relay maze solver |
| 13 | draper inertial gyroscope | 1953 | floated integrating gyro accelerometer |
| 14 | event horizon black hole imaging | 2019 | interferometric computational radio |
| 15 | raibert 2d planar hopping machine | 1983 | dynamic leg balance pneumatic actuator |
| 16 | mit floor turtle robot | 1972 | papert logo cybernetic mechanical creature |
| 17 | brooks genghis hexapod walker | 1989 | subsumption architecture walking robot |
| 18 | breazeal kismet sociable robot | 1999 | expressive humanoid robotic face |
| 19 | cog humanoid upper-body robot | 1994 | embodied social humanoid torso |
| 20 | hart nautical carved half-hull | 1895 | carved white pine & mahogany lines |
| 21 | hart nautical collection display | 1922 | cased rigged sailing vessel models |
| 22 | benton rainbow white-light hologram | 1968 | transmission rainbow holographic plate |
| 23 | crochet coral reef installation | 2022 | hyperbolic crochet coral ecosystem |
| 24 | essential mit collection artifacts | 2018 | mit campus history, timber & foil |

---

## research manuscripts & citations

1. **vitrified synapses in superconducting neuromorphic circuits**  
   *erick oduniyi*, massachusetts institute of technology (2026).  
   a 3-page theoretical framework connecting time-resolved cryo-et morphometry to single flux quantum (sfq) circuits and magnetic josephson synapses.  
   located at [`research/papers/vitrified-synapses/paper1.pdf`](research/papers/vitrified-synapses/paper1.pdf).

2. **thinking cells frozen and in motion**  
   *erick oduniyi*, ieee computer graphics & applications / acm interactions (2026).  
   detailed technical manuscript detailing the 4-tier system architecture, benchmarks, and gallery installation designs.  
   located at [`research/papers/thinking-cells-cga/thinking_machines_ieee_cga_paper.pdf`](research/papers/thinking-cells-cga/thinking_machines_ieee_cga_paper.pdf).

---

## extending to other collections

institutions and researchers can adapt the pipeline to new collections by running the python preprocessing script:
```bash
python3 scripts/preprocess_collection.py --input /path/to/raw_photos/ --output public/assets/
```
the script resamples images to $384\times 384$ lanczos squares and compiles `museum_corpus_data.js`, enabling instant drag-and-drop replacement of the exhibition corpus.

---

## license

mit license. copyright (c) 2026 erick oduniyi / mit media lab.
