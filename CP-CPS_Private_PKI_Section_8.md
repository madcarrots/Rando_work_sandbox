# 8 COMPLIANCE AUDIT AND OTHER ASSESSMENTS

SSL.com's operations and practices meet or exceed generally accepted industry standards (including the requirements described in §8.4). This is ensured by the implementation of regularly scheduled external assessments and audits, as well as ongoing internal assessments and audits.

## 8.1 Frequency or circumstances of assessment

SSL.com is audited on an annual basis in order to ensure compliance with the standards identified in this section. Audits are performed by a Qualified Auditor and cover all SSL.com activities.

## 8.2 Identity/qualifications of assessor

Any external audit shall be performed by a Qualified Auditor who can demonstrate the following:

- Independence from the subject of the audit
- The ability to conduct an audit that addresses the criteria specified in an eligible audit scheme as stipulated in §8.4
- The employment of individuals proficient in the examination of Public Key Infrastructure technology, information security tools and techniques, information technology and security auditing, and the third-party attestation function
- Status as certified, accredited, licensed, or otherwise meeting the qualification requirements of auditors under the audit scheme
- Adherence to applicable laws, government regulation, and professional code of ethics
- Maintains Professional Liability/Errors & Omissions insurance with a minimum of one million ($1,000,000) US dollars in coverage.

## 8.3 Assessor's relationship to assessed entity

Any external auditor shall be independent from any relationships that might constitute a conflict of interest, or that could in any way impair the external auditor's objective assessment.

## 8.4 Topics covered by assessment

### 8.4.1 CA assessment

SSL.com shall undergo a conformity assessment audit for compliance with the following requirements:

- CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted TLS Server Certificates
- CA/Browser Forum Guidelines for the Issuance and Management of Extended Validation Certificates
- CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted Code Signing Certificates
- CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted S/MIME Certificates
- CA/Browser Forum Network and Certificate System Security Requirements
- BIMI Group Minimum Security Requirements for Issuance of Mark Certificates

in accordance with the latest applicable versions of the following schemes:

- WebTrust Principles and Criteria for Certification Authorities
- WebTrust Principles and Criteria for Certification Authorities - SSL Baseline
- WebTrust Principles and Criteria for Certification Authorities - Network Security
- WebTrust Principles and Criteria for Certification Authorities - Extended Validation SSL
- WebTrust Principles and Criteria for Certification Authorities - Code Signing Baseline Requirements
- WebTrust Principles and Criteria for Certification Authorities - S/MIME Certificates
- WebTrust Principles and Criteria for Certification Authorities - Mark Certificates

Relevant aspects of SSL.com's operations undergo regularly scheduled external audits which adhere to all of the industry standards listed in chapter 8. These audits are conducted by a Qualified Auditor, as specified in §8.2.

Internal audits and assessments, as described in §8.7, shall address all aspects of SSL.com's operations as required to ensure integrity and security.

Audits MUST be conducted for all obligations under this CP/CPS, including the operations of Timestamp Authorities and Signing Services.

For Delegated Third Parties which are not Enterprise RAs, SSL.com SHALL obtain an audit report, issued under the auditing standards that underlie the accepted audit schemes found in this §8.4, which provides an opinion whether the Delegated Third Party’s performance complies with either the Delegated Third Party’s practice statement or SSL.com's CP/CPS.

If the opinion is that the Delegated Third Party does NOT comply with the above requirements, then SSL.com SHALL NOT allow the Delegated Third Party to continue performing delegated functions.

The audit period for any Delegated Third Party SHALL NOT exceed one year (ideally aligned with SSL.com's audit).

For Enterprise RAs participating in the validation of S/MIME Certificates:

- An annual audit that meets the criteria specified in §8.4 SHALL apply, or
- SSL.com SHALL ensure the practices and procedures of delegated parties are in compliance with S/MIME Baseline Requirements and the relevant CP and/or CPS, including the SSL.com CP/CPS. SSL.com SHALL document the obligations of delegated parties and perform monitoring on at least an annual basis of the delegated parties’ adherence with those obligations.

### 8.4.2 Signing Service assessment

For Audit Periods starting after June 30, 2024, the Signing Service MUST undergo a conformity assessment audit for compliance with the "CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted Code Signing Certificates" performed in accordance with one of the following schemes:

1. “WebTrust for Certification Authorities - Code Signing Baseline Requirements v2.0 or newer” AND “WebTrust for Certification Authorities - Network Security - Version 1.0 or newer”; or
2. ETSI EN 319 411-1, which includes normative references to ETSI EN 319 401 (the latest version of the referenced ETSI documents should be applied).

Whichever scheme is chosen, it MUST incorporate periodic monitoring and/or accountability procedures to ensure that its audits continue to be conducted in accordance with the requirements of the scheme.

The audit MUST be conducted by a Qualified Auditor, as specified in §8.2.

### 8.4.3 Timestamp Authority assessment

The Timestamp Authority MUST undergo a conformity assessment audit for compliance with the "CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted Code Signing Certificates" performed in accordance with one of the following schemes:

1. “WebTrust for Certification Authorities - Code Signing Baseline Requirements v2.0 or newer” AND “WebTrust for Certification Authorities - Network Security - Version 1.0 or newer”; or
2. ETSI EN 319 411-1, which includes normative references to ETSI EN 319 401 (the latest version of the referenced ETSI documents should be applied).

Whichever scheme is chosen, it MUST incorporate periodic monitoring and/or accountability procedures to ensure that its audits continue to be conducted in accordance with the requirements of the scheme.

The audit MUST be conducted by a Qualified Auditor, as specified in §8.2.

## 8.5 Actions taken as a result of deficiency

SSL.com shall create and implement an appropriate action plan to correct any deficiency deemed to constitute material non-compliance with applicable law, the SSL.com CP/CPS, or any standard listed in §8.4.

Any corrective action plan shall be submitted to SSL.com management. Any plan which affects SSL.com policy shall also be referred to the SSL.com Policy Management Authority (PMA). Any plan shall also be communicated to any appropriate party legally obligated to be notified. Any corrective actions deemed necessary shall be implemented and documented. Corrective actions which result in changes to SSL.com policies or procedures shall be documented and incorporated into any subsequent SSL.com PKI CP/CPS.

## 8.6 Communication of results

Audit results are communicated to SSL.com management, the SSL.com PMA and to any third party entities entitled or required to be notified of audit results by law, regulation, or agreement.
Audit compliance will be communicated to other interested parties (such as Application Service Suppliers and browser vendors) as appropriate.
SSL.com makes letters showing compliance with annual external Audit Reports publicly available in the legal Repository (<https://www.ssl.com/repository>).

## 8.7 Self-Audits

SSL.com performs regular internal audits (on at least a quarterly basis) drawing upon populations of Certificates issued since the last internal audit. These audits MUST be drawn against randomly selected samples of each of the following populations:

- DV TLS Certificates;
- OV TLS Certificates;
- EV TLS Certificates;
- Code Signing Certificates;
- S/MIME Certificates;
- Document Signing Certificates; and
- Mark Certificates.

For each population, samples will consist of at least the greater of one (1) certificate or three percent (3%) of issued Certificates.

For EV TLS Certificates or for Code Signing Certificates where the Final Cross‐Correlation and Due Diligence requirements of Section 3.2.2.13 of the EV Guidelines or Section 3.2.9 of the Code Signing Baseline Requirements respectively, is performed by a Delegated Third Party RA, SSL.com MUST strictly control its service quality by performing ongoing self audits against a randomly selected sample of at least six percent (6%) of the EV TLS or Code Signing Certificates it has issued in the period beginning immediately after the last sample was taken.

**Effective 2025-03-15**, SSL.com SHOULD use a Linting process to verify the technical accuracy of Certificates within the selected sample set independently of previous linting performed on the same Certificates.

Self-audits are performed in accordance with applicable CA/B Forum Guidelines.

SSL.com shall perform an annual self-assessment evaluating the conformance of this CP/CPS against CA/B Forum Baseline Requirements and the applicable Root Program Policies.

Completed self-assessments shall be submitted to the CCADB within 92 days from the “BR Audit Period End Date” field specified in the root CA’s “CA Owner/Certificate” CCADB record (i.e. End Date of the Audit Period). If a self-assessment covers multiple CAs operating under this CP/CPS, SSL.com shall enumerate the CAs in the scope of the assessment on the provided cover sheet.