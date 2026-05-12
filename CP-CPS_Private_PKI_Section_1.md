---
title: SSL.com Private PKI CP/CPS
subtitle: Certificate Policy and Certification Practice Statement
version: 0.1
author:
    - SSL.com
date: May XX, 2026
copyright: |
    Copyright 2026 SSL.com

    This work is licensed under the Creative Commons Attribution 4.0 International license.
---

# 1 INTRODUCTION

SSL.com is a Certification Authority (CA) that issues digital Certificates to entities and individuals according to the SSL.com Private PKI Certificate Policy and Certification Practice Statement (CP/CPS). SSL.com performs Public Key life-cycle functions that include receiving certificate requests, issuing, revoking and renewing digital Certificates. In addition, SSL.com maintains and publishes the Certificate Revocation Lists (CRLs) for participants within the SSL.com Public Key Infrastructure (PKI).

## 1.1 Overview - The SSL.com CP/CPS

This document incorporates the SSL.com Certificate Policy (CP) and SSL.com Certification Practice Statement (CPS) into a single document, henceforth referred to as the SSL.com CP/CPS. It sets forth the business, legal, and technical requirements, principles and practices surrounding digital certification services provided by SSL.com.

This CP/CPS conforms to the current version of guidelines adopted by the Certification Authority/Browser Forum (“CAB Forum”) and published at (<https://www.cabforum.org>). In particular:

- Publicly trusted TLS Certificates are issued and managed per the Baseline Requirements for the Issuance and Management of Publicly-Trusted TLS Server Certificates (“Baseline Requirements”). The Guidelines for Extended Validation Certificates (“EV Guidelines”) are observed in the issuance of Extended Validation ("EV") TLS Certificates.
- Code Signing and Extended Validation Code Signing ("EV Code Signing") Certificates are issued and managed per the Baseline Requirements for the Issuance and Management of Publicly-Trusted Code Signing Certificates ("Code Signing Baseline Requirements").
- Email Protection ("S/MIME") Certificates are issued and managed per the Baseline Requirements for the Issuance and Management of Publicly-Trusted S/MIME Certificates ("S/MIME Baseline Requirements").
- Mark Certificates ("MC") are issued and managed per the Minimum Security Requirements for Issuance of Mark Certificates ("MC Requirements") maintained by the AuthIndicators Working Group and published at <https://bimigroup.org/supporting-documents/>.
- Issuance of SSL.com certificates to NAESB Subscribers observes the North American Energy Standards Board (NAESB) Accreditation Requirements for Authorized Certificate Authorities.
- SSL.com time-stamping services follow IETF RFC 3161.

The SSL.com CP/CPS uses the Internet X.509 Public Key Infrastructure Certificate Policy and Certification Practices Framework (RFC 3647). In accordance with RFC 3647, this CP/CPS is organized using numbered paragraphs. Items that do not currently apply to SSL.com PKI will have the statement "Not applicable" or "No stipulation".

SSL.com's Policy Management Authority (PMA) will continuously keep track of changes in SSL.com policies and applicable guidelines, incorporate required changes before their effective dates, and update this CP/CPS accordingly. In the event of any inconsistency between this CP/CPS and the guidelines given above, the relevant CAB Forum publication shall take precedence over this document.

This CP/CPS applies to all entities and individuals utilizing SSL.com certification services.

Other important documents also apply to SSL.com certification services. These include public documents (such as agreements with Subscribers and other SSL.com customers, Relying Party agreements, and the SSL.com privacy policy) and private documents governing internal operations.

## 1.2 Identification Number and Document Name

### 1.2.1 Document Identification Number

The OID assigned to SSL.com by IANA is:

> iso (1) org (3) dod (6) internet (1) private (4) enterprise (1) SSL.com (38064)

A special OID arc has been allocated by SSL.com for Certificate Policy / Certification Practice Statement:

> iso (1) org (3) dod (6) internet (1) private (4) enterprise (1) SSL.com (38064) certificationServicesProvision (1) certificatePolicyCertificationPracticeStatement (1)

The globally unique Identification Number (OID) of the SSL.com CP/CPS (this document) is:

**1.3.6.1.4.1.38064.1.1.1.29**

| OID Arc | Description |
| -- | -------- |
| 1.3.6.1.4.1.**38064** | Identification Number (OID) of SSL.com, registered to IANA (www.iana.org) |
| 1.3.6.1.4.1.38064.**1** | Certification Services Provision |
| 1.3.6.1.4.1.38064.1.**1** | Certificate Policy / Certification Practice Statement |
| 1.3.6.1.4.1.38064.1.1.**1.29** | First and Second number of the version identifying this document

**Version Control**

| **Version** | **Date** | **Information** |
| - | -- | ------- |
| 1.0 | **June XX 2026** | First release |


### 1.2.2 Document Name

This document is the SSL.com CP/CPS and constitutes the documentation and regulatory frame for SSL.com's PKI. This document incorporates both the Certificate Policy and the Certification Practice Statement for SSL.com's operations. In abbreviation, it will be referred as the “SSL.com CP/CPS” or "CP/CPS".

### 1.2.3 Certification Practice Statements and specific scenarios

Should the need arise to follow any additional practice beyond what is outlined in this CP/CPS, a corresponding alternate certification practice statement (alternate CPS) will be created and referenced in this document. The resulting document(s) will be a separate CPS that applies to specific cases. The new alternate CPS will describe particular cases where it applies, the different procedures that will apply in those particular cases, and the specific sections of the SSL.com CP/CPS which the alternate CPS modifies or supersedes.

For NAESB Subscribers, SSL.com shall follow all procedures (including those related to verification, issuance, re-issuance and revocation, log archiving and any other NAESB-specific requirements) as described in the relevant WEQ and related NAESB guidelines (see §1.6.3). Any certificate issued to NAESB Subscribers SHALL incorporate the appropriate OID for the level of assurance of that certificate (see §7.1.6).

### 1.2.4 Provision and amendment of SSL.com CP/CPS

The provisions of the SSL.com CP/CPS, as amended from time to time, are publicly available via the SSL.com repository. Amendments to this document will be made in accordance with Sections 1.5 and 9.12.

## 1.3 PKI participants and their roles

The roles which comprise SSL.com’s PKI include Certification Authorities (CAs), Registration Authorities (RAs), Subscribers and Relying Parties.

- A Certification Authority (CA) is the entity responsible for issuing Certificates.
- A CA utilizes at least one Registration Authority (RA) for identifying, authenticating and managing a Subscriber's certificate request information.
- A Subscriber is any party which has been issued a certificate by SSL.com.
- A Relying Party is any party who performs transactions, communications and/or functions that rely on a certificate issued by SSL.com.

Also refer to §1.6.1 for definition of these terms.

### 1.3.1 Certification Authority

Within the SSL.com PKI hierarchy, SSL.com functions as both the Root CA and as an Issuing CA.

#### 1.3.1.1 Root CA role

In its role as a Root CA, SSL.com makes available to Subscribers a dedicated root hierarchy to ensure the integrity and uniqueness of Certificates issued through the SSL.com PKI. Starting in 2022, SSL.com created separate hierarchies per certificate type as follows:

- TLS Root hierarchy to be used for server TLS Certificates
- Client Root hierarchy to be used for client authentication and email (S/MIME) Certificates
- Code Signing Root hierarchy to be used for Code Signing and Time-stamping Certificates associated with Code Signing
- Document Signing Root hierarchy to be used for Document Signing and Time-stamping Certificates associated with Document Signing.

#### 1.3.1.2 Issuing CA role

In its role as an issuing CA, SSL.com performs functions associated with Public Key operations that include:

- Receiving requests for Certificates
- Issuing, revoking and renewing Certificates
- Maintenance, issuance, and publication of a definitive Certificate Revocation List (CRL) and Online Certificate Status Protocol (OCSP) as resources for users of Certificates related to the SSL.com PKI.

SSL.com intends to use the following issuing CA structure under the "2022" TLS Root hierarchy:

- "global" subCA for DV TLS
- "global" subCA for OV TLS
- "global" subCA for IV TLS
- "global" subCA for EV TLS
- "branded" subCA per customer for DV/OV/IV/EV.

#### 1.3.1.3 General CA roles

In its capacity as a CA, SSL.com:

- Conforms its operations to the SSL.com CP/CPS
- Issues and publishes Certificates in a timely manner
- Revokes Certificates upon receipt of a valid and authorized request, or on its own initiative when circumstances warrant
- Notifies Certificate holders of the imminent expiry of their Certificates.

### 1.3.2 Registration Authority

Any CA utilizes at least one RA for identifying, authenticating and managing a Subscriber's certificate request information. Depending on the type of CA, registration requirements of this CA and the assurance level, a Subscriber may need to perform specific registration operations (for example face-to-face proof of identity, inquiries to official local government list of commercial organizations, etc). These operations are performed by RAs operated under the supervision of SSL.com, utilizing trusted personnel and/or trustworthy systems providing equivalent assurance. SSL.com operates the central RA of the SSL.com hierarchy.

With the exception of sections §3.2.2.4 and §3.2.2.5, SSL.com MAY delegate the performance of all or any part of these requirements to a Delegated Third Party, provided that the process as a whole fulfills all of the requirements of §3.2 of this CP/CPS.

Before SSL.com authorizes a Delegated Third Party to perform a delegated function, SSL.com SHALL contractually require the Delegated Third Party to:

1. Meet the qualification requirements of §5.3.1, when applicable, to the delegated function;
2. Retain documentation in accordance with §5.5.2;
3. Comply with (a) the SSL.com CP/CPS or (b) the Delegated Third Party’s (SSL.com-approved) CP/CPS; and
4. Abide by the other provisions (i.e. CAB Forum Requirements designated in §1.1, Contract between SSL.com and Delegated Third Parties) that are applicable to the delegated function.

SSL.com MAY delegate the performance of all or any part of EV Validation to an Affiliate or a Registration Authority (RA) or subcontractor, provided that the process employed fulfills all of the requirements of the EV Guidelines.
Affiliates and/or RAs must comply with the qualification requirements of Sections §5.2 and §5.3.

SSL.com SHALL verify that any Delegated Third Party's personnel involved in the issuance of a Certificate meet the training and skills requirements of §5.3 and the document retention and event logging requirements of §5.4.

### 1.3.2.1 Enterprise RAs

**For TLS Server Certificates:**
SSL.com MAY designate an Enterprise RA to verify certificate requests from the Enterprise RA’s own organization. SSL.com SHALL NOT accept certificate requests authorized by an Enterprise RA unless the following requirements are satisfied:

1. SSL.com SHALL confirm that the requested Fully-Qualified Domain Name(s) are within the Enterprise RA’s verified Domain Namespace.
2. If the certificate request includes a Subject name of a type other than a Fully-Qualified Domain Name, SSL.com SHALL confirm that the name is either that of the delegated enterprise, or an Affiliate of the delegated enterprise, or that the delegated enterprise is an agent of the named Subject. For example, SSL.com SHALL NOT issue a Certificate containing the Subject name "XYZ Co." on the authority of Enterprise RA "ABC Co.", unless the two companies are affiliated (see §3.2) or "ABC Co." is the agent of "XYZ Co". This requirement applies regardless of whether the accompanying requested Subject FQDN falls within the Domain Namespace of ABC Co.’s Registered Domain Name.

SSL.com SHALL impose these limitations as a contractual requirement on the Enterprise RA and monitor compliance by the Enterprise RA.

**For EV TLS and Code Signing Certificates:**
SSL.com MAY contractually authorize the Subject of a specified Valid EV Certificate to perform the RA function and authorize SSL.com to issue additional EV Certificates at third and higher domain levels that are contained within the domain of the original EV Certificate (also known as an Enterprise EV Certificate). In such case, the Subject shall be considered an Enterprise RA, and the following requirements SHALL apply:

1. An Enterprise RA SHALL NOT authorize SSL.com to issue an Enterprise EV Certificate at the third or higher domain levels to any Subject other than the Enterprise RA or a business that is owned or directly controlled by the Enterprise RA;
2. In all cases, the Subject of an Enterprise EV Certificate must be an organization verified by SSL.com in accordance with the EV Guidelines;
3. SSL.com must impose these limitations as a contractual requirement with the Enterprise RA and monitor compliance by the Enterprise RA;
4. The Final Cross-Correlation and Due Diligence requirements of the EV Guidelines may be performed by a single person representing the Enterprise RA; and
5. The audit requirements of §8.4 SHALL apply to the Enterprise RA, except in the case where SSL.com maintains control over the Root CA Private Key or Subordinate CA Private Key used to issue the Enterprise EV Certificates, in which case, the Enterprise RA may be exempted from the audit requirements.
6. SSL.com does NOT contractually authorize the Subject of a specified Valid EV Code Signing Certificate to perform the RA function and authorize SSL.com to issue additional EV Code Signing Certificates.

### 1.3.2.2 Guidelines Compliance Obligation

In all cases, SSL.com contractually obligates each Affiliate, RA, subcontractor, and Enterprise RA to comply with all applicable requirements in this CP/CPS and to perform them as required of SSL.com itself. SSL.com shall enforce these obligations and internally audit each Affiliate's, RA's, subcontractor's, and Enterprise RA's compliance with this CP/CPS on an annual basis.

### 1.3.3 Subscribers

A Subscriber is any natural person or Legal Entity to whom a Certificate is issued and who is legally bound by a Subscriber Agreement or Terms of Use.

#### 1.3.3.1 Applicants

An Applicant is any natural person or Legal Entity that applies for (or seeks renewal of) a Certificate. Prior to verification of identity and issuance of a certificate, any requesting Subscriber is defined as an Applicant. Once the Certificate is issued, the Applicant is referred to as the Subscriber. For Certificates issued to devices, the Applicant is the entity that controls or operates the device named in the Certificate, even if the device is sending the actual certificate request.
Prior to verification of identity and issuance of a certificate, any requesting Subscriber is defined as an Applicant.

#### 1.3.3.2 Role of Applicants and/or Subscribers

Before accepting and using a certificate, an Applicant must:

1. Generate a unique Key Pair.
2. Submit an application for the type of certificate requested which must be approved by SSL.com's RA
3. Agree to and accept the terms and conditions of the applicable SSL.com Subscriber Agreement

For Key Pair generation on behalf of the Subscriber, the provisions of §6.2.1 apply.

#### 1.3.3.3 Applicant and/or Subscriber responsibilities

Each Applicant and/or Subscriber is solely responsible for the generation of the Key Pair associated with an SSL.com certificate. For Key Pair generation on behalf of the Subscriber, the provisions of §6.2.1 apply.

Each Applicant and/or Subscriber is solely responsible for the protection of the Private Key related to their SSL.com certificate.

A Subscriber shall immediately notify SSL.com if any information contained in an issued SSL.com certificate changes or becomes false or misleading, or in the event that its Private Key has been compromised or the Subscriber has reason to believe that it has been compromised. A Subscriber must immediately stop using and uninstall any SSL.com certificate upon that certificate’s revocation or expiration.

Applicants and Subscribers are required to operate under the SSL.com CP/CPS and agree to the SSL.com Subscriber Agreement.

### 1.3.4. Relying Parties

A Relying Party is any entity performing transactions, communications and/or functions which rely on a certificate issued by SSL.com.

Before relying on or using an SSL.com certificate, Relying Parties should:

- Read the SSL.com CP/CPS in its entirety
- Review the SSL.com repository to determine whether the certificate has expired or been revoked (per the CRL and/or OCSP) and/or to collect more information concerning the certificate

Relying Parties should make their own judgment as to what degree, if any, they rely on any certificate and must make a trust decision based on the content of the corresponding certificate in order to proceed to specific actions or justified belief.
In order to verify the validity of the certificate, Relying Parties must check that:

- The validity period of the certificate has begun and has not expired
- The certificate is correctly signed by an SSL.com Trusted Certification Authority
- The certificate has not been revoked/suspended
- Subject identification matches the details that the signer presents
- The usage for which the certificate was originally intended corresponds with those presented and abides by the terms and the conditions that are described in SSL.com's CP/CPS.

### 1.3.5 Other participants in the SSL.com PKI

SSL.com shall contractually guarantee that all applicable requirements specified in the CP/CPS, including satisfaction of EV Guidelines, are met in all contracts with Subordinate CAs, external RAs, Enterprise RAs, and/or subcontractors that involve or relate to the issuance or maintenance of Certificates.

For Technically Constrained Subordinate CAs allowed to issue TLS Certificates in line with §7.1.5, SSL.com shall enforce these obligations and internally audit each such entity for compliance with this CP/CPS on an annual basis per §8.7.

For Subordinate CAs that are not Technically Constrained, SSL.com shall require an annual audit performed by a Qualified Auditor per §8.4.

Signing Services MUST support generation of Subscriber Key Pair and maintain security of the Subscriber Private Key.

Timestamp Authorities may be used by the Subscriber to provide timestamp records to indicate data existed at a specific time.

## 1.4 Certificate usage

### 1.4.1 Allowed certificate usage

A certificate issued by SSL.com under the guidelines of the SSL.com CP/CPS shall be used only as designated by the key usage or extended key usage fields defined in the certificate profile for that product (including authentication, encryption, access control, and digital signature purposes).

### 1.4.2 Prohibited certificate usage

A certificate issued by SSL.com under the guidelines of this SSL.com CP/CPS may not be used for any purpose other than those defined in the certificate profile of the respective product.

Note to Relying Parties: Digitally signed code by a Code Signing Certificate does not guarantee that the code is safe from Suspect Code.

Third parties are not allowed to use TLS Server Certificates issued by SSL.com to conduct surreptitious interception, except with the domain registrant's permission.

## 1.5 Policy Administration

### 1.5.1 Organization administering the SSL.com CP/CPS

The SSL.com CP/CPS, related procedural or security policy documents, and any other related agreements referenced, are administered by the SSL.com Policy Management Authority (PMA), appointed by SSL.com management.

### 1.5.2 Contact information for the SSL.com PMA

The SSL.com PMA can be contacted via the following methods:

- **Mail:**
    - SSL.com
    - 3200 Southwest Fwy Ste 1150
    - Houston, Texas 77027
- **Email:** [compliance@ssl.com](mailto:compliance@ssl.com)
- **Phone:** [+1 877-775-7328](tel:+18777757328)
- **Fax:** +1 832-201-7706

Instructions on how to submit a Certificate Problem Report is provided in §4.9.3.3.

### 1.5.3 Person determining CP/CPS suitability for the policy

Compliance and suitability with the SSL.com CP/CPS is monitored and managed by the SSL.com PMA, with reference to results and recommendations made by Qualified Auditors and Self-Audits (§8).

### 1.5.4 CPS approval procedures

The SSL.com CP/CPS is approved and amended by the SSL.com PMA per the provisions of §9.12.

## 1.6 Definitions and acronyms

### 1.6.1 Definitions

**Account Dashboard:** User interface for management of SSL.com Certificates. Any Applicant will be directed to log in to or create an SSL.com account before any request shall be processed.

**Address and Routing Parameter Area Name**: A Domain Name whose Top-Level Domain is "arpa". Examples: `a.b.c.d.in-addr.arpa` or `....x.x.x.x.ip6.arpa.`.

**Affiliate:** A corporation, partnership, joint venture or other entity controlling, controlled by, or under common control with another entity, or an agency, department, political subdivision, or any entity operating under the direct control of a Government Entity.

**Applicant:** The natural person or Legal Entity that applies for (or seeks renewal of) a Certificate. Once the Certificate is issued, the Applicant is referred to as the Subscriber. For Certificates issued to devices, the Applicant is the entity that controls or operates the device named in the Certificate, even if the device is sending the actual certificate request.

**Applicant Representative:** A natural person or human sponsor who is either the Applicant, employed by the Applicant, or an authorized agent who has express authority to represent the Applicant: (i) who signs and submits, or approves a certificate request on behalf of the Applicant, and/or (ii) who signs and submits a Subscriber Agreement on behalf of the Applicant, and/or (iii) who acknowledges the Terms of Use on behalf of the Applicant when the Applicant is an Affiliate of SSL.com or is SSL.com.

**Application Software Supplier:** A supplier of Internet browser software or other Relying Party application software that displays or uses Certificates and incorporates Root Certificates.

**Attestation Letter:** A letter attesting that Subject Information is correct written by an accountant, lawyer, government official, or other reliable third party customarily relied upon for such information.

**Audit Period:** In a period-of-time audit, the period between the first day (start) and the last day of operations (end) covered by the auditors in their engagement. (This is not the same as the period of time when the auditors are on-site at the CA.) The coverage rules and maximum length of audit periods are defined in §8.1.

**Audit Report:** A report from a Qualified Auditor stating the Qualified Auditor's opinion on whether an entity's processes and controls comply with the mandatory provisions of industry standards Requirements.

**Authorization Domain Name:** The FQDN used to obtain authorization for a given FQDN to be included in a Certificate. SSL.com may use the FQDN returned from a DNS CNAME lookup as the FQDN for the purposes of domain validation. If a Wildcard Domain Name is to be included in a Certificate, then SSL.com MUST remove `*.` from the left-most portion of the Wildcard Domain Name to yield the corresponding FQDN. SSL.com may prune zero or more Domain Labels of the FQDN from left to right until encountering a Base Domain Name and may use any one of the values that were yielded by pruning (including the Base Domain Name itself) for the purpose of domain validation.

**Authorized Port:** One of the following ports: 80 (http), 443 (https), 25 (smtp), 22 (ssh).

**Base Domain Name:** The portion of an applied-for FQDN that is the first Domain Name node left of a registry-controlled or public suffix plus the registry-controlled or public suffix (e.g. "example.co.uk" or "example.com"). For FQDNs where the right-most Domain Name node is a gTLD having ICANN Specification 13 in its registry agreement, the gTLD itself may be used as the Base Domain Name.

**Business Entity:** Any entity that is not a Private Organization, Government Entity, or Non-Commercial Entity as defined herein. Examples include, but are not limited to, general partnerships, unincorporated associations, sole proprietorships, etc.

**CAA:** For TLS Server Certificates, from RFC 8659: "The Certification Authority Authorization (CAA) DNS Resource Record allows a DNS domain name holder to specify one or more Certification Authorities (CAs) authorized to issue certificates for that domain name. CAA Resource Records allow a public CA to implement additional controls to reduce the risk of unintended certificate mis-issue". For S/MIME Certificates, from RFC 9495: "The Certification Authority Authorization (CAA) DNS resource record (RR) provides a mechanism for domains to express the allowed set of Certification Authorities that are authorized to issue certificates for the domain."

**CA Key Pair:** A Key Pair where the Public Key appears as the Subject Public Key Info in one or more Root CA Certificate(s) and/or Subordinate CA Certificate(s).

**CAB Forum:**  The Certification Authority/Browser Forum, a voluntary group of certification authorities (CAs), vendors of Internet browser software, and suppliers of other applications that use X.509 v.3 digital certificates for TLS and Code Signing. The CAB Forum determines guidelines and requirements to establish public trust in browsers and other software using digital certificates.

**CCADB:** A repository of information about externally operated Certificate Authorities (CAs) whose root and intermediate certificates are included within the products and services of Application Software Suppliers who are CCADB root store members. The repository is available at <https://ccadb.org>.

**Certificate:** An electronic document that uses a digital signature to bind a public key and an identity.

**Certificate Approver:** A natural person who is either the Applicant, employed by the Applicant, or an authorized agent who has express authority to represent the Applicant to (i) act as a Certificate Requester and to authorize other employees or third parties to act as a Certificate Requester, and (ii) to approve EV or Mark Certificate Requests submitted by other Certificate Requesters.

**Certificate Data:** Certificate requests and data related thereto (whether obtained from the Applicant or otherwise) in the CA's possession or control or to which the CA has access.

**Certificate Management Process:** Processes, practices, and procedures associated with the use of keys, software, and hardware, by which SSL.com verifies Certificate Data, issues Certificates, maintains a Repository, and revokes Certificates.

**Certificate Management System**: A system used by SSL.com or Delegated Third Party to process, approve issuance of, or store certificates or certificate status information, including the database, database server, and storage.

**Certificate Policy:** A set of rules that indicates the applicability of a named Certificate to a particular community and/or PKI implementation with common security requirements.

**Certificate Problem Report:** Complaint of suspected Key Compromise, Certificate misuse, or other types of fraud, compromise, misuse, or inappropriate conduct related to Certificates.

**Certificate Profile:** A set of documents or files that defines requirements for Certificate content and Certificate extensions in accordance with §7, e.g. a Section in a CA’s CPS or a certificate template file used by CA software.

**Certificate Requester:** A natural person who is either the Applicant, employed by the Applicant, an authorized agent who has express authority to represent the Applicant, or a third party (such as an ISP or hosting company) that completes and submits an EV or Mark Certificate Request on behalf of the Applicant.

**Certificate Revocation List:** A regularly updated time-stamped list of revoked Certificates that is created and digitally signed by the CA that issued the Certificates.

**Certificate Systems:** The systems used by SSL.com or Delegated Third Party in providing identity verification, registration and enrollment, certificate approval, issuance, validity status, support, and other PKI‐related services.

**Certification Authority:** An organization that is responsible for the creation, issuance, revocation, and management of Certificates. The term applies equally to both Root CAs and Subordinate CAs.

**Certification Practice Statement:** One of several documents forming the governance framework in which Certificates are created, issued, managed, and used.

**Code Signature:** A Signature logically associated with a signed Object

**Combined Mark:** A mark consisting of a graphic design, stylized logo, or image, with words and/or letters having a particular stylized appearance. For greater certainty, a “Combined Mark” includes marks made up of both word and design elements.

**Common Mark Certificate:** A Mark Certificate that contains a Mark Representation that has not been verified as a Registered Mark or Government Mark.

**Confirmation Request:** An appropriate out-of-band communication requesting verification or confirmation of the particular fact at issue.

**Contract Signer:** A natural person who is either the Applicant, employed by the Applicant, or an authorized agent who has express authority to represent the Applicant, and who has authority on behalf of the Applicant to sign Subscriber Agreements.

**Control:** "Control" (and its correlative meanings, "controlled by" and "under common control with") means possession, directly or indirectly, of the power to: (1) direct the management, personnel, finances, or plans of such entity; (2) control the election of a majority of the directors ; or (3) vote that portion of voting shares required for "control" under the law of the entity's Jurisdiction of Incorporation or Registration but in no case less than 10%.

**Country:** Either a member of the United Nations OR a geographic region recognized as a Sovereign State by at least two UN member nations.

**Cross-Certified Subordinate CA Certificate**: A certificate that is used to establish a trust relationship between two CAs.

**CSPRNG:** A random number generator intended for use in a cryptographic system.

**Dashboard:** See Account Dashboard.

**Delegated Third Party:** A natural person or Legal Entity that is not SSL.com, and whose activities are not within the scope of SSL.com's external audits, but is authorized by SSL.com to assist in the Certificate Management Process by performing or fulfilling one or more of the CA requirements found herein.

**Delegated Third Party System**: Any part of a Certificate System used by a Delegated Third Party while performing the functions delegated to it by SSL.com.

**Design Mark:** A mark consisting of a graphic design, stylized logo, or image, without words and/or letters. For greater certainty, a “Design Mark” includes marks made up solely of design elements.

**Designated Individual:** The person who completes the F2F Verification Procedure under the provisions of the MC Requirements.

**DNS CAA Email Contact:** The email address defined as a property in a DNS CAA record. Example: `CAA 0 contactemail "domainowner@example.com"`. The CAA contactemail property takes an email address as its parameter. The entire parameter value MUST be a valid email address as defined in RFC 6532 section 3.2, with no additional padding or structure, or it cannot be used. The contactemail property MAY be critical, if the domain owner does not want CAs who do not understand it to issue certificates for the domain.

**DNS CAA Phone Contact:** The phone number defined as a property in a DNS CAA record. Example: `CAA 0 contactphone "+1 (555) 123-4567"`. The CAA contactphone property takes a phone number as its parameter.  The entire parameter value MUST be a valid Global Number as defined in RFC 3966 section 5.1.4, or it cannot be used.  Global Numbers MUST have a preceding + and a country code and MAY contain visual separators. The contactphone property MAY be critical if the domain owner does not want CAs who do not understand it to issue certificates for the domain.

**DNS TXT Record Email Contact:** The email address placed in a DNS TXT record. The DNS TXT record MUST be placed on the `_validation-contactemail` subdomain of the domain being validated. The entire RDATA value of this TXT record MUST be a valid email address as defined in RFC 6532 section 3.2, with no additional padding or structure, or it cannot be used.

**DNS TXT Record Phone Contact:** An email address placed in a DNS TXT record. This DNS TXT record MUST be placed on the `_validation-contactphone` subdomain of the domain being validated. The entire RDATA value of this TXT record MUST be a valid Global Number as defined in RFC 3966 section 5.1.4, or it cannot be used.

**Domain Contact:** The Domain Name Registrant, technical contact, or administrative contact (or the equivalent under a ccTLD) as listed in the WHOIS record of the Base Domain Name or in a DNS SOA record, or as obtained through direct contact with the Domain Name Registrar.

**Domain Label**: From RFC 8499: "An ordered list of zero or more octets that makes up a portion of a domain name. Using graph theory, a label identifies one node in a portion of the graph of all possible domain names."

**Domain Name**: An ordered list of one or more Domain Labels assigned to a node in the Domain Name System.

**Domain Name Registrant:** Sometimes referred to as the "owner" of a Domain Name, but more properly the person(s) or entity(ies) registered with a Domain Name Registrar as having the right to control how a Domain Name is used, such as the natural person or Legal Entity that is listed as the "Registrant" by WHOIS or the Domain Name Registrar.

**Domain Name Registrar:** A person or entity that registers Domain Names under the auspices of or by agreement with: (i) the Internet Corporation for Assigned Names and Numbers (ICANN), (ii) a national Domain Name authority/registry, or (iii) a Network Information Center (including their affiliates, contractors, delegates, successors, or assigns).

**Domain Namespace:** The set of all possible Domain Names that are subordinate to a single node in the Domain Name System.

**Enterprise EV Certificate:** An EV Certificate that an Enterprise RA authorizes SSL.com to issue at third and higher domain levels.

**Enterprise EV RA:** An employee or agent of an organization unaffiliated with SSL.com who authorizes issuance of EV Certificates at third and higher domain levels to that organization.

**Enterprise RA:** An employee or agent of an organization unaffiliated with SSL.com who authorizes issuance of Certificates to that organization.

**EV Certificate:** A certificate that contains subject information specified in, and which has been validated in accordance with the EV Guidelines.

**EV Certificate Renewal:** The process whereby an Applicant who has a valid, unexpired and non-revoked EV Certificate issued by SSL.com, makes an application to SSL.com for a newly issued EV Certificate that includes the same organizational name and Domain Name as the existing EV Certificate, a new 'valid to' date beyond the expiry of the current EV Certificate and the application is prior to the expiration of the Applicant's existing EV Certificate.
  
**EV Certificate Request:** A request from an Applicant to SSL.com requesting that SSL.com issue an EV Certificate to the Applicant whose valid request is authorized by the Applicant and signed by the Applicant Representative.

**EV Code Signing Certificate:** A certificate that contains subject information validated according to the EV Guidelines.

**EV OID:** An identifying number, in the form of an “object identifier,” that is included in the certificatePolicies field of a certificate that: (i) indicates which CA policy statement relates to that certificate, and (ii) by pre-agreement with one or more Application Software Supplier, marks the certificate as being an EV Certificate.

**EV Processes:** The keys, software, processes, and procedures by which SSL.com verifies Certificate Data, issues EV Certificates, maintains a Repository and revokes EV Certificates.

**Expiry Date:** The "notAfter" date in a Certificate that defines the end of a Certificate's validity period.

**Extant S/MIME CA**: A Subordinate CA that:

   1. Is a Publicly-Trusted Subordinate CA Certificate whose `notBefore` field is before September 1, 2023 and which is included in a valid trust chain of an end entity S/MIME Certificate;
   2. The CA Certificate includes no Extended Key Usage extension, contains `anyExtendedKeyUsage` in the EKU extension, or contains `id-kp-emailProtection` in the EKU extension;
   3. The CA Certificate complies with the profile defined in RFC 5280. The following two deviations from the RFC 5280 profile are acceptable:
    a. The CA Certificate contains a `nameConstraints` extension that is not marked critical;
    b. The CA Certificate contains a policy qualifier of type UserNotice which contains `explicitText` that uses an encoding that is not permitted by RFC 5280 (i.e., the `DisplayText` is encoded using BMPString or VisibleString); and
   4. The CA Certificate contains the `anyPolicy` identifier (2.5.29.32.0) or specific OIDs in the `certificatePolicies` extension that do not include those defined in Section 7.1.6.1 of the S/MIME Baseline Requirements.

**Extended Validation Certificate:** See EV Certificate.

**Fully-Qualified Domain Name:** A Domain Name that includes Domain Labels of all superior nodes in the Internet Domain Name System.

**F2F Verification Procedure:** Either the Notarization process or the web based F2F session as specified in the MC Requirements.

**Government Agency:** In the context of a Private Organization, the government agency in the Jurisdiction of Incorporation under whose authority the legal existence of Private Organizations is established (e.g., the government agency that issued the Certificate of Incorporation). In the context of Business Entities, the government agency in the jurisdiction of operation that registers business entities. In the case of a Government Entity, the entity that enacts law, regulations, or decrees establishing the legal existence of Government Entities.

**Government Entity:** A government-operated legal entity, agency, department, ministry, branch, or similar element of the government of a country, or political subdivision within such country (such as a state, province, city, county, etc.).

**Hardware Crypto Module:** A tamper-resistant device, with a cryptography processor,
used for the specific purpose of protecting the lifecycle of cryptographic keys (generating, managing, processing, and storing).

**High Risk Certificate Request:** A Request which SSL.com flags for additional scrutiny by reference to internal criteria and databases maintained by the CA, which may include names at higher risk for phishing or other fraudulent usage, names contained in previously rejected certificate requests or revoked Certificates, names listed on the Miller Smiles phishing list or the Google Safe Browsing list, or names which SSL.com identifies using its own risk-mitigation criteria.

**High Risk Region of Concern (HRRC):** A geographic location where the detected number of Code Signing Certificates associated with signed Suspect Code exceeds 5% of the total number of detected Code Signing Certificates originating or associated with the same geographic area. This information is provided in Appendix D of the "Baseline Requirements for the Issuance and Management of Publicly-Trusted Code Signing Certificates" document.

**Incorporating Agency:** In the context of a Private Organization, the government agency in the Jurisdiction of Incorporation under whose authority the legal existence of the entity is registered (e.g., the government agency that issues certificates of formation or incorporation). In the context of a Government Entity, the entity that enacts law, regulations, or decrees establishing the legal existence of Government Entities.

**Individual:** A natural person.

**Individual‐Validated:** Refers to a Certificate Subject that includes only Individual (Natural Person) attributes, rather than attributes linked to an Organization.

**Internal Name**: A string of characters (not an IP address) in a Common Name or Subject Alternative Name field of a Certificate that cannot be verified as globally unique within the public DNS at the time of certificate issuance because it does not end with a Top-Level Domain registered in IANA's Root Zone Database.

**Intermediate CA Certificate:** A Certificate issued by a Root Certificate or another Intermediate CA Certificate which is deemed as capable of being used to issue new Certificates and which contains an X.509v3 basicConstraints extension, with the cA boolean set to true. If an Intermediate CA Certificate is issued to a non-affiliated organization, then this Intermediate CA Certificate is also referred to as an Intermediate CA Certificate of a Subordinate CA.

**Internal Name:** A string of characters (not an IP address) in a Common Name or Subject Alternative Name field of a Certificate that cannot be verified as globally unique within the public DNS at the time of certificate issuance because it does not end with a Top-Level Domain registered in IANA's Root Zone Database.

**IP Address:** A 32-bit or 128-bit number assigned to a device that uses the Internet Protocol for communication.

**Issuing CA:** In relation to a particular Certificate, the CA that issued the Certificate. This could be either a Root CA or a Subordinate CA.

**IP Reverse Zone Suffix**: One of the two FQDNs that consist of the Domain Labels "in-addr.arpa" or "ip6.arpa". These two FQDNs serve as the root of the IP version 4 and IP version 6 reverse mapping space. "in-addr.arpa" is the root of the IP version 4 reverse mapping space and "ip6.arpa" is the root of the IP version 6 reverse mapping space.

**Jurisdiction of Incorporation:** In the context of a Private Organization, the country and (where applicable) the state or province or locality where the organization’s legal existence was established by a filing with (or an act of) an appropriate government agency or entity (e.g., where it was incorporated). In the context of a Government Entity, the country and (where applicable) the state or province where the Entity’s legal existence was created by law.

**Jurisdiction of Registration:** In the case of a Business Entity, the state, province, or locality where the organization has registered its business presence by means of filings by a Principal Individual involved in the business.

**Key Compromise:** A Private Key is said to be compromised if its value has been disclosed to an unauthorized person or an unauthorized person has had access to it.

**Key Generation Script:** A documented plan of procedures for the generation of a CA Key Pair.

**Key Pair:** The Private Key and its associated Public Key.

**LDH Label**: From RFC 5890: "A string consisting of ASCII letters, digits, and the hyphen with the further restriction that the hyphen cannot appear at the beginning or end of the string. Like all DNS labels, its total length must not exceed 63 octets."

**Latin Notary:** A person with legal training whose commission under applicable law not only includes authority to authenticate the execution of a signature on a document but also responsibility for the correctness and content of the document. A Latin Notary is sometimes referred to as a Civil Law Notary.

**Legacy Profile:** The S/MIME Legacy Generation profiles provide flexibility for existing reasonable S/MIME certificate practices to become auditable under the S/MIME Baseline Requirements. This includes options for Subject DN attributes, extKeyUsage, and other extensions. The Legacy Profiles will be deprecated in a future version of the S/MIME Baseline Requirements.

**Legal Entity:** An association, corporation, partnership, proprietorship, trust, government entity or other entity with legal standing in a country's legal system.

**Legal Existence:** A Private Organization, Government Entity, or Business Entity has Legal Existence if it has been validly formed and not otherwise terminated, dissolved, or abandoned.

**Legal Practitioner:** A person who is either a lawyer or a Latin Notary (see above) and competent to render an opinion on factual claims of the Applicant.

**Lifetime Signing OID:** An optional extended key usage OID (`1.3.6.1.4.1.311.10.3.13`) used by Microsoft Authenticode to limit the lifetime of the Code Signature to the expiration of the Code Signing certificate.

**Linting**: A process in which the content of digitally signed data such as a Precertificate [RFC 6962], Certificate, Certificate Revocation List, or OCSP response, or data-to-be-signed object such as a `tbsCertificate` (as described in RFC 5280, Section 4.1.1.1) is checked for conformance with the profiles and requirements defined in the Baseline Requirements.

**Mailbox-Validated (MV)**: Refers to a Certificate Subject that is limited to (optional) `subject:emailAddress`, `subject:commonName`, and/or `subject:serialNumber` attributes.

**Mailbox Address**: Also Email Address. The format of a Mailbox Address is defined as a "Mailbox" as specified in Section 4.1.2 of RFC 5321 and amended by Section 3.2 of RFC 6532, with no additional padding or structure.

**Mailbox Field**: In Subscriber Certificates contains a Mailbox Address of the Subject via `rfc822Name` or `otherName` value of type `id-on-SmtpUTF8Mailbox` in the `subjectAltName` extension, or in Subordinate CA Certificates via `rfc822Name` in permittedSubtrees within the `nameConstraints` extension.

**Multi-Perspective Issuance Corroboration**: A process by which the determinations made during domain validation and CAA checking by the Primary Network Perspective are corroborated by other Network Perspectives before Certificate issuance.

**Multipurpose Profile**: The S/MIME Multipurpose Generation profiles are aligned with the more defined Strict Profiles, but with additional options for `extKeyUsage` and other extensions. This is intended to allow flexibility for crossover use cases between document signing and secure email.

**Natural Person**: An Individual; a human being as distinguished from a Legal Entity.

**Network Perspective**: Related to Multi-Perspective Issuance Corroboration. A system (e.g., a cloud-hosted server instance) or collection of network components (e.g., a VPN and corresponding infrastructure) for sending outbound Internet traffic associated with a domain control validation method and/or CAA check. The location of a Network Perspective is determined by the point where unencapsulated outbound Internet traffic is typically first handed off to the network infrastructure providing Internet connectivity to that perspective.

**Non-Reserved LDH Label**: From RFC 5890: "The set of valid LDH labels that do not have `--` in the third and fourth positions."

**Notary:** A person whose commission under applicable law includes authority to authenticate the execution of a signature on a document.

**Object Identifier:** A unique alphanumeric or numeric identifier registered under the International Organization for Standardization's applicable standard for a specific object or object class.

**OCSP:** See Online Certificate Status Protocol.

**OCSP Responder:** An online server operated under the authority of SSL.com and connected to its Repository for processing Certificate status requests. See also, Online Certificate Status Protocol.

**OID:** see Object Identifier.

**Onion Domain Name**: A Fully Qualified Domain Name ending with the RFC 7686 ".onion" Special-Use Domain Name. For example, `2gzyxa5ihm7nsggfxnu52rck2vv4rvmdlkiu3zzui5du4xyclen53wid.onion` is an Onion Domain Name, whereas `torproject.org` is not an Onion Domain Name.

**Online Certificate Status Protocol:** An online Certificate-checking protocol that enables Relying Party application software to determine the status of an identified Certificate. See also OCSP Responder.

**Organization‐Validated:** Refers to a Certificate Subject that includes only Organizational (Legal Entity) attributes, rather than attributes linked to an Individual.

**P-Label**: A XN-Label that contains valid output of the Punycode algorithm (as defined in RFC 3492, Section 6.3) from the fifth and subsequent positions.

**Parent Company:** A company that Controls a Subsidiary Company.

**Pending Prohibition​​**: The use of a behavior described with this label is highly discouraged, as it is planned to be deprecated and will likely be designated as MUST NOT in the future.

**Personal Name:** Personal Name is a name of an Individual Subject typically presented as `subject:givenName` and/or `subject:surname`. However, the Personal Name may be in a format preferred by the Subject, the CA, or Enterprise RA as long as it remains a meaningful representation of the Subject’s verified name.

**PKI:** See Public Key Infrastructure.

**Place of Business:** The location of any facility (such as a factory, retail store, warehouse, etc.) where the Applicant’s business is conducted.

**Policy Management Authority:** Administrative body appointed by SSL.com management to create and maintain policies described in the SSL.com CP/CPA and related procedural or security policy documents.

**Primary Network Perspective**: The Network Perspective used by the CA to make the determination of 1) the CA's authority to issue a Certificate for the requested domain(s) or IP address(es) and 2) the Applicant's authority and/or domain authorization or control of the requested domain(s) or IP address(es).

