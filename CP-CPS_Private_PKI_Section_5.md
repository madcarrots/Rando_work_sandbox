# 5 FACILITY, MANAGEMENT, AND OPERATIONAL CONTROLS

SSL.com implements and maintains a comprehensive security program to protect Certificate Data and all aspects of the Certificate Management Process.

SSL.com's security plan is based on an annual risk assessment designed to identify and assess threats and to implement appropriate steps to address these threats.

## 5.1 Physical controls

SSL.com implements and maintains physical security controls to restrict access to the hardware and software used for SSL.com PKI operations.

### 5.1.1 Site location and construction

SSL.com operates from a secure commercial datacenter. All critical facilities are housed in secure areas with appropriate security barriers and entry controls. These are protected from unauthorized access, damage and/or interference.

### 5.1.2 Physical access

SSL.com equipment is physically secured and protected from unauthorized access.

Measures to secure datacenter equipment include two-factor access control through physical cards and biometric readers, 24-hour video surveillance and full-time human security presence which monitors and logs all access.

Support and vetting rooms where RA functions are performed are secured by controlled access and keyed-lock doors. Access card use is logged by the building security system. Video monitoring is employed to record all access to the location. Unauthorized personnel needing to enter into the physical location of a secure datacenter or the area where RA functions are performed shall never be left without oversight by an authorized person.

### 5.1.3 Power and air conditioning

SSL.com equipment is maintained in a facility which utilizes uninterrupted power supply (UPS) units and automatic backup generators to ensure multiple redundant power sources.

HVAC systems for heating, cooling and ventilation are sufficient to support the operation of the CA system.

### 5.1.4 Water exposures

SSL.com equipment is maintained in a facility which provides protection against water exposures.

### 5.1.5 Fire prevention and protection

SSL.com equipment is maintained in a facility equipped with automatic engineered fire suppression systems designed to preserve electronic equipment.

### 5.1.6 Media storage

Any media used by SSL.com is securely handled and stored to protect it from damage, theft and unauthorized access.

Media containing Private Key material is handled, packaged and stored in a manner compliant with the requirements for the sensitivity level of the information it protects or to which it provides access.  Storage protection of CA Private Key material shall be consistent with stipulations in §5.1.2.

### 5.1.7 Waste disposal

Paper documents or any other printed material containing SSL.com PKI information or related confidential information are securely disposed of by shredding or destruction by an approved service. Removable media containing SSL.com PKI information or related confidential information are securely disposed of by complete destruction of the media, or by the use of an approved utility to wipe or overwrite removable media.

### 5.1.8 Off-site backup

An off-site location is used for the storage and retention of SSL.com PKI backup software and data. The off-site storage facility is available to authorized personnel 24 hours per day 7 days per week for the purpose of retrieving software and data. The off-site storage facility has appropriate levels of physical security in place and is protected against fire and unauthorized access.

## 5.2 Procedural controls

### 5.2.1 Trusted roles

PKI functions are performed by individuals working within clearly defined trusted roles. These trusted roles are established and maintained to share responsibility, limit the ability for action by individual participants, and securely separate duties and functions within the PKI. Trusted roles include but are not limited to:

- **CA Administrator:** Authorized to install, configure and maintain the CA systems used for Certificate life-cycle management.
- **RA Administrator:** Certificate generation and revocation, and end entity creation and deletion
- **System Administrator:** Responsible for operating the CA and RA systems on a day-to-day basis.
- **Network Administrator:** Responsible for operating networking equipment on a day-to-day basis.
- **Vetting Agent:** Responsible for validating the authenticity and integrity of data to be included within Certificates via a suitable RA system
- **Security Auditor** Responsible for internal auditing of CAs and RAs and responsible for administering the implementation of the security practices. This sensitive role shall be free from conflict of interest that might prejudice the impartiality of their duties, e.g. a person assigned with the Security Auditor role shall not audit operations performed partially or entirely by the same person. Security Auditors shall review, maintain, and archive audit logs, and perform or oversee internal audits (independent of formal compliance audits) to ensure that CAs and RAs are operating in accordance with any applicable CP/CPS.

### 5.2.2 Number of persons required per task

PKI-sensitive operations shall require active participation by SSL.com personnel. This participation shall require at least two trusted individuals to perform the required duties of their specified roles.

