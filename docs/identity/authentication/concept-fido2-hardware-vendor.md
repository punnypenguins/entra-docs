---
title: Microsoft Entra ID attestation for FIDO2 security key vendors
description: Explains requirements to prepare FIDO2 hardware for attestation with Microsoft Entra ID
ms.date: 07/15/2025
ms.service: entra-id
ms.subservice: authentication
author: justinha
ms.author: justinha
ms.reviewer: calui
ms.topic: conceptual
---

# Microsoft Entra ID attestation for FIDO2 security key vendors

FIDO2 security keys enable phishing-resistant authentication. They can replace weak credentials with strong hardware-backed public/private-key credentials that can't be reused, replayed, or shared across services. Security keys support shared device scenarios, allowing you to carry your credential with you and safely authenticate on any supported device.

In Microsoft Entra ID Authentication methods policy, administrators can enforce attestation for FIDO2 security keys. When **Enforce attestation** is set to **Yes**, Microsoft requires extra metadata from FIDO2 security keys that are registered with the tenant. As a vendor, your FIDO2 security key is usable when attestation is enforced, if the following requirements are met.

>[!NOTE]
>Microsoft Entra ID currently supports device-bound passkeys stored on FIDO2 security keys and in Microsoft Authenticator. Microsoft is committed to securing customers and users with passkeys. We're investing in both synced and device-bound passkeys for work accounts.

## Attestation requirements

