## Please edit system and help pages ONLY in the moinmaster wiki! For more
## information, please see MoinMaster:MoinPagesEditorGroup.
##acl MoinPagesEditorGroup:read,write,delete,revert All:read
##master-page:HelpTemplate
##master-date:Unknown-Date
#format wiki
#language en
'''Интеграция Urchin с Ad``Words'''

ПО Urchin 6.6 интегрировано с такими функциями Ad```Words, как инструмент подсказки ключевых слов, Редактор Ad```Words и рекомендации по дневным бюджетам кампаний.

Перед использованием этих инструментов необходимо загрузить данные о ценах за клик и аккаунте Ad```Words. Данные о ценах за клик можно загрузить из Ad```Words только вручную: в диалоговом окне настроек источника цен за клик или в планировщике цен за клик.

![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_1.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_1.jpg)

Данные аккаунта Ad```Words, касающиеся текущей структуры аккаунта Ad```Words, автоматически загружаются через равные промежутки времени, указанные в настройке "Данные аккаунта – интервал загрузки" для соответствующего источника цен за клик, или в соответствии с общими настройками в разделе "Обновление источника цен за клик". Чтобы сразу же загрузить данные аккаунта AdWords, установите в разделе "Данные аккаунта – интервал загрузки" значение, равное 5 минутам.

![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_2.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_2.jpg)

Новые режим просмотра "Рекламодатель" и раздел "Оптимизация рекламы" созданы специально для пользователей, которые активно работают с функциями Ad``Words. Режим просмотра "Рекламодатель" и раздел "Оптимизация рекламы" можно включить и выключить на странице "Настройки отчетов".

![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_3.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_3.jpg)

В Urchin 6.6 также можно включить или отключить режим просмотра "Рекламодатель" и раздел "Оптимизация рекламы" для отдельных пользователей и групп. Для этого перейдите в раздел "Профиль" -> "Пользователи". В разделе "Открыть доступ" выберите нужного пользователя и нажмите "Переопределить панель инструментов". В раскрывшемся окне установите переключатель "отключить" в разделе "Использовать значения по умолчанию для профиля".  Установите или снимите флажки рядом с нужными панелями управления и разделами отчетов, а затем нажмите кнопку "Обновить".

![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_4.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_4.jpg)

Чтобы закрыть или открыть доступ к инструментам Ad``Words для определенного пользователя, выберите для него раздел "Настройки пользователя" -> "Свойства".

![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_5.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_5.jpg)

В режиме просмотра "Рекламодатель" доступна панель управления "Сводка маркетинговых данных" и 5 основных отчетов с инструментами и ссылками Ad``Words:

![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_6.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_6.jpg)

В разделе отчетов "Оптимизация для рекламодателей" представлены 3 группы отчетов – "Результаты маркетинговых кампаний", "Маркетинг в поисковых системах" и "Структура цен за клик" и следующие отчеты:

![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_7.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_7.jpg)

Новые функции, связанные с Ad```Words, такие как инструмент подсказки ключевых слов, Диспетчер тегов, экспорт в файл AES для Редактора Ad```Words, находятся в отчетах раздела "Оптимизация рекламы":

![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_8.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_8.jpg)
![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_9.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_9.jpg)

'''Оповещения по бюджетам'''

Оповещение по бюджету – это сообщение с рекомендациями по размеру дневного бюджета из Ad```Words, которое позволяет оценить возможности изменения средств, выделяемых на кампании Ad```Words. При увеличении бюджета до рекомендуемой величины ваши объявления будут показываться чаще и получать больше кликов за месяц.


Чтобы просмотреть рекомендации, наведите курсор мыши на название кампании в разделе "Оповещения Ad``Words". Появится текстовое окно с информацией о выбранной кампании:
![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_10.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_10.jpg)

Чтобы обновить информацию в разделе "Оповещения по бюджетам Ad``Words", нажмите на ссылку "Обновить сейчас".

![http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_11.jpg](http://www.google.com/urchin/images/wiki/Urchin_Integration_AdWords_11.jpg)

Оповещения по бюджетам включены в отчеты "Сводка маркетинговых данных", "Конверсии в кампаниях", "Рентабельность инвестиций в кампании" в режиме просмотра "Рекламодатель" и разделе "Оптимизация рекламы".