CA Private Keys shall be backed up, stored, and recovered only by personnel in Trusted Roles using, at least, dual control in a physically secured environment.

With the exception of audit functions, multi-party control shall not be achieved using personnel that operate under the Security Auditor role. The following tasks shall require two or more persons:

- Generation, activation, and backup of CA keys
- Performance of CA administration or maintenance tasks
- Archiving or deleting CA audit logs. At least one of the participants shall serve in the Security Auditor role
- Physical access to CA equipment
- Access to any copy of the CA cryptographic module

Systems used to process and approve EV Certificate Requests shall require actions by at least two persons in Trusted Roles before issuing an EV Certificate.

### 5.2.3 Identification and authentication for each role

All individuals authorized in trusted roles must properly authenticate themselves to the relevant CA or RA before performing their duties.

### 5.2.4 Roles requiring separation of duties

Any trusted role as defined in 5.2.1 intrinsically possesses duties and/or capabilities separate from those in other trusted roles.

As described in 5.2.2, validation of EV certificate requests shall require the participation of at least two validation specialists. For example, one Validation Specialist may review and verify all the Applicant information and a second Validation Specialist may approve issuance of the EV Certificate.

## 5.3 Personnel controls

### 5.3.1 Qualifications, experience, and clearance requirements

SSL.com verifies the identity and trustworthiness of all personnel, whether as an employee, agent, or an independent contractor, prior to the engagement of such person(s).

Any personnel occupying a trusted role (as defined in 5.2.1) must possess suitable experience and be deemed qualified by SSL.com.

### 5.3.2 Background check procedures

All individuals performing trusted role functions have cleared current SSL.com security screenings or background checks appropriate for that role. Background check procedures verify information relevant to the role and may include identity verification (through government-issued photo), as well as examination of one's public record (through research of previous employment history, relevant qualifications and criminal records).

### 5.3.3 Training requirements

Personnel in trusted roles shall undergo SSL.com training prior to performing any duties as part of that role.

SSL.com shall provide comprehensive training to all personnel performing information verification duties with skills-training that covers:

- Basic Public Key Infrastructure knowledge
- Authentication and vetting policies and procedures (including SSL.com’s CP/CPS)
- Common threats to the information verification process (including phishing and other social engineering tactics).

SSL.com shall ensure that all personnel performing validation duties be trained to and maintain an appropriate skill level. Training shall include an initial examination and periodic retraining as required to reflect changes in PKI operations. All training shall be thoroughly documented.

Training for personnel involved in issuance of EV Certificates shall include an internal examination reflecting the EV Certificate validation criteria.

### 5.3.4 Retraining frequency and requirements

All personnel occupying any Trusted Role shall maintain skill levels consistent with that Trusted Role and shall undergo periodic retraining related to that Role. SSL.com’s retraining programs shall reflect and address any relevant changes to the SSL.com PKI and related operations.

SSL.com shall maintain records of all retraining performed.

### 5.3.5 Job rotation frequency and sequence

SSL.com shall ensure that changes in personnel, including changes in personnel occupying Trusted Roles, shall not affect the operations, services and/or security of the SSL.com PKI and related functions.

### 5.3.6 Sanctions for unauthorized actions

SSL.com employees and agents failing to comply with the SSL.com CP/CPS, whether through negligence or malicious intent, are subject to administrative or disciplinary actions, including termination of employment or agency and criminal sanctions.

Any SSL.com employee holding a Trusted Role shall be immediately removed from that role following identification of any unauthorized actions.

SSL.com management will review the underlying details of an incident and promptly issue an applicable resolution report once a conclusion has been reached.

Resolution may result in termination, other sanctions, and/or demotion to a new non-trusted role within the SSL.com PKI.

Resolution may also require retained personnel to undergo additional training programs as determined by SSL.com management.

### 5.3.7 Independent contractor requirements

Any independent contractor or Delegated Third Party’s personnel involved in the issuance of a Certificate via the SSL.com PKI shall be fully subject to the SSL.com's CP/CPS, including training and skills requirements (Section 5.3.3), sanctions (5.3.6), document retention and event logging requirements (5.4.1).

### 5.3.8 Documentation supplied to personnel

SSL.com shall provide authorized personnel with any relevant documentation needed to carry out job functions or duties. All documentation required for duties, functions and obligations for any personnel utilizing the SSL.com PKI and related functions shall be available to authorized personnel and properly maintained/updated.

