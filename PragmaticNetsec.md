
#Executive Guide to Pragmatic Network Security Management

##The Demise of Network Security Has Been Greatly Exaggerated

DLP, IPS, NGFW, WAF. Chief Information Security Officers today suffer no shortage of network security tools to protect their environments, but most CISOs we talk with struggle to implement and maintain an effective network security program. They tell us it isn't a lack of technologies or even necessarily resources (not that there are ever enough), but the inherent difficulties in defending a large, amorphous, business-critical asset with tendrils throughout the organization. It's never as simple as magazine articles and conference presentations make it out to be.

Managing network security at scale is not easy, but the organizations that do it the best tend to follow a predictable, repeatable pattern. This paper distills those lessons into a pragmatic process designed for larger organizations and those with more complicated networks (such as medium-sized businesses with multiple locations). We won't make the false claim that our process is magical or easy, but it's certainly _easier than many alternatives_. Even if you only pick out a few tidbits, it should help you refine and operate your network security more efficiently.

The network is the aspect of our infrastructure that ties everything else together. The more we can do to efficiently and effectively secure it, the better.

###Why Network Security Is So Darn Difficult

Networks and endpoints are the two most fundamental pieces of our IT infrastructure, yet despite decades of advancements they still consume a disproportionate amount of our security resources. First the good news -- we are *far* more resilient to network attacks than even five years ago. The days of a Internet-wide worms knocking down enterprises while script kiddies deface websites are mostly in the past. But every CISO knows establishing and maintaining network security is a constant challenge, even if they can't always articulate why. We have narrowed down a handful of root causes, which this Pragmatic process is designed to address:

* _Security and operations are divided_. IT Operations is responsible for and manages the network, servers, endpoints, and applications, and information security is responsible for defending everything. Basically, security protects the enterprise from the *outside* -- lacking insight into what is being protected, where it is, and how everything connects together. In many cases security doesn't even know how all the pieces of the network are connected, but is still expected to manage firewall rules to protect it. Many of our recommendations are designed to bridge this divide without throwing away traditional organizational boundaries.
* _Networks are dynamic and complex_. Not only are new assets constantly joining and leaving the network, but its structure is never static, especially for larger organizations.
    * Organic growth. All networks grow over time. Perhaps it's a new office, extending a WiFi network, or an extra switch or router in the datacenter. Not all of these have major security implications but they add up over time.
    * Mergers and acquisitions require blending resources, technologies, and different configurations.
    * New technologies with different network requirements are constantly added, from a new remote access portal to an entire private cloud.
    * We mix and match various security tools, often with overlapping functionality. This is sometimes a result of different branches of the company operating partially or completely autonomously, and other times results from turnover, project requirements, or keeping auditors happy.
* _Needs change over time_. Many organizations today are working on consolidating network perimeters, compartmentalizing internal networks, adding application awareness, expanding egress monitoring and filtering for breach and infection defenses, or adapting the network for cloud computing and eventually SDN. Network and network security technologies evolve to meet new business needs and evolving threats.

Our networks are large and complex, sometimes even when our organizations aren't. They change constantly, as do the assets connected to them. Security doesn't manage this infrastructure, but is tasked with protecting it. _Network Security Management is about improving both security and efficiency to keep up._

###From Blocking and Tackling to Integrated Defense

Our primary goal is to adopt processes that are flexible enough to account for an ever-changing network environment, while avoiding the constant firefighting that is so inefficient. The key isn't any particular technology or security trick, but better integrating defenses into day-to-day management of the enterprise. What makes it pragmatic? _The fact that the process is designed to work in the real world, without gutting or stumbling over organizational and bureaucratic divisions._

We get it -- even if you are the CEO, there are limits to change. We have collected the best practices we have seen work in the real world, lining them up in a practical and achievable process that accounts for real-world restrictions. Our next sections will dig into the process. As we said earlier, pick and choose those which work for you.

##The Pragmatic Process

As mentioned in the previous section, this process is designed primarily for more complex networks, and takes into account real-life organizational and technological complexities.

Here is the outline, followed by the details:

1. Know your network.
1. Know your assets.
1. Know your security.
1. Map the topology.
1. Prioritize and fix.
1. Monitor continuously.
1. Manage change and build workflows.

The first five steps *establish the baseline*, and the next two *manage the program*, although you will need to periodically revisit previous steps to ensure your program stays up to date as the business evolves and risks change.

###Know Your Network

