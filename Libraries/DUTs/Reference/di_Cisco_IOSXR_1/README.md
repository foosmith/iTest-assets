# project://di_Cisco_IOSXR_1
1 QuickCall Library in project://di_Cisco_IOSXR_1:
## project://di_Cisco_IOSXR_1/session_profiles/IOS_XR_SSH_quickcall_library.fftc (project://di_Cisco_IOSXR_1/session_profiles/IOS_XR_SSH_quickcall_library.fftc)

### AddInterfaceToIsis
add the specified interface to isis
Rerturns block JSON response:
success - true on successful config change, false otherwise

Argument | Description
------------ | -------------
interface | The interface to add to isis
group_name | Name of existing ISIS group 
isis_proc_id | ISIS process ID to add interface to
### ChangeIsisMetric
This quick call will change the isis metric of an interface on an router. 

config t
router isis 1 
interface bundle-ether 95
address-family ipv4 unicast 
metric 10
address-family ipv6 unicast
metric 10
commit
end

Argument | Description
------------ | -------------
isis_proc_id | ISIS process id
interface_name | This is the interface on which the ISIS metric is being changed. 
address_family | Address family of the interface. 
metric_value | Value to set the interface metric to
### ClearInterfaceArpCache
Clear the ARP cache on a Cisco IOS XR device.

Argument | Description
------------ | -------------
interface | Name of interface to clear ARP on
### ClearInterfaceCounters
Clear interface counters for one interface or all

Argument | Description
------------ | -------------
interface | Name of interface to clear counters on. 
NOTE: If not given, will clear counters on all interfaces.
### ClearMplsForwardingCounters
Clear global MPLS forwarding counters
### ClearRsvpCounters
Clear RSVP forwarding counters for a specific type

Argument | Description
------------ | -------------
target | Type of RSVP counters to clear. Options include:
authentication
all
chkpt
events
messages
oor
prefix-filtering
### ClearPbrCounters
Clear PBR counters on a specific interface

Argument | Description
------------ | -------------
interface | Interface to be cleared
### ConfigureClassMap
Add or remove class-map in the global config

Argument | Description
------------ | -------------
class_map_name | Enter class map name you want to use. Valid examples:
inet-classifier-af1
type traffic match-any PBTS-classifier-FC1
unconfigure | Used for unconfiguration
all - to unconfigure the class
parameter - to unconfigure a specific parameter
match_value | Used to configure match value. Valid examples:
dscp <dscp_value>
vlan <vlan_value>
### ConfigureExplicitPaths
Add or remove explicit path to global config

Argument | Description
------------ | -------------
path_name | user given name for path
unconfigure | Values:
\t- null
\t- entry - unconfigure one entry
\t- path - unconfigure the entire path
index_list | Note: Use index_list along with path_type_list and ip_address_list

Ex: For index_list "10 20" ; path_type_list "{next-address strict} exclude-srlg" ; ip_address_list "1.1.1.1 2.2.2.2"
Config resulted will be:
\texplicit-path name NAME
\t\tindex 10 next-address strict ipv4 unicast 1.1.1.1
\t\tindex 20 exclude-srlg ipv4 unicast 2.2.2.2
type_list | Note: Use index_list along with path_type_list and ip_address_list

Ex: For index_list "10 20" ; type_list "{next-address strict} exclude-srlg" ; ip_address_list "1.1.1.1 2.2.2.2"
Config resulted will be:
\texplicit-path name NAME
\t\tindex 10 next-address strict ipv4 unicast 1.1.1.1
\t\tindex 20 exclude-srlg ipv4 unicast 2.2.2.2
ip_address_list | Note: Use index_list along with path_type_list and ip_address_list

Ex: For index_list "10 20" ; path_type_list "{next-address strict} exclude-srlg" ; ip_address_list "1.1.1.1 2.2.2.2"
Config resulted will be:
\texplicit-path name NAME
\t\tindex 10 next-address strict ipv4 unicast 1.1.1.1
\t\tindex 20 exclude-srlg ipv4 unicast 2.2.2.2
ip_ver | ipv4 or ipv6
### ConfigureGroupInterface
Add, edit or remove an interface group

Argument | Description
------------ | -------------
group_name | Name of interface group to modify
record_route | Values:
\t- null
\t- any for configuring
forward_class | Set interface forward class
interface_status | Parameter to modify the status of the interface.
 Usage : 
shut  - to disable interface
no shut - to enable interface 
   
priority_setup | give this argument a numerical value to set the "priority setup" for the tunnnel
ex: setup priority is 1 and hold priority is 2
priority 1 2
priority_hold | give this argument a numerical value to set the "priority hold" for the tunnel
ex: setup priority is 1 and hold priority is 2
priority 1 2
autoroute_metric | give this argument the value yes in order to configure
Ex:
R(...)# autoroute announce
R(...auto-aa)#metric 5