Documentation which accurately reflects current operations and processes shall be made readily available.

Access to documentation related to specific Trusted Roles may be limited to personnel occupying those roles.

Relevant materials are systematically disseminated through SSL.com’s training and retraining programs.

Any changes to operations, processes or practices related to the SSL.com PKI shall be recorded and reflected in the related documentation.

## 5.4 Audit logging procedures

### 5.4.1 Types of events recorded

All events relating to the security of Certificate Systems, Certificate Management Systems, Root CA Systems and Delegated Third Party Systems of SSL.com and of each Delegated Third Party are recorded in audit log files.

Security audit logs shall be automatically generated whenever possible. Where this is not an option, a logbook, paper form, or other physical mechanism shall be used.

All security audit logs are retained (per §5.4.3 and §5.5) and made available to Qualified Auditors as requested.

Log entries include at least the following elements:

1. Date and time of event;
2. Identity of the person making the journal entry (when applicable); and
3. Description of the event.

#### 5.4.1.1 Types of events recorded for publicly-trusted TLS and Code Signing Certificates

For publicly-trusted TLS and Code Signing Certificates, SSL.com shall record at least the following events:

1. CA certificate and key lifecycle events, including:
    a. Key generation, backup, storage, recovery, archival, and destruction;
    b. Certificate requests, renewal, and re‐key requests, and revocation;
    c. Approval and rejection of certificate requests;
    d. Cryptographic device lifecycle management events;
    e. Generation of Certificate Revocation Lists;
    f. Signing of OCSP Responses (as described in §4.9 and §4.10); and
    g. Introduction of new Certificate Profiles and retirement of existing Certificate Profiles.

