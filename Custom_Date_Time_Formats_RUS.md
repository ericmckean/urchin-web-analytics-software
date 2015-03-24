## Please edit system and help pages ONLY in the moinmaster wiki! For more
## information, please see MoinMaster:MoinPagesEditorGroup.
##acl MoinPagesEditorGroup:read,write,delete,revert All:read
##master-page:HelpTemplate
##master-date:Unknown-Date
#format wiki
#language en


Автор статьи: [""Friedrich Software Resources""], авторизованный консультант по ПО Urchin.

'''Пользовательские форматы даты/времени'''


Введение

Urchin обрабатывает практически любые форматы даты/времени, содержащиеся в файле журнала. Для этого необходимо лишь предоставить Urchin тот же формат даты или времени, который используется в файле журнала. В этой статье описываются переменные, с помощью которых задается формат даты или времени. Эти форматы указываются в файле пользовательских форматов журнала. Дополнительную информацию см. в статье "Пользовательские форматы журнала" выше.

Принципы синтаксического анализа даты/времени

Urchin определяет дату/время, сопоставляя указанный формат с полями даты/времени в файле журнала.

Например, в журнале IIS дата приводится в следующем виде:
2002-11-12
Urchin может определить год, месяц и день по следующему формату:
%Г-%м-%д.

Создание формата даты/времени

Чтобы создать пользовательский формат даты/времени, прежде всего посмотрите, как оформлены эти данные в файле журнала. Затем выберите следующие переменные даты/времени из перечисленных ниже, чтобы создать формат. Часовые пояса вокруг земного шара выражаются как положительное или отрицательное смещение от UTC (всемирного координированного времени).

Например, если в файле журнала время указано как "07:01:47", вам нужно будет создать формат по этому образцу. Прежде всего следует учесть, что время указывается в следующем виде: часы:минуты:секунды. Просмотрев приведенный ниже список, вы заметите, что для часов используется переменная %H, для минут – %M, а для секунд – %S. Сложив все вместе, мы получим "%H:%M:%S". Если в поле формата даты или времени имеется буквенный символ %, можно указать его как %%.

Чаще всего используются следующие переменные: %Y, %m, %d, %H, %M и %S.

Определения переменных даты/времени

  * %A = полное название дня недели, принятое в данной стране.
  * %a = сокращенное обозначение дня недели, принятое в данной стране.
  * %B = полное название месяца, принятое в данной стране.
  * %b = сокращенное обозначение месяца, принятое в данной стране.
  * %d = день месяца в виде десятичного числа (01-31).
  * %e = день месяца в виде десятичного числа (1-31); перед однозначными числами ставится пробел.
  * %H = час (в 24-часовом исчислении) в виде десятичного числа (00-23).
  * %I = час (в 12-часовом исчислении) в виде десятичного числа (01-12).
  * %j = день года в виде десятичного числа (001-366).
  * %k = час (в 24-часовом исчислении) в виде десятичного числа (0-23); перед однозначными числами ставится пробел.
  * %l = час (в 12-часовом исчислении) в виде десятичного числа (1-12); перед однозначными числами ставится пробел.
  * %M = минута в виде десятичного числа (00-59).
  * %m = месяц в виде десятичного числа (01-12).
  * %p = обозначение времени "до полудня" или "после полудня", принятое в данной стране.
  * %S = секунда в виде десятичного числа (00-60).
  * %s = количество секунд с начала отсчета, UTC (см. mktime(3)).
  * %w = день недели (неделя начинается в воскресенье) в виде десятичного числа (0-6).
  * %Y = год с указанием века в виде десятичного числа.
  * %y = год без указания века в виде десятичного числа (00-99).
  * %z = смещение часового пояса относительно UTC; знак плюса в начале обозначает нахождение к востоку от UTC, минуса – к западу от UTC, затем указываются часы и минуты без каких-либо знаков-разделителей между ними (обычная форма для заголовков времени RFC 822).
  * %% = `%'.