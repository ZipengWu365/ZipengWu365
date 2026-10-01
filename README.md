# Zipeng Wu

<p>
  <a href="mailto:zxw365@student.bham.ac.uk"><img alt="Email" src="https://img.shields.io/badge/email-zxw365%40student.bham.ac.uk-0A66C2?style=flat-square"></a>
  <a href="https://zipengwu365.github.io/"><img alt="Website" src="https://img.shields.io/badge/Website-zipengwu365.github.io-C98A00?style=flat-square"></a>
  <a href="https://zipengwu365.github.io/cv.html"><img alt="CV" src="https://img.shields.io/badge/CV-temporal%20representation-17324D?style=flat-square"></a>
  <a href="https://scholar.google.com/citations?user=CROGdXYAAAAJ&hl=en"><img alt="Google Scholar" src="https://img.shields.io/badge/Google%20Scholar-Zipeng%20Wu-4285F4?style=flat-square&logo=googlescholar&logoColor=white"></a>
  <a href="https://www.linkedin.com/in/zipeng-wu-a98944189/"><img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-Zipeng%20Wu-0A66C2?style=flat-square&logo=linkedin&logoColor=white"></a>
  <a href="https://research.birmingham.ac.uk/en/persons/zipeng-wu"><img alt="University of Birmingham profile" src="https://img.shields.io/badge/UoB-research%20profile-A1211B?style=flat-square"></a>
</p>

I am a PhD researcher in Applied Mathematics at the University of Birmingham. My research focuses on temporal representation theory and methods, with applications to non-stationary time-series learning, foundation models, and world models.

I study how representations of temporal structure support comparison, retrieval, forecasting, and classification. My current scope includes time series, action histories, VLA trajectories, model rollouts, and temporal memory.

## Research focus

- **Representation and decomposition:** representation theory, temporal component recovery, mechanism-driven evaluation, and signal feature extraction.
- **Similarity and retrieval:** structural comparison and stationarity-aware retrieval for forecasting.
- **Prediction and regression:** output dependencies, online learning, hierarchical forecasting, and interpretable grouped regression.
- **Current directions:** time-series classification, symbolic representation and compression, and temporal tokenization for foundation and world models.

## Research map

My research centres on **temporal representation**. The map places my published work under three research themes, with my MRes and PhD work on representation theory as the common basis.

