# A/B-testing: Расчет объемов выборки и оценка результатов

## План A/B теста:
* Планируем эксперимент 
* Собираем и готовим данные  
* Разведочный анализ
* Проверка гипотезы 
* Выводы

### Планируем эксперимент
Здесь мы рассмотрим почти реальную ситуацию, точнее гипотеза была реальная, а данные здесь приближенные к реальным. 
Например, мы хотим увеличить конверсию в подписку предлагая разные условия пробного периода (триала). Вариант А - 30 дней, вариат B - 15 дней. <br />

#### В эксперименте планиурется две фазы:
1. Проверяем значимость различий конверсии в триал для триалов разной продолжительности. <br />
Формулировать нулевую гипотезу H0 и альтернативную H1 для первой фазы <br />

#### Нулевая гипотеза 1: 
*Конверсия в подписку при разных условиях пробного периода НЕ отличаются.* <br />
#### Альтернативная гипотеза 1: 
*Конверсия в подписку при разных условиях пробного периода ЗНАЧИМО отличаются.* <br />

**Пояснение:** 
*в нашем случае, мы хотим, чтобы верной оказалась нулевая гипотеза, ведь если продолжительности триала не влияет на коверсию, значит мы можем поставить меньший триал, а значит пользователи будут быстрее конвертироваться в платящих.* <br />

Если различий нет или вариант с уменьшенным триалом лучше - **внедряем изменения**

2. Проверяем значимость различий конверсии в платящего пользоватлея.  <br />
Формулировать нулевую гипотезу H0 и альтернативную H1 для второй фазы <br />

#### Нулевая гипотеза 2: 
*Конверсия в платного пользователя при разных условиях пробного периода НЕ отличаются.* <br />
#### Альтернативная гипотеза 2: 
*Конверсия в платного пользователя при разных условиях пробного периода ЗНАЧИМО отличаются.* <br />

Если вариант с уменьшенным триалом лучше - **внедряем изменения** <br />
Если разницы нет - смотрим когорты, сравниваем ARPPU и принимаем решение.  <br />
Если вариант с уменьшенным триалом хуже - откатываем изменения, но продолжаем следить за когортой, возможно, на этапе 1-2 месяцев эффект проявится. <br />

**Определяем уровень достоверности.** Пусть будет 95%, это значит, что уровень значимости должен быть 0,05. <br />

Нам понадобится две группы <br />
А - контрольная (trial_30_day) <br />
В - тестовая (trial_15_day) <br />

Принадлежность группе - независимая переменная  <br />
Конверсия - зависимая переменная (то, на что мы хотим влиять) <br />

## Определение размера выборки

От размера выборки зависит надежность и точность расчетов. По идее, чем больше, тем лучше. Но мы всегда находимся в условиях ограничений, в первую очередь временных. Поэтому нам важно определить минимальное количество людей в группе, необходимых для получения надежных результатов. 

Для определения размера выборок используется анализ мощности. <br />

#### Мощность зависит от нескольких факторов: 

* Мощность теста (1 - β) — это вероятность обнаружения статистической разницы между группами, когда разница действительно присутствует. Чаще всего мощность устанавливают равной 0,8.
* Уровень значимости альфа (α) — критическое значение. Чаще всего устанавливают 0,05 или 0,01. В нашем случае будет 0,05
* Ожидаемый эффект - разница между текущим коэффициентом конверсии и тем, которого мы хотели бы получить в результате изменений.

#### То есть нам нужно ответить на два вопроса:
* Какой коэффициент конверсии сейчас
* Какой ожидаемый эффект будет после внесения изменения. 

#### Остальные этапы будут рассмотрены в Jupiter Notebook