**Principal Individual:** An individual of a Private Organization, Government Entity, or Business Entity that is either an owner, partner, managing member, director, or officer, as identified by their title of employment, or an employee, contractor or agent authorized by such entity or organization to conduct business related to the request, issuance, and use of EV Certificates.

**Private Organization:** A non-governmental legal entity (whether ownership interests are privately held or publicly traded) whose existence was created by a filing with (or an act of) the Incorporating Agency or equivalent in its Jurisdiction of Incorporation.

**Private Key:** The key of a Key Pair that is kept secret by the holder of the Key Pair, and that is used to create Digital Signatures and/or to decrypt electronic records or files that were encrypted with the corresponding Public Key.

**Pseudonym**: A fictitious identity that a person assumes for a particular purpose. Unlike an anonymous identity, a pseudonym can be linked to the person's real identity.

**Public Key:** The key of a Key Pair that may be publicly disclosed by the holder of the corresponding Private Key and that is used by a Relying Party to verify Digital Signatures created with the holder's corresponding Private Key and/or to encrypt messages so that they can be decrypted only with the holder's corresponding Private Key.

**Public Key Infrastructure:** A set of hardware, software, people, procedures, rules, policies, and obligations used to facilitate the trustworthy creation, issuance, management, and use of Certificates and keys based on Public Key Cryptography.

