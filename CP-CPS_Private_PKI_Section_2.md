# 2 SSL.com DOCUMENTS AND REPOSITORY

## 2.1 Repositories

SSL.com maintains a central Repository to allow access to documents related to SSL.com's policies and practices, including this CP/CPS, Subscriber and Relying Party agreements and root Certificates.
SSL.com's central Repository is available at <https://www.ssl.com/repository>.

SSL.com's central Repository is maintained with resources sufficient to provide a commercially reasonable response time for access at all times. Distributed repositories that include at least the same type of information as the central repository may also exist.

## 2.2 Publication of certification information

CRL distribution points are included in intermediate and end-entity Certificates. CRLs and OCSP services are publicly available online.

### 2.2.1 SSL.com PKI CP/CPS

The SSL.com CP/CPS shall always be publicly accessible in the SSL.com Repository.

### 2.2.2 Certificate Revocation List and On-line Certificate Status Protocol

SSL.com maintains Certificate Revocation Lists (CRLs) and Online Certificate Status Protocol (OCSP) responders as public resources which provide Relying Parties with pertinent information regarding the validity or current status of an SSL.com certificate.  CRL distribution points are included in intermediate and end-entity Certificates. CRLs and OCSP services are publicly available online.

#### 2.2.2.1 CRLs

CRLs maintained by SSL.com contain lists of serial numbers for all revoked, un-expired Certificates issued by SSL.com. These lists adhere to the standards set out in RFC 5280 for X.509 Certificate Revocation Lists. SSL.com maintains CRLs as described in Sections §4.9.7, §4.9.8 and §4.10 of this CP/CPS.

#### 2.2.2.2 OCSP

OCSP is part of SSL.com's Repository and documents all relevant status information for each certificate issued by SSL.com. This status information is presented by SSL.com's OCSP responding server(s) (also known as the OCSP responder). This resource adheres to the standards set out in RFC 6960. See also Sections §4.9.9, §4.9.10 and §4.10 of this CP/CPS.

### 2.2.3 SSL.com Certificate Subscriber Agreement

A copy of the latest SSL.com Certificate Subscriber Agreement is available in the SSL.com repository <https://www.ssl.com/repository/Subscriber-agreement>.

### 2.2.4 SSL.com Relying Party Agreement and Warranty

A copy of the latest SSL.com Certificate Relying Party Agreement and SSL.com Relying Party Warranty are available in the SSL.com repository at <https://www.ssl.com/relying-party-agreement> and <https://www.ssl.com/relying-party-warranty>, respectively.

### 2.2.5 SSL.com Root and Intermediate Certificates

All Root and Intermediate CA Certificates utilized by the SSL.com PKI are available in the SSL.com Repository listed in §2.1.

### 2.2.6 Audit Reports

Copies of auditor report letters, including those confirming Extended Validation (EV) certification and other relevant statuses, are available in the SSL.com Repository listed in §2.1.

### 2.2.7 Additional resources related to SSL.com EV Certificates

The SSL.com Repository contains copies of all documents required by Applicants to request an SSL.com Extended Validation (EV) certificate for SSL or Code Signing usage. These include downloadable .pdf versions of:

- EV Certificate Subscriber Agreement
- Sample EV CPA Letter
- Sample EV Legal Opinion

### 2.2.8 Disclosure of Verification Sources

The SSL.com Repository contains agency information about the Incorporating Agency or Registration Agency used to validate EV Certificates

This agency information SHALL include at least the following:

- Sufficient information to unambiguously identify the Incorporating Agency or Registration Agency (such as a name, jurisdiction, and website); and,
- The accepted value or values for each of the `subject:jurisdictionLocalityName` (OID: `1.3.6.1.4.1.311.60.2.1.1`), `subject:jurisdictionStateOrProvinceName` (OID: `1.3.6.1.4.1.311.60.2.1.2`), and `subject:jursidictionCountryName` (OID: `1.3.6.1.4.1.311.60.2.1.3`) fields, when a certificate is issued using information from that Incorporating Agency or Registration Agency, indicating the jurisdiction(s) that the Agency is appropriate for; and,
- The acceptable form or syntax of Registration Numbers used by the Incorporating Agency or Registration Agency, if SSL.com restricts such Numbers to an acceptable form or syntax; and,
- A revision history that includes a unique version number and date of publication for any additions, modifications, and/or removals from this list.

### 2.2.9 Other SSL.com Legal Documents

The SSL.com repository contains copies of the following SSL.com legal documents:

- Terms of Service
- Privacy Policy

### 2.2.10 Documents not included in the SSL.com Repository

SSL.com does not make publicly available documents or elements of documents deemed as internal, which include security controls, internal security polices, etc. However, these documents are fully disclosed in audits associated with any formal accreditation process that SSL.com adheres to.

## 2.3. Time or Frequency of Publication

### 2.3.1 Frequency of Publication of Certificates

Certificate information is published immediately upon acceptance by the Subscriber or when a Certificate is revoked. More information is available in §4.4.2.

### 2.3.2 Frequency of Publication of CRLs

Frequency of CRL updating and publication is described in §4.9.7

### 2.3.3 Frequency of Publication of CP/CPS, Terms & Conditions

The SSL.com CP/CPS will be revised and/or amended, and the updated document published, as described in §1.5.4.

### 2.3.4 Notification of major changes

Major changes to any documents, agreements and resources will be clearly noted in the relevant item when published. SSL.com reserves the right to make minor changes to any item in the Repository if such changes do not substantially affect or modify SSL.com PKI operations, practices and policies. More information is available in §9.12.3.

## 2.4 Access Controls on Repositories

All online repositories described in §2.2 are publicly and anonymously available on the Internet with read-only access. Only authorized entities within SSL.com have rights to perform modification to documents in these repositories.
Restrictions and access-controls are applied to public repositories for protection against enumeration and Denial of Service attacks.

Any participant in the SSL.com PKI (including Applicants, Subscribers and Relying Parties) shall have unlimited read-only access to any item in the SSL.com Repository.

Any participant in the SSL.com PKI accessing the SSL.com Repository and/or other SSL.com directory resources are deemed to have agreed with the provisions of the SSL.com CP/CPS and to any other conditions of usage that SSL.com makes available.
