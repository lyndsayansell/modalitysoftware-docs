# Custom User Attributes

In addition to basic user attributes like `id`, `country` and `department`, Teamwork Analytics allows you to report on _custom user attributes_ from your active directory (we currently support [Directory Extensions](https://docs.microsoft.com/en-gb/azure/active-directory/hybrid/how-to-connect-sync-feature-directory-extensions)).

## Gathering the attributes

To configure custom attributes, you must add their names to the `configuration.CustomUserProperties` table in the TWA SQL database.

The table has one column called `Name` which supports alphanumeric characters and underscores (`a-z`, `A-Z`, `0-9`, `_`), as in the following examples:

| Name |
| ---- |
| companyName |
| faxNumber |
| mailNickname |
| preferredColour |
| shoeSize |
| favouriteSuperhero |


The next time TWA queries user data it will search for these attributes and save any values it finds to the SQL database within the `dbo.UserProperties` table.

## Filtering by custom attributes in Power BI

To configure custom attributes to show up in your Power BI reports, you must add their names to the `configuration.CustomUserPropertiesForReports` table in the TWA SQL database.

The table has numbered CustomAttribute columns for their corresponding filter in Power Bi. The values must match whichever custom attributes names you have previously configured in the `configuration.CustomUserProperties` table to use. They can be in whatever order you wish for them to show up in, such as in the following example. 

| CustomAttribute1 | CustomAttribute2 | CustomAttribute3 | etc.. |
| --- | --- | --- | --- |
| companyName | favouriteSuperhero | faxNumber

There can only be one row in this table and we currently only support up to 10 custom attributes to show in Power BI at a time.

These configured filters will then be displayed in the filter bar in all supported pages.

![CustomUserAttributesFilterBar](images/CustomUserAttributesFilterBar.png)
