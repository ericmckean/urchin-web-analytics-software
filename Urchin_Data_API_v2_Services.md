# Urchin Data API v2 Services #

### Overview ###

The Urchin Data API v1 provides entry level data mining capabilities - aggregates, custom tables, totals, visitor and transaction details. Along with sorting and pagination, it introduces basic regular expression and numeric filters.

The Urchin Data API v2 significantly extends the analysis machinery introducing visit, path and transaction segmentations. It now becomes possible to specify up to 50 filters of each type per single query and squeeze the most valuable data out of the reporting database.

### Introduction to the Urchin Data API v2 Web Services ###

Urchin 7.0 is bundled with v1 and v2 instances of the Data API. V2 is the default, although the API can be easily switched back to v1 by setting DataApiVersion to 1 in `<`urchin\_home`>`/etc/urchin.conf.

WSDL location:
```
AdminService:  http://your_host:your_port/services/v2/adminservice?wsdl
ReportService: http://your_host:your_port/services/v2/reportservice?wsdl   
```
REST methods URIs:
```
AdminService: http://your_host:your_port/services/v2/adminservice
ReportService:http://your_host:your_port/services/v2/reportservice
```
REST services explorer is also available at <font color='blue'><a href='http://your_host:your_port/uapi.html'>http://your_host:your_port/uapi.html</a></font>

The Report Service allows to extract the following information:
  * Aggregate dimensions and metrics - tables from #1 to #43
  * Custom tables - user defined tables from `<`urchin\_home`>`/lib/custom folder
  * Visit related dimensions and metrics - table #256
  * Transaction related dimensions and metrics - table #257
  * Page related dimensions and metrics - table #259
  * Totals and metrics over time - table #258

### Data API v2 Reference ###

#### Admin service (v2) ####

The Admin service provides operations for retrieving account and profile information.<br><br>
WSDL location: <font color='blue'><a href='http://your_host:your_port/services/v2/adminservice?wsdl'>http://your_host:your_port/services/v2/adminservice?wsdl</a></font>
<br><br>
This service provides the following methods:<br>
<ul><li><b>getAccountList</b> - Method was not changed and works as described in the v1 version. To see more information please refer to the article [<a href='https://secure.urchin.com/helpwiki/en/Data_API'>| Data API</a>].<br>
</li><li><b>getProfileList</b> - Method was not changed and works as described in the v1 version. To see more information please refer to the article [<a href='https://secure.urchin.com/helpwiki/en/Data_API'>| Data API</a>].</li></ul>

<h4>Report service (v2)</h4>

The Report Service lets you extract data and generate reports from Urchin.<br><br>
WSDL location: <font color='blue'><a href='http://your_host:your_port/services/v2/reportservice?wsdl'>http://your_host:your_port/services/v2/reportservice?wsdl</a></font>

This service provides the following methods:<br>
<ul><li><b>getTableList</b> - Method was extended with new fields "nregexfilters" and "nnumericfilters".</li></ul>

<blockquote>Sample response:<br>
<pre><code>&lt;tns:getTableListResponse xmlns:tns="https://urchin.com/api/urchin/v2/"&gt;<br>
&lt;table&gt;<br>
&lt;tableId&gt;257&lt;/tableId&gt;<br>
&lt;dimensions&gt;<br>
  &lt;dimension&gt;u:transaction_id&lt;/dimension&gt;<br>
  ...<br>
&lt;/dimensions&gt;<br>
&lt;metrics&gt;<br>
  &lt;metric&gt;u:transactions&lt;/metric&gt;<br>
  ...<br>
&lt;/metrics&gt;<br>
&lt;nregexfilters&gt;50&lt;/nregexfilters&gt;<br>
&lt;nnumericfilters&gt;50&lt;/nnumericfilters&gt;<br>
&lt;/table&gt;<br>
&lt;/tns:getTableListResponse&gt;<br>
</code></pre>
</blockquote><blockquote>This response shows that Urchin table #257 can be filtered by 50 numeric and 50 regular expression filters. For more information, please refer to the help article <a href='https://secure.urchin.com/helpwiki/en/Data_API'>Data API</a>.<br>
</blockquote><ul><li><b>getData</b> - Beginning with v2, the method fully supports regular expression and numeric filters.  For more information, please refer to the help article <a href='https://secure.urchin.com/helpwiki/en/Data_API'>Data API</a>.</li></ul>

<h5>Filtering gears</h5>
<ul><li><b>tables ##1-43</b> - tables contain aggregated dimensions and metrics, support filtering by dimensions and metrics from the queried table only<br>
</li><li><b>table #256</b> - the table contains all visit details, supports filtering by visit, transaction and path dimensions from tables #256, #257, #258; visit metrics from table #256<br>
</li><li><b>table #257</b> - the table contains all transaction and visit details, supports filtering by visit, transaction and path dimensions from #256, #257, #258; transaction metrics from table #257<br>
</li><li><b>table #258</b> - the table contains total data and metrics over time, supports filtering by metrics from table #258 only<br>
</li><li><b>table #259</b> - the table contains all page and visit details, supports filtering by visit, transaction and path dimensions from #256, #257, #258; page metrics from table #259</li></ul>


