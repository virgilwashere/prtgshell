##Description :


This module contains 41 cmdlets :  
**Connect-PrtgServer**  
**Copy-PrtgSensor**  
**Find-PrtgDevice**  
**Move-PrtgSensor**  
**Pause-PrtgObject**  
**Pause-PrtgSensor**  
**Rename-PrtgSensor**  
**Set-PrtgObjectLocation**  
**Copy-PrtgObject**  
**Get-PrtgDeviceByHostname**  
**Get-PrtgDeviceSensors**  
**Get-PrtgDeviceSensorsByTag**  
**Get-PrtgGroups**  
**Get-PrtgObjectDetails**  
**Get-PrtgObjectProperty**  
**Get-PrtgObjectStatus**  
**Get-PrtgObjectType**  
**Get-PrtgParentProbe**  
**Get-PrtgProbes**  
**Get-PrtgSensorChannels**  
**Get-PrtgSensorHistoricData**  
**Get-PrtgSensorTree**  
**Get-PrtgServer**  
**Get-PrtgServerStatus**  
**Get-PrtgTableData**  
**Invoke-PrtgObjectDiscovery**  
**Invoke-PrtgObjectScan**  
**Measure-PRTGStorage**  
**Move-PrtgObject**  
**New-PrtgSensor**  
**New-PrtgSnmpCpuLoadSensor**  
**New-PrtgSnmpTrafficSensor**  
**Remove-PrtgObject**  
**Remove-PrtgSensorNumbers**  
**Rename-PrtgObject**  
**Resume-PrtgObject**  
**Set-PrtgError**  
**Set-PrtgObjectGeo**  
**Set-PrtgObjectProperty**  
**Set-PrtgResult**  
**Suspend-PrtgObject**  


##Connect-PrtgServer :



The Get-PrtgServer cmdlet establishes and validates connection parameters to allow further communications to the PRTG 
API. The cmdlet needs at least three parameters:
 - The server name (without the protocol)
 - An authenticated username
 - A passhash that can be retrieved from the PRTG user's "My Account" page.


Alias Connect-PrtgServer

The cmdlet returns an object containing details of the connection, but this can be discarded or saved as desired; the 
returned object is not necessary to provide to further calls to the API.

###Parameters :


**Server :** Fully-qualified domain name for the PRTG server. Don't include the protocol part ("https://" or "http://").  


**UserName :** PRTG username to use for authentication to the API.  


**PassHash :** PassHash for the PRTG username. This can be retrieved from the PRTG user's "My Account" page.  


**Port :** The port that PRTG is running on. This defaults to port 443 over HTTPS, and port 80 over HTTP.  


**HttpOnly :** When specified, configures the API connection to run over HTTP rather than the default HTTPS.  
If not specified, it defaults to False .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>Get-PrtgServer "prtg.company.com" "jsmith" 1234567890


Connects to PRTG using the default port (443) over SSL (HTTPS) using the username "jsmith" and the passhash 1234567890.




-------------------------- EXAMPLE 2 --------------------------

PS C:\>Get-PrtgServer "prtg.company.com" "jsmith" 1234567890 -HttpOnly


Connects to PRTG using the default port (80) over SSL (HTTP) using the username "jsmith" and the passhash 1234567890.




-------------------------- EXAMPLE 3 --------------------------

PS C:\>Get-PrtgServer -Server "monitoring.domain.local" -UserName "prtgadmin" -PassHash 1234567890 -Port 8080 -HttpOnly


Connects to PRTG using port 8080 over HTTP using the username "prtgadmin" and the passhash 1234567890.








##Copy-PrtgSensor :


Copy source object to destination object, with new name.

###Parameters :


**ObjectId :**   
If not specified, it defaults to 0 .


**Name :**   


**TargetId :**   


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>$BackupDeviceId = Find-PrtgDevice srv-veeam-w02


Copy-PrtgObject -ObjectId 6535 -Name 'New backup job' -TargetId $BackupDevice.objid








##Find-PrtgDevice :


Find PRTG device which matches hostname, IP Address, or FQDN.

###Parameters :


**hostname :** string to search devices  


**AsObjID :**   
If not specified, it defaults to False .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Move-PrtgSensor :


if you want positional changes, you give the string nouns ("up","down","top","bottom")
if you want group changes, you give an integer for the target objectid

###Parameters :


**ObjectId :**   
If not specified, it defaults to 0 .


**Position :**   


**TargetId :**   


**WhatIf :**   


**Confirm :**   


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Pause-PrtgObject :


See also Resume-PrtgObject

###Parameters :


