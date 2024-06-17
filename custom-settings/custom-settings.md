******************** **CUSTOM SETTINGS** ************************


Custom settings are similar to custom objects. Application developers can create custom sets of data and associate custom data for an organization, profile, or specific user. 
All custom settings data is exposed in the application cache, which enables efficient access without the cost of repeated queries to the database. 
Formula fields, validation rules, flows, Apex, and SOAP API can then use this data

NOTE: While custom settings data is included in sandbox copies, it is treated as data for the purposes of Apex test isolation. 
Apex tests must use SeeAllData=true to see existing custom settings data in the organization. As a best practice, create the required custom settings data in your test setup.

**> List Custom Settings :**
---------------------------------------------------------------
A type of custom setting that provides a reusable set of static data that can be accessed across your organization. 
If you use a particular set of data frequently within your application, putting that data in a list custom setting streamlines access to it. 

**> Hierarchy Custom Settings :**
---------------------------------------------------------------
A type of custom setting that uses a built-in hierarchical logic that lets you “personalize” settings for specific profiles or users. 
The hierarchy logic checks the organization, profile, and user settings for the current user and returns the most specific, or “lowest,” value. 
In the hierarchy, settings for an organization are overridden by profile settings, which, in turn, are overridden by user settings.

**Accessing a List Custom Setting**
---------------------------------------------------------------
Syntax > Map<String_dataset_name, CustomSettingName__c> mcs = CustomSettingName__c.getAll();
Example > CustomSettingName__c mc = CustomSettingName__c.getValues(data_set_name);

**Accessing a Hierarchy Custom Setting**
---------------------------------------------------------------
> CustomSettingName__c mc = CustomSettingName__c.getOrgDefaults();
> CustomSettingName__c mc = CustomSettingName__c.getInstance(Profile_ID);
