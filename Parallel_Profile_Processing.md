# Urchin 7 Parallel Profile Processing #

### Overview ###

Previous versions of Urchin processed profiles in serial manner. For example, if it took 1 minute to process 1 profile, processing 100 profiles would require approximately 100 minutes.

To address this issue, Urchin 7.0 introduces parallel profile processing. Now, several profile processing jobs can be run simultaneously.

This functionality targets middle and high volume enterprise clients:
  * hosting providers
  * clients with huge number of profiles

### Configuration of parallel profile processing ###

By default, a newly installed or upgraded instance of Urchin 7.0 allows only a single profile to be processed at a time. To enable parallel profile processing:
  1. Uncomment the option `MaxConcurrentProfileTasks` in `<`urchin\_home`>`/etc/urchin.conf and set it to necessary value.<br>For example:<br>
<pre><code>MaxConcurrentProfileTasks: 2 <br>
</code></pre>
<ol><li>Restart Urchin services:<br>
<pre><code>urchinctl restart<br>
</code></pre>
<b>Note:</b> Urchin profile is processed exclusively by one instance of the processing engine.</li></ol>

<h3>Restrictions</h3>

The profile processing job is extremely RAM- and IO-hungry. Blindly increasing the parameter <code>MaxConcurrentProfileTasks</code> will most likely exhaust system resources and significantly degrade processing speed.<br>
<br>
You should increase <code>MaxConcurrentProfileTasks</code> only:<br>
<ul><li>if you have enough RAM to fit several jobs in memory<br>
</li><li>when profiles and log sources are physically located <b>on different physical hard disk drives</b> or you have a high-speed hard disk drive<br>
</li><li>if Urchin is used in Data Center mode</li></ul>

Approximate resource consumption:<br>
<table><thead><th>Number of parallel jobs</th><th>RAM, MB</th><th>IO read, MB/s</th><th>IO write, MB/s</th></thead><tbody>
<tr><td>1 </td><td>1000</td><td>10</td><td>5 </td></tr>
<tr><td>2 </td><td>2000</td><td>20</td><td>10</td></tr></tbody></table>
