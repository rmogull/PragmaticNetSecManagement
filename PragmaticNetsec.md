
# Executive Guide to Pragmatic Network Security Management

## The Demise of Network Security is Greatly Exaggerated  
DLP, IPS, NGFW, WAF. Chief Information Security Officers today suffer no shortage of network security tools to protect their environment, yet most CISOs we talk with struggle to implement and maintain an effective network security program. They tell us it isn't a lack of technologies, or even necessarily resources (not that there are ever enough), but the inherent difficulties in defending a large, amorphous, business-critical asset with tendrils underlying the entire organization. It's never as simple as the magazine articles and conference presentations make it out to be.
  
Managing network security at scale is never easy, but the organizations that do it the best tend to follow a predictable, repeatable pattern. This paper distills those lessons into a pragmatic process designed for larger organizations, or those with more complicated networks (like a medium-sized business with multiple locations). We won't make the false claim that our magical process is easy, _but it's certainly easier than many alternatives_. Even if you only pick out a few tidbits it should help you refine and operate your network security more efficiently.

The network is the one aspect of our infrastructure that ties everything else together. The more we can do to efficiently and effectively secure it, the better.
  
###Why Network Security is So Darn Difficult

Networks and endpoints are the two most fundamental pieces of our IT infrastructure, yet despite decades of advancements they still consume a disproportionate amount of our security resources. First the good news — we are *far* more resilient to network attacks than even five years ago. The days of a Internet-wide worms knocking down enterprises while script kiddies deface websites are mostly tempered. However, every CISO knows establishing and maintaining network security is a constant challenge, even if they can't always articulate why. We have narrowed these down to a handful of root causes, which the Pragmatic process is designed to address:

* _Security and operations are divided_. IT operations is responsible for and manages the network, servers, endpoints, and applications, and information security is responsible for defending everything. In effect, security protects the enterprise from the outside, lacking insight into what is being protected, where it is, and how everything is connected together. In many cases security doesn't even know how all the pieces of the network are connected, yet is supposed to manage the firewall rules around it. Many of our recommendations are designed to bridge this divide, without throwing away traditional organizational boundaries.
* _Networks are dynamic and complex_. Not only are new assets constantly joining and leaving the network, but the structure itself is never static, especially for larger organizations.
    * Organic growth. All networks grow over time. Perhaps it's a new office, extending a WiFi network, or maybe an extra switch or router in the datacenter. Not all of these have big security implications, but they add up over time.
    * Mergers and acquisitions require a blending of resources, technologies, and different configurations. 
    * New technologies with different network needs are constantly added. Be it a new remote access portal, or an entire private cloud.
    * Our mixing and matching of various security tools, often with overlapping functionality. This is sometimes a result of different branches of the company operating semi or completely autonomously, and other times the result of turnover, project requirements, or keeping auditors happy.
* _Needs change over time_. Many organizations today are working on consolidating network perimeters, compartmentalizing internal networks, adding application awareness, expanding egress monitoring and filtering for breach and infection defenses, or adapting the network for cloud computing (and eventually SDN). Network and network security technologies evolve to meet new business needs and evolving threats.

Our networks are big and complex, even sometimes when our organizations aren't. They constantly change over time, as do the assets connected to them. Security doesn't manage this infrastructure, but is tasked with protecting it.  _Network Security Management is about improving both your security and efficiency to keep up with this pace of change._
	
### From Blocking and Tackling to Integrated Defense

Our primary goal is to adopt processes that allow are flexible enough to account for an ever-changing network environment, but avoid the constant firefighting that is so inefficient. The key isn't any particular technology or security trick, but better integrating defenses into day to day management of the enterprise. What makes it pragmatic? _The fact that the process is designed to work in the real world, without gutting organizational and bureaucratic divisions. _

We get it, even if you are the CEO there are limits to change. We have tried our best together the best practices we've seen work in the real world, and line them up in a practical, achievable process that accounts for real-world limits. Our next sections will dig into the process, and as we said earlier, pick and choose what works for you.

## The Pragmatic Process

As we mentioned in the previous section, this process is designed primarily for more-complex networks, and tries to account for real-life organizational and technological complexities.

Here's the outline of the process, followed by the details:

* Know your network.
* Know your assets.
* Know your security.
* Map the topology.
* Prioritize and fix.
* Continuously monitor.
* Manage change and build workflows.

The first five steps *establish the baseline*, while the next two steps *manage the program*, although you will need to periodically revisit previous steps to ensure your program is still up to date as the business evolves and risks change.

###Know Your Network

