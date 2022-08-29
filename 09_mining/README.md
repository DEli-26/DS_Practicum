# Я.Практикум**. Сборный Проект №2

***

### Постановка задачи

**Заказчик:** ГК "Цифра", разрабатывающая решения для эффективной работы промышленных предприятий.

**Цель:** 
Оптимизировать производство, чтобы не запускать предприятие с убыточными характеристиками.

Для этого требуется подготовить прототип модели машинного обучения, которая должна предсказать коэффициент восстановления золота из золотосодержащей руды (recovery).

**Задачи:** 
1. Загрузить и проанализировать данные;
1. Провести исследовательский анализ данных;
1. Подготовить данные;
1. Построить и обучить модель.

**Исходные данные:** Выгруженные из хранилища компании сырые данные с параметрами добычи и очистки, индексируемые датой и временем получения информации (признак date). 
Соседние по времени параметры часто похожи.
Некоторые параметры недоступны, потому что замеряются и/или рассчитываются значительно позже. 
Из-за этого в тестовой выборке отсутствуют некоторые признаки, которые могут быть в обучающей. Также в тестовом наборе нет целевых признаков.
Исходный датасет содержит обучающую и тестовую выборки со всеми признаками.

Коэффициент восстановления золота рассчитывается по формуле: 

<tex>$$Recovery=\frac{C \cdot (F - T)}{F \cdot (C - T)},$$</tex>

где:
*C* — доля золота в концентрате после флотации/очистки;  
*F* — доля золота в сырье/концентрате до флотации/очистки;  
*T* — доля золота в отвальных хвостах после флотации/очистки.  

Модель должна прогнозировать сразу две величины:  
* эффективность обогащения чернового концентрата rougher.output.recovery;  
* эффективность обогащения финального концентрата final.output.recovery.  

В качестве метрики качества обоих величин следует использовать SMAPE, а для итоговой метрики - их сумму с коэффициентами:

<tex>$$sMAPE_{total}= 0,25 \cdot sMAPE_{rougher} + 0,75 \cdot sMAPE_{final}$$</tex>

### Выводы
Проведено моделирование для предсказания коэффициента восстановления золота из золотосодержащей руды.

Разработана опорная модель (baseline), предсказывающая среднее значение целевых признаков обучающей выборки.  

Проанализированы три типа моделей: линейная регрессия, дерево решений и случайный лес.
При помощи метода кроссвалидации показано, что модель дерева решений неприменима к настоящей задаче.
Анализ оставшихся моделей на обоих этапах - флотации и очистки, показал преимущество модели линейной регрессии.
Это объясняется тем, что многие признаки имеют высокую корреляцию между собой и использование их полного переченя нецелесообразно.
Так, для этапа флотации лучшее качество показывает модель только с двумя признаками - 'rougher.input.feed_ag' и 'rougher.input.feed_rate'.
Столь малое количество существенно ограничивает перечень типов моделей машинного обучения, возможных для обучения, и делает модель линейной регрессии оптимальной для использования.  
На этапе очистки лучшие метрики модели достигаются при использовании десяти признаков, включая целевой признак модели этапа флотации.

Результаты моделирования сведены в таблицу, из которой следует, что обученная модель позволяет предсказывать итоговую метрику на 0,7% лучше относительно опорной модели.

| Параметр | sMAPE(rougher.output.recovery) | sMAPE(final.output.recovery) | sMAPE(total) |
|-|-|-|-|
| Baseline | 5,2% | 8,3% | 7,6% |
| Линейная регрессия | 4,2% | 7,7% | 6,9% |

Учитывая относительно небольшое различие метрик моделей линейной регрессии и опорной, рекомендуется провести поиск в научной литературе аналитических зависимостей целевых признаков с признаками, оказывающими наибольший вклад в качество моделей.
Использование таковых позволит существенно повысить качество моделей. 

Тем не менее, разработанная модель машинного обучения позволяет решить поставленную задачу и предсказывает коэффициент восстановления золота из золотосодержащей руды.  
Для дальнейшей оптимизации производства целесообразно определить цену одного процента по рассматриваемой метрике.