# 3 NAMING, IDENTIFICATION AND AUTHENTICATION

## 3.1 Naming

### 3.1.1 Type of names

All SSL.com Certificates adhere to rules for naming and identification, and (except as specifically detailed in the profile for that certificate type) shall require a Distinguished Name that is in compliance with the ITU X.500 standard for Distinguished Names (DN). Names shall be interpreted using the X.500 and RFC822 standards.

For S/MIME Certificates:

- When the `subject:commonName` of a Certificate issued to an Individual does not contain a Mailbox Address, it is specified as a Personal Name or Pseudonym as described in §7.1.4.2.2(a).
- Names consisting of multiple words are permitted. Given names joined with a hyphen are considered as one single given name. Subjects with more than one given name MAY choose one or several of their given names in any sequence. Subjects MAY choose the order of their given name(s) and surname in accordance with national preference.
- SSL.com MAY allow common variations or abbreviations of Personal Names consistent with local practice.

### 3.1.2 Need for names to be meaningful, unambiguous and unique

For S/MIME Certificates, Personal Names SHALL be a meaningful representation of the Subject's name as verified in the identifying documentation or Enterprise RA records.

### 3.1.3 Anonymous, pseudonymous and role-based Certificates

The purpose of a Pseudonym is to provide a unique identifier linked to an Individual in a pseudonymized manner when certain privacy conditions are required. For example, a Pseudonym may be used if a government agency requires officials to sign certain decisions via S/MIME so those decisions trace back to individuals, but emphasize the importance of the role over Individual identity in the Certificate.

SSL.com SHALL NOT allow Certificates to be issued with anonymous or pseudonymous Subscriber information. However, for IDNs, SSL.com MAY include the Punycode version of the IDN as a Subject Name.

SSL.com MAY allow Certificates to include role-based Subscriber information. This information SHALL be verified, validated, and SHALL be submitted along with other verified Subscriber information included in the Subject Identity Information field.

### 3.1.4 Rules for interpreting various name forms

SSL.com Certificates shall be issued with Distinguished Names interpreted using X.500 standards and ASN.1 syntax.

### 3.1.5 Uniqueness of names

The full combination of the Subject Attributes (Distinguished name) has to be unique in SSL.com's PKI. Depending on the type of certificate (SSL, S/MIME, Code Signing), different elements/attributes of the certificate ensure uniqueness.

### 3.1.6 Recognition, authentication, and role of trademarks

Applicants agree by submitting a certificate request to SSL.com that their request does not contain data which in any way interferes with or infringes upon the rights of any third parties in any jurisdiction with respect to trademarks, service marks, trade names, company names, "doing business as" (DBA) names, or any other intellectual property right, and that they are not presenting the data for any unlawful purpose whatsoever. Data covered by this agreement includes but is not limited to any domain name, domain name space, Distinguished Name (DN), or Fully-Qualified Domain Name (FQDN), and/or any trade name or DBA name, contained in any portion of the certificate request.

If the certificate is to include a DBA, a Mark or trade name in any field whatsoever, SSL.com shall verify the Applicant's right to use the DBA, Mark or trade name using the steps detailed in §4.2.

Applicants requesting SSL.com Certificates shall be responsible for the legality of the information they present for verification and/or use in Certificates for any jurisdiction in which such content may be used or viewed.

Any certificate issued using information which is deemed to violate §3.1.6 may be revoked by SSL.com.

Subscribers shall defend, indemnify, and hold SSL.com harmless for any loss or damage resulting from any interference or infringement upon the rights of third parties and shall be responsible for defending all actions against SSL.com.

## 3.2 Initial identity validation

A valid certificate request SHALL establish possession of the Private Key related to the request.

All requests for Certificates sent to SSL.com SHALL be verified at the level of assurance appropriate to the certificate requested. SSL.com issues different types of digital Certificates (including SSL, Code Signing, personal authentication, Mark and S/MIME Certificates) with varying and appropriate levels of verification including "Extended Validation" (EV).

SSL.com SHALL inspect any document relied upon for verification for alteration or falsification. SSL.com SHALL verify the identity and status of any Applicant as appropriate and required for the certificate requested. Alteration or falsification of any document used in this process, and/or falsification or misrepresentation of the identity or status of any Applicant and/or organization referenced in this process, SHALL constitute grounds for disapproval of a certificate request and/or immediate revocation of any existing certificate relying upon altered or falsified documents or false or misrepresented identity or status.

All information that is supplied by the Applicant SHALL be verified by using an independent source of information or an alternative communication channel before it is included in a Certificate.

For EV Certificates, SSL.com takes all verification steps reasonably necessary to satisfy the EV Verification Requirements set forth in the EV Guidelines.

### 3.2.1 Method to prove possession of Private Key

Any Applicant for any SSL.com certificate must submit a Certificate Signing Request (CSR). This establishes that the Applicant holds the Private Key corresponding to the Public Key to be included in the requested certificate.

This requirement does not apply when a Key Pair is generated by SSL.com on behalf of a Subscriber (e.g. for Document Signing, Code Signing and EV Code Signing Applicants). In these cases SSL.com shall ensure control of Key Pairs as described in 6.2.1.

### 3.2.2 Authentication of organization and domain identity

Requests for Certificates which include an organization identity shall be verified using the criteria described below. Items to be verified include the legal existence, legal name, assumed name, legal form, jurisdiction of incorporation or registration of the legal entity, identifier and type of identifier of the legal entity, requested address of the legal entity, and the authority of the requesting party, as applicable. SSL.com shall inspect any document relied upon for these purposes for alteration or falsification.

If the Applicant requests a TLS Certificate that will contain Subject Identity Information comprised only of the countryName field, then SSL.com SHALL verify the country associated with the Subject using a verification process meeting the requirements of §3.2.2.3 of this CP/CPS. If the Applicant requests a TLS Certificate that will contain the countryName field and other Subject Identity Information, then SSL.com SHALL verify the identity of the Applicant, and the authenticity of the Applicant Representative’s certificate request using a verification process meeting the requirements of §3.2.2.1 of this CP/CPS.

Verification of organization identity in any request for an Extended Validation Certificate shall follow the EV verification procedures described in the EV Guidelines. In particular, before issuing an EV Certificate, SSL.com SHALL ensure that all Subject organization information to be included in the EV Certificate conforms to the requirements of, and is verified in accordance with, EV Guidelines and matches the information confirmed and documented by SSL.com pursuant to its verification processes. Extended validation processes SHALL verify the following:

1. The Applicant’s existence and identity, including;
    a. The Applicant’s legal existence and identity, as per Section 3.2.2.2 of the EV Guidelines,
    b. The Applicant’s physical existence (business presence at a physical address), as per Section 3.2.2.4 of the EV Guidelines,
    c. The Applicant’s operational existence (business activity), as per Section 3.2.2.6 of the EV Guidelines, and
    d. The Applicant's assumed name, as per Section 3.2.2.3 of the EV Guidelines (if applicable).
2. That the Applicant is a registered holder, or has control, of the Domain Name(s) to be included in the EV Certificate, as per Section 3.2.2.7 of the EV Guidelines;
3. A Verified Method of Communication with the entity to be named as the Subject in the Certificate, as per Section 3.2.2.5 of the EV Guidelines;
4. The Applicant’s authorization for the EV Certificate, including;
    a. The name, title, and authority of the Contract Signer, Certificate Approver, and Certificate Requester, as per Section 3.2.2.8 of the EV Guidelines,
    b. That a Contract Signer signed the Subscriber Agreement or that a duly authorized Applicant Representative acknowledged and agreed to the Terms of Use, as per Section 3.2.2.9 of the EV Guidelines; and
    c. That a Certificate Approver has signed or otherwise approved the EV Certificate Request, as per Section 3.2.2.10 of the EV Guidelines.

When performing the above, SSL.com MAY take additional verification steps that MAY be reasonably necessary under the circumstances to satisfy the applicable Verification Requirement. Whenever the use of documentation obtained by an Incorporating Agency or Registration Agency is required in this process, SSL.com SHALL only use agencies included in its approved, at time of issuance, List of Approved Incorporating and Registration Agencies. This list is publicly available at <https://www.ssl.com/repository> (see §2.2.8).

#### 3.2.2.1 Identity