<b>Note</b>: In order to see all available dimensions and metrics of these tables, please retrieve information via the method "getTableList" of the Report Service or refer to services explorer at <font color='blue'><a href='http://your_host:your_port/uapi.html'>http://your_host:your_port/uapi.html</a></font>.<br>
<br>
<br>
For example: extract visit details using REST request.<br>
<blockquote>Sample REST request:<br>
<pre><code>http://&lt;urchin host&gt;:&lt;port&gt;/services/v2/reportservice/data?login=admin&amp;password=urchin&amp;ids=7&amp;start-date=2008-01-01&amp;end-date=2010-01-01<br>
&amp;dimensions=u:session_id,u:visitor_id,u:session_ip,u:session_start_time,u:session_end_time&amp;metrics=u:pages,u:visits&amp;table=256<br>
</code></pre>
Sample REST response:<br>
<pre><code>&lt;tns:getDataResponse xmlns:tns="https://urchin.com/api/urchin/v2/"&gt;<br>
&lt;record&gt;<br>
  &lt;recordId&gt;1&lt;/recordId&gt; <br>
&lt;dimensions&gt;<br>
  &lt;dimension name="u:session_id"&gt;1262784738&lt;/dimension&gt; <br>
  &lt;dimension name="u:visitor_id"&gt;HWH2-C43FX-GSPE&lt;/dimension&gt; <br>
  &lt;dimension name="u:session_ip"&gt;10.6.28.81&lt;/dimension&gt; <br>
  &lt;dimension name="u:session_start_time"&gt;2010-01-06T07:32:37-08:00&lt;/dimension&gt; <br>
  &lt;dimension name="u:session_end_time"&gt;2010-01-06T07:32:49-08:00&lt;/dimension&gt; <br>
&lt;/dimensions&gt;<br>
&lt;metrics&gt;<br>
  &lt;u:pages xmlns:u="https://urchin.com/api/urchin/v2/"&gt;1&lt;/u:pages&gt; <br>
  &lt;u:visits xmlns:u="https://urchin.com/api/urchin/v2/"&gt;1&lt;/u:visits&gt; <br>
&lt;/metrics&gt;<br>
&lt;/record&gt;<br>
&lt;/tns:getDataResponse&gt;<br>
</code></pre></blockquote>

<h3>Query Examples</h3>
Get visits from yahoo.com where more than one page has been visited and order by visitor ID:<br>
<pre><code>http://&lt;urchin host&gt;:&lt;port&gt;/services/v2/reportservice/data?login=admin&amp;password=urchin&amp;ids=7&amp;start-date=2008-01-01&amp;end-date=2010-01-01<br>
&amp;dimensions=u:visitor_id,u:session_ip,u:utm_campaign&amp;metrics=u:pages,u:visits,u:transactions&amp;sort=u:visitor_id&amp;filters=u:utm_source%3D~yahoo,u:pages%3E1&amp;table=256<br>
</code></pre>
Get visitors from google.com and number of bookings they conducted:<br>
<pre><code>http://&lt;urchin host&gt;:&lt;port&gt;/services/v2/reportservice/data?login=admin&amp;password=urchin&amp;ids=7&amp;start-date=2008-01-01&amp;end-date=2010-01-01<br>
&amp;dimensions=u:visitor_id&amp;metrics=u:pages,u:visits,u:transactions&amp;filters=u:utm_source%3D~google,u:request_stem%3D~cart.html&amp;table=256<br>
</code></pre>
Get all transactions resulting from bing.com searches for a given term:<br>
<pre><code>http://&lt;urchin host&gt;:&lt;port&gt;/services/v2/reportservice/data?login=admin&amp;password=urchin&amp;ids=7&amp;start-date=2008-01-01&amp;end-date=2010-01-01<br>
&amp;dimensions=u:transaction_id&amp;metrics=u:transactions,u:revenue,u:tax,u:shipping,u:items&amp;filters=u:utm_source%3D~msn,u:utm_term%3D~schwag&amp;table=257<br>
</code></pre>
Get daily metrics for a given period:<br>
<pre><code>http://&lt;urchin host&gt;:&lt;port&gt;/services/v2/reportservice/data?login=admin&amp;password=urchin&amp;ids=7&amp;start-date=2008-01-01&amp;end-date=2010-01-01<br>
&amp;dimensions=u:day&amp;metrics=u:pages,u:visits&amp;table=258<br>
</code></pre>
Get all pages visited by a given visitor during a period of time:<br>
<pre><code>http://&lt;urchin host&gt;:&lt;port&gt;/services/v2/reportservice/data?login=admin&amp;password=urchin&amp;ids=7&amp;start-date=2008-01-01&amp;end-date=2010-01-01<br>
&amp;dimensions=u:request_stem&amp;metrics=u:pages&amp;filters=u:visitor_id%3D~N8T3-DU4N9-7RPL&amp;table=259<br>
</code></pre>


<h3>How to enable the older version of the Urchin Data API in Urchin 7.0</h3>

By default, newly installed or upgraded instances of Urchin 7.0 use the latest version of the Data API. To switch to another version, please refer to section "How do I switch to another version of the Urchin Data API?" of the article <a href='https://secure.urchin.com/helpwiki/en/Urchin_Data_API_FAQ'>Urchin Data API FAQ</a>.