# 7 CERTIFICATE, CRL, AND OCSP PROFILES

## 7.1 Certificate Profiles

SSL.com shall meet the technical requirements set forth in §6.1.5 and §6.1.6 of the SSL.com CP/CPS.

SSL.com shall generate Certificate serial numbers greater than zero (0) containing at least 64 bits of output from a CSPRNG.

### 7.1.1 Version Numbers

The SSL.com PKI issues Certificates in compliance with the X.509 Version 3, which corresponds to certificate version number 2.

### 7.1.2 Certificate Content and Extensions

SSL.com Certificates comply with RFC 5280 and with applicable best industry practices.

A tabled view of the most common certificate profiles used by SSL.com are listed in Annex A (SSL.com Certificate Profiles).

#### 7.1.2.1 Root CA Certificate

##### a. basicConstraints

- This extension MUST appear as a critical extension. The cA field MUST be set true. The pathLenConstraint field SHOULD NOT be present.

##### b. keyUsage

- This extension MUST be present and MUST be marked critical. Bit positions for keyCertSign and cRLSign MUST be set. If the Root CA Private Key is used for signing OCSP responses, then the digitalSignature bit MUST be set.

##### c. certificatePolicies

- This extension SHOULD NOT be present.

##### d. extKeyUsage

- This extension MUST NOT be present.

#### 7.1.2.2 Subordinate CA Certificate

##### a. certificatePolicies

- This extension must be present and should not be marked critical.
    - certificatePolicies:policyIdentifier (Required): See §7.1.6
- The following fields may be present if the Subordinate CA is not an Affiliate of SSL.com.
    - certificatePolicies:policyQualifiers:policyQualifierId (Optional)
        - id-qt 1 RFC 5280
        - certificatePolicies:policyQualifiers:qualifier:cPSuri (Optional)
- HTTP URL for the Root CA's Certificate Policy, Certification Practice Statement, Relying Party Agreement, or other pointer to online policy information provided by SSL.com and the Subordinate CA.

##### b. cRLDistributionPoints (if applicable)

- This extension must be present and must not be marked critical. It must contain the HTTP URL of the Issuing CA's CRL service.

##### c. authorityInformationAccess (if applicable)

- If the Issuing CA issues Code Signing or Time-stamping Certificates, this extension MUST be present and MUST NOT be marked critical. The extension MUST contain the HTTP URL of the Issuing CA’s certificate (accessMethod = `1.3.6.1.5.5.7.48.2`) and if the CA provides OCSP responses, the HTTP URL for the CA’s OCSP responder (accessMethod = `1.3.6.1.5.5.7.48.1`).

- For all other Issuing CAs this extension SHOULD be present. It MUST NOT be marked critical. It SHOULD contain the HTTP URL of the Issuing CA's certificate (accessMethod = `1.3.6.1.5.5.7.48.2`) and it MAY contain the HTTP URL of the Issuing CA's OCSP responder (accessMethod = `1.3.6.1.5.5.7.48.1`).

##### d. basicConstraints (critical)

- The cA field is set true. The pathLenConstraint field may be present.

##### e. keyUsage (critical)

- keyCertSign and cRLSign bits are set. Optionally, digitalSignature can be set.

##### f. nameConstraints (optional)

- If present, this extension should not be marked critical[^CriticalNameConstraints].

[^CriticalNameConstraints]: Non-critical Name Constraints are an exception to RFC 5280 (4.2.1.10), however, they may be used until the Name Constraints extension is supported by Application Software Suppliers whose software is used by a substantial portion of Relying Parties worldwide.

##### g. extkeyUsage

- For Cross Certificates that share a Subject Distinguished Name and Subject Public Key with a Root Certificate operated in accordance with this CP/CPS, this extension MAY be present. If present, this extension SHOULD NOT be marked critical. This extension MUST only contain usages for which the issuing CA has verified the Cross Certificate is authorized to assert. This extension MAY contain the `anyExtendedKeyUsage` RFC 5280 usage, if the Root Certificate(s) associated with this Cross Certificate are operated by the same organization as the issuing Root Certificate.

- For all other Subordinate CA Certificates, including Technically Constrained Subordinate CA Certificates:
    - This extension MUST be present and SHOULD NOT be marked critical.
    - For Subordinate CA Certificates that will be used to issue TLS certificates, the value `id-kp-serverAuth` RFC 5280 MUST be present. The value `id-kp-clientAuth` RFC 5280 MAY be present. The values `id-kp-emailProtection` RFC 5280, `id-kp-codeSigning` RFC 5280, `id-kp-timeStamping` RFC 5280, and `anyExtendedKeyUsage` RFC 5280 MUST NOT be present. Other values SHOULD NOT be present.
    - For Subordinate CA Certificates that are not used to issue TLS certificates, then the value `id-kp-serverAuth` RFC 5280 MUST NOT be present. Other values MAY be present, but SHOULD NOT combine multiple independent key purposes (e.g. including `id-kp-timeStamping` RFC 5280 with `id-kp-codeSigning` RFC 5280).
    - For Subordinate CA Certificates that will be used to issue Mark Certificates, value MUST contain `id-kp-BrandIndicatorforMessageIdentification` (OID: `1.3.6.1.5.5.7.3.31`) as specified in Section 7 of the IETF Internet-Draft at <https://tools.ietf.org/html/draft-chuang-bimi-certificate-00>. This indicates the application of the Mark Certificate Profile. Other KeyPurposeIds MUST NOT be included.

##### h. authorityKeyIdentifier (required)

- This extension MUST be present and MUST NOT be marked critical. It MUST contain a keyIdentifier field and it MUST NOT contain a authorityCertIssuer or authorityCertSerialNumber field.

- By issuing a Subordinate CA Certificate, SSL.com represents that it followed the procedure set forth in this CP/CPS to verify that, as of the CA Certificate’s issuance date, all of the Subject Information was validated and found to be accurate.

#### 7.1.2.3 Subscriber Certificate

##### a. certificatePolicies

- This extension must be present and should not be marked critical.
    - certificatePolicies:policyIdentifier (Required): (See §7.1.6)