**Public Suffix:** Determination of what is "registry-controlled" versus the registerable portion of a Country Code Top-Level Domain Namespace is not standardized at the time of writing and is not a property of the DNS itself. Current best practice is to consult a "public suffix list" such as <https://publicsuffix.org/> (PSL), and to retrieve a fresh copy regularly. If using the PSL, a CA SHOULD consult the "ICANN DOMAINS" section only, not the "PRIVATE DOMAINS" section. The PSL is updated regularly to contain new gTLDs delegated by ICANN, which are listed in the "ICANN DOMAINS" section. SSL.com is not prohibited from issuing a Wildcard Certificate to the Registrant of an entire gTLD, provided that control of the entire namespace is demonstrated in an appropriate way.

**Publicly-Trusted Certificate:** A Certificate that is trusted by virtue of the fact that its corresponding Root Certificate is distributed as a trust anchor in widely-available application software.

**Qualified Auditor:** A natural person or Legal Entity that meets the requirements of §8.2 (Auditor Qualifications).

**RA:** See Registration Authority

**Random Value:** A value specified by SSL.com to the Applicant that exhibits at least 112 bits of entropy.

**Registered Domain Name:** A Domain Name that has been registered with a Domain Name Registrar.

**Registration Agency:** A Governmental Agency that registers business information in connection with an entity’s business formation or authorization to conduct business under a license, charter or other certification. A Registration Agency may include, but is not limited to (i) a State Department of Corporations or a Secretary of State; (ii) a licensing agency, such as a State Department of Insurance; or (iii) a chartering agency, such as a state office or department of financial regulation, banking or finance, or a federal agency such as the Office of the Comptroller of the Currency or Office of Thrift Supervision.

