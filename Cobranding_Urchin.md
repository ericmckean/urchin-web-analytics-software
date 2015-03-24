# Cobranding Urchin #


## Overview ##

Urchin accomodates cobranding in the administration interface, the reporting interface, and the login screen. There are three files to edit in order to include HTML at the top of the interface. If a complete portal integration is being done, then the Urchin reporting can be delivered within a frameset or table by your application server.


## Cobranding Instructions ##

To cobrand your interface, you will need to edit the following files located in the Urchin installation:
```
     [urchin install dir]/lib/custom/cobrands/cobrand_admin.tpl.sample
     [urchin install dir]/lib/custom/cobrands/cobrand_report.tpl.sample
     [urchin install dir]/lib/custom/cobrands/cobrand_session.tpl.sample
```
  * Rename files by removing '.sample' (file name must be e.g. cobrand\_admin.tpl)
  * Add HTML content to these files as necessary to include your branding

The first file controls the cobranding on the admin interface and the second controls the cobranding on the reporting interface. The third file controls the cobranding on the login screen. The HTML provided in these files will be placed on top of the Urchin interface.

On the picture below you can see example of cobranded Urchin 7 Login page with corresponding cobrand\_session.tpl

http://urchin-web-analytics-software.googlecode.com/svn/trunk/cobrandin_login_page.PNG


**Note:** If additional changes are required in default Urchin Login page below cobranded area, you need to edit default Urchin session template(`<URCHIN_HOME>/lib/session/templates/template.tpl`)<br>
For example, to change Urchin logotype image:<br>
<ol><li>Put a new image in folder <code>&lt;URCHIN_HOME&gt;/htdocs/uicons/common/</code>
</li><li>Modify the following string in the session template: <code>&lt;td class="logo"&gt;&lt;img src="uicons/common/urchin_logo.jpg"&gt;&lt;/td&gt;</code></li></ol>
