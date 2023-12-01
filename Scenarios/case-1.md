# Case 1: Metal
### Daniel is the Chief Innovation Officer at Metal, an independent music label based out of RTP, North Carolina. As part of an automation initiative, he has tasked his engineering teams with adopting Infrastructure as Code practices.
### You've been hired as a consultant to verify and assist in their IaC goals. Your first task is to help Metal Engineering understand how networking infrastructure can be modeled and represented. 
---
1. (**FREE RESPONSE**) In a few sentences, describe some benefits of 	Infrastructure as Code.


<br><br>

2. Below is an example XML script. Answer the following questions by referring to the code.
```xml
<?xml version="1.0" encoding="UTF-8"?>
<interface xmlns="ietf-interfaces">
	<name>GigabitEthernet2</name>
	<description>Wide Area Network</description>
	<enabled>True</enabled>
	<ipv4>
		<address>
			<ip>172.16.0.2</ip>
			<netmask>255.255.255.0</netmask>
		</address>
	</ipv4>
</interface>
```

- (**Multiple Choice**) What YANG model is the XML instance referencing?
  
a.  UTF-8

b.  Gigabit Ethernet 2

c.  ietf-interfaces

d.  interfaces


<br>

- (**Free Response**) Complete the following Cisco IOS XE command to manually execute the representation defined in the XML instance. *Note: As of November 2023 the DevNet Associate exam does not require labs... challenge yourself!*
```ios-xe
Router> enable
Router# configure terminal
Router(config)# [TODO-1]
Router(config-if)# description "Wide Area Network"
Router(config-if)# ip address [TODO-2] [TODO-3]
Router(config-if)# no [TODO-4]
```

<br><br>

- (**Drag and Drop**) Complete the following tree representation of the above YANG model. *Use the options below to fill in each TODO. Note that not all options are used.*
```
+--rw interfaces
   +--rw [TODO-1]* [name]
      +--rw name  			[TODO-2]
      +--rw description?  		string
      +--rw type?  			identityref
      +--rw [TODO-3]  			boolean
      +--rw ipv4
	 +--rw [TODO-4]
            +--rw ip  			string
            +--rw netmask 		string
```
|**OPTIONS** |||
|--|--|--|
| ietf-interfaces | interface  | integer |
| string | Wide Area Network | enabled |
| UTF-8 | True | address |

<br><br>

- (**Drag and Drop**) Translate the XML script to its corresponding JSON equivalent. *Use the options below to fill in each TODO. Note that not all options are used.*
```yaml
{
  "ietf-interfaces:interface": {
    "name": "TODO-1",
    "TODO-2": "Wide Area Network",
    "enabled": "TODO-3",
    "ipv4": {
      "TODO-4": [
        {
          "TODO-5": "172.16.0.2",
          "netmask": "TODO-6"
        }
      ]
    }
  }
}			
```
|**OPTIONS** ||||
|--|--|--|--|
| GigabitEthernet2 | Interface:GigabitEthernet2  | Boolean |255.255.255.0|
| description | status | 1 |/24|
| address | ip-address | ip |True|