use unconfigure =null for configuration
use unconfigure =yes (or anything else) for unconfiguration
metric | this is an argument used in the command "autoroute announce" 
give this argument a numerical value - the metric you want to use!
ex:
R(...)# autoroute announce
R(...auto-aa)#metric 5
autoroute_include_ipv6 | Ex:
R(...)# autoroute announce
R(...auto-aa)#   include-ipv6

use unconfigure =null for configuration
use unconfigure = yes (or anything else) for unconfiguration
logging_events_lsp_list | Give this argument a value like: reroute, bw-change, reoptimize, switchover etc


Ex:
logging_events_list " lsp-status reroute lsp-status bw-change"

  logging events lsp-status reroute
  logging events lsp-status bw-change
etc

use unconfigure =null for configuration
use unconfigure = yes (or anything else) for unconfiguration
log_events_pcalc_failure | give this argument the value yes in order to configure "logging events pcalc-failure"

give this argument the value no, and unconfig yes in order to configure: "no logging events pcalc-failure"
signalled_bw | ex: 
signalled-bandwidth 200
give signalled_bw a value in order to configure : ex: 200 or 300 etc

use unconfigure =null for configuration
use unconfigure = yes (or anything else) for unconfiguration
soft_preemption | use a value different then null in order to configure soft-preemption
 soft-preemption
use unconfigure =null for configuration
use unconfigure = yes (or anything else) for unconfiguration
fast_reroute_protect | Give this argument only the values: node or  bandwidth
ex:
fast-reroute protect node

use the $fast-reroute protect variable to configure node or  bandwidth ex: "fast-reroute protect node" or "fast-reroute protect bandwidth"

use unconfigure =null for configuration
use unconfigure = yes (or anything else) for unconfiguration
ipv6 | If set to a valiue other than "null" will configure ipv6. If unconfigure is also set, will remove ipv6. 
log_events_link_status | give this argument the value yes in order to configure:
logging events link-status

give this arg the value yes, and unconfigure yes in order to:
no logging events link-status
interface_name | Name of interface to modify within group
unconfigure | Value:
\t- null
\t- interface - Delete the entire interface
\t- parameter - remove partial config. For example, setting the ipv4_unnumbered arugment to an interface name with unconfigure set to "parameter" will remove ipv4 unnumbered from that interface.
ipv4_unnumbered | Supply an Interface name to configure or unconfigure ipv4 unnumbered.
Ex: loopback0
load_interval | New load interval to set. Will remove load interval if this argument is not "null" and unconfigure is set.
auto_bw_limit_min | New value for min auto bandwidth limit. Will remove min auto bandwidth limit if this argument is not "null" and unconfigure is set.
auto_bw_limit_max | New value for max auto bandwidth limit. Will remove max auto bandwidth limit if this argument is not "null" and unconfigure is set.
auto_bw_adj_th_percent | New value for auto bandwidth adjustment threshold. Will remove auto bandwidth adjustment threshold if this argument is not "null" and unconfigure is set.
auto_bw_adj_th_min | 
auto_bw_application | New value for auto bandwidth application. Will remove auto bandwidth application if this argument is not "null" and unconfigure is set.
path_option | Path option ID.
Example: 10
path_option_dynamic | Example: isis 1 level 2
path_option_explicit_name | Example: Name of the explicit-path
autoroute | give this argument the value: announce



### ConfigureGroupRouter

Argument | Description
------------ | -------------
group_name | Specifies the group name. Eg: ISIS-METRICS
protocol | Specifies the group type. Options:
 - isis
process_id | Specifies the process-id for the protocol in regexp form. Eg: '1'
unconfigure | Unconfigures. Options include
- all
- parameter - remove partial config. For example, setting the interface arugment to an interface name with unconfigure set to "parameter" will remove the interface from the router.
interface | Describes the interface in Regex format. Eg: 'TenGigE.*'
address_family | Eg: ipv4 unicast
metric | Set the metric. Eg: 12
### ConfigureIsis
Configure or remove ISIS routing

Argument | Description
------------ | -------------
process_id | Defines the process ID (Eg: 1)
apply_group_remove | Remove group from apply-group
### ConfigureLldp
Configure or remove LLDP in the global config

Argument | Description
------------ | -------------
holdtime | Cofigure the holdtime
unconfigure | Options:
all - removes LLDP from global config
holdtime - removes holdtime, leaves LLDP enabled
### ConfigureMplsTunnelFrr
Configure/Remove a path-option for an MPLS TE Tunnel

Argument | Description
------------ | -------------
group_name | Use this argument to specify a configuration group, e.g. "GOOGLE-BACKBONE-MPLS"
Leave as "none" to not confiugre a group name
interface | Interface name and number , e.g.:
tunnel-te1
'tunnel.*'
...if you are using regex-based group configuration
frr_action | Supported actions are:
protect
frr_protection_type | Use together with frr_action = protect

Supported values are:
node
bandwidth
...or both values in a space separated string, in any order.
remove_configuration | Remove FRR configuration if this parameter is set to yes
### ConfigureRsvp
Configure RSVP in the global config

Argument | Description
------------ | -------------
apply_group | Configuration group name you wish to apply to the interface. 
Use the value "wipe" to remove all apply groups from the interface.

