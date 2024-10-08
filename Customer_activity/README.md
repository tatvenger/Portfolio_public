# Описание проекта
Интернет-магазин «В один клик» продаёт разные товары: для детей, для дома, мелкую бытовую технику, косметику и даже продукты. Отчёт магазина за прошлый период показал, что активность покупателей начала снижаться. Привлекать новых клиентов уже не так эффективно: о магазине и так знает большая часть целевой аудитории. Возможный выход — удерживать активность постоянных клиентов. Сделать это можно с помощью персонализированных предложений. В особенности тем клиентам, чья активность может снизиться в ближайшее время.

**Цель проекта**
Разработать модель машинного обучения, которая будет предсказывать вероятность снижения активности покупателей и позволит персонализировать предложения постоянным клиентам.

# Общие выводы
Перед нами была поставлена задача разработки решения c применением машинного обучения, которое позволит персонализировать предложения постоянным клиентам интернет-магазина, чтобы увеличить их покупательскую активность. 

Покупательскую активность клиентов магазина принято измерять в категориях "Снизилась" и "Прежний уровень". Предсказание вероятности отнесения клиента к той или иной категории в переводе на язык машинного обучения представляет собой задачу классификации.

В ходе проекта были выполнены предобработка и исследовательский анализ данных. Для подбора лучшей модели классификации был настроен пайплайн, который с помощью автоматизированного подбора гиперпараметров с помощью класса `GridSearchCV`, осуществлял выбор наилучшей из набора моделей на основе результатов метрики ROC_AUC.

Лучшей моделью стала модель логистической регрессии cо значением параметра регуляризации, равным 2 и наилучшим скейлером количественных столбцов MinMaxScaler(). Значение метрики ROC_AUC данной модели на тренировочных данных составило 0.89. 

**Рекомендации**

На базе выбранной модели были выявлены важные признаки для уровня покупательской активности. Например, наиболее значимыми являются число просмотренных страниц за визит,  среднее число просмотренных категорий за визит, время, проведенное на сайте за предыдущий и текущий месяцы, доля акционных покупок и количество неоплаченных товаров в корзине за последний квартал). Интернет-магазину стоит понимать, какие значимые признаки влияют на покупательскую активность, и уметь воздействовать на нее через них.

С помощью выбранной модели были предсказаны вероятности снижения покупательской активности для всех клиентов тестовой выборки. 

На основе прибыли, генерируемой клиентами, и вероятности снижения покупательской активности были выделены следующие сегменты клиентов:
- по уровню прибыли:
   - низкая;
   - средняя;
   - высокая;
- по вероятности снижения покупательской активности:
   - выше 0.7;
   - ниже 0.7.
   
Так как основным сегментом, генерирующим прибыль, является сегмент клиентов со средней прибылью, для решения задачи была выбрана группа клиентов со средней прибылью и вероятностью снижения покупательской активности выше 0.7. Для выбранной группы были подготовлены следующие рекомендации для поддержания/повышения их активности:
- направлять клиентам персонализованные предложения с промокодами на покупки ко дню рождения или другим праздникам либо списки товаров по акции из той категории, которая является у них популярной;
- предлагать клиентам те товары, которые являются сопутствующими тем, что они приобрели в прошлом или положили в корзину при текущей визите;
- ввиду достаточно большого количество неоплаченных товаров в корзине у большей части покупателей рекомендуется разобраться с причинами большого количества неоплат.