- The following extensions may be present:
    - certificatePolicies:policyQualifiers:policyQualifierId (Recommended)
        - id-qt 1 RFC 5280
    - certificatePolicies:policyQualifiers:qualifier:cPSuri (Optional)
        - HTTP URL for the Subordinate CA's Certificate Polic<ins>y</ins><del>ies</del>, Certification Practice Statement, Relying Party Agreement, or other pointer to online policy information provided by SSL.com and the Subordinate CA.

##### b. cRLDistributionPoints (if applicable)

- The CRL Distribution Points extension MUST be present in TLS Subscriber Certificates that
    1. do not qualify as "Short-lived Subscriber Certificates" and
    2. do not include an Authority Information Access extension with an id-ad-ocsp accessMethod.
- The CRL Distribution Points extension is OPTIONAL in Short-lived TLS Subscriber Certificates.
- When present, the CRL Distribution Points extension MUST contain at least one `DistributionPoint`; containing more than one is NOT RECOMMENDED. All `DistributionPoint` items must be formatted as follows:

| __Field__ | __Presence__ | __Description__ |
| --- | -- | ----- |
| `distributionPoint` | MUST | The `DistributionPointName` MUST be a `fullName` formatted as described below. |
| `reasons` | MUST NOT | |
| `cRLIssuer` | MUST NOT | |

A `fullName` MUST contain at least one `GeneralName`; it MAY contain more than one. All `GeneralName`s MUST be of type `uniformResourceIdentifier`, and the scheme of each MUST be "http". The first `GeneralName` must contain the HTTP URL of the Issuing CA's CRL service for this certificate.

##### c. authorityInformationAccess (if applicable)

- For TLS, Code Signing and Time-stamping Certificates this extension MUST be present and for other types of Certificates it MAY be present. If present, it MUST NOT be marked critical. For TLS Certificates it MUST contain the HTTP URL of the Issuing CA's OCSP responder (`accessMethod` = `1.3.6.1.5.5.7.48.1`) and SHOULD contain the HTTP URL of the Issuing CA's certificate (`accessMethod` = `1.3.6.1.5.5.7.48.2`). For Code Signing or Timestamping Certificates, it MUST contain the HTTP URL of the Issuing CA's certificate (`accessMethod` = `1.3.6.1.5.5.7.48.2`) and if the CA provides OCSP responses, the HTTP URL for the CA’s OCSP responder (accessMethod = `1.3.6.1.5.5.7.48.1`). For all other Subscriber Certificates, it MAY contain the HTTP URL of the Issuing CA's certificate (`accessMethod` = `1.3.6.1.5.5.7.48.2`) and if the CA provides OCSP responses, the HTTP URL for the CA’s OCSP responder (accessMethod = `1.3.6.1.5.5.7.48.1`).

##### d. basicConstraints (optional)

- This extension should not be present. If present, the cA field must be set false.

##### e. keyUsage (optional)

- If present, bit positions for keyCertSign and cRLSign must not be set.

##### f. extKeyUsage (required)

- Depending on the usage of the certificate, the proper extended key usage (EKU) will be applied. More information available in Annex A.
- For Timestamp Certificates, this extention MUST be marked critical. For other types, the extention SHOULD NOT be marked critical.
- For TLS Certificates either the value `id-kp-serverAuth` RFC 5280 or `id-kp-clientAuth` RFC 5280 or both values MUST be present. `id-kp-emailProtection` RFC 5280 MAY be present. Other values SHOULD NOT be present. The value `anyExtendedKeyUsage` MUST NOT be present.
- For Code Signing Certificates the value `id-kp-codeSigning` RFC 5280 MUST be present. The value `lifetimeSigning` (`1.3.6.1.4.1.311.10.3.13`) MAY be present. The value `anyExtendedKeyUsage` (2.5.29.37.0), `serverAuth` (`1.3.6.1.5.5.7.3.1`), `emailProtection` (`1.3.6.1.5.5.7.3.4`) and `timeStamping` (`1.3.6.1.5.5.7.3.8`) MUST NOT be present. Other values SHOULD NOT be present. If any other value is present, SSL.com MUST have a business agreement with a Platform vendor requiring that EKU in order to issue a Platform-specific code signing certificate with that EKU.
- For Timestamp Certificates the value `id-kp-timeStamping` RFC 5280 MUST be present. The value `anyExtendedKeyUsage` (2.5.29.37.0), `serverAuth` (`1.3.6.1.5.5.7.3.1`), `emailProtection` (`1.3.6.1.5.5.7.3.4`) and `codeSigning` RFC 5280 MUST NOT be present. Other values SHOULD NOT be present. If any other value is present, SSL.com MUST have a business agreement with a Platform vendor requiring that EKU in order to issue a Platform-specific code signing certificate with that EKU.
- It is forbidden for Intermediate CAs to issue end-entity Certificates which blend the serverAuth (`1.3.6.1.5.5.7.3.1`), emailProtection (`1.3.6.1.5.5.7.3.2`) and codeSigning (`1.3.6.1.5.5.7.3.3`) extended key usages.

##### g. DelegationUsage (optional)

- For TLS Certificates, SSL.com supports the IETF draft <https://datatracker.ietf.org/doc/html/draft-ietf-tls-subcerts> for Delegated Credentials.

##### h. signedCertificateTimestampList (OID: 1.3.6.1.4.1.11129.2.4.2)

- This extension MUST NOT be critical
  
#### 7.1.2.4 OCSP Responder Certificate

##### a. certificatePolicies

- For OCSP Responder Certificates issuing responses for TLS Certificates, this extension MUST NOT be present.

##### b. cRLDistributionPoints

- For OCSP Responder Certificates issuing responses for TLS Certificates, this extension MUST NOT be present.

##### c. authorityInformationAccess

- For OCSP Responder certificates issuing responses for TLS Certificates, this extension is NOT RECOMMENDED, as the Relying Party should already possess the necessary information. In order to validate the given Responder certificate, the Relying Party must have access to the Issuing CA's certificate, eliminating the need to provide `id-ad-caIssuers`. Similarly, because of the requirement for an OCSP Responder certificate to include the `id-pkix-ocsp-nocheck` extension, it is not necessary to provide `id-ad-ocsp`, as such responses will not be checked by Relying Parties.

- If present, for OCSP Responder certificates issuing responses for TLS Certificates the `AuthorityInfoAccessSyntax` MUST contain one or more `AccessDescription`s. Each `AccessDescription` MUST only contain a permitted `accessMethod`, as detailed below, and each `AuthorityInfoAccessSyntax` MUST contain all required `AccessDescription`s.