Use the value "remove <apply-group-names>" to remove a list of apply groups from the interface.

Use the value "append <apply-group-names>" to append a list of apply groups to the interface.
### ConfigureServicePolicy
Add or remove a service policy in the global config

Argument | Description
------------ | -------------
apply_order | Defines the apply order. Options:
pbr qos
qos pbr
unconfigure | unconfigures the service policy. Options:
-all
### CreateRoutePolicy
Quickcall used to configure a BGP peer.

Argument | Description
------------ | -------------
route_policy | Name of policy to create or delete
local_pref | Specify the value for set local preference
pass | 
delete_route_policy | Change to "yes" to delete route policy named by $route_policy
### ConfigureInterfaceAcl
Add or remove an ACL from an interface

Argument | Description
------------ | -------------
interface | Name of interface to modify
acl_name_add | Name of ACL to add
acl_name_remove | Name of acl to remove
### ConfigureInterfaceIP
Configure or remove an IPv4 address on an interface. 

Argument | Description
------------ | -------------
ipv4_address | If given, will configure IPv4 address on the interface. If left as defualt, will remove the IPv4 address from the interface. 
netmask_v4 | Required if supplying IPv4 address. Integer.
Length of v4 subnet mask to apply to the interface. 
ipv6_address | If given, will configure IPv6 address on the interface. If left as defualt, will remove the IPv6 address from the interface. 
netmask_v6 | Required if supplying IPv4 address. Integer.
Length of v6 prefix to apply to the interface. 
interface | Name of interface to alter
### ConfigureInterfaceMTU
Configure MTU size on an interface

Argument | Description
------------ | -------------
interface | Name of the interface to alter.
new_mtu | New MTU size to apply.
### CreateAcl
Create an Access Control List on the global config

Argument | Description
------------ | -------------
acl_name | Name to give to newly created ACL
deny_string | String to be placed on the 'deny' line of the ACL. Example "tcp any any eq www log"
permit_string | String to be placed on the 'permit' line of the ACL. Example "ipv4 any any"
### ConfigureHostname
Change the hostname 

Argument | Description
------------ | -------------
hostname | New value for the hostname
### EnterConfigMode
Enter config mode on an IOS XR device. Mainly to be used by other quick calls.

Argument | Description
------------ | -------------
interface | Optional. Interface to configure. 
### ExitConfigMode
Commit changes and exit config mode. Used mainly by other quick calls.
### GetArpTable
Returns the complete response to 'show arp'
### GetApplyGroupList
Returns a list of apply-groups

Argument | Description
------------ | -------------
include | Type of groups to include in list. 
Options: all|global|non-global
### GetBgpPaths
Gets the bgp scale and returns the number of active paths and total paths

Response: block JSON string

Argument | Description
------------ | -------------
type | Type of BGP paths to get
Valid values:

IPv4 Unicast
IPv6 Unicast
Total      (default)
### GetBgpInfo
Get info from BGP table

Return:
block JSON string

Argument | Description
------------ | -------------
type | ipv4 or ipv6
ipAddress | ip address
### GetBundleInterfaces
Get the list of interfaces belonging to this bundle

Returns:
A table of the interfaces and the corresponding states

Argument | Description
------------ | -------------
bundle | The bundle for which to retrieve the list of interfaces
### GetCefTables
Get the cef tables for the specified ip

Argument | Description
------------ | -------------
ipAddress | The ip address for which to find cef tables
### GetExplicitPaths
Returns configured explicit paths on the router. 
### GetInterfaceErrorCounts
Get all error counters on a specified interface. Returns a block JSON response'

Argument | Description
------------ | -------------
interface | provide the interface to run the command
### GetInterfaceInfo
Returns information about an interface. Uses 30 second rates for return data. Returns a block JSON string.

Argument | Description
------------ | -------------
interface | the name of the interface
### GetLabelTraffic
For the specified label, return the traffic information. Returns a block JSON string.

Argument | Description
------------ | -------------
label | The numeric value of the label
### GetMplsTunnelsSummary
Get summary information for tunnels

Returns:
 
block
### GetCpuUsageTable
Returns entire output of 'show process cpu' command
### GetInterfaceCounters
Get interface coutners shown in the 'show interface detail' command.

Argument | Description
------------ | -------------
interface | Name of interface to get counter info from
### GetNdTable
Returns the entire response to 'show ipv6 neighbors'
### Ping
Ping an IPv4 or IPv6 address.

Argument | Description
------------ | -------------
ip_address | IPv4 or IPv6 address to ping. 
### RemoveApplyGroup
Remove apply group from global config

Argument | Description
------------ | -------------
groupName | Name of apply-group to remove 
### RemoveGroup
remove an interface group

Argument | Description
------------ | -------------
groupName | Name of group to remove
### RemoveAcl
Remove an ACL from the global config

Argument | Description
------------ | -------------
acl_name | Name of ACL to remove
### RestartProcess
Restart a process

Argument | Description
------------ | -------------
process | Job ID <0-4294967295> or name of process to restart
