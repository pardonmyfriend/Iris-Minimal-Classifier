# Iris Minimal Classifier - Minimalny Klasyfikator dla Zbioru Iris

## 📌 Opis projektu
Celem projektu było znalezienie **minimalnego klasyfikatora** dla zbioru danych Iris, który osiąga **skuteczność powyżej 95%**.  
Minimalność rozumiana była w kategoriach:
- **Złożoność czasowa** - szybkość wykonywania predykcji.
- **Złożoność pamięciowa** - niewielkie zużycie zasobów.
- **Złożoność implementacyjna** - łatwość implementacji i utrzymania.

Projekt został wykonany w ramach zajęć akademickich.

---

## 📊 Zbiór danych
- **Nazwa:** Iris  
- **Źródło:** Wbudowany w bibliotekę `scikit-learn` (`sklearn.datasets.load_iris`)  
- **Opis:** Zawiera 150 próbek kwiatów irysa, każda opisana 4 cechami numerycznymi:  
  - Długość działki kielicha (sepal length)  
  - Szerokość działki kielicha (sepal width)  
  - Długość płatka (petal length)  
  - Szerokość płatka (petal width)  
- **Klasy:** Setosa, Versicolor, Virginica

---

## 🛠 Metodyka
1. **EDA**: podstawowe statystyki, rozkłady cech, korelacje; wizualizacje w `seaborn/matplotlib`.
2. **Podziały danych**: wykorzystano kilka wariantów, m.in. `train/test` (np. 70/30) oraz `train/val/test` (60/20/20).
3. **Walidacja krzyżowa**: `StratifiedKFold` (K-fold ze stratami) do oceny zestawów hiperparametrów.
4. **Modele porównywane**: `DecisionTreeClassifier`, `KNeighborsClassifier`, `LogisticRegression`, `SVC`, `RandomForestClassifier`, `GaussianNB`.
5. **Strojenie hiperparametrów**: siatka parametrów (grid) testowana per model; dla wybranych modeli użyto **pipeline’u ze standaryzacją** (`StandardScaler`) – np. dla SVM, KNN, Regresji Logistycznej.
6. **Metryka główna**: **accuracy**; dodatkowo mierzono **czas trenowania i predykcji** z użyciem `perf_counter`, uśredniany po wielu (np. 100) powtórzeniach, aby zmniejszyć szum pomiaru.
7. **Kryterium wyboru**: model spełniający **>95% accuracy** oraz możliwie **najprostszy** (czas, pamięć, implementacja).

---

## ✅ Wyniki
- **Wybrany klasyfikator:** Drzewo decyzyjne
- **Dokładność:** ~97.3% na zbiorze testowym
- **Uzasadnienie wyboru:** Dobry kompromis między dokładnością a prostotą i szybkością działania.

---

## 🚀 Uruchamianie projektu
### 1. Sklonuj repozytorium
```bash
git clone https://github.com/<twoja-nazwa-uzytkownika>/Iris-Minimal-Classifier.git
cd Iris-Minimal-Classifier
```

### 2. Utwórz i aktywuj środowisko wirtualne (opcjonalne, ale zalecane)
```bash
python -m venv .venv
source .venv/bin/activate    # Linux/macOS
.venv\Scripts\activate     # Windows
```

### 3. Zainstaluj wymagane biblioteki
```bash
pip install -r requirements.txt
```

### 4. Uruchom notebook
```bash
jupyter notebook PUM.ipynb
```

---

## 📦 Wymagania
Wszystkie wymagane biblioteki znajdują się w pliku `requirements.txt`.  
Najważniejsze pakiety:
- `scikit-learn`
- `numpy`
- `pandas`
- `matplotlib`