2. Subscriber Certificate lifecycle management events, including:
    a. Certificate requests, renewal, and re-key requests, and revocation;
    b. All verification activities stipulated in the Baseline Requirements and this CP/CPS;
    c. Approval and rejection of certificate requests;
    d. Issuance of Certificates;
    e. Generation of Certificate Revocation Lists; and
    f. Signing of OCSP Responses (as described in §4.9 and §4.10).
    g. Multi-Perspective Issuance Corroboration attempts from each Network Perspective, minimally recording the following information:
        i. an identifier that uniquely identifies the Network Perspective used;
        ii. the attempted domain name and/or IP address; and
        iii. the result of the attempt (e.g., "domain validation pass/fail", "CAA permission/prohibition").
    h. Multi-Perspective Issuance Corroboration quorum results for each attempted domain name or IP address represented in a Certificate request (i.e., "3/4" which should be interpreted as "Three (3) out of four (4) attempted Network Perspectives corroborated the determinations made by the Primary Network Perspective).

3. Security events, including:
    a. Successful and unsuccessful PKI system access attempts;
    b. PKI and security system actions performed;
    c. Security profile changes;
    d. Installation, update and removal of software on a Certificate System;
    e. System crashes, hardware failures, and other anomalies;
    f. Relevant router and firewall activities (as described in §5.4.1.3); and
    g. Entries to and exits from the CA facility.

#### 5.4.1.2 Types of events recorded for publicly-trusted Time-stamping Certificates

For publicly-trusted Time-stamping Certificates, SSL.com shall record at least the following events:

1. Physical or remote access to a timestamp server, including the time of the access and the identity of the individual accessing the server,
2. History of the timestamp server configuration,
3. Any attempt to delete or modify timestamp logs,
4. Security events, including:
    a. Successful and unsuccessful Timestamp Authority access attempts;
    b. Timestamp Authority  actions performed;
    c. Security profile changes;
    d. System crashes, hardware failures, and other anomalies; and
    e. Firewall and router activities;
5. Revocation of a timestamp certificate,
6. Major changes to the timestamp server’s time, and
7. System startup and shutdown.

#### 5.4.1.3 Router and firewall activities logs

Logging of router and firewall activities necessary to meet the requirements of §5.4.1.1, Subsection 3(f) SHALL at a minimum include:

1. Successful and unsuccessful login attempts to routers and firewalls; and
2. Logging of all administrative actions performed on routers and firewalls, including configuration changes, firmware updates, and access control modifications; and
3. Logging of all changes made to firewall rules, including additions, modifications, and deletions; and
4. Logging of all system events and errors, including hardware failures, software crashes, and system restarts.
  
### 5.4.2 Frequency of processing audit log

SSL.com shall monitor the integrity of the logging processes for application and system logs through continuous automated monitoring and alerting or through a human review to ensure that logging and log‐integrity functions are effective. If a human review is utilized and the system is online, the process shall be performed at least once every 31 days.

SSL.com shall monitor audit logs through continuous automated monitoring and alerting or through a human review for possible issues, such as:

- Anomalies and/or irregularities
- Malicious activity

Each review should be reported to the appropriate personnel by summarizing findings, if any.

Investigations which result from reported findings, recommendations made based on these investigations, and actions taken to address reported issues are recorded and made available to auditors as requested.

### 5.4.3 Retention period for audit log

SSL.com and each Delegated Third Party SHALL retain, for at least two (2) years:

1. CA certificate and key lifecycle management event records (as set forth in §5.4.1.1 (1)) after the later occurrence of:
    a. the destruction of the CA Private Key; or
    b. the revocation or expiration of the final CA Certificate in that set of Certificates that have an X.509v3 `basicConstraints` extension with the `cA` field set to true and which share a common Public Key corresponding to the CA Private Key;
2. Subscriber Certificate lifecycle management event records (as set forth in §5.4.1.1 (2)) after the expiration of the Subscriber Certificate;
3. Timestamp Authority data records (as set forth in §5.4.1.2) after the revocation or renewal of the Timestamp Certificate private key;
4. Any security event records (as set forth in §5.4.1.1 (3)) after the event occurred.

**Note:** While these Requirements set the minimum retention period, SSL.com MAY choose a greater value as more appropriate in order to be able to investigate possible security or other types of incidents that will require retrospection and examination of past audit log events.

### 5.4.4 Protection of audit log

SSL.com shall collect and regularly analyze relevant audit data for any attempts to violate the integrity of any element of the SSL.com PKI. SSL.com audit logs may be viewed only by authorized personal and auditors.

SSL.com shall decide whether and which audit records may be viewed by others and under what circumstances it shall make those records available.

SSL.com shall protect logs from modification and destruction and maintain digital logs in an encrypted format.

### 5.4.5 Audit log backup procedures

SSL.com shall perform an onsite backup of the audit log daily. The backup process includes at least a weekly copy of the audit log from the SSL.com facility and storage at a secure, offsite location.

### 5.4.6 Audit collection system (internal vs. external)

The security audit process shall run independently of the SSL.com PKI certificate issuance software. Security audit processes shall be invoked at system start up and cease only at system shutdown. Security audit processes shall not be capable of being circumvented.

### 5.4.7 Notification to event-causing subject

SSL.com shall not be required to give any notice to the individual, Organization, device, or application that caused any event which invoked logging.

### 5.4.8 Vulnerability assessments

SSL.com and Delegated Third Parties perform regular vulnerability assessments and penetration tests (at least once a year) covering all Certificate Systems. These assessments document and implement a vulnerability correction process to identify, review and remediate issues and threats.

Vulnerability assessments may also be performed:

- Within one week of receiving a request from the CA/Browser Forum
- After any system or network changes that the CA determines are significant, and
- At least once per quarter, on public and private IP addresses identified by the CA or Delegated Third Party as the CA’s or Delegated Third Party’s Certificate Systems

Additionally, SSL.com and Delegated Third Parties perform an annual Risk Assessment to:

- Identify foreseeable internal and external threats that could result in unauthorized access, disclosure, misuse, alteration, or destruction of any Certificate Data or Certificate Management Processes;
- Assess the likelihood and potential damage of these threats, taking into consideration the sensitivity of the Certificate Data and Certificate Management Processes; and
- Assess the sufficiency of the policies, procedures, information systems, technology, and other arrangements that SSL.com has in place to counter such threats.

## 5.5 Records archival

### 5.5.1 Types of records archived

SSL.com and each Delegated Third Party shall archive all documentation relating to certificate requests and the verification thereof, and all Certificates and revocation thereof.

Additionally, SSL.com and each Delegated Third Party SHALL archive:

1. Documentation related to the security of their Certificate Systems, Certificate Management Systems, Root CA Systems, and Delegated Third Party Systems; and
2. Documentation related to their verification, issuance, and revocation of certificate requests and Certificates.

SSL.com may also archive other records relating to:

1. CA certificate and key lifecycle
2. Subscriber Certificate lifecycle management
3. Security operations

SSL.com may also archive any other documents deemed relevant to SSL.com PKI operations.

### 5.5.2 Retention period for archive

Archived audit logs (as set forth in §5.5.1 SHALL be retained for a period of at least two (2) years from their record creation timestamp, or as long as they are required to be retained per §5.4.3, whichever is longer.

Additionally, SSL.com and each Delegated Third Party SHALL retain, for at least two (2) years:

1. All archived documentation related to the security of Certificate Systems, Certificate Management Systems, Root CA Systems and Delegated Third Party Systems (as set forth in §5.5.1); and
2. All archived documentation relating to the verification, issuance, and revocation of certificate requests and Certificates (as set forth in §5.5.1) after the later occurrence of:
    a. such records and documentation were last relied upon in the verification, issuance, or revocation of certificate requests and Certificates; or
    b. the expiration of the Subscriber Certificates relying upon such records and documentation.

Note: While these Requirements set the minimum retention period, SSL.com MAY choose a greater value as more appropriate in order to be able to investigate possible security or other types of incidents that will require retrospection and examination of past records archived.

For any other archived records, set forth in §5.5.1 (1) to (3), SSL.com shall apply mutatis mutandis the retention rules set forth in §5.4.3.

For any other archived documents deemed relevant to SSL.com PKI operations, set forth in §5.5.1, appropriate retention period shall be applied.

### 5.5.3 Protection of archive

Archives shall be retained and protected against modification or destruction for the minimum time period specified in §5.5.2.

SSL.com shall take all appropriate measures to ensure that only authorized access is allowed with respect to any archives.

### 5.5.4 Archive backup procedures

SSL.com shall utilize secure and verifiable backup procedures to provide a complete and readily accessible backup archive in the event of loss or damage to a primary archive.

Any backup archive shall be maintained at a separate, secure location from the primary archive. Access to any backup archive shall employ protections equivalent to the security protocols of its primary archive.

Backup archive maintenance shall include periodic transfer of archived data to new media to prevent data loss.

### 5.5.5 Requirements for time-stamping of records

All archived documents shall include the date and time of creation, occurrence or modification. The date and time for any document archived shall derive these from a trusted time source as defined in §6.8.

### 5.5.6 Archive collection system (internal or external)

SSL.com shall employ internal systems to collect and maintain a primary archive.

### 5.5.7 Procedures to obtain and verify archive information

SSL.com's primary and backup archives shall only be accessible by authorized SSL.com personnel and qualified auditors.

SSL.com may upon request, at its sole discretion, release specific records related to requests by a Subscriber, a Relying Party or an authorized agent of a Subscriber or Relying Party.

SSL.com shall not release archives in their entirety, except as required by law.

SSL.com may require compensation and fees for any costs incurred in accessing or retrieving any requested archival data.

SSL.com shall verify the integrity and readability of primary and backup archives through periodic random testing.

## 5.6 Key changeover

SSL.com shall ensure a securely managed changeover of Private Keys for any expiring Root Certificate utilized by the SSL.com PKI.

For any key changeover, SSL.com shall maintain, for a temporary and strictly delimited period, concurrent Root Certificates (the original, expiring Root Certificate with the expiring Private Key and the new Root Certificate with the new Private Key) to maintain a seamless transition of functions and services. This period shall end upon the expiration of the original Root Certificate's Private Key.

SSL.com shall provide the new Public Key to Subscribers and Relying Parties through the delivery methods detailed in §6.1.4.

Similar key changeover and key distribution methods shall be employed to manage the expiration of any Cross-Certified Subordinate CA Certificate.

## 5.7 Compromise and disaster recovery

SSL.com maintains a Business Continuity Plan which details required steps, procedures and actions to restore operations in a timely manner when any function of the SSL.com PKI has been negatively impacted by incidents or disasters.

### 5.7.1 Incident and compromise handling procedures

#### 5.7.1.1 Incident Response and Disaster Recovery Plans

SSL.com maintains policies and procedures to respond to potential or actual security compromises, natural disasters, and similar events. Documents addressing these needs include (but are not limited to) an Incident Management Policy (IMP), a Business Continuity and Disaster Recovery Plan and other related resources.

SSL.com shall review, test and update these policies and procedures as needed.

#### 5.7.1.2 Mass Revocation Plans

SSL.com maintains a comprehensive and actionable plan for mass revocation events, performs annual testing of the mass revocation plan, and incorporates lessons learned into such plan in order to continually improve its preparedness for mass revocation events over time.

SSL.com's mass revocation plan includes clearly defined, actionable, and comprehensive procedures designed to ensure rapid, consistent, and reliable response to large-scale certificate revocation scenarios. SSL.com is not required to publicly disclose its mass revocation plan or procedures but MUST make them available to its auditors upon request. SSL.com SHALL annually test, review, and update its plan and such procedures. SSL.com's mass revocation plan MAY be integrated into the SSL.com's incident response, business continuity, disaster recovery, or other similar plans or procedures, provided that provisions governing mass revocation events remain clearly identifiable and satisfy these requirements.

Mass revocation provisions include:

1. Activation criteria – specific, objective, and measurable thresholds at which the mass revocation plan is triggered based on the CA’s risk profile, issuance volumes, and operational capabilities;
2. Customer contact information – how subscriber and customer contact details are stored, maintained, and kept up to date;
3. Automation points – processes that are automated or could be automated, and those processes that require manual intervention;
4. Targets and timelines – for incident triage, revocation initiation, certificate replacement, and post-event review;
5. Subscriber notification methods – mechanisms for notifying impacted Subscribers;
6. Role assignments – roles and responsibilities of personnel responsible for initiating, coordinating, and executing the plan;
7. Training and education – training, awareness, and readiness activities for personnel responsible for, or supporting, the plan;
8. Plan testing – annual operational testing to assess readiness and demonstrate implementation feasibility, using one or more of tabletop exercises, simulations, parallel testing, or controlled test environments that DO NOT involve the revocation of active Subscriber Certificates; and
9. Post-test analysis and update schedule – how lessons learned from testing or live incidents are incorporated into the plan, and how often it is reviewed and updated.

### 5.7.2 Recovery Procedures if Computing Resources, Software, and/or Data Are Corrupted

SSL.com's Business Continuity Plan includes measures to address any incident in which Computing Resources, Software, and/or Data related to the SSL.com PKI are corrupted. Any affected operations shall be investigated and suspended as required. Any suspended activities shall be restored as quickly as possible commensurate with secure operation of the SSL.com PKI.

The Disaster Recovery Plan shall be tested at least annually.

### 5.7.3 Recovery Procedures After Key Compromise

SSL.com maintains procedures to address any incident wherein a CA Private Key is lost, destroyed, compromised, or suspected to be compromised. The same applies to the event of a compromise of the algorithms and parameters used to generate the Private Key and certificate. Steps taken after thorough investigation of the incident may include, but are not limited to:

- Revocation of the affected CA Private Key
- Generation of a new CA Key Pair
- Notification of all affected Subscribers
- Revocation of all Certificates signed with the affected CA Private Key

In case of a CA key compromise, SSL.com SHALL notify the relevant Application Software Suppliers without undue delay.

### 5.7.4 Business continuity capabilities after a disaster

SSL.com's Business Continuity Plan is designed to ensure secure continuous operations, and/or timely and secure restoration of affected operations, in the event of an incident or disaster.

## 5.8 CA or RA termination

In the event of the termination of any CA and/or RA associated with the SSL.com PKI, SSL.com shall provide timely notice of this information to all affected parties. In addition to prompt notification of termination to the appropriate parties, SSL.com shall:

- Destroy all associated Private Keys
- Revoke all affected unexpired Certificates in existence
- Transfer all responsibilities for the affected CA and/or RA to an entity approved by SSL.com.

In case of a transfer of SSL.com operations to another Trust Service Provider (TSP), a thorough migration plan will be created. All SSL.com Subscribers will receive due notice of this transfer. During the transfer, all critical operations are expected to continue to function properly according to this CP/CPS.

In the event that SSL.com decides upon a full CA business termination, SSL.com will provide a timely notice (including a schedule for business termination) to allow Subscribers and other affected parties to switch to another TSP. When the scheduled termination time is reached, SSL.com will revoke all issued Certificates, update the relevant CRLs and revoke its own root Certificates. Furthermore, it will inform interested third parties (such as Application Software Suppliers) about the end of its operation.