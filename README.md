---
title: "Finn Lim"
permalink: /
layout: single
author_profile: true
---

**Quantitative Research/ Data Scientist**

**Technical Skills:** Python, SQL, AWS, R, Microsoft Excel, Power BI

## Education
- Masters of Data Science in Economics | Singapore Management University (SMU) (_Aug 2026 - Ongoing_)
  - Relevant Courses: Cloud Computing
  - Awards: MDSE DSA Distinguished Alumni Scholarship for Academic Excellence and Leadership

- Bachelor of Business Management | Double Major in Quantitative Finance and Data Science | Singapore Management University (SMU) (_Aug 2022 - May 2026_)
  - Relevant Courses: Linear Algebra, Stochastic Calculus, Text Mining, Reinforcement Learning, Time Series
  - Honors: Summa Cum Laude (GPA: 3.90/4.00); Dean's List (AY2022/23 & AY2024/25)

- Diploma in Banking and Finance | Ngee Ann Polytechnic (GPA: 3.84/4.00) (_Apr 2017 - May 2020_)

## Personal Projects
**[LLM Agent for Automated Financial News Intelligence](https://github.com/finnlimjc/portfolio_analytics)** (_Jul 2026 - Ongoing_)
- Architected an autonomous research agent that resolves a tracked equity universe, aggregates coverage across 12+ sources, and renders a cited daily digest by splitting logic between deterministic scripts and LLM-driven judgment, connected via JSON contracts to prevent either layer from silently assuming the other's responsibility.
- Built pipeline-level correctness safeguards after an early run silently shipped an incomplete digest: a completion gate blocking downstream processing until every source is clear, plus an append-only URL index with schema validation to prevent duplicate reporting.
- Cut LLM token consumption by 33% by profiling per-source token spend, instructing the agent to craft search queries for targeted results, and restructuring lines of agent instructions into point-of-use modules.

**[Realized Volatility Forecasting with HAR-X and GARCH](https://github.com/finnlimjc/Realized-Volatility-Forecasting)** (_Jan 2026 - Feb 2026_)
![Streamlit volatility forecasting dashboard](/assets/img/realized-volatility.png){: .align-right width="300px"}
- Built a Streamlit dashboard for one-step-ahead volatility forecasting, fitting HAR and HAR-X models on candidate range-based volatility estimators (Parkinson, Garman-Klass, Rogers-Satchell and the average of the three) and a GARCH(1,1) model on log returns, all estimated over a rolling window of 1,000 observations.
- Extended HAR with exogenous macro-factors by applying PCA separately to the VIX-VVIX and MOVE-GVZ-OVX groups and using the leading principal component of each as a regressor.
- Benchmarked forecasts against intraday realized volatility computed from Alpaca 5-minute data, scoring them with QLIKE and MSE loss; used the Model Confidence Set (MCS) procedure (5% significance, 10,000 bootstrap replications) to identify the best model, which was the equal-weighted average of the GARCH and HAR-X forecasts.

**[Regime Detection with Gaussian Mixture Autoregressive Model](https://github.com/finnlimjc/Regime-Classification)** (_Dec 2025 - Jan 2026_)
![Regime classification dashboard](/assets/img/regime-detection.png){: .align-right width="300px"}
- Replicated a Gaussian Mixture Autoregressive (MAR) paper from scratch to soft-cluster market regimes in SPY returns from 1992 to 2025, with each regime having its own autoregressive coefficients and variance, and latent regime memberships inferred via the Expectation-Maximization algorithm.
- Derived the E-step responsibilities and M-step updates for mixture weights, component variances, and weighted least-squares AR coefficients, documenting the derivation in the Jupyter notebooks and PDF.
- Reduced runtime from seconds to milliseconds using Numba acceleration, enabling scalable experimentation across multiple financial assets; implemented grid search hyperparameter optimization to identify optimal model configurations.

**[Sydney Temperature Derivatives Pricing Model](https://github.com/finnlimjc/Sydney-Temperature-Derivatives-Pricing-Model)** (_Jun 2025 - Jul 2025_)
![Temperature option pricing dashboard](/assets/img/temperature-derivatives.png){: .align-right width="300px"}
- Developed a time-series temperature model using additive classical decomposition, analyzed the trend component via ACF/PACF diagnostics, and fitted an ARIMA(1,1,2) model; transformed the seasonal component into the frequency domain, applied convolution filtering to remove noise, and derived a Fourier series representation with parameters estimated using the least-squares method.
- Utilized a modified Ornstein-Uhlenbeck process derived from the time-series model to describe temperature dynamics, where the process reverts to a trending mean; modelled volatility with a separate mean-reverting process, with parameters for both processes estimated using Euler discretization and an AR(1) model.
- Derived the risk-neutral pricing formula for Winter Heating Degree Day (HDD) options under the naive assumption that daily temperatures will remain below 18°C in winter, controlled by a market risk parameter; separately implemented a Monte Carlo simulation method to approximate call and put option prices while validating convexity to ensure arbitrage-free pricing.

## Academic Projects
**[Whisper Speech-to-Text System Evaluation](https://github.com/finnlimjc/AI-Systems-Evaluation)** (_Sep 2026 - Sep 2026_)
![Whisper accuracy overview](/assets/img/whisper-evaluation.png){: .align-right width="300px"}
- Benchmarked OpenAI Whisper (Tiny, Base, Large-v3) across latency, cost, and accent robustness, timing each clip using the median of 3 runs on 200 LibriSpeech clips per model; Large-v3 reached 3.8% Word Error Rate (WER) against 7.8-10.2% for the smaller models, at roughly 6-7x the latency and 11-14x the cost per 1,000 audio hours.
- Evaluated 300 accented-speech samples per model (Singaporean, Indian, and British) using WER, Substitution/Deletions/Insertion error decomposition alongside BERT-F1 semantic scoring, showing Large-v3 at ~10% WER versus ~30-35% for Tiny and Base, while all models kept BERT-F1 of 0.92-0.96.
- Built a rule-based word-level error analysis to decompose substitutions into finer categories (numeral/abbreviation, function-word swap, near-spelling variant), showing that model size reduced the number of edits. Traced Large-v3's high deletion share (52% of edits) to filler words kept in the conversational British references rather than model failure.
- Tested accent hint prompting and found it broke the small models: a rule-based transcript classifier (exact, minor, heavy, truncated, prompt echo, repetition loop via gzip compression ratio, runaway) showed truncated, looping, and runaway outputs rising for the smaller models, while Large-v3 was almost unchanged.

**[Retrieval-Augmented Generation (RAG) Chatbot for Financial Documents](https://github.com/finnlimjc/Retrieval-Augmented-Generation)** (_Sep 2026 - Sep 2026_)
![RAG chatbot architecture diagram](/assets/img/rag-chatbot.png){: .align-right width="300px"}
- Built a multi-format ingestion pipeline in Python for a 54-file financial corpus (PDF, DOCX, PPTX, XLSX, Markdown, EML) using pdfplumber, pypdf, python-docx, python-pptx and openpyxl, extracting narrative text, tables as Markdown, hidden worksheets, speaker notes, and recursively re-ingested email attachments.
- Routed embedded images and scanned PDFs to Gemini 3.6 Flash for OCR and chart-data extraction using LangChain and prompt templates, cached outputs on disk keyed by a hash of image bytes and prompt to avoid repeat calls across re-runs, cutting API cost and latency.
- Collaborated on the Streamlit RAG chatbot using Chroma for persistent vector storage, configurable overlapping word-based chunking and top-k semantic retrieval, with Gemini generating grounded answers with numbered source citations; filtered out sources containing detected prompt-injection patterns and documented remaining gaps (vector charts, confidentiality enforcement, unvalidated vision output).

**[Singapore HDB Resale Price Forecast](https://github.com/finnlimjc/Singapore-Housing-Price-Forecast)** (_Sep 2025 - Nov 2025_)
![Final HDB resale price model](/assets/img/hdb-resale.png){: .align-right width="300px"}
- Built an interpretable OLS regression model on HDB resale data with log-transformed price and floor area, min-max scaled remaining lease, and dummy-coded categoricals; engineered features by grouping towns into mature/non-mature estates and five regions, converting storey ranges to midpoints and storey groups, and consolidating flat models using lease and floor area.
- Identified outliers via studentised residuals (±3) and high-leverage points via Cook's Distance, then compared full, outlier-removed and outlier-and-leverage-removed models; selected the outlier-removed model with the highest adjusted R² of 86.07% and substantially improved AIC/BIC while retaining more data.
- Validated model assumptions through actual-vs-predicted plots, residual density and Q-Q diagnostics, identifying heavy tails and underestimation of higher-priced flats, and excluded quarter as a feature after recognising that the absence of sale year made the temporal trend unreliable.

**Text Mining for English Amazon Reviews** (_Feb 2025 - Apr 2025_)
- Built an NLP preprocessing pipeline in Python (spaCy, TextBlob, num2words, emot) that normalized noisy text by handling emojis/emoticons, internet slang, contractions, spelling errors and selective number conversion through POS tagging of dates, enabling improved sentiment analysis and text classification while preserving contextual meaning.
- Managed a team of 5 to build a multi-stage classification pipeline by developing a Bernoulli Naïve Bayes model that leveraged FastText word embeddings to separate meaningful and meaningless reviews; assisted in the development of a TF-IDF Latent Dirichlet Allocation (LDA) model that categorized general versus aspect reviews and further into specific aspect topics.
- Developed a TF-IDF n-grams Support Vector Classification (SVC) model for five-level sentiment classification; engineered features using the NLTK opinion lexicon for positive and negative word counts, VADER for compound polarity scores, and capitalization frequency, achieving 70% accuracy.
- Implemented an extractive summarization pipeline using TextRank, leveraging FastText word embeddings for semantic similarity and NetworkX PageRank with normalized thumbs-up counts as personalization weights. Grouped reviews by time, sentiment, and topic to extract representative reviews with aggregated sentiment scores.

**Prediction of Seoul's Bike Sharing Demand** (_May 2024 - Jun 2024_)
- Developed a regression model to predict daily rental bike demand, utilizing an open-source dataset with 8,760 data points incorporating environmental and temporal factors.
- Performed comprehensive exploratory data analysis (EDA) using Matplotlib and Seaborn to identify trends and correlations, while addressing preprocessing requirements like data manipulation and feature engineering.
- Supported the building of machine learning models (Multiple Linear Regression, LASSO Regression) to achieve an R-squared of 0.60 on the test set.

## Research Experience
### Singapore Management University (SMU) | Research Assistant

**Distributionally Robust Reinforcement Learning** (_Jan 2026 - Apr 2026_)
- Replicated a distributionally robust reinforcement learning framework that optimizes against worst-case distributional shifts, using Sinkhorn distance to bound deviations from a reference probability measure.
- Redesigned the price-simulation engine to replace a computationally expensive simulator with a stationary block bootstrap featuring automatic block-length calibration to preserve volatility clustering in synthetic return paths.
- Re-engineered the training pipeline by developing a shared lambda optimization method and a pre-allocated tensor-based replay buffer, cutting training time from 16-24 hours to approximately 1 hour.

**Securities Lending Data Collection** (_Oct 2024 - Oct 2025_)
- Automated extraction of securities lending data from 15,000+ SEC EDGAR filings across 3,300 entities spanning 2016-2024 using Selenium, BeautifulSoup, and FuzzyWuzzy text matching, achieving 90% automated match accuracy.
- Reviewed corporate 10-K filings and EPA news releases to identify disclosure patterns related to environmental penalties, supporting research on the relationship between regulatory enforcement and corporate reporting practices.

**Social Media Text Collection** (_Sep 2024 - Oct 2024_)
- Developed Python scripts (Selenium, BeautifulSoup4) to navigate complex site structures, consisting of form submissions, dynamically updated pages, and multiple layers of content expansion with varying formats.
- Extracted relevant data from the raw HTML content and processed the data into structured formats for analysis and storage based on client specifications. Collected approximately 100,000 posts and comments for further analysis by the professor.

## Teaching Experience
### Singapore Management University (SMU)
**[Postgraduate-Level] Data Analytics for Economics** (_Aug 2026 - Nov 2026_)
- Supported a course that teaches students to turn raw data into insights using Python, covering data cleaning, transformation, visualization and exploratory analysis, alongside Git/GitHub version control, reproducible data workflows and interactive dashboards.
