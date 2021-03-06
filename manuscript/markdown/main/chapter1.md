# Starting with the 30,000' View {#starting-with-the-30000-foot-view}

![](images/30000View.gif)

First of all, why? Why do we need to start so high? Because Developers spend most of their lives focussing on code and sometimes on architectural concepts and patterns. Software Developers rarely focus on anything higher than this. This has the affect of causing blind spots. The reason we start so high and encourage the developer come back to this level every so often is to recalibrate that they are actually creating the right thing and that their priorities are correctly aligned with the needs of their business, not even necessarily the business's wants.

Stepping back allows your peripheral vision to kick in.

This modelling process should be performed by a collection of the following people:

1. Deeply technical (software expert (developer/engineer)). I specifically do not mention tester(s) here, as testing is the job of the developer. The developer is responsible for delivering high quality working code every Sprint.
2. Network expert(s)
3. Domain expert(s) 
4. The person solely responsible for the project or product being delivered
5. Person(s) with security specialisations in the areas involved in the finished product.

Now you might be thinking that this team looks very familiar. Well that is probably because it is. It looks very much like a Scrum Team.

"_Scrum Teams are self-organizing and **cross-functional**. Self-organizing teams choose how best to accomplish their work, rather than being directed by others outside the team. Cross-functional teams have **all competencies needed to accomplish the work** without depending on others not part of the team. The team model in Scrum is designed to optimize flexibility, creativity, and productivity._"