If the Subject Identity Information is to include the name or address of an organization, SSL.com shall verify the identity and address of the Applicant. This verification shall use documentation provided by, or through communication with, at least one of the following:

1. A government agency or Incorporating Agency or Registration Agency in the jurisdiction of the Applicant's legal creation, existence, or recognition;
2. A third party database that is periodically updated and considered a Reliable Data Source as defined in §3.2.2.7;
3. A site visit by SSL.com or a third party who is acting as an agent for SSL.com; or
4. An Attestation Letter, as defined in §1.6.1

SSL.com may use the same documentation or communication described in 1) through 4) above to verify both the Applicant's identity and address.

Alternatively, SSL.com may verify the address of the Applicant (but not the identity of the Applicant) using a utility bill, bank statement, credit card statement, government-issued tax document, or other form of identification that SSL.com determines to be reliable.

#### 3.2.2.2 DBA/Trade Name

If the Subject Identity Information is to include a DBA or trade name, SSL.com shall verify the Applicant's right to use the DBA/trade name with at least one of the following criteria:

1. Documentation provided by, or communication with, government agency or Incorporating Agency or Registration Agency in the jurisdiction of the Applicant's legal creation, existence, or recognition;
2. A Reliable Data Source as defined in §3.2.2.7;
3. Communication with a government agency responsible for the management of such DBAs or trade names;
4. An Attestation Letter accompanied by verifying practitioner credentials; or
5. A utility bill, bank statement, credit card statement, government-issued tax document, or other form of identification that SSL.com determines to be reliable.

Use of a DBA or trade name is governed by and further described in §3.1.6.

#### 3.2.2.3 Verification of Country

If the `subject:countryName` field is present, then SSL.com shall verify the country associated with the Subject using one of the following:

1. The IP Address range assignment by country for either
    a. The web site's IP address, as indicated by the DNS record for the web site, or
    b. The Applicant's IP address;
2. The ccTLD of the requested Domain Name;
3. Information provided by the Domain Name Registrar; or
4. A method identified in §3.2.2.1.

#### 3.2.2.4 Validation of Domain Authorization or Control

This Section defines the permitted processes and procedures for validating the Applicant's ownership or control of the domain.

SSL.com shall confirm that, prior to the date of Certificate issuance, SSL.com has validated each Fully-Qualified Domain Name (FQDN) listed in the Certificate using at least one of the methods listed below.

SSL.com shall confirm that prior to issuance, SSL.com has validated each Fully-Qualified Domain Name (FQDN) listed in the Certificate as follows:

1. When the FQDN is not an Onion Domain Name, SSL.com SHALL validate the FQDN using at least one of the methods listed below; and
2. When the FQDN is an Onion Domain Name, SSL.com SHALL validate the FQDN in accordance with Appendix B of the "Baseline Requirements for the Issuance and Management of Publicly-Trusted TLS Server Certificates" document.

Completed confirmations of Applicant authority may be valid for the issuance of multiple certificates over time. In all cases, the confirmation must have been initiated within the time period specified in the relevant requirement (such as §4.2.1 of this document) prior to certificate issuance. For purposes of domain validation, the term Applicant includes the Applicant's Parent Company, Subsidiary Company, or Affiliate.

Effective March 15th, 2026: DNSSEC validation back to the IANA DNSSEC root trust anchor MUST be performed on all DNS queries associated with the validation of domain authorization or control by the Primary Network Perspective. The DNS resolver used for all DNS queries associated with the validation of domain authorization or control by the Primary Network Perspective MUST:

* perform DNSSEC validation using the algorithm defined in RFC 4035 Section 5; and
* support NSEC3 as defined in RFC 5155; and 
* support SHA-2 as defined in RFC 4509 and RFC 5702; and
* properly handle the security concerns enumerated in RFC 6840 Section 4.

Effective March 15th, 2026: SSL.com MUST NOT use local policy to disable DNSSEC validation on any DNS query associated with the validation of domain authorization or control.

DNSSEC validation back to the IANA DNSSEC root trust anchor MAY be performed on all DNS queries associated with the validation of domain authorization or control by Remote Network Perspectives used for Multi-Perspective Issuance Corroboration.

DNSSEC validation back to the IANA DNSSEC root trust anchor is considered outside the scope of self-audits performed to fulfill the requirements in §8.7.

SSL.com shall maintain a record of which domain validation method was used to validate each domain, including the relevant Baseline Requirements version number applicable.

**Note:** FQDNs may be listed in Subscriber Certificates using dNSNames in the subjectAltName extension or in Subordinate CA Certificates via dNSNames in permittedSubtrees within the Name Constraints extension.

##### 3.2.2.4.1 Validating the Applicant as a Domain Contact

This method has been retired and MUST NOT be used.

##### 3.2.2.4.2 Email, Fax, SMS, or Postal Mail to Domain Contact

This method has been retired and MUST NOT be used. Prior validations using this method and validation data gathered according to this method SHALL NOT be used to issue certificates.

##### 3.2.2.4.3 Phone Contact with Domain Contact

This method has been retired and MUST NOT be used. Prior validations using this method and validation data gathered according to this method SHALL NOT be used to issue certificates.

##### 3.2.2.4.4 Constructed Email to Domain Contact

SSL.com shall confirm the Applicant's control over the FQDN by (i) sending an email to one or more addresses created by using 'admin', 'administrator', 'webmaster', 'hostmaster', or 'postmaster' as the local part, followed by the at-sign ("@"), followed by an Authorization Domain Name, (ii) including a Random Value in the email, and (iii) receiving a confirming response utilizing the Random Value.

**Note:** Once the FQDN has been validated using this method, SSL.com MAY also, at its discretion, issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN. This method is suitable for validating Wildcard Domain Names.

Each email MAY confirm control of multiple FQDNs, provided the Authorization Domain Name used in the email is an Authorization Domain Name for each FQDN being confirmed.

The Random Value SHALL be unique in each email.

The email MAY be re-sent in its entirety, including the re-use of the Random Value, provided that its entire contents and recipient SHALL remain unchanged.

The Random Value SHALL remain valid for use in a confirming response for no more than 30 days from its creation.

Effective March 15, 2028:
- SSL.com MUST NOT rely on this method.
- Prior validations using this method and validation data gathered according to this method MUST NOT be used to issue Subscriber Certificates.

##### 3.2.2.4.5 Domain Authorization Document

This method has been retired and MUST NOT be used. Prior validations using this method and validation data gathered according to this method SHALL NOT be used to issue certificates.

##### 3.2.2.4.6 Agreed-Upon Change to Website

This method has been retired and MUST NOT be used. Prior validations using this method and validation data gathered according to this method SHALL NOT be used to issue certificates.

##### 3.2.2.4.7 DNS Change

SSL.com shall confirm the Applicant's control over the FQDN by confirming the presence of a Random Value or Request Token in a DNS CNAME, TXT or CAA record for either

1. an Authorization Domain Name; or
2. an Authorization Domain Name that is prefixed with a Domain Label that begins with an underscore character.

If a Random Value is used, SSL.com SHALL provide a Random Value unique to the certificate request and SHALL not use the Random Value after

1. 30 days; or
2. if the Applicant submitted the certificate request, the time frame permitted for reuse of validated information relevant to the certificate (such as in §4.2.1 of this CP/CPS or Section 3.2.2.14.3 of the CA/Browser Forum EV Guidelines).

Any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same challenge information (i.e. Random Value or Request Token) as the Primary Network Perspective.

**Note:** Once the FQDN has been validated using this method, SSL.com MAY also, at its discretion, issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN. This method is suitable for validating Wildcard Domain Names.

##### 3.2.2.4.8 IP Address

SSL.com shall confirm the Applicant's control over the  FQDN by confirming that the Applicant controls an IP address returned from a DNS lookup for A or AAAA records for the FQDN in accordance with Section 3.2.2.5.

Any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same IP address as the Primary Network Perspective.

**Note:** Once the FQDN has been validated using this method, SSL.com SHALL NOT also issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN, unless SSL.com performs separate validations for each of those other FQDNs using authorized methods. This method is NOT suitable for validating Wildcard Domain Names.

Effective March 15, 2026:
- SSL.com MUST NOT rely on this method.
- Prior validations using this method and validation data gathered according to this method MUST NOT be used to issue Subscriber Certificates.

##### 3.2.2.4.9 Test Certificate

