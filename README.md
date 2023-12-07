## Исследование оттока клиентов банка 
### (поиск инсайтов, составление рекомендаций стейкхолдерам, построение дашборда)

---

#### Цель проекта: 
Создать отчет в виде дашборда, который отражает зависимость клиентов, склонных к уходу из клиентов банка от различных факторов.

---

#### Задачи:
1.	Выделить сегменты клиентов, склонных к оттоку.
2.	Подтвердить или опровергнуть ряд гипотез о зависимости клиентов к оттоку от различных факторов.

---

Ссылка на данные: [Churn for Bank Customers](https://www.kaggle.com/datasets/mathchi/churn-for-bank-customers)

---
#### Требования:
Дашборд должен отражать зависимость процентного соотношения числа ушедших клиентов от общего числа клиентов от различных факторов (пол, возраст, география, наличие кредитной карты, кредитный рейтинг, баланс, доход, активность, стаж клиента).

Для исследования были выдвинуты следующие гипотезы:

1.	Клиент с низким кредитным рейтингом с большей вероятностью покинет банк.
2.	Пожилые (клиенты старших возрастных групп) реже покидают банк, чем молодые.
3.	Пол клиентов не оказывает значительного влияния на склонность покидать банк.
4.	География клиентов оказывает влияние на склонность покидать банк.
5.	Чем больше стаж клиента (время, в течение которого он является клиентом банка), тем реже он покидает банк.
6.	Чем больше остаток на счете клиента, тем меньше вероятность, что он покинет банк.
7.	Чем больше у клиента продуктов банка, тем меньше вероятность, что он покинет банк.
8.	Клиенты, которые используются кредитную карту банка, менее склонны покидать банк.
9.	Активные клиенты банка реже покидают банк.
10.	Клиенты с более низким доходом чаще покидают банк.

##### Техника: 
дашборд, выполненный в **MS Power BI**
##### Требования к исходным данным: 
- корректное указание типов данных;    
- отсутствие ошибок в данных.
---
#### Описание проекта:
Исходные данные представляли собой табличные данные, содержащие информацию по каждому клиенту банка.    
Типы данных были приведены к нужным, откорректированы знаки, произведена замена значений категориальных переменных с числовых на текстовые.    
 1. Построена система **метрик**    
* Количество клиентов – посчитано количество уникальных CustomerID в исходной таблице    
* Количество ушедших клиентов – посчитано количество клиентов в контексте поля Exited    
* Процент оттока клиентов – посчитан как частное от деления количества ушедших клиентов на общее количество клиентов.    

2. Разработана **модель** данных    
Модель данных включает 2 таблицы: исходную таблицу и таблицу мер.    

3. В Power Query созданы **дополнительные столбцы**    
* Пользовательский столбец для разбивки по возрастным группам:    
4 возрастные группы определены по ключевым задачам, стоящим перед группой:    
  18-25 – студенты, начинающие специалисты;    
  26-39 – молодые семьи;    
  40-59 – люди с большей финансовой свободой;    
  старше 60 - пенсионеры и предпенсионеры      
* Условный столбец для разбивки по размеру баланса на 4 группы:    
  1) от 0 до 50 тыс,    
  2) от 50 до 100 тыс,    
  3) от 100 до 200 тыс,    
  4) больше 200 тыс.

4. Построен дашборд из 18 визуальных элементов, каждая визуализация выбрана с учетом более наглядной демонстрации конкретного фактора (карточки, датчик, графики, круговая диаграмма, гистограммы)
   
