# Я.Практикум. Проект №14. Определение возраста покупателей

***

### Постановка задачи

**Заказчик**  
Сетевой супермаркет «Хлеб-Соль»

**Цель**  
Построить модель для использования в системе обработки фотографий покупателей. 
Фотофиксация в прикассовой зоне поможет определять возраст клиентов, чтобы:
* Анализировать покупки и предлагать товары, которые могут заинтересовать покупателей этой возрастной группы;
* Контролировать добросовестность кассиров при продаже алкоголя.  

Качество модели следует оценивать при помощи MAE, значение которого на тестовой выборке должно быть не больше 8.

**Задачи**  

1. Провести исследовательский анализ набора фотографий.
1. Подготовить данные к обучению.
1. Обучить нейронную сеть и рассчитать её качество.

**Исходные данные**  
Набор фотографий людей с указанием возраста, основанный на датасете, представленном в работе:  
**E Agustsson, R Timofte, S Escalera, X Baro, I Guyon, R Rothe** Apparent and real age estimation in still images with deep residual regressors on APPA-REAL database // 12th IEEE International Conference and Workshops on Automatic Face and Gesture Recognition (FG). - 2017. - pp. 87-94.

### Выводы

Проведен исследовательский анализ набора фотографий, в ходе которого определена корректность их разметки.
Распределение возраста в датасете лежит в диапазоне от 1 до 100, что позволяет определить возраст в этом же диапазоне.  

Подготовлены данные и проведено обучение нейронной сети. Ее качество, измеряемое при помощи метрики МАЕ составило 6,3 года, что удовлетворяет заданному критерию.

Разработанная модель пригодна для использования в системе обработки фотографий покупателей. 
Однако, учитывая специфику ее использования (определение возрастной группы для таргетированных предложений и контроль работы кассиров), представляется целесообразным уточнить техническое задание и разработать модель классификации возрастных групп.
Подобные модели обладают более высокой точностью предсказания и могут принести большую пользу бизнесу.
