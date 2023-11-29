# Case 1: Metal
### Daniel is the Chief Innovation Officer at Metal, an independent music label based out of RTP, North Carolina. As part of an automation initiative, he has tasked his engineering teams with adopting Infrastructure as Code practices.
### You've been hired as a consultant to verify and assist in their IaC goals. Your first task is to help Metal Engineering understand how networking infrastructure can be modeled and represented. 
---
1. (**FREE RESPONSE**) In a few sentences, describe some benefits of Infrastructure as Code.

Infrastructure as Code is the managing and provisioning of infrastructure through code instead of through manual processes.
With IaC, configuration files are created that contain your infrastructure specifications, which makes it easier to edit and distribute configurations. 
It also ensures that you provision the same environment every time. Manual provisioning is often prone to human error! 
By codifying and documenting your configuration specifications, IaC aids configuration management and version control, which helps you to avoid undocumented, ad-hoc configuration changes.


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

**c.  ietf-interfaces**

d.  interfaces

The correct answer is **c**. The YANG model is referenced within the namespace definition ```xmlns="ietf-interfaces"```.


- (**Free Response**) Complete the following Cisco IOS XE command to manually execute the representation defined in the XML instance. *Note: As of November 2023 the DevNet Associate exam does not require labs... challenge yourself!*
```ios-xe
Router> enable
Router# configure terminal
Router(config)# interface GigabitEthernet2
Router(config-if)# description "Wide Area Network"
Router(config-if)# ip address 172.16.0.2 255.255.255.0
Router(config-if)# no shutdown
```

- (**Drag and Drop**) Complete the following tree representation of the above YANG model. *Use the options below to fill in each TODO. Note that not all options are used.*
```
+--rw interfaces
  +--rw interface* [name]
    +--rw name                string
    +--rw description?        string
    +--rw type?               identityref
    +--rw enabled             boolean
    +--rw ipv4
      +--rw address
        +--rw ip              string
        +--rw netmask         string
```


- (**Drag and Drop**) Translate the XML script to its corresponding JSON equivalent. *Use the options below to fill in each TODO. Note that not all options are used.*
```yaml
{
  "ietf-interfaces:interface": {
    "name": "GigabitEthernet2",
    "TODO-2": "Wide Area Network",
    "enabled": "True",
    "ipv4": {
      "address": [
        {
          "TODO-5": "172.16.0.2",
          "netmask": "255.255.255.0
        }
      ]
    }
  }
}			
```
