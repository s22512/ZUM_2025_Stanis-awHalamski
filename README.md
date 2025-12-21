# **Projekt zaliczeniowy – Zastosowania Uczenia Maszynowego**

## **1. Informacje ogólne**
**Nazwa projektu:**  
wykrywanie pozytywnych i negatywnych opinii na temat produktów 

**Autor:**  
Stanisław Halamski 

**Kierunek, rok i tryb studiów:**  
Informatyka, semestr V  

**Data oddania projektu:**  
22.12.2001  

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

## **6. Modele**
Projekt obejmuje trzy różne podejścia do modelowania danych:

### **6.1 Model klasyczny ML**
- Algorytm:  
- Krótki opis działania:  
- Wyniki / metryki:  

### **6.2 Sieć neuronowa zbudowana od zera**
- Architektura:  
- Liczba warstw / neuronów:  
- Funkcje aktywacji i optymalizator:  
- Wyniki:  

### **6.3 Model transformerowy (fine-tuning)**
- Nazwa modelu:  
- Zastosowana biblioteka (np. HuggingFace Transformers):  
- Zakres dostosowania:  
- Wyniki:  

---

## **7. Ewaluacja**
**Użyte metryki:**  
*(np. accuracy, precision, recall, F1, ROC-AUC, MSE itp.)*  

**Porównanie modeli:**

| Model | Metryka główna | Wynik | Uwagi |
|--------|----------------|--------|--------|
| Klasyczny ML |  |  |  |
| Sieć neuronowa |  |  |  |
| Transformer |  |  |  |

**Wizualizacje:**  
- Macierz pomyłek  
- Krzywa ROC  
- Learning curve  

---

## **8. Wnioski i podsumowanie**
- Który model okazał się najlepszy i dlaczego?  
- Jakie trudności pojawiły się podczas pracy?  
- Co można by poprawić w przyszłości?  
- Jakie potencjalne zastosowania ma ten projekt?  

---

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
├── results/
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