> [Scrum Guide](http://www.scrumguides.org/scrum-guide.html)

Having this process performed by a team brings out the best in everyone. There are of course times when it is more effective to break out and work alone for a period of time.

## 1. SSM Asset Identification {#starting-with-the-30000-foot-view-asset-identification}
* [MS 1. Identify Assets](https://msdn.microsoft.com/en-us/library/ff648644.aspx#c03618429_006)
* [OWASP Assets](https://www.owasp.org/index.php/Application_Threat_Modeling#Assets)

The first question we must ask ourselves is: What are assets in the context of threat modelling? Assets are something we or our clients place value on that we are responsible for and subsequently will probably want to protect because someone unauthorised to access them also places value (covets) on them.

Assets will often emerge as you progress through the following steps, so you will probably end up modifying this list as you go, but it is vital that you do not miss this step in your eagerness to secure your world. If you do not have a good grasp on what it is that you are trying to protect, then there may be nothing or at least little to protect. This is unlikely, but still, you will want to have some idea of what your assets are before taking the next step. Feel free as you progress to jump back and modify the list of assets. More than likely you will keep adding to it as you identify additional risks and even work through the countermeasures of each chapter. This is how the process usually unfolds.

Identifying your assets is a domain specific task, so you are the best person(s) to do this. I will help to direct your thoughts as we progress though.

Many of the following chapters will address asset identification as the first step. Many assets will be the same for many chapters. Do not think about the assets as the be all and end all, but they can be useful to keep in your thoughts through the following steps of this chapter, which will be specialised in each following chapter.

Here are some that may or may not apply to your domain:

* User credentials
  Often stored within data stores, but also often found on the likes of post-it notes stuck to monitors or under a keyboard etc.
* Identity information
  such as: Email addresses, physical addresses, phone numbers, birth certificates
* Credit card numbers and similar
* Confidential business information
  This could come in many forms such as email, organisation wide wikis, document storage, and be stored in many places, such as: in data stores, code, configuration files, peoples heads, peoples desks and many others
* Confidential client information
* Reputation. I am sure you can think of a few ways that you or your organisations reputation could be tarnished or worse.

Now if you relate the potential loses with information security vectors, you will come up with a target list we can take into the next stages.

## 2. SSM Identify Risks {#starting-with-the-30000-foot-view-identify-risks}

* [MS 2. Create an Architecture Overview](https://msdn.microsoft.com/en-us/library/ff648644.aspx#c03618429_007)
* [MS 3. Decompose the Application](https://msdn.microsoft.com/en-us/library/ff648644.aspx#c03618429_008)
* [MS 4. Identify the Threats](https://msdn.microsoft.com/en-us/library/ff648644.aspx#c03618429_009)
* [OWASP Threat Model Information](https://www.owasp.org/index.php/Application_Threat_Modeling#Threat_Model_Information)
* [OWASP External Dependencies](https://www.owasp.org/index.php/Application_Threat_Modeling#External_Dependencies)
* [OWASP Entry Points](https://www.owasp.org/index.php/Application_Threat_Modeling#Entry_Points)

This is where we abstract things a bit and think about some of the entities that could be risky to the target business.

{#starting-with-the-30000-foot-view-identify-risks-threat-agents}
![](images/ThreatAgents.png)

Then think about some of the relationships the target business depends on and how they could be leaking IP.

{#starting-with-the-30000-foot-view-identify-risks-likelihood-and-impact}
![](images/LikelihoodAndImpact.gif)

{#ms-5-document-the-threats}
[MS 5. Document the Threats](https://msdn.microsoft.com/en-us/library/ff648644.aspx#c03618429_010)

[OWASP Risk Rating Methodology](https://www.owasp.org/index.php/OWASP_Risk_Rating_Methodology) is also useful here

* Likelihood "Threat Agent Factors"
  * How likely are particular exploits to be carried out?
  * How technically skilled is each group of threat agents?
  * How motivated is this group of threat agents to find and exploit this vulnerability?
  * What resources and opportunities are required for this group of threat agents to find and exploit this vulnerability?
  * What sort of access can they acquire?
  * How large is this group of threat agents?
* Likelihood "Vulnerability Factors"
  * How easy is it for this group of threat agents to discover this vulnerability?
  * How easy is it for this group of threat agents to actually exploit this vulnerability?
  * How well known is this vulnerability to this group of threat agents?
  * How likely is an exploit to be detected?
* Impact    "Technical Factors"
  * What's the impact likely to be if a particular exploit is executed
  * How much data could be disclosed and how sensitive is it?
  * How much data could be corrupted and how damaged is it?
  * Which services could be lost, how vital are they and how long could they be down for?
  * Would you be able to trace the threat agents actions to an individual?
* Impact    "Business Factors"
  * What would the financial damage be to any given exploit?
  * Would the exploit result in reputation damage that could harm your business?
  * How much exposure does non-compliance introduce?
  * How much personally identifiable information could be disclosed?

{#intel-threat-agent-library}
and the [Intel Threat Agent Library](http://www.sbs.ox.ac.uk/cybersecurity-capacity/system/files/Intel%20-%20Threat%20Agent%20Library%20Helps%20Identify%20Information%20Security%20Risks.pdf)

### Rating of Threats {#ms-6-rate-the-threats}

So how do we rate the threats we have just discovered? With a simple formula
Based on the [MicroSoft 6. Rate the Threats](https://msdn.microsoft.com/en-us/library/ff648644.aspx#c03618429_011)

I> Risk = Likelihood * Impact

Record the risks you have identified and rank as per above formula.

Keep your eye on the vulnerability advisories, as that is part of what an attacker or penetration tester will use to [formulate their exploits](#process-and-practises-penetration-testing-vulnerability-searching) for you:

{#vulnerability-advisories}
* [Exploit Database](https://github.com/offensive-security/exploit-database) from Offensive Security
  * [Web Front-end](https://www.exploit-db.com/)
  * CLI (searchsploit) in Kali Linux
* SecurityFocus [BugTraq](http://www.securityfocus.com/archive/1)
* Rapid7 (current owner of Metasploit) also has a [database](http://www.rapid7.com/db/modules/search)
* [NodeSecurity](https://nodesecurity.io/advisories)
* [National Vulnerability Database](https://web.nvd.nist.gov/view/vuln/search)

## 3. SSM Countermeasures {#starting-with-the-30000-foot-view-countermeasures}

![](images/BobTheBuilder.jpg)
 <!---This is where the images live: https://raw.githubusercontent.com/wiki/binarymist/HolisticInfoSec-For-WebDevelopers/BinaryMist-Approach-To-Threat-Modelling-Assets/BobTheBuilder.jpg-->

This is where you work through collaboratively creating countermeasure Product Backlog Items (PBIs). Countermeasure PBIs are like any other PBI. PBI qualities:

* Estimable
* Independent
* Testable
* Should promote collaboration
* Must fit within a Sprint by the time they are properly groomed
 
Your countermeasure PBIs also need to reference the risk they were created due to, thus providing context and urgency information. The PBIs need to be integrated into the Product Backlog, ordered based on the risk ratings. This way what you decide to fix first will be determined by the highest scoring risks.

* [OWASP Countermeasure Identification](https://www.owasp.org/index.php/Application_Threat_Modeling#Countermeasure_Identification)
* [MS STRIDE provides countermeasures to identified threats](https://msdn.microsoft.com/en-us/library/ff648641.aspx#c02618429_005)
* [MS Threats and Countermeasures](https://msdn.microsoft.com/en-us/library/ff648641.aspx)

## 4. SSM Risks that Solution Causes {#starting-with-the-30000-foot-view-risks-that-solution-causes}

This is really dependent on the solution(s) you discover. Often there will be new risks that the mitigation techniques introduce. We will work through many possibilities in the following chapters.

* Make sure before you test that you have written permission for all the areas that you are about to test, documenting what could possibly go wrong.
* Make sure you have backups and that they work.
* Complacency?
* Spending too much on technological solutions and ignoring the fact that the person on the front desk can easily be tricked to reveal information an attacker needs or lower the defences of a computer system. See the section on [People](#people).

As we work through the following chapters we will discuss many more hypothetical risks that proposed countermeasures may cause.

## 5. SSM Costs and Trade-offs {#starting-with-the-30000-foot-view-costs-and-trade-offs}
I am not here to do the work for you, but rather to help you do it.

> Give a man a fish and feed him for a day. Teach a man to fish and feed him for life

This is really dependent on the solution(s) you discover.

Think in terms of Counter-Measure costs - vs - Breach Costs and weigh them up against each other.


