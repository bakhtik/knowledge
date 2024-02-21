# Consent string technicalities

## TC String Format

There are 3 distinct segments that are jointed together on a "dot" character:

- Core String: The core vendor transparency and consent details.
- Disclosed vendors (optional).
- Publisher TC: Publisher purposes transparency and consent for their pwn data uses (optional)

## The Core String

The fields are stored in big-endian format. Bit numberings are left-to-right.

| Field Name / Section Name 	| Description 	|
|-------------------------------|---------------|
| Version | Version number of the encoding format (2) |
| CmpId | Consent Management Platform ID that last updated the TC String |
| VendorListVersion | Version of the GVL used to create this TC String |
| TcfPolicyVersion | Version of policy used within GVL |
| SpecialFeatureOptIns | Opted in / Not opted in per each special feature |
| PurposesConsent | The user's consent value for each Purpose established on the legal basis of consent (Consent/No Consent) |
| PurposesLITransparency | The Purpose's transparency requirements are met for each Purpose on the legal basis of legitimate interest and the user has not exercised their "Right to Object" to that Purpose. By default purposes are set to zero. `1` legitimate interest established. `0` legitimate interest was **NOT** established or it was established but user exercised their "Right to Object" to the Purpose. | 
| Vendor Consent Section | List of vendors who have received consent from a user to process their personal data. |
| Vendor Legitimate Interest Section | The CMP has established transparency for that vendor's legitimate interest disclosures for one or more Purposes (includeing Special Purposes) | `1` Legitimate interest established. `0` Legitimate interest not established or the user exercised their "Right to Object" |

## Disclosed Vendors

The `DisclosedVendors` is an optional TC String segment that records which vendors have been disclosed to a given user by a CMP. It may be used by a CMP while storing TC Strings, but must not be included in the TC String when returned by the CMP API.

