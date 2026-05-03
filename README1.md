# 📊 Data Science Portfolio — Viktoriia Lahoda

> A collection of data science and machine learning projects covering statistical analysis, NLP, and classification modelling.
> Each project includes full code, methodology, and business context.

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![R](https://img.shields.io/badge/R-276DC3?style=flat-square&logo=r&logoColor=white)](https://r-project.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)](https://scikit-learn.org)
[![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21F?style=flat-square&logo=huggingface&logoColor=black)](https://huggingface.co)

---

## 🗂️ Projects

| # | Project | Type | Tools | Language |
|---|---------|------|-------|----------|
| 01 | [Phishing Website Detection](#-01-phishing-website-detection) | Classification (ML) | Python, scikit-learn | 🐍 Python |
| 02 | [Sentiment Analysis — Olivia Rodrigo](#-02-sentiment-analysis--entity-level-nlp) | NLP / Sentiment Analysis | Python, BERT, NLTK | 🐍 Python |
| 03 | [LaLuz Bulb Lifespan Analysis](#-03-laluz-bulb-lifespan-analysis) | Statistical Analysis / EDA | R, RMarkdown | 📊 R |

---

## 🔐 01. Phishing Website Detection

**Type:** Binary Classification · Machine Learning  
**Tools:** Python · scikit-learn · pandas · numpy

### Overview
A classification system built for BookMyShow (a ticketing platform) to automatically detect whether a URL is legitimate or a phishing attempt — protecting users from malicious links in the ad system.

### Dataset
- **11,000 URL samples** with 30 technical features (SSL status, domain age, redirect count, IP address usage, etc.)
- **2 classes:** Legitimate (1) vs Phishing (0)
- Balanced class distribution (~56% / 44%)

### Methodology
- Exploratory data analysis and class balance check
- Stratified 70/30 train-test split (preserving class ratios)
- **Priority metric: Recall** — because missing a phishing link (False Negative) is far more costly than a false alarm (False Positive)
- 5-fold Stratified Cross-Validation for model stability assessment

### Models Tested & Results

| Model | Recall | F1-Score |
|---|---|---|
| Logistic Regression | 0.9105 | 0.9105 |
| k-NN (k=5) | 0.9494 | 0.9493 |
| Decision Tree | 0.9536 | 0.9536 |
| **Random Forest ✅** | **0.9671** | **0.9671** |
| Naive Bayes | 0.5855 | 0.5286 |
| Gradient Boosting | 0.9626 | 0.9626 |

### Best Model: Random Forest
- **Accuracy:** 96.71% · **Recall:** 96.71% · **Precision:** 96.71%
- False Negative Rate: 3.03% — model prioritises catching phishing over false alarms ✅
- `class_weight='balanced'`, `n_estimators=100`, `max_depth=15`

---

## 💬 02. Sentiment Analysis — Entity-Level NLP

**Type:** NLP · Sentiment Analysis  
**Tools:** Python · HuggingFace Transformers · DistilBERT · NLTK

### Overview
An entity-level sentiment analysis pipeline that extracts sentences mentioning a specific named entity (Olivia Rodrigo) from multiple text sources and classifies the sentiment of each sentence using a pre-trained transformer model.

### Methodology
- **Named Entity Recognition:** Custom sentence extractor using NLTK tokenisation — filters sentences containing any variation of the entity name
- **Model:** `distilbert-base-uncased-finetuned-sst-2-english` via HuggingFace `pipeline`
- **Sentiment classes:** POSITIVE / NEGATIVE / NEUTRAL
- **Valence scoring:** +1 / -1 / 0 for aggregated verdict

### Data Sources
- 10 real-world news articles and media texts
- 20 AI-generated texts (for dataset balancing)
- All filtered to include only sentences mentioning the entity

### Results & Visualisations
- Pie chart of sentiment distribution
- Score distribution histogram
- Box plots of confidence scores per sentiment class
- Scatter plot of sentiment scores across sentence index

### Key Findings
- Predominantly **positive media image** of the entity
- Dominant themes: awards, artistic talent, world tour achievements
- Pipeline is **fully reusable** — changing `ENTITY_NAME` applies the full analysis to any public figure or brand

---

## 💡 03. LaLuz Bulb Lifespan Analysis

**Type:** Statistical Analysis · EDA · Hypothesis Testing  
**Tools:** R · RMarkdown · ggplot2 · Shapiro-Wilk · Mann-Whitney U · t-test

### Overview
A statistical study evaluating the effectiveness of two innovations by lightbulb manufacturer LaLuz: the **DoubleBulb** (double-glass design) and the **CoatItYourself** spray (sealant coating). The analysis answers four business questions about product lifespan, cost-efficiency, and actionable recommendations.

### Dataset
- **400 lightbulbs** (200 standard, 200 DoubleBulb)
- Each type: 100 with CoatItYourself spray, 100 without
- Measured variable: `time_in_hours` of operational life

### Methodology
1. **Outlier detection** via box plots → 2 extreme outliers removed
2. **Normality testing** via Shapiro-Wilk (α = 0.05) before each test
3. **Test selection logic:**
   - Normal distribution → **Student's t-test**
   - Non-normal → **Mann-Whitney U test** (non-parametric)
4. **Economic analysis:** cost-per-hour calculated for all 4 bulb/spray combinations

### Key Findings

| Question | Finding |
|---|---|
| Does DoubleBulb last longer? | ✅ Yes — statistically significant (Mann-Whitney, p < 0.05) |
| Does spray extend lifespan? | ✅ For standard bulbs · ❌ No effect on DoubleBulb |
| Is DoubleBulb cost-effective? | ❌ More expensive per hour despite longer lifespan |
| Is spray cost-effective? | ⚠️ Marginally cheaper per hour, but impractical (hourly reapplication) |

### Recommendations
- For consumers: standard bulb + spray is the cheapest option, but marginal benefit barely justifies effort
- For manufacturer: extend spray reapplication interval, reduce price, investigate DoubleBulb formula for spray compatibility

---

## 🛠️ Stack Used Across Projects

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21F?style=for-the-badge&logo=huggingface&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-154f3c?style=for-the-badge&logo=python&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=python&logoColor=white)

---

## 📬 Contact

**Viktoriia Lahoda**  
📧 viktoriialahoda1@gmail.com  
💼 [linkedin.com/in/viktoriia-lahoda](https://linkedin.com/in/viktoriia-lahoda)  
🐙 [github.com/ViktoriiaLahoda](https://github.com/ViktoriiaLahoda)

---
---

# 📊 Portfolio Data Science — Viktoriia Lahoda

> Zbiór projektów z zakresu data science i machine learningu: analiza statystyczna, NLP oraz modelowanie klasyfikacyjne.
> Każdy projekt zawiera pełny kod, metodologię i kontekst biznesowy.

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![R](https://img.shields.io/badge/R-276DC3?style=flat-square&logo=r&logoColor=white)](https://r-project.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)](https://scikit-learn.org)
[![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21F?style=flat-square&logo=huggingface&logoColor=black)](https://huggingface.co)

---

## 🗂️ Projekty

| # | Projekt | Typ | Narzędzia | Język |
|---|---------|-----|-----------|-------|
| 01 | [Wykrywanie phishingu](#-01-wykrywanie-stron-phishingowych) | Klasyfikacja (ML) | Python, scikit-learn | 🐍 Python |
| 02 | [Analiza sentymentu — Olivia Rodrigo](#-02-analiza-sentymentu--nlp-na-poziomie-encji) | NLP / Analiza sentymentu | Python, BERT, NLTK | 🐍 Python |
| 03 | [Analiza skuteczności rozwiązań dla żarówek LaLuz](#-03-analiza-żywotności-żarówek-laluz) | Analiza statystyczna / EDA | R, RMarkdown | 📊 R |

---

## 🔐 01. Wykrywanie Stron Phishingowych

**Typ:** Klasyfikacja binarna · Machine Learning  
**Narzędzia:** Python · scikit-learn · pandas · numpy

### Opis
System klasyfikacji zbudowany dla platformy BookMyShow w celu automatycznego wykrywania, czy dany URL jest legalny czy phishingowy — chroniący użytkowników przed złośliwymi linkami w systemie reklamowym.

### Zbiór danych
- **11 000 próbek URL** z 30 cechami technicznymi (status SSL, wiek domeny, liczba przekierowań, użycie adresu IP itp.)
- **2 klasy:** Legalna (1) vs Phishing (0)
- Zrównoważony rozkład klas (~56% / 44%)

### Metodologia
- Eksploracyjna analiza danych i weryfikacja balansu klas
- Stratyfikowany podział 70/30 (zachowanie proporcji klas)
- **Priorytetowa metryka: Recall** — pominięcie phishingu (False Negative) jest znacznie droższe niż fałszywy alarm (False Positive)
- 5-krotna stratyfikowana walidacja krzyżowa (StratifiedKFold)

### Przetestowane modele i wyniki

| Model | Recall | F1-Score |
|---|---|---|
| Regresja Logistyczna | 0.9105 | 0.9105 |
| k-NN (k=5) | 0.9494 | 0.9493 |
| Drzewo Decyzyjne | 0.9536 | 0.9536 |
| **Random Forest ✅** | **0.9671** | **0.9671** |
| Naive Bayes | 0.5855 | 0.5286 |
| Gradient Boosting | 0.9626 | 0.9626 |

### Najlepszy model: Random Forest
- **Accuracy:** 96.71% · **Recall:** 96.71% · **Precision:** 96.71%
- False Negative Rate: 3.03% — model priorytetowo wykrywa phishing ✅
- `class_weight='balanced'`, `n_estimators=100`, `max_depth=15`

---

## 💬 02. Analiza Sentymentu — NLP na poziomie encji

**Typ:** NLP · Analiza sentymentu  
**Narzędzia:** Python · HuggingFace Transformers · DistilBERT · NLTK

### Opis
Pipeline do analizy sentymentu na poziomie encji — wyodrębnia zdania zawierające wzmianki o konkretnej osobie (Olivia Rodrigo) z wielu źródeł tekstowych i klasyfikuje sentyment każdego zdania przy użyciu wstępnie wytrenowanego modelu transformerowego.

### Metodologia
- **Ekstrakcja encji:** własny ekstraktor zdań oparty na tokenizacji NLTK — filtruje zdania zawierające dowolny wariant imienia
- **Model:** `distilbert-base-uncased-finetuned-sst-2-english` przez HuggingFace `pipeline`
- **Klasy sentymentu:** POSITIVE / NEGATIVE / NEUTRAL
- **Ocena walencji:** +1 / -1 / 0 dla łącznego werdyktu

### Źródła danych
- 10 autentycznych artykułów i tekstów medialnych
- 20 tekstów generowanych przez AI (do uzupełnienia zbioru)
- Wszystkie przefiltrowane pod kątem wzmianek o encji

### Wizualizacje
- Wykres kołowy rozkładu sentymentu
- Histogram dystrybucji wartości
- Box ploty pewności modelu według klasy sentymentu
- Scatter plot wyników w kolejności analizy

### Kluczowe wnioski
- Zdecydowanie **pozytywny wizerunek medialny** artystki
- Dominujące tematy: nagrody, talent, osiągnięcia trasy koncertowej
- Pipeline jest **w pełni wielokrotnego użytku** — zmiana `ENTITY_NAME` stosuje analizę do dowolnej osoby publicznej lub marki

---

## 💡 03. Analiza Skuteczności Rozwiązań dla Żarówek LaLuz

**Typ:** Analiza statystyczna · EDA · Testowanie hipotez  
**Narzędzia:** R · RMarkdown · ggplot2 · Shapiro-Wilk · Mann-Whitney U · t-test

### Opis
Badanie statystyczne oceniające skuteczność dwóch innowacji producenta żarówek LaLuz: **DoubleBulb** (podwójna bańka szklana) oraz spray **CoatItYourself** (powłoka uszczelniająca). Analiza odpowiada na cztery pytania biznesowe dotyczące czasu życia produktu, opłacalności i rekomendacji.

### Zbiór danych
- **400 żarówek** (200 standardowych, 200 DoubleBulb)
- Każdy typ: 100 ze sprayem CoatItYourself, 100 bez
- Mierzona zmienna: `time_in_hours` — czas użytkowania

### Metodologia
1. **Detekcja wartości odstających** poprzez wykresy pudełkowe → usunięto 2 skrajne obserwacje
2. **Test normalności** Shapiro-Wilka (α = 0.05) przed każdym testem
3. **Dobór testu:**
   - Rozkład normalny → **t-test Studenta**
   - Brak normalności → **test U Manna-Whitneya** (nieparametryczny)
4. **Analiza ekonomiczna:** koszt godzinny dla 4 kombinacji żarówka/spray

### Kluczowe wyniki

| Pytanie | Wynik |
|---|---|
| Czy DoubleBulb działa dłużej? | ✅ Tak — istotne statystycznie (Mann-Whitney, p < 0.05) |
| Czy spray wydłuża czas życia? | ✅ Dla zwykłych żarówek · ❌ Brak efektu dla DoubleBulb |
| Czy DoubleBulb jest opłacalny? | ❌ Droższy za godzinę mimo dłuższego czasu życia |
| Czy spray jest opłacalny? | ⚠️ Nieznacznie tańszy za godzinę, ale niepraktyczny (reaplikacja co godzinę) |

### Rekomendacje
- Dla konsumentów: zwykła żarówka + spray to najtańsza opcja, choć korzyść jest marginalna
- Dla producenta: wydłużyć czas reaplikacji sprayu, obniżyć cenę, zbadać kompatybilność spray + DoubleBulb

---

## 🛠️ Stack używany w projektach

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21F?style=for-the-badge&logo=huggingface&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-154f3c?style=for-the-badge&logo=python&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=python&logoColor=white)

---

## 📬 Kontakt

**Viktoriia Lahoda**  
📧 viktoriialahoda1@gmail.com  
💼 [linkedin.com/in/viktoriia-lahoda](https://linkedin.com/in/viktoriia-lahoda)  
🐙 [github.com/ViktoriiaLahoda](https://github.com/ViktoriiaLahoda)