**Registration Authority:** Any Legal Entity that is responsible for identification and authentication of subjects of Certificates, but is not a CA, and hence does not sign or issue Certificates. An RA may assist in the certificate application process or revocation process or both. When "RA" is used as an adjective to describe a role or function, it does not necessarily imply a separate body, but can be part of the CA.

**Registration Reference**: An identifier assigned to a Legal Entity.

**Registration Scheme**: A scheme for assigning a Registration Reference meeting the requirements identified in Appendix A of S/MIME Baseline Requirements.

**Re-keying:** Creation of an entirely new certificate, using some or all of the information submitted for an existing certificate and using a newly generated Private Key.

**Reliable Data Source:** An identification document or source of data used to verify Subject Identity Information that is generally recognized among commercial enterprises and governments as reliable, and which was created by a third party for a purpose other than the Applicant obtaining a Certificate.

**Relying Party:** Any natural person or Legal Entity that relies on a Valid Certificate. An Application Software Supplier is not considered a Relying Party when software distributed by such Supplier merely displays information relating to a Certificate.

**Repository:** An online database containing publicly-disclosed PKI governance documents (such as Certificate Policies and Certification Practice Statements) and Certificate status information, either in the form of a CRL or an OCSP response. SSL.com maintains its repository at <https://www.ssl.com/repository>.

