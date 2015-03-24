## Please edit system and help pages ONLY in the moinmaster wiki! For more
## information, please see MoinMaster:MoinPagesEditorGroup.
##acl MoinPagesEditorGroup:read,write,delete,revert All:read
##master-page:HelpTemplate
##master-date:Unknown-Date
#format wiki
#language en

'''Планировщик Urchin работает, но запланированные задачи не выполняются. Почему?'''


'''Описание проблемы'''

Иногда запланированные задачи не выполняются, даже если Планировщик Urchin (urchind) работает. На это указывают следующие признаки:

  1. В окне "Конфигурация" -> "Планировщик" -> "Планировщик задач" инструмента администрирования Urchin отображаются запланированные задачи, их график обновляется, но сами они не выполняются.
> 2. При нажатии кнопки "Запустить сейчас" на вкладке "Запуск/расписание задач" появляется всплывающее окно с индикатором процесса, в котором указывается "Ошибка (0%)"; при этом задание не выполняется.

'''Причина'''

Обычно такая ошибка возникает, если каталог, из которого был запущен Планировщик Urchin, удалили или установили для него новые разрешения, не позволяющие Urchin получить доступ.

К примеру, обычно при установке и обновлении Urchin инсталлятор распаковывают во временный каталог, который также используется в качестве рабочего каталога Планировщика Urchin во время этих процессов. Удаление этого каталога приведет к нарушению работы планировщика.

'''Решение'''

Чтобы приложения Urchin запускались и работали правильно, запуск Планировщика Urchin должен осуществляться из постоянного каталога, к которому Urchin имеет постоянный доступ. Если при работе планировщика возникают проблемы, перезапустите службы Urchin следующим образом:

'''Системы Windows'''

  1. "Пуск" -> "Все программы" -> Urchin -> "Отключить службы Urchin".
> 2. "Пуск" -> "Все программы" -> Urchin -> "Включить службы Urchin".

'''UNIX-подобные системы'''

  1. Откройте командную оболочку в качестве суперпользователя ("root") или пользователя, от имени которого выполняется Urchin.
> 2. Измените каталог на тот, в котором установлено ПО Urchin (например, с помощью команды "cd /usr/local/urchin").
> 3. Перезапустите службы Urchin с помощью команды "bin/urchinctl restart".