![Вид дашборда](https://github.com/Vitochkasonik/Churn_research/blob/master/Screen%20Dash_1.jpg)


Также реализована подсказка на отдельной странице, высплывающая при наведении курсора на график - для более удобного просмотра

![Подсказка](https://github.com/Vitochkasonik/Churn_research/blob/master/Podskazka.jpg)


5. Проведена проверка гипотез    
Гипотезы проверяются путем сравнения значений метрик при установке необходимых **фильтров** в дашборде,    
фильтры выведены в виде срезов на дашборд.

---
#### Выводы:
Из 10 тысяч клиентов банка ушли 2 тысячи клиентов, **процентный отток составил 20%**     
Предлагаю исходить из этой цифры как ориентира, который может показать, насколько больше/меньше отток клиентов по определенному фактору.

**Подтвержденные гипотезы:**    
1.	Клиент с низким **кредитным рейтингом** с большей вероятностью покинет банк.    
   Да, это так, но эта вероятность работает для клиентов с самым низким кредитным рейтингом – от 350 до 500.        
  	После 500 рост кредитного рейтинга не оказывает значительного влияния на уход клиентов.
  	
2.	**География** клиентов оказывает влияние на склонность покидать банк.    
   Действительно клиенты из Германии чаще покидают банк (32%), чем клиенты Франции (16%) и Испании (17%).
  	
3.	**Активные** клиенты банка реже покидают банк.    
   Да, действительно, отток активных клиентов составляет 14%, в то время как неактивных – 27%.

**Неподтверждённые гипотезы:**
1.	**Пожилые (клиенты старших возрастных групп)** реже покидают банк, чем молодые.    
   Строго наоборот.
  	Наибольший отток клиентов характерен для возрастной группы 40-59 лет – 37%
  	
2.	**Пол** клиентов не оказывает значительного влияния на склонность покидать банк.      
Женщины (25%) покидают банк чаще, чем мужчины (16%).
Причём во всех возрастных категориях и географических регионах, при любых фильтрах.

3.	Чем больше **стаж** клиента (время, в течение которого он является клиентом банка), тем реже он покидает банк. 
   Не выявлено такой зависимости. Процент оттока клиентов изменяется от 17 до 23, что в среднем составляет 20%.
  	Можно обратить внимание, что клиенты со стажем до 1 года покидают банк чаще (23%). А клиенты со стажем 3, 7 и 8 лет несколько реже.
  	
4.	Чем больше **остаток** на счете клиента, тем меньше вероятность, что он покинет банк.    
   Напротив, клиента с остатком меньше 50 тыс наименее часто покидают банк (процент оттока 14%), клиенты же с остатком от 100 тыс до 200 тыс и более 200 тыс покидают банк чаще (25% и 56% соответственно).
  	
5.	Чем больше у клиента **продуктов** банка, тем меньше вероятность, что он покинет банк.    
    Наоборот, клиенты с 4 и 3 продуктами покидают банк чаще (100% и 83%).
  	 Меньше всего склонны к оттоку клиенты с 2 продуктами (8%).
  	
6.	Клиенты, которые используются **кредитную карту** банка, менее склонны покидать банк.    
   Не выявлено существенной разницы в оттоке между клиентами с кредитной картой (20%) и без кредитной карты (21%).
  	
7.	Клиенты с более низким **доходом** чаще покидают банк.    
    Не выявлено зависимости оттока клиентов от величины дохода.

   ##### Дополнение:
   Можно составить **портрет клиента, который чаще всего покидает банк**    
  	Это женщина возрастной группы 40-59 лет из Германии с балансом от 100 до 200 тыс, не активная обладательница кредитной карты.    
  	Для этой категории доля оттока 65%, но есть момент, что таких клиентов всего 173 человека.
  	
   В противовес **портрет клиента, который не склонен покидать банк**    
   Это мужчина 18-25 лет из Испании с балансом на счёте от 0 до 50 тыс, не активный.

---
#### Рекомендации:
1.	Добавить данные по LTV (Lifetime Value), узнать сколько прибыли приносит клиент банку, т.к. отток клиентов не равен количеству потерянных денег (упущенной выгоды),
    проанализировать с этой точки зрения, какой бюджет на удержание той или иной категории клиентов стоит тратить.
  	
2.	Добавить данные по временному разрезу, чтобы посчитать коэффициент оттока клиентов и проанализировать, какая динамика оттока клиентов от года к году и внутри года по сезонности,
    соответственно можно будет определить время, когда лучше проводить акции по удержанию клиентов.
  	
3.	Продумать маркетинговые активности для женской клиентуры, клиентов после 40 лет, обладателей баланса от 100 до 200 тыс.    
   
4.	Не перегружать клиентов банковскими продуктами, 2 банковских продукта – оптимально.
   
5.	Стимулировать у клиентов активность.