**ObjectId :** ID of the object to pause/resume  
If not specified, it defaults to 0 .


**PauseLength :** Length of time in minutes to pause the object, $null for indefinite  


**PauseMessage :** Message to associate with the pause event  
If not specified, it defaults to Paused by PowerShell API .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Pause-PrtgSensor :


See also Resume-PrtgObject

###Parameters :


**ObjectId :** ID of the object to pause/resume  
If not specified, it defaults to 0 .


**PauseLength :** Length of time in minutes to pause the object, $null for indefinite  


**PauseMessage :** Message to associate with the pause event  
If not specified, it defaults to Paused by PowerShell API .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Rename-PrtgSensor :


###Parameters :


**ObjectId :**   
If not specified, it defaults to 0 .


**NewName :**   


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Set-PrtgObjectLocation :


/api/setlonlat.htm?id=objectid&location=name_of_object_location&lonlat=longitude,latitude

###Parameters :


**ObjectId :** ID of the object to set  
If not specified, it defaults to 0 .


**Location :** Name of the object's property to get  


**Geo :** Value to which to set the geo location property of the object  


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>Set-PrtgObjectGeo -ObjectId 6250 -Geo '-27.465358, 153.029785' -Location 'NextDC B1 Brisbane'


Sets Geo location of this group object to NextDC B1.








##Copy-PrtgObject :


Copy source object to destination object, with new name.

###Parameters :


**ObjectId :**   
If not specified, it defaults to 0 .


**Name :**   


**TargetId :**   


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>$BackupDeviceId = Find-PrtgDevice srv-veeam-w02


Copy-PrtgObject -ObjectId 6535 -Name 'New backup job' -TargetId $BackupDevice.objid








##Get-PrtgDeviceByHostname :


Find PRTG device which matches hostname, IP Address, or FQDN.

###Parameters :


**hostname :** string to search devices  


**AsObjID :**   
If not specified, it defaults to False .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Get-PrtgDeviceSensors :


###Parameters :


**DeviceId :**   
If not specified, it defaults to 0 .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Get-PrtgDeviceSensorsByTag :


###Parameters :


**FilterTags :**   


**SensorId :**   
If not specified, it defaults to 0 .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Get-PrtgGroups :


###Parameters :


###Examples :


##Get-PrtgObjectDetails :


The Get-PrtgObjectDetails provides metadata about a given object in PRTG. This includes the object name and type, 
information about the parent device and the probe, last status information, and uptime summaries.

For objects other than sensors, this will only report around half of the listed values. Sensor objects will return all 
of the values.

The Value parameter can be used to return a single named value rather than the complete hash table.

###Parameters :


**ObjectId :** An object ID from PRTG. Objects include probes, groups, devices, and sensors, as well as reports, maps, and todos.  
If not specified, it defaults to 0 .


**Value :** If the Value parameter is specified, the cmdlet will return a simple string containing the named value specified.  


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>Get-PrtgObjectDetails 1002


Returns details for object 1002, which is typically the Core Server's Probe Device Core Health sensor.




-------------------------- EXAMPLE 2 --------------------------

PS C:\>Get-PrtgObjectDetails -ObjectId 40 -Value sensortype


Returns the sensortype of object 40, which is typically the Core Server Prove Device.








##Get-PrtgObjectProperty :


###Parameters :


**ObjectId :** ID of the object to query  
If not specified, it defaults to 0 .


**Property :** Name of the object's property to get  


**Raw :**   
If not specified, it defaults to False .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Get-PrtgObjectStatus :


###Parameters :


**ObjectId :** ID of the object to query  
If not specified, it defaults to 0 .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Get-PrtgObjectType :


This cmdlet simply returns a string value identifying the object type of the requested object. It can return "group", 
"probenode", "device", or "sensor", as well as other object types such as reports and maps. If the -Detailed switch is 
used, it will also report additional details about sensor types.

###Parameters :


**ObjectId :** An object ID from PRTG. Objects include probes, groups, devices, and sensors, as well as reports, maps, and todos.  
If not specified, it defaults to 0 .


**Detailed :** If the Detailed switch is set, the cmdlet will return additional details about sensor types (but not group, device, probenode, or other object types).  
If not specified, it defaults to False .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>Get-PrtgObjectType 40


Reports "device", as object 40 refers to the Core Server device.




-------------------------- EXAMPLE 2 --------------------------

PS C:\>Get-PrtgObjectType 1002


Reports "sensor", referring to the Core State sensor on the Core Server device.




-------------------------- EXAMPLE 3 --------------------------

PS C:\>Get-PrtgObjectType 1002 -Detailed


