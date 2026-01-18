# **Projekt zaliczeniowy – Zastosowania Uczenia Maszynowego**

## **1. Informacje ogólne**
**Nazwa projektu:**  
wykrywanie pozytywnych i negatywnych opinii na temat produktów 

**Autor:**  
Stanisław Halamski 

**Kierunek, rok i tryb studiów:**  
Informatyka, semestr V  

**Data oddania projektu:**  
18.01.2026  

---

## **2. Opis projektu**
Celem projektu jest automatyczna analiza opinii użytkowników na temat produktów oraz klasyfikacja ich wydźwięku jako pozytywnego lub negatywnego. Projekt wykorzystuje metody przetwarzania języka naturalnego (NLP) oraz różne podejścia uczenia maszynowego – od klasycznych algorytmów, przez sieci neuronowe, aż po nowoczesne modele transformerowe.

Tego typu rozwiązania mogą być wykorzystywane m.in. w systemach rekomendacji, analizie satysfakcji klientów, monitorowaniu opinii w e-commerce oraz wsparciu decyzji biznesowych.  


## **3. Dane**
**Źródło danych:**  
Kaggle 
**Link do danych:**  
https://www.kaggle.com/datasets/bittlingmayer/amazonreviews  

**Opis danych:**  
liczba próbek: ok. 50 000
liczba cech / kolumn: 2–3
format danych: CSV
rodzaj etykiet / klas:
0 – opinia negatywna
1 – opinia pozytywna

licencja: zgodna z licencją Kaggle

Uwagi:
usunięto brakujące wartości
skrócono bardzo długie recenzje
teksty zostały wstępnie oczyszczone z duplikatów 


## **4. Cel projektu**
Celem projektu jest zbudowanie modelu, który:
- automatycznie rozpoznaje wydźwięk opinii o produktach,
- klasyfikuje tekst jako pozytywny lub negatywny,
- umożliwia porównanie skuteczności różnych podejść ML.

Na podstawie wyników możliwe jest określenie, które metody najlepiej radzą sobie z analizą sentymentu w tekstach recenzji.

## **5. Struktura projektu**
Projekt składa się z czterech głównych etapów, każdy w osobnym notatniku `.ipynb`:

| Etap | Nazwa pliku | Opis |
|------|--------------|------|
| 1 | `1_EDA.ipynb` | Analiza danych, wizualizacje, wnioski |
| 2 | `2_Preprocessing_Features.ipynb` | Czyszczenie danych, preprocessing, inżynieria cech |
| 3 | `3_Models_Training.ipynb` | Trening modeli klasycznego ML, sieci neuronowej i transformera |
| 4 | `4_Evaluation.ipynb` | Ewaluacja, porównanie modeli, wizualizacje wyników |

---

## 6. Modele
Projekt obejmuje trzy różne podejścia do modelowania danych:

### 6.1 Model klasyczny ML
- **Algorytm:** Logistic Regression  
- **Krótki opis działania:**  
  Model liniowy, który na podstawie cech TF-IDF (wektorów reprezentujących częstość i ważność słów) uczy się wag dla każdej cechy. Dla nowej recenzji oblicza wartość funkcji logistycznej, która jest interpretowana jako prawdopodobieństwo przynależności do klasy pozytywnej.  
- **Wyniki / metryki:**  
  - Accuracy: **0.565**  
  - Precision: **0.596**  
  - Recall: **0.454**  
  - F1: **0.515**

### 6.2 Sieć neuronowa zbudowana od zera
- **Architektura:**  
  Wielowarstwowa sieć w pełni połączona (Fully Connected / MLP) wykorzystująca jako wejście wektory TF-IDF.  
- **Liczba warstw / neuronów:**  
  - Warstwa wejściowa: rozmiar wektora TF-IDF (20 000 cech)  
  - Warstwa ukryta 1: 256 neuronów  
  - Warstwa ukryta 2: 128 neuronów  
  - Warstwa wyjściowa: 1 neuron  
