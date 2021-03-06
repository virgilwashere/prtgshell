﻿# Module: prtgshell 

This module contains 37 cmdlets :  
 * **Connect-PrtgServer**  
 * **Copy-PrtgObject**  
 * **Get-PrtgDeviceByHostname**  
 * **Get-PrtgDeviceSensors**  
 * **Get-PrtgDeviceSensorsByTag**  
 * **Get-PrtgGroups**  
 * **Get-PrtgObjectDetails**  
 * **Get-PrtgObjectMonitoringState**  
 * **Get-PrtgObjectProperty**  
 * **Get-PrtgObjectStatus**  
 * **Get-PrtgObjectType**  
 * **Get-PrtgParentProbe**  
 * **Get-PrtgPassHash**  
 * **Get-PRTGProbes**  
 * **Get-PrtgSensorChannels**  
 * **Get-PrtgSensorDetails**  
 * **Get-PrtgSensorHistoricData**  
 * **Get-PrtgSensorTree**  
 * **Get-PrtgServer**  
 * **Get-PrtgServerStatus**  
 * **Get-PrtgTableData**  
 * **Invoke-PrtgObjectDiscovery**  
 * **Invoke-PrtgObjectScan**  
 * **Measure-PrtgStorage**  
 * **Move-PrtgObject**  
 * **New-PrtgSensor**  
 * **New-PrtgSnmpCpuLoadSensor**  
 * **New-PrtgSnmpTrafficSensor**  
 * **Remove-PrtgObject**  
 * **Remove-PrtgSensorNumbers**  
 * **Rename-PrtgObject**  
 * **Resume-PrtgObject**  
 * **Set-PrtgError**  
 * **Set-PrtgObjectGeo**  
 * **Set-PrtgObjectProperty**  
 * **Set-PrtgResult**  
 * **Suspend-PrtgObject**  
 

This module contains 9 aliases :  
 * **Get-PrtgServer** -> Connect-PrtgServer
 * **Copy-PrtgSensor** -> Copy-PrtgObject  
 * **Find-PrtgDevice** -> Get-PrtgDeviceByHostname  
 * **Move-PrtgSensor** -> Move-PrtgObject  
 * **Pause-PrtgObject** -> Suspend-PrtgObject  
 * **Pause-PrtgSensor** -> Suspend-PrtgObject  
 * **Rename-PrtgSensor** -> Rename-PrtgObject  
 * **Set-PrtgObjectLocation** -> Set-PrtgObjectGeo  
 

# [Connect-PrtgServer]
## Synopsis
Get-PrtgServer
Establishes initial connection to PRTG API.
 

## Syntax
```PowerShell
 Connect-PrtgServer [[-Server] <String>] [[-UserName] <String>] [[-PassHash] <String>] [[-Port] <Int32>] [-HttpOnly] [<CommonParameters>]   
```
## Description
The Get-PrtgServer cmdlet establishes and validates connection parameters to allow further communications to the PRTG API. The cmdlet needs at least three parameters:
 - The server name (without the protocol)
 - An authenticated username
 - A passhash that can be retrieved from the PRTG user's "My Account" page.


Alias Get-PrtgServer

The cmdlet returns an object containing details of the connection, but this can be discarded or saved as desired; the returned object is not necessary to provide to further calls to the API.

## Examples 


###  Example 1 
```PowerShell
PS C:\>Connect-PrtgServer "prtg.company.com" "jsmith" 1234567890
```
Connects to PRTG using the default port (443) over SSL (HTTPS) using the username "jsmith" and the passhash 1234567890.





###  Example 2 
```PowerShell
PS C:\>Connect-PrtgServer "prtg.company.com" "jsmith" 1234567890 -HttpOnly
```
Connects to PRTG using the default port (80) over SSL (HTTP) using the username "jsmith" and the passhash 1234567890.





###  Example 3 
```PowerShell
PS C:\>Connect-PrtgServer -Server "monitoring.domain.local" -UserName "prtgadmin" -PassHash 1234567890 -Port 8080 -HttpOnly
```
Connects to PRTG using port 8080 over HTTP using the username "prtgadmin" and the passhash 1234567890.




## Parameters
### Server

Fully-qualified domain name for the PRTG server. Don't include the protocol part ("https://" or "http://").



- **Type**: String
- **DefaultValue**: prtg.techproject.com.au
- **PipelineInput**: false
- **Position**: 1
- **Required**: false


### UserName
PRTG username to use for authentication to the API.



- **Type**: String
- **DefaultValue**: "$env:USERNAME"
- **PipelineInput**: false
- **Position**: 2
- **Required**: false


### PassHash
PassHash for the PRTG username. This can be retrieved from the PRTG user's "My Account" page.



- **Type**: String
- **DefaultValue**: (Get-PSCredential $Server\$Username).GetNetworkCredential().password
- **PipelineInput**: false
- **Position**: 3
- **Required**: false


### Port
The port that PRTG is running on. This defaults to port 443 over HTTPS, and port 80 over HTTP.



- **Type**: Int32
- **PipelineInput**: false
- **Position**: 4
- **Required**: false


### HttpOnly
When specified, configures the API connection to run over HTTP rather than the default HTTPS.



- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Copy-PrtgObject]
## Synopsis
Copy source object to target 

## Syntax
```PowerShell
 Copy-PrtgObject [-ObjectId] <Int32> [-Name] <String> [-TargetId] <String> [<CommonParameters>]   
```
## Description
Copy source object to destination object, with new name.

## Examples 


###  Example 1 
```PowerShell
PS C:\>$BackupDeviceId = Find-PrtgDevice srv-veeam-w02
```
Copy-PrtgObject -ObjectId 6535 -Name 'New backup job' -TargetId $BackupDevice.objid




## Parameters
### ObjectId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### Name


- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### TargetId


- **Type**: String
- **PipelineInput**: false
- **Position**: 3
- **Required**: true


# [Get-PrtgDeviceByHostname]
## Synopsis
Find PRTG device with hostname 

## Syntax
```PowerShell
 Get-PrtgDeviceByHostname [-hostname] <String> [-AsObjID] [<CommonParameters>]   
```
## Description
Find PRTG device which matches hostname, IP Address, or FQDN.

## Examples 


###  Example 1 





## Parameters
### hostname
string to search devices



- **Type**: String
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### AsObjID


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Get-PrtgDeviceSensors]
## Syntax
```PowerShell
 Get-PrtgDeviceSensors [-DeviceId] <Int32> [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### DeviceId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


# [Get-PrtgDeviceSensorsByTag]
## Syntax
```PowerShell
 Get-PrtgDeviceSensorsByTag [-FilterTags] <String[]> [[-SensorId] <Int32>] [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### FilterTags


- **Type**: String[]
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### SensorId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 2
- **Required**: false


# [Get-PrtgGroups]
## Synopsis
Lists the groups in the device tree 

## Syntax
```PowerShell
 Get-PrtgGroups [<CommonParameters>]   
```
## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgGroups
```





# [Get-PrtgObjectDetails]
## Synopsis
Provides details for the specified object. 

## Syntax
```PowerShell
 Get-PrtgObjectDetails [-ObjectId] <Int32> [[-Value] <String>] [<CommonParameters>]   
```
## Description
The Get-PrtgObjectDetails provides metadata about a given object in PRTG. This includes the object name and type, information about the parent device and the probe, last status information, and uptime summaries.

For objects other than sensors, this will only report around half of the listed values. Sensor objects will return all of the values.

The Value parameter can be used to return a single named value rather than the complete hash table.

## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgObjectDetails 1002
```
Returns details for object 1002, which is typically the Core Server's Probe Device Core Health sensor.





###  Example 2 
```PowerShell
PS C:\>Get-PrtgObjectDetails -ObjectId 40 -Value sensortype
```
Returns the sensortype of object 40, which is typically the Core Server Prove Device.




## Parameters
### ObjectId
An object ID from PRTG. Objects include probes, groups, devices, and sensors, as well as reports, maps, and todos.



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### Value
If the Value parameter is specified, the cmdlet will return a simple string containing the named value specified.



- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: false


# [Get-PrtgObjectMonitoringState]
## Synopsis
Get object monitoring state 

## Syntax
```PowerShell
 Get-PrtgObjectMonitoringState [-ObjectId] <Int32> [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### ObjectId
ID of the object to query



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


# [Get-PrtgObjectProperty]
## Synopsis
Get object property/setting 

## Syntax
```PowerShell
 Get-PrtgObjectProperty [-ObjectId] <Int32> [-Property] <String> [-Raw] [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### ObjectId
ID of the object to query



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### Property
Name of the object's property to get



- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### Raw


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Get-PrtgObjectStatus]
## Synopsis
Get object status 

## Syntax
```PowerShell
 Get-PrtgObjectStatus [-ObjectId] <Int32> [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### ObjectId
ID of the object to query



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


# [Get-PrtgObjectType]
## Synopsis
Returns the object of a given object ID. 

## Syntax
```PowerShell
 Get-PrtgObjectType [-ObjectId] <Int32> [-Detailed] [<CommonParameters>]   
```
## Description
This cmdlet simply returns a string value identifying the object type of the requested object. It can return "group", "probenode", "device", or "sensor", as well as other object types such as reports and maps. If the -Detailed switch is used, it will also report additional details about sensor types.

## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgObjectType 40
```
Reports "device", as object 40 refers to the Core Server device.





###  Example 2 
```PowerShell
PS C:\>Get-PrtgObjectType 1002
```
Reports "sensor", referring to the Core State sensor on the Core Server device.





###  Example 3 
```PowerShell
PS C:\>Get-PrtgObjectType 1002 -Detailed
```
Reports "sensor: corestate", referring to the Core State sensor on the Core Server device.




## Parameters
### ObjectId
An object ID from PRTG. Objects include probes, groups, devices, and sensors, as well as reports, maps, and todos.



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### Detailed
If the Detailed switch is set, the cmdlet will return additional details about sensor types (but not group, device, probenode, or 
other object types).



- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Get-PrtgParentProbe]
## Synopsis
Show parent probe of device 

## Syntax
```PowerShell
 Get-PrtgParentProbe [-DeviceId] <Int32> [<CommonParameters>]   
```
## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgParentProbe 3521
```





## Parameters
### DeviceId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


# [Get-PrtgPassHash]
## Synopsis
Get a password hash to enable further communication to PRTG API. 

## Syntax
```PowerShell
 Get-PrtgPassHash [[-Server] <String>] [-UserName] <String> [<CommonParameters>]   
```
## Description
The Get-PrtgPassHash cmdlet establishes and validates connection parameters to allow further communications to the PRTG API. The cmdlet needs at least three parameters:
 - The server name (without the protocol)
 - An authenticated username
 
 You are prompted for a password.

The cmdlet returns an a PSCredential that is used to save the passhash.

## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgPassHash "prtg.company.com" "jsmith"
```
Connects to PRTG using the default port (443) over SSL (HTTPS) using the username "jsmith" and gets passhash.




## Parameters
### Server
Fully-qualified domain name for the PRTG server. Don't include the protocol part ("https://" or "http://").



- **Type**: String
- **DefaultValue**: prtg.techproject.com.au
- **PipelineInput**: false
- **Position**: 1
- **Required**: false


### UserName
PRTG username to use for authentication to the API.



- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


# [Get-PRTGProbes]
## Synopsis
Lists of probes 

## Syntax
```PowerShell
 Get-PRTGProbes [<CommonParameters>]   
```
## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PRTGProbes
```





# [Get-PrtgSensorChannels]
## Synopsis
Lists the channels defined in a sensor 

## Syntax
```PowerShell
 Get-PrtgSensorChannels [-SensorId] <Int32> [<CommonParameters>]   
```
## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgSensorChannels -SensorId 6250
```





## Parameters
### SensorId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


# [Get-PrtgSensorDetails]
## Synopsis
Provides details for the specified object. 

## Syntax
```PowerShell
 Get-PrtgSensorDetails [-SensorId] <Int32> [[-Value] <String>] [<CommonParameters>]   
```
## Description
The Get-PrtgSensorDetails provides metadata about a given object in PRTG. This includes the object name and type, information about the parent device and the probe, last status information, and uptime summaries.

For objects other than sensors, this will only report around half of the listed values. Sensor objects will return all of the values.

The Value parameter can be used to return a single named value rather than the complete hash table.

## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgSensorDetails 1002
```
Returns details for object 1002, which is typically the Core Server's Probe Device Core Health sensor.





###  Example 2 
```PowerShell
PS C:\>Get-PrtgSensorDetails -ObjectId 40 -Value sensortype
```
Returns the sensortype of object 40, which is typically the Core Server Prove Device.




## Parameters
### SensorId
ID of the object to query



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: true (ByPropertyName)
- **Position**: 1
- **Required**: true


### Value
If the Value parameter is specified, the cmdlet will return a simple string containing the named value specified.



- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: false


# [Get-PrtgSensorHistoricData]
## Syntax
```PowerShell
 Get-PrtgSensorHistoricData [-SensorId] <Int32> [-HistoryInDays] <Int32> [[-ChannelName] <String>] [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### SensorId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### HistoryInDays
really, this should be a (negative) timespan



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### ChannelName


- **Type**: String
- **PipelineInput**: false
- **Position**: 3
- **Required**: false


# [Get-PrtgSensorTree]
## Synopsis
Lists the sensors on a device 

## Syntax
```PowerShell
 Get-PrtgSensorTree [[-ObjectId] <Int32>] [[-Value] <String>] [<CommonParameters>]   
```
## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgSensorTree -ObjectId 6250
```





## Parameters
### ObjectId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: false


### Value


- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: false


# [Get-PrtgServer]
## Synopsis
Connect-PrtgServer
Establishes initial connection to PRTG API.
Get current system status
 

## Syntax
```PowerShell
 Get-PrtgServer [-Server] <String> [-UserName] <String> [-PassHash] <String> [[-Port] <Int32>] [-HttpOnly] [<CommonParameters>]  Get-PrtgServerStatus [-Raw] [<CommonParameters>]   
```
## Description
The Get-PrtgServer cmdlet establishes and validates connection parameters to allow further communications to the PRTG API. The cmdlet needs at least three parameters:
 - The server name (without the protocol)
 - An authenticated username
 - A passhash that can be retrieved from the PRTG user's "My Account" page.

Alias Connect-PrtgServer
The cmdlet returns an object containing details of the connection, but this can be discarded or saved as desired; the returned object is not necessary to provide to further calls to the API.
This a lightweight call to get status data like number of alarms, messages.


## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgServer "prtg.company.com" "jsmith" 1234567890
```
Connects to PRTG using the default port (443) over SSL (HTTPS) using the username "jsmith" and the passhash 1234567890.





###  Example 2 
```PowerShell
PS C:\>Get-PrtgServer "prtg.company.com" "jsmith" 1234567890 -HttpOnly
```
Connects to PRTG using the default port (80) over SSL (HTTP) using the username "jsmith" and the passhash 1234567890.





###  Example 3 
```PowerShell
PS C:\>Get-PrtgServer -Server "monitoring.domain.local" -UserName "prtgadmin" -PassHash 1234567890 -Port 8080 -HttpOnly
```
Connects to PRTG using port 8080 over HTTP using the username "prtgadmin" and the passhash 1234567890.





###  Example 1 
```PowerShell
PS C:\>Get-PrtgServerStatus
```





## Parameters
### Server
Fully-qualified domain name for the PRTG server. Don't include the protocol part ("https://" or "http://").



- **Type**: String
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### UserName
PRTG username to use for authentication to the API.



- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### PassHash
PassHash for the PRTG username. This can be retrieved from the PRTG user's "My Account" page.



- **Type**: String
- **PipelineInput**: false
- **Position**: 3
- **Required**: true


### Port
The port that PRTG is running on. This defaults to port 443 over HTTPS, and port 80 over HTTP.



- **Type**: Int32
- **PipelineInput**: false
- **Position**: 4
- **Required**: false


### HttpOnly
When specified, configures the API connection to run over HTTP rather than the default HTTPS.



- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### Raw


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Get-PrtgServerStatus]
## Synopsis
Get current system status 

## Syntax
```PowerShell
 Get-PrtgServerStatus [-Raw] [<CommonParameters>]   
```
## Description
This a lightweight call to get status data like number of alarms, messages.

## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgServerStatus
```





## Parameters
### Raw


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Get-PrtgTableData]
## Synopsis
Returns a PowerShell object containing data from the specified object in PRTG. 

## Syntax
```PowerShell
 Get-PrtgTableData [-Content] <String> [[-ObjectId] <Int32>] [-Columns <String[]>] [-FilterTags <String[]>] [-Count <Int32>] [-Raw] [<CommonParameters>]   
