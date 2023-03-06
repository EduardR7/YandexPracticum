
# YandexPracticum
Проекты, выполненные на курсе Data Science на Яндекс.Практикум.


# Список проектов:
### 09. [*Технологический процесс*] (https://github.com/EduardR7/YandexPracticum/blob/09_tech_process/09_tech_process_git.ipynb)
**Описание проекта:**
1. Необходимо оптимизировать технологический процесс получения золота из руды.
2. Оптимизация техпроцесса подразумевает оптимизацию recovery: recovery_pred = ((C * (F - T)) / (F * (C - T))) * 100
3. В качестве метрики качества использовать — sMAPE (англ. Symmetric Mean Absolute Percentage Error, «симметричное среднее абсолютное процентное отклонение»).

**Результат:**
1. Путем исследования трех моделей регрессии, удалось выявить наилучшую, с наилучшими показателями sMAPE, этой моделью оказался алгоритм DummyRegressor.
2. Худшие показатели были замечены у модели случайного леса. Вероятно такие результаты связаны с несбалансированностью target.
3. В ходе подсчета итогового sMAPE мы получили результат 8.03%.

**Инструменты и техники:**
Python, matplotlib, sklearn, seaborn

**Статус проекта:**
Закончен


### 10. [*Защита персональных данных клиентов*] (https://github.com/EduardR7/YandexPracticum/blob/toxic_coments/toxic1.ipynb)
**Описание проекта:**
1. Необходимо защитить данные клиентов страховой компании «Хоть потоп». Разработайте такой метод преобразования данных, чтобы по ним было сложно восстановить персональную информацию. Обоснуйте корректность его работы.
2. Нужно защитить данные, чтобы при преобразовании качество моделей машинного обучения не ухудшилось. Подбирать наилучшую модель не требуется.

**Результат:**
1. Для решения задачи сделаны предварительные теоретические выводы. Указано, что при умножении матрицы с признаками на случайную матрицу, качество оценки не должно уменьшиться.
2. Исходный набор разделен на матрицу признаков (X) и вектор таргетов, y.
3. Матрица признаков умножена на обратимую слуайную матрицу (4х4), получена матрица X1.
4. Обе матрицы и таргеты разбиты на наборы train и test. На train обучены две модели линейной регресси. С помощью моделей сделаны два предсказания на тестовых наборах (исходном X_test) и преобразованном (X1_test).
5. Оба набора сгенерировали практически идентичные наборы y_test_pred y1_test_pred. Метрики R2 совпали до 11 знака после запятой.
6. Численный расчет подтверждает теоретические выводы.

**Инструменты и техники:**
Numpay, Pandas, sklearn, seaborn

**Статус проекта:**
Закончен

### 11. [*Проект "Определение стоимости автомобилей"*] (https://github.com/EduardR7/YandexPracticum/blob/main/11_auto_price.ipynb))
**Описание проекта:**
Сервис по продаже автомобилей с пробегом «Не бит, не крашен» разрабатывает приложение, чтобы привлечь новых клиентов. В нём можно будет узнать рыночную стоимость своего автомобиля.
Постройте модель, которая умеет её определять. В вашем распоряжении данные о технических характеристиках, комплектации и ценах других автомобилей.
Критерии, которые важны заказчику: 1. качество предсказания; 2. время обучения модели; 3. время предсказания модели.

**Результат:**
1. Для решения задачи сделана предобработка данных. Произведена очистка, убраны дубликаты и шипы.
2. Подготовлены категориальные данные (OHE преобразование)
3. Произвено разделение на признаки и таргеты, выделены наборы - train
4. Для оценки алгоритом использовано 3 алгоритма - Линейный, CatBoost, LightGBM.
5. Минимальная метрика RMSE (как на валиде, так и на тесте кстати) - достигнута на алгоритме CatBoost
6. Минимальное время обучения модели (для RMSE < 2500) - достигнуто на алгоритме LightGBM
7. Минимальное время расчета валидных и тестовых предсказаний достигнуто на алгоритме CatBoost.
**Инструменты и техники:**
pandas, sklearn, catboost, lightgbm, matplotlib, seaborn

**Статус проекта:**
Закончен


### 12. [*Проект "Прогнозирование заказов такси"*] (https://github.com/EduardR7/YandexPracticum/blob/main/12_taxi.ipynb)
**Описание проекта:**
Компания «Чётенькое такси» собрала исторические данные о заказах такси в аэропортах. Чтобы привлекать больше водителей в период пиковой нагрузки, нужно спрогнозировать количество заказов такси на следующий час. Постройте модель для такого предсказания.
Значение метрики RMSE на тестовой выборке должно быть не больше 48.
Инструкция по выполнению проекта
Загрузите данные и выполните их ресемплирование по одному часу.
Проанализируйте данные.
Обучите разные модели с различными гиперпараметрами. Сделайте тестовую выборку размером 10% от исходных данных.
Проверьте данные на тестовой выборке и сделайте выводы.

**Результат:**
1. Для решения задачи сделана предобработка данных. Проверена монотонность, стационарность ряда. Сделано несколько иллюстративных графиков.
2. Для дальнейшей работы из временного ряда сгенерированы дополнительные признаки - дни недели, часы дня, лаги, скользящие средние. Данные очищены от NaN.
3. Произведено масштабирование признаков.
4. Произвено разделение на фолды/слоты с помощью tscv.split(train). Так как в начальных фолдах тренд не очень выраженный, очевидно, предсказательная способность и вес предсказаний на начальных фолдах (например train fold=0, valid fold=1) будут искажать прогноз. По этой причине принято решение при прогнозировании брать под valid только дальние промежутки, 7 и 8 фолды.
5. Для оценки алгоритом использовано 3 алгоритма - Линейный, CatBoost, LightGBM.
6. После выбора алгоритма, и фолдов train и valid производится выделение train, valid, target, features и производится оптимизация гиперпараметров. Данные по фолдам для каждого алгоритма усредняются.
7. Минимальная метрика RMSE на тесте - достигнута на алгоритме LightGBM. Алгоритм так-же имеет близкое с Linear regression время fit, predict.
8. Тестирование LightGBM показало соответствие требованиям задачи, RMSE менее 48.
9. Рекомендуется в прод LightGBM...

**Инструменты и техники:**
sklearn.model_selection.TimeSeriesSplit, catboost, lightgbm, matplotlib, scipy, seaborn, statsmodels
Выделение тренда и сезонности, проверка стационарности ряда

**Статус проекта:**
Закончен


### 13. [*Проект для «Викишоп», с использованием BERT*] (https://github.com/EduardR7/YandexPracticum/blob/main/13_toxic.ipynb)
**Описание проекта:**
1. Интернет-магазин «Викишоп» запускает новый сервис. Теперь пользователи могут редактировать и дополнять описания товаров, как в вики-сообществах. То есть клиенты предлагают свои правки и комментируют изменения других. Магазину нужен инструмент, который будет искать токсичные комментарии и отправлять их на модерацию.
2. Обучите модель классифицировать комментарии на позитивные и негативные. В вашем распоряжении набор данных с разметкой о токсичности правок.
3. Решить задачу можно как с помощью BERT, так и без этой нейронки. Если хотите попробовать BERT — Выполните проект локально. Упомяните BERT в заголовке проекта в первой ячейке.

**Результат:**
1. Задача оценки токсичных коментариев сделана с использованием предтестированных моделей BERT.
2. Данные предварительно очищены. Выявлен дисбаланс по таргетам.
3. Токенизация, эмбединг и padding выполнены с помощью BERT.
4. Самая длительная процедура - оптимизация векторов признаков, после padding. После оптимизации, получилось всего 6 признаков. 
5. Было выполнено разделение target и признаки, train и test.
6. Затем создается цикл поиска оптимальных гиперпараметров. В каждом цикле производится разделение выборки train на – valid (1/5) и train (4/5) объема. Для Upsampling применяется SMOT. Применение стандартных методик кросс валидации приводит к ошибочному завышению f1 на 12%.
7. Для предсказаний использовалась линейная регрессия. Результат хороший:
- f1 на валидации 85%,
- f1 на test 83%.

**Инструменты и техники:**
Python, лемматизация, предобработка данных,
torch, transformers, tqdm, pandas, numpy, sklearn, imblearn

**Статус проекта:**
Закончен
