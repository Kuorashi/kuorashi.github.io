---
layout: certification_item
title: "Certified Red Team Professional (CRTP)"
provider: "Altered Security"
status: "Obtenue"
date_obtained: "2024"
image: "/assets/images/htb/certificates/crtp.png"
description: "Certification spécialisée en Red Teaming et attaques Active Directory, couvrant les techniques d'attaque avancées sur les environnements Windows."
date: 2025-10-24 10:00:00 +0200
---

![CRTP Badge](/assets/images/htb/certificates/crtp_certificate.png)

## About the certification

The certification **CRTP (Certified Red Team Professional)** of Altered Security (formerly PentesterAcademy) is a recognized certification in the field of Red Teaming and Active Directory attacks.

## Validated skills

- **Active Directory Enumeration**
- **Offensive PowerShell Tradecraft**
- **Offensive .NET Tradecraft**
- **Local Privilege Escalation**
- **Domain Privilege Escalation**
- **Domain Persistence and Dominance**
- **Cross Trust Attacks**
- **Abusing AD CS**
- **Defenses and bypass – MDE EDR**
- **Defenses and bypass – MDE EDRDefenses and bypass – MDI**
- **Defenses and bypass – Architecture and Work Culture Changes**
- **Defenses – Monitoring**
- **Defenses and Bypass – Deception**

## Exam format

- **Duration** : 24 hours for the exam plus 48 hours for the report.
- **Objective** : exploit and gain a minima os command execution on all machine on a fully patched Enterprise Active Directory environment containing multiple domains and forests.

---

## **Introduction**

The importance of Active Directory in an enterprise cannot be stressed enough. Used by more than 90% of Fortune 1000 companies, the all-pervasive AD is the focal point for adversaries. Still, when it comes to AD security, there is a large gap of knowledge which security professionals and administrators struggle to fill. Over the years, Altered Security has taught numerous professionals in real-world trainings on AD security and consistently found that there is a lack of quality material and, especially, a dearth of practice labs where one can practice AD attacks in a controlled environment.

<br>

**Why I Chose This Training**

At the time of purchase and certification, I was working as an apprentice within a red team. This was an excellent opportunity to expand my skills, learn more, and discover different methods and tools beyond those used within my team. This certification allowed me to validate my technical skills in junior Red Teaming with and without command & control, as well as demonstrate my ability to conduct comprehensive red-team assessments in a professional environment.

## **Certification Overview**

**About Altered Security**

Altered Security is a cybersecurity training provider specializing in offensive security, particularly in Active Directory and Azure environments. Founded by security practitioners with years of hands-on experience, the company focuses on delivering practical, real-world training that bridges the gap between theoretical knowledge and practical application. Their flagship certifications—CRTP (Certified Red Team Professional), CRTE (Certified Red Team Expert), and CRTM (Certified Red Team Master) form a comprehensive learning path for aspiring and experienced red teamers.

<br>

What sets Altered Security apart is their commitment to providing not just courses, but complete learning ecosystems that include detailed course materials, hands-on labs, detection perspectives through integrated XDR, and an active community for ongoing support. Their training philosophy emphasizes understanding both offensive techniques and defensive countermeasures, preparing students for real-world engagements where stealth and evasion are crucial.

<br>

**Training Format**

The training includes:
- Video lessons for visual learners
- Comprehensive written course materials
- A hands-on training lab
- Lab manual for exploitation using provided tools
- Alternative lab manual for exploitation using the Sliver C2 framework
- Integrated Microsoft XDR for detection analysis
- Access to an active Discord community

**Duration and Options**  
Several options are available depending on your current skill level. You can purchase the course only (without the training lab) or with the training lab for various durations: 30, 60, or 90 days. With prior knowledge, 30 days is a good option; otherwise, I would recommend 60 to 90 days of lab access to fully absorb the material and practice thoroughly.

<br>

**Recommended Prerequisites**

- Basic understanding of Active Directory
- Ability to use command-line tools on Windows
- Familiarity with general security concepts
- Experience with Windows boxes (e.g., on HackTheBox) is a significant plus

## **Course Content**

### **Pedagogical Approach**

**Quality and Completeness of Course Materials**

The course material is exceptionally comprehensive and detailed, covering both theoretical foundations and practical applications. Each module is well-structured, progressing logically from fundamental concepts to advanced techniques. The written materials are complemented by video demonstrations, making complex topics more accessible.

<br>

**Key Feature: Offensive AND Defensive Approach**

One of the standout features of this training is its dual perspective. Every offensive technique is accompanied by corresponding detection methods and protective measures. This approach provides invaluable insight into:
- How defensive tools identify malicious activity
- What indicators of compromise (IOCs) your actions leave behind
- How to refine techniques to evade detection
- Why certain defenses work and how they can be bypassed

This defensive awareness is crucial for modern red teamers who must operate stealthily in environments with mature security controls.

<br>

**Practical Tips**

- Take structured notes from the beginning—you'll thank yourself during the exam
- Don't hesitate to take breaks and use the lab in parallel with reading
- The course can be lengthy and dense; breaking it into manageable sections helps maintain focus and retention

### **The Paradigm Shift: Windows-First Approach**

**Transitioning from Linux/Kali to Native Windows**

Most penetration testing training traditionally focuses on Linux-based attack platforms like Kali Linux. CRTP takes a different approach by conducting operations from a Windows machine, which is significantly more realistic for red team engagements. In real-world scenarios, once you've established initial access, you're often operating from a compromised Windows endpoint, not a Kali box.

<br>

**Tools and Methodologies**

The course covers Windows-native tools and techniques, including:
- PowerShell for reconnaissance and exploitation
- Windows built-in binaries (LOLBins)
- .NET-based offensive tools
- Native Windows commands for persistence and privilege escalation
- Integration with C2 frameworks like Sliver from a Windows perspective


**Advantages for Realistic Red Teaming**

This Windows-first approach offers several benefits:
- **Realism**: Mimics actual post-exploitation scenarios
- **Stealth**: Native Windows tools often trigger fewer alerts than traditional Linux tools
- **Practicality**: Directly applicable to enterprise environments where Windows dominates
- **Skill diversity**: Expands your toolkit beyond Linux-centric methods
- **Detection evasion**: Understanding Windows internals helps you blend in with legitimate activity

## **The Training Lab**

### **Environment and Infrastructure**

![Active Directory Lab](/assets/images/htb/certificates/crtp_lab.png)

**Active Directory Lab Description**

The lab contains various Windows client machines, Windows servers, and different Windows services. It includes multiple domains and forests, replicating a complete Active Directory environment that could be found in an enterprise setting. Windows Defender is enabled on all machines, and an XDR is also present to capture all indicators created by students in the lab.

<br>

**Available Tools**

Many tools are provided with explanations on how to use them in the course. You also have access to the lab manual to exploit it using the provided tools or by using the Sliver C2 framework.

### **Practical Tips**

- **Use the lab in parallel** with reading the course material to take breaks and maintain focus
- **Repeat exercises**: For unclear concepts, redo the manipulations multiple times
- **Microsoft XDR**: Test your techniques and verify detection, learn to reproduce them without being detected
- **Have fun and experiment** as much as possible in the lab. Access is time-limited based on what you selected at purchase. I recommend exploiting the entirety of your available time before launching the exam, as unused time is lost once you start the exam. This can be an opportunity to refine your knowledge, test things out, and have fun.

### **Note-Taking Management**

**Importance of a Clear and Organized Structure**

There's no point in copy-pasting the course content, you need to synthesize and record important information that can be reused. Everyone has their own way of taking notes, and you may need to test several software options and approaches to feel comfortable with your notes. Personally, I chose Obsidian for note-taking; I appreciate its structure, plugins, and the ability to link notes together.

<br>

**My Personal Approach**

I separated technical notes from general notes. I had a general section explaining the type of attack, how it works, why it might be present, how to secure/patch it, and the indicators that could signal exploitation of this type. My technical notes included command examples, the information needed to carry out the action, etc.

<br>

**Recommended Structure**

Consider organizing your notes with:
- **General concepts**: Attack methodology, theory, detection methods
- **Technical references**: Commands, syntax, required prerequisites
- **Lab-specific information**: Environment details, credentials, specific configurations
- **Quick reference sections**: Common commands, cheat sheets for rapid access during the exam

## **The Exam**

### **Format and Process**

**Duration and Objectives**  
The practical exam lasts 24 hours, and you have an additional 24 to 48 hours (I don't remember exactly) to submit your report. In your report, you're expected to prove that you've at least achieved OS command execution, you don't necessarily need to become admin on all machines. Your report should explicitly detail your thought process and explain why you performed each action, demonstrating that you fully understood the purpose and expected outcome of your actions.

<br>

**Type of Environment**  
The environment may be similar to the training lab, featuring multiple Windows machines and several Active Directory domains or forests.

### **Tips for Success**

- **Mental Preparation**: Be well-rested and allocate sufficient time
- **Stress Management**: 
  - Know when to take breaks if you feel stuck, coming back with fresh eyes often helps you breakthrough blockers
  - Keep your notes well-organized and easily accessible
  - Follow a consistent methodology during the exam

## **My Personal Experience**

**What I Appreciated Most**  
The training lab and XDR access, the Discord community always ready to help, and lifetime access to the course materials and tools.

<br>

**Challenges Encountered**  
Some VPN connection issues and Kerberos cache problems, but that's on you to clear the cache periodically or when you go back to a previous lab step. I got stuck on one specific machine for a while; ultimately, the issue was with the machine itself. Once I contacted support about my problem, they asked for screenshots of the actions I'd performed and were able to determine that the issue was indeed with the target machine. They quickly reset it, and everything worked afterward. Staying focused and attentive during the course reading can be challenging, the course material can be quite lengthy at times.

<br>

**What I Learned Beyond Technical Content**  
Perseverance, staying calm, seeking solutions independently before asking for help, self-questioning, being diligent in note-taking, and synthesizing important information effectively.

<br>

**Skills Acquired**  
- Active Directory exploitation techniques
- Windows-based red teaming operations
- Detection and evasion methodologies
- XDR analysis and understanding of attack indicators
- Structured approach to complex environments

## **Conclusion**

### **Who Is This Certification For?**

**Recommended Profiles**  
Junior pentesters and red teamers, cybersecurity enthusiasts, SOC operators, really, any type of profile can pursue this certification, as everyone will find value in it.

<br>

**Required Level**  
Suitable for all levels, provided you have a solid understanding of Active Directory functionality, Kerberos, general attacks like Silver Ticket, Golden Ticket, certificate attacks (ESC vulnerabilities), and similar concepts. Experience solving Windows boxes on platforms like HackTheBox is a real plus before starting this certification.

### **Final Verdict**

**Quality-to-Content Ratio**  
I purchased this training during Black Friday, and for a course that cost me €200, I can confidently say I got my money's worth. The training includes a comprehensive and dense course material, an extensive and high-quality practice lab that allows you to test all the concepts covered in the course, an XDR throughout the training to understand the indicators we leave during exploitation that could lead to our detection, and a very active Discord community that enables you to learn more and get help when stuck or confused.

<br>

**Would I Recommend This Training?**  
Absolutely, yes. This is an excellent training for taking your first steps in red team operations, but also an outstanding course for SOC analysts to learn detection methods and attack indicators in an Active Directory environment. It's important to remember that this is a junior-level certification, it's only the first step into a vast world. To expand your knowledge, CRTE and CRTM and lot of other certs exist and will incorporate offensive tool development to bypass security systems implemented in target labs.

<br>

**Comparison with Other Certifications**  
If we had to find an equivalent certification, it would be RTO 1 from ZeroPointSecurity in terms of difficulty and target level. However, these two certifications are quite different: while CRTP focuses on using open-source, free tools, manual exploitation tool by tool, or via a free C2 like Sliver, RTO 1 concentrates on exploitation using the CobaltStrike C2. You'll need to make a choice based on your needs, a generalist junior red team training or specialization in CobaltStrike usage.

## **Useful Resources**

**Certification Link**
- [CRTP](https://www.alteredsecurity.com/adlab)

**Additional Resources That Helped Me**
- [ired.team](https://www.ired.team/)

**Community/Discord/Forums**
- [AlteredSecurity Discord](https://discord.com/invite/vcEwaRMwJe)