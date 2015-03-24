# Embedded Help and Local Help Center #

<p align='justify'>Beginning with Urchin 7.0, Embedded help (EH) and Urchin Help Center articles (HC) are included in the Urchin package.<br>
<br>
<p align='justify'>EH articles are located in <i>"%URCHIN_HOME%/htdocs/help/eh/VVVV/LANG_CODE"</i> folder, where V is a EH version and LANG_CODE is a language code.<br>HC articles are located in  <i>"URCHIN_HOME/htdocs/help/hc/VVVV/LANG_CODE"</i> folder, where V is a HC version and LANG_CODE is a language code.<br>
<br>
A single instance of EH and HC articles can be used by multiple Urchin instances. In this case, the base URL for the shared EH and HC articles can be defined in urchin.conf file:<br>
<pre><code>helpBaseUrl: /help/ <br>
</code></pre>

Urchin 7.0+ supports automated updates of the EH and HC via the UI or "autoupdate" utility. Finding new versions and checking for updates requires a connection to the Internet. You can find and install new versions of Embedded Help and Urchin Help Center articles by choosing options on the Settings\Global Settings\Autoupdate tab. A new version will be downloaded according to the "Schedule Update" options and a "schedule download now" link will appear at the left of information about the new version.  Use the "Update Settings" options to update EH and HC in silent mode, which permits installation without user intervention.<br>
<br>
<img src='http://urchin-web-analytics-software.googlecode.com/svn/trunk/Autoupdate_Help_Articles.png' />

The Urchin automated updates utility,  invoked from the command line, automatically upgrades the Embedded Help and the Help Center articles to the latest version:<br>
<br><b>"autoupdate -e"</b>
