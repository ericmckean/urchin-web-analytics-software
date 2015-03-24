## Please edit system and help pages ONLY in the moinmaster wiki! For more
## information, please see MoinMaster:MoinPagesEditorGroup.
##acl MoinPagesEditorGroup:read,write,delete,revert All:read
##master-page:HelpTemplate
##master-date:Unknown-Date
#format wiki
#language en
'''Как скрыть переменные отслеживания кампании UTM в ссылках?'''


Urchin позволяет помечать ссылки тегами с использованием мастер-кодов отслеживания (известных как utm\_id) вместо того, чтобы включать список отдельных переменных. Вам нужно просто использовать utm\_id в своих ссылках и определить значение каждого мастер-кода utm\_id в таблице. Например, вместо
```
    http://www.example.com/?utm_source=overture&utm_medium=cpc&utm_campaign=springpromo
```
можно использовать мастер-код utm\_id:
```
    http://www.example.com/?utm_id=2
```
Использование utm\_id позволяет скрыть переменные отслеживания кампании от веб-серферов и сделать процесс пометки тегами менее подверженным ошибкам, так как значения переменных отслеживания указаны в таблице, где очень легко вносить изменения и исправления.

Для использования мастер-кодов отслеживания необходимо:

  1. Определить коды в таблице.
> 2. Разместить мастер-коды отслеживания в своих ссылках.

Подробнее читайте в статье ["Использование мастер-кодов отслеживания"].