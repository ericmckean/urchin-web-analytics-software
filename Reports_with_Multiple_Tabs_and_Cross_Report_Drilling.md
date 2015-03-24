# Reports with Multiple Tabs and Cross Report Drilling #

In Urchin7 supported report structures have been extended with the following new features:

  * reports with multiple tabs
  * ability to display different metric sets at different drill-down levels
  * ability to switch the detail level in reports

## Reports with Multiple Tabs ##

In rs2-file, each report with tabs has NDATA field equal to number of tabs and each tab has prefix T in unique report ID in the tab definition list after the main report.

On the picture below, you can see how  two reports "Top Files" and "Downloads" from "IT Report/Pages&Files" section can be merged in one report with two tabs

http://urchin-web-analytics-software.googlecode.com/svn/trunk/2tab_report.PNG

## Cross Report Drilling and Detail Level Selectors ##

Each report that requires variance at drill levels(different set of metrics or drilling sequence) is described by a combination of a main report that is visible in the navigation menu and a set of hidden pages that describe the variance.

TITLE,CTITLES and TABLE columns have been changed to allow you to specify different values depending on currently selected drill level. The values are separated with the usual Urchin level separation sign (|). A shortened notation is allowed if the field values at all drill levels are the same, i.e. instead of writing 43|43|43 as a TABLE field value, one can simply write 43.
New DLEVELS and DTITLES columns specify the reports to load when the user switches between detail levels and UI titles respectively, i.e. 0|1333,1334|0 means no variation at the 1st level, switching between reports 1333 and 1334 allowed on the 2nd level and no variation at the 3rd level.
Metric set and column types for all drill levels are not allowed to vary.

Here is the sample for Event Tracking "Categories" hierarchy. It allows the following drill paths:

  * Categories -> Actions -> Labels
  * Categories -> Labels -> Actions


The rs2 records that define this hierarchy are described as

|**ID**|**TITLE**|**CTITLES**|**TABLE**|**DXFORMAT**|**DLEVELS**|**DTITLES**|
|:-----|:--------|:----------|:--------|:-----------|:----------|:----------|
|S1333|949|950|951 | 949|950|951,948,952,904,953 |42|41|40 |$A|$B|$C,38,11,40,40/38 |0|1333,1334|0 | 0|950,951|0 |
|P1334|949|951|950 | 949|951|950,948,952,904,953 |42|40|40 |$A|$C|$B,38,11,40,40/38 |0|1333,1334|0 | 0|950,951|0 |


Two different reports describe the two different drill paths a user can take. The DLEVELS field can be read as follows: at 1st level, only Categories are displayed, on 2nd level user can switch between Actions and Labels, and no variation at 3rd field because it depends upon previously selected drill path.


_Basic information on rs2-files and Custom Report creation can be found in article [How To Create Custom Reports](https://secure.urchin.com/helpwiki/en/How_To_Create_Custom_Reports)_