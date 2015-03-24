# Custom Order of Filters #

<p> Beginning with Urchin 7.0, the user can control the order in which log and profile filters are applied during Profile processing.</p>
<p> New "Up" and "Down" arrows on the Profile Settings\Filters and Log Source Settings\Log Filters tabs allow the user to change the order of filters applied to a profile or log source.</p>

![http://urchin-web-analytics-software.googlecode.com/svn/trunk/Order_of_filters_buttons.png](http://urchin-web-analytics-software.googlecode.com/svn/trunk/Order_of_filters_buttons.png)

<p> If filters are defined for a profile and log source simultaneously, log-level filters are applied first. It is also important to note that lookup table, search&replace and advanced filters can create new field values and modify the existing ones. Users should take this into consideration when specifying the filter processing order.</p>
<p> The ability to change filter order is reserved for Super Admin and Account Admin users.</p>