Reports "sensor: corestate", referring to the Core State sensor on the Core Server device.








##Get-PrtgParentProbe :


###Parameters :


**DeviceId :**   
If not specified, it defaults to 0 .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Get-PrtgProbes :


###Parameters :


###Examples :


##Get-PrtgSensorChannels :


###Parameters :


**SensorId :**   
If not specified, it defaults to 0 .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Get-PrtgSensorHistoricData :


###Parameters :


**SensorId :**   
If not specified, it defaults to 0 .


**HistoryInDays :** really, this should be a (negative) timespan  
If not specified, it defaults to 0 .


**ChannelName :**   


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Get-PrtgSensorTree :


###Parameters :


**ObjectId :**   


**Value :**   


###Examples :


##Get-PrtgServer :


The Get-PrtgServer cmdlet establishes and validates connection parameters to allow further communications to the PRTG 
API. The cmdlet needs at least three parameters:
 - The server name (without the protocol)
 - An authenticated username
 - A passhash that can be retrieved from the PRTG user's "My Account" page.


Alias Connect-PrtgServer

The cmdlet returns an object containing details of the connection, but this can be discarded or saved as desired; the 
returned object is not necessary to provide to further calls to the API.

###Parameters :


**Server :** Fully-qualified domain name for the PRTG server. Don't include the protocol part ("https://" or "http://").  


**UserName :** PRTG username to use for authentication to the API.  


**PassHash :** PassHash for the PRTG username. This can be retrieved from the PRTG user's "My Account" page.  


**Port :** The port that PRTG is running on. This defaults to port 443 over HTTPS, and port 80 over HTTP.  


**HttpOnly :** When specified, configures the API connection to run over HTTP rather than the default HTTPS.  
If not specified, it defaults to False .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>Get-PrtgServer "prtg.company.com" "jsmith" 1234567890


Connects to PRTG using the default port (443) over SSL (HTTPS) using the username "jsmith" and the passhash 1234567890.




-------------------------- EXAMPLE 2 --------------------------

PS C:\>Get-PrtgServer "prtg.company.com" "jsmith" 1234567890 -HttpOnly


Connects to PRTG using the default port (80) over SSL (HTTP) using the username "jsmith" and the passhash 1234567890.




-------------------------- EXAMPLE 3 --------------------------

PS C:\>Get-PrtgServer -Server "monitoring.domain.local" -UserName "prtgadmin" -PassHash 1234567890 -Port 8080 -HttpOnly


Connects to PRTG using port 8080 over HTTP using the username "prtgadmin" and the passhash 1234567890.








##Get-PrtgServerStatus :


This a lightweight call to get status data like number of alarms, messages.

###Parameters :


**Raw :**   
If not specified, it defaults to False .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>Get-PrtgServerStatus











##Get-PrtgTableData :


The Get-PrtgTableData cmdlet can return data of various different content types using the specified parent object, as 
well as specify the return columns or filtering options. The input formats generally coincide with the Live Data demo 
from the PRTG API documentation, but there are some content types that the cmdlet does not yet support, such as 
"sensortree".
Valid content types are "devices", "groups", "sensors", "todos", "messages", "values", "channels", and "history". Note 
that all content types are not valid for all object types; for example, a device object can contain no groups or 
channels.

###Parameters :


**Content :** The type of data for the specified object. Valid values are "devices", "groups", "sensors", "todos", "messages", "values", "channels", and "history". Note that all content types are not valid for all object types; for example, a device object can contain no groups or channels.  


**ObjectId :** An object ID from PRTG. Objects include probes, groups, devices, and sensors, as well as reports, maps, and todos.  
If not specified, it defaults to 0 .


**Columns :** A string array of named column values to return. In general the default return values for a given content type will return all of the available columns; this parameter can be used to change the order of columns or specify which columns to include or ignore.  


**FilterTags :** A string array of sensor tags. This parameter only has any effect if the content type is "sensors". Output will only include sensors with the specified tags. Note that specifying multiple tags performs a logical OR of tags.  


**Count :** Number of records to return. PRTG's internal default for this is 500. Valid values are 1-50000.  
If not specified, it defaults to 500 .


**Raw :** If this switch is set, the cmdlet will return the raw XML data rather than a PowerShell object.  
If not specified, it defaults to False .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>Get-PrtgTableData groups 1


Returns the groups under the object ID 1, which is typically the Core Server's Local Probe.




-------------------------- EXAMPLE 2 --------------------------

PS C:\>Get-PrtgTableData sensors -FilterTags corestatesensor,probesensor


Returns a filtered list of sensors tagged with "corestatesensor" or "probesensor".




-------------------------- EXAMPLE 3 --------------------------

PS C:\>Get-PrtgTableData messages 1002


Returns the messages log for device 1002.




-------------------------- EXAMPLE 4 --------------------------

PS C:\>Get-PrtgTableData channels -SensorId 2591


Returns the channel data for object (sensor) 2591.








##Invoke-PrtgObjectDiscovery :


###Parameters :


**ObjectId :** ID of the object to scan  
If not specified, it defaults to 0 .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Invoke-PrtgObjectScan :


###Parameters :


**ObjectId :** ID of the object to scan  
If not specified, it defaults to 0 .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Measure-PRTGStorage :


###Parameters :


**HistoryInDays :**   


**HistorySensorObjectId :**   


###Examples :


##Move-PrtgObject :


if you want positional changes, you give the string nouns ("up","down","top","bottom")
if you want group changes, you give an integer for the target objectid

###Parameters :


**ObjectId :**   
If not specified, it defaults to 0 .


**Position :**   


**TargetId :**   


**WhatIf :**   


**Confirm :**   


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##New-PrtgSensor :


###Parameters :


**PrtgObject :**   


###Examples :


##New-PrtgSnmpCpuLoadSensor :


###Parameters :


**Interval :**   


**Name :**   


**ParentId :**   


**Priority :**   


**Tags :**   


###Examples :


##New-PrtgSnmpTrafficSensor :


###Parameters :


**ChartType :**   


**ErrorOnDown :**   


**InterfaceNumber :**   


**Interval :**   


**Name :**   


**ParentId :**   


**Priority :**   


**ShowBroadcast :**   


**ShowDiscards :**   


**ShowErrors :**   


**ShowMulticast :**   


**ShowNonUnicast :**   


**ShowUnicast :**   


**ShowUnknown :**   


**Tags :**   


###Examples :


##Remove-PrtgObject :


###Parameters :


**ObjectId :** TODO: document this; $ObjectID for this cmdlet can either be a single integer or a comma-separated string of integers to handle multiples  


**WhatIf :**   


**Confirm :**   


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Remove-PrtgSensorNumbers :


###Parameters :


**ObjectId :**   


###Examples :


##Rename-PrtgObject :


###Parameters :


**ObjectId :**   
If not specified, it defaults to 0 .


**NewName :**   


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Resume-PrtgObject :


See also Suspend-PrtgObject

###Parameters :


**ObjectId :** ID of the object to pause/resume  
If not specified, it defaults to 0 .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>











##Set-PrtgError :


###Parameters :


**PrtgErrorText :**   


###Examples :


##Set-PrtgObjectGeo :


/api/setlonlat.htm?id=objectid&location=name_of_object_location&lonlat=longitude,latitude

###Parameters :


**ObjectId :** ID of the object to set  
If not specified, it defaults to 0 .


**Location :** Name of the object's property to get  


**Geo :** Value to which to set the geo location property of the object  


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>Set-PrtgObjectGeo -ObjectId 6250 -Geo '-27.465358, 153.029785' -Location 'NextDC B1 Brisbane'


Sets Geo location of this group object to NextDC B1.








##Set-PrtgObjectProperty :


Change properties of object

If $Property = 'priority', Set priority of an object (valid values are 1 to 5).

###Parameters :


**ObjectId :** ID of the object to query  
If not specified, it defaults to 0 .


**Property :** Name of the object's property to get  


**Value :** Value to which to set the property of the object  


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>Set-PrtgObjectProperty 2512 name newname







-------------------------- EXAMPLE 2 --------------------------

PS C:\>Set-PrtgObjectProperty 2512 -Property priority 4











##Set-PrtgResult :


###Parameters :


**Channel :**   


**DecimalMode :**   


**ErrorMsg :**   


**MaxError :**   


**MaxWarn :**   


**MinWarn :**   


**Mode :**   


**ShowChart :**   


**SpeedSize :**   


**Unit :**   


**Value :**   


**ValueLookup :**   


**VolumeSize :**   


**WarnMsg :**   


**Warning :**   


###Examples :


##Suspend-PrtgObject :


See also Resume-PrtgObject

###Parameters :


**ObjectId :** ID of the object to pause/resume  
If not specified, it defaults to 0 .


**PauseLength :** Length of time in minutes to pause the object, $null for indefinite  


**PauseMessage :** Message to associate with the pause event  
If not specified, it defaults to Paused by PowerShell API .


###Examples :


-------------------------- EXAMPLE 1 --------------------------

PS C:\>