[![Zipeng Wu's research map: Representation and Decomposition contains the ICML 2026 benchmark and MIIR 2025 ultrasound report; Similarity and Retrieval contains SARAF, KDD 2026; Prediction and Regression contains taxi demand, online multi-output regression, COVID-19 prediction, hierarchical load forecasting, and iTARGET. Software, accepted workshop work, and current projects have explicit labels.](assets/temporal-representation.png)](https://zipengwu365.github.io/research.html#research-map)

- **Representation and decomposition:** the ICML 2026 component-recovery benchmark and the MIIR 2025 report on battery ultrasound signals. DeTime and TSDecompose-Benchmark are research software outputs.
- **Similarity and retrieval:** SARAF (KDD 2026) uses stationarity-aware historical retrieval for forecasting. EchoTime provides explainable structural comparison.
- **Prediction and regression:** dynamic regressor chains for taxi demand (IJCNN 2020), online kNN regressor chains (ICONIP 2023), and adaptive COVID-19 prediction (Heliyon 2023) address output dependencies and online learning. Hierarchical load forecasting (ICONIP 2022) and iTARGET (BIBM 2024) develop interpretable prediction. iTARGET estimates age from methylation profiles.

Current work includes time-series classification, symbolic encoding and compression, and temporal tokenization for foundation and world models. The map also labels **Semantics-Enhanced Retrieval-Augmented Time Series Forecasting** as **accepted ICML 2026 workshop work**.

PAA, SAX, and SAA-SAX are representative literature methods for the symbolic/compression direction. [Paper summaries and connections](https://zipengwu365.github.io/research.html#research-map) explain how the individual works fit the programme.

[Related work](https://zipengwu365.github.io/research.html#research-map) · [Editable PowerPoint](assets/temporal-representation.pptx)

## Recent highlights

- **UKRI/AIRR compute resources (2026):** two Gateway Project allocations on Isambard-AI: **Time Series Language and Foundation Model** and **Language-Action Time-Series Tokenization for Efficient VLA Policies**. Each project provides 10,000 GPUHR with nominal compute-resource value GBP 45,000; together they total 20,000 GPUHR with nominal compute-resource value GBP 90,000. Compute resources only, not direct cash funding.
- **University of Birmingham College PhD Scholarship:** full scholarship support for Applied Mathematics PhD study from Jan 2024 to Jul 2027, covering tuition fees and stipend/living costs.
- **ICML 2026:** first-author main-conference paper, **Time-Series Decomposition as a Standalone Task: A Mechanism-Driven Diagnostic Benchmark**.
- **KDD 2026:** co-author on **Stationarity-Aware Retrieval-Augmented Time Series Forecasting**.

## Selected publications

- **ICML 2026 | CORE/ICORE A&#42;**: **Time-Series Decomposition as a Standalone Task: A Mechanism-Driven Diagnostic Benchmark.** First author.
- **KDD 2026 | CORE/ICORE A&#42;**: **Stationarity-Aware Retrieval-Augmented Time Series Forecasting.** Co-author.
- **MIIR 2025 | Technical report**: **Non-contact ultrasound testing of batteries.** Co-author. [Institutional record](https://research.birmingham.ac.uk/en/publications/non-contact-ultrasound-testing-of-batteries/).
- **BIBM 2024 | CORE/ICORE B**: **iTARGET: Interpretable Tailored Age Regression for Grouped Epigenetic Traits.** First author.
- **Heliyon 2023 | JCR Q1**: **A novel online multi-task learning for COVID-19 multi-output spatio-temporal prediction.** First author.
- **ICONIP 2023 | Oral presentation | CORE/ICORE B**: **Correlated Online k-Nearest Neighbors Regressor Chain for Online Multi-output Regression.** First author.
- **ICONIP 2022 | Oral presentation | CORE/ICORE B**: **An Interpretable Multi-target Regression Method for Hierarchical Load Forecasting.** First author.
- **IJCNN 2020 | Oral presentation | CORE/ICORE B**: **A Novel Dynamically Adjusted Regressor Chain for Taxi Demand Prediction.** First author.

## Selected research software

| Project | Research role | Output |
|---|---|---|
| [TSDecompose-Benchmark](https://github.com/ZipengWu365/TSDecompose-Benchmark) | Standalone time-series decomposition evaluated as component recovery; ICML 2026 paper-core results and separately labelled extension tracks. | Benchmark source and paper tables; [dataset](https://huggingface.co/datasets/Zipeng365/TSDecompose-Benchmark) / [interactive leaderboard](https://huggingface.co/spaces/Zipeng365/TSDecompose-Benchmark-Leaderboard) |
| [DeTime](https://github.com/systems-mechanobiology/DeTime) | Time-series decomposition as representation extraction for trend, oscillatory/periodic structure, residuals, and method-specific components. | Python/CLI library; [project page](https://systems-mechanobiology.github.io/DeTime/) |
| [EchoTime](https://github.com/ZipengWu365/EchoTime) | Explainable structural similarity for time series and time-series datasets. | Python package with HTML reports and compact JSON; [project page](https://zipengwu365.github.io/EchoTime/) |

## Interactive research visualizations

**[NeurIPS 2026 Institution Atlas](https://github.com/ZipengWu365/neurips-institution-atlas)** — Explore institutional paper participation through global top-200 treemaps and ten country editions. Search full institution names and download SVG charts or CSV data. An unofficial analysis of a 26 September 2026 snapshot; counting rules and affiliation limitations are documented in the repository.

**[Open the interactive atlas](https://zipengwu365.github.io/neurips-institution-atlas/)** · **[UK edition](https://zipengwu365.github.io/neurips-institution-atlas/?view=united-kingdom)**

Full publication list and CV: [academic homepage](https://zipengwu365.github.io/) / [publications](https://zipengwu365.github.io/publications.html) / [CV](https://zipengwu365.github.io/cv.html).