This method has been retired and MUST NOT be used.

##### 3.2.2.4.10. TLS Using a Random Value

This method has been retired and MUST NOT be used.

##### 3.2.2.4.11 Any Other Method

This method has been retired and MUST NOT be used.

##### 3.2.2.4.12 Validating Applicant as a Domain Contact

SSL.com does not use this method.

##### 3.2.2.4.13 Email to DNS CAA Contact

Confirming the Applicant's control over the FQDN by sending a Random Value via email and then receiving a confirming response utilizing the Random Value. The Random Value MUST be sent to a DNS CAA Email Contact. The relevant CAA Resource Record Set MUST be found using the search algorithm defined in RFC 8659, Section 3.

Each email MAY confirm control of multiple FQDNs, provided that each email address is a DNS CAA Email Contact for each Authorization Domain Name being validated. The same email MAY be sent to multiple recipients as long as all recipients are DNS CAA Email Contacts for each Authorization Domain Name being validated.

The Random Value SHALL be unique in each email. The email MAY be re-sent in its entirety, including the re-use of the Random Value, provided that its entire contents and recipient(s) SHALL remain unchanged. The Random Value SHALL remain valid for use in a confirming response for no more than 30 days from its creation. The CPS MAY specify a shorter validity period for Random Values.

Any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same selected contact address used for domain validation as the Primary Network Perspective.

**Note**: Once the FQDN has been validated using this method, SSL.com MAY also issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN. This method is suitable for validating Wildcard Domain Names.

Effective March 15, 2028:
- SSL.com MUST NOT rely on this method.
- Prior validations using this method and validation data gathered according to this method MUST NOT be used to issue Subscriber Certificates.

##### 3.2.2.4.14 Email to DNS TXT Contact

SSL.com SHALL confirm the Applicant's control over the FQDN by sending a Random Value via email and then receiving a confirming response utilizing the Random Value. The Random Value MUST be sent to a DNS TXT Record Email Contact for the Authorization Domain Name selected to validate the FQDN.

Each email MAY confirm control of multiple FQDNs, provided that each email address is a DNS TXT Record Email Contact for each Authorization Domain Name being validated. The same email MAY be sent to multiple recipients as long as all recipients are DNS TXT Record Email Contacts for each Authorization Domain Name being validated.

The Random Value SHALL be unique in each email. The email MAY be re-sent in its entirety, including the re-use of the Random Value, provided that its entire contents and recipient(s) SHALL remain unchanged. The Random Value SHALL remain valid for use in a confirming response for no more than 30 days from its creation.

Any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same selected contact address used for domain validation as the Primary Network Perspective.

**Note:** Once the FQDN has been validated using this method, SSL.com MAY also issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN. This method is suitable for validating Wildcard Domain Names.

Effective March 15, 2028:
- SSL.com MUST NOT rely on this method.
- Prior validations using this method and validation data gathered according to this method MUST NOT be used to issue Subscriber Certificates.

##### 3.2.2.4.15 Phone Contact with Domain Contact

This method has been retired and MUST NOT be used. Prior validations using this method and validation data gathered according to this method SHALL NOT be used to issue certificates.

##### 3.2.2.4.16 Phone Contact with DNS TXT Record Phone Contact

SSL.com SHALL confirm the Applicant's control over the FQDN by calling the DNS TXT Record Phone Contact's phone number and obtain a confirming response to validate the Authorization Domain Name. Each phone call MAY confirm control of multiple Authorization Domain Names provided that the same DNS TXT Record Phone Contact phone number is listed for each Authorization Domain Name being verified and they provide a confirming response for each Authorization Domain Name.

This call from SSL.com MUST NOT knowingly be transferred or requested to be transferred, as this phone number has been specifically listed for the purposes of Domain Validation.

In the event of reaching voicemail, SSL.com may leave the Random Value and the Authorization Domain Name(s) being validated. The Random Value MUST be returned to SSL.com to approve the request.

The Random Value SHALL remain valid for use in a confirming response for no more than 30 days from its creation.

Any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same selected contact address used for domain validation as the Primary Network Perspective.

**Note:** Once the FQDN has been validated using this method, SSL.com MAY also issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN. This method is suitable for validating Wildcard Domain Names.

Effective March 15, 2027:
- SSL.com MUST NOT rely on this method.
- Prior validations using this method and validation data gathered according to this method MUST NOT be used to issue Subscriber Certificates.

##### 3.2.2.4.17 Phone Contact with DNS CAA Phone Contact

SSL.com SHALL Confirm the Applicant's control over the FQDN by calling the DNS CAA Phone Contact’s phone number and obtain a confirming response to validate the ADN. Each phone call MAY confirm control of multiple ADNs provided that the same DNS CAA Phone Contact phone number is listed for each ADN being verified and they provide a confirming response for each ADN. The relevant CAA Resource Record Set MUST be found using the search algorithm defined in RFC 8659 Section 3.

SSL.com MUST NOT be transferred or request to be transferred as this phone number has been specifically listed for the purposes of Domain Validation.  

In the event of reaching voicemail, SSL.com may leave the Random Value and the ADN(s) being validated.  The Random Value MUST be returned to SSL.com to approve the request.

The Random Value SHALL remain valid for use in a confirming response for no more than 30 days from its creation.

Any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same selected contact address used for domain validation as the Primary Network Perspective.

**Note:** Once the FQDN has been validated using this method, SSL.com MAY also issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN.  This method is suitable for validating Wildcard Domain Names.

Effective March 15, 2027:
- SSL.com MUST NOT rely on this method.
- Prior validations using this method and validation data gathered according to this method MUST NOT be used to issue Subscriber Certificates.

##### 3.2.2.4.18 Agreed-Upon Change to Website v2

Confirming the Applicant's control over the FQDN by verifying that the Request Token or Random Value is contained in the contents of a file.

1. The entire Request Token or Random Value MUST NOT appear in the request used to retrieve the file, and
2. SSL.com MUST receive a successful HTTP response from the request (meaning a 2xx HTTP status code must be received).

The file containing the Request Token or Random Value:

1. MUST be located on the Authorization Domain Name, and
2. MUST be located under the "/.well-known/pki-validation" directory, and
3. MUST be retrieved via either the "http" or "https" scheme, and
4. MUST be accessed over an Authorized Port.

If SSL.com follows redirects, the following apply:

1. Redirects MUST be initiated at the HTTP protocol layer.
    a. For validations performed on or after July 1, 2021, redirects MUST be the result of a 301, 302, or 307 HTTP status code response, as defined in RFC 7231, Section 6.4, or a 308 HTTP status code response, as defined in RFC 7538, Section 3. Redirects MUST be to the final value of the Location HTTP response header, as defined in RFC 7231, Section 7.1.2.
    b. For validations performed prior to July 1, 2021, redirects MUST be the result of an HTTP status code result within the 3xx Redirection class of status codes, as defined in RFC 7231, Section 6.4.
2. Redirects MUST be to resource URLs with either the "http" or "https" scheme.
3. Redirects MUST be to resource URLs accessed via Authorized Ports.

If a Random Value is used, then:

1. SSL.com MUST provide a Random Value unique to the certificate request.
2. The Random Value MUST remain valid for use in a confirming response for no more than 30 days from its creation.

Except for Onion Domain Names, any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same challenge information (i.e. Random Value or Request Token) as the Primary Network Perspective.

**Note:** SSL.com MUST NOT issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN unless it performs separate validations for each of those other FQDNs using authorized methods. This method is NOT suitable for validating Wildcard Domain Names.

##### 3.2.2.4.19 Agreed-Upon Change to Website - ACME

Confirming the Applicant's control over a FQDN by validating domain control of the FQDN using the ACME HTTP Challenge method defined in section 8.3 of RFC 8555. The following are additive requirements to RFC 8555.

SSL.com MUST receive a successful HTTP response from the request (meaning a 2xx HTTP status code must be received).

The token (as defined in RFC 8555, section 8.3) MUST NOT be used for more than 30 days from its creation.

If SSL.com follows redirects, the following apply:

1. Redirects MUST be initiated at the HTTP protocol layer.
    a. For validations performed on or after July 1, 2021, redirects MUST be the result of a 301, 302, or 307 HTTP status code response, as defined in RFC 7231, Section 6.4, or a 308 HTTP status code response, as defined in RFC 7538, Section 3. Redirects MUST be to the final value of the Location HTTP response header, as defined in RFC 7231, Section 7.1.2.
    b. For validations performed prior to July 1, 2021, redirects MUST be the result of an HTTP status code result within the 3xx Redirection class of status codes, as defined in RFC 7231, Section 6.4.
2. Redirects MUST be to resource URLs with either the "http" or "https" scheme.
3. Redirects MUST be to resource URLs accessed via Authorized Ports.

Except for Onion Domain Names, any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same challenge information (i.e. token) as the Primary Network Perspective.

**Note:** SSL.com MUST NOT issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN unless it performs separate validations for each of those other FQDNs using authorized methods. This method is NOT suitable for validating Wildcard Domain Names.

##### 3.2.2.4.20 TLS Using ALPN

SSL.com shall confirm the Applicant's control over a FQDN by validating domain control of the FQDN by negotiating a new application layer protocol using the TLS Application-Layer Protocol Negotiation (ALPN) Extension RFC 7301 as defined in RFC 8737. The following are additive requirements to RFC 8737.

The token (as defined in RFC 8737, Section 3) MUST NOT be used for more than 30 days from its creation.

Except for Onion Domain Names, any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same challenge information (i.e. token) as the Primary Network Perspective.

**Note:** SSL.com MUST NOT issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN unless it performs separate validations for each of those other FQDNs using authorized methods. This method is NOT suitable for validating Wildcard Domain Names.

##### 3.2.2.4.21 DNS Labeled with Account ID - ACME

Confirming the Applicant's control over the FQDN by performing the procedure documented for a “dns-account-01” challenge in draft 00 of “Automated Certificate Management Environment (ACME) DNS Labeled With ACME Account ID Challenge,” available at [https://datatracker.ietf.org/doc/draft-ietf-acme-dns-account-label/](https://datatracker.ietf.org/doc/draft-ietf-acme-dns-account-label/).

The token (as defined in draft 00 of “Automated Certificate Management Environment (ACME) DNS Labeled With ACME Account ID Challenge,” Section 3.1) MUST NOT be used for more than 30 days from its creation.

When performing validations using this method, SSL.com MUST implement Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same token as the Primary Network Perspective.

**Note**: Once the FQDN has been validated using this method, SSL.com MAY also issue Certificates for other FQDNs that end with all the Domain Labels of the validated FQDN. This method is suitable for validating Wildcard Domain Names.

#### 3.2.2.5 Authentication for an IP Address

SSL.com SHALL confirm that prior to issuance, SSL.com has validated the Applicant's ownership or control of each IP Address listed in a Certificate using at least one of the methods specified in this section.

Completed validations of Applicant authority may be valid for the issuance of multiple Certificates over time. In all cases, the validation must have been initiated within the time period specified in §4.2.1 prior to Certificate issuance. For purposes of IP Address validation, the term Applicant includes the Applicant's Parent Company, Subsidiary Company, or Affiliate.

After July 31, 2019, SSL.com SHALL maintain a record of which IP validation method, including the relevant BR version number, was used to validate every IP Address.

**Note:** IP Addresses verified in accordance with this §3.2.2.5 may be listed in Subscriber Certificates as defined in §7.1.4.2 or in Subordinate CA Certificates via iPAddress in permittedSubtrees within the Name Constraints extension. SSL.com is not required to verify IP Addresses listed in Subordinate CA Certificates via iPAddress in excludedSubtrees in the Name Constraints extension prior to inclusion in the Subordinate CA Certificate.

##### 3.2.2.5.1 Agreed-Upon Change to Website

SSL.com SHALL confirm the Applicant's control over the requested IP Address by confirming the presence of a Request Token or Random Value contained in the content of a file or webpage in the form of a meta tag under the "/.well-known/pki-validation" directory, or another path registered with IANA for the purpose of validating control of IP Addresses, on the IP Address that is accessible by SSL.com via HTTP/HTTPS over an Authorized Port. The Request Token or Random Value MUST NOT appear in the request.

If a Random Value is used, SSL.com SHALL provide a Random Value unique to the certificate request and SHALL not use the Random Value after the longer of (i) 30 days or (ii) if the Applicant submitted the certificate request, the time frame permitted for reuse of validated information relevant to the certificate (see §4.2.1).

Any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same challenge information (i.e. Random Value or Request Token) as the Primary Network Perspective.

##### 3.2.2.5.2 Email, Fax, SMS, or Postal Mail to IP Address Contact

SSL.com SHALL confirm the Applicant's control over the IP Address by sending a Random Value via email, fax, SMS, or postal mail and then receiving a confirming response utilizing the Random Value. The Random Value MUST be sent to an email address, fax/SMS number, or postal mail address identified as an IP Address Contact.

Each email, fax, SMS, or postal mail MAY confirm control of multiple IP Addresses.

SSL.com MAY send the email, fax, SMS, or postal mail identified under this section to more than one recipient provided that every recipient is identified by the IP Address Registration Authority as representing the IP Address Contact for every IP Address being verified using the email, fax, SMS, or postal mail.

The Random Value SHALL be unique in each email, fax, SMS, or postal mail.

SSL.com MAY resend the email, fax, SMS, or postal mail in its entirety, including re-use of the Random Value, provided that the communication's entire contents and recipient(s) remain unchanged.

The Random Value SHALL remain valid for use in a confirming response for no more than 30 days from its creation.

Effective March 15, 2027:
- SSL.com MUST NOT rely on this method.
- Prior validations using this method and validation data gathered according to this method MUST NOT be used to issue Subscriber Certificates.

##### 3.2.2.5.3 Reverse Address Lookup

SSL.com SHALL confirm the Applicant's control over the IP Address by obtaining a Domain Name associated with the IP Address through a reverse-IP lookup on the IP Address and then verifying control over the FQDN using a method permitted under §3.2.2.4.

Any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same FQDN as the Primary Network Perspective.

##### 3.2.2.5.4 Any Other Method

This method has been retired and MUST NOT be used.

##### 3.2.2.5.5 Phone Contact with IP Address Contact

SSL.com SHALL confirm the Applicant's control over the IP Address by calling the IP Address Contact's phone number and obtaining a response confirming the Applicant's request for validation of the IP Address. SSL.com MUST place the call to a phone number identified by the IP Address Registration Authority as the IP Address Contact. Each phone call SHALL be made to a single number.

In the event that someone other than an IP Address Contact is reached, SSL.com MAY request to be transferred to the IP Address Contact.

In the event of reaching voicemail, SSL.com may leave the Random Value and the IP Address(es) being validated. The Random Value MUST be returned to SSL.com to approve the request.

The Random Value SHALL remain valid for use in a confirming response for no more than 30 days from its creation.

Effective March 15, 2027:
- SSL.com MUST NOT rely on this method.
- Prior validations using this method and validation data gathered according to this method MUST NOT be used to issue Subscriber Certificates.

##### 3.2.2.5.6 ACME "http-01" method for IP Addresses

SSL.com SHALL confirm the Applicant's control over the IP Address by performing the procedure documented for an “http-01” challenge in RFC 8738.

Any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same challenge information (i.e. token) as the Primary Network Perspective.

##### 3.2.2.5.7 ACME "tls-alpn-01" method for IP Addresses

SSL.com SHALL confirm the Applicant's control over the IP Address by performing the procedure documented for a “tls-alpn-01” challenge in RFC 8738.

Any domain validations and CAA checks performed on or after 2025-03-15 using this method SHALL be based on Multi-Perspective Issuance Corroboration as specified in §3.2.2.13. To count as corroborating, a Network Perspective MUST observe the same challenge information (i.e. token) as the Primary Network Perspective.

#### 3.2.2.6 Wildcard Domain Validation

SSL.com shall follow specific practices to validate  any certificate containing a wildcard character (\*).

Before issuing a Wildcard Certificate, SSL.com shall determine if the FQDN portion of any Wildcard Domain Name in the Certificate is “registry-controlled” or is a “public suffix” (e.g. “\*.com”, “\*.co.uk”, see RFC 6454 Section 8.2 for further explanation).

If the FQDN portion of any Wildcard Domain Name is "registry-controlled" or is a "public suffix", SSL.com SHALL NOT issue a Certificate unless the Applicant proves its rightful control of the entire Domain Namespace. (e.g. SSL.com SHALL NOT issue "\*.co.uk" or "\*.local", but MAY issue "\*.example.com" to Example Co.).

In all such cases, SSL.com shall observe stipulations and considerations as given in RFC 6454 Section 8.2.

Determination of what is "registry-controlled" versus the registerable portion of a Country Code Top-Level Domain Namespace is not standardized at the time of writing and is not a property of the DNS itself. SSL.com follows the current best practice and consults the [Public Suffix List (PSL)](<https://publicsuffix.org/>), and regularly retrieves a fresh copy.

#### 3.2.2.7 Data Source Accuracy

Prior to using any data source as a Reliable Data Source, SSL.com shall evaluate the source for its reliability, accuracy, and resistance to alteration or falsification.

Criteria for this evaluation shall include:

- The age of the information provided
- The frequency of updates to the information source
- The data provider and purpose of the data collection
- The public accessibility of the data availability, and
- The relative difficulty in falsifying or altering the data.

For S/MIME Certificates, Enterprise RA records are a Reliable Data Source for Individual Subject attributes included in Sponsor-validated Certificates issued to the Enterprise RA’s Organization.

Prior to using any data source as a QIIS, SSL.com SHALL:

1. Ensure that:
    a. Industries other than the certificate industry rely on the database for accurate location, contact, or other information; and
    b. The database provider updates its data on at least an annual basis.
2. Check the accuracy of the database and ensure its data is acceptable, including reviewing the database provider’s terms of use. In particular, SSL.com SHALL NOT use any data in a QIIS that SSL.com knows is
    a. self‐reported and
    b. not verified by the QIIS as accurate.

#### 3.2.2.8 CAA Records

As part of the TLS or Mark Certificate issuance process, SSL.com MUST retrieve and process CAA records in accordance with RFC 8659 for each `dNSName` in the `subjectAltName` extension that does not contain an Onion Domain Name. These practices are described in §4.2, including specifying the set of Issuer Domain Names that SSL.com recognizes in CAA "issue" or "issuewild" records as permitting it to issue.

Some methods relied upon for validating the Applicant's ownership or control of the subject domain(s) (see §3.2.2.4) or IP address(es) (see §3.2.2.5) to be listed in a certificate require CAA records to be retrieved and processed from additional remote Network Perspectives before Certificate issuance (see §3.2.2.13). To corroborate the Primary Network Perspective, a remote Network Perspective's CAA check response MUST be interpreted as permission to issue, regardless of whether the responses from both Perspectives are byte-for-byte identical. Additionally, SSL.com MAY consider the response from a remote Network Perspective as corroborating if one or both of the Perspectives experience an acceptable CAA record lookup failure, as defined in this section.

SSL.com MAY check CAA records at any other time.

When processing CAA records for the issuance of TLS Certificates, SSL.com must process the `issue`, `issuewild`, and `iodef` property tags as specified in RFC 8659, although SSL.com is not required to act on the contents of the `iodef` property tag. Additional property tags MAY be supported, but MUST NOT conflict with or supersede the mandatory property tags set out in the Baseline Requirements. Additional property tags may be supported, but must not conflict with or supersede the mandatory property tags set out in this document. SSL.com must respect the critical flag and not issue a certificate if an unrecognized property with this flag set is encountered.

When processing CAA records for the issuance of Mark Certificates, SSL.com must process the `issuevmc` property tag as specified in RFC 8659. CAA records with `issue` or `issuewild` Property Tags do not restrict the issuance of Mark Certificates. The sub-syntax of the `issuevmc` Property Tag value is treated the same as the `issue` Property Tag as defined in section 4.2 of RFC 8659. The semantics of the `issuevmc` Property Tag are similar to the `issue` Property Tag, with the only difference being that the `issuevmc` Property Tag restricts issuance of Mark Certificates as opposed to TLS Server Authentication Certificates.

If SSL.com issues a TLS certificate after processing a CAA record, it MUST do so within the TTL of the CAA record, or 8 hours, whichever is greater.

RFC 8659 requires that a CA "MUST NOT issue a certificate unless the CA determines that either (1) the certificate request is consistent with the applicable CAA RRset or (2) an exception specified in the relevant CP or CPS applies." For issuances conforming to this CP/CPS, SSL.com must not rely on any exceptions specified in this CP/CPS unless they are one of the following:

1. CAA checking is optional for certificates for which a Certificate Transparency Precertificate (see Section 7.1.2.9 for Precertificate Profile) was created and logged in at least two public logs, and for which CAA was checked at time of Precertificate issuance.
2. CAA checking is optional for certificates issued by a Technically Constrained Subordinate CA Certificate as set out in Baseline Requirements Section 7.1.2.3 or 7.1.2.5, where the lack of CAA checking is an explicit contractual provision in the contract with the Applicant.

SSL.com is permitted to treat a record lookup failure as permission to issue if:

1. the failure is outside SSL.com's infrastructure;
2. the lookup has been retried at least once; and
3. SSL.com has confirmed that the domain is "Insecure" as defined in RFC 4035 Section 4.3.

SSL.com MUST document potential issuances that were prevented by a CAA record in sufficient detail to provide feedback to the CA/Browser Forum on the circumstances, and SHOULD dispatch reports of such issuance requests to the contact(s) stipulated in the CAA iodef record(s), if present. SSL.com is not expected to support URL schemes in the iodef record other than mailto: or https:.

##### 3.2.2.8.1 DNSSEC Validation of CAA Records

Effective March 15th, 2026: DNSSEC validation back to the IANA DNSSEC root trust anchor MUST be performed on all DNS queries associated with CAA record lookups performed by the Primary Network Perspective. The DNS resolver used for all DNS queries associated with CAA record lookups performed by the Primary Network Perspective MUST:

* perform DNSSEC validation using the algorithm defined in RFC 4035 Section 5; and
* support NSEC3 as defined in RFC 5155; and 
* support SHA-2 as defined in RFC 4509 and RFC 5702; and
* properly handle the security concerns enumerated in RFC 6840 Section 4.

Effective March 15th, 2026: SSL.com MUST NOT use local policy to disable DNSSEC validation on any DNS query associated CAA record lookups.

Effective March 15th, 2026: DNSSEC-validation errors observed by the Primary Network Perspective (e.g., SERVFAIL) MUST NOT be treated as permission to issue.

DNSSEC validation back to the IANA DNSSEC root trust anchor MAY be performed on all DNS queries associated with CAA record lookups performed by Remote Network Perspectives as part of Multi-Perspective Issuance Corroboration.

DNSSEC validation back to the IANA DNSSEC root trust anchor is considered outside the scope of self-audits performed to fulfill the requirements in Section 8.7.

#### 3.2.2.9 Validation of mailbox authorization or control

This section defines the permitted processes and procedures for confirming the Applicant’s control of Mailbox Addresses to be included in issued Certificates.

SSL.com SHALL verify that Applicant controls the email accounts associated with all Mailbox Fields referenced in the Certificate or has been authorized by the email account holder to act on the

SSL.com SHALL NOT delegate the verification of mailbox authorization or control.

Completed validations of Applicant authority MAY be valid for the issuance of multiple Certificates over time. In all cases, the validation SHALL have been initiated within the time period specified in the relevant requirement (such as Section 4.2.1) prior to Certificate issuance.

##### 3.2.2.9.1 Validating authority over mailbox via domain

SSL.com MAY confirm the Applicant, such as an Enterprise RA, has been authorized by the email account holder to act on the account holder’s behalf by verifying the entity’s control over the domain portion of the Mailbox Address to be used in the Certificate.

An Applicant that confirms control of the domain part of an email address is authorized for any local part followed by the at-sign ("@"), followed by the Authorization Domain Name or by any other Domain Name that ends with all the Domain Labels of the validated Authorization Domain Name.

SSL.com SHALL use only the approved methods described in §3.2.2.4 to perform this verification.

For purposes of domain validation, the term Applicant includes the Applicant’s Parent Company, Subsidiary Company, or Affiliate.

##### 3.2.2.9.2 Validating control over mailbox via email

SSL.com MAY confirm the Applicant’s control over each Mailbox Field to be included in a Certificate by sending a Random Value via email and then receiving a confirming response utilizing the Random Value.

Control over each Mailbox Address SHALL be confirmed using a unique Random Value. The Random Value SHALL be sent only to the email address being validated and SHALL not be shared in any other way.

The Random Value SHALL be unique in each email. The Random Value SHALL remain valid for use in a confirming response for no more than 24 hours from its creation.

The Random Value SHALL be reset upon each instance of the email sent by SSL.com to a Mailbox Address, however all relevant Random Values sent to that Mailbox Address MAY remain valid for use in a confirming response within the validity period described in this Section.

In addition, the Random Value SHALL be reset upon first use by the user if intended for additional use as an authentication factor following the Mailbox Address verification.

##### 3.2.2.9.3 Validating applicant as operator of associated mail server(s)

SSL.com MAY confirm the Applicant’s control over each Mailbox Field to be included in the Certificate by confirming control of the SMTP FQDN to which a message delivered to the Mailbox Address should be directed. The SMTP FQDN SHALL be identified using the address resolution algorithm defined in RFC 5321 Section 5.1 which determines which SMTP FQDNs are authoritative for a given Mailbox Address. If more than one SMTP FQDN has been discovered, SSL.com SHALL verify control of an SMTP FQDN following the selection process at RFC 5321 Section 5.1. Aliases in MX record RDATA SHALL NOT be used for this validation method.

To confirm the Applicant’s control of the SMTP FQDN, SSL.com SHALL use only the currently‐approved methods described in §3.2.2.4.

##### 3.2.2.9.4 Validating control over mailbox using ACME extensions

SSL.com MAY confirm the Applicant's control over each Mailbox Field to be included in a Certificate using ACME for S/MIME as defined in RFC 8823. SSL.com's ACME server MAY respond to a POST request by sending the Random Value token components via email and SMTP, and then receiving a confirming response utilizing the generated Random Value, in accordance with RFC 8823.

Control over each Mailbox Address SHALL be confirmed using a newly-generated Random Value. The Random Value token components SHALL only be shared in accordance with RFC 8823. As defined by RFC 8823, `token-part1` SHALL contain at least 128 bits of entropy and `token-part2` SHOULD contain at least 128 bits of entropy.

The Random Value SHALL NOT be reused by SSL.com for other Certificate Requests. The Random Value SHALL remain valid for use in a confirming response for no more than 24 hours from its creation.

Implementations MAY use ACME External Account Binding as defined by RFC 8555.  

#### 3.2.2.10 Mark Verification in Verified Mark Certificates

SSL.com issues Verified Mark Certificates (VMCs) for Marks registered with a Trademark Office and qualify as a Registered Mark. These Marks can be Combined Marks, Design Marks, or Word Marks.

##### 3.2.2.10.1 Verification of Mark with Trademark Office

SSL.com SHALL verify the:

1. Registered Mark’s trademark registration number and name of the Trademark Office that granted the trademark registration; and
2. Mark Representation in SVG format that the Applicant wishes to include in the Verified Mark Certificate. Registered Marks MUST be in good standing and MUST be verified through consultation with the official database of the applicable Trademark Office.

As an alternative, the Validation Specialist MAY verify the Registered Mark through the WIPO Global Brand Database at <https://www.wipo.int/reference/en/branddb/>.

##### 3.2.2.10.2 Verification of Registered Mark Ownership or License

SSL.com SHALL confirm that the owner of the Registered Mark identified in the official database of the applicable Trademark Office or the WIPO Global Brand Database is the same Subject organization verified in §3.2.2.1.

##### 3.2.2.10.3 Confirmation of Mark Representation

SSL.com SHALL verify that the Mark submitted by the Applicant exactly matches the Registered Mark on record. This verification will be documented by comparing the Mark with the official database of the relevant Trademark Office or the WIPO Global Brand Database.

##### 3.2.2.10.4 Color Restrictions

Verified Mark Certificates for Combined and Design Marks can only display colors explicitly permitted for the Registered Mark by the relevant trademark office, if any. SSL.com SHALL review the registration to identify any specific colors claimed by the owner of the registered mark.

#### 3.2.2.11 Mark Verification in Common Mark Certificates

SSL.com issues Common Mark Certificates (MCs) for a Mark Representation that has not been verified as a Registered Mark or Government Mark.

##### 3.2.2.11.1 Verification of Prior Use of Mark for Minimum Period

This type of Mark Certificate is appropriate for Common Marks that are not Registered Marks.

The Applicant will provide SSL.com with the Mark Representation in SVG format that the Applicant
wishes to include in the Mark Certificate. SSL.com SHALL verify that:

1.	a Mark that matches the Mark Representation is currently displayed on a website. The Applicant’s control of the Domain Name of the website MUST be verified using at least one method specified in Section 3.2.14 of the MC Guidelines, and
2.	a Mark that matches the Mark Representation was historically displayed at least 12 months earlier than the date of Mark verification on the same Domain Name that was verified as being controlled by the Applicant in (1). The historical display MUST be verified via one of the Archive Webpage Sources allowed by these Requirements.

SSL.com SHALL also retain a screenshot or other record of the Mark Representation provided by the Applicant and all Mark images found during the verification process stated in the previous paragraph.

##### 3.2.2.11.2 Approved Archive Webpage Sources

Validations of Mark Representations performed in accordance with §3.2.2.11.1 SHALL employ one of the following Archive Webpage Sources:

- archive.org

This approved list may be modified from time to time.

##### 3.2.2.11.3 Color Restrictions

Mark Representations in Mark Certificates based on proof of prior use shall follow the same color rules that apply to Common Marks in the applicable jurisdiction. SSL.com SHALL review the prior use to identify any specific colors claimed by the owner of the Mark Representation.

#### 3.2.2.12 Government Mark Verification

SSL.com issues Government Mark Certificates for a Mark or equivalent granted to or claimed by a Government Entity or Non-Commercial Entity (International Organization) (or granted to a private organization or other organization by a Government Entity or Non-Commercial Entity [International Organization] through official statute, regulation, treaty,
or government action) as it appears or is described in the statute, regulation, treaty, or government action and confirmed by a Mark Verifying Authority.

##### 3.2.2.12.1 Verification of Statute, Regulation, Treaty, or Action

SSL.com MUST confirm that the Government Mark has been granted to, or claimed by, a Government Entity or a Non-Commercial Entity (International Organization) by verifying the grant or claim in publicly available records of the applicable statute, regulation, treaty, or government action.

SSL.com MUST retain a copy of the statute, regulation, treaty, or government action, including all official references (e.g., statute or regulation number and jurisdiction), as well as a copy of the Mark as contained in or referenced by the statute or regulation.

A Government Mark may also be granted to private or other types of organizations by Government or Non-Commercial Entities through an official statute, regulation, treaty, or government action.

##### 3.2.2.12.2 Verification of Government Mark Ownership or License

SSL.com MUST confirm that the owner of the Government Mark identified in Section §3.2.2.12.1 either:
1. is the same Subject Organization (Applicant) verified through the Verified Mark Identity vetting process; or
2. has granted the Subject Organization (Applicant) the right to use the Government Mark pursuant to applicable statute, regulation, treaty, or government action, or through a mutually agreed-upon license.

If the owner of record of the Government Mark is not the Applicant, the Applicant MAY use the Government Mark only if SSL.com obtains a written authorization letter from the owner of record of the Government Mark.

##### 3.2.2.12.3 Confirmation of Mark Representation

SSL.com SHALL confirm that the Mark Representation submitted by the Applicant matches the Government Mark as confirmed under Section §3.2.2.12.1. 

##### 3.2.2.12.4 Color Restrictions

SSL.com MUST review the Government Mark submitted for inclusion in a Government Mark Certificate and ensure that only the colors permitted, if any, under the applicable statute, regulation, treaty, or government action are used.

#### 3.2.2.13 Multi-Perspective Issuance Corroboration

Multi-Perspective Issuance Corroboration attempts to corroborate the determinations (i.e., domain validation pass/fail, CAA permission/prohibition) made by the Primary Network Perspective from multiple remote Network Perspectives before Certificate issuance. This process can improve protection against equally-specific prefix Border Gateway Protocol (BGP) attacks or hijacks.

SSL.com MAY use either the same set, or different sets of Network Perspectives when performing Multi-Perspective Issuance Corroboration for the required 1) Domain Authorization or Control and 2) CAA Record checks.

The set of responses from the relied upon Network Perspectives MUST provide SSL.com with the necessary information to allow it to affirmatively assess:

a. the presence of the expected 1) Random Value, 2) Request Token, 3) IP Address, or 4) Contact Address, as required by the relied upon validation method specified in Sections §3.2.2.4 and §3.2.2.5; and
b. the CA's authority to issue to the requested domain(s), as specified in §3.2.2.8.

§3.2.2.4 and §3.2.2.5 describe the validation methods that require the use of Multi-Perspective Issuance Corroboration and how a Network Perspective can corroborate the outcomes determined by the Primary Network Perspective.

Results or information obtained from one Network Perspective MUST NOT be reused or cached when performing validation through subsequent Network Perspectives (e.g., different Network Perspectives cannot rely on a shared DNS cache to prevent an adversary with control of traffic from one Network Perspective from poisoning the DNS cache used by other Network Perspectives). The network infrastructure providing Internet connectivity to a Network Perspective MAY be administered by the same organization providing the computational services required to operate the Network Perspective. All communications between a remote Network Perspective and the CA MUST take place over an authenticated and encrypted channel relying on modern protocols (e.g., over HTTPS).

A Network Perspective MAY use a recursive DNS resolver that is NOT co-located with the Network Perspective. However, the DNS resolver used by the Network Perspective MUST fall within the same Regional Internet Registry service region as the Network Perspective relying upon it. Furthermore, for any pair of DNS resolvers used on a Multi-Perspective Issuance Corroboration attempt, the straight-line distance between the two DNS resolvers MUST be at least 500 km. The location of a DNS resolver is determined by the point where unencapsulated outbound DNS queries are typically first handed off to the network infrastructure providing Internet connectivity to that DNS resolver.

SSL.com MAY immediately retry Multi-Perspective Issuance Corroboration using the same validation method or an alternative method (e.g., a CA can immediately retry validation using "Email to DNS TXT Contact" if "Agreed-Upon Change to Website - ACME" does not corroborate the outcome of Multi-Perspective Issuance Corroboration). When retrying Multi-Perspective Issuance Corroboration, SSL.com MUST NOT rely on corroborations from previous attempts. There is no stipulation regarding the maximum number of validation attempts that may be performed in any period of time.

The "Quorum Requirements" Table describes quorum requirements related to Multi-Perspective Issuance Corroboration. If SSL.com does NOT rely on the same set of Network Perspectives for both Domain Authorization or Control and CAA Record checks, the quorum requirements MUST be met for both sets of Network Perspectives (i.e.,the Domain Authorization or Control set and the CAA record check set). Network Perspectives are considered distinct when the straight-line distance between them is at least 500 km. Network Perspectives are considered "remote" when they are distinct from the Primary Network Perspective and the other Network Perspectives represented in a quorum.

SSL.com MAY reuse corroborating evidence for CAA record quorum compliance for a maximum of 398 days. After issuing a Certificate to a domain, remote Network Perspectives MAY omit retrieving and processing CAA records for the same domain or its subdomains in subsequent Certificate requests from the same Applicant for up to a maximum of 398 days.

Table: Quorum Requirements

| # of Distinct Remote Network Perspectives Used | # of Allowed non-Corroborations |
| --- | --- |
| 2-5 | 1 |
| 6+ | 2 |

Remote Network Perspectives performing Multi-Perspective Issuance Corroboration:

MUST:

- Network Hardening
    - Rely upon networks (e.g., Internet Service Providers or Cloud Provider Networks) implementing measures to mitigate BGP routing incidents in the global Internet routing system for providing internet connectivity to the Network Perspective.

SHOULD:

- Facility & Service Provider Requirements
    - Be hosted from an ISO/IEC 27001 certified facility or equivalent security framework independently audited and certified or reported.
    - Rely on services covered in one of the following reports: System and Organization Controls 2 (SOC 2), IASE 3000, ENISA 715, FedRAMP Moderate, C5:2020, CSA STAR CCM, or equivalent services framework independently audited and certified or reported.
- Vulnerability Detection and Patch Management
    - Implement intrusion detection and prevention controls to protect against common network and system threats.
    - Document and follow a vulnerability correction process that addresses the identification, review, response, and remediation of vulnerabilities.
    - Undergo or perform a Vulnerability Scan at least every three (3) months.
    - Undergo a Penetration Test on at least an annual basis.
    - Apply recommended security patches within six (6) months of the security patch's availability, unless the CA documents that the security patch would introduce additional vulnerabilities or instabilities that outweigh the benefits of applying the security patch.
- System Hardening
    - Disable all accounts, applications, services, protocols, and ports that are not used.
    - Implement multi-factor authentication for all user accounts.
- Network Hardening
    - Configure each network boundary control (firewall, switch, router, gateway, or other network control device or system) with rules that support only the services, protocols, ports, and communications identified as necessary to its operations.
    - Rely upon networks (e.g., Internet Service Providers) that: 1) use mechanisms based on Secure Inter-Domain Routing (RFC 6480), for example, BGP Prefix Origin Validation (RFC 6811), 2) make use of other non-RPKI route-leak prevention mechanisms (such as RFC 9234), and 3) apply current best practices described in BCP 194. While It is RECOMMENDED that under normal operating conditions Network Perspectives performing Multi-Perspective Issuance Corroboration forward all Internet traffic via a network or set of networks that filter RPKI-invalid BGP routes as defined by RFC 6811, it is NOT REQUIRED.

Beyond the above considerations, computing systems performing Multi-Perspective Issuance Corroboration are considered outside of the audit scope described in §8 of these Requirements.

If any of the above considerations are performed by a Delegated Third Party, SSL.com MAY obtain reasonable evidence from the Delegated Third Party to ascertain assurance that one or more of the above considerations are followed. As an exception to §1.3.2, Delegated Third Parties are not required to be within the audit scope described in §8 of these Requirements to satisfy the above considerations.

Phased Implementation Timeline:

- *Effective September 15, 2024*, SSL.com SHOULD implement Multi-Perspective Issuance Corroboration using at least two (2) remote Network Perspectives.
- *Effective March 15, 2025*, SSL.com MUST implement Multi-Perspective Issuance Corroboration using at least two (2) remote Network Perspectives. SSL.com MAY proceed with certificate issuance if the number of remote Network Perspectives that do not corroborate the determinations made by the Primary Network Perspective ("non-corroborations") is greater than allowed in the Quorum Requirements table.  
- *Effective September 15, 2025*, SSL.com MUST implement Multi-Perspective Issuance Corroboration using at least two (2) remote Network Perspectives. SSL.com MUST ensure that the requirements defined in Quorum Requirements Table are satisfied. If the requirements are not satisfied, then SSL.com MUST NOT proceed with issuance of the Certificate.
- *Effective March 15, 2026*, SSL.com MUST implement Multi-Perspective Issuance Corroboration using at least three (3) remote Network Perspectives. SSL.com MUST ensure that the requirements defined in Quorum Requirements Table are satisfied, and the remote Network Perspectives that corroborate the Primary Network Perspective fall within the service regions of at least two (2) distinct Regional Internet Registries. If the requirements are not satisfied, then SSL.com MUST NOT proceed with issuance of the Certificate.  
- *Effective June 15, 2026*, SSL.com MUST implement Multi-Perspective Issuance Corroboration using at least four (4) remote Network Perspectives. SSL.com MUST ensure that the requirements defined in Quorum Requirements Table are satisfied, and the remote Network Perspectives that corroborate the Primary Network Perspective fall within the service regions of at least two (2) distinct Regional Internet Registries. If the requirements are not satisfied, then SSL.com MUST NOT proceed with issuance of the Certificate.
- *Effective December 15, 2026*, SSL.com MUST implement Multi-Perspective Issuance Corroboration using at least five (5) remote Network Perspectives. SSL.com MUST ensure that the requirements defined in Quorum Requirements Table are satisfied, and the remote Network Perspectives that corroborate the Primary Network Perspective fall within the service regions of at least two (2) distinct Regional Internet Registries. If the requirements are not satisfied, then SSL.com MUST NOT proceed with issuance of the Certificate.

### 3.2.3 Authentication of individual identity

#### 3.2.3.1 Natural Person as an individual Applicant

If an Applicant is a natural person applying as an individual, then SSL.com shall verify the Applicant’s name and the authenticity of the certificate request.

For Server Authentication certificates, Code Signing certificates, or when the Applicant's address is displayed in the SubjectDN of the certificate, SSL.com shall also verify the Applicant's address.

For server certificates, SSL.com SHALL verify:

- the Applicant's name using a legible copy, which discernibly shows the Applicant's face, of at least one currently valid government-issued photo ID (passport, drivers license, military ID, national ID, or equivalent document type). SSL.com SHALL inspect the copy for any indication of alteration or falsification.
- the Applicant's address using a form of identification that the CA determines to be reliable, such as a government ID, utility bill, or bank or credit card statement. SSL.com MAY rely on the same government-issued ID that was used to verify the Applicant's name.
- the certificate request with the Applicant using a Reliable Method of Communication.

For Code Signing certificates, verification shall be through one or more of the methods described in the Minimum Requirements for Code Signing.

For Extended Validation Certificates, SSL.com shall follow the EV verification procedures as described in the EV Guidelines. Verification for EV Code Signing certificates must meet requirements in both the Minimum Requirements for Code Signing and the EV Guidelines.

For Document Signing Certificates, SSL.com shall rely on strong identity proofing, based on a face to face meeting with the Applicant, or a procedure that provides an equivalent assurance. The latter may include any of the following:

- means of secure video communication;
- use of identity verification software/AI;
- hybrid or other methods.

For S/MIME Certificates, the following requirements SHALL be fulfilled to authenticate Individual identity attributes included in `Sponsor-validated` and `Individual-validated` Certificate profiles:

1. SSL.com, the RA, or the Enterprise RA SHALL collect and retain evidence supporting the following identity attributes for the Individual Applicant:
    a. Given name(s) and surname(s), which SHALL be current names;
    b. Title (if used);
    c. Address (if displayed in Subject); and
    d. Further information as needed to uniquely identify the Applicant.
2. SSL.com or the RA SHALL comply with applicable data protection legislation in the gathering and retention of evidence relating to Individual identity supporting this Requirement in accordance with Section 9.4.
3. The above-mentioned identity proofing methods utilized for Document Signing Certificates MAY also be used for S/MIME Certificates.

#### 3.2.3.2 Natural Person associated with a Legal Entity

For Document Signing, S/MIME and Client Authentication Certificates issued to Natural Persons associated with Legal Entities, SSL.com  

- shall validate the Legal Entity following the requirements of §3.2.2.1;
- shall obtain evidence that the individual is associated with the Legal Entity.

For Document Signing Certificates, SSL.com shall perform identity verification of individual natural persons associated with that Legal Entity following the requirements of §3.2.3.1.

For S/MIME and Client Authentication Certificates, SSL.com may also rely on the Legal Entity to perform identity verification of individual natural persons associated with that Legal Entity.

For S/MIME Certificates, an Enterprise RA issuing a Sponsor-validated Certificate SHALL validate all identity attributes of an Individual to be included in the Certificate. The Enterprise RA MAY rely upon existing internal records to validate Individual identity.

### 3.2.4 Non-verified information

SSL.com does not verify information contained in the Organization Unit (OU) field in any certificate request, and only ensures that the OU attribute meets the requirements described in §7.1.4.2.2 i. Other information may be designated as non-verified in specific certificate profiles. Non-verified information other than the OU field will be detailed in the certificate profile and in the verification process for that certificate type as given in §4.

SSL.com may waive its standard identity validation procedures for Test Document Signing Certificates. Any such certificates SHALL clearly indicate that they are for testing purposes, as specified in §7.1.6.

### 3.2.5 Validation of authority

SSL.com shall verify the authorization of all certificate requests.

For server certificate requests:

- If the Applicant for a Certificate containing Subject Identity Information is an organization, SSL.com SHALL use a Reliable Method of Communication to verify the authenticity of the Applicant Representative's certificate request.
- SSL.com MAY use the sources listed in §3.2.2.1 to verify the Reliable Method of Communication. Provided that a Reliable Method of Communication is used, SSL.com MAY establish the authenticity of the certificate request directly with the Applicant Representative or with an authoritative source within the Applicant's organization, such as the Applicant's main business offices, corporate offices, human resource offices, information technology offices, or other department that SSL.com deems appropriate.
- In addition, SSL.com SHALL establish a process that allows an Applicant to specify the individuals who may request Certificates. If an Applicant specifies, in writing, the individuals who may request a Certificate, then SSL.com SHALL NOT accept any certificate requests that are outside this specification. SSL.com SHALL provide an Applicant with a list of its authorized certificate requesters upon the Applicant's verified written request.

For Code Signing certificate requests, verification of this authority shall be through one or more of the methods described in the Code Signing Baseline Requirements. Verification of authority for EV Code Signing certificates must meet the EV requirements described in the Code Signing Baseline Requirements.

For Extended Validation TLS Certificate requests, SSL.com shall follow procedures described in the EV Guidelines to verify the authority of the request.

### 3.2.6 Criteria for interoperation

SSL.com MAY issue Cross-Certified Subordinate CA Certificates as required in order to assist root roll-over operations.

SSL.com MAY issue Cross-Certified Subordinate CA Certificates to other CA operators provided there is alignment with this CP/CPS and SSL.com arranged for or accepted the establishment of the trust relationship (i.e. the Cross-Certified Subordinate CA Certificate at issue). The cross certification terms and criteria are to be set forth in an applicable agreement.

All Cross-Certified Subordinate CA Certificates that identify SSL.com as the Subject SHALL be disclosed in CCADB and the SSL.com Repository.

## 3.3 Identification and authentication for re-keying

Re-keying (sometimes called reissuing) refers to the issuance of an entirely new certificate, using some or all of the information submitted for an existing certificate and using a newly generated Private Key.

Subscribers may request re-keying of an SSL.com certificate prior to the certificate's expiration.

Subordinate CAs of SSL.com may request re-keying of a certificate registered by them prior to the certificate's expiration.
The re-keying process is detailed fully in §4.7.

This section is not applicable to Mark Certificates.

### 3.3.1 Re-keying request by Subscriber

#### 3.3.1.1 Subscriber re-keying request via SSL.com Account Dashboard

A Subscriber may request re-key of any unexpired SSL.com certificate via their SSL.com Account Dashboard. Any changes made when requesting re-keying by this method may require validation and/or authentication steps as described in §4.7.

#### 3.3.1.2 Subscriber re-keying request via other means

A Subscriber requesting re-keying of an unexpired SSL.com certificate by any method other than their SSL.com Account Dashboard requires validation and/or authentication steps as described in §4.7.

### 3.3.2 Identification and authentication for re-key after revocation

A Subscriber requesting re-key of an SSL.com certificate after that certificate has been revoked will need to apply for and follow all validation and/or authentication procedures for a new certificate.

## 3.4 Identification and authentication for revocation requests

SSL.com may revoke any certificate issued within the SSL.com PKI at its sole discretion.
In all cases, identification and/or authorization for a revocation request must follow the procedures detailed in §4.9.3.

### 3.4.1 Identification and authentication for revocation requests by Subscribers

A Subscriber, or the Subscriber's authorized agent, may request revocation of any unexpired SSL.com certificate via their SSL.com Account Dashboard.

Revocation requests from  a Subscriber or authorized agent for an unexpired SSL.com certificate by any method other than their SSL.com Account Dashboard may, at SSL.com's sole discretion, require further validation and/or authentication steps as described in §4.9.

SSL.com may, if necessary, and at its sole discretion, confirm a revocation request by other means, including (but not limited to) contact with the Subscriber or authorized representatives of the Subscriber.

### 3.4.2 Revocation requests by non-Subscribers

Non-Subscribers  (such as Relying Parties, Application Software Suppliers, and other third parties) may file a Certificate Revocation Request in order to register:

- Complaints related to certificate issuance
- Suspected Private Key compromise
- Certificate misuse
- Other types of fraud, compromise, misuse, or inappropriate conduct related to the certificate.

Non-Subscriber Certificate Revocation Requests must follow the procedures detailed in §4.9.3.

### 3.4.3 Identification and authentication for revocation requests by other participants in the SSL.com PKI

A revocation request for an SSL.com-issued certificate by any other authorized participant in the SSL.com PKI (such as a Subordinate CA or external RA) shall be identified and/or authenticated by that authorized participant.

Identification and/or authorization for a revocation request must in all cases follow the procedures detailed in §4.9.