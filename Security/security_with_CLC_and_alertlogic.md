{{{
  "title": "Security with CenturyLink Cloud and AlertLogic Threat Manager",
  "date": "10-06-2015",
  "author": "Luis Cornejo",
  "attachments": [],
  "contentIsHTML": false,
  "sticky": false
}}}


**Introduction**|**Planing**|**Reference**
-----------------|------------|--------------
[Audience](#Audience)| [Deployment Scenarios](#Deployments)|
[Considerations](#Considerations)|
[Prerequisites](#Prerequisites)|
<BR>
<HR>

### Audience.

This article should assist individuals interested in data security and also IT professionals concerned about security threats and compliance. 

This guide is not intended to be exhaustive, but it may rather be considered general advice given that security standards and threats continuously evolve. We hope it provide a baseline in few areas of security as a starting point for considerations prior to any implementation.

As with other CenturyLink Cloud ecosystem partners, the content of this guide is focused on the gained advantages by the inclusion of third party products and services in combination with CenturyLink Cloud features. 

It is also intended to provide complementary measures to security policies, standards, and process developed in-house and it should not be considered a substitution of these.

This article touches on the following subjects:

**Category**|**Topics**
-------------|-----------------------------|
Security     |User access controls
|				  |Intrusion detection (IDS)
|				  |Log Management
|				  |Firewall rules & network zones

<BR>
### Considerations.

Information about AlertLogic security products and services, additional references, and how to contact or purchase AlertLogic can be found in our [Public Knowledge Base](../ecosystem-partners/marketplace-guides/getting-started-with-alert-logic-threat-manager-partner-template/).
<br>

AlertLogic's official documentation is available in their [Webhelp site](http://docs.alertlogic.com/).

#### Prerequisites.

* A CenturyLink Cloud account.
* An AlertLogic account activated with *Threat Manager*, *Log Manager* or both.
* Understanding of CenturyLink Cloud sub-account hierarchy for multi-tenant environments.


#### Compatibility.

At the time of this writing the AlertLogic agent supports:

* Windows Server: 2003 SP1 | 2008 | 2012.
* Debian Linux: 5.x | 6.x | 7.x
* Red Hat Enterprise Linux: 6.x | 7.x
* Ubuntu Linux: 10.x | 12.x | 14.x

Up to date OS support is available directly from AlertLogic [here.](http://docs.alertlogic.com/#docs/install_and_configure/agents/agentopsupp.htm)


<BR>
### What do AlertLogic products do?

AlertLogic's suite of products assist IT and security departments to detect, alert, store and correlate security related events occurring in applications and their underlying infrastructure. 

AlertLogic's detection abilities are based on thousands of matching signatures of known events. AlertLogic's NOC continually keeps adding signatures for new events as they are detected by hundreds of worldwide appliances or shortly after issued by the security community.

<BR>
### How does it work?

AlertLogic Threat manager and Log manager products work similarly within CenturyLink cloud. There are three required components to successfully benefit from AlertLogic's services:

**Component**|**Purpose**
-----------------|------------------------------
**Virtual Appliance**|Serves as a centralized collection point for security events reported by the protected hosts (threats and logs) and for management of the environment. The appliance can also provide signature updates and perform internal vulnerability assessments.
**Host Agent**|An individual software agent installed in each protected host, able to scan network packets and report threats that match AlertLogic's signatures and also can watch host logs and report events back to the appliance.
**AlertLogic Portal**|A centralized UI where a virtual appliance can report events to and where all collected security information is consolidated. [Access it here (account is required).](https://invision.alertlogic.net/)

<BR>
Once set, each protected host (VM or bare metal) will be running an AlertLogic agent that is capable to examine network traffic traversing the NIC. The agent listens for all traffic and compares to a local signature database that is regularly updated.

Upon matching a signature, the agent triggers and event and reports it to the AlertLogic virtual appliance that the agent was provisioned on. The appliance maintains track of these events and updates AlertLogic's NOC over a secure connection where the events are parsed and logged in the AlertLogic Portal platform.

The virtual appliance manages the register agents and is also able to push updates, whether these are new signatures or software updates.


<BR><HR>

### Deployment Scenarios

#### -Single tenant

**Situation:** A single application or platform that is self-contained and self sufficient, where all elements of the application are deployed in one account and no network connections to other accounts or sites exist.

![IDS single tenant](../images/alertlogic/tmgr_net.png)

#### -Multi-tenant, shared VLANs

**Situation:** 

**Pros**|**Cons**
--------|----------
Simpler network topology.|Traffic across accounts is visible.
A single appliance may be used.|The appliance may reach capacity.
Least complexity of firewall rules.|

![IDS multitenant](../images/alertlogic/subacct_shared.png) 

#### -Multi-tenant, private VLANs using inter-account firewall rules

**Situation:** 

#### -Hybrid: cloud / on-premise

**Situation:** 

<BR><HR>
### Responsibilities

Task|Responsible|Notes
------|-------------|-------
Provision AlertLogic Account|Customer, AlertLogic Sales| Customers engage AlertLogic sales directly to select products and level of access to their features.
Pre-deployment Planning|Customer, CenturyLink|  
Deploy virtual appliance|CenturyLink|The customer must request deployment via service task


<BR><HR>
### Resources.

#### Vendor documentation.

[AlertLogic Threat Manager Documentation](http://docs.alertlogic.com/#docs/threat_manager/about_threat_manager.htm%3FTocPath%3DThreat%2520Manager%7C_____0)

[AlertLogic Log Manager Documentation](http://docs.alertlogic.com/#docs/log_manager/about_log_manager.htm#get%3FTocPath%3DLog%2520Manager%7C_____0)


#### [AlertLogic Downloads *(Requires access to AlertLogic)*](https://invision.alertlogic.net/tm/support/downloads)