You can't secure what you don't know, but effectively mapping a network topology, especially a large network, can be daunting. We even meet many organizations that believe they have an accurate network topology, but they are rarely correct or complete for all the reasons we covered in the previous section. The most common problem is simply failing to keep it up to date. Topology maps are produced occasionally as needed for audits or projects, and not maintained in the interim. 

The first step is to work with network operations to see what they have and how up to date it is. Aside from being politically correct, there's also no reason not to leverage what is already available. Position it as "we need to make sure we have our security in the right places," not, "we don't trust you". Once you get their data in hand, evaluate it and then decide how much you need to validate it or extend it.

There are a few ways to validate your network topology, and you  want to rely on automation when possible. Even if your network operations team provides a map or [CMDB](http://en.wikipedia.org/wiki/Configuration_management_database), you need to verify that it is current and accurate. One issue we see at times is that security uses a different toolset than the network operations teams. 

*Security scanners* use a variety of techniques to probe the network and figure out the structure, but standard security scanners (like vulnerability assessment tools) aren't necessarily well suited to building out a complete network map. 

Network operations teams have their own set of mapping tools, some of which use similar scanning techniques, but also add in additional routing and other analysis that rely on management-level access to the routers and network infrastructure. These tools tend to rely more on trusting the information provided to them and don't probe as heavily as security tools. They also aren't generally run organization-wide on a continuous basis, but are rather used for specific problem solving and planning. 

<!-- The security team needs to know the network structure to properly position defensive assets. Unless you are completely confident that your operations teams are providing you current and complete data on a relatively continuous basis, you will need to perform your own network mapping, not just standard security scanning. -->

###Know Your Assets

Once you have a picture of the network, then you start evaluating the assets on it (servers, endpoints, and other hardware). Security tends to have better tools and experiences for scanning and analyzing assets than the underlying network structure, especially for workstations. 

Depending on how mature you are at this point, either prioritize your scanning to particular network segments, or use the information from the network map to target weak spots in your analysis. Endpoint tools like configuration/patch management or endpoint protection platforms can feed some information, but you also need to integrate a security scan (like a vulnerability assessment) to identify problems. 

As before, this really needs to be a continuous process using automated tools. You also need to have a sense of the importance of the assets, especially in data centers, so you can prioritize defenses. This is a tough one, so make your best guesses if you have to, it doesn't need to be perfect.

### Know Your Security

There are three major pieces of network security you need to collect detailed information on:

* Base infrastructure security. This includes your standard perimeter security, plus anything you have deployed internally to enforce any kind of compartmentalization or detection. Think firewalls (including NGFW), intrusion prevention, intrusion detection, network forensics, Netflow feeds to your SIEM, and similar. Think the things designed predominantly to protect the core network layer. Even network access control, for both of you using it.
* Extended security tools. These are designed to protect particular applications and activities, such as your secure mail gateway, web filter, web application firewalls, DLP, and other "layer 7" tools. 
* Remote access. Security tends to be tightly integrated into VPNs and other remote access gateways. These aren't always managed by security, but unlike network routers they have security settings set internally that affect network access.

For each collect the location and configuration. You don't need all the deep particulars of a WAF or DLP (beyond what they are positioned to protect), but you certainly need complete details of base infrastructure tools. Yes, that means every firewall rule. Also determine how you manage and maintain each of those tools. Who is responsible? How do they manage it? What are the policies?

###Map the Topology

This is the key step where you align your network topology, assets (focusing on bulk and critical analysis, not every single workstation), and existing security controls. There are two kinds of analysis you then perform:

* A _management analysis_ to determine who and how you manage all the security and network assets. Who keeps firewall X up and running? How? Using which tool? Who manages the network hardware that controls the routing that firewall X is responsible for? Do you feed netflow data from this segment to the SIEM? IDS alerts? Your objective here is to understand the technical underpinnings of your network security management, and the meatspace mapping for who is responsible.
* A _controls analysis_ to ensure the right tools are in the right places with the right configurations. Again, you probably want to prioritize this based on the assets. Do you use application-aware firewalls (NGFW) where you need them? Are firewalls configured correctly for the underlying network topology? Do you segment internal networks? Capture network traffic for detecting attacks in the right places? Are there network segments or locations that lack security controls because you didn't know about them? Is that database really safe behind a firewall, is or it totally unprotected if a user clicks the wrong link in a phishing email?

In essence, the first analysis focuses the implementation of your management processes and workflow. Sure, everyone has policies, but how are the actual infrastructure and defenses managed? Who is responsible for what and where does the data flow? The second analysis is all about preventing and detecting attacks and aligning your controls. Are the right defenses configure properly in front of the right assets?

Once you map the assets, to the network topology, to the security defenses, to the management infrastructure two pictures emerge — how your defenses are really aligned, and how you manage them. 

###Prioritize and Fix

By now you have a deep understanding of your network topology, a decent understanding of where important things are on the network, and a solid idea of how your security is configured around and within it. Now its time to start fixing things. And remember, we are focusing on *network security* today, not the endless list of other controls you can bring to the table. Also, your goal is to improve how you manage your security over time, not just plug a few holes until you need to start all over again.

This involves:

* Repositioning network security tools. Ensure you have the correct preventative or monitoring control in the right physical location. This isn't about buying new things, but about understanding and best using the ones you have at your disposal.
* Reconfiguring network security tools. Adjust the rules and configurations of the tools to provide the desired protection. 
* Consolidating your network security management so you can maintain visibility and implement changes more efficiently in the future. 
* Position new tools as needed. You may already be using tools like application-aware network security, egress and command and control monitoring, DDoS protection, cloud web filtering, or malware gateways. But, if not, you now have much better information to integrate them effectively into your program and best position and configure them.

Right now we are still in the "initial fix" phase. In a moment we will get to the continuous change management phase where you focus more on ensuring things never get as out of sync as they are at the start. Most organizations will fix some immediate things at the same time they start adjusting their management processes and workflow. There's no reason you have to hop through these steps one at a time.

###Continuously Monitor

This is they key phase to make sure you don't have to start all over again in a year once everything gets out of sync again. We've moved past *baselining* and into *managing the program*. There are four key pieces to keep track of:

* Network topology changes. Sometimes these are small changes like a new routing rule, and other times it might be the addition of an entire new large network due to an acquisition. Security can monitor for these themselves, or establish stronger collaborative workflows with network operations. Regardless, it will need to be revalidated from time to time to catch errors and omissions. You can use the same tools you used to build and validate your initial topology map, except now you run them on a continuous or periodic basis, plus passive network monitoring tools that track live traffic.
* Asset changes. If your servers, workstations, and other IT assets aren't moving around on pretty much a daily basis, odds are you are out of business. Security scanners, especially vulnerability scanners, are your tool of choice.
* Network security tool changes, which includes both uses and configurations, and is why we emphasized consolidating your network security management infrastructure.

You'll notice we skipped the part about *monitoring for bad guys*. That's because this report is focused on managing your overall program, not the details of your daily defenses and incident response. It goes without saying (but we'll say it anyway), that continuous security monitoring also includes extensive monitoring of real time network activity. That's why we spend so much time determining the best places to monitor (and defend) and the best tools and configurations for the job as part of our monitoring program. 

The past piece of this phase is creating reports for auditors and executives. This is essential to meet compliance obligations and demonstrate your value to the rest of the organization. Ideally you can quickly create these reports without undue effort since you have all the required data constantly updated and accessible.

###Manage Change and Build Workflows

This is the most important phase of the entire process. Up until now you have mostly focused on understanding your infrastructure, and developing the security controls around it. But this is impossible to maintain unless security works more closely with both IT operations and various business units. The key is not only to refine your internal processes, but create *minimal-friction workflows* for working with the rest of the organization. The easier it is for them to go through an approved process, the less likely they are to try and circumvent it. 

And the more you can automate this, including ongoing data gathering to detect the details and implications of changes, the better.

In this section we will cover the security change management process, and in the next section we will give examples of common workflows for working with other areas of the organization. For more depth on detailed processes for network security operations, we suggest you read our [Network Security Operations Quant Report](https://securosis.com/Research/Publication/network-security-operations-quant-report) . 

* **Trigger:** A change can be due to a formal request from the outside, internal updates, or due to a change to the operating environment (such as a routing change that was detected by security, but didn't go through a change request process). Ideally everything runs through the approval process, but even the best-run organizations still have to deal with out-of-process changes they detect on their own.
* **Process change request and authorize:** Examine the unapproved change to determine the security response, or process the internal or external change request. Determine the requirements, impact, security risks, and priority, then slot the change into a maintenance window. Priority factors in both business needs and security needs, especially where threats are a factor.
* **Test and approve:** This step includes development of test criteria, any required testing, result analysis, and approval of the signature/rule change for release once it satisfies requirements. 
* **Deploy and confirm:** Deploy and verify that changes were successful, including both installation and operation. This might include use of vulnerability assessment tools or application test scripts to ensure there is no disruption of production systems or attack surface added as a result of the change.
* **Audit/validate:** The full process of making a change encompasses more than merely having the operations team confirm it during the Deploy step — another entity (internal or external, but not part of the ops team) should audit it as well to provide separation of duties. This entails validating the change to ensure policies were properly updated and matching it against a specific request. This closes the loop to make sure there is documentation (and an audit trail) for every change.
* **Emergency updates:** In some cases, including data breach lockdowns and imminent or active zero-day attacks, a change to the network security device’s configuration must be made immediately. An ‘express’ process should be established and documented in advance as an alternative to the normal full change process, ensuring proper authorized approval for emergency changes, as well as a rollback capability in case of unintended consequences.

## Workflows: From Sec and Ops to SecOps

Even mature organizations occasionally struggle to keep their security aligned with the infrastructure. Managing changes at scale is never easy, and something is always bound to slip through the cracks. However, establishing low-friction processes that don't overly burden other areas of the enterprise reduce both errors and deliberate circumvention. 

Frequently this manifests as a lack of communication between network security and network operations. Not out of any antagonism, but simply due to different priorities, toolsets, and issues to manage on a day to day basis. A seemingly minor routing change, or the addition of a new server, can quietly expose the organization to new risks if security defenses aren't coordinated. On the other hand, security can also easily break things and create an operational incident with a single firewall rule change.

Efficient programs don't just divide up operational responsibilities, they implement workflows where each team does what they are best at, and still communicates cleanly and effectively to each other. Security is best at understanding what needs to be protected and how, while operations is best at keeping it running. Here are examples of four integrated operations workflows:

* **Network topology changes:** Changes to the topology of the network have a dramatic impact on the configuration of security tools. The workflow consists of two tracks — approved changes and detected changes. For approved changes the network team defines the change and submits to security. Security analyzes it for security impact, including the changes to risks and required security updates. Security then approves the change for network operations to implement. Some organizations even have network operations manage basic security changes, mostly firewall rule updates (security defines the policy, but network operations implements the change on the firewall itself). A detected change goes through the same analysis process, but may require an emergency fix, or communications with the network team to roll back the change (and obviously requires some level on ongoing monitoring to detect it in the first place). In both cases it can be helpful to integrate the process into your change management or workflow tool to automatically handle routing of tasks. Finally, both sides should have response requirements to make sure the process flows smoothly and changes can be implemented in a timely fashion. Finally, all changes with security implications also need to be validated to ensure everything occurred as expected.
* **Business exemption/change requests:** Occasionally a business unit will need a change to network security. Many of these will come through network operations, but quite a few come from application teams or the business units themselves for particular projects. The same basic process is followed — the change request comes in, is analyzed for risks and required changes, and then approved, implemented, and validated. You'll notice we always assume approval, since flatly turning down a request should be a rare and measured result; it is far better to determine what security is needed for an acceptable level of risk. Network operations may also need to be involved depending on where the asset is positioned and how traffic needs to be routed, especially for things like applications that need traffic to flow through particular security tools, or host-based security that needs a communications path to its management server. As before, you also should plan to monitor for and manage unapproved changes, which is where application aware monitoring can be helpful (e.g. a new server popping up on an unexpected subnet). Also, consider making a portal for business units to submit and track requests, instead of handling through email or spreadsheets. 
* **New assets/applications:** This is similar to a business exemption/change request, but is focused on new projects and assets as opposed to creating an special exemption to an existing policy. There may be more planning, earlier in the process, with a lot more people involved. Develop a two track process — one for new applications or assets that are pretty standard (e.g. a business unit file server or basic web application) that can be more automated, and a second for larger programs (like major new applications). 
* **New security tools or policy changes:** Adding a new security tool or policy change reverses the workflow, where the responsibility is now on the security team to initiate communications with network operations and other affected teams. Security should first analyze the change and the potential downstream impacts, then work with those teams to determine any operational risks, timelines, or other requirements.

## Conclusion

Network security management isn't easy, but there are certainly more efficient ways to address the problems. Knowing your posture and maintaining visibility are key, as are developing core workflows to bridge the gaps between different operational teams. Network security operations monitors the environment and change requests to adapt the security posture, as needed, in a timely manner. It monitors for changes that slip outside approved processes, and develops workflows to handle the unexpected, as well as respond quickly when changes are requested to support other areas of the business. Finally, network security also understands that security policy changes also affect other operations, and the need to analyze and communicate these potential implications.

Pragmatic network security management starts by building a baseline of the network topology, information assets, and security controls. Then we prioritize and address issues, and build processes and workflows to better manage change requests, and unexpected changes, over time. All while keeping an eye that everything is structured and functioning as expected. It may not always be easy, but it is certainly more efficient and effective than the alternatives, and frees up the security team to focus on what they are best at.