- **Funkcje aktywacji i optymalizator:**  
  - ReLU (warstwy ukryte)  
  - Sigmoid (warstwa wyjściowa)  
  - Optymalizator: Adam  
  - Funkcja straty: Binary Crossentropy  
- **Wyniki:**  
  - Accuracy: **0.564**  
  - Precision: **0.571**  
  - Recall: **0.580**  
  - F1: **0.575**

### 6.3 Model transformerowy (fine-tuning)
- **Nazwa modelu:** distilbert-base-uncased  
- **Zastosowana biblioteka:** HuggingFace Transformers  
- **Zakres dostosowania:**  
  Fine-tuning całego modelu DistilBERT na zbiorze danych (tokenizacja, dopasowanie wag modelu oraz klasyfikatora) z użyciem metody uczenia nadzorowanego. Trening przeprowadzono na próbce danych (z uwagi na ograniczenia sprzętowe), aby zachować czas wykonania i możliwość uruchomienia w środowisku Colab.  
- **Wyniki:**  
  - Accuracy: **0.886**  
  - Precision: **0.910**  
  - Recall: **0.846**  
  - F1: **0.877**

---

## 7. Ewaluacja
**Użyte metryki:**  
accuracy, precision, recall, F1

**Porównanie modeli:**

| Model | Metryka główna | Wynik | Uwagi |
|--------|----------------|--------|--------|
| Klasyczny ML (Logistic Regression) | F1 | **0.515** | Szybki baseline, ale słabsze uchwycenie kontekstu |
| Sieć neuronowa od zera | F1 | **0.575** | Lepsza niż LR, potrafi wychwycić nieliniowości, ale nadal ograniczona przez TF-IDF |
| Transformer (DistilBERT) | F1 | **0.877** | Najlepszy wynik; model kontekstowy lepiej rozumie sens zdań |

**Wizualizacje:**  
- Macierz pomyłek  
- Krzywa ROC  
- Learning curve  

---

## 8. Wnioski i podsumowanie
- **Najlepszy model:**  
  Najlepszy wynik osiągnął model transformerowy DistilBERT mimo małego sampla do nauki (F1 = **0.877**). Wynika to z jego zdolności do rozumienia kontekstu i zależności w zdaniu, co jest kluczowe w analizie sentymentu.

- **Trudności:**  
  - Duży rozmiar danych i ograniczenia sprzętowe (Colab)  
  - Czas treningu modelu transformerowego  
  - Konieczność redukcji danych w celu skrócenia czasu treningu

- **Co można poprawić:**  
  - zwiększyć rozmiar danych treningowych (jeśli dostępny mocniejszy sprzęt)  
  - zastosować hiperparametryzację (GridSearch / Optuna)  
  - zastosować bardziej zaawansowane modele transformerowe (np. RoBERTa, BERT)  
  - dodać augmentację danych lub balansowanie klas

- **Potencjalne zastosowania:**  
  - analiza opinii klientów w e-commerce  
  - monitoring nastrojów w mediach społecznościowych  
  - automatyczne klasyfikowanie recenzji produktów  


## **9. Struktura repozytorium**
```
projekt_zum_2025/
│
├── data/
│ ├── raw/
│ └── processed/
├── notebooks/
│ ├── 1_EDA.ipynb
│ ├── 2_Preprocessing_Features.ipynb
│ ├── 3_Models_Training.ipynb
│ └── 4_Evaluation.ipynb
├── models/
├── README.md
└── requirements.txt
```
## **10. Technologia i biblioteki**
- Python 3.x  
- NumPy, Pandas, Matplotlib, Plotly, Seaborn  
- scikit-learn  
- TensorFlow lub PyTorch  
- HuggingFace Transformers  

---

## **11. Licencja projektu**
Projekt udostępniony na licencji:  
*(np. MIT License, CC-BY 4.0, GPL-3.0)*  

Źródło danych: zgodnie z licencją wskazaną w sekcji **Dane**.

