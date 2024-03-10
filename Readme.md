# Анализ успеваемости студентов университета Junyi Academy Online Learning 

**Цель**: проанализировать успеваемость, факторы, влияющие на нее, а также стратегии, которые выбирают студенты при учебе в онлайн Академии Цзюньи.


## О наборе данных
Важность и популярность онлайн-обучения значительно возросли по мере того, как мир вступает в информационную эпоху. Текущая ситуация с COVID-19 показывает, что онлайн-обучение выступает многообещающей средой для справедливого качественного образования, а также важным компонентом системы образования в случае закрытия кампусов.

Фонд Академии Цзюньи, некоммерческая организация, базирующаяся на Тайване, целью которой является предоставление всем детям справедливого и качественного образования с помощью технологий, стремится поддержать  обучающееся сообщество во время этой пандемии. Они публикуют на своей платформе набор данных, состоящий из более чем 16 миллионов задокументированных попыток упражнений от более чем 72 000 студентов в течение года (с 2018/08 по 2019/07). Набор данных возможно поможет исследованиям по созданию более качественного и персонализированного обучения для студентов, а также будет стимулировать более широкое участие междисциплинарных экспертов для внесения вклада в будущее онлайн-обучения.

*Описание данных*
[Ссылка на датасет](https://www.kaggle.com/datasets/junyiacademy/learning-activity-public-dataset-by-junyi-academy?s=) 
Представлены три таблицы в наборе данных:

В файле Log_Problem.csv зарегистрировано 16 217 311 попыток решения задач 72 630 выбранными учащимися за год с 2018/08 по 2019/07 год.

Info_Content.csv описывает метаданные упражнений, каждое упражнение представляет собой базовую единицу обучения, состоящую из множества задач.

Info_UserData.csv описывает метаданные выбранных зарегистрированных студентов в Академии Цзюньи.

### Info_UserData.csv

*Описание таблицы*

Эта таблица содержит метаданные для 72 758 избранных пользователей этого набора данных.

Все выбранные пользователи — студенты, соответствующие следующим критериям фильтрации:

Дата регистрации между 01.08.2018 и 31.07.2019.
Оценка пользователя от 1 до 12.
Город пользователя не равен нулю
Энергетические очки зарабатываются в Академии Цзюньи после выполнения упражнений, просмотра видео и получения значка пользователем.

Что такое энергетические очки?
Энергетические очки подобны очкам опыта в играх.
Как и в случае с игровым обучением, пользователи будут стараться учиться, чтобы заработать больше энергетических очков.
Энергетические очки зарабатываются в Академии Цзюньи после выполнения упражнений, просмотра видео и получения значка пользователем.

Правила энергетической точки следующие:
* Пользователь зарабатывает 750 * (эффективное время просмотра / продолжительность видео) энергетических баллов после просмотра видео.
(Эффективное время просмотра 10-минутного видео на скорости 2X составит всего 5 минут)
* Пользователь зарабатывает базовые 75 очков энергии после выполнения упражнения на уровне 0.
(Подробности системы прокачки будут описаны в разделе «Механизм квалификации» описания Log_Problem)
* Это число может увеличиться максимум до 225 из-за высокой скорости ответа или повторных правильных попыток.
Заработанные баллы уменьшатся до 5 по мере повышения уровня пользователя в этом упражнении, чтобы побудить пользователя практиковать другие упражнения.

У пользователей могут быть учителя, которые могут назначать упражнения ученику и следить за ходом и результатами заданий.
Учащийся также может добавить себя в качестве преподавателя для себя или других учеников.
Занятия – это группа учеников с определённым учителем.

* uuid Уникальный идентификатор этого пользователя
* gender Пол этого пользователя. Существует четыре возможных значения: `male`, `female`, `unspecified` and `null`.
* points Пользователь получит очки энергии от Академии Цзюньи после выполнения упражнений, просмотра видео и получения значка.
* badges_cnt Значки вручаются пользователям, когда пользователь достигает определенных условий.
* first_login_date_TW Первая дата входа в систему после регистрации пользователя в Академии Джуньи.
* user_grade Уровень пользователя. Возможные значения: от 1 до 12 (1-6 начальная школа, 7-9 средняя школа, 10-12 старшая школа).
* user_city Город проживания пользователя.
* has_teacher_cnt Количество учителей этого пользователя в Академии Цзюньи.
* is_self_coach Добавляет ли пользователь себя в качестве собственного учителя?
* has_student_cnt Количество студентов этого пользователя в Академии Цзюньи. Несмотря на то, что ролью этого пользователя является студент, он все равно может добавить другого пользователя в качестве студента.
* belongs_to_class_cnt 
* has_class_cnt

### Info_Content.csv
*Описание таблицы*

Обучение Академии Цзюньи содержит упражнения, видеоролики и экзамены.
Все содержимое этого набора данных относится к типу упражнений.

Упражнение — это базовая единица обучения учащихся определенной концепции.
В одном упражнении содержится несколько задач, каждая из которых связана с определенной концепцией.

В этой таблице записаны метаданные и иерархическая структура каждого упражнения в Академии Цзюньи.
Для каждого контента предусмотрены три уровня сложности, что указывает на сложность изучения концепции.
Этап обучения разделен на три этапа: `Elementary`, `Junior` and `Senior`.

Упражнения в Академии Цзюньи организованы в древовидную структуру.
Текущая версия набора данных имеет четыре уровня иерархии.

* ucid Хешированный уникальный идентификатор контента.
* content_pretty_name Отображаемое название этого контента на китайском языке.
* content_kind Тип этого контента. Текущая версия набора данных включает только Exercise.
* difficulty Сложность этого контента. Существует четыре возможных значения: `Easy`, `Normal`, `Hard` and `Unset`. `Unset` означает, что для этого контента еще не установлен уровень сложности.
* subject Тема этого контента. Текущая версия набора данных включает только математику.
* learning_stage Этап изучения этого контента. Существует три возможных значения:  `Elementary`, `Junior` and `Senior`.
* level1_id Хешированный идентификатор слоя уровня 1 этого контента. Уровни образуют древовидную иерархическую структуру содержания Академии Цзюньи. Текущая версия набора данных имеет четыре уровня иерархии.
* level2_id Хешированный идентификатор уровня 2 этого контента. Уровни образуют древовидную иерархическую структуру содержания Академии Цзюньи. Текущая версия набора данных имеет четыре уровня иерархии.
* level3_id Хешированный идентификатор слоя 3-го уровня этого контента. Уровни образуют древовидную иерархическую структуру содержания Академии Цзюньи. Текущая версия набора данных имеет четыре уровня иерархии.
* level4_id Хешированный идентификатор слоя 4-го уровня этого контента. Уровни образуют древовидную иерархическую структуру содержания Академии Цзюньи. Текущая версия набора данных имеет четыре уровня иерархии.

![](..\images\ic.jpg)

### Log_Problem.csv
*Описание таблицы*

Упражнение — это базовая единица обучения учащихся определенной концепции.
В одном упражнении содержится несколько задач, каждая из которых связана с определенной концепцией.


![](..\images\lp.jpg)

В этой таблице записаны журналы попыток, когда учащиеся пытаются ответить на каждую задачу.

Временная метка попытки округляется до ближайшего 15-минутного интервала, чтобы уменьшить проблемы конфиденциальности.
uuid и ucid можно использовать для объединения других таблиц (Info_UserData, Info_Content).

problem_number  указывает на количество задач, которые пытался решить пользователь, включая эту попытку в этом упражнении.
exercise_problem_repeat_session  указывает, сколько раз пользователь столкнулся с этой проблемой в этом упражнении.

Мы определяем ответ как правильный, если пользователь ответил на правильный ответ с первого раза и не использует никаких подсказок.
Имеются подсказки, которыми учащийся может воспользоваться и которые представляют собой пошаговое руководство для получения правильного ответа.
Каждый раз, когда учащийся использует подсказку, отображается шаг пошагового руководства.

Механизм квалификации
Согласно кривой забывания, предложенной психологом Германом Эббингаузом, выполняя повторение с интервалами в процессе обучения, мы можем улучшить память недавно изученных концепций и знаний.

Для достижения этой цели Академия Цзюньи использовала «Механизм повышения квалификации», чтобы побудить студентов регулярно возвращаться и проверять результаты.
«Механизм квалификации» позволяет учащимся конвертировать кратковременную память в долговременную посредством соответствующего и многократного повторения.

Существует пять возможных уровней: все пользователи начинают с уровня 0 и переходят на уровень 4, который мы считали Proficient  для этого упражнения.

Чтобы достичь уровня 1, пользователю придется правильно ответить на задачи 5 раз из последних 6 попыток решения задач в упражнении.

После достижения уровня 1 пользователю необходимо подождать 6 часов, прежде чем он/она сможет снова попытаться повысить уровень до уровня 2.

После ожидания пользователь ответит на 2 задачи из упражнения. Например, пользователь находится на уровне 2 и имеет возможность ответить на 2 задачи:
* Если оба верны, пользователь повышается до уровня 3.
* Если оба значения неверны, уровень пользователя понижается до 1.
* Если один из них правильный, а другой неправильный, уровень не изменится, и пользователю будет предложено повторить попытку.

Процедура повышения или понижения уровня одинакова для других уровней. Но пользователи не будут понижены до уровня 1 или при достижении пользователем уровня 4 Proficient.

После достижения уровня 2 пользователю необходимо подождать 16 часов, прежде чем он/она сможет снова попытаться повысить уровень до уровня 3.

После достижения уровня 3 пользователю необходимо подождать 40 часов, прежде чем он/она сможет снова попытаться повысить уровень до уровня 4, который является последним уровнем и считается Proficient для этого упражнения.

Столбцы is_downgrade, is_upgrade и level относятся к этому механизму.

* timestamp_TW Временная метка первого действия, ответа на проблему или использования подсказки. Он находится в часовом поясе UTC+8 и округлен до ближайшего 15-минутного интервала для сохранения конфиденциальности.
* uuid Уникальный идентификатор пользователя. Его можно использовать для присоединения к Info_UserData.
* ucid Уникальный идентификатор контента. Его можно использовать для присоединения к Info_Content.
* upid Уникальный идентификатор проблемы.
* problem_number Количество задач, с которыми столкнулся этот пользователь, включая эту задачу, в этом упражнении.
* exercise_problem_repeat_session Сколько раз пользователь сталкивается с этой задачей в этом упражнении
* is_correct Считается ли ответ правильным или нет. Только если учащийся впервые ответил на правильный ответ, он будет  `TRUE`. Если учащийся впервые воспользовался подсказкой или ответил неправильно, то это будет `FALSE`
* total_sec_taken Сколько секунд пользователь потратил на решение  этой проблемы
* total_attempt_cnt Сколько раз пользователь отправлял ответ на эту проблему?
* Used_hint_cnt Сколько подсказок пользователь использовал для решения этой проблемы.
* is_hint_used
* is_downgrade 
* is_upgrade
* level

## Задачи исследования

1. Найти минимальное, максимальное и медианное количество очков пользователей. 
2. Посчитать учеников какой школы user_grade (начальной 1-6, средней 7-9 или старшей 10-12) больше среди пользователей.
3. Посчитать максимальное, минимальное и среднее количество учителей has_teacher_cnt и студентов has_student_cnt, которые имеют пользователи разных уровней школ; количество студентов, которые добавлялись как учителя сами себе и не добавлялись.
4. Среди первых 1000 пользователей с максимальными по рангу очками вывести количество задач, с которыми столкнулся этот пользователь, включая эту задачу, в этом упражнении (problem_number); сколько раз пользователь сталкивается с этой задачей в этом упражнении (exercise_problem_repeat_session); среднее total_sec_taken число секунд, которое пользователь из данной группы потратил на решение  этих задач в разрезе количества задач.
5. Посчитать среднее количество очков points и среднее количество значков badges_cnt в разрезе уровней пользователя level
6. Для каждого уровня пользователей (level от 0 до 4) узнать: что делали пользователи чаще: использовали подсказку или нет; сколько раз минимально и максимально использовали подсказку, если использовали; сколько процентов пользователей каждого уровня ответили правильно и неправильно.

## Этапы исследования

1. Создание новой базы данных
2. Считывание данных в датафрейм
3. Изучение и предобработка данных
4. Запись данных в новые таблицы базы данных
5. Написание запросов и построение графиков для ответа на задачи исследования
6. Описание выводов исследования

## Выводы исследования

1. Минимальное количество очков пользователей равно 1, максимальное 4047528, т.е. очень большой разброс. При этом медиана равна всего лишь 20400.
2. На данной платформе больше всего зарегистрировано пользователей начальной школы, далее по количеству - средней, и меньше всего - старшей.
3. Видно, что если исходить из среднего количества, то: а) в количестве учителей пользователя сильного разброса нет в разрезе уровней школ; б) в количестве студентов довольно большой разброс (пользователи 2 уровня школы имеют в среднем 72 студента, а 10 и 11 - 2 студента). По параметру добавления себя в качестве учителя пользователи всех уровней школ одинаковы - практически все не добавляются в этом качестве. Таким образом все студенты выбирают примерно похожую стратегию в плане выбора количества учителей и недобавления себя в качестве учителя. Но при этом студентов набирают в разном количестве.
4. Проанализировав топ-1000 пользователей (с максимальным количеством очков) видно: а) среднее количество секунд на решение задач в зависимости от количества проблем снижается; б) количество задач, с которыми столкнулся пользователь - примерно в одном диапазоне (от 1 до 20), есть некоторые выбросы; в) количество секунд на решение проблемы тоже примерно в одном диапазоне (от 1 до 30).
5. С ростом уровня пользователя растут среднее количество очков и среднее количество значков.
6. Большая часть пользователей каждого уровня выбирают стратегию не использовать подсказки, а с ростом уровня пользователя доля таких пользователей растет. Также с ростом уровня растет отношение доли ответивших правильно к доле ответивших неправильно, т.е. ответивших правильно в общем количестве пользователей уровня становится больше.