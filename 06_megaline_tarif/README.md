# Я.Практикум. Проект №6. Мегалайн. Тариф

***

### Постановка задачи

**Заказчик:** Оператор мобильной связи «Мегалайн».

**Цель:** построить модель для задачи классификации, способную проанализировать поведение клиентов и предложить пользователям новый тариф: «Смарт» или «Ультра». Accuracy модели должно быть не менее 0,75.

**Задачи:** 
1. получить данные и изучить их структуру;
1. разделить данные на обучающую, валидационную и тестовую выборки;
1. подобрать модель с лучшей достоверностью;
1. проверить модель на тестовой выборке;
1. проверить модель на адекватность.

**Исходные данные:** прошедшие предобработку данные о поведении клиентов, которые уже перешли на тарифы «Смарт» и «Ультра». 
Каждый объект — это информация о поведении одного пользователя за месяц. 

### Выводы

В результате выполненной работы получены данные о поведении клиентов тарифов «Смарт» и «Ультра», изучена их структура и проведено разделение на обучающую, валидационную и тестовую выборки.

Лучшее значения показателя достоверности (accuracy) на валидационной выборке составило 81,8% и получено на модели случайного леса.

Проверка указанной модели на тестовой выборке показала увеличение достоверности до уровня 82,2% что объясняется несбалансированностью исходных данных для обучения модели и удовлетворяет предъявленному требованию - 75%. 

Таким образом, полученная модель способна проанализировать поведение клиентов и предложить им новый тариф: «Смарт» или «Ультра».
Эффективность модели заключается в увеличении на 12,9% вероятности успешного предложения тарифа по сравнению со случаем предложения тарифа "Смарт" всем пользователям без исключения.