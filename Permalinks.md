# Permalinks #
### Overview ###
A permanent link ("permalink") is a link to an Urchin report that preserves the exact settings of the report, such as the filtering, paging, etc. It can be embedded into e-mail or Web pages.<br><br>
"Permalink" can be accessed from the Urchin tool bar (see screenshot below).<br>
<br><br><a href='http://urchin-web-analytics-software.googlecode.com/svn/trunk/permalink_closed.PNG'>http://urchin-web-analytics-software.googlecode.com/svn/trunk/permalink_closed.PNG</a><br><br>

Clicking on the "Permalink" button opens a popup from which you can copy the permalink.<br>
<br><br><a href='http://urchin-web-analytics-software.googlecode.com/svn/trunk/permalink_opened.PNG'>http://urchin-web-analytics-software.googlecode.com/svn/trunk/permalink_opened.PNG</a><br><br>

<h3>Permalink features:</h3>
<ul><li>Permanent links are accessible from the report page and Urchin Home page only. Permalinks are not supported for the Configuration UI;<br>
</li><li>Permanent links include the current settings of profile, selected report, date ranges, filtering, drill-down level, paging and selected advanced segment;<br>
</li><li>Permalink does not preserve any currently open popup reports like "Data Over Time" or "To-date Lifetime Value". It does not also preserve the currently open cross-segment;<br>
</li><li>Permanent links depend on the execution context, i.e. the link acquired from under the session controller is processed via the session controller interface; the link acquired via the direct report linking is processed via the direct report linking interface. In other words, a user who can access report only via direct report linking will not be able to  open the permalink, created in the logged-in session.</li></ul>


<h3>Limitations:</h3>
<ul><li>A permanent link to the admin interface is not allowed (to avoid XSRF and accidental data modification);<br>
</li><li>A permanent link doesn't restore the state of  the "Performance Comparison" report.<br>
</li><li>Permanent links require the user to authenticate when accessing reports. Authentication can be bypassed if Urchin is being setup in Authentication Bypass or Direct Report Linking modes.