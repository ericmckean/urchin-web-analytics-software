# Automatic Updates #

### Overview ###

Urchin 7.000 (and later) supports automated updates for all Urchin components including the Urchin product, Help Articles and Geo database.

The main reasons for automated updates are:
  * The Adwords Data API receives frequent updates; backwards compatibility is guaranteed only for limited period of time;
  * Urchin Embedded Help and Help Center documentation can now be updated independently from product releases.
  * Patches with critical bug fixes can be rolled out to Urchin users and seamlessly installed.

### How to Use the Automated Updates ###

By default, automated update is switched off. All auto updates settings can be configured on the tab "Global Settings->Auto Updates" and are available for super admin users only.
<br><br>
<img src='http://urchin-web-analytics-software.googlecode.com/svn/trunk/Autoupdate_Help_Articles.png' />
<br><br>
To automatically upgrade the product from the web UI, set the updating interval. The Urchin scheduler checks for updates according to this interval. If updates are available, the user receives alerts in the Admin UI and is able to schedule a download of updates. Once the updates have been downloaded, the UI message is changed to "install now".<br>
<br>
Clicking "install now" causes Urchin to automatically back itself up and upgrade to the latest version. If no updates are available,  the message <font color='blue'> "Urchin is up to date: <i>LAST_UPDATE_TIME</i>"</font> is displayed. If any components require update, the message is changed to <font color='blue'>"Updates available, <u>view now</u>"</font>. "View now" is a link to the Autoupdates Scheduler Configuration tab.<br>

<b>Note:</b> A Super Admin user is allowed to cancel the upgrade process. Upon "cancel", the downloaded packages are removed from the system and Urchin restores to its pre-upgrade state.<br>
<br>
Every auto update activity that has been performed via the Auto Update Scheduler is displayed on the Auto Update History page. A summary of the updates is listed, which provides valuable information on each update. The Status field can be clicked to view the runtime detail for a previously run task.<br>
<br>
<h3>Autoupdate Scheduler Configuration</h3>

The Autoupdate Scheduler Configuration is responsible for the actual scheduling and execution of Urchin component updates. From the Autoupdates Scheduler, you can add upgrade tasks to the list of Urchin events for repeated execution at nearly any interval desired.<br>
<br>
The following upgrade frequencies are available:<br>
<ul><li>never<br>
</li><li>daily<br>
</li><li>monthly</li></ul>

<h3>Unattended upgrade</h3>

Automated updates can be configured in unattended mode for the following Urchin components:<br>
<ul><li>Help Articles<br>
</li><li>GEO database<br>
<font color='red'><b>Note:</b> Items were changed. Need to synchronize with other supported languages. <br /> No translation is required.<br>
</font></li></ul>

<h3>Urchin Auto Update Recovery mode</h3>

In the event of an unhandled error during the upgrade (e.g. power outage), Urchin performs a rollback operation and restores itself to its pre-upgraded state.<br>
<br>
<h3>Downloading Urchin updates via proxy</h3>

The automated update needs an internet connection to check for and download new updates. If your network topology includes a proxy server, you need to enable update downloading via proxy.   To enable it, navigate to the section "HTTP Proxy Settings" on the tab Settings->Global Settings->Auto Updates and provide values for the following settings:<br>
<ul><li>Proxy Server - Server name or IP Address running proxy server<br>
</li><li>Proxy Port - Port number of running proxy server<br>
</li><li>Proxy Username<br>
</li><li>Proxy Password</li></ul>
