# Selekcija instanci u masinskom ucenju

**Seminarski rad I** - Elektronski fakultet, Univerzitet u Nisu

## O cemu se radi

Selekcija instanci je tehnika predobrade podataka koja iz trening skupa bira reprezentativan podskup — manji, cistiji, a jednako (ili vise) efikasan za klasifikaciju. Rad pokriva cetiri kategorije metoda:

- **Kondenzacija** (CNN, RNN): drasticno smanjuje broj instanci zadrzavanjem samo onih na granicama klasa
- **Uredjivanje** (ENN, RENN, All k-NN): uklanja sumne i pogresno oznacene instance radi poboljsanja tacnosti
- **Hibridne metode** (DROP3, ICF): kombinuju oba pristupa za optimalan balans redukcije i kvaliteta
- **Evolucione metode** (GA, PSO): koriste meta-heuristike za globalnu optimizaciju selekcije

## Obim projekta

- **Teorijski deo:** seminarski rad (`Seminarski_Rad_Instance_Selection.docx`, `Seminarski_Rad_Instance_Selection.pdf`)
- **Praktican deo:** Jupyter notebook (`instance_selection.ipynb`)

## Dataset

- **Lokalni fajl:** `data/winequality-red.csv`
- **Izvor (Kaggle):**
  - https://www.kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009
- 1599 instanci, 11 fizicko-hemijskih atributa, vise-klasna ocena kvaliteta (3–8)

## Tok rada (Notebook)

Pipeline u `instance_selection.ipynb` ukljucuje:

1. Ucitavanje podataka i eksploratorna analiza
2. Predobrada (standardizacija, podela na trening/test skup)
3. Baseline k-NN klasifikacija (kompletan trening skup)
4. Metode selekcije instanci:
   - Edited Nearest Neighbor (ENN)
   - Repeated ENN (RENN)
   - All k-NN
   - Condensed Nearest Neighbor (CNN)
   - DROP3 (rucna implementacija)
   - Tomek Links
5. k-NN klasifikacija nakon selekcije
6. Uporedna evaluacija (tacnost, F1-score, stopa redukcije, vreme predikcije)
7. Confusion matrice i distribucija klasa posle selekcije

## Tehnologije

- **Jezik:** Python (notebook workflow)
- **Osnovne biblioteke:** `pandas`, `numpy`, `scikit-learn`
- **Selekcija instanci:** `imbalanced-learn`, rucna implementacija (DROP3)
- **Vizualizacija:** `matplotlib`, `seaborn`

## Strategija modelovanja

Projekat poredi performanse k-NN klasifikatora kroz razlicite strategije selekcije instanci:

- **Baseline:** k-NN treniran na kompletnom (nemodifikovanom) trening skupu
- **Metode uredjivanja:** ENN, RENN, All k-NN: fokus na uklanjanje suma i poboljsanje tacnosti
- **Metode kondenzacije:** CNN, Tomek Links: fokus na redukciju velicine skupa
- **Hibridna metoda:** DROP3: kombinacija ENN ciscenja i decrementalne kondenzacije
- Zavrsna tabela ukljucuje tacnost, F1-score, stopu redukcije i vreme klasifikacije

## Napomene

- Ocene kvaliteta su grupisane u tri klase (los/srednji/dobar) radi jasnijih granica klasifikacije.
- Svi atributi su standardizovani pre primene metoda zasnovanih na rastojanju.
- DROP3 je implementiran rucno jer ne postoji u standardnim Python bibliotekama.
- Tacne vrednosti metrika zavise od random seed-a i podele pri kros-validaciji.