**Request Token:** A value derived in a method specified by SSL.com which binds this demonstration of control to the certificate request.

The Request Token SHALL incorporate the key used in the certificate request.

A Request Token MAY include a timestamp to indicate when it was created.

A Request Token MAY include other information to ensure its uniqueness.

A Request Token that includes a timestamp SHALL remain valid for no more than 30 days from the time of creation.

A Request Token that includes a timestamp SHALL be treated as invalid if its timestamp is in the future.

A Request Token that does not include a timestamp is valid for a single use and SSL.com SHALL NOT re-use it for a subsequent validation.

The binding SHALL use a digital signature algorithm or a cryptographic hash algorithm at least as strong as that to be used in signing the certificate request.

**Required Website Content:** Either a Random Value or a Request Token, together with additional information that uniquely identifies the Subscriber, as specified by SSL.com.

**Reserved IP Address:** An IPv4 or IPv6 address that is contained in the address block of any entry in either of the following IANA registries:

- <https://www.iana.org/assignments/iana-ipv4-special-registry/iana-ipv4-special-registry.xhtml>
- <https://www.iana.org/assignments/iana-ipv6-special-registry/iana-ipv6-special-registry.xhtml>

**Root CA:** A top level Certification Authority whose Root Certificate is distributed by Application Software Suppliers and that issues Subordinate CA Certificates.

**Root CA System**: A system used to create a Root Certificate or to generate, store, or sign with the Private Key associated with a Root Certificate.

**Root Certificate:** The self-signed Certificate issued by the Root CA to identify itself and to facilitate verification of Certificates issued to its Subordinate CAs.

**Root Program Policy:** Policy set by an Application Software Supplier to establish the minimum requirements for CA certificates to be distributed in their software.

**Signature:** An encrypted electronic data file which is attached to or logically associated with other electronic data and which (i) identifies and is uniquely linked to the signatory of the electronic data, (ii) is created using means that the signatory can maintain under its sole control, and (iii) is linked in a way so as to make any subsequent changes that have been made to the electronic data detectable.

**Signing Service:** An organization that generates the Key Pair and securely manages the Private Key associated with a Code Signing Certificate, on behalf of a Subscriber.

**Short-lived Subscriber Certificate**: For Certificates issued on or after 15 March 2024 and prior to 15 March 2026, a Subscriber Certificate with a Validity Period less than or equal to 10 days (864,000 seconds). For Certificates issued on or after 15 March 2026, a Subscriber Certificate with a Validity Period less than or equal to 7 days (604,800 seconds).

**Sovereign State:** A state or country that administers its own government, and is not dependent upon, or subject to, another power.

**Sponsor‐validated:** Refers to a Certificate Subject which combines Individual (Natural Person) attributes in conjunction with a `subject:organizationName` (an associated Legal Entity) attribute. Registration for Sponsor‐validated Certificates MAY be performed by an Enterprise RA where the `subject:organizationName` is either that of the delegated enterprise, or an Affiliate of the delegated enterprise, or that the delegated enterprise is an agent of the named Subject Organization.

