# Lookup Table Filters #

The Lookup Table filter can be used to:

  * implement master tracking codes for campaign tracking. Read [How To Use Master Tracking Codes](https://secure.urchin.com/helpwiki/en/How_To_Use_Master_Tracking_Codes).
  * implement an external data table to lookup and replace character field values when a match occurs. Lookup tables can match against a single field and update multiple fields.

How to use the filter:

  1. In the Filter Wizard:Settings screen, enter your desired filter name (Filter Name field).
  1. Select "Lookup Table" as the filter type.
  1. Select the field you want to update from the Filter Field drop down menu.
  1. Select an internal preconfigured table (see [How To Use Master Tracking Codes](https://secure.urchin.com/helpwiki/en/How_To_Use_Master_Tracking_Codes)) from the Table Name drop down menu or add an external preconfigured table (Urchin 7.0+). External Lookup tables can be added like external Log sources via the "Browse" dialog.

## Internal Lookup Table ##

To add an Internal lookup table:
  1. Open the Filter Manager (or Profile Settings -> Filters tab)
  1. Click ''the Add'' button
  1. Select Filter Type ''Lookup Table ''(''Internal'' table radio button(Urchin 7.0+) is selected by default)
  1. Select table from the drop down list.

http://urchin-web-analytics-software.googlecode.com/svn/trunk/Lookup_int_create.PNG

  1. Click the ''Finish'' button to complete the Internal Lookup table creation.   Note:  A corresponding lookup table file must be created first, and installed in the lib/custom/lookuptables directory of the Urchin distribution. Existing Lookup Tables can be selected in Table Name field.

## External Lookup Table ##

To add an External lookup table:
  1. Open the Filter Manager (or Profile Settings -> Filters tab)
  1. Click ''Add'' button
  1. Select Filter Type ''Lookup Table, ''
  1. Select'' External'' Table type(Urchin 7.0+)
  1. Enter the path to the external lookup file, or click ''Browse'' button to open an external lookup file selection dialog.    Provide Username and Password for UNC authentication.

http://urchin-web-analytics-software.googlecode.com/svn/trunk/Lookup_ext_create.PNG

**Note**: Local file system, NFS and UNC (Windows) shares are supported. FTP/HTTP sources are not supported in Urchin 7.000.