You can't secure what you don't know, but effectively mapping a network topology -- especially for a large network -- can be daunting. Many organizations *believe* they have accurate network topologies, but they are rarely correct or complete -- for all the reasons in the previous section. The most common problem is simply failure to keep up-to-date. Topology maps are produced occasionally as needed for audits or projects, but rarely maintained.

The first step is to work with Network Operations to see what they have and how current it is. Aside from being politically correct, there is also no reason not to leverage what is already available. Position it as "We need to make sure we have our security in the right places," rather than "We don't trust you." Once you get their data, evaluate it and decide how much you need to validate or extend it.

There are a few ways to validate your network topology, and you should rely on automation when possible. Even if your network operations team provides a map or [CMDB](http://en.wikipedia.org/wiki/Configuration_management_database), you need to verify that it is current and accurate. One issue we see at times is that security uses a different toolset than network operations.

*Security scanners* use a variety of techniques to probe the network and discover its structure, but standard security scanners (including vulnerability assessment tools) aren't necessarily well suited to building out a complete network map.

Network operations teams have their own mapping tools, some of which use similar scanning techniques, but add in routing and other analyses that rely on management-level access to the routers and network infrastructure. These tools tend to rely more on trusting the information provided to them and don't probe as heavily as security tools. They also aren't generally run organization-wide on a continuous basis, but are instead used as needed for problem-solving and planning.

<!-- The security team needs to know the network structure to properly position defensive assets. Unless you are completely confident that your operations teams are providing current and complete data continuously, you need to perform your own network mapping, not just standard security scanning. -->

###Know Your Assets

Once you have a picture of the network you start evaluating the assets on it: servers, endpoints, and other hardware. Security tends to have better tools and experiences for scanning and analyzing assets than underlying network structure, especially for workstations.

Depending on how mature you are at this point, either prioritize your scanning to particular network segments or use the information from the network map to target weak spots in your analysis. Endpoint tools such as configuration/patch management or endpoint protection platforms offer some information, but you also need to integrate a security scan (perhaps a vulnerability assessment) to identify problems.

As before, this really needs to be a continuous process using automated tools. You also need a sense of the importance of the assets, especially in data centers, so you can prioritize defenses. This is a tough one, so make your best guesses if you have to -- it doesn't need to be perfect.

###Know Your Security

You need to collect detailed information on three major pieces of network security:

* Base infrastructure security. This includes standard perimeter security, and anything you have deployed internally to enforce any kind of compartmentalization or detection. Think firewalls (including NGFW), intrusion detection, intrusion prevention, network forensics, Netflow feeds to your SIEM, and similar. Things designed primarily to protect the core network layer. Even network access control, for both of you using it.
* Extended security tools. These are designed to protect particular applications and activities, such as your secure mail gateway, web filter, web application firewalls, DLP, and other "layer 7" tools.
* Remote access. Security tends to be tightly integrated into VPNs and other remote access gateways. These aren't always managed by security, but unlike network routers they have internal security settings that affect network access.

For each component collect location and configuration. You don't need all the deep particulars of a WAF or DLP (beyond what they are positioned to protect), but you certainly need complete details of base infrastructure tools. Yes, that means every firewall rule. Also determine how you manage and maintain each of those tools. Who is responsible? How do they manage it? What are the policies?

###Map the Topology

This is the key step where you align your network topology, assets (focusing on bulk and critical analysis, not every single workstation), and existing security controls. There are two kinds of analysis to then perform:

* A _management analysis_ to determine who manages all the security and network assets, and how. Who keeps firewall X up and running? How? Using which tool? Who manages the network hardware that controls the routing that firewall X is responsible for? Do you feed netflow data from this segment to the SIEM? IDS alerts? The objective is to understand the technical underpinnings of your network security management, and the meatspace mapping for who is responsible.
* A _controls analysis_ to ensure the right tools are in the right places with the right configurations. Again, you probably want to prioritize this by assets. Do you use application-aware firewalls (NGFW) where you need them? Are firewalls configured correctly for the underlying network topology? Do you segment internal networks? Capture network traffic for detecting attacks in the right places? Are there network segments or locations that lack security controls because you didn't know about them? Is that database really safe behind a firewall, is or it totally unprotected if a user clicks the wrong link in a phishing email?

The first analysis focuses on implementation of management processes and workflow. Sure, everyone has policies, but how are the actual infrastructure and defenses managed? Who is responsible for what and where does the data flow? The second analysis is all about preventing and detecting attacks and aligning controls. Are the right defenses configured properly in front of the right assets?

Once you map the assets to the network topology, to the security defenses, to the management infrastructure, two pictures emerge -- how your defenses are really aligned and how you manage them.

###Prioritize and Fix

By now you have a deep understanding of your network topology, a decent understanding of where important things are on the network, and a solid idea of how your security is configured around and within it. Now it is time to start fixing things. And remember, we are focusing on *network security* today, not the endless list of other controls you can bring to the table. Your goal is to improve how you manage your security over time, not just plug a few holes until you need to start all over again.

This involves:

* Repositioning network security tools. Ensure you have the correct preventative or monitoring control in the right physical location. This isn't about buying new things, but understanding and best using the ones at your disposal.
* Reconfiguring network security tools. Adjust rules and configurations to provide the desired protection.
* Consolidating network security management so you can maintain visibility and implement changes more efficiently in the future.
* Position new tools as needed. You may already be using application-aware network security, egress monitoring, command and control monitoring, DDoS protection, cloud web filtering, and malware gateways. But if not you now have much better information for integrating them effectively into your program, and positioning and configuring them.

Right now we are still in the "initial fix" phase. In a moment we will discuss the continuous change management phase, where you focus on ensuring things never get so out of sync again. Most organizations fix some immediate things while they begin adjusting their management processes and workflow. There is no reason you have to hop through these steps one at a time.

###Continuously Monitor

This phase is they key to not needing to start all over again in a year, after everything gets out of sync again. We have moved past *baselining* into *managing the program*. There are four key pieces to keep track of:

1. Network topology changes. Sometimes these are small changes such as a new routing rule, while other times it might be addition of an entire new large network due to an acquisition. Security can monitor for these themselves or establish stronger collaborative workflows with network operations. Regardless, topology needs to be revalidated periodically to catch errors and omissions. You can use the same tools you used to build and validate your initial topology map, but now on a continuous or periodic basis, in addition to passive network monitoring tools that track live traffic.
1. Asset changes. If your servers, workstations, and other IT assets aren't moving around on pretty much a daily basis, odds are you are out of business. Security scanners, especially vulnerability scanners, are your tool of choice here.
1. Network security tool changes, including both uses and configurations, which is why we emphasized consolidating network security management infrastructure.

You will notice we skipped the part about *monitoring for bad guys*. That's because this report is focused on managing your overall program, not the details of daily defenses and incident response. It goes without saying, but we'll say anyway, that continuous security monitoring also includes extensive monitoring of network activity. That's why we spend so much time determining the best places to monitor and defend, and the best tools and configurations for the job.

The last piece of this phase is creating reports for auditors and executives. This is essential to meet compliance obligations and demonstrate your value to the rest of the organization. Ideally you can quickly create these reports without undue effort because you already have all the required data, constantly updated and accessible.

###Manage Change and Build Workflows

This is the most important phase of the entire process. Until now you have mostly focused on understanding your infrastructure and developing the security controls around it. But this is impossible to maintain unless security works more closely with both IT operations and various business units. The key is not only to refine internal processes, but to create *minimal-friction workflows* for working with the rest of the organization. The easier it is for *them* to go through an approved process, the less likely they are to try and circumvent it.

And the more you can automate this, including ongoing data gathering to detect the details and implications of changes, the better.

In this section we will cover the security change management process, and in the next section we will offer examples of common workflows for coordinating with other areas. For detailed processes for network security operations, we recommend our own [Network Security Operations Quant Report](https://securosis.com/Research/Publication/network-security-operations-quant-report).

* **Trigger:** A change can be a formal request from the outside, internal updates, or a change in the operating environment (such as a routing change detected by security, which didn't go through a change request process). Ideally everything runs through the approval process, but even the best-run organizations need to deal with out-of-process changes they detect.
* **Process change request and authorize:** Examine the unapproved change to determine the security response, or process the internal or external change request. Determine the requirements, impact, security risks, and priority, then slot the change into a maintenance window. Priority reflects both business and security needs, especially when threats are a factor.
* **Test and approve:** This step includes development of test criteria, any required testing, result analysis, and approval of the signature or rule change for release once it satisfies requirements.
* **Deploy and confirm:** Deploy and verify that changes were successful, including both installation and operation. This might include use of vulnerability assessment tools or application test scripts to ensure there is no disruption of production systems or attack surface added as a result of the change.
* **Audit/validate:** The full process of making a change encompasses more than merely having the operations team confirm it during the Deploy step -- another entity (internal or external, but not part of the ops team) should audit it as well to provide separation of duties. This entails validating the change to ensure policies were properly updated and matching it against a specific request. This closes the loop to make sure there is documentation (and an audit trail) for every change.
* **Emergency updates:** In some cases, including data breach lockdowns and imminent or active zero-day attacks, a change to the network security device's configuration must be made immediately. An 'express' process should be established and documented in advance as an alternative to the normal full change process, ensuring authorized approval for emergency changes, as well as a rollback capability in case of unintended consequences.

##Workflows: from Sec and Ops to SecOps

Even mature organizations occasionally struggle to keep security aligned with infrastructure. Managing changes at scale is never easy, and something is always bound to slip through the cracks. But low-friction processes that don't overly burden other areas of the enterprise reduce both errors and deliberate circumvention.

Frequently the problem manifests as a lack of communication between network security and network operations. Not out of antagonism but simply due to different priorities, toolsets, and issues to manage on a day to day basis. A seemingly minor routing change, or the addition of a new server, can quietly expose the organization to new risks if security defenses aren't coordinated. On the other hand, security can easily break things and create an operational incident with a single firewall rule change.

Efficient programs don't just divide up operational responsibilities -- they implement workflows where each team does what they are best at, while still communicating cleanly and effectively to each other. Security is best at understanding what needs to be protected and how, while operations is best at keeping it running. Here are examples of four integrated operations workflows:

* **Network topology changes:** Changes to the topology of the network have a dramatic impact on the configuration of security tools. The workflow consists of two tracks -- *approved* changes and *detected* changes. For approved changes the network team defines the change and submits it to security for review. Security analyzes it for impact, including any risk changes and required security updates. Security then approves the change for operations to implement. Some organizations even have network operations manage basic security changes -- mostly firewall rule updates (security defines the policy but network operations implements the change on the firewall itself). A detected change goes through the same analysis process but may require an emergency fix or communications with the network team to roll back the change (and obviously requires ongoing monitoring for detection in the first place). In both cases it can be helpful to integrate the process into your change management or workflow tool to automatically route tasks. Finally, both sides should have response requirements to make sure the process flows smoothly and changes can be implemented in a timely fashion. Finally, all changes with security implications need to be validated to ensure everything works as expected.
* **Business exemption or change requests:** Occasionally a business unit will need a change to network security. Many of these come through network operations, but quite a few come from application teams or business units themselves for particular projects. The same basic process is followed -- the change request comes in, is analyzed for risks and required changes, and then approved, implemented, and validated. You will notice we always assume approval -- flatly turning down a request should be a rare and measured result; it is far better to determine what security is needed for an acceptable level of risk. Network operations may also need to be involved, depending on where the asset is positioned and how traffic needs to be routed, especially for things like applications that need traffic to flow through particular security tools, or host-based security that needs a communications path to a management server. As before, you also should plan to monitor for and manage unapproved changes, which is where application-aware monitoring is particularly helpful (*e.g.,* a new server popping up on an unexpected subnet). Also, consider making a portal for business units to submit and track requests, rather than handling through email or spreadsheets.
* **New assets and applications:** This is similar to a business exemption or change request, but focused on new projects and assets rather than creating a special exemption to existing policy. There may be more planning, earlier in the process, with a lot more people involved. Develop a two-track process -- one for new applications or assets that are fairly standard (*e.g.,* a business unit file server or basic web application) which can be more automated, and a second for larger programs such as major new applications.
* **New security tools or policy changes:** Adding a new security tool or policy change reverses the workflow, so the responsibility is now on the security team to initiate communications with network operations and other affected teams. Security should first analyze the change and potential downstream impacts, then work with teams to determine operational risks, timelines, and any other requirements.

##Conclusion

Network security management isn't easy, but there are more and less efficient ways to handle it. Knowing your posture and maintaining visibility are key, as are developing core workflows to bridge gaps between different operational teams. Network security operations monitors the environment and change requests to adapt the security posture as needed in a timely manner. It monitors for changes that slip through outside approved processes, develops workflows to handle the unexpected, and responds quickly when changes are requested to support other business areas. Finally, network security understands that security policy changes impact other operations, along with the need to analyze and communicate these potential implications.

Pragmatic network security management starts by building a baseline of network topology, information assets, and security controls. Then we prioritize and address issues, building processes and workflows to better manage change requests, as well as unexpected changes, over time. All while keeping an eye out to ensure that everything is structured and functioning as expected. It is not always easy, but it is far more efficient and effective than the alternatives, and frees up the security team to focus on what they are best at.