**Subject:** The natural person, device, system, unit, or Legal Entity identified in a Certificate as the Subject. The Subject is either the Subscriber or a device under the control and operation of the Subscriber.

**Subject Identity Information:** Information that identifies the Certificate Subject. Subject Identity Information does not include a Domain Name listed in the `subjectAltName` extension or the Subject `commonName` field.

**Subordinate CA:** A Certification Authority whose Certificate is signed by the Root CA, or another Subordinate CA.

**Subscriber:** A natural person or Legal Entity to whom a Certificate is issued and who is legally bound by a Subscriber Agreement or Terms of Use. For Code Signing and EV Code Signing Certificates, the Subscriber is

1. the Subject of the EV Code Signing Certificate and
2. the entity responsible for distributing the software, but does not necessarily hold the copyright to the software.

**Subscriber Agreement:** An agreement between the CA and the Applicant/Subscriber that specifies the rights and responsibilities of the parties.

**Subsidiary Company:** A company that is controlled by a Parent Company.

**Suspect code:** Code that contains malicious functionality or serious vulnerabilities, including spyware, malware and other code that installs without the user's consent and/or resists its own removal, code that compromises user security and/or code that can be exploited in ways not intended by its designers to compromise the trustworthiness of the platforms on which it executes.

**Takeover Attack:** An attack where a Private Key associated with a Code Signing Certificate has been compromised by means of fraud, theft, intentional malicious act of the Subject's agent, or other illegal conduct.

**Technically Constrained Subordinate CA Certificate**: A Subordinate CA certificate which uses a combination of Extended Key Usage and/or Name Constraint extensions, as defined within the relevant Certificate Profiles, to limit the scope within which the Subordinate CA Certificate may issue Subscriber or additional Subordinate CA Certificates.

**Terms of Use:** Provisions regarding the safekeeping and acceptable uses of a Certificate issued in accordance with these Requirements when the Applicant/Subscriber is an Affiliate of SSL.com or is SSL.com.

**Test Document Signing Certificate:** A Document Signing Certificate which includes an extension with the specified Adobe Test Policy Identifier (`1.2.840.113583.1.2.2`), or (ii) is issued under a CA where there are no certificate paths/chains to a root CA certificate subject to any of the requirements of §1.1 of this CP/CPS.

**Timestamp Authority:** An organization that timestamps data, thereby asserting that the data existed at the specified time.

**Top-Level Domain**: From RFC 8499: "A Top-Level Domain is a zone that is one layer below the root, such as "com" or "jp"."

