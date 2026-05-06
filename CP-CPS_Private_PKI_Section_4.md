# 4 CERTIFICATE LIFE-CYCLE OPERATIONAL REQUIREMENTS

This chapter specifies the policy, procedures and requirements for the management of Certificates across the entire life cycle, including:

- Application processing
- Certificate issuance
- Certificate acceptance
- Key pair and certificate usage
- Certificate re-issuance
- Certificate renewal
- Certificate re-key
- Certificate modification
- Certificate revocation and suspension
- Certificate status services
- End of subscription
- Key escrow and recovery

Any request to re-issue a certificate without changing the expiration date (the `validTo` field) and the Subject Information (the `Subject Distinguished Name` field), shall be defined as a "re-issuance" and addressed in §4.2.5.

Any request to re-issue a certificate without changing the Public Key or any other information, with the sole exception of the expiration date (the `validTo` field), shall be defined as a “renewal” and addressed in §4.6.

Any request to change the Key Pair in a certificate shall be defined as “re-keying” and addressed in §4.7. Note that, apart from the Key Pair, any other information (such as the CN, SAN entries, email addresses etc.)  may also be changed in the re-key process.

Any request to change any information in a certificate (such as the CN, SAN entries, email addresses etc.), without changing the Public Key, shall be defined as “modification” and addressed in §4.8.

SSL.com’s PKI operations follow the Certificate Management Protocol (CMP) as defined in RFC 4210.

## 4.1 Certificate Application

### 4.1.1 Who may submit a certificate application

Either the Applicant or an authorized Certificate Requester may submit certificate requests. Applicants are responsible for the accuracy of any data submitted.

In all cases SSL.com or any Enterprise RA shall require identification and authentication sufficient to meet the requirements relevant to the type of certificate requested.

SSL.com shall not issue Certificates to organizations or entities on a government denied list maintained by the United States, or which is located in a country with which the laws of the United States prohibit doing business.

SSL.com shall only issue EV SSL and EV Code Signing Certificates to Applicants which submit a complete Certificate Request and meet the requirements specified in the CA/Browser Forum's EV SSL and EV Code Signing Guidelines respectively, in addition to the requirements of this CP/CPS.

SSL.com shall only issue Mark Certificates to Mark Asserting Entities which submit a complete Certificate Request and meet the requirements specified in the MC Guidelines, in addition to the requirements of this CP/CPS.

### 4.1.2 Enrollment process and responsibilities

The enrollment process to obtain an SSL.com certificate shall include:

- Applying for a certificate
- Generating a Key Pair (except for requests associated with Mark Certificates)
- Delivering the Public Key of the Key Pair to SSL.com (except for requests associated with Mark Certificates)
- Agreeing to the applicable Subscriber Agreement, and
- Paying any applicable fees

The order in which these events occur may vary, depending on the method used and product ordered.

SSL.com shall obtain any additional documentation and perform any additional steps deemed necessary to meet the requirements for the product requested. EV TLS, EV Code Signing and Mark Certificate requests must fully meet the requirements for those products.

#### 4.1.2.1 Enrollment process for SSL.com central RA

In most cases, a request for an SSL.com certificate is made through the SSL.com Account Dashboard. Any Applicant will be directed to log in to or create an SSL.com account before any request shall be processed. A request submitted via the SSL.com Account Dashboard is identified with the account holder and considered authentic.

SSL.com may, at its sole discretion, and on a case by case basis, accept requests which are not submitted via the Applicant’s SSL.com Account. Additional verification and/or authentication may be required for requests submitted outside of the SSL.com Account Dashboard.

The following Applicant roles are required for the issuance of an EV and Mark Certificate.

1. **Certificate Requester:** The EV/Mark Certificate Request must be submitted by an authorized Certificate Requester. A Certificate Requester is a natural person who is either the Applicant, employed by the Applicant, an authorized agent who has express authority to represent the Applicant, or a third party (such as an ISP or hosting company) that completes and submits an EV/Mark Certificate Request on behalf of the Applicant.
2. **Certificate Approver:** The EV/Mark Certificate Request must be approved by an authorized Certificate Approver. A Certificate Approver is a natural person who is either the Applicant, employed by the Applicant, or an authorized agent who has express authority to represent the Applicant to (i) act as a Certificate Requester and to authorize other employees or third parties to act as a Certificate Requester, and (ii) to approve EV/Mark Certificate Requests submitted by other Certificate Requesters.
3. **Contract Signer:** A Subscriber Agreement applicable to the requested EV/Mark Certificate must be signed by an authorized Contract Signer. A Contract Signer is a natural person who is either the Applicant, employed by the Applicant, or an authorized agent who has express authority to represent the Applicant, and who has authority on behalf of the Applicant to sign Subscriber Agreements.
4. **Applicant Representative:** In the case where SSL.com and the Subscriber are affiliated, Terms of Use applicable to the requested EV/Mark Certificate must be acknowledged and agreed to by an authorized Applicant Representative. An Applicant Representative is a natural person who is either the Applicant, employed by the Applicant, or an authorized agent who has express authority to represent the Applicant, and who has authority on behalf of the Applicant to acknowledge and agree to the Terms of Use.

The Applicant may authorize one individual to occupy two or more of these roles, and/or may authorize more than one individual to occupy any of these roles.

In the F2F Verification Procedure required for Mark Certificate requests, either the Contract Signer or the Certificate Approver can act as the Designated Individual.

#### 4.1.2.2 Enrollment process for Enterprise RAs

Any Enterprise RA authorized to use the SSL.com PKI to issue Certificates must have appropriate processes in place to receive certificate requests, as detailed in chapter 3.

Any Enterprise RA authorized to use the SSL.com PKI may submit certificate requests by an authorized call to the SSL.com API.

#### 4.1.2.3 The Certificate Signing Request (CSR)

With the exception of SSL.com generating Key Pairs on behalf of an Applicant as described in §6.2.1, a valid Certificate Signing Request (CSR) must be created and submitted by the Applicant. A valid CSR will be derived from a Key Pair generated by the Applicant or the Applicant’s agent. A valid CSR will incorporate the generated Public Key and other such information as is required to create the requested certificate.

## 4.2 Certificate application processing

### 4.2.1 Performing identification and authentication functions

The Certificate request may include all factual information about the Applicant to be included in the Certificate, and such additional information as is required for SSL.com to comply with this CP/CPS. In cases where the Certificate request does not contain all the necessary information about the Applicant, SSL.com shall obtain the remaining information from the Applicant or, having obtained it from a reliable, independent, third-party data source, confirm it with the Applicant.

SSL.com maintains systems and processes to authenticate the identity of any Applicant, and follows documented procedures to verify all data requested for inclusion in the Certificate by the Applicant.

In the case of TLS certificates, applicant information MUST include, but is not limited to, at least one Fully-Qualified Domain Name or IP address to be included in the Certificate’s subjectAltName extension.

Initial identity verification and any additional validation required for specific certificate types shall follow the procedures detailed in Chapter 3.

Successful validation through these identification and authentication procedures must occur prior to issuance of any certificate.

§6.3.2 limits the validity period of Subscriber Certificates.