```
## Description
The Get-PrtgTableData cmdlet can return data of various different content types using the specified parent object, as well as specify the return columns or filtering options. The input formats generally coincide with the Live Data demo from the PRTG API documentation, but there are some content types that the cmdlet does not yet support, such as "sensortree".
Valid content types are "devices", "groups", "sensors", "todos", "messages", "values", "channels", and "history". Note that all content types are not valid for all object types; for example, a device object can contain no groups or channels.

## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgTableData groups 1
```
Returns the groups under the object ID 1, which is typically the Core Server's Local Probe.





###  Example 2 
```PowerShell
PS C:\>Get-PrtgTableData sensors -FilterTags corestatesensor,probesensor
```
Returns a filtered list of sensors tagged with "corestatesensor" or "probesensor".





###  Example 3 
```PowerShell
PS C:\>Get-PrtgTableData messages 1002
```
Returns the messages log for device 1002.





###  Example 4 
```PowerShell
PS C:\>Get-PrtgTableData channels -SensorId 2591
```
Returns the channel data for object (sensor) 2591.




## Parameters
### Content
The type of data for the specified object. Valid values are "devices", "groups", "sensors", "todos", "messages", "values", 
"channels", and "history". Note that all content types are not valid for all object types; for example, a device object can 
contain no groups or channels.



- **Type**: String
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### ObjectId
An object ID from PRTG. Objects include probes, groups, devices, and sensors, as well as reports, maps, and todos.



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 2
- **Required**: false


### Columns
A string array of named column values to return. In general the default return values for a given content type will return all of 
the available columns; this parameter can be used to change the order of columns or specify which columns to include or ignore.



- **Type**: String[]
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### FilterTags
A string array of sensor tags. This parameter only has any effect if the content type is "sensors". Output will only include 
sensors with the specified tags. Note that specifying multiple tags performs a logical OR of tags.



- **Type**: String[]
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### Count
Number of records to return. PRTG's internal default for this is 500. Valid values are 1-50000.



- **Type**: Int32
- **DefaultValue**: 500
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### Raw
If this switch is set, the cmdlet will return the raw XML data rather than a PowerShell object.



- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Invoke-PrtgObjectDiscovery]
## Synopsis
Run Auto Discovery for an object 