Microsoft relies on the [FIDO Alliance Metadata Service (MDS)](https://fidoalliance.org/metadata/) to determine security key compatibility with Windows, Microsoft Edge browser, and online Microsoft accounts. Vendors report data to the FIDO MDS.

During FIDO2 registration, Microsoft Entra ID requires security keys to provide an attestation statement. For vendors, the expected attestation format is *packed*, as defined by [the FIDO standard](https://www.w3.org/TR/webauthn-2/#sctn-packed-attestation).

The specific requirements vary based on how an administrator configures the FIDO2 authentication methods policy.

| Enforce attestation set to Yes | Enforce attestation set to No |
|--------------------------------|-------------------------------|
|It must provide a valid *packed* attestation statement and a complete certificate that chains back to the attestation roots extracted from the FIDO Alliance MDS, so that Microsoft can validate the key's metadata.|It must provide a valid *packed* attestation statement (but Microsoft will ignore attestation verification results) and a complete certificate (which doesn't need to be associated with a particular certificate chain). |

>[!NOTE]
>Vendors are responsible to publish all root attestation certificates to the FIDO Alliance MDS; otherwise, attestation verification can fail.

Additionally, if attestation is enforced, the following requirements apply:
- Your authenticator needs to have a FIDO2 certification. This can be at *any* level. To learn more about the certification, visit the FIDO Alliance Certification Overview [website](https://fidoalliance.org/certification/). 
- Your product metadata needs to be uploaded to the FIDO Alliance MDS, and you need to verify your metadata is in the MDS. The metadata must indicate that your authenticator supports: 
  - FIDO 2.0 or higher. 
  - User verification or client PIN - Microsoft Entra ID requires user verification with biometrics or PIN for all FIDO2 authentication attempts.
  - Resident keys (or discoverable credentials) - Resident keys are required for using a security key to sign in to Microsoft Entra ID without entering a username.
  - Hash-Based Message Authenticator Codes (HMAC) secret extension or Pseudo-Random Function (PRF) extension - An HMAC secret extension or PRF extension is required for using a security key to unlock Windows in offline scenarios.

## Timelines
Microsoft ingests the latest version of the FIDO Alliance MDS every month. There may be a maximum four-week delay from the time that your FIDO2 security key appears in FIDO Alliance MDS to when Microsoft recognizes the key model. If your key meets the Microsoft attestation requirements, it automatically appears on the Microsoft FIDO2 partner page.

## FIDO2 security keys eligible for attestation with Microsoft Entra ID

The following table includes each FIDO2 security key model listed in MDS version 173 that's eligible for attestation with Microsoft Entra ID. For each model, the table shows its Authenticator Attestation Globally Unique Identifier (AAGUID) and feature capabilities. 

Description|AAGUID|Bio|USB|NFC|BLE
-----------|------|---------|-----|----|------
ACS FIDO Authenticator|50a45b0c-80e7-f944-bf29-f552bfa2e048|&#10060;|&#x2705;|&#10060;|&#10060;
ACS FIDO Authenticator Card|973446ca-e21c-9a9b-99f5-9b985a67af0f|&#10060;|&#10060;|&#x2705;|&#10060;
ACS FIDO Authenticator NFC|c89e6a38-6c00-5426-5aa5-c9cbf48f0382|&#10060;|&#x2705;|&#x2705;|&#10060;
Allthenticator Android App: roaming BLE FIDO2 Allthenticator for Windows, Mac, Linux, and Allthenticate door readers|5ca1ab1e-fa57-1337-f1d0-a117371ca702|&#x2705;|&#x2705;|&#10060;|&#10060;
Allthenticator iOS App: roaming BLE FIDO2 Allthenticator for Windows, Mac, Linux, and Allthenticate door readers|5ca1ab1e-1337-fa57-f1d0-a117e71ca702|&#x2705;|&#x2705;|&#10060;|&#10060;
Arculus FIDO 2.1 Key Card \[P71\]|3f59672f-20aa-4afe-b6f4-7e5e916b6d98|&#10060;|&#x2705;|&#10060;|&#10060;
Arculus FIDO2/U2F Key Card|9d3df6ba-282f-11ed-a261-0242ac120002|&#10060;|&#x2705;|&#10060;|&#10060;
ATKey.Card CTAP2.0|d41f5a69-b817-4144-a13c-9ebd6d9254d6|&#x2705;|&#10060;|&#10060;|&#10060;
ATKey.Card NFC|da1fa263-8b25-42b6-a820-c0036f21ba7f|&#x2705;|&#x2705;|&#x2705;|&#10060;
ATKey.Pro CTAP2.0|e1a96183-5016-4f24-b55b-e3ae23614cc6|&#x2705;|&#10060;|&#10060;|&#10060;
ATKey.Pro CTAP2.1|e416201b-afeb-41ca-a03d-2281c28322aa|&#x2705;|&#x2705;|&#10060;|&#10060;
ATKey.ProS|ba76a271-6eb6-4171-874d-b6428dbe3437|&#x2705;|&#x2705;|&#10060;|&#10060;
Atos CardOS FIDO2|1c086528-58d5-f211-823c-356786e36140|&#10060;|&#x2705;|&#x2705;|&#10060;
authenton1 - CTAP2.1|b267239b-954f-4041-a01b-ee4f33c145b6|&#10060;|&#x2705;|&#x2705;|&#10060;
CardOS FIDO2 Token|8da0e4dc-164b-454e-972e-88f362b23d59|&#10060;|&#x2705;|&#x2705;|&#10060;
Chunghwa Telecom FIDO2 Smart Card Authenticator|175cd298-83d2-4a26-b637-313c07a6434e|&#10060;|&#10060;|&#x2705;|&#10060;
Crayonic KeyVault K1 (USB-NFC-BLE FIDO2 Authenticator)|be727034-574a-f799-5c76-0929e0430973|&#x2705;|&#x2705;|&#x2705;|&#x2705;
Cryptnox FIDO2|9c835346-796b-4c27-8898-d6032f515cc5|&#10060;|&#10060;|&#x2705;|&#10060;
Cryptnox FIDO2.1|1d1b4e33-76a1-47fb-97a0-14b10d0933f1|&#10060;|&#10060;|&#x2705;|&#10060;
Deepnet SafeKey/Classic (NFC)|b12eac35-586c-4809-a4b1-d81af6c305cf|&#10060;|&#x2705;|&#x2705;|&#10060;
Egomet FIDO2 Authenticator for Android|1105e4ed-af1d-02ff-ffff-ffffffffffff|&#x2705;|&#10060;|&#10060;|&#10060;
Ensurity AUTH BioPro|454e5346-4944-4ffd-6c93-8e9267193e9b|&#x2705;|&#x2705;|&#10060;|&#10060;
Ensurity ThinC|454e5346-4944-4ffd-6c93-8e9267193e9a|&#x2705;|&#x2705;|&#10060;|&#10060;
eToken Fusion FIPS|050dd0bc-ff20-4265-8d5d-305c4b215192|&#10060;|&#x2705;|&#10060;|&#10060;
eToken Fusion NFC FIPS|10c70715-2a9a-4de1-b0aa-3cff6d496d39|&#10060;|&#10060;|&#x2705;|&#10060;
eToken Fusion NFC PIV|146e77ef-11eb-4423-b847-ce77864e9411|&#10060;|&#10060;|&#x2705;|&#10060;
eWBM eFA310 FIDO2 Authenticator|95442b2e-f15e-4def-b270-efb106facb4e|&#x2705;|&#10060;|&#10060;|&#10060;
eWBM eFA320 FIDO2 Authenticator|87dbc5a1-4c94-4dc8-8a47-97d800fd1f3c|&#x2705;|&#10060;|&#10060;|&#10060;
eWBM eFPA FIDO2 Authenticator|61250591-b2bc-4456-b719-0b17be90bb30|&#x2705;|&#10060;|&#10060;|&#10060;
Excelsecu eSecu FIDO2 Fingerprint Key|6002f033-3c07-ce3e-d0f7-0ffe5ed42543|&#x2705;|&#x2705;|&#10060;|&#10060;
Excelsecu eSecu FIDO2 Fingerprint Security Key|d384db22-4d50-ebde-2eac-5765cf1e2a44|&#x2705;|&#x2705;|&#10060;|&#10060;
Excelsecu eSecu FIDO2 Fingerprint Security Key|20f0be98-9af9-986a-4b42-8eca4acb28e4|&#x2705;|&#x2705;|&#10060;|&#10060;
Excelsecu eSecu FIDO2 NFC Security Key|fbefdf68-fe86-0106-213e-4d5fa24cbe2e|&#10060;|&#x2705;|&#x2705;|&#10060;
Excelsecu eSecu FIDO2 NFC Security Key|a3975549-b191-fd67-b8fb-017e2917fdb3|&#10060;|&#x2705;|&#x2705;|&#10060;
Excelsecu eSecu FIDO2 Pro Security Key|0d9b2e56-566b-c393-2940-f821b7f15d6d|&#10060;|&#x2705;|&#x2705;|&#x2705;
Excelsecu eSecu FIDO2 PRO Security Key|bbf4b6a7-679d-f6fc-c4f2-8ac0ddf9015a|&#10060;|&#x2705;|&#x2705;|&#x2705;
Excelsecu eSecu FIDO2 Security Key|cdbdaea2-c415-5073-50f7-c04e968640b6|&#10060;|&#x2705;|&#10060;|&#10060;
Feitian AllinOne FIDO2 Authenticator|12ded745-4bed-47d4-abaa-e713f51d6393|&#x2705;|&#x2705;|&#x2705;|&#x2705;
Feitian BioPass FIDO2 Authenticator|77010bd7-212a-4fc9-b236-d2ca5e9d4084|&#x2705;|&#x2705;|&#10060;|&#10060;
Feitian BioPass FIDO2 Plus (Enterprise Profile)|a02140b7-0cbd-42e1-a9b5-a39da2545114|&#x2705;|&#x2705;|&#10060;|&#10060;
Feitian BioPass FIDO2 Plus Authenticator|b6ede29c-3772-412c-8a78-539c1f4c62d2|&#x2705;|&#x2705;|&#10060;|&#10060;
Feitian BioPass FIDO2 Plus Authenticator|42df17de-06ba-4177-a2bb-6701be1380d6|&#x2705;|&#x2705;|&#10060;|&#10060;
Feitian BioPass FIDO2 Pro (Enterprise Profile)|2bff89f2-323a-48fc-b7c8-9ff7fe87c07e|&#x2705;|&#x2705;|&#10060;|&#10060;
Feitian BioPass FIDO2 Pro Authenticator|4c0cf95d-2f40-43b5-ba42-4c83a11c04ba|&#x2705;|&#x2705;|&#10060;|&#10060;
Feitian ePass FIDO Authenticator (CTAP2.1, CTAP2.0, U2F)|12755c32-8ad1-46eb-881c-e0b38d848b09|&#10060;|&#x2705;|&#10060;|&#10060;
Feitian ePass FIDO2 Authenticator|833b721a-ff5f-4d00-bb2e-bdda3ec01e29|&#10060;|&#x2705;|&#10060;|&#10060;
Feitian ePass FIDO2-NFC Authenticator|ee041bce-25e5-4cdb-8f86-897fd6418464|&#10060;|&#x2705;|&#x2705;|&#10060;
Feitian ePass FIDO2-NFC Series (CTAP2.1, CTAP2.0, U2F)|234cd403-35a2-4cc2-8015-77ea280c77f5|&#10060;|&#x2705;|&#x2705;|&#10060;
Feitian ePass FIDO-NFC (Enterprise Profile) (CTAP2.1, CTAP2.0, U2F)|39589099-9a75-49fc-afaa-801ca211c62a|&#10060;|&#x2705;|&#x2705;|&#10060;
Feitian ePass FIDO-NFC(CTAP2.1, CTAP2.0, U2F)|78ba3993-d784-4f44-8d6e-cc0a8ad5230e|&#10060;|&#x2705;|&#x2705;|&#10060;
Feitian iePass FIDO Authenticator|3e22415d-7fdf-4ea4-8a0c-dd60c4249b9d|&#10060;|&#x2705;|&#10060;|&#10060;
FIDO KeyPass S3|f4c63eff-d26c-4248-801c-3736c7eaa93a|&#10060;|&#x2705;|&#10060;|&#10060;
Foongtone FIDO Authenticator|46544d5d-8f5d-4db4-89ac-ea8977073fff|&#10060;|&#10060;|&#x2705;|&#10060;
FT-JCOS FIDO Fingerprint Card|8c97a730-3f7b-41a6-87d6-1e9b62bda6f0|&#10060;|&#10060;|&#x2705;|&#10060;
Google Titan Security Key v2|42b4fb4a-2866-43b2-9bf7-6c6669c2e5d3|&#10060;|&#x2705;|&#x2705;|&#10060;
GoTrust Idem Card FIDO2 Authenticator|9f0d8150-baa5-4c00-9299-ad62c8bb4e87|&#10060;|&#10060;|&#10060;|&#10060;
GoTrust Idem Key FIDO2 Authenticator|3b1adb99-0dfe-46fd-90b8-7f7614a4de2a|&#10060;|&#10060;|&#10060;|&#10060;
GSTAG OAK FIDO2 Authenticator|773c30d9-5919-4e96-a4f5-db65e95cf890|&#10060;|&#10060;|&#x2705;|&#10060;
HID Crescendo 4000|2a55aee6-27cb-42c0-bc6e-04efe999e88a|&#10060;|&#10060;|&#x2705;|&#10060;
HID Crescendo C2300|aeb6569c-f8fb-4950-ac60-24ca2bbe2e52|&#10060;|&#10060;|&#x2705;|&#10060;
HID Crescendo C3000|c80dbd9a-533f-4a17-b941-1a2f1c7cedff|&#10060;|&#10060;|&#x2705;|&#10060;
HID Crescendo Enabled|54d9fee8-e621-4291-8b18-7157b99c5bec|&#10060;|&#10060;|&#x2705;|&#10060;
HID Crescendo Fusion|c4ddaf11-3032-4e77-b3b9-3a340369b9ad|&#10060;|&#10060;|&#x2705;|&#10060;
HID Crescendo Key|692db549-7ae5-44d5-a1e5-dd20a493b723|&#10060;|&#x2705;|&#x2705;|&#10060;
HID Crescendo Key V2|2d3bec26-15ee-4f5d-88b2-53622490270b|&#10060;|&#x2705;|&#x2705;|&#10060;
HID Crescendo Key V3|7991798a-a7f3-487f-98c0-3faf7a458a04|&#10060;|&#x2705;|&#x2705;|&#10060;
Hideez Key 4 FIDO2 SDK|4e768f2c-5fab-48b3-b300-220eb487752b|&#10060;|&#x2705;|&#x2705;|&#x2705;
Hyper FIDO Bio Security Key|d821a7d4-e97c-4cb6-bd82-4237731fd4be|&#x2705;|&#10060;|&#10060;|&#10060;
Hyper FIDO Pro|9f77e279-a6e2-4d58-b700-31e5943c6a98|&#10060;|&#10060;|&#10060;|&#10060;
HYPR FIDO2 Authenticator|0076631b-d4a0-427f-5773-0ec71c9e0279|&#x2705;|&#10060;|&#10060;|&#10060;
IDCore 3121 Fido|e86addcd-7711-47e5-b42a-c18257b0bf61|&#10060;|&#10060;|&#x2705;|&#10060;
IDEMIA ID-ONE Card|8d1b1fcb-3c76-49a9-9129-5515b346aa02|&#10060;|&#x2705;|&#x2705;|&#10060;
IDmelon Android Authenticator|39a5647e-1853-446c-a1f6-a79bae9f5bc7|&#x2705;|&#10060;|&#10060;|&#10060;
IDmelon iOS Authenticator|820d89ed-d65a-409e-85cb-f73f0578f82a|&#x2705;|&#10060;|&#10060;|&#10060;
ID-One Card|bb405265-40cf-4115-93e5-a332c1968d8c|&#10060;|&#10060;|&#x2705;|&#10060;
IDPrime 3930 FIDO|ca4cff1b-5a81-4404-8194-59aabcf1660b|&#10060;|&#10060;|&#x2705;|&#10060;
IDPrime 3940 FIDO|b50d5e0a-7f81-4959-9b12-f45407407503|&#10060;|&#10060;|&#x2705;|&#10060;
IDPrime 931 Fido|2194b428-9397-4046-8f39-007a1605a482|&#10060;|&#10060;|&#x2705;|&#10060;
IDPrime 941 Fido|2ffd6452-01da-471f-821b-ea4bf6c8676a|&#10060;|&#10060;|&#x2705;|&#10060;
IIST FIDO2 Authenticator|4b89f401-464e-4745-a520-486ddfc5d80e|&#10060;|&#x2705;|&#10060;|&#10060;
ImproveID Authenticator|4c50ff10-1057-4fc6-b8ed-43a529530c3c|&#10060;|&#x2705;|&#x2705;|&#10060;
KEY-ID FIDO2 Authenticator|d91c5288-0ef0-49b7-b8ae-21ca0aa6b3f3|&#10060;|&#x2705;|&#10060;|&#10060;
KeyXentic FIDO2 Secp256R1 FIDO2 CTAP2 Authenticator|4b3f8944-d4f2-4d21-bb19-764a986ec160|&#x2705;|&#x2705;|&#10060;|&#10060;
KeyXentic FIDO2 Secp256R1 FIDO2 CTAP2 Authenticator|ec31b4cc-2acc-4b8e-9c01-bade00ccbe26|&#x2705;|&#x2705;|&#10060;|&#10060;
KONAI Secp256R1 FIDO2 Conformance Testing CTAP2 Authenticator|f7c558a0-f465-11e8-b568-0800200c9a66|&#x2705;|&#x2705;|&#x2705;|&#10060;
KX701 SmartToken FIDO|fec067a1-f1d0-4c5e-b4c0-cc3237475461|&#10060;|&#x2705;|&#x2705;|&#10060;
NEOWAVE Badgeo FIDO2|c5703116-972b-4851-a3e7-ae1259843399|&#10060;|&#x2705;|&#x2705;|&#10060;
NEOWAVE Winkeo FIDO2|3789da91-f943-46bc-95c3-50ea2012f03a|&#10060;|&#x2705;|&#10060;|&#10060;
Nitrokey 3 AM|2cd2f727-f6ca-44da-8f48-5c2e5da000a2|&#10060;|&#x2705;|&#10060;|&#10060;
NXP Semiconductros FIDO2 Conformance Testing CTAP2 Authenticator|07a9f89c-6407-4594-9d56-621d5f1e358b|&#10060;|&#10060;|&#10060;|&#10060;
Nymi FIDO2 Authenticator|0acf3011-bc60-f375-fb53-6f05f43154e0|&#x2705;|&#10060;|&#x2705;|&#10060;
OCTATCO EzFinger2 FIDO2 AUTHENTICATOR|a1f52be5-dfab-4364-b51c-2bd496b14a56|&#x2705;|&#10060;|&#10060;|&#10060;
OneSpan DIGIPASS FX1 BIO|30b5035e-d297-4ff1-b00b-addc96ba6a98|&#x2705;|&#x2705;|&#10060;|&#x2705;
OneSpan DIGIPASS FX1a|30b5035e-d297-4ff1-010b-addc96ba6a98|&#x2705;|&#x2705;|&#x2705;|&#10060;
OneSpan DIGIPASS FX7|30b5035e-d297-4ff7-b00b-addc96ba6a98|&#10060;|&#x2705;|&#10060;|&#10060;
OneSpan FIDO Touch|30b5035e-d297-4fc1-b00b-addc96ba6a97|&#10060;|&#x2705;|&#10060;|&#x2705;
OnlyKey Secp256R1 FIDO2 CTAP2 Authenticator|998f358b-2dd2-4cbe-a43a-e8107438dfb3|&#10060;|&#10060;|&#10060;|&#10060;
OpenSK authenticator|664d9f67-84a2-412a-9ff7-b4f7d8ee6d05|&#10060;|&#x2705;|&#10060;|&#10060;
Pone Biometrics OFFPAD Authenticator|69700f79-d1fb-472e-bd9b-a3a3b9a9eda0|&#x2705;|&#10060;|&#10060;|&#x2705;
Precision InnaIT Key FIDO 2 Level 2 certified|88bbd2f0-342a-42e7-9729-dd158be5407a|&#x2705;|&#x2705;|&#10060;|&#10060;
RSA Authenticator 4 for Android|59f85fe7-faa5-4c92-9f52-697b9d4d5473|&#x2705;|&#10060;|&#10060;|&#10060;
RSA Authenticator 4 for iOS|8681a073-5f50-4d52-bce4-e21658d207b3|&#x2705;|&#10060;|&#10060;|&#10060;
RSA DS100|7e3f3d30-3557-4442-bdae-139312178b39|&#10060;|&#x2705;|&#10060;|&#10060;
Safenet eToken FIDO|efb96b10-a9ee-4b6c-a4a9-d32125ccd4a4|&#10060;|&#x2705;|&#10060;|&#10060;
SafeNet eToken Fusion|74820b05-a6c9-40f9-8fb0-9f86aca93998|&#10060;|&#x2705;|&#10060;|&#10060;
SafeNet eToken Fusion CC|23786452-f02d-4344-87ed-aaf703726881|&#10060;|&#x2705;|&#10060;|&#10060;
Security Key by Yubico|f8a011f3-8c0a-4d15-8006-17111f9edc7d|&#10060;|&#x2705;|&#10060;|&#10060;
Security Key by Yubico|b92c3f9a-c014-4056-887f-140a2501163b|&#10060;|&#x2705;|&#10060;|&#10060;
Security Key by Yubico with NFC|149a2021-8ef6-4133-96b8-81f8d5b7f1f5|&#10060;|&#x2705;|&#x2705;|&#10060;
Security Key by Yubico with NFC|6d44ba9b-f6ec-2e49-b930-0c8fe920cb73|&#10060;|&#x2705;|&#x2705;|&#10060;
Security Key NFC by Yubico|b7d3f68e-88a6-471e-9ecf-2df26d041ede|&#10060;|&#x2705;|&#x2705;|&#10060;
Security Key NFC by Yubico|a4e9fc6d-4cbe-4758-b8ba-37598bb5bbaa|&#10060;|&#x2705;|&#x2705;|&#10060;
Security Key NFC by Yubico|e77e3c64-05e3-428b-8824-0cbeb04b829d|&#10060;|&#x2705;|&#x2705;|&#10060;
Security Key NFC by Yubico - Enterprise Edition|47ab2fb4-66ac-4184-9ae1-86be814012d5|&#10060;|&#x2705;|&#x2705;|&#10060;
Security Key NFC by Yubico - Enterprise Edition|ed042a3a-4b22-4455-bb69-a267b652ae7e|&#10060;|&#x2705;|&#x2705;|&#10060;
Security Key NFC by Yubico - Enterprise Edition|0bb43545-fd2c-4185-87dd-feb0b2916ace|&#10060;|&#x2705;|&#x2705;|&#10060;
Security Key NFC by Yubico - Enterprise Edition (Enterprise Profile)|9ff4cc65-6154-4fff-ba09-9e2af7882ad2|&#10060;|&#x2705;|&#x2705;|&#10060;
Security Key NFC by Yubico - Enterprise Edition (Enterprise Profile)|72c6b72d-8512-4c66-8359-9d3d10d9222f|&#10060;|&#x2705;|&#x2705;|&#10060;
Sentry Enterprises CTAP2 Authenticator|89b19028-256b-4025-8872-255358d950e4|&#x2705;|&#x2705;|&#10060;|&#x2705;
SHALO AUTH|57235694-51a5-4a4d-a81a-f42185df6502|&#10060;|&#x2705;|&#10060;|&#10060;
SI0X FIDO CL WRIST v1.0|912435d9-4a88-42f3-972d-1244b0d51420|&#10060;|&#10060;|&#x2705;|&#10060;
SmartDisplayer BobeePass FIDO2 Authenticator|516d3969-5a57-5651-5958-4e7a49434167|&#10060;|&#x2705;|&#x2705;|&#x2705;
Solo Secp256R1 FIDO2 CTAP2 Authenticator|8876631b-d4a0-427f-5773-0ec71c9e0279|&#10060;|&#10060;|&#10060;|&#10060;
Solo Tap Secp256R1 FIDO2 CTAP2 Authenticator|8976631b-d4a0-427f-5773-0ec71c9e0279|&#10060;|&#10060;|&#x2705;|&#10060;
Somu Secp256R1 FIDO2 CTAP2 Authenticator|9876631b-d4a0-427f-5773-0ec71c9e0279|&#10060;|&#10060;|&#10060;|&#10060;
StarSign FIDO Card|c89674e3-a765-4b07-888a-7c086fbdf04b|&#10060;|&#10060;|&#x2705;|&#10060;
StarSign Key Fob|f8d5c4e9-e539-4c06-8662-ec2a4155a555|&#x2705;|&#x2705;|&#x2705;|&#x2705;
Swissbit iShield Key 2|7787a482-13e8-4784-8a06-c7ed49a7aaf4|&#10060;|&#x2705;|&#x2705;|&#10060;
Swissbit iShield Key 2 Enterprise|e400ef8c-711d-4692-af46-7f2cf7da23ad|&#10060;|&#x2705;|&#x2705;|&#10060;
Swissbit iShield Key 2 FIPS|817cdab8-0d51-4de1-a821-e25b88519cf3|&#10060;|&#x2705;|&#x2705;|&#10060;
Swissbit iShield Key 2 FIPS Enterprise|5eaff75a-dd43-451f-af9f-87c9eeae293e|&#10060;|&#x2705;|&#x2705;|&#10060;
Swissbit iShield Key FIDO2|931327dd-c89b-406c-a81e-ed7058ef36c6|&#10060;|&#x2705;|&#10060;|&#10060;
Swissbit iShield Key Pro|5d629218-d3a5-11ed-afa1-0242ac120002|&#10060;|&#x2705;|&#x2705;|&#10060;
Taglio CTAP2.1 CS|092277e5-8437-46b5-b911-ea64b294acb7|&#10060;|&#10060;|&#x2705;|&#10060;
Taglio CTAP2.1 EP|7d2afadd-bf6b-44a2-a66b-e831fceb8eff|&#10060;|&#10060;|&#x2705;|&#10060;
Thales IDPrime FIDO Bio|4d41190c-7beb-4a84-8018-adf265a6352d|&#x2705;|&#10060;|&#x2705;|&#10060;
Token Ring 3 FIDO2 Authenticator|c62100de-759b-4bf8-b22b-63b3e3a80401|&#x2705;|&#10060;|&#x2705;|&#10060;
Token Ring FIDO2 Authenticator|91ad6b93-264b-4987-8737-3a690cad6917|&#x2705;|&#10060;|&#x2705;|&#10060;
TOKEN2 FIDO2 Security Key|ab32f0c6-2239-afbb-c470-d2ef4e254db7|&#10060;|&#10060;|&#10060;|&#10060;
TOKEN2 PIN Plus Security Key Series |eabb46cc-e241-80bf-ae9e-96fa6d2975cf|&#10060;|&#x2705;|&#x2705;|&#10060;
T-Shield TrustSec FIDO2 Bio and client PIN version|882adaf5-3aa9-4708-8e7d-3957103775b4|&#x2705;|&#x2705;|&#x2705;|&#10060;
uTrust FIDO2 Security Key|73402251-f2a8-4f03-873e-3cb6db604b03|&#10060;|&#x2705;|&#x2705;|&#10060;
VALMIDO PRO FIDO|5626bed4-e756-430b-a7ff-ca78c8b12738|&#x2705;|&#10060;|&#10060;|&#x2705;
VeriMark Guard Fingerprint Key|d94a29d9-52dd-4247-9c2d-8b818b610389|&#x2705;|&#10060;|&#10060;|&#10060;
VeroCard FIDO2 Authenticator|99ed6c29-4573-4847-816d-78ad8f1c75ef|&#10060;|&#10060;|&#10060;|&#x2705;
VinCSS FIDO2 Authenticator|5fdb81b8-53f0-4967-a881-f5ec26fe4d18|&#10060;|&#10060;|&#10060;|&#10060;
WiSECURE AuthTron USB FIDO2 Authenticator|504d7149-4e4c-3841-4555-55445a677357|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey 5 FIPS Series|73bb0cd4-e502-49b8-9c6f-b59445bf720b|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 FIPS Series|57f7de54-c807-4eab-b1c6-1c9be7984e92|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 FIPS Series (Enterprise Profile)|905b4cb4-ed6f-4da9-92fc-45e0d4e9b5c7|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 FIPS Series with Lightning|85203421-48f9-4355-9bc8-8a53846e5083|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 FIPS Series with Lightning|7b96457d-e3cd-432b-9ceb-c9fdd7ef7432|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 FIPS Series with Lightning (Enterprise Profile)|3a662962-c6d4-4023-bebb-98ae92e78e20|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 FIPS Series with NFC|fcc0118f-cd45-435b-8da1-9782b2da0715|&#10060;|&#x2705;|&#x2705;|&#10060;
YubiKey 5 FIPS Series with NFC|c1f9a0bc-1dd2-404a-b27f-8e29047a43fd|&#10060;|&#x2705;|&#x2705;|&#10060;
YubiKey 5 FIPS Series with NFC (Enterprise Profile)|79f3c8ba-9e35-484b-8f47-53a5a0f5c630|&#10060;|&#x2705;|&#x2705;|&#10060;
YubiKey 5 Series|19083c3d-8383-4b18-bc03-8f1c9ab2fd1b|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series|cb69481e-8ff7-4039-93ec-0a2729a154a8|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series|ee882879-721c-4913-9775-3dfcce97072a|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series|ff4dac45-ede8-4ec2-aced-cf66103f4335|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series (Enterprise Profile)|4599062e-6926-4fe7-9566-9e8fb1aedaa0|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series (Enterprise Profile)|20ac7a17-c814-4833-93fe-539f0d5e3389|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series with Lightning|c5ef55ff-ad9a-4b9f-b580-adebafe026d0|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series with Lightning|a02167b9-ae71-4ac7-9a07-06432ebb6f1c|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series with Lightning|24673149-6c86-42e7-98d9-433fb5b73296|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series with Lightning (Enterprise Profile)|b90e7dc1-316e-4fee-a25a-56a666a670fe|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series with Lightning (Enterprise Profile)|3b24bf49-1d45-4484-a917-13175df0867b|&#10060;|&#x2705;|&#10060;|&#10060;
YubiKey 5 Series with NFC|fa2b99dc-9e39-4257-8f92-4a30d23c4118|&#10060;|&#x2705;|&#x2705;|&#10060;
YubiKey 5 Series with NFC|2fc0579f-8113-47ea-b116-bb5a8db9202a|&#10060;|&#x2705;|&#x2705;|&#10060;
YubiKey 5 Series with NFC|d7781e5d-e353-46aa-afe2-3ca49f13332a|&#10060;|&#x2705;|&#x2705;|&#10060;
YubiKey 5 Series with NFC|a25342c0-3cdc-4414-8e46-f4807fca511c|&#10060;|&#x2705;|&#x2705;|&#10060;
YubiKey 5 Series with NFC (Enterprise Profile)|1ac71f64-468d-4fe0-bef1-0e5f2f551f18|&#10060;|&#x2705;|&#x2705;|&#10060;
YubiKey 5 Series with NFC (Enterprise Profile)|6ab56fad-881f-4a43-acb2-0be065924522|&#10060;|&#x2705;|&#x2705;|&#10060;
YubiKey Bio Series - FIDO Edition|d8522d9f-575b-4866-88a9-ba99fa02f35b|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - FIDO Edition|dd86a2da-86a0-4cbe-b462-4bd31f57bc6f|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - FIDO Edition|7409272d-1ff9-4e10-9fc9-ac0019c124fd|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - FIDO Edition (Enterprise Profile)|ad08c78a-4e41-49b9-86a2-ac15b06899e2|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - FIDO Edition (Enterprise Profile)|8c39ee86-7f9a-4a95-9ba3-f6b097e5c2ee|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - FIDO Edition (Enterprise Profile)|83c47309-aabb-4108-8470-8be838b573cb|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - Multi-protocol Edition|90636e1f-ef82-43bf-bdcf-5255f139d12f|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - Multi-protocol Edition|34744913-4f57-4e6e-a527-e9ec3c4b94e6|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - Multi-protocol Edition|7d1351a6-e097-4852-b8bf-c9ac5c9ce4a3|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - Multi-protocol Edition (Enterprise Profile)|6ec5cff2-a0f9-4169-945b-f33b563f7b99|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - Multi-protocol Edition (Enterprise Profile)|97e6a830-c952-4740-95fc-7c78dc97ce47|&#x2705;|&#x2705;|&#10060;|&#10060;
YubiKey Bio Series - Multi-protocol Edition 1VDJSN|58276709-bb4b-4bb3-baf1-60eea99282a7|&#x2705;|&#x2705;|&#10060;|&#10060;
ZTPass SmartAuth|b415094c-49d3-4c8b-b3fe-7d0ad28a6bc4|&#10060;|&#x2705;|&#x2705;|&#10060;

## Next steps

For more information about Microsoft Entra ID support for phishing-resistant authentication with FIDO2 security keys in browsers and native apps, see [FIDO2 compatibility](fido2-compatibility.md).