SSL.com MAY use the documents and data provided in §3.2 to verify certificate information, or may reuse previous validations themselves, provided that SSL.com obtained the data or document from a source specified under §3.2 or completed the validation itself within the maximum number of days prior to issuing the Certificate, as defined in the following table:

Table: Subject Identity Information validation data reuse periods

| __Certificate issued on or after__ | __Certificate issued before__  | __Maximum data reuse period__  |
| --                                 | --                             | --                             |
|                                    | March 15, 2026                 | 825 days                       |
| March 15, 2026                     |                                | 398 days                       |

For validation of Domain Names and IP Addresses according to §3.2.2.4 and §3.2.2.5, any data, document, or completed validation used MUST be obtained within the maximum number of days prior to issuing the Certificate, as defined in the following table:

Table: Domain Name and IP Address validation data reuse periods

| __Certificate issued on or after__ | __Certificate issued before__  | __Maximum data reuse period__  |
| --                                 | --                             | --                             |
|                                    | March 15, 2026                 | 398 days                       |
| March 15, 2026                     | March 15, 2027                 | 200 days                       |
| March 15, 2027                     | March 15, 2029                 | 100 days                       |
| March 15, 2029                     |                                | 10 days                        |

As an exception to the validation reuse period defined above, for Mark Certificates face-to-face validation is not required more than once for any Subscriber Organization (or Parent, Subsidiary, or Affiliate) so long as SSL.com has maintained continuous contact with one or more Subscriber representatives and maintains a system for authorization by the Subscriber of new Subscriber representatives (or representatives of a Parent, Subsidiary, or Affiliate). "Continuous contact" means SSL.com has one or more direct contacts with a Subscriber representative during the validity period of any MC issued to the Subscriber or within 90 days of the expiration of the last of the Subscriber’s MC to expire.

An authorization letter from the owner of record of the Registered Mark or Government Mark (as described in Section 3.2.17.1.2 and Section 3.2.17.2.2 of the MC Requirements) may be reused for up to 1,858 days.

Methods 4, 5 and 7 of §6.2.7.4.1 may be reused if Subscriber Private Key protection has been validated no more than 13 months prior to issuing the Code Signing Certificate.

In no case may a prior validation be reused if any data or document used in the prior validation was obtained more than the maximum time permitted for reuse of the data or document prior to issuing the Certificate.

SSL.com shall develop, maintain, and implement documented procedures that identify and require additional verification activity for High Risk Certificate Requests prior to the Certificate’s approval, as reasonably necessary to ensure that such requests are properly verified under this CP/CPS. For Code Signing and EV Code Signing Certificates, SSL.com shall determine whether the entity is identified as requesting a Code Signing Certificate from a High Risk Region of Concern

If a Delegated Third Party fulfills any of SSL.com’s obligations under this section, SSL.com shall verify that the process used by the Delegated Third Party to identify and further verify High Risk Certificate Requests provides at least the same level of assurance as SSL.com’s own processes.

### 4.2.2 Approval or rejection of certificate applications

Any certificate request which cannot be verified shall be rejected.

SSL.com SHALL NOT issue Certificates containing Internal Names or Reserved IP Addresses, as such names cannot be validated according to Section 3.2.2.4 or Section 3.2.2.5.

**Effective 2025-09-15**, SSL.com SHALL NOT issue Certificates containing Address and Routing Parameter Area Names.

**Effective 2026-03-15**, SSL.com SHALL NOT issue Certificates containing Domain Names that end in an IP Reverse Zone Suffix.

SSL.com reserves the right to reject any certificate application for any reason, including but not limited to:

- Correlation with previously revoked Certificates
- Correlation with previously rejected certificate requests
- Presence on a government denied list maintained by the United States or location in a country with which the laws of the United States prohibit doing business
- Insufficient, incorrect or inapplicable supporting documentation

SSL.com may reject the request for any certificate the issuance of which may harm, diminish or otherwise negatively impact SSL.com’s business or reputation. SSL.com shall be the sole determinant of what meets these criteria, and is not obligated to provide a reason for rejection of any Certificate Request.

SSL.com shall not issue new or replacement Code Signing Certificates to an entity that SSL.com determined intentionally signed Suspect Code. SSL.com shall keep meta-data about the reason for revoking a Code Signing Certificate as proof that the Code Signing Certificate was not revoked because the Applicant was intentionally signing Suspect Code.

SSL.com MAY issue new or replacement Code Signing Certificates to an entity who is the victim of a documented Takeover Attack, resulting in a loss of control of the Private Key associated with their Code Signing Certificate.

If SSL.com is aware that the Applicant was the victim of a Takeover Attack, SSL.com MUST verify that the Applicant is protecting its Code Signing Private Keys under §6.2.1. SSL.com MUST verify the Applicant’s compliance with §6.2.1 (i) through technical means that confirm the Private Keys are protected using the method described in §6.2.1 or (ii) by relying on a report provided by the Applicant that is signed by an auditor who is approved by SSL.com and who has IT and security training.

Documentation of a Takeover Attack MAY include a police report (validated by SSL.com) or public news report that admits that the attack took place. The Subscriber MUST provide a report from an auditor with IT and security training that provides information on how the Subscriber was storing and using Private keys and how the intended solution for better security meets this CP/CPS for improved security.

Except where issuance is expressly authorized by the Application Software Supplier, SSL.com MUST not issue new Code Signing Certificates to an entity where SSL.com is aware that the entity has been the victim of two Takeover Attacks or where SSL.com is aware that entity breached a requirement under this Section to protect Private Keys under Section 6.2.1.

Other than in the cases given above, SSL.com shall approve any successfully validated certificate application which meets the criteria for the certificate requested.

Extended Validation (EV) and Mark Certificate Requests shall require a second validation specialist for final cross-correlation and due diligence before approval, in accordance with Section 3.2.2.13 of the EV Guidelines and Section 3.2.19 of the MC Guidelines respectively. The second validation specialist may require additional documentation and/or verification before authorizing an EV or Mark Certificate. The second validation specialist cannot be the same individual who collected the documentation and originally approved the EV or Mark Certificate. In no case shall an EV or Mark Certificate be validated, authorized or issued by a single validation specialist.

In the case of EV or Mark Certificates to be issued in compliance with the requirements of section 1.3.2 of the EV Guidelines or section 1.3.2 of the MC Guidelines respectively, an Enterprise RA MAY perform the requirements of Final Cross-Correlation and Due Diligence of section 3.2.2.13 of the EV Guidelines or section 3.2.19 of the MC Guidelines respectively.

### 4.2.3 Time to process certificate applications

SSL.com shall process certificate applications in a commercially reasonable time frame.

SSL.com shall not be responsible for delays in application processing resulting from action or inaction by the Applicant or the Applicant’s agent, including omitted or incorrect details and/or documentation in the application.

SSL.com shall not be responsible for events outside of SSL.com’s control which delay application processing.

### 4.2.4 Certificate Authority Authorization (CAA)

SSL.com supports CAA for the issuance of TLS and Mark Certificates as described in §3.2.2.8.

Subscribers who wish to authorize SSL.com to issue TLS Certificates for their FQDNs should include a CAA record property `issue` or `issuewild`, including the value "ssl.com" in their respective DNS zone.

