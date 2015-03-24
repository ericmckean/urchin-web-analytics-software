# Urchin Reporting Database Settings #

### Overview ###
Urchin provides two options for managing the reporting database scalability and precision:

### DB Table Limit ###

This option allows you to maintain large site data within reasonable limits. Use this option to limit the number of records in a single Urchin reporting db table. The default option is appropriate for most installations. If, for a month, the number of records in any table exceeds this limit, then the records beyond this limit are grouped into the last record (named ’Other’). So, larger the table size, the more precise the reporting data.
If an Urchin report shows a high percentage of entries labeled Other, you should increase the DB Table Limit to increase precision.

### Memory Usage Target ###

To limit the amount of memory that can be allocated during log processing, Urchin provides this option to specify the upper limit on the size of reporting db in memory. For larger sites, a larger memory footprint can increase performance as it will be doing less page swapping. Although the default setting is conservative, you should set a larger value if the system has sufficient physical memory available.


### Memory Settings ###

Currently, Urchin supports following max values for reporting DB settings:
  * 32-bit version:
    * DB Table Limit : <= 500,000 records
    * Memory Usage Target : <= 1024 MB
  * 64-bit version:
    * DB Table Limit : <= 10,000,000 records
    * Memory Usage Target : <= 8192 MB

### Urchin 32-bit: Experimental Settings ###

Beginning with version 6.5, Urchin may support extended value for these settings, which should only be used by experienced Urchin users. These extended values will not be visible on the administration interface and will have to be configured via the configuration database. For Urchin 6.5, following are the max values for extended reporting DB settings.
> DB Table Limit : <= 2,000,000 records<br>
<blockquote>Memory Usage Target : <= 2GB</blockquote>

<h3>Urchin 32-bit: Experimental Settings Guidelines</h3>

Since these extended setting are experimental and may lead to out of memory errors on some system, the following information and guidelines should be considered before using them.<br>
<ul><li>In general, each 32-bit application has 4 gigabyte (GB) of virtual address space, which is divided between user address space and kernel address space. User process can only allocate memory in the user address space.<br>
</li><li><b>Windows platform:</b> 2 GB is available to the user application and the other 2 GB is available to the kernel. Although windows OS allows to extend user space up to 3GB via <a href='http://msdn.microsoft.com/en-us/library/bb613473(VS.85).aspx'>4-gigabyte tuning</a>, yet Urchin processes don't assumes this highly unlikely scenario and are always compiled/linked for 2GB limits. Therefore, on windows OS, user should not set DB Table Limit more than <b>500,000</b> records and Memory Usage Target more than <b>1GB</b>.<br>
<ul><li>For maximum <i>performance</i>, set:<br>
<ul><li>Memory Usage Target : <b>1024</b> MB<br>
</li><li>DB Table Limits : <b>500,000</b> db table rows<br>
</li></ul></li><li>For maximum <i>precision</i>, set:<br>
<ul><li>Memory Usage Target : <b>256</b> MB<br>
</li><li>DB Table Limits : <b>1,000,000</b> db table rows<br>
</li></ul></li></ul></li><li><b>Unix platforms:</b> 3 GB is available to the user application and the remaining 1 GB to the kernel. Therefore, on UNIX platform, user should not set DB Table Limit more than <b>500,000</b> records and Memory Usage Target more than <b>2GB</b>.<br>
<ul><li>For maximum performance, set:<br>
<ul><li>Memory Usage Target : <b>2048</b> MB<br>
</li><li>DB Table Limits : <b>500,000</b> db table rows<br>
</li></ul></li><li>For maximum precision, set:<br>
<ul><li>Memory Usage Target : <b>1024</b> MB<br>
</li><li>DB Table Limits : <b>2, 000,000</b> db table rows</li></ul></li></ul></li></ul>

<h3>Urchin 32-bit: Configuring extended 'DB Table Limit'</h3>

Like regular 'DB Table Limit' value, these extended values can be configured for individual profiles as well as globally. The following query will set the DB Table Limit to 1,000,000 records for a profile with profile id '1'.<br>
<pre><code>UPDATE uprofiles SET uipr_db_table_limit=1000000 WHERE uspr_id=1;<br>
</code></pre>
The following query will set the global DB Table Limit to 1,000,000 records. It will get applied to all profiles whose value for uipr_db_table_limit field is 0.<br>
<pre><code>UPDATE uglobals SET uigl_db_table_limit=1000000 WHERE ucgl_name='Global Settings';<br>
</code></pre>

<h3>Urchin 32-bit: Configuring extended 'Memory Usage Target'</h3>

Memory Usage Target can only be set globally.<br>
It automatically is applied to profiles when the DB Memory Usage is set to 'Limit to Cache System' (or db field 'ubpr_limit_db_cache_size' set to 1).<br>
The following query will set the global Memory Usage Target to 2 GB. Note that db field consider the number in 'megabytes' (512 will actually be 512 MB).<br>
<pre><code>UPDATE uglobals SET uigl_db_cache_size=2048 WHERE ucgl_name='Global Settings';<br>
</code></pre>