| __Access Method__ | __OID__ | __Access Location__ | __Presence__ | __Maximum__ | __Description__ |
| - | - | - | - | - | ----- |
| `id-ad-ocsp` | `1.3.6.1.5.5.7.48.1` | `uniformResourceIdentifier` | NOT RECOMMENDED | \* | A HTTP URL of the Issuing CA's OCSP responder. |
| Any other value | - | - | MUST NOT | - | No other `accessMethod`s may be used. |

##### d. basicConstraints (optional)

- OCSP Responder certificates MUST NOT be CA certificates. The issuing CA may indicate this one of two ways: by omission of the `basicConstraints` extension, or through the inclusion of a `basicConstraints` extension that sets the `cA` boolean to FALSE.

| __Field__ | __Description__ |
| -- | -- |
| `cA` | MUST be FALSE |
| `pathLenConstraint` | MUST NOT be present |

**Note**: Due to DER encoding rules regarding the encoding of DEFAULT values within OPTIONAL fields, a `basicConstraints` extension that sets the `cA` boolean to FALSE MUST have an `extnValue` `OCTET STRING` which is exactly the hex-encoded bytes `3000`, the encoded representation of an empty ASN.1 `SEQUENCE` value.

##### e. keyUsage (required)

| __Key Usage__ | __Permitted__ | __Required__ |
| ------ | -- | -- |
| `digitalSignature` | Y | Y |
| `nonRepudiation` | N | -- |
| `keyEncipherment` | N | -- |
| `dataEncipherment` | N | -- |
| `keyAgreement` | N | -- |
| `keyCertSign` | N | -- |
| `cRLSign` | N | -- |
| `encipherOnly` | N | -- |
| `decipherOnly` | N | -- |

##### f. extKeyUsage (required)

| __Key Purpose__ | __OID__ | __Presence__ |
| ------ | -- | -- |
| `id-kp-OCSPSigning` | `1.3.6.1.5.5.7.3.9` | MUST |
| Any other value | - | MUST NOT |

#### 7.1.2.5 All Certificates

All other fields and extensions must be set in accordance with RFC 5280. SSL.com shall not issue a Certificate that contains a keyUsage flag, extKeyUsage value, Certificate extension, or other data not specified in §7.1.2.1, §7.1.2.2, §7.1.2.3 and Annex A unless SSL.com is aware of a reason for including the data in the Certificate.

SSL.com shall not issue a Server TLS Certificate with:

1. Extensions that do not apply in the context of the public Internet (such as an extKeyUsage key purpose for a service that is only valid in the context of a privately managed network), unless:
    a. such value falls within an OID arc for which the Applicant demonstrates ownership, or
    b. the Applicant can otherwise demonstrate the right to assert the data in a public context.
    c. the extension is defined within an open standards specification and intended for use by other organizations. A Certificate that includes such an extension MUST conform to the specifications of the open standard and this CP/CPS.
2. Field or extension values which have not been validated according to the processes and procedures described in this CP/CPS.

All Certificates include the following extensions:

- Authority Key Identifier: Provides information to identify the Public Key corresponding to the Private Key used to sign a Certificate. This field contains the "Subject Key Identifier" of the issuing CA’s Certificate
- Subject Key Identifier: Identifies a particular Public Key uniquely. It contains the ID of the Certificate Holder’s key

#### 7.1.2.6 Application of RFC 5280

For purposes of clarification, a Precertificate, as described in RFC 6962 - Certificate Transparency, shall not be considered to be a "certificate" subject to the requirements of RFC 5280 - Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile.

### 7.1.3 Algorithm object identifiers

#### 7.1.3.1 SubjectPublicKeyInfo

The following requirements apply to the `subjectPublicKeyInfo` field within a Certificate or Precertificate. No other encodings are permitted.

##### 7.1.3.1.1 RSA

SSL.com SHALL indicate an RSA key using the rsaEncryption (OID: 1.2.840.113549.1.1.1) algorithm identifier. The parameters MUST be present, and MUST be an explicit NULL.

SSL.com SHALL NOT use a different algorithm, such as the id-RSASSA-PSS (OID: 1.2.840.113549.1.1.10) algorithm identifier, to indicate an RSA key.

When encoded, the `AlgorithmIdentifier` for RSA keys MUST be byte-for-byte identical with the following hex-encoded bytes: `300d06092a864886f70d0101010500`

##### 7.1.3.1.2 ECDSA

SSL.com SHALL indicate an ECDSA key using the id-ecPublicKey (OID: 1.2.840.10045.2.1) algorithm identifier. The parameters SHALL use the `namedCurve` encoding.

- For P-256 keys, the `namedCurve` MUST be secp256r1 (OID: 1.2.840.10045.3.1.7).
- For P-384 keys, the `namedCurve` MUST be secp384r1 (OID: 1.3.132.0.34).
- For P-521 keys, the `namedCurve` MUST be secp521r1 (OID: 1.3.132.0.35).

When encoded, the `AlgorithmIdentifier` for ECDSA keys MUST be byte-for-byte identical with the following hex-encoded bytes:

- For P-256 keys, `301306072a8648ce3d020106082a8648ce3d030107`.
- For P-384 keys, `301006072a8648ce3d020106052b81040022`.
- For P-521 keys, `301006072a8648ce3d020106052b81040023`.

#### 7.1.3.2 Signature AlgorithmIdentifier

All objects signed by a CA Private Key MUST conform to this CP/CPS on the use of the `AlgorithmIdentifier` or `AlgorithmIdentifier`-derived type in the context of signatures.

In particular, it applies to all of the following objects and fields:

- The `signatureAlgorithm` field of a Certificate or Precertificate.
- The `signature` field of a TBSCertificate (for example, as used by either a Certificate or Precertificate).
- The `signatureAlgorithm` field of a CertificateList
- The `signature` field of a TBSCertList
- The `signatureAlgorithm` field of a BasicOCSPResponse.

No other encodings are permitted for these fields.

##### 7.1.3.2.1 RSA

SSL.com SHALL use one of the following signature algorithms and encodings. When encoded, the `AlgorithmIdentifier` MUST be byte-for-byte identical with the specified hex-encoded bytes.