SSL.com has a contractual agreement with [Entrust](<https://www.entrust.com>) which allows SSL.com to accept Entrust's CAA domain names for issuance authorization. Subscribers who utilize Entrust as a RA and wish to authorize SSL.com to issue TLS Certificates for their Domain Names should include a CAA record property `issue` or `issuewild`, including at least one of the values "entrust.net", or "affirmtrust.com" in their respective DNS zone.

Subscribers who wish to authorize SSL.com to issue Mark Certificates for their FQDNs should include a CAA record property `issuevmc` including the value "ssl.com" in their respective DNS zone.

Subscribers who already have CAA entries with property `issue` or `issuewild` in their respective DNS zone and need a TLS Certificate from SSL.com must add a CAA record property `issue` or `issuewild`, including the value "ssl.com".

Subscribers who already have CAA entries with property `issuevmc` in their respective DNS zone and need a Mark Certificate from SSL.com must add a CAA record property `issuevmc`, including the value "ssl.com".

Starting on March 15, 2025 prior to issuing a Certificate that includes a Mailbox Address, SSL.com SHALL retrieve and process CAA records in accordance with Section 4 of RFC 9495 (Certification Authority Authorization (CAA) Processing for Email Addresses).

When processing CAA records, SSL.com SHALL process the `issuemail` property tag as specified in RFC 9495. Additional property tags MAY be supported, but SHALL NOT conflict with or supersede the authorizations to issue S/MIME Certificates as specified in the `issuemail` property tag.

If SSL.com issues a Certificate following a CAA check, SSL.com SHALL do so within the TTL of the CAA record, or 8 hours, whichever is greater. This stipulation does not prevent SSL.com from checking CAA records at any other time.

If the Certificate includes more than one Mailbox Address, then SSL.com SHALL perform the above procedure for each Mailbox Address.

CAA checking is optional for Certificates issued by a Technically Constrained Subordinate CA Certificate as set out in §7.1.5, where the lack of CAA checking is an explicit contractual provision in the contract with the Technically Constrained Subordinate CA Applicant.

SSL.com SHALL NOT issue a Certificate unless SSL.com determines that Certificate Request is consistent with the applicable CAA RRset. SSL.com SHALL log all actions taken, if any, consistent with its CAA processing practice.

SSL.com is permitted to treat a record lookup failure as permission to issue if:

- the failure is outside SSL.com's infrastructure; and
- the lookup has been retried at least once; and
- the domain's zone does not have a DNSSEC validation chain to the ICANN root.

### 4.2.5 Re-issuance Requests

In the case of EV SSL and EV Code Signing Certificates, SSL.com may rely on a previously verified certificate request to issue a replacement certificate, so long as the certificate being referenced was not revoked due to fraud or other illegal conduct, if:

1. The expiration date of the replacement certificate is the same as the expiration date of the EV Certificate that is being replaced, and
2. The Subject Information of the Certificate is the same as the Subject in the EV Certificate that is being replaced.

## 4.3 Certificate issuance

### 4.3.1 CA actions during certificate issuance

Any RA, internal or external, utilizing SSL.com’s PKI shall perform validation of all information sent before issuing any certificate.

Before issuance of a Mark Certificate, SSL.com SHALL log the Mark pre-certificate (including all the data included in the Subject field of the certificate plus the Mark Representation) to one or more public CT logs.

#### 4.3.1.1 Manual authorization of certificate issuance for Root CAs

Certificate issuance by a Root CA shall require an individual authorized by SSL.com (i.e. the CA system operator, system officer, or PKI administrator) to deliberately issue a direct command in order for the Root CA to perform a certificate signing operation.

#### 4.3.1.2 Linting of to-be-signed Certificate content

Due to the complexity involved in implementing Certificate Profiles that conform to the Baseline Requirements, SSL.com SHOULD implement a Linting process to test the technical conformity of each to-be-signed artifact prior to signing it. When a Precertificate has undergone Linting, it is not necessary for the corresponding to-be-signed Certificate to also undergo Linting, provided that SSL.com has a technical control to verify that the to-be-signed Certificate corresponds to the to-be-signed Precertificate in the manner described by RFC 6962, Section 3.2.

**Effective 2025-03-15**, SSL.com SHALL implement such a Linting process.

Methods used to produce a certificate containing the to-be-signed Certificate content include, but are not limited to:

1. Sign the `tbsCertificate` with a "dummy" Private Key whose Public Key component is not certified by a Certificate that chains to a publicly-trusted CA Certificate; or
2. Specify a static value for the `signature` field of the Certificate ASN.1 SEQUENCE.

SSL.com SHOULD use the Linting tools that have been widely adopted by the industry (see <https://cabforum.org/resources/tools/>). SSL.com MAY also use its own certificate Linting tools.

#### 4.3.1.3 Linting of issued Certificates

SSL.com MAY use a Linting process to test each issued Certificate.

### 4.3.2 Notification to Subscriber by the CA of issuance of Certificate

Any RA, internal or external, utilizing SSL.com’s PKI shall notify the Subscriber of the successful issuance of a certificate. Notification shall be by email, using an email address provided by the Subscriber.
Notification may, at SSL.com’s sole discretion, be provided by other means as required.

Notification shall also constitute acknowledgement that the certificate is available for review, access and download from the SSL.com Account Dashboard correlating to the certificate ordered.

## 4.4 Certificate acceptance

### 4.4.1 Conduct constituting certificate acceptance

The Subscriber or Subscriber’s agent is responsible for review and verification of information contained in the issued certificate. The Subscriber or agent shall be deemed to have accepted the certificate:

- By downloading, installing or taking delivery by any other method of the certificate
- After 30 (thirty) days have passed from the communication of fulfillment.

### 4.4.2 Publication of the certificate by the CA

Any certificate issued by SSL.com shall be published by email to the address corresponding to the Subscriber or agent requesting the certificate.

The certificate may also be published by other means, including:

- Publication to the corresponding SSL.com Account
- Publication to a public repository, such as an x.500 or LDAP repository
- Publication to other entities as required by the SSL.com PKI CP/CPS

### 4.4.3 Notification of certificate issuance by the CA to other Entities

Any RA, internal or external, may be notified regarding the issuance of a certificate. Notification may include transmission of the certificate by SSL.com as the issuing CA to a corresponding Enterprise RA.

## 4.5 Key pair and certificate usage

### 4.5.1 Subscriber Private Key and certificate usage

Subscribers using any certificate issued through the SSL.com PKI are required to protect the Private Key for that certificate, including:

- Securing the Private Key (and any copies made) to prevent disclosure or compromise
- Using the Private Key and/or certificate only as authorized by the relevant terms of service and/or Subscriber Agreement
- Ceasing use of the Private Key after expiration or revocation of the associated certificate
- Contacting the issuing entity if the Private Key is compromised
- Using the certificate only as applicable and for the intended purpose (per the key usage field of that certificate)

Subscribers requesting or utilizing Document Signing, Code Signing or EV Code Signing Certificates must observe the requirements for Private Key generation and protection given in §6.2.1 of this CP/CPS.

Subscriber private keys associated with Mark Certificates do not need to be protected, and may be discarded.

### 4.5.2 Relying party Public Key and certificate usage

Any party relying on a certificate issued using the SSL.com PKI accepts responsibilities for the use of a Subscriber’s Public Key and certificate. These responsibilities include:

- Obligation to rely on the certificate only for applications appropriate for the Certificate type (as set forth in this CP/CPS) and consistent with applicable certificate content (e.g., key usage field)
- Successful performance of Public Key operations as a condition of relying on a certificate
- Assumption of responsibility to check the certificate’s status, including using one of the required or permitted mechanisms set forth in this CP/CPS (as referenced in §4.9)
- Assent to the terms of the applicable Relying Party Agreement as a condition of relying on the certificate

## 4.6 Certificate renewal

For the purposes of this CP/CPS, “certificate renewal” means the issuance of a new certificate without changing the Public Key or any other information used in the original certificate, with the sole exception of the `notAfter` field (i.e. the renewal date).

### 4.6.1 Circumstance for certificate renewal

Unless otherwise specifically prohibited in this CP/CPS, any certificate issued utilizing the SSL.com PKI may be renewed if the certificate meets the following criteria:

- The original certificate has not been revoked or otherwise flagged
- The Public Key from the original certificate has not been blocklisted
- The Private Key corresponding to the original certificate has not been compromised
- The key lifetime is not exceeded as stated in §6.3.2
- All information within the certificate, other than the `notAfter` field, remains accurate
- The renewed certificate's cryptographic security is deemed to remain sufficient for the certificate’s intended lifetime
- The information provided in the request still passes the appropriate validation checks
- No further or additional validation is required beyond repeating the same steps performed originally

Certificates which have either been previously renewed or previously re-keyed may be renewed again so long as the criteria above are met.
The original certificate may be revoked after renewal is complete. Revocation after renewal shall be at the sole discretion of SSL.com or the authorized entity utilizing the SSL.com PKI to process the renewal.
Regardless of revocation status, the original certificate shall not be further renewed, re-keyed or modified.

### 4.6.2 Who may request renewal

Renewal of a certificate issued utilizing the SSL.com PKI may be requested by the Subscriber or the Subscriber’s agent.

Subscribers with Certificates issued directly by SSL.com may request renewal via their SSL.com Account Dashboard.

Any RA, internal or external, utilizing the SSL.com PKI shall require a specific request for renewal.

Certificates issued by any entity utilizing the SSL.com PKI shall not be automatically renewed.

### 4.6.3 Processing certificate renewal requests

Renewal requests shall require validation and/or authentication identical to that for a new certificate.

Subscribers with Certificates issued directly by SSL.com may request renewal via their SSL.com Account Dashboard.

Any certificate slated for renewal shall re-use all information in the original request, with the sole exception of the expiration date (the `notAfter` field).

Any certificate slated for renewal which for any reason fails re-verification and/or re-authentication of the certificate shall not be renewed.

Certificates which cannot be renewed may be capable of re-keying as defined and described in §4.7.

### 4.6.4 Notification of renewed certificate issuance to Subscriber

Any certificate renewed via the SSL.com PKI shall utilize a notification method identical to that for a new certificate, in compliance with §4.4.2.

### 4.6.5 Conduct constituting acceptance of a renewal certificate

Acceptance of any certificate renewed via the SSL.com PKI shall use the same methods described for a new certificate in §4.4.1.

### 4.6.6 Publication of the renewal certificate by the CA

Any certificate renewed via the SSL.com PKI may be published via email to the Subscriber using the same methods described for a new certificate in §4.4.2.

### 4.6.7 Notification of certificate issuance by the CA to other Entities

Notification to other entities may also be performed for any renewed certificate using the same methods described for a new certificate in §4.4.3.

## 4.7 Certificate re-key

For the purposes of this CP/CPS, “certificate re-keying” means the re-issuance of a certificate which utilizes a new Key Pair.

Other information used in the original certificate may or may not be changed when a certificate is re-keyed.

In all cases where re-keying is requested and/or performed a new Certificate Signing Request (CSR) must be submitted (per §4.1.2.3) to obtain the new Public Key required.

Mark Certificates shall not be re-keyed.

### 4.7.1 Circumstances for certificate re-key

Any certificate issued utilizing the SSL.com PKI may be re-keyed, unless otherwise specifically prohibited in the SSL.com PKI CP/CPS.

#### 4.7.1.1 Revocation

In certain cases, an original certificate or previously issued certificate must be revoked as a condition of re-keying.

For instance, if the `subject:commonName` or a `subjectAltName:dNSName` field is altered for the following certificate categories with relation to the previously issued certificate, the original certificate must be revoked as a condition of re-keying:

- Basic SSL
- High Assurance SSL
- Premium SSL
- Wildcard SSL
- Enterprise EV SSL

In all other cases, the original certificate may be revoked after re-keying is complete. In these cases, revocation after re-keying shall be at the sole discretion of SSL.com or the authorized entity utilizing the SSL.com PKI to process the re-key request.

#### 4.7.1.2 Loss, theft or compromise

Any Subscriber, agent or authorized entity utilizing the SSL.com PKI to create a certificate whose Private Key has been stolen, lost or otherwise compromised should immediately request re-keying of that certificate.

The Subscriber should also request revocation of the Public Key that is associated with the lost, stolen or compromised Private Key.

For Server Certificates, if the Subscriber requests that SSL.com revoke a Certificate for the reason of Key Compromise, and has not previously demonstrated and cannot currently demonstrate possession of the associated Private Key of the Certificate, SSL.com MAY revoke all certificates associated with that Subscriber that contain that Public Key. SSL.com SHALL NOT assume that it has evidence of Private Key compromise for the purposes of revoking the certificates of other subscribers, but MAY block issuance of future certificates with that key.

SSL.com is not responsible for loss, damages or injury resulting from any compromise of a Private Key. Reference should be made to the Subscriber Agreement and/or Relying Party Agreement applicable to the certificate for more information regarding compromised Private Keys.

#### 4.7.1.3 Key pair expiration

Any expired certificate issued from a Key Pair whose usage period has also expired must be re-keyed, unless otherwise specifically prohibited in the SSL.com CP/CPS.

### 4.7.2 Who may request certification of a new Public Key

Re-keying of a certificate issued via the SSL.com PKI may be requested by the Subscriber or the Subscriber’s agent.

Subscribers with Certificates issued directly by SSL.com may request re-keying directly via their SSL.com Account Dashboard.

Any RA, internal or external, utilizing the SSL.com PKI may request a certificate re-key if compromise of that certificate’s Private Key is known or suspected to have occurred. This re-keying shall occur at the discretion of SSL.com and/or the internal or Enterprise RA concerned.

### 4.7.3 Processing certificate re-keying requests

Re-keying requests must be accompanied by a new CSR.

Any certificate slated for re-keying may be re-issued using any or all information in the original request, with the exception of the Public Key and the date of issuance date (the `validFrom` field).

Other information may be changed in a re-key request, as requested by the Subscriber or the Authorized Entity requesting the re-key.

Re-keying requests shall require validation and/or authentication, as described in §4.2.

Any certificate submitted for re-keying which for any reason fails verification and/or authentication shall not be issued.

### 4.7.4 Notification of new certificate issuance to Subscriber

Any certificate re-keyed via the SSL.com PKI shall utilize a notification method which is in compliance with Section 4.4.2.

### 4.7.5 Conduct constituting acceptance of a re-keyed certificate

Acceptance of any certificate re-keyed via the SSL.com PKI shall use the same methods described for a new certificate in §4.4.1.

### 4.7.6 Publication of the re-keyed certificate by the CA

Any certificate re-keyed via the SSL.com PKI may be published via email to the Subscriber using the same methods described for a new certificate in §4.4.2.

### 4.7.7 Notification of certificate issuance by the CA to other Entities

Notification to other entities may also be performed for any re-keyed certificate using the same methods as described in §4.4.3

## 4.8 Certificate modification

For the purposes of the SSL.com CP/CPS, “certificate modification” means the issuance of a new certificate in which non-essential information has changed, without changing the Key Pair related to the original certificate.

### 4.8.1 Circumstance for certificate modification

Certificate modification may be requested by a Subscriber when non-essential attributes change, including but not limited to:

- Country change
- Role change
- Address change
- A reorganization resulting in alteration of a DN

Any re-issuance of a certificate in which information other than the Key Pair changes, shall be considered certificate modification. The original Certificate may be revoked after modification is complete, but the original Certificate shall not be further renewed, re-keyed or modified.

### 4.8.2 Who may request certificate modification

Modification of a certificate issued via the SSL.com PKI may be requested by the Subscriber or the Subscriber’s agent.

Subscribers with Certificates issued directly by SSL.com may request modification directly via their SSL.com Account Dashboard.

### 4.8.3 Processing certificate modification requests

Modification requests shall require validation and/or authentication, as described in §4.2. Any certificate slated for modification which for any reason fails verification and/or authentication of the certificate shall not be renewed.

### 4.8.4 Notification of modified certificate issuance to Subscriber

Any certificate modified via the SSL.com PKI shall utilize a notification method which is in compliance with Section 4.4.2.

### 4.8.5 Conduct constituting acceptance of modified certificate

Acceptance of any certificate modified via the SSL.com PKI shall use the same methods described for a new certificate in §4.4.1.

### 4.8.6 Publication of the modified certificate by the CA

Any certificate modified via the SSL.com PKI may be published via email to the Subscriber using the same methods described for a new certificate in §4.4.2.

### 4.8.7 Notification of modified certificate issuance by the CA to other Entities

Notification to other entities may also be performed for any modified certificate using the same methods as described in §4.4.3.

## 4.9 Certificate revocation and suspension

For the purposes of the SSL.com CP/CPS, "revocation" is defined as adding the serial number of a certificate issued via the SSL.com PKI to a Certificate Revocation List (CRL), an Online Certificate Status Protocol (OSCP) and any other relevant database used for blocklisting.

### 4.9.1 Circumstances for revocation

#### 4.9.1.1 Reasons for Revoking a Subscriber Certificate

Mark Certificates need not be revoked if their unused Private Key suffers a Key Compromise.

SSL.com MAY support revocation of Short-lived Subscriber Certificates.

With the exception of Short-lived Subscriber Certificates, SSL.com SHALL revoke a TLS or Code Signing Certificate within 24 hours and use the corresponding CRLReason (see Section 7.2.2) if one or more of the following occurs:

1. The Subscriber requests in writing that SSL.com revoke the Certificate
    a. specifying a CRLreason of
        - keyCompromise (CRLReason #1) (e.g. the Subscriber's Private Key is suspected of compromise);
        - cessationOfOperation (CRLReason #5) (e.g. the Subscriber will no longer be using the Certificate because they are discontinuing their website);
        - affiliationChanged (CRLReason #3) (e.g. identifying information about the Subscriber in the Certificate has changed); or
        - superseded (CRLReason #4) (e.g. the Subscriber requests a new certificate to replace an existing certificate);
    b. without specifying a CRLreason, which leads to CRLReason "unspecified (0)" which results in no reasonCode extension being provided in the CRL;

If the Subscriber requests revocation for Key Compromise and cannot demonstrate possession of the associated Private Key of that Certificate, then SSL.com MAY revoke all certificates associated with that Subscriber that contain that Public Key. SSL.com MUST NOT assume that it has evidence of Key Compromise for the purposes of revoking the Certificates of other Subscribers, but MAY block issuance of future certificates with that key;

2. The Subscriber notifies SSL.com that the original certificate request was not authorized and does not retroactively grant authorization (CRLReason #9, privilegeWithdrawn);
3. SSL.com obtains evidence that the Subscriber's Private Key corresponding to the Public Key in the Certificate suffered a Key Compromise (CRLReason #1, keyCompromise);
4. SSL.com is made aware of a demonstrated or proven method that can easily compute the Subscriber’s Private Key based on the Public Key in the Certificate, including but not limited to those identified in [Section 6.1.1.2(5)](#6112-subscriber-key-pair-generation) (CRLReason #1, keyCompromise);
5. SSL.com is made aware of a demonstrated or proven method that exposes the Subscriber's Private Key to compromise, or if there is clear evidence that the specific method used to generate the Private Key was flawed (CRLReason #1, keyCompromise);
6. SSL.com obtains evidence that the validation of domain authorization or control for any Fully-Qualified Domain Name or IP address or email address in the Certificate should not be relied upon (CRLReason #4, superseded).
7. SSL.com has reasonable assurance that the Certificate was used to sign Suspect Code (CRLReason #9, privilegeWithdrawn).

With the exception of Short-lived Subscriber Certificates, SSL.com SHOULD revoke a certificate within 24 hours and SHALL revoke a Certificate within 5 days and use the corresponding CRLReason (see Section 7.2.2) if one or more of the following occurs:

1. The Certificate no longer complies with the requirements of §6.1.5 and §6.1.6 (CRLReason #4, superseded);
2. SSL.com obtains evidence that the Certificate was misused (CRLReason #9, privilegeWithdrawn);
3. SSL.com is made aware that a Subscriber has violated one or more of its material obligations under the Subscriber Agreement or Terms of Use (CRLReason #9, privilegeWithdrawn);
4. SSL.com is made aware of any circumstance indicating that use of a Fully-Qualified Domain Name or IP address or email address in the Certificate is no longer legally permitted (e.g. a court or arbitrator has revoked a Domain Name Registrant's right to use the Domain Name, a relevant licensing or services agreement between the Domain Name Registrant and the Applicant has terminated, or the Domain Name Registrant has failed to renew the Domain Name) (CRLReason #5, cessationOfOperation);
5. SSL.com is made aware that a Wildcard Certificate has been used to authenticate a fraudulently misleading subordinate Fully-Qualified Domain Name (CRLReason #9, privilegeWithdrawn);
6. SSL.com is made aware of a material change in the information contained in the Certificate (CRLReason #9, privilegeWithdrawn);
7. SSL.com is made aware that the Certificate was not issued in accordance with the applicable requirements or this CP/CPS or an applicable alternate CPS (CRLReason #4, superseded);
8. SSL.com determines or is made aware that any of the information appearing in the Certificate is inaccurate (CRLReason #9, privilegeWithdrawn);
9. SSL.com's right to issue Certificates is revoked or terminated, unless SSL.com has made arrangements to continue maintaining the CRL/OCSP Repository (CRLReason "unspecified (0)" which results in no reasonCode extension being provided in the CRL);
10. Revocation is required by SSL.com's CP/CPS for a reason that is not otherwise required to be specified by section 4.9.1.1 of the Baseline Requirements or section 4.9.1.1 of the Code Signing Baseline Requirements (CRLReason "unspecified (0)" which results in no reasonCode extension being provided in the CRL); or
11. SSL.com receives a lawful and binding ruling from a Government or regulatory body to revoke the Certificate (CRLReason #9, privilegeWithdrawn).
12. For Mark Certificates SSL.com receives a Court Order of Infringement, confirms the authenticity of the Court Order of Infringement, and provides 3 business days notice to the Subscriber that the MC will be revoked.

SSL.com MAY delay revocation of a Code Signing Certificate based on a request from Application Software Suppliers where immediate revocation has a potentially large negative impact to the ecosystem.

When SSL.com obtains verifiable evidence of Key Compromise for a Certificate whose CRL entry does not contain a reasonCode extension or has a reasonCode extension with a non-keyCompromise reason, SSL.com SHOULD update the CRL entry to enter keyCompromise as the CRLReason in the reasonCode extension. Additionally, SSL.com SHOULD update the revocation date in a CRL entry when it is determined that the Private Key of the Certificate was compromised prior to the revocation date that is indicated in the CRL entry for that Certificate.

#### 4.9.1.2 Reasons for Revoking a Subordinate CA Certificate

SSL.com SHALL revoke a Subordinate CA Certificate within seven (7) days, if one or more of the following occurs:

1. The Subordinate CA requests revocation in writing;
2. The Subordinate CA notifies SSL.com that the original certificate request was not authorized and does not retroactively grant authorization;
3. SSL.com obtains evidence that the Subordinate CA’s Private Key corresponding to the Public Key in the Certificate suffered a Key Compromise or no longer complies with the requirements of §6.1.5 and §6.1.6,
4. SSL.com obtains evidence that the Certificate was misused;
5. SSL.com is made aware that the Certificate was not issued in compliance with the applicable requirements or this CP/CPS or an applicable alternate CPS;
6. SSL.com determines that any of the information appearing in the Certificate is inaccurate or misleading;
7. SSL.com or Subordinate CA ceases operations for any reason and has not made arrangements for another CA to provide revocation support for the Certificate;
8. SSL.com’s or Subordinate CA's right to issue Certificates under the applicable requirements and this CP/CPS expires or is revoked or terminated, unless the Issuing CA has made arrangements to continue maintaining the CRL/OCSP Repository;
9. Revocation is required by SSL.com’s CP/CPS.
10. SSL.com receives a lawful and binding ruling from a Government or regulatory body to revoke a CA Certificate.

Applicable revocation reasons (per RFC 5280 and ITU-T X.509) for CA Certificates, are:

- **cACompromise** is used in revoking a CA certificate; it indicates that it is known or suspected that the subject's private key, or other aspects of the subject validated in the CA certificate, have been compromised.
- **affiliationChanged** indicates that the subject's name or other information in the public-key certificate has been modified but there is no cause to suspect that the private key has been compromised.
- **superseded** indicates that the public-key certificate has been superseded but there is no cause to suspect that the private key has been compromised.
- **cessationOfOperation** indicates that the public-key certificate is no longer needed for the purpose for which it was issued but there is no cause to suspect that the private key has been compromised.
- **privilegeWithdrawn** indicates that a public-key certificate was revoked because a privilege contained within that public-key certificate has been withdrawn.

### 4.9.2 Who can request revocation

Revocation of a certificate issued utilizing the SSL.com PKI may be requested by the Subscriber or the Subscriber’s agent. Any RA, internal or external, utilizing the SSL.com PKI may request revocation of a certificate.

Non-Subscribers who wish to request revocation due to reasons which meet one or more of the criteria given in §4.9.1 may file a Certificate Problem Report, as described in §3.4.2 and §4.9.3.3.

### 4.9.3 Procedure for revocation request

Revocation may be initiated by submitting a request to the appropriate RA (internal or external). A Subscriber can submit a revocation request via an email account associated with the corresponding SSL.com certificate order. Other approved methods of communication may be allowed, provided that corresponding account credentials are sufficiently presented.

SSL.com shall maintain a continuous 24x7 ability to accept and respond to revocation requests and Certificate Problem Reports.

Relying Parties, Application Software Suppliers, and other non-Subscribers may report suspected Private Key Compromise, Certificate misuse, or other types of fraud, compromise, misuse, inappropriate conduct, or any other matter related to Certificates and request certificate revocation as described in §4.9.3.3.

#### 4.9.3.1 Revocation requested by Subscriber or Subscriber's agent

SSL.com shall respond within 24 hours to a Subscriber's valid revocation request. A valid revocation request is one in which the corresponding account credentials, in conjunction with one or more of the criteria outlined in §4.9.1, are sufficiently presented.

For Server Certificates, if a Subscriber requesting revocation for the reason of Key Compromise has previously demonstrated or can currently demonstrate possession of the private key of the certificate as described in §4.9.12, then SSL.com SHALL revoke all non-expired Server Certificates associated with that key across all Subscribers.

#### 4.9.3.2 Revocation Requested by an Enterprise RA

Any authorized Enterprise RA utilizing the SSL.com PKI may request revocation of a certificate only if proper credentials are presented. Should the request meet any of the criteria given in §4.9.1, along with approved account credentials, SSL.com CA shall complete the revocation.

For any revocation request received from an External RA, SSL.com shall provide a signed acknowledgement of the request and confirmation of actions to the requesting RA.

#### 4.9.3.3 Revocation requested by Non-Subscribers

Relying Parties, Application Software Suppliers, and other non-Subscribers seeking to request revocation of a Certificate will find instructions for filing a Certificate Problem Report at <https://www.ssl.com/revoke>. Certificate Problem Reports should be filed to report suspected Private Key Compromise, Certificate misuse, or other types of fraud, compromise, misuse, inappropriate conduct, or any other matter related to Certificates. SSL.com shall proceed with the revocation process if the request meets any of the scenarios described in §3.4.2 and/or §4.9.1.1.

For Server Certificates, if anyone requesting revocation for the reason of Key Compromise has previously demonstrated or can currently demonstrate possession of the private key of the certificate as described in §4.9.12, then SSL.com SHALL revoke all non-expired Server Certificates associated with that key across all Subscribers.

#### 4.9.3.4 Revocation requested by an Application Software Supplier

If an Application Software Supplier requests SSL.com to revoke a Certificate because the Application Software Supplier believes that a Certificate attribute is deceptive, or that the Certificate is being used for malware, bundle ware, unwanted software, or some other illicit purpose, then the Application Software Supplier may request that SSL.com revoke the certificate.

Within two (2) business days of receipt of the request, SSL.com MUST either revoke the certificate or inform the Application Software Supplier that it is conducting an investigation.

If SSL.com decides to conduct an investigation, it MUST inform the Application Software Supplier whether or not it will revoke the Certificate, within two (2) business days.

If SSL.com decides that the revocation will have an unreasonable impact on its customer, then SSL.com MUST propose an alternative course of action to the Application Software Supplier based on its investigation.

### 4.9.4 Revocation request grace period

The grace period given for TLS certificates is the maximum allowed by the CA/B Forum Baseline Requirements.

For all incidents involving malware, SSL.com SHALL revoke the Code Signing Certificate in accordance with and within the following maximum timeframes. Nothing herein prohibits SSL.com from revoking a Code Signing Certificate prior to these timeframes.

1. SSL.com SHALL contact the software publisher within one (1) business day after SSL.com is made aware of the incident.
2. SSL.com SHALL determine the volume of relying parties that are impacted (e.g., based on OCSP logs) within 72 hours after being made aware of the incident.
3. SSL.com SHALL request the software publisher send an acknowledgement to SSL.com within 72 hours of receipt of the request.
    a. If the publisher responds within 72 hours, SSL.com and publisher SHALL determine a "reasonable date" to revoke the certificate based on discussions with SSL.com.
    b. If the publisher does NOT respond within 72 hours, SSL.com SHALL notify the publisher that SSL.com will revoke the certificate in 7 days if no further response is received.
        i. If the publisher responds within 7 days, SSL.com and the publisher will determine a "reasonable date" to revoke the certificate based on discussion with SSL.com.
        ii. If the publisher does NOT respond after 7 days, SSL.com SHALL revoke the certificate, except if SSL.com has documented proof (e.g., OCSP logs) that this will cause significant impact to the general public.
  
#### 4.9.4.1 Code Signing Certificate revocation dates

When revocation of a Code Signing Subscriber Certificate is done due to a Key Compromise or use in Suspect Code SSL.com SHALL determine an appropriate value for the revocationDate based on its own investigation. SSL.com SHALL set a historic date as revocationDate if deemed appropriate.

More specifically:

1. A Certificate MAY have a one-to-one relationship or one-to-many relationship with the signed Code. Regardless, revocation of a Certificate may invalidate the Code Signatures on all signed Code, some of which could be perfectly sound. Because of this, after working with the Subscriber, SSL.com MAY specify the time at which the Certificate is first considered to be invalid in the `revocationDate` field of a CRL entry or the `revocationTime` field of an OCSP response to time-bind the set of software affected by the revocation, and software should continue to treat objects containing a timestamp dated before the revocation date as valid. This is called a back dated revocation and applies only to signing Certificates.
2. Backdating the revocationDate field is an exception to best practice described in RFC 5280 (section 5.3.2); however, the Code Signing Baseline Requirements specify the use of the `revocationDate` field to convey the “invalidity date” to support Application Software Supplier software implementations that process the `revocationDate` field as the date when the Certificate is first considered to be invalid.
3. SSL.com reserves the right to back date a revocation of signing certificates to nullify any trust applied to Code signed with those certificates, for reasons described in §4.9.1.1, including the violation of material obligations established in the Subscriber Agreement (e.g. non-payment, dispute or chargeback of payment, breach of financial obligations, or other payment disputes resulting in a refund of fees associated with the certificate lifespan).
4. If a Code Signing Certificate previously has been revoked, and the SSL.com later becomes aware of a more appropriate revocation date, then SSL.com MAY use that revocation date in subsequent CRL entries and OCSP responses for that Code Signing Certificate.

### 4.9.5 Time within which CA must process the revocation request

SSL.com SHALL provide a preliminary report on its findings within 24 hours after receiving a Certificate Problem Report to both the Subscriber and the entity who filed the Certificate Problem Report.

Based on these findings, SSL.com SHALL work with the Subscriber and any entity reporting the Certificate Problem Report or other revocation-related notice to establish whether or not the certificate will be revoked, and if so, a date upon which SSL.com will revoke the certificate. The period from receipt of the Certificate Problem Report or revocation-related notice to published revocation MUST NOT exceed the time frame set forth in §4.9.1.1.

SSL.com SHALL determine whether revocation or other appropriate action is warranted and set a revocation date based on at least the following criteria:

1. The nature of the alleged problem (scope, context, severity, magnitude, risk of harm);
2. The consequences of revocation (direct and collateral impacts to Subscribers and Relying Parties);
3. The number of Certificate Problem Report received about a particular Certificate or Subscriber;
4. The entity making the complaint (for example, a complaint from a law enforcement official that a Web site is engaged in illegal activities should carry more weight than a complaint from a consumer alleging that she didn't receive the goods she ordered); and
5. Relevant legislation.

### 4.9.6 Revocation checking requirement for relying parties

Relying parties should validate the authenticity and intended usage of a Certificate using the resources described in §4.10.1.

### 4.9.7 CRL issuance frequency

Within **twenty-four (24) hours** of issuing its first Certificate, the Issuing CA SHALL generate and publish either:

- a full and complete CRL; OR
- partitioned (i.e., "sharded") CRLs that, when aggregated, represent the equivalent of a full and complete CRL.

For CAs issuing Subscriber Certificates:

- A new CRL SHALL be updated and published at least every:
    - **seven (7) days** if all Certificates include an Authority Information Access extension with an id-ad-ocsp accessMethod (“AIA OCSP pointer”); or
    - **four (4) days** in all other cases;
- A new CRL SHALL be updated and published within **twenty-four (24) hours** after recording a Certificate as revoked.
- The value of the `nextUpdate` field of the CRL SHALL NOT be more than **ten (10) days** beyond the value of the `thisUpdate` field.

For the status of Code Signing Certificates, SSL.com SHALL publish a CRL then it SHALL be updated and reissued at least once every **seven (7) days**, and the value of the `nextUpdate` field SHALL NOT be more than **ten (10) days** beyond the value of the `thisUpdate` field.

For the status of NAESB Subscriber Certificates, the CRL SHALL be updated and reissued at least once every **twenty-four (24) hours**, and the value of the `nextUpdate` field SHALL NOT be more than **ten (10) days** beyond the value of the `thisUpdate` field.

For CAs issuing CA Certificates:  

- A new CRL SHALL be updated and published at least every **twelve (12) months**;
- A new CRL SHALL be updated and published SHALL be updated and published within **twenty-four (24) hours** after recording a Certificate as revoked.
- The value of the `nextUpdate` field of the CRL SHALL NOT be more than **twelve (12) months** beyond the value of the `thisUpdate` field.

For the status of CA Certificates issuing NAESB Subscriber Certificates, SSL.com SHALL update and reissue CRLs at least:

- once every **six (6) months** and
- within **three (3) hours** after revoking a NAESB Issuing Subordinate CA Certificate,

and the value of the `nextUpdate` field SHALL NOT be more than **twelve (12) months** beyond the value of the `thisUpdate` field.

Under normal conditions, SSL.com posts new entries to the CRL as soon as a revocation request is confirmed.

For TLS Certificates, SSL.com SHALL continue issuing CRLs until one of the following is true:
- all Subordinate CA Certificates containing the same Subject Public Key are expired or revoked; OR
- the corresponding Subordinate CA Private Key is destroyed.

For Code Signing, EV Code Signing, Document Signing and Timestamp Certificate, SSL.com SHALL provide accurate and up-to-date revocation status information for a period not less than **ten (10) years** beyond expiry of a Certificate (see also 4.10.1). After the expiration of a Code Signing or Timestamp Issuing CA, the associated CRLs SHALL remain published for at least **five (5) years** beyond the expiry of that Issuing CA.

### 4.9.8 Maximum latency for CRLs

Where applicable, the maximum latency for the Certificate Revocation List is ten (10) minutes.

### 4.9.9 On-line revocation/status checking availability

The validity interval of an OCSP response is the difference in time between the `thisUpdate` and `nextUpdate` field, inclusive. For purposes of computing differences, a difference of 3,600 seconds shall be equal to one hour, and a difference of 86,400 seconds shall be equal to one day, ignoring leap-seconds.

A certificate serial is "assigned" if:

- a Certificate or Precertificate with that serial number has been issued by the Issuing CA; or
- a Precertificate with that serial number has been issued by a Precertificate Signing Certificate, as defined in Section 7.1.2.4 of the Baseline Requirements, associated with the Issuing CA.

A certificate serial is "unassigned" if it is not "assigned".

The following SHALL apply for communicating the status of Certificates and Precertificates which include an Authority Information Access extension with an id-ad-ocsp accessMethod.

OCSP responders operated by SSL.com SHALL support the HTTP GET method, as described in RFC 6960 and/or RFC 5019. The CA MAY process the Nonce extension (`1.3.6.1.5.5.7.48.1.2`) in accordance with RFC 8954.

For the status of a Subscriber Certificate or its corresponding Precertificate:

- An authoritative OCSP response MUST be available (i.e. the responder MUST NOT respond with the "unknown" status) starting no more than 15 minutes after the Certificate or Precertificate is first published or otherwise made available.
- For OCSP responses with validity intervals less than sixteen hours, SSL.com SHALL provide an updated OCSP response prior to one-half of the validity period before the nextUpdate.
- For OCSP responses with validity intervals greater than or equal to sixteen hours, SSL.com SHALL provide an updated OCSP response at least eight hours prior to the nextUpdate, and no later than four days after the thisUpdate.

For the status of a Subordinate CA Certificate, SSL.com SHALL provide an updated OCSP response at least every twelve months, and within 24 hours after revoking the Certificate.

The following SHALL apply for communicating the status of *all* Certificates for which an OCSP responder is willing or required to respond.

OCSP responses MUST conform to RFC6960 and/or RFC5019. OCSP responses MUST either:

1. be signed by the CA that issued the Certificates whose revocation status is being checked, or
2. be signed by an OCSP Responder which complies with the OCSP Responder Certificate Profile in Section 7.1.2.8 of the Baseline Requirements.

OCSP responses for Subscriber Certificates MUST have a validity interval greater than or equal to eight hours and less than or equal to ten days.

If the OCSP responder receives a request for the status of a certificate serial number that is "unassigned", then the responder SHOULD NOT respond with a "good" status. If the OCSP responder is for a CA that is not Technically Constrained in line with Section 7.1.2.3 or Section 7.1.2.5 of the Baseline Requirements, the responder MUST NOT respond with a "good" status for such requests.

### 4.9.10 On-line revocation checking requirements

No stipulation

### 4.9.11 Other forms of revocation advertisements available

Because some Application Software Suppliers utilize non‐standard revocation mechanisms, SSL.com SHALL, if requested by the Application Software Supplier and using a method of communication specified by the Application Software Vendor, notify the Application Software Supplier whenever SSL.com revokes a Code Signing Certificate because

1. the CA mis‐issued the Certificate,
2. the Certificate was used to sign Suspect Code, or
3. there is a suspected or actual compromise of the Applicant’s or CA’s Private Key.

### 4.9.12 Special requirements regarding key compromise

Third parties must use the Certificate Problem report process, as described in §3.4.2 and may follow at least one of the following methods to demonstrate that a Private Key is indeed Compromised:

1. Submission of the private key itself;

2. Submission of a signed CSR with a Common Name indicating that the key is compromised e.g. "This key is compromised". This CSR can be generated using the following OpenSSL command:

```sh
openssl req -new -key privkey.pem -subj "/CN=This key is compromised/" -out proofofcompromise.csr
```

3. Submission of signed data indicating that the key is compromised e.g. "This key is compromised" by following the instructions at [Proving Possession of a Private Key](<https://www.ssl.com/how-to/proving-possession-of-a-private-key/#ftoc-heading-1>).

### 4.9.13 Circumstances for suspension

The SSL.com PKI does not support Certificate suspension.

### 4.9.14 Who can request suspension

No entity is permitted to request suspension of any Certificate issued utilizing the SSL.com PKI.

### 4.9.15 Procedure for suspension request

Certificate suspension is not provided.

### 4.9.16 Limits on suspension period

Certificate suspension is not provided.

## 4.10 Certificate status services

SSL.com shall maintain services to provide certificate status information for any certificate issued by the SSL.com PKI.

### 4.10.1 Operational characteristics

CRLs SHALL be available via a publicly-accessible HTTP URL (i.e., "published").

If SSL.com provides OCSP responses for Code Signing, EV Code Signing, Document Signing and Timestamp Certificates, then it shall provide them beyond expiry of such a Certificate which MAY be at least ten (10) years after the expiration of the certificate. Application Software Suppliers MAY request SSL.com to support a longer life-time according to their trust store requirements.

If a Code Signing Certificate contains the Lifetime Signing OID, the digital signature becomes invalid when the Code Signing Certificate expires, even if the digital signature is timestamped.

SSL.com CAs shall include URLs to revocation information within any issued Certificate in `CRL Distribution Points` (where applicable) and `Authority Information Access` extensions.

### 4.10.2 Service availability

SSL.com shall operate and maintain its CRL and optional OCSP capability with resources sufficient to provide a response time of ten (10) seconds or less under normal operating conditions.

SSL.com shall maintain an online 24x7 Repository that application software can use to automatically check the current status of all unexpired Certificates issued by SSL.com.

SSL.com shall maintain a continuous 24x7 ability to respond internally to a high-priority Certificate Problem Report, and where appropriate, forward such a complaint to law enforcement authorities, and/or revoke any Certificate which is the subject of such a complaint.

### 4.10.3 Optional features

No stipulation

## 4.11 End of subscription

Subscribers have two options in terms of ending a certificate subscription. A certificate subscription is deemed to end when the certificate:

1. is revoked prior to the date found in the `validTo` field, or
2. reaches the `validTo` date and expires.

Either of these options shall result in the termination of subscription.
SSL.com, or the appropriate Authorized Third Party or Enterprise RA, shall notify a Subscriber of the need for renewal prior to the expiration of any certificate issued via the SSL.com PKI. Notifications can be configured through the Subscriber's SSL.com Account.

## 4.12 Key escrow and recovery

The SSL.com PKI does not support key escrow.

### 4.12.1 Key escrow and recovery policy and practices

The SSL.com PKI does not support key escrow.

### 4.12.2 Session key encapsulation and recovery policy and practices

The SSL.com PKI does not support key escrow.