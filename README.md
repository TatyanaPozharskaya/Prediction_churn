#### Задача:

Сеть фитнес-центров разрабатывает стратегию взаимодействия с клиентами на основе аналитических данных, необходимо провести анализ и подготовить план действий по удержанию клиентов: 

- научиться прогнозировать вероятность оттока (на уровне следующего месяца) для каждого клиента;
  
- сформировать типичные портреты клиентов: выделить несколько наиболее ярких групп и охарактеризовать их основные свойства;

- проанализировать основные признаки, наиболее сильно влияющие на отток;

- сформулировать основные выводы и разработать рекомендации по повышению качества работы с клиентами:

  - выделить целевые группы клиентов;
  - предложить меры по снижению оттока;
  - определить другие особенности взаимодействия с клиентами.
  
#### Описание данных: 

Данные клиента за предыдущий до проверки факта оттока месяц:

'gender' — пол;

'Near_Location' — проживание или работа в районе, где находится фитнес-центр;

'Partner' — сотрудник компании-партнёра клуба (сотрудничество с компаниями, чьи сотрудники могут получать скидки на абонемент — в таком случае фитнес-центр хранит информацию о работодателе клиента);

Promo_friends — факт первоначальной записи в рамках акции «приведи друга» (использовал промо-код от знакомого при оплате первого абонемента);

'Phone' — наличие контактного телефона;

'Age' — возраст;

'Lifetime' — время с момента первого обращения в фитнес-центр (в месяцах).

Информация на основе журнала посещений, покупок и информация о текущем статусе абонемента клиента:

'Contract_period' — длительность текущего действующего абонемента (месяц, 6 месяцев, год);

'Month_to_end_contract' — срок до окончания текущего действующего абонемента (в месяцах);

'Group_visits' — факт посещения групповых занятий;

'Avg_class_frequency_total' — средняя частота посещений в неделю за все время с начала действия абонемента;

'Avg_class_frequency_current_month' — средняя частота посещений в неделю за предыдущий месяц;

'Avg_additional_charges_total' — суммарная выручка от других услуг фитнес-центра: кафе, спорттовары, косметический и массажный салон.

'Churn' — факт оттока в текущем месяце.

1. Проведите исследовательский анализ данных (EDA); 
2. Постройте модель прогнозирования оттока клиентов:
   - построить модель бинарной классификации клиентов, где целевой признак — факт оттока клиента в следующем месяце:
   - разбить данные на обучающую и валидационную выборку функцией train_test_split();
   - обучите модель на train-выборке двумя способами: логистической регрессией, случайным лесом;
   - оценить метрики accuracy, precision и recall для обеих моделей на валидационной выборке: сравнить по ним модели, какая модель показала себя лучше на основании метрик?
3. Сделать кластеризацию клиентов:
   - стандартизируйте данные;
   - построить матрицу расстояний функцией linkage() на стандартизованной матрице признаков, нарисовать дендрограмму;
   - обучить модель кластеризации на основании алгоритма K-Means, спрогнозировать кластеры клиентов;
   - определить средние значения признаков для кластеров;
   - построить распределения признаков для кластеров;
   - для каждого полученного кластера посчитать долю оттока.
 4. Сделать базовые рекомендации по работе с клиентами.

#### Выводы:

После проведения анализа и подготовки данных нам удалось разработать алгоритм для предсказывания оттока клиентов на уровне следующего месяца с полнотой 81% (доля оттока, которую удаётся обнаружить). Также можно сказать, что единого признака, влияющего на отток, не обнаружилось. На отток клиентов влияет ряд признаков.

Алгоритм кластеризации помог нам собрать следующие портреты клиентов (номера соответствуют номерам кластеров):

№0 - средний возраст клиента 29 лет, живет/работает близко к клубу, примерно половина пришли по партнерской программе, участвуют в акции "приведи друга", в этот кластер попали клиенты, не указавшие номер телефона, покупают абонемент на 3 и больше месяцев, посещают групповые занятия, пользуются дополнительными услугами клуба, занимаются больше 3 месяцев, посещают клуб примерно 2 раза в неделю, примерно треть из них уйдут в отток(показатель оттока - 0,276);

№1 - возраст клиента 29-30 лет, живет/работает близко к клубу, не участвует ни в одной акции/программе, номер телефона указан, покупают абонемент на 3 месяца, посещают групповые занятия, пользуются допольнительными услугами клуба, в среднем посещают клуб 2-3 раза в неделю, показатель оттока - низкий - всего 0,113;

№2 - возраст 29-30 лет, живет/работает близко к клубу, в этом кластере больше всего клиентов из партнеров клуба, пришли с друз ьями, телефон указан у всех клиентов в этом кластере, выбрали абонемент на 12 месяцев, посещают групповые занятия, пользуются дополнительными услугами клуба чаще других клиентов, в среднем посещают клуб 2 раза в неделю. показатель оттока - на уровне 0,023 - самый низкий по кластерам;

№3 - 27-28 лет, не работают/не живут близко от клуба - самый низкий показатель - 0,719, не участвует ни в одной акции/программе, номер телефона указан, покупают абонемент на 1-3 месяца, не посещают групповые занятия, не пользуются дополнительными услугами клуба или очень редко, посещают примерно 1 раз в 1-2 недели, больше половины из них уйдут в отток - самый высокий показатель - 0,587;

№4 - 29 лет, живет/работает близко к клубу, примерно половина пришла по партнерской программе, все клиенты этого кластера пришли по акции "Приведи друга", номер телефона указан, купили абонемент только на 3 месяца, группы посещают, естественно приносят клубу выручку от дополнительных услуг, ходят примерно 1-2 в неделю, показатель оттока - 0,255 - к сожалению в этом кластере примерно треть отвалится в отток.

Рекомендации по удержанию клиентов:

Самые ненадежные клиенты в кластерах 0, 3 и 4. Их необходимо подтянуть до показателей кластеров 1 и 2. Возможно, самая частая причина оттока клиентов - для тех, кто только начал посещать фитнес-клуб (у них просто нет еще привычки заниматься спортом и скорее всего просто не знают чего хотят и вообще с чего начать) - так называемое "одиночество" в клубе - их никто не ведет, нет наставника, поскольку индивидульные тренировки всегда платные, и таким клиентам кажется зачастую, что это лишняя трата денег, что они сами смогут. По моему мнению, новичкам можно предложить индивидуальные тренировки, составление плана тренировок на первых неделях абонемента, что называется "подсадить" на тренировки, поощрять первые успехи, например, бесплатными напитками в фитнес-баре и тому подобные акции. Также можно предлагать более гибкий график тем, кто далеко работает/живет от клуба.