- RSASSA-PKCS1-v1_5 with SHA-256:

  Encoding:
  `300d06092a864886f70d01010b0500`.

- RSASSA-PKCS1-v1_5 with SHA-384:

  Encoding:
  `300d06092a864886f70d01010c0500`.

- RSASSA-PKCS1-v1_5 with SHA-512:

  Encoding:
  `300d06092a864886f70d01010d0500`.

- RSASSA-PSS with SHA-256, MGF-1 with SHA-256, and a salt length of 32 bytes:

  Encoding:
  ```
  304106092a864886f70d01010a3034a00f300d0609608648016503040201
  0500a11c301a06092a864886f70d010108300d0609608648016503040201
  0500a203020120
  ```

- RSASSA-PSS with SHA-384, MGF-1 with SHA-384, and a salt length of 48 bytes:

  Encoding:
  ```
  304106092a864886f70d01010a3034a00f300d0609608648016503040202
  0500a11c301a06092a864886f70d010108300d0609608648016503040202
  0500a203020130
  ```

- RSASSA-PSS with SHA-512, MGF-1 with SHA-512, and a salt length of 64 bytes:

  Encoding:
  ```
  304106092a864886f70d01010a3034a00f300d0609608648016503040203
  0500a11c301a06092a864886f70d010108300d0609608648016503040203
  0500a203020140
  ```

In addition, SSL.com MAY use the following signature algorithm and encoding if all of the following conditions are met:

- If used within a Certificate, such as the `signatureAlgorithm` field of a Certificate or the `signature` field of a TBSCertificate:
    - The new Certificate is a Root CA Certificate or Subordinate CA Certificate that is a Cross-Certificate; and,
    - There is an existing Certificate, issued by the same issuing CA Certificate, using the following encoding for the signature algorithm; and,
    - The existing Certificate has a `serialNumber` that is at least 64-bits long; and,
    - The only differences between the new Certificate and existing Certificate are one of the following:
        - A new `subjectPublicKey` within the `subjectPublicKeyInfo`, using the same algorithm and key size; and/or,
        - A new `serialNumber`, of the same encoded length as the existing Certificate; and/or
        - The new Certificate's `extKeyUsage` extension is present, has at least one key purpose specified, and none of the key purposes specified are the id-kp-serverAuth (OID: `1.3.6.1.5.5.7.3.1`) or the anyExtendedKeyUsage (OID: `2.5.29.37.0`) key purposes; and/or
        - The new Certificate's `basicConstraints` extension has a pathLenConstraint that is zero.
- If used within an OCSP response, such as the `signatureAlgorithm` of a BasicOCSPResponse:
    - The `producedAt` field value of the ResponseData MUST be earlier than 2022-06-01 00:00:00 UTC; and,
    - All unexpired, un-revoked Certificates that contain the Public Key of the CA Key Pair and that have the same Subject Name MUST also contain an `extKeyUsage` extension with the only key usage present being the id-kp-ocspSigning (OID: `1.3.6.1.5.5.7.3.9`) key usage.
- If used within a CRL, such as the `signatureAlgorithm` field of a CertificateList or the `signature` field of a TBSCertList:
    - The CRL is referenced by one or more Root CA or Subordinate CA Certificates; and,
    - The Root CA or Subordinate CA Certificate has issued one or more Certificates using the following encoding for the signature algorithm.

**Note:** The above requirements do not permit SSL.com to sign a Precertificate with this encoding.

- RSASSA-PKCS1-v1_5 with SHA-1:

    Encoding:
    `300d06092a864886f70d0101050500`

##### 7.1.3.2.2 ECDSA

SSL.com SHALL use the appropriate signature algorithm and encoding based upon the signing key used.

If the signing key is P-256, the signature MUST use ECDSA with SHA-256. When encoded, the `AlgorithmIdentifier` MUST be byte-for-byte identical with the following hex-encoded bytes: `300a06082a8648ce3d040302`.

If the signing key is P-384, the signature MUST use ECDSA with SHA-384. When encoded, the `AlgorithmIdentifier` MUST be byte-for-byte identical with the following hex-encoded bytes: `300a06082a8648ce3d040303`.

If the signing key is P-521, the signature MUST use ECDSA with SHA-512. When encoded, the `AlgorithmIdentifier` MUST be byte-for-byte identical with the following hex-encoded bytes: `300a06082a8648ce3d040304`.

### 7.1.4 Name forms

SSL.com Certificates support name chaining as specified in RFC 5280. All issued Certificates incorporate a unique identifying serial number.

#### 7.1.4.1 Name Encoding

The content of the Certificate Issuer Distinguished Name field must match the Subject DN of the Issuing CA to support Name chaining as specified in RFC 5280, Section 4.1.2.4.

For every valid Certification Path (as defined by RFC 5280, Section 6):

- For each Certificate in the Certification Path, the encoded content of the Issuer Distinguished Name field of a Certificate SHALL be byte-for-byte identical with the encoded form of the Subject Distinguished Name field of the Issuing CA certificate.
- For each CA Certificate in the Certification Path, the encoded content of the Subject Distinguished Name field of a Certificate SHALL be byte-for-byte identical among all Certificates whose Subject Distinguished Names can be compared as equal according to RFC 5280, Section 7.1, and including expired and revoked Certificates.

#### 7.1.4.2 Subject Information - Subscriber Certificates

By issuing a Server Certificate, SSL.com represents that it followed the procedures set forth in this CP/CPS to verify that, as of the Certificate's issuance date, all of the Subject Information was accurate. SSL.com shall not include a Domain Name or IP Address in a Subject attribute except as specified in §3.2.2.4 or §3.2.2.5. Subject attributes MUST NOT contain only metadata such as '.', '-', and ' ' (i.e. space) characters, and/or any other indication that the value is absent, incomplete, or not applicable.

By issuing a Personal/Client/CodeSigning Certificate, SSL.com represents that it followed the procedures set forth in this CP/CPS to verify that, as of the Certificate's issuance date, all of the Subject Information was accurate. SSL.com shall not include a commonName, emailAddress in a Subject attribute except as specified in §3.2.3. Because Subject name attributes for individuals (e.g. givenName (2.5.4.42) and surname (2.5.4.4)) are not broadly supported by application software, SSL.com may use the `subject:organizationName` field to convey a natural person Subject’s name or DBA.