## Syntax
```PowerShell
 Invoke-PrtgObjectDiscovery [-ObjectId] <Int32> [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### ObjectId
ID of the object to scan



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


# [Invoke-PrtgObjectScan]
## Synopsis
Scan a sensor now 

## Syntax
```PowerShell
 Invoke-PrtgObjectScan [-ObjectId] <Int32> [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### ObjectId
ID of the object to scan



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


# [Measure-PrtgStorage]
## Synopsis
Measures storage used by sensor 

## Syntax
```PowerShell
 Measure-PrtgStorage [-HistorySensorObjectId] <Int32> [[-HistoryInDays] <Int32>] [<CommonParameters>]   
```
## Description
Returns detailed PRTG storage information including: 
remaining disk available
monitoring data stored
average daily growth rate
x days space available

## Examples 


###  Example 1 
```PowerShell
PS C:\>Measure-PRTGStorage -SensorId 1241
```





## Parameters
### HistorySensorObjectId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### HistoryInDays


- **Type**: Int32
- **DefaultValue**: 30
- **PipelineInput**: false
- **Position**: 2
- **Required**: false


# [Move-PrtgObject]
## Synopsis
Moves an object in PRTG tree 

## Syntax
```PowerShell
 Move-PrtgObject [-ObjectId] <Int32> [-Position] <String> [-WhatIf] [-Confirm] [<CommonParameters>] Move-PrtgObject [-ObjectId] <Int32> [-TargetId] <String> [-WhatIf] [-Confirm] [<CommonParameters>]   
```
## Description
if you want positional changes, you give the string nouns ("up","down","top","bottom")
if you want group changes, you give an integer for the target objectid

## Examples 


###  Example 1 





## Parameters
### ObjectId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### Position


- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### TargetId


- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### WhatIf


- **Type**: SwitchParameter
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### Confirm


- **Type**: SwitchParameter
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [New-PrtgSensor]
## Synopsis
Create a new sensor 

## Syntax
```PowerShell
 New-PrtgSensor [-PrtgObject] <PSObject> [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### PrtgObject


- **Type**: PSObject
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


# [New-PrtgSnmpCpuLoadSensor]
## Synopsis
Create a new sensor 

## Syntax
```PowerShell
 New-PrtgSnmpCpuLoadSensor [-Name] <String> [-ParentId] <Int32> [[-Tags] <String>] [[-Priority] <Int32>] [[-Interval] <Int32>] [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### Name


- **Type**: String
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### ParentId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### Tags


- **Type**: String
- **PipelineInput**: false
- **Position**: 3
- **Required**: false


### Priority


- **Type**: Int32
- **DefaultValue**: 3
- **PipelineInput**: false
- **Position**: 4
- **Required**: false


### Interval


- **Type**: Int32
- **DefaultValue**: 60
- **PipelineInput**: false
- **Position**: 5
- **Required**: false


# [New-PrtgSnmpTrafficSensor]
## Synopsis
Create a new sensor 

## Syntax
```PowerShell
 New-PrtgSnmpTrafficSensor [-Name] <String> [-InterfaceNumber] <Int32> [-ParentId] <Int32> [[-Tags] <String>] [[-Priority] <Int32>] [[-Interval] <Int32>] [[-ChartType] <String>] [-ErrorOnDown] [-ShowErrors] [-ShowDiscards] [-ShowUnicast] [-ShowNonUnicast] [-ShowMulticast] [-ShowBroadcast] [-ShowUnknown] [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### Name


- **Type**: String
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### InterfaceNumber


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### ParentId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 3
- **Required**: true


### Tags


- **Type**: String
- **PipelineInput**: false
- **Position**: 4
- **Required**: false


### Priority


- **Type**: Int32
- **DefaultValue**: 3
- **PipelineInput**: false
- **Position**: 5
- **Required**: false


### Interval


- **Type**: Int32
- **DefaultValue**: 60
- **PipelineInput**: false
- **Position**: 6
- **Required**: false


### ChartType


- **Type**: String
- **DefaultValue**: Independent
- **PipelineInput**: false
- **Position**: 7
- **Required**: false


### ErrorOnDown


- **Type**: SwitchParameter
- **DefaultValue**: True
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### ShowErrors


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### ShowDiscards


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### ShowUnicast


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### ShowNonUnicast


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### ShowMulticast


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### ShowBroadcast


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### ShowUnknown


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Remove-PrtgObject]
## Syntax
```PowerShell
 Remove-PrtgObject [-ObjectId] <Object> [-WhatIf] [-Confirm] [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### ObjectId
TODO: document this; $ObjectID for this cmdlet can either be a single integer or a comma-separated string of integers to handle 
multiples



- **Type**: Object
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### WhatIf


- **Type**: SwitchParameter
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### Confirm


- **Type**: SwitchParameter
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Remove-PrtgSensorNumbers]
## Synopsis
Remove extra numbers from sensor names 

## Syntax
```PowerShell
 Remove-PrtgSensorNumbers [-ObjectId] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]   
```
## Description
Remove the extra numbers from the end of the sensor names.

## Examples 


###  Example 1 
```PowerShell
PS C:\>Get-PrtgGroups | ft
```
Where 2005 is the groupId from this list





###  Example 2 
```PowerShell
PS C:\>$DeviceList = Get-PrtgTableData devices -ObjectId 2005 -Column "objid"
```
Get the list of devices you want to clean up





###  Example 3 
```PowerShell
PS C:\>ForEach ($device in $DeviceList) { Write-Warning DeviceID $device ; Remove-PrtgSensorNumbers $device }
```
Execute the PRTG command




## Parameters
### ObjectId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### WhatIf


- **Type**: SwitchParameter
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### Confirm


- **Type**: SwitchParameter
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Rename-PrtgObject]
## Syntax
```PowerShell
 Rename-PrtgObject [-ObjectId] <Int32> [-NewName] <String> [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### ObjectId


- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### NewName


- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


# [Resume-PrtgObject]
## Synopsis
Resume-PrtgObject 

## Syntax
```PowerShell
 Resume-PrtgObject [-ObjectId] <Int32> [<CommonParameters>]   
```
## Description
See also Suspend-PrtgObject

## Examples 


###  Example 1 





## Parameters
### ObjectId
ID of the object to pause/resume



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


# [Set-PrtgError]
## Syntax
```PowerShell
 Set-PrtgError [[-PrtgErrorText] <String>] [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### PrtgErrorText


- **Type**: String
- **PipelineInput**: false
- **Position**: 1
- **Required**: false


# [Set-PrtgObjectGeo]
## Synopsis
set the geo location of an object 

## Syntax
```PowerShell
 Set-PrtgObjectGeo [-ObjectId] <Int32> [-Location] <String> [-Geo] <String> [<CommonParameters>]   
```
## Examples 


###  Example 1 
```PowerShell
PS C:\>Set-PrtgObjectGeo -ObjectId 6250 -Geo '-27.465358, 153.029785' -Location 'NextDC B1 Brisbane'
```
Sets Geo location of this group object to NextDC B1.




## Parameters
### ObjectId
ID of the object to set



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### Location
Name of the object's property to get



- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### Geo
Value to which to set the geo location property of the object



- **Type**: String
- **PipelineInput**: false
- **Position**: 3
- **Required**: true


# [Set-PrtgObjectProperty]
## Synopsis
Change properties of object 

## Syntax
```PowerShell
 Set-PrtgObjectProperty [-ObjectId] <Int32> [-Property] <String> [-Value] <String> [<CommonParameters>]   
```
## Description
Change properties of object

If $Property = 'priority', Set priority of an object (valid values are 1 to 5).

## Examples 


###  Example 1 
```PowerShell
PS C:\>Set-PrtgObjectProperty 2512 name newname
```






###  Example 2 
```PowerShell
PS C:\>Set-PrtgObjectProperty 2512 -Priority 4
```





## Parameters
### ObjectId
ID of the object to query



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### Property
Name of the object's property to get



- **Type**: String
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### Value
Value to which to set the property of the object



- **Type**: String
- **PipelineInput**: false
- **Position**: 3
- **Required**: true


# [Set-PrtgResult]
## Syntax
```PowerShell
 Set-PrtgResult [-Channel] <String> [-Value] <Object> [-Unit] <String> [-MaxWarn <String>] [-MinWarn <String>] [-MaxError <String>] [-WarnMsg <String>] [-ErrorMsg <String>] [-Mode <String>] [-ShowChart] [-SpeedSize <String>] [-VolumeSize <String>] [-DecimalMode <String>] [-Warning] [-ValueLookup <String>] [<CommonParameters>]   
```
## Examples 


###  Example 1 





## Parameters
### Channel


- **Type**: String
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### Value


- **Type**: Object
- **PipelineInput**: false
- **Position**: 2
- **Required**: true


### Unit


- **Type**: String
- **PipelineInput**: false
- **Position**: 3
- **Required**: true


### MaxWarn


- **Type**: String
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### MinWarn


- **Type**: String
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### MaxError


- **Type**: String
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### WarnMsg


- **Type**: String
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### ErrorMsg


- **Type**: String
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### Mode


- **Type**: String
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### ShowChart


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### SpeedSize


- **Type**: String
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### VolumeSize


- **Type**: String
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### DecimalMode


- **Type**: String
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### Warning


- **Type**: SwitchParameter
- **DefaultValue**: False
- **PipelineInput**: false
- **Position**: named
- **Required**: false


### ValueLookup


- **Type**: String
- **PipelineInput**: false
- **Position**: named
- **Required**: false


# [Suspend-PrtgObject]
## Synopsis
Suspend-PrtgObject 

## Syntax
```PowerShell
 Suspend-PrtgObject [-ObjectId] <Int32> [[-PauseLength] <Int32>] [[-PauseMessage] <String>] [<CommonParameters>]   
```
## Description
See also Resume-PrtgObject

## Examples 


###  Example 1 





## Parameters
### ObjectId
ID of the object to pause/resume



- **Type**: Int32
- **DefaultValue**: 0
- **PipelineInput**: false
- **Position**: 1
- **Required**: true


### PauseLength
Length of time in minutes to pause the object, $null for indefinite



- **Type**: Int32
- **PipelineInput**: false
- **Position**: 2
- **Required**: false


### PauseMessage
Message to associate with the pause event



- **Type**: String
- **DefaultValue**: Paused by PowerShell API
- **PipelineInput**: false
- **Position**: 3
- **Required**: false





