- WHAT IS THE PRINCIPLE OF LEAST PRIVILEGE (POLP)?
- Least privilege is the concept and practice of restricting access rights for
  users, accounts, and computing processes to only those resources absolutely
  required to perform legitimate functions. Privilege itself refers to the
  authorization to bypass certain security restraints. When applied to people, the
  principle of least privilege (POLP), means enforcing the minimal level of user
  rights, or lowest clearance level, that allows the user to perform his/her role.
  However, least privilege access also applies to processes, applications,
  systems, and devices (such as IoT), as they each should have only those
  permissions needed to perform an authorized activity. Enforcing least privilege
  access is an instrumental best practice to reduce security risk and minimize
  business disruption resulting from errors or malicious intent.
- Least privilege access is a timeless security principle. The security landscape
  has rapidly shifted in recent years due to increased remote work, rapid cloud
  migration, and an increasingly perimeterless world, putting zero trust
  [https://www.beyondtrust.com/zero-trust] and identity-centric security
  approaches in the spotlight. However, implementing least privilege has only
  become more critical, and is a foundational concept of any zero trust
  architecture (ZTA) and identity security approach
  [https://www.beyondtrust.com/blog/entry/identity-access-security-best-practices-highlighted-at-identity-management-day].
- The principle of least privilege is straightforward, but can be complex to
  effectively implement, especially when you consider the many variables, such as:
- Heterogeneous systems (Windows, macOS, Unix, Linux, etc.)
  * Expanding numbers and types of applications and endpoints (desktops, servers, laptops, tablets smartphones, IoT, ICS, etc.)
  * Diverse computing environments (cloud, virtual, on-prem, hybrid)
  * Many different types of identities and user roles (human, application, machine)
  * Third-party / vendor access
- While this blog will focus on the cybersecurity [https://www.beyondtrust.com/resources/glossary/cyber-security] context of least
  privilege access, no doubt you’re familiar with analogous concepts, such as
  “need to know” popularized amongst military and governmental circles. In fact,
  adoption of “least privilege” was advanced by the publication of the “Department
  of Defense Trusted Computer System Evaluation Criteria”
  [http://csrc.nist.gov/publications/history/dod85.pdf] in 1985, following the
  recommendations of a task force dedicated to safeguarding classified data.
  
  Read on for an in-depth overview of least privilege, including: types of
  computing privileges, privileged and non-privileged accounts, privileged threat
  vectors and attacks
  [https://www.beyondtrust.com/blog/entry/new-privileged-attack-vectors-book-q-a-with-author-morey-haber],
  challenges to applying a least privilege model, best practices and strategies
  for implementing least privilege, and the cornerstone technologies for enabling
  a least-privilege computing environment.
-
- # WHAT ARE PRIVILEGED ACCOUNTS?
  
  Privileged accounts
  [https://www.beyondtrust.com/resources/glossary/privileged-accounts] are users
  with some privilege assignment, or delegation built on role-based attributes,
  such as business unit, (i.e. marketing, HR, or IT) as well as other parameters
  (seniority, time of day, special circumstance, etc.). Additionally, various
  operating systems provide different default privilege settings for different
  types of user accounts.
  
  Superuser accounts
  [https://www.beyondtrust.com/blog/entry/superuser-accounts-what-are-they-how-do-you-secure-them],
  primarily used for administration by specialized IT employees, may have
  virtually unlimited privileges, or carte blanche, over a system. Superuser
  account privileges can include full read / write / execute privileges, and the
  power to render systemic changes across a network, such as creating or
  installing files or software, modifying files and settings, and deleting users
  and data.
  
  
  
  Standard user accounts, sometimes called least-privileged user accounts (LUA) or
  non-privileged accounts, have a limited set of privileges. In a least-privilege
  environment, these are the type of accounts most users should be operating in 90
  – 100% of the time.
  
  
  
  As a best practice, most non-IT users should only have standard user account
  access. However, some IT roles (such as a network admin) may possess multiple
  accounts, logging in as a standard user for routine tasks, while logging into a
  superuser account to perform administrative activities. Because administrative
  accounts possess more privileges, and thus pose a heightened risk compared to
  standard user accounts, a best practice is to only use these administrator
  accounts when necessary, and for the shortest time needed.
  
  
  
  The fastest growing area of privileged accounts today is associated with machine
  identities
  [https://www.beyondtrust.com/blog/entry/securing-machine-non-human-identities],
  including applications. Forrester Research has stated
  [https://www.beyondtrust.com/forrester-wave-privileged-identity-management-2023],
  “Our clients tell us that machine identities are growing at twice the rate of
  human identities.” Just like human accounts and privileges, these non-human
  privileges must be identified and managed.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  PRIVILEGED ACCOUNTS IN UNIX, LINUX, WINDOWS, AND MACOS PLATFORMS
  
  
  
  In Unix and Linux-like systems, the superuser account, called ‘root,’ is
  virtually omnipotent over the system, with unrestricted access to all commands,
  files, directories, and resources. Root can even grant and revoke any
  permissions for other users! If misused, either in error (such as accidentally
  deleting an important file or mistyping a powerful command), or with malicious
  intent, these root accounts can wreak catastrophic damage to a system or entire
  enterprise.
  
  
  
  Because of the immense potential for destruction inherent to root privileges, IT
  admins should only log into and assume root account privileges when necessary.
  Sometimes, this is done by leveraging the sudo (super user do) command
  [https://www.beyondtrust.com/blog/entry/cant-make-sudo]. Sudo allows the user to
  temporarily elevate privileges to root-level, but without having direct access
  to the root account and password.
  
  
  
  Standard, “non-privileged” Unix and Linux accounts lack access to sudo, but
  still retain minimal default privileges, allowing for basic customizations and
  software installations.
  
  
  
  In Windows systems, the Administrator account holds superuser privileges. Each
  Windows computer has at least one local administrator account. The Administrator
  account allows the user to perform such activities as installing software and
  changing local configurations and settings. Standard users have substantially
  curtailed privileges, while guest user accounts are generally limited even
  further to basic application access and Internet browsing.
  
  
  
  On the other hand, macOS is Unix-like, but unlike Unix and Linux, is rarely
  deployed as a server. However, macOS endpoints
  [https://www.beyondtrust.com/blog/entry/macos-security-managing-privileged-access-credentials]
  are increasingly prevalent at enterprises. While Mac users run with root access
  by default, as a security best practice, a non-privileged account should be
  created and used for routine computing to limit the likelihood and scope of
  privileged threats.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  PRIVILEGED ACCOUNTS AND THE CLOUD
  
  
  
  While cloud and virtualized environments provide many benefits, chief among
  them, rapid scalability, many traditional security tools are architected for
  on-premise environments. When extended or retrofitted to the cloud or across
  hybrid environments, these legacy tools leave gaps for excessive privileged
  access and permissions.
  
  
  
  Cloud and virtualization have also ushered in administrator consoles (such as
  with AWS and Microsoft 365) that confer substantial superuser capabilities,
  enabling users to instantly provision, configure, and delete servers at
  incredible scale. While it’s just a matter of a few simple clicks to spin-up and
  manage thousands of virtual machines—each with its own set of privileges and
  privileged accounts—from a single console, it can be complex to onboard and
  manage all these privileged accounts, many of which are ephemeral.
  
  
  
  Additionally, cloud platforms may provide some basic native tools for managing
  pieces of privileged access or other capabilities, but they cannot typically be
  extended for multicloud use.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  COMMON PRIVILEGED THREAT VECTORS
  
  
  
  Hackers, malware, partners / vendors, insiders-gone-rogue, and simple user
  errors—especially in the case of superuser accounts, round-out the most common
  privileged threat vectors.
  
  
  
  Let’s delve into how some of these vectors play out and review a few real-world
  examples.
  
  
  
  Poor Computing Hygiene + Unmanaged Privileges = Opportunities for Exploits
  
  
  
  Routine computing activities might entail internet browsing, watching streaming
  video, use of Microsoft 365 and other basic applications, such as Salesforce,
  Google Docs, Dropbox, etc. In the case of Windows PCs, users often log in with
  administrative account privileges—far broader than what is needed. Privilege
  over-provisioning massively increases the risk that malware or hackers may steal
  passwords or install malicious code delivered via web surfing or email
  attachments. The malware or hacker could then leverage the entire set of
  privileges of the account, accessing data of the infected computer, and even
  launching an attack against other networked computers or servers.
  
  
  
  For example, should a standard user click on an attachment or link within a
  phishing email, it may consequently load ransomware
  [https://www.beyondtrust.com/blog/entry/ransomware-a-problem-of-excesses-access-privileges-vulnerabilities]
  onto their system. The effect of this act alone would be isolated to the user’s
  own systems and the limited resources to which they can access. However, if the
  user was logged in as a superuser with broad admin privileges, the ransomware
  package could leverage domain account privileges to modify settings, corrupt,
  and access and encrypt sensitive data from other endpoints and servers across
  the network.
  
  
  
  
  EXTERNAL HACKERS
  
  
  Hackers covet privileged accounts and credentials, knowing that once obtained,
  they provide a fast track to an organization’s most critical systems and
  sensitive data. With privileged credentials in hand, a hacker essentially
  becomes an “insider”— a dangerous scenario.
  
  
  
  Cyberattackers commonly seek to gain an initial foothold through a low-level
  exploit, such as through a phishing attack on a standard user account. The
  attacker then surreptitiously zigzags through the network until they find a
  dormant or orphaned account
  [https://www.beyondtrust.com/resources/glossary/orphaned-accounts] allowing them
  to escalate their privileges
  [https://www.beyondtrust.com/blog/entry/privilege-escalation-attack-defense-explained].
  Elevation of privilege vulnerabilities are increasingly common and can make it
  particularly easy for an attacker, even an unprivileged one, to elevate
  privileges.
  
  
  
  Organizations lacking robust enterprise password management capabilities, such
  as automated password rotation
  [https://www.beyondtrust.com/blog/entry/password-rotation-needed], are also more
  susceptible to pass-the-hash (PtH) attacks. In these attacks, a hacker who has
  already gained low-level credentials can steal the password hash from an admin
  account if revealed—such as during a helpdesk session with the infiltrated
  account—and then reuse the hash to unlock administrative access rights.
  
  
  
  Hackers are also adept at obtaining deep privileges on a single computer and
  then expanding their privileges to other devices across a network via lateral
  movement
  [https://www.beyondtrust.com/blog/entry/cybersecurity-strategies-to-stop-lateral-movement-attacks-leave-your-adversaries-marooned]
  and privilege escalation
  [https://www.beyondtrust.com/blog/entry/privilege-escalation-attack-defense-explained].
  With the proper privileges and inadequate technology controls, a hacker can
  easily erase their tracks to avoid detection while they traverse the environment
  and get closer to achieving their objectives.
  
  
  
  
  INSIDER PRIVILEGE MISUSE OR ABUSE
  
  
  
  Allowing a user, or perhaps even multiple users, to utilize the all-powerful
  root in Unix / Linux environments means a simple error, such as a mistyped
  command or an accidental deletion, could have far-reaching consequences. Such an
  instance of privilege abuse could cause downtime of Tier-1 systems, opening
  gigantic vulnerabilities that let in rootkits and other exploits, or worse. In
  Windows environments, misused admin accounts also have potential to cause
  outsized damage compared to non-privileged accounts.
  
  
  
  However, rogue insiders likely pose the most dangerous threat. Insider threats
  take the longest to uncover since employees, contractors, and partners generally
  benefit from some level of trust by default, which may help them avoid
  detection. The protracted time-to-discovery also translates into greater
  potential for damage.
  
  
  
  Unlike external hackers, insiders already start within the perimeter, while also
  benefitting from know-how of where sensitive assets and data lie and how to zero
  in on them.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  CAUTIONARY TALES OF PRIVILEGED ACCESS EXPLOITS
  
  
  
  Here are a few infamous breaches underscoring the need to get least privilege
  right.
  
  
  
  
  SOLARWINDS
  
  
  Nation-state attackers hacked into SolarWinds and then inserted malware into
  SolarWinds Orion's source code. Consequently, the Orion application was
  leveraged as a backdoor to compromise SolarWinds customers when they applied
  auto-updates. SolarWinds customers were vulnerable to this supply chain attack
  because the Orion application needed unrestricted access, more specifically,
  global shared administrator access, to work. The core issue is global
  administrative accounts, with all their privileges, are often needed for legacy
  applications, like Orion, to operate correctly, and therefore cannot operate
  using the concept of least privilege application management. Thus, attackers are
  allowed full and unrestricted access to operate, which presents a massive attack
  surface. Since the Orion application itself was compromised, threat actors
  leveraged unrestricted privileged access throughout the victims' environments
  using the application.
  
  
  To prevent or mitigate these instances of over-privileged applications,
  organizations must first identify all the applications in their environment with
  high levels of privileges. Wherever possible, enterprises should implement least
  privilege application management
  [https://www.beyondtrust.com/privilege-management/], which entails removing all
  excessive application privileges. But again, this may prove impossible with many
  legacy applications. In some instances, the best mitigation strategy is to
  remove the application and choose a new vendor/application to solve for the
  business need. This issue is covered in more depth in this blog on least
  privilege application management
  [https://www.beyondtrust.com/blog/entry/least-privilege-application-management-a-lesson-learned-from-solarwinds-orion].
  
  
  
  VERKADA
  
  
  In 2020, the breach of Verkada
  [https://www.beyondtrust.com/blog/entry/dangers-of-iot-privilege-management-blind-spots-exposed-in-verkada-security-camera-breach]
  exposed the live feeds of 150,000 security cameras used by their customers,
  including jails, hospitals, women’s health clinics, psychiatric facilities,
  police departments, major tech companies, and more. The Verkada breach
  originated via compromised super admin credentials that were found embedded in a
  python script that was remotely accessible. The threat actors obtained “root”
  access to the Verkada cameras using built-in functionality that escalated their
  privileges to “Super Admin.” This superuser/root account permitted access to all
  of Verkada customers’ camera feeds, potentially jeopardizing security and
  privacy at every customer environment.
  
  
  Many least-privilege controls (removing admin rights, etc.) would have helped
  prevent or mitigate this breach, as would enforcing separation of privilege and
  separation of duties. No one account should wield control over so many different
  customer accounts and have such high-level privileges across so many systems.
  
  
  
  NSA / EDWARD SNOWDEN BREACH
  
  
  As a technology contractor for the NSA, Edward Snowden had administrative access
  rights, ostensibly to perform such activities as backing up computer systems and
  migrating data to local servers. However, by abusing his admin privileges and
  utilizing some simple and widely-available software tools, including an
  automated web crawler, Snowden illegally copied, accessed, and then leaked an
  estimated 1.7 million NSA files.
  
  
  In response to the Snowden breach, the NSA announced the drastic action
  [http://www.reuters.com/article/us-usa-security-nsa-leaks-idUSBRE97801020130809]
  of eliminating 90% of system administrators, to limit access and improve its
  least-privilege posture.
  
  
  
  
  THE TARGET BREACH
  
  
  The 2013 Target breach
  [https://www.beyondtrust.com/blog/entry/are-you-a-target-investigating-security-breaches-with-kevin-johnson/]
  impacted roughly 70 million customers. Hackers gained unauthorized access into
  Target’s systems through pilfered credentials of a third-party vendor, a heating
  and air conditioning contractor. The HVAC contractor had access to Target’s
  network, including permissions to upload executables. These privileges were far
  more than required for the contractors to perform their maintenance work.
  
  
  By restricting access permissions to the fewest resources, functions, and areas
  necessary for the HVAC company, Target likely would have avoided the breach and
  the subsequent fallout. Enforcing least privilege for vendor access
  [https://www.beyondtrust.com/blog/entry/what-is-vendor-privileged-access-management-vpam]
  is a critical, but often overlooked and under-implemented, security best
  practice.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  EMERGING PRIVILEGED THREAT VECTORS
  
  
  
  Digital transformation (DX) continues to drive the creation of new business
  opportunities and help organizations adapt to a changing work environment. At
  the same time, many DX initiatives significantly increase the privileged threat
  surface. Here are a few examples:
  
  
  
  OPERATIONAL TECHNOLOGY (OT), INTERNET OF THINGS (IOT), AND EDGE COMPUTING
  
  
  A rapidly expanding universe of connected “things”—from health monitoring and
  delivery devices to industrial controls to wearables, smart appliances, and
  more—presents enormous challenges for IT. Identifying and securely onboarding
  legitimate devices at scale is itself a massive undertaking. Many of these
  endpoints also comprise the backbone of edge computing, which is powering a new
  wave of mobility and digital transformation by enabling data processing to occur
  closer to where it is needed, reducing latency times. Other equipment, such as
  in OT environments, was not natively designed to the security requirements
  necessitated by our hyperconnected world today.
  
  
  IoT devices, especially older devices that are no longer supported, frequently
  suffer serious security limitations, such as the inability to have the software
  hardened or firmware updated, and hard-coded passwords. IoT is also vulnerable
  to exploits such as man-in-the-middle attacks (MiTM), when an attacker
  intercepts and / or possibly modifies data communicated between two systems.
  
  
  
  Long ago, large-scale IoT hacks made the leap from theory to reality. DDOS
  attacks leveraging IoT botnets comprised of as many as a million “things” (such
  as cameras, thermostats, DVRs, and even light bulbs) knocked many U.S. East
  Coast businesses and the nation of Liberia offline, in separate incidents. The
  scale and scope of such attacks could increase exponentially as 5G becomes more
  widespread.
  
  
  
  While IoT and all the “smart” things certainly pose some unique security
  challenges, when it comes down to it, organizations need to be able to enforce
  least privilege and / or application control over any endpoint with an
  IP—traditional or IoT. Network segmentation for IoT devices is one way to
  broadly restrict the permissions of IoT devices and the associated systems and
  operations, while role-based access permissions should also be enforced as a
  best practice. The privileged access pathways across edge networks must also be
  managed and secured.
  
  
  
  
  ROBOTIC PROCESS AUTOMATION (RPA)
  
  
  By automating mundane business tasks, robotic process automation can reduce
  manual effort and errors—and often without the heavy lift needed of other
  digital transformation projects, like DevOps. RPA security may be overlooked by
  IT because it involves software robots, service accounts, and other machine
  accounts rather than human identities, and also because it tends to occur as
  shadow IT.
  
  
  
  RPA processes, applications, toolsets, and workflows commonly involve privileges
  that must be managed. RPA bots, after all, need the same application and access
  as humans. For instance, a software robot may need to log into a business
  system, then copy and transmit data to another process or system. RPA
  credentials are often shared by software robots, which multiplies the risk
  exposure should the credentials be compromised. Ideally, credentials are managed
  with a unique privilege for each software robot, and separation of privileges is
  applied to minimize risk.
  
  
  
  
  DEVOPS
  
  
  While DevOps has been in force for over a dozen years, it’s often the core
  engine of IT innovation at organizations today. DevOps tools and processes
  exacerbate many of the security issues found in other parts of the enterprise
  due to the focus on speed and automation, combined with the scale and elasticity
  of the cloud. While DevSecOps is gaining adoption and helping to improve overall
  DevOps security
  [https://www.beyondtrust.com/blog/entry/devops-security-best-practices], risks
  are still abundant.
  
  
  
  Some frequent privilege-related issues of DevOps environments include:
  
  
  * Inadequate privileged controls around applications and tools
   
  * Overprivileged users
   
  * Lack of segmentation between dev and production environments
   
  * Highly-privileged credentials embedded in CI/CD tools, code, and applications
   
  * Misconfigurations or errors providing too much privileged access
   
  * Sharing privileged accounts
   
  
  
  All the human, machine, toolset, application, and other privileges in DevOps
  workflows should be discovered and managed. The added challenge, however, is to
  achieve least privilege across CI/CD pipelines without hindering workflows.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  CHALLENGES TO APPLYING LEAST PRIVILEGE
  
  
  
  If excessive privileges pose such a vexing threat, why don’t organizations rein
  them in? The short answer is companies do—or try to—via policies and technology
  solutions, but numerous factors contribute to make dialing in the optimal amount
  of privilege rights and access a challenge.
  
  
  
  
  LACK OF VISIBILITY AND AWARENESS
  
  
  Lack of visibility and awareness of all the privileged accounts, assets, and
  credentials across an enterprise stands as one pervasive stumbling block for
  companies in effectively managing privileges. Independent research, surveys, and
  audits show permanent accounts and orphaned accounts with high degrees of
  privilege are spread across the physical, virtual, and cloud environments of
  most organizations. To complicate matters, manifold systems and applications
  have easily-guessable default credentials. Until these applications (such as
  shadow IT
  [https://www.beyondtrust.com/blog/entry/most-common-and-dangerous-types-of-shadow-it])
  and systems are discovered, properly configured, and brought under management,
  they pose a high risk for exploit by a hacker or through malware.
  
  
  
  
  CULTURAL CHALLENGES
  
  
  Employee resistance often rears its head in the face of least-privilege
  policies. If privileged access controls are overly restrictive, they can disrupt
  user workflows, causing frustration and hindering productivity. To obviate
  helpdesk requests and end-user headaches (users rarely complain about having too
  many privileges), IT admins traditionally provision end users with broad sets of
  privileges. This superfluous access translates into a broadened attack surface.
  
  
  
  Role-based access, administered through Active Directory or another rights
  management solution, can help enforce general rules around a role, a group, a
  team, or an individual’s set of privileges. However, an individual’s role is
  often fluid and can evolve over the course of employment. Eventually, the
  employee accumulates new responsibilities and corresponding privileges—while
  still keeping privileges they no longer use or are irrelevant to their role.
  Moreover, a drawback to role-based access is it lacks the contextual granularity
  to only provide access when required for a specific use. Of course, the
  explosion of machine identities and ephemeral privileged accounts (in
  cloud/virtualized environments), further complicates this picture.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  BENEFITS OF LEAST PRIVILEGE FOR SECURITY & PRODUCTIVITY
  
  
  
  According to the Microsoft Vulnerabilities Report 2023
  [https://www.beyondtrust.com/resources/whitepapers/microsoft-vulnerability-report]
  (published by BeyondTrust), removing local admin rights and controlling
  execution—important least privilege practices—have historically mitigated 75% of
  Microsoft’s critical vulnerabilities.
  
  
  
  Unfettered privileged rights and access essentially equates to uncapped
  potential for damage. The more privileges a user, account, or process amasses,
  the greater the potential for abuse, exploitation, or error. Implementing least
  privilege not only reduces the likelihood of a breach occurring in the first
  place, but it helps limit the scope of a breach, should one happen.
  
  
  
  Least privilege confers several high-level benefits, including:
  
  
  
  1) A condensed attack surface: Limiting privileges for people, processes, and
  applications/machines diminishes the pathways and ingresses for exploit.
  
  
  
  2) Reduced malware infection and propagation: Least privilege helps dramatically
  reduce malware infection and propagation, as the malware (such as SQL injections
  or ransomware) should be denied the ability to elevate processes to allow it to
  install or execute.
  
  
  
  3) Improved operational performance: When it comes to applications and systems,
  restricting privileges to the minimal range of processes to perform an
  authorized activity reduces the chance of incompatibility issues cropping up
  between other applications or systems, and helps reduce the risk of downtime.
  
  
  
  4) Easier to achieve, and prove, compliance: By constraining the possible
  activities, least privilege enforcement helps create a less complex, and
  subsequently, a more audit-friendly environment. Moreover, many compliance
  regulations (including HIPAA, PCI DSS, FDDC, Government Connect, FISMA, and SOX)
  require organizations to apply least-privilege access policies to ensure proper
  data stewardship and systems security. For instance:
  
  
  * The US federal government’s FDCC mandate states federal employees must log in
   to PCs with standard user privileges.
   
  * The HIPAA Privacy Rule
   [http://www.hhs.gov/hipaa/for-professionals/privacy/laws-regulations/index.html]
   provides guidelines for the establishment of least privilege, such as
   restricting access to data (i.e., a subset of a patient record as opposed to
   the entire record) based on the “minimum necessary use” to accomplish a
   specific purpose.
   
  * PCI DSS
   [https://www.pcisecuritystandards.org/pdfs/pci_dss_saq_navigating_dss.pdf]
   states organizations who process or store credit card data must restrict
   access to cardholder data by business need to know, and specifically invokes
   the use of least privilege user accounts [7.1.1 Restriction of access rights
   to privileged user IDs to least privileges necessary to perform job
   responsibilities; 7.2.2 Assignment of privileges to individuals based on job
   classification and function].
   
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  PRINCIPLE OF LEAST PRIVILEGE & BEST PRACTICES
  
  
  
  So, what does wholly adopting the principles of a least-privilege computing
  environment look like? How does your organization get there?
  
  
  
  Here are some best practices and strategies to help you bake in least privilege
  access across your organization:
  
  
  
  1) Perform a privilege audit to discover, and bring under policy management, all
  privileged accounts and credentials for employees, contractors, and vendors.
  This should include all user and local accounts, SSH keys, Windows and Linux
  groups, DevOps secrets, and default and hard-coded passwords for human and
  machine identities.
  
  
  
  2) Remove admin rights on endpoints. As opposed to provisioning default access,
  default all users to standard privileges, while enabling elevated privileges for
  applications and to perform specific tasks. If access is not initially provided
  and is required, the user can submit a help desk request for approval.
  
  
  
  3) Remove all root and admin access rights to servers and reduce every user to a
  standard user. This dramatically reduces the attack surface and enhances server
  security
  [https://www.beyondtrust.com/blog/entry/server-security-best-practices-for-unix-linux-systems]
  to safeguard your most sensitive assets.
  
  
  
  4) Segment systems and networks to broadly separate users and processes based on
  different levels of trust, needs, and privilege sets.
  
  
  
  5) Enforce separation of privileges
  [https://www.beyondtrust.com/blog/entry/how-separation-privilege-improves-security].
  This includes separating administrative account functions from standard account
  requirements, separating auditing/logging capabilities within the administrative
  accounts, and separating system functions (read, edit, write, execute, etc.).
  
  
  
  6) Implement just-in-time privileges (JIT)
  [https://www.beyondtrust.com/blog/entry/just-in-time-privileged-access-management-jit-pam-the-missing-piece-to-achieving-true-least-privilege-maximum-risk-reduction].
  Ideally, privileged access should be time-bound and/or bound by completion of a
  specific task or process. Eliminate always-on / standing privileges
  [https://www.beyondtrust.com/resources/glossary/zero-standing-privileges] as
  much as is practical, with zero standing privileges
  [https://www.beyondtrust.com/resources/glossary/zero-standing-privileges] as the
  ideal state. This means privileges should only be elevated on an as-needed basis
  for specific applications and tasks only for the moment of time they are needed,
  without requiring administrative credentials or exposing passwords. This is
  sometimes called “privilege bracketing.”
  
  
  
  7) Implement one-time-use credentials. For instance, use password "safes," where
  a one-time-password (OTP)
  [https://www.beyondtrust.com/blog/entry/one-time-password-otp-solutions-for-privileged-access]
  for privileged accounts is "checked out" until an activity is completed,
  immediately after which time, it is checked back in. The used password is then
  retired.
  
  
  
  8) Replace hardcoded credentials with APIs allowing credentials to be retrieved
  from password safes. Alternatively, such as with DevOps and CI/CD toolsets,
  replace hardcoded credentials with dynamic secrets.
  
  
  
  9) Ensure individual actions are traceable. This can be accomplished through
  user IDs as well as via auditing and other tools, to provide oversight and
  accountability.
  
  
  
  10) Extend least privilege policies beyond the perimeter. Least privilege
  security controls must also be applied to vendors, contractors, and all remote
  access sessions.
  
  
  
  
  11) Analyze and report on all privileged accounts and access. This should
  encompass shared admin accounts, application accounts (A2A), local admin
  accounts, service accounts, database accounts, cloud and social media accounts,
  devices (including IoT), SSH keys, and more. Auditing activities can also
  include capturing keystrokes and screens.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  LEAST PRIVILEGE ACCESS & ZERO TRUST
  
  
  
  Least privilege is one of the foundational principles of zero trust security
  models. Zero trust architectures, such as published in NIST SP 800-207
  [https://www.beyondtrust.com/resources/whitepapers/mapping-beyondtrust-capabilities-to-nist-sp-800-207],
  were developed to address the increasingly distributed, perimeterless IT
  computing environment. At the core, zero trust frameworks treat users,
  applications, endpoints, and other assets as untrusted. Zero trust layers on
  contextual, in-the-moment data to enable decisions on granting, restricting, and
  terminating access.
  
  
  
  The zero trust model requires many different technologies and solutions.
  However, applying continuous authentication—such as after an interval (day or
  hours) of time has passed or for different levels of access, microsegmentation,
  and least privilege will put you in a strong position to achieve zero trust and
  reduce enterprise risk.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  LEAST PRIVILEGE SOLUTIONS
  
  
  
  So, now that you have some best practices and strategies, what are the best
  tools or technologies to implement least privilege?
  
  
  
  Network segmentation, such as the creation of different zones through firewall
  configuration and rules, is one key way to enforce least privilege in broad
  strokes. By controlling access and movement between zones, which may have a
  different mix of applications and services, firewalls can restrict users broadly
  based on privileges. For instance, firewalls are used to create a DMZ
  (demilitarized zone) between a corporate network and the public network.
  Firewalls can also easily block unauthorized privilege elevation activity (such
  as from service requests) based on rules applicable to the zone.
  
  
  
  Privilege Access Management (PAM)
  [https://www.beyondtrust.com/resources/glossary/privileged-access-management-pam],
  also called Privileged Identity Management (PIM), Privileged Account Management,
  or just Privilege Management, involves the creation and deployment of solutions
  and strategies to manage privileged accounts across an environment. Holistic PAM
  solutions discover and bring under management all privileged accounts and
  credentials, both human and machine. These solutions remove admin rights
  [https://www.beyondtrust.com/blog/entry/removing-users-from-the-local-administrators-group]
  from users, and instead, elevate privileges for authorized applications or tasks
  as needed, ideally in alignment with just-in-time access models. Application
  control capabilities are an important component of many PAM solutions
  [https://www.beyondtrust.com/blog/entry/what-is-least-privilege], helping ensure
  only authorized applications execute approved functions or communications. While
  identity and access management (IAM) controls
  [https://www.beyondtrust.com/blog/entry/what-is-identity-and-access-management-and-why-is-it-a-vital-it-security-layer]
  provide authentication of identities, PAM allows organizations to control
  authorization over ability to perform a granular activity. IAM and PAM solutions
  working together can help provide fine-grained control, visibility, and
  auditability over all credentials and privileges. The most mature PAM solutions
  can also extend least privilege management best practices beyond the perimeter
  to vendors and remote workers, ensuring more granular control than is possible
  with VPNs or other remote access tools. Privileged access management
  technologies, especially those applying just-time-access, are also a principle
  enabler of zero trust environments.
  
  
  
  Systems hardening
  [https://www.beyondtrust.com/resources/glossary/systems-hardening], entailing
  the removal of superfluous programs, accounts, and services (such as with a
  server connecting to the internet), and the closing of unneeded firewall ports,
  is another common mechanism for applying least privilege. Systems hardening not
  only markedly improves security posture by reducing the attack surface, but it
  also reduces complexity and simplifies the environment. PAM solutions are also
  one of the many tools enabling organizations to harden devices, software,
  applications, and other assets.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  HOW TO IMPLEMENT LEAST PRIVILEGE
  
  
  
  Effective implementation of least privilege will involve policies, procedures,
  technologies—and proper configuration of those technologies. Formalizing a
  policy should also help you get a better handle on where your sensitive data
  resides, and who can access it.
  
  
  
  Most likely, various aspects of least privilege will need to be phased in over
  time, rather than implemented all at once. The best path forward for any
  organization will always be tailored to its unique needs and resources.
  
  
  
  The more mature a least-privilege policy implementation, the more effective an
  organization will be in condensing the attack surface, minimizing threat
  windows, mitigating the impact of attacks (by hackers, malware, or insiders),
  enhancing operational performance, and in reducing the risk from and impact of
  user errors. Even as the threat surface rapidly evolves via advances in
  automation, generative AI, and more, the benefits of least privilege access
  remain as essential and timeless as ever.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  ----------
  Tags: