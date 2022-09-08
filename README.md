# CupIT2022—DS—One-Zero

| Название файла/директории | Содержание файла |
|----:|:----------|
| CupIT2022—DS—One-Zero-code.ipynb | Ноутбук формата .ipynb с актуальной look-alike моделью на основе анализа данных о клиентах магазинов "Перекрёсток"|
| CupIT2022—DS—One-Zero-presentation.pdf | Файл с презентацией решения кейса в расширении .pdf. Содержит механики взаимодействия с выделенной аудиторией и визуализацию решения кейса|
| CupIT2022—DS—One-Zero-output_data.csv  | Файл .csv, содержащий извлеченные таблицы из исходного файла|
|CupIT2022-DS-One-Zero-learning_model-LGBMClassifier.pickle| Файл .pickle, содержащий обученную модель
## Описание 

Решение кейса состоит из анализа накопленных компанией данных. Данные представляют помесячно агрегированные сведения о покупках участников программы лояльности перекрёстка с флагом участия в клубе в .csv формате.     
* client_id - уникальный идентификатор клиента, число от 0 до X    
* rto_n - сумма товарооборота клиента в месяц    
* rto_n_category - сумма товарооборота клиента в месяц в определенной категории    
* rto_std_n - стандартное отклонение суммы товарооборота от чека к чеку в месяц    
* rto_std_n_category - стандартное отклонение суммы товарооборота от чека к чеку в месяц в определенной категории
* cnt_checks_n - количество уникальных чеков клиента в месяц    
* cnt_checks_n_category - Количество уникальных чеков клиента в месяц в определенной категории    
* is_in_club - флаг участия в клубе
#n - месяц
Происходит построение  look-alike-модели на основе классификации этих данных для поиска клиентов, максимально похожих на людей, недавно присоединившихся к «Клубу полезных привычек» магазинов «Перекрёсток». Это поможет компании выработать механики взаимодействия с покупателями.    
Обученная модель представляет собой файл типа .pickle, который можно интегрировать в любую среду разработки Python. Входные данные требуют предобработки:    
- Замены всех NaN на 0, поскольку это означает, что не было покупок в этой категории/месяце;    
- Исключения дубликатов при их наличии;    
- Обработки признаков, а именно        
1) Выделения новых фич: последовательное применение функции new_feature(data, prefix, start_month=6, finish_month=13), где data : pandas.DataFrame - данные, prefix : string - название столбца без указания месяца и категории товара, start_month : integer - начальный месяц,  start_month : integer - конечный месяц. Возвращает data.fillna(0): pandas.DataFrame - датафрейм с новыми столбцами(те столбцы, которые участвовали в образовании новых, удаляются);    
2)  Поиск сильно коррелирующих признаков: применение функции correlated_features(data, stop=0.75), где data : pandas.DataFrame - данные, stop : float - максимально допустимый коэффициент корреляции. Возвращает correlated_features : set - коллекцию столбцов, чей коэффициент корреляции выше порогового значения stop:    
3)  Удаление одного из пары коррелирующих столбцов: применение функции drop_cor_features(data, correlated_features), где data : pandas.DataFrame - данные, correlated_features : set - коллекция коррелирующих столбцов;

Запуск осуществляется в Jupyter Notebook или Google Collab. 

## Документация

* [Документация по работе с Python](https://www.python.org/)
* [Документация по работе с библиотекой Pandas](https://pandas.pydata.org/pandas-docs/stable/index.html)
* [Документация по работе с gdown](https://pypi.org/project/gdown//)
* [Документация по работе с warnings](https://docs.python.org/3/library/warnings.html)
* [Документация по работе с time](https://docs.python.org/3/library/time.html)
* [Документация по работе с numpy](https://numpy.org/doc/)
* [Документация по работе с seaborn](https://seaborn.pydata.org/)
* [Документация по работе с scipy](https://docs.scipy.org/doc/scipy/)
* [Документация по работе с hypertools](https://hypertools.readthedocs.io/en/latest/)
* [Документация по работе с matplotlib](https://matplotlib.org/)
* [Документация по работе с sklearn](https://scikit-learn.org/stable/)
* [Документация по работе с lightgbm](https://lightgbm.readthedocs.io/en/latest/)
* [Документация по работе с pickle](https://docs.python.org/3/library/pickle.html)


## :shipit: Контакты
| **ФИ** | **Tелефон** | **Email**|
|----:|:----------:|:----|
| Агишев Владимир| 8(905)3960344| agishev1961@gmail.com|
| Исаева Диана| 8(964)0497904| dii.grase@yandex.ru|
| Мичурин Артём| 8(916)3176642| amichurin0@gmail.ru|
| Попова Нина| 8(989)2666821| popovaninam@yandex.ru|

