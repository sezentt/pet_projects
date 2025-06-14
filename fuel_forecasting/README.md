# Прогнозирование свойств дизельного топлива

Данный проект посвящён задаче регрессии, направленной на прогнозирование физико-химических свойств дизельного топлива по его спектральным характеристикам, полученным методом ближней инфракрасной спектроскопии (NIR).

## Описание задачи

Цель – построение моделей, способных точно предсказывать свойства топлива (такие как температура вспышки, вязкость и т.д.) по данным спектроскопии. Исходные данные представлены двумя наборами:

### 1. Датасет со свойствами топлива (`data_prop`)

* Каждая строка соответствует одному образцу дизельного топлива.
* **Признаки:**

  * `id` – идентификатор образца
  * `BP50`, `CN`, `D4052`, `FLASH`, `FREEZE`, `TOTAL`, `VISC` – физико-химические свойства топлива (целевые переменные)
* **Размерность:** 784 × 8
* **Особенности:** большинство целевых переменных содержат пропуски (до 50%)

### 2. Датасет со спектральными характеристиками (`data_spec`)

* Каждая строка соответствует тому же образцу, что и в `data_prop`.
* **Признаки:**

  * `id` – идентификатор образца
  * 401 числовой признак – значения спектра в диапазоне 750–1550 нм с шагом 2 нм
* **Размерность:** 784 × 402
* **Особенности:** высокая размерность и потенциальная коррелированность признаков

## Целевая переменная

Необходимо спрогнозировать значения семи свойств топлива (`BP50`, `CN`, `D4052`, `FLASH`, `FREEZE`, `TOTAL`, `VISC`) на основе спектроскопических данных.

## Реализованные этапы

* Предобработка данных:

  * Обработка пропущенных значений
  * Масштабирование и снижение размерности с помощью PCA
  * Объединение датасетов по идентификатору
* Моделирование:

  * Линейная регрессия
  * CatBoost Regressor
  * Support Vector Regressor (SVR)
* Оценка качества:

  * Используются метрики регрессии (MAE, RMSE, R²)

## Используемые библиотеки
 *pandas*, *numpy*<br>*matplotlib*, *seaborn*<br>*missingno*<br>*PCA*, *GridSearchCV*<br>*Ridge*, *SVR*<br>*CatBoostRegressor*
