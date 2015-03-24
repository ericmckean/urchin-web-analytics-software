# Autoupdate: Urchin Automatic Updates Utility #


### Overview ###

The autoupdate utility is used to check, download, and upgrade Urchin components.

Supported operations:
  * automatic upgrades of Urchin components such as the Urchin Product, Embedded Help, Help Center documentation and Geo Databases.
  * rollback of an upgrade process if there are errors.

### Usage ###
The autoupdate utility can be invoked by the Urchin scheduler (urchind) on a scheduled basis or manually via the command line. Autoupdate scheduler settings are available via  Settings -> Global Settings -> Autoupdate in the Urchin Admin Interface.

The default behavior is to check for updates, download and install the new urchin components.  Usage is as follows:<br>
<pre><code>autoupdate [-h] [-v] [-V] [-u] [-r] [-e] [-g] [-H] [-D] [-T] [-f]<br>
</code></pre>

Where:<br>
<pre><code>  -h            Prints help information and exits<br>
  -v            Prints version information and exits<br>
  -V            Prints components version numbers and exits<br>
  -u            Updates entire product to newer version<br>
  -r            Rolls back entire product to previously installed version<br>
  -e            Updates help articles<br>
  -g            Updates GeoDB<br>
  -H            Specifies to log run output to history file <br>
  -D            Enabled debug mode <br>
  -T &lt;task id&gt;  Specifies the task history record to update               <br>
                Specifying -T forces use of -H               <br>
                Specifying -T prohibits use of -u -g <br>
  -f &lt;path&gt;     Specifies locally served update package<br>
                Specifying -f also requires explicit -u -g  <br>
</code></pre>

<h3>Examples</h3>

To upgrade all Urchin components to the latest version:<br>
<pre><code>  autoupdate -u  <br>
</code></pre>

If no updates are available for Urchin components, the message "Urchin is up to date: <i>"LAST_UPDATE_TIME"</i> is displayed.<br>
<br>
To upgrade Urchin Help Articles to the latest version:<br>
<pre><code>  autoupdate -e <br>
</code></pre>
<b>Note:</b> The autoupdate utility needs an internet connection to be able to check for and download new updates. The utility uses port 80 to communicate with the Web server providing the updates. It is possible that you will have problems when going through firewalls and proxy servers when performing updates. Please consult your network administrator if this is the case.