**Trademark Office:** An intellectual property office recognized by the World Intellectual Property Organization for registration of trademarks (see names of intellectual property offices as listed in the column “Office” at <https://www.wipo.int/directory/en/urls.jsp>.

**Unregistered Domain Name:** A Domain Name that is not a Registered Domain Name.

**Valid Certificate:** A Certificate that passes the validation procedure specified in RFC 5280.

**Validation Specialist:** Someone who performs the information verification duties specified in this CP/CPS.

**Validity Period:** From RFC 5280, Section 4.1.2.5: "The period of time from notBefore through notAfter, inclusive".

**Verified Method of Communication:** The use of a telephone number, a fax number, an email address, or postal delivery address, confirmed by the CA in accordance with Section 3.2.2.5 of EV Guidelines as a reliable way of communicating with the Applicant.

**WebTrust EV Program:** The additional audit procedures specified for CAs that issue EV Certificates by the AICPA/CICA to be used in conjunction with its WebTrust Program for Certification Authorities.

**WebTrust Program for CAs:** The AICPA/CPA Canada WebTrust Program for Certification Authorities.

**WebTrust Seal of Assurance:** An affirmation of compliance resulting from the WebTrust Program for CAs.

**WHOIS:** information retrieved directly from the Domain Name Registrar or registry operator via the protocol defined in RFC 3912, the Registry Data Access Protocol defined in RFC 7482, or an HTTPS website.

**Wildcard Certificate:** A Certificate containing at least one Wildcard Domain Name in the Subject Alternative Names in the Certificate.

**Wildcard Domain Name:** A string starting with `*.` (U+002A ASTERISK, U+002E FULL STOP) immediately followed by a Fully-Qualified Domain Name.

**XN-Label**: From RFC 5890: "The class of labels that begin with the prefix `xn--` (case independent), but otherwise conform to the rules for LDH labels."

### 1.6.2 Acronyms

| **Short Term** | **Explained Term** |
| -- | -------- |
| ADN | Authorization Domain Name |
| AI | Artificial Intelligence |
| AICPA | American Institute of Certified Public Accountants |
| CA | Certification Authority |
| CAA | Certification Authority Authorization |
| CCADB | Common CA Database |
| ccTLD | Country Code Top-Level Domain |
| CICA | Canadian Institute of Chartered Accountants |
| CMC | Common Mark Certificate |
| CP | Certificate Policy |
| CPA | Chartered Professional Accountant |
| CP/CPS | Certification Practice Statement |
| CRL | Certificate Revocation List |
| CSO | Chief Security Officer |
| CSR | Certificate Signing Request |
| CT | Certificate Transparency |
| DBA | Doing Business As |
| DN | Distinguished Name |
| EKU | Extended Key Usage |
| EV | Extended Validation |
| EVCP | Extended Validation Certificates Policy |
| FIPS | United States Federal Information Processing Standards |
| FQDN | Fully-Qualified Domain Name |
| gTLD | Generic Top-Level Domain |
| HSM | Hardware Security Module |
| HTTP | Hyper Text Transfer Protocol |
| IANA | Internet Assigned Numbers Authority |
| ICANN | Internet Corporation for Assigned Names and Numbers |
| IETF | Internet Engineering Task Force |
| IM | Instant Messaging |
| ISO | International Organization for Standardization |
| ISP | Internet Service Provider |
| ITU | International Telecommunication Union |
| ITU-T | ITU Telecommunication Standardization Sector |
| IV | Individual-Validated |
| MC | Mark Certificate |
| NIST | (US Government) National Institute of Standards and Technology |
| OCSP | On-line Certificate Status Protocol |
| OID | Object Identifier |
| OV | Organization-Validated |
| OVCP | Organization Validation Certificates Policy |
| PIN | Personal identification number |
| PKCS | Public Key Cryptography Standard |
| PKI | Public Key Infrastructure |
| PKIX | IETF Working Group on PKI |
| PMA | Policy Management Authority |
| QGIS | Qualified Government Information Source |
| QTIS | Qualified Government Tax Information Source |
| QIIS | Qualified Independent Information Source |
| RA | Registration Authority |
| SHA | Secure Hashing Algorithm |
| S/MIME | Secure Multipurpose Internet Mail Extensions |
| SSL | Secure Socket Layer |
| subCA | Subordinate Certification Authority |
| SV | Sponsor-Validated |
| TLD | Top-Level Domain |
| TLS | Transport Layer Security |
| URL | Uniform Resource Locator |
| VMC | Verified Mark Certificate |
| VoIP | Voice Over Internet Protocol |
| X.509 | ITU-T standard for Certificates and authentication framework |

### 1.6.3 References

The definitions, acronyms and terminology used in the SSL.com CP/CPS may draw from the documents and publications listed below:

| **Document** | **Title** |
| -- | -------- |
| FIPS 140-2 | Federal Information Processing Standards Publication - Security Requirements For Cryptographic Modules, Information Technology Laboratory, National Institute of Standards and Technology, May 25, 2001 |
| FIPS 140-3 | Federal Information Processing Standards Publication - Security Requirements For Cryptographic Modules, Information Technology Laboratory, National Institute of Standards and Technology, March 22, 2019 |
| FIPS 186-5 | Federal Information Processing Standards Publication - Digital Signature Standard (DSS), Information Technology Laboratory, National Institute of Standards and Technology, February 2023 |
| ISO 21188:2018 | Public key infrastructure for financial services -- Practices and policy framework |
| NIST SP 800-89 | Recommendation for Obtaining Assurances for Digital Signature Applications, <https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-89.pdf> |
| RFC 822 | Standard For the Format of ARPA Internet Text Messages |
| RFC 2119 | Key words for use in RFCs to Indicate Requirement Levels |
| RFC 3161 | Internet X.509 Public Key Infrastructure Time-Stamp Protocol (TSP) |
| RFC 3492 | Punycode: A Bootstring encoding of Unicode for Internationalized Domain Names in Applications (IDNA) |
| RFC 3647 | Internet X.509 Public Key Infrastructure Certificate Policy and Certification Practices Framework |
| RFC 3912 | WHOIS Protocol Specification |
| RFC 3986 | Punycode: Uniform Resource Identifier (URI): Generic Syntax |
| RFC 4035 | Protocol Modifications for the DNS Security Extensions |
| RFC 4210 | Internet X.509 Public Key Infrastructure Certificate Management Protocol (CMP) |
| RFC 4509 | Use of SHA-256 in DNSSEC Delegation Signer (DS) Resource Records (RRs) |
| RFC 5019 | The Lightweight Online Certificate Status Protocol (OCSP) Profile for High-Volume Environmentsn |
| RFC 5155 | DNS Security (DNSSEC) Hashed Authenticated Denial of Existence |
| RFC 5280 | Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile |
| RFC 5702 | Use of SHA-2 Algorithms with RSA in DNSKEY and RRSIG Resource Records for DNSSEC |
| RFC 5890 | Internationalized Domain Names for Applications (IDNA): Definitions and Document Framework |
| RFC 5952 | A Recommendation for IPv6 Address Text Representation |
| RFC 6454 | The Web Origin Concept |
| RFC 6840 | Clarifications and Implementation Notes for DNS Security (DNSSEC) |
| RFC 6960 | X.509 Internet Public Key Infrastructure Online Certificate Status Protocol - OCSP |
| RFC 6962 | Certificate Transparency |
| RFC 7231 | Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content |
| RFC 7301 | Transport Layer Security (TLS), Application-Layer Protocol Negotiation Extension |
| RFC 7482 | Registration Data Access Protocol (RDAP) Query Format |
| RFC 7538 | The Hypertext Transfer Protocol Status Code 308 (Permanent Redirect) |
| RFC 8499 | DNS Terminology |
| RFC 8555 | Automatic Certificate Management Environment (ACME) |
| RFC 8659 | DNS Certification Authority Authorization (CAA) Resource Record |
| RFC 8737 | Automated Certificate Management Environment (ACME) TLS Application-Layer Protocol Negotiation (ALPN) Challenge Extension |
| RFC 8738 | Automated Certificate Management Environment (ACME) IP Identifier Validation Extension |
| RFC 8823 | Extensions to Automatic Certificate Management Environment for End-User S/MIME Certificates |
| RFC 8954 | Online Certificate Status Protocol (OCSP) Nonce Extension |
| RFC 9336 | X.509 Certificate General-Purpose Extended Key Usage (EKU) for Document Signing |
| RFC 9495 | Certification Authority Authorization (CAA) Processing for Email Addresses |
| RFC 9598 | Internationalized Email Addresses in X.509 Certificates |
| X.509v3 | ITU-T Recommendation X.509 (2005) ISO/IEC 9594-8:2005, Information technology - Open Systems Interconnection - The Directory:  Public-key and attribute certificate frameworks |

### 1.6.4 Conventions

Terms not otherwise defined in this document shall be defined in applicable agreements, user manuals, Certificate Policies and Certification Practice Statements, of SSL.com.

#### 1.6.4.1 Definitions per RFC 2119

The key words “must”, “must not”, “required”, “shall”, “shall not”, “should”, “should not”, “recommended”, “may”, and “optional” in these documents shall be interpreted in accordance with RFC 2119.
