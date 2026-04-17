# Selekcija instanci u mašinskom učenju

**Seminarski rad I** – Elektronski fakultet, Univerzitet u Nišu

## O čemu se radi

Selekcija instanci je tehnika predobrade podataka koja iz trening skupa bira reprezentativan podskup — manji, čistiji, a jednako (ili više) efikasan za klasifikaciju. Rad pokriva četiri kategorije metoda:

- **Kondenzacija** (CNN, RNN): drastično smanjuje broj instanci zadržavanjem samo onih na granicama klasa
- **Uređivanje** (ENN, RENN, All k-NN): uklanja šumne i pogrešno označene instance radi poboljšanja tačnosti
- **Hibridne metode** (DROP3, ICF): kombinuju oba pristupa za optimalan balans redukcije i kvaliteta
- **Evolucione metode** (GA, PSO): koriste meta-heuristike za globalnu optimizaciju selekcije

## Obim projekta

- **Teorijski deo:** seminarski rad (`Seminarski_Rad_Instance_Selection.docx`, `Seminarski_Rad_Instance_Selection.pdf`)
- **Praktičan deo:** Jupyter notebook (`instance_selection.ipynb`)

## Dataset

- **Lokalni fajl:** `data/winequality-red.csv`
- **Izvor (Kaggle):**
  - https://www.kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009
- 1599 instanci, 11 fizičko-hemijskih atributa, više-klasna ocena kvaliteta (3–8)

## Tok rada (Notebook)

Pipeline u `instance_selection.ipynb` uključuje:

1. Učitavanje podataka i eksploratorna analiza
2. Predobrada (standardizacija, podela na trening/test skup)
3. Baseline k-NN klasifikacija (kompletan trening skup)
4. Metode selekcije instanci:
   - Edited Nearest Neighbor (ENN)
   - Repeated ENN (RENN)
   - All k-NN
   - Condensed Nearest Neighbor (CNN)
   - DROP3 (ručna implementacija)
   - Tomek Links
5. k-NN klasifikacija nakon selekcije
6. Uporedna evaluacija (tačnost, F1-score, stopa redukcije, vreme predikcije)
7. Confusion matrice i distribucija klasa posle selekcije

## Tehnologije

- **Jezik:** Python (notebook workflow)
- **Osnovne biblioteke:** `pandas`, `numpy`, `scikit-learn`
- **Selekcija instanci:** `imbalanced-learn`, ručna implementacija (DROP3)
- **Vizualizacija:** `matplotlib`, `seaborn`

## Strategija modelovanja

Projekat poredi performanse k-NN klasifikatora kroz različite strategije selekcije instanci:

- **Baseline:** k-NN treniran na kompletnom (nemodifikovanom) trening skupu
- **Metode uređivanja:** ENN, RENN, All k-NN: fokus na uklanjanje šuma i poboljšanje tačnosti
- **Metode kondenzacije:** CNN, Tomek Links: fokus na redukciju veličine skupa
- **Hibridna metoda:** DROP3: kombinacija ENN čišćenja i dekrementalne kondenzacije
- Završna tabela uključuje tačnost, F1-score, stopu redukcije i vreme klasifikacije

## Napomene

- Ocene kvaliteta su grupisane u tri klase (loš/srednji/dobar) radi jasnijih granica klasifikacije.
- Svi atributi su standardizovani pre primene metoda zasnovanih na rastojanju.
- DROP3 je implementiran ručno jer ne postoji u standardnim Python bibliotekama.
- Tačne vrednosti metrika zavise od random seed-a i podele pri kros-validaciji.