##### 7.1.4.2.1 Subject Alternative Name Extension

Certificate Field: extensions:subjectAltName

- Required/Optional:
    - **Required** for TLS
    - **Optional** for Code Signing Certificates

**Contents for non-EV TLS Server Certificates**: This extension must contain at least one entry. Each entry SHALL be one of the following types:

- `dNSName`: The entry SHALL contain either a Fully-Qualified Domain Name or Wildcard Domain Name that SSL.com has validated in accordance with §3.2.2.4. Wildcard Domain Names SHALL be validated for consistency with §3.2.2.6. The entry SHALL NOT contain an Internal Name. Underscore characters ("_") SHALL NOT be present in `dNSName` entries. Effective 2025-09-15, the entry MUST NOT contain an Address and Routing Parameter Area Name. Effective 2026-03-15, the entry MUST NOT contain a Domain Name that ends in an IP Address Reverse Zone Suffix.

   The Fully-Qualified Domain Name or the FQDN portion of the Wildcard Domain Name contained in the entry SHALL be composed entirely of LDH Labels joined together by a U+002E FULL STOP (".") character. The zero-length Domain Label representing the root zone of the Internet Domain Name System SHALL NOT be included (e.g. "example.com" SHALL be encoded as "example.com" and SHALL NOT be encoded as "example.com.").

   The Fully-Qualified Domain Name or the FQDN portion of the Wildcard Domain Name SHALL consist solely of Domain Labels that are P-Labels or Non-Reserved LDH Labels.

- `iPAddress`: The entry SHALL contain an IPv4 or IPv6 address that SSL.com has validated in accordance with §3.2.2.5. The entry SHALL NOT contain a Reserved IP Address.

**Contents for Code Signing Certificates**: If this field is present, it shall not contain dNSName, iPAddress or other entries that point to a Domain Name or IP Address.

##### 7.1.4.2.2 Subject Distinguished Name Fields

###### a. Certificate Field: subject:commonName (OID 2.5.4.3)

- Required/Optional:
    - **Deprecated** (Discouraged, but not prohibited) for SSL (EV and non-EV) and Mark Certificates
    - **Required** for Code Signing or EV Code Signing Certificates
- **Contents for non-EV SSL Server Certificates:** If present, this field MUST contain exactly one entry that is one of the values contained in the Certificate's `subjectAltName` extension (see §7.1.4.2.1). The value of the field MUST be encoded as follows:
    - If the value is an IPv4 address, then the value MUST be encoded as an IPv4Address as specified in RFC 3986, Section 3.2.2.
    - If the value is an IPv6 address, then the value MUST be encoded in the text representation specified in RFC 5952, Section 4.
    - If the value is a Fully-Qualified Domain Name or Wildcard Domain Name, then the value MUST be encoded as a character-for-character copy of the `dNSName` entry value from the `subjectAltName` extension. Specifically, all Domain Labels of the Fully-Qualified Domain Name or FQDN portion of the Wildcard Domain Name must be encoded as LDH Labels, and P-Labels MUST NOT be converted to their Unicode representation.
- **Contents for Code Signing Certificates:** This field must contain the Subject’s legal name as verified under §3.2.2.2.

###### b. Certificate Field: subject:organizationName (OID 2.5.4.10)

- Required/Optional:
    - **Optional** for non-OV or non-EV TLS
    - **Required** for OV TLS, EV TLS, or Code Signing
- **Contents for non-EV TLS Certificates:** If present, the `subject:organizationName` field must contain either the Subject’s name and/or DBA/tradename as verified under §3.2.2.2. SSL.com may include information in this field that differs slightly from the verified name, such as common variations or abbreviations, provided that SSL.com documents the difference and any abbreviations used are locally accepted abbreviations; e.g., if the official record shows "Company Name Incorporated", SSL.com may use "Company Name Inc." or "Company Name". Because Subject name attributes for individuals (e.g. givenName (2.5.4.42) and surname (2.5.4.4)) are not broadly supported by application software, SSL.com may use the `subject:organizationName` field to convey a natural person Subject’s name and/or DBA/tradename. If both are included, the DBA/tradename SHALL appear first, followed by the Subject's name in parentheses.
- **Contents for Code Signing Certificates:** If present, the `subject:organizationName` field must contain either the Subject’s name or DBA as verified under §3.2.2.2. SSL.com may include information in this field that differs slightly from the verified name, such as common variations or abbreviations, provided that SSL.com documents the difference and any abbreviations used are locally accepted abbreviations; e.g., if the official record shows "Company Name Incorporated", SSL.com may use "Company Name Inc." or "Company Name". Because Subject name attributes for individuals (e.g. givenName (2.5.4.42) and surname (2.5.4.4)) are not broadly supported by application software, SSL.com may use the `subject:organizationName` field to convey a natural person Subject’s name or DBA.
- If the combination of names or the organization name by itself exceeds 64 characters, SSL.com may abbreviate parts of the organization name, and/or omit non-material words in the organization name in such a way that the text in this field does not exceed the 64-character limit. SSL.com shall check this field in accordance with §4.2.1 and a Relying Party will not be misled into thinking that they are dealing with a different organization.

###### c. Certificate Field: subject:givenName (2.5.4.42) and subject:surname (2.5.4.4)

- **Contents:** If present, the `subject:givenName` field and `subject:surname` field MUST contain a natural person Subject’s name as verified under §3.2.3. A TLS Certificate containing a `subject:givenName` field or `subject:surname` field MUST contain the (`2.23.140.1.2.3`) Certificate Policy OID.

###### d. Certificate Field: Number and street: subject:streetAddress (OID: 2.5.4.9)

- Required/Optional:
    - **Optional** if the `subject:organizationName` field, `subject:givenName` field, or `subject:surname` field are present.
    - **Prohibited** if the `subject:organizationName` field, subject:givenName, and `subject:surname` field are absent.
- **Contents for non-EV TLS or Code Signing Certificates:** If present, the `subject:streetAddress` field must contain the Subject’s street address information as verified under §3.2.2.1.

###### e. Certificate Field: subject:localityName (OID: 2.5.4.7)

- Required/Optional:
    - **Required** if the `subject:organizationName` field, `subject:givenName` field, or `subject:surname` field are present and the `subject:stateOrProvinceName` field is absent.
    - **Optional** if the `subject:stateOrProvinceName` field and the `subject:organizationName` field, `subject:givenName` field, or `subject:surname` field are present.
    - **Prohibited** if the `subject:organizationName` field, subject:givenName, and `subject:surname` field are absent.
- **Contents:** If present, the `subject:localityName` field must contain the Subject’s locality information as verified under §3.2.2.1. If the `subject:countryName` field specifies the ISO 3166-1 user-assigned code of XX in accordance with §7.1.4.2.2(h), the localityName field may contain the Subject’s locality and/or state or province information as verified under §3.2.2.1.

###### f. Certificate Field: subject:stateOrProvinceName (OID: 2.5.4.8)

- Required/Optional:
    - **Required** if the `subject:organizationName` field, `subject:givenName` field, or `subject:surname` field are present and `subject:localityName` field is absent.
    - **Optional** if the `subject:localityName` field and the `subject:organizationName` field, the `subject:givenName` field, or the `subject:surname` field are present.
    - **Prohibited** if the `subject:organizationName` field, the `subject:givenName` field, or `subject:surname` field are absent.
- **Contents:** If present, the `subject:stateOrProvinceName` field must contain the Subject’s state or province information as verified under §3.2.2.1. If the `subject:countryName` field specifies the ISO 3166-1 user-assigned code of XX in accordance with §7.1.4.2.2(h), the `subject:stateOrProvinceName` field may contain the full name of the Subject’s country information as verified under §3.2.2.1.

###### g. Certificate Field: subject:postalCode (OID: 2.5.4.17)

- Required/Optional:
    - **Optional** if the subject:organizationName, `subject:givenName` field, or `subject:surname` fields are present.
    - **Prohibited** if the `subject:organizationName` field, `subject:givenName` field, or `subject:surname` field are absent.
- **Contents:** If present, the `subject:postalCode` field must contain the Subject’s zip or postal information as verified under §3.2.2.1.

###### h. Certificate Field: subject:countryName (OID: 2.5.4.6)

- Required/Optional:
    - **Required** if the `subject:organizationName` field, subject:givenName, or `subject:surname` field are present. It is always required for EV Server Certificates.
    - **Optional** if the `subject:organizationName` field, `subject:givenName` field, and `subject:surname` field are absent.
- **Contents for non-EV TLS or Code Signing:** If the `subject:organizationName` field is present, the `subject:countryName` must contain the two-letter ISO 3166-1 country code associated with the location of the Subject verified under §3.2.2.1. If the `subject:organizationName` field is absent, the `subject:countryName` field may contain the two-letter ISO 3166-1 country code associated with the Subject as verified in accordance with §3.2.2.3. If a Country is not represented by an official ISO 3166-1 country code, SSL.com may specify the ISO 3166-1 user-assigned code of XX indicating that an official ISO 3166-1 alpha-2 code has not been assigned.

###### i. Certificate Field: subject:organizationalUnitName (OID: 2.5.4.11)

- Required/Optional:
    - **Optional** for non-TLS certificates
    - **Prohibited** for Server TLS Certificates.

SSL.com shall implement a process that prevents an OU attribute from including a name, DBA, trade name, trademark, address, location, or other text that refers to a specific natural person or Legal Entity unless SSL.com has verified this information in accordance with §3.2 and the Certificate also contains subject:organizationName, subject:localityName, and `subject:countryName` attributes, also verified in accordance with §3.2.2.1.

###### j. Certificate Field: subject:organizationIdentifier (OID: 2.5.4.97)

- Required/Optional:
    - **Optional** for all types of certificates covered by this CP/CPS.
- **Contents:** If present, the `subject:organizationIdentifier` SHALL be encoded as a PrintableString or UTF8String, and it SHALL contain a Registration Reference to the Legal Entity assigned in accordance to the identified Registration Scheme. The Registration Reference SHOULD be unique where the Registration Scheme and jurisdiction provide unique identifiers.

###### k.  Other Subject Attributes

- Other attributes MAY be present within the subject field. If present, other attributes MUST contain information that has been verified by SSL.com.
- For Code Signing Certificates, SSL.com SHALL NOT include any Subject Distinguished Name attributes except as specified in §9.2

#### 7.1.4.3 Subject Information - Root Certificates and Subordinate CA Certificates

By issuing a Subordinate CA Certificate, SSL.com represents that it followed the procedure set forth in this CP/CPS to verify that, as of the Certificate’s issuance date, all of the Subject Information was accurate.

##### 7.1.4.3.1 Subject Distinguished Name Fields

###### a. Certificate Field: subject:commonName (OID 2.5.4.3)

- Required/Optional: **Required**
- **Contents:** This field MUST be present and the contents SHOULD be an identifier for the certificate such that the certificate’s Name is unique across all certificates issued by the issuing certificate.

###### b. Certificate Field: subject:organizationName (OID 2.5.4.10)

- Required/Optional: **Required**
- **Contents:** This field MUST be present and the contents MUST contain either the Subject CA’s name or DBA as verified under §3.2.2.2. SSL.com may include information in this field that differs slightly from the verified name, such as common variations or abbreviations, provided that SSL.com documents the difference and any abbreviations used are locally accepted abbreviations; e.g., if the official record shows “Company Name Incorporated”, SSL.com MAY use “Company Name Inc.” or “Company Name”.

###### c. Certificate Field: subject:countryName (OID: 2.5.4.6)

- Required/Optional: **Required**
- **Contents:** This field MUST contain the two-letter ISO 3166-1 country code for the country in which the CA’s place of business is located.

### 7.1.5 Name Constraints

SSL.com reserves the right to issue Certificates with name constraints and/or marked as critical when deemed necessary.

If SSL.com decides to apply Name Constraints and if the Subordinate CA Certificate includes the `id-kp-serverAuth` RFC 5280 extended key usage, then the Subordinate CA Certificate must include the Name Constraints X.509v3 extension with constraints on dNSName, iPAddress and DirectoryName as follows:

a. For each dNSName in permittedSubtrees, SSL.com must confirm that the Applicant has registered the dNSName or has been authorized by the domain registrant to act on the registrant's behalf in line with the verification practices of §3.2.2.4.
b. For each iPAddress range in permittedSubtrees, SSL.com must confirm that the Applicant has been assigned the iPAddress range or has been authorized by the assigner to act on the assignee's behalf.
c. For each DirectoryName in permittedSubtrees SSL.com must confirm the Applicant's and/or Subsidiary's Organizational name and location such that end entity Certificates issued from the subordinate CA Certificate will be in compliance with §7.1.2.4 and §7.1.2.5.

If the Subordinate CA Certificate is not allowed to issue Certificates with an iPAddress, then the Subordinate CA Certificate must specify the entire IPv4 and IPv6 address ranges in excludedSubtrees. The Subordinate CA Certificate must include within excludedSubtrees an iPAddress GeneralName of 8 zero octets (covering the IPv4 address range of 0.0.0.0/0). The Subordinate CA Certificate must also include within excludedSubtrees an iPAddress GeneralName of 32 zero octets (covering the IPv6 address range of ::0/0). Otherwise, the Subordinate CA Certificate must include at least one iPAddress in permittedSubtrees.

A decoded example for issuance to the domain and sub domains of example.com by organization: "Example LLC, Boston, Massachusetts, US" would be:

> X509v3 Name Constraints: \
> > Permitted: \
> > > DNS:example.com \
> > > DirName: C=US, ST=MA, L=Boston, O=Example LLC \
> > Excluded: \
> > > IP:0.0.0.0/0.0.0.0 \
> > > IP:0:0:0:0:0:0:0:0/0:0:0:0:0:0:0:0 \

If the Subordinate CA is not allowed to issue Certificates with dNSNames, then the Subordinate CA Certificate must include a zero-length dNSName in excludedSubtrees. Otherwise, the Subordinate CA Certificate must include at least one dNSName in permittedSubtrees.

### 7.1.6 Certificate Policy object identifier

The OID (Object Identifier) of this CP/CPS is documented in §1.2.1.

A special OID arc has been allocated by SSL.com based on a certain certificate type:

> iso (1) org (3) dod (6) internet (1) private (4) enterprise (1) SSL.com (38064) certificationServicesProvision (1) certificateTypes (3)

SSL.com issues Certificates containing the following OIDs / OID arcs:

| **Digitally Signed Object** | **Policy Object Identifier (OID)** |
| ------- | --- |
| **TLS Server Authentication Certificates** | **1.3.6.1.4.1.38064.1.3.1** |
| Domain Validation (DV) Policy, and IP address validation compatible with CA/B Forum Policy OID `2.23.140.1.2.1` | **1.3.6.1.4.1.38064.1.3.1.1** |
| Organization Validation (OV) Policy compatible with CA/B Forum Policy OID `2.23.140.1.2.2` | **1.3.6.1.4.1.38064.1.3.1.2** |
| Individual Validation (IV) Policy compatible with CA/B Forum Policy OID `2.23.140.1.2.3` | **1.3.6.1.4.1.38064.1.3.1.3** |
| NAESB Server Cert Medium Assurance compatible with CA/B Forum EV Policy OID `2.23.140.1.1` and NAESB Policy OID `2.16.840.1.114505.1.12.3.2.` | **1.3.6.1.4.1.38064.1.3.1.6** |
| **Code Signing Certificates** | **1.3.6.1.4.1.38064.1.3.3** |
| Minimum Requirements for Code Signing Policy, compatible with CA/B Forum Policy OID `2.23.140.1.4.1` | **1.3.6.1.4.1.38064.1.3.3.1** |
| Extended Validation (EV) Code Signing Policy, compatible with CA/B Forum Policy OID `2.23.140.1.3` | **1.3.6.1.4.1.38064.1.3.3.2** |
| **Client Authentication Certificates** | **1.3.6.1.4.1.38064.1.3.5** |
| Organization Validation (e.g. the full name of individual associated with a particular Organization, or just the Organization information) | **1.3.6.1.4.1.38064.1.3.5.1** |
| Individual Validation (e.g. the full name of individual only) | **1.3.6.1.4.1.38064.1.3.5.2** |
| Email Address validation only | **1.3.6.1.4.1.38064.1.3.5.7** |
| **Time-Stamping** | **1.3.6.1.4.1.38064.1.3.6** |
| Basic Time-Stamping, compatible with CA/B Forum Policy OID `2.23.140.1.4.2` | **1.3.6.1.4.1.38064.1.3.6.1** |
| EV Time-Stamping, compatible with CA/B Forum Policy OID `2.23.140.1.4.2` | **1.3.6.1.4.1.38064.1.3.6.2** |
| Time-stamping Certificate for Document Signing Trust | **1.3.6.1.4.1.38064.1.3.6.3** |
| OCSP Responder Certificate | **1.3.6.1.4.1.38064.1.3.7** |

These SSL.com custom Policy OIDs are used when Certificates are signed pursuant to this CP/CPS are indicated in the certificate's respective certificatePolicies extension. When a Certificate is issued containing a certain policy identifier which is indicated as compatible with the "CA/B Forum Policy OID X" or "NAESB Policy OID X", it asserts that the Certificate was issued and is managed in accordance with those applicable requirements AND the provisions of this CP/CPS.

Subordinate CAs that are Affiliated with SSL.com can use the reserved `AnyPolicy` OID **2.5.29.32.0**.

### 7.1.7 Usage of Policy Constraints extension

No stipulation

### 7.1.8 Policy qualifiers syntax and semantics

SSL.com's policy qualifier field includes information relying parties may consult in order to determine any limitations a certificate may have.

### 7.1.9 Processing semantics for the critical Certificate Policies extension

No stipulation

## 7.2 CRL Profile

### 7.2.1 Version Numbers

SSL.com's PKI issues version 2 CRLs which comply with RFC 5280 and contain the following:

- Issuer Signature Algorithm: The algorithm used to sign the CRL.
- Issuer Distinguished Name: The Distinguished Name of the Certification Authority that has signed and issued the CRL, matched byte-for-byte.
- thisUpdate: Issue date of the CRL in UTCTime or GeneralizedTime.
- nextUpdate: Date by which the next CRL will be issued in UTCTime or GeneralizedTime.
- Revocation list (Identified by certificate serial number): List of all revoked Certificates including their serial number and the date and time of the revocation in UTCTime or GeneralizedTime.
- Serial Number
- Issuer's Signature

### 7.2.2 CRL and CRL Entry Extensions

CRL and CRL Entry Extensions follow the requirements of section 5 of RFC 5280.

If a CRL has a thisUpdate field value of 2022-07-01 00:00:00 UTC or later and the CA includes the Invalidity Date CRL entry extension in a CRL entry for a Code Signing Certificate, then the time encoded in the Invalidity Date CRL extension SHALL be equal to the time encoded in the revocationDate field of the CRL entry.

#### 7.2.2.1 CRL Number

Sequentially increasing unique number for each CRL.

#### 7.2.2.2 Authority Key Identifier

The Authority Key Identifier of an issuing CA used for chaining and validation.

#### 7.2.2.3 Revocation `reasonCode` (OID 2.5.29.21)

If present, this extension MUST NOT be marked critical.

If a CRL entry is for a Root CA or Subordinate CA Certificate, including Cross Certificates technically capable of issuing TLS Certificates, this CRL entry extension MUST be present.

If a CRL entry is for a Certificate not technically capable of causing issuance, this CRL entry extension SHOULD be present, but MAY be omitted, subject to the following requirements.

The `CRLReason` indicated MUST NOT be unspecified (0). If the reason for revocation is unspecified, CAs MUST omit `reasonCode` entry extension, if allowed by the previous requirements.

If a CRL entry is for a TLS or a Code Signing Certificate, the `CRLReason` MUST NOT be certificateHold (6).
  
If a `reasonCode` CRL entry extension is present, the `CRLReason` MUST indicate the most appropriate reason for revocation of the certificate (see §4.9.1.1 and §4.9.1.2).

CRLReason MUST be included in the `reasonCode` extension of the CRL entry corresponding to a Subscriber TLS Server Certificate that is revoked after July 15, 2023, unless the CRLReason is "unspecified (0)". Revocation reason code entries for Subscriber TLS Server Certificates revoked prior to July 15, 2023, do NOT need to be added or changed.

Only the following CRLReasons MAY be present in the CRL `reasonCode` extension for Subscriber TLS or Code Signing Certificates:

- **keyCompromise (RFC 5280 CRLReason #1):** Indicates that it is known or suspected that the Subscriber’s Private Key has been compromised;
- **affiliationChanged (RFC 5280 CRLReason #3):** Indicates that the Subject's name or other Subject Identity Information in the Certificate has changed, but there is no cause to suspect that the Certificate's Private Key has been compromised;
- **superseded (RFC 5280 CRLReason #4):** Indicates that the Certificate is being replaced because: the Subscriber has requested a new Certificate, the CA has reasonable evidence that the validation of domain authorization or control for any fully‐qualified domain name or IP address in the Certificate should not be relied upon, or the CA has revoked the Certificate for compliance reasons such as the Certificate does not comply with these Baseline Requirements or the CA's CP or CPS;
- **cessationOfOperation (RFC 5280 CRLReason #5):** Indicates that the website with the Certificate is shut down prior to the expiration of the Certificate, or if the Subscriber no longer owns or controls the Domain Name in the Certificate prior to the expiration of the Certificate; or
- **privilegeWithdrawn (RFC 5280 CRLReason #9):** Indicates that there has been a subscriber-side infraction that has not resulted in keyCompromise, such as the Certificate Subscriber provided misleading information in their Certificate Request or has not upheld their material obligations under the Subscriber Agreement or Terms of Use.

The Subscriber Agreement, or an online resource referenced therein, MUST inform Subscribers of TLS or Code Signing Certificates about the revocation reason options listed above and provide explanation about when to choose each option. Tools that SSL.com provides to the Subscribers of TLS or Code Signing Certificates MUST allow for these options to be easily specified when the Subscriber requests revocation of their TLS or Code Signing Certificate, with the default value being that no revocation reason is provided (i.e. the default corresponds to the CRLReason “unspecified (0)” which results in no reasonCode extension being provided in the CRL).

The privilegeWithdrawn reasonCode SHOULD NOT be made available to the Subscriber as a revocation reason option, because the use of this reasonCode is determined by SSL.com and not the Subscriber.

When SSL.com obtains verifiable evidence of Key Compromise for a Certificate whose CRL entry does not contain a reasonCode extension or has a reasonCode extension with a non-keyCompromise reason, SSL.com SHOULD update the CRL entry to enter keyCompromise as the CRLReason in the reasonCode extension. Additionally, SSL.com SHOULD update the revocation date in a CRL entry when it is determined that the private key of the certificate was compromised prior to the revocation date that is indicated in the CRL entry for that certificate.

**Note:** Backdating the revocationDate field is an exception to best practice described in RFC 5280 (section 5.3.2); however, these requirements specify the use of the revocationDate field to support TLS and Code Signing implementations that process the revocationDate field as the date when the Certificate is first considered to be compromised.

#### 7.2.2.4 `issuingDistributionPoint` (OID 2.5.29.28)

If a CRL does not contain entries for all revoked unexpired certificates issued by the CRL issuer, then it MUST contain a critical Issuing Distribution Point extension and MUST populate the `distributionPoint` field of that extension.

## 7.3 OCSP Profile

SSL.com's PKI system operates an Online Certificate Status Profile (OCSP) responder in compliance with RFC 5019 and highlights this via an OCSP responder URL. OCSP version 1 defined by RFC 6960 is also supported.

If an OCSP response is for a Root CA or Subordinate CA Certificate, including Cross Certificates, and that certificate has been revoked, then the `revocationReason` field within the `RevokedInfo` of the `CertStatus` MUST be present.

The `CRLReason` indicated MUST contain a value permitted for CRLs, as specified in §7.2.2.3.

### 7.3.1 Version Numbers

SSL.com’s OCSP responders conform to version 1 of RFC 6960.

### 7.3.2 OCSP Extensions

The `singleExtensions` of an OCSP response MUST NOT contain the `reasonCode` (OID `2.5.29.21`) CRL entry extension.

The `singleExtensions` of an OCSP response MAY contain the `ArchiveCutOff` (OID `1.3.6.1.5.5.7.48.1.6`) as described in section 4.4.4 of RFC 6960 with values according to §4.10.1 of this CP/CPS.