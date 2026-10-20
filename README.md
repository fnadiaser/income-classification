# Классификация уровня дохода (Adult Income)

Курсовая работа: по демографическим данным предсказать, зарабатывает ли человек больше $50K в год.

## Данные
Датасет [Adult (UCI)](https://archive.ics.uci.edu/dataset/2/adult): 32 561 строка, 14 признаков (возраст, образование, профессия, семейное положение, часы работы и др.), целевая переменная `>50K / <=50K`.

## Что сделано
1. **Подготовка данных:** удалён неинформативный признак `fnlwgt`, пропуски в `workclass`, `occupation`, `native-country` (2-6%) заполнены модой, проверены дубликаты и выбросы, сделан отчёт ydata-profiling.
2. **EDA:** доход выше 50K чаще у людей с более высоким образованием и возрастом, заметен разрыв между мужчинами и женщинами; классы несбалансированы.
3. **Моделирование:** LabelEncoder, StandardScaler, разбиение 75/25, сравнение KNN, Decision Tree, Random Forest и логистической регрессии.

## Результаты

| Модель | Accuracy |
|---|---|
| **Random Forest** | **0,847** |
| Decision Tree | 0,828 |
| Logistic Regression | 0,820 |
| KNN | 0,816 |

Random Forest ошибается реже остальных, но пропускает часть класса `>50K` (471 из 866). Для несбалансированных классов в следующей итерации стоит смотреть precision/recall и F1 и подбирать порог.

## Инструменты
Python · pandas · NumPy · scikit-learn · Seaborn · Matplotlib · Plotly · ydata-profiling

## Как запустить
```bash
pip install pandas numpy scikit-learn seaborn matplotlib plotly ydata-profiling
jupyter notebook income_classification.ipynb
```
Файл `adult.csv` положить рядом с ноутбуком.
