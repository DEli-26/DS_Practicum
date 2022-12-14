# Я.Практикум. Проект №11. Определение стоимости автомобилей

***

### Постановка задачи

**Заказчик**  
Сервис по продаже автомобилей с пробегом «Не бит, не крашен».

**Цель**  
Построить модель для определения рыночной стоимости автомобиля, обеспечивающей оптимальное соотношение качества предсказания, его скорости и времени обучения.
Для оценки качества моделей должна использоваться метрика RMSE, ее значение должно быть меньше 2500 евро.

**Задачи**   
1. Загрузить и подготовить данные;
1. Провести exploratory data analys;
1. Обучить модели градиентного бустинга LighGBM и Catboost, для каждой попробовать различные гиперпараметры;
1. Обучить модель линейной регрессии;
1. Проанализировать скорость работы и обучения, а также качество моделей.

**Исходные данные**  
Исторические данные: технические характеристики, комплектации и цены автомобилей.

### Выводы

Построена модель для определения рыночной стоимости автомобиля, обеспечивающей оптимальное соотношение качества предсказания, его скорости и времени обучения.
Для оценки качества моделей использовалана метрика RMSE, пороговое значение которой установлено в 2500 евро.

Результаты анализа на валидационной выборке приведены в таблице. 
Учитывая, что время выполнения операции зависит от параметров аппартной части вычислсительного средства, соответствующие характеристики прведены в относительных единицах, где за единицу принято минимальной значение для всех моделей.

|Характеристика|Требование задания|LightGBM (настройки по умолчанию)|LightGBM (настроенные гиперпараметры)|Catboost|LinearRegression|
|:-:|:-:|:-:|:-:|:-:|:-:|
|Время обучения, о.е.|Минимальное    |1,04    |5,4                                 |28,4     |1|
|Время предсказания, о.е.|Минимальное|4|54|22|1|
|Метрика RMSE, евро|2500             |1761 |1637                                 |1654    |2804|

Из таблицы хорошо видно, что модель LightGBM с настройками по умолчанию обладает наилучшими характеристиками по скорости обучения и предсказания по сравнению с остальными моделями.
Учитывая, что эта модель удовлетворяет требованиям по значению метрики качества, она является оптимальной для решения поставленной задачи.

Проверка модели LIghtGBM на тестовой выборке показала, что качество предсказания снижается менее чем на 1% и составляет 1762 евро.
