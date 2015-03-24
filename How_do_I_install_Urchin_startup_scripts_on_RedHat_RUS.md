## Please edit system and help pages ONLY in the moinmaster wiki! For more
## information, please see MoinMaster:MoinPagesEditorGroup.
##acl MoinPagesEditorGroup:read,write,delete,revert All:read
##master-page:HelpTemplate
##master-date:Unknown-Date
#format wiki
#language en
'''Как установить скрипты запуска Urchin на Red``Hat?'''


При установке Urchin создается специальный скрипт запуска. Он называется "urchin\_daemons" и находится в каталоге util программы Urchin. "/path/to/urchin/util/"

Скопируйте этот скрипт в каталог /etc/rc.d/init.d/.
  * cd /path/to/urchin/util
  * cp urchin\_daemons /etc/rc.d/init.d/
  * chmod +x /etc/rc.d/init.d/urchin\_daemons
  * Найдите файл /etc/inittab и определите уровень запуска по умолчанию (обычно это 3). [[См. ниже]]
  * Затем переименуйте его в /etc/rc.d/rcX.d (где X – уровень запуска).
  * cd /etc/rc.d/rc3.d
  * Создайте символьные ссылки, указывающие на /etc/rc.d/init.d/urchin\_daemons, с именами S95urchin и K05urchin.
  * ln -s ../init.d/urchin\_daemons S95urchin
  * ln -s ../init.d/urchin\_daemons K05urchin

[[ Номер уровня запуска по умолчанию. Уровни запуска в системах ReadHat:
  * 0 - остановка (НЕ устанавливайте это значение для initdefault)
  * 1 – режим одного пользователя
  * 2 – многопользовательский режим без использования сетевой файловой службы (то же самое, что и 3, если у вас нет сети)
  * 3 – полнофункциональный многопользовательский режим
  * 4 – не используется
  * 5 - X11
  * 6 - перезапуск (НЕ устанавливайте это значение для initdefault)
id:3:initdefault:
]]