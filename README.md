# Open Badges Events Caliper Metric Profiles
We propose creating a new Metric Profile to cover events related to Open Badges. Because of the distributed nature of the Open Badges ecosystem, a number of events that are critical to understanding how badges are related and how badges are being used are not naturally known to the relevant parties, including the Issuer. Common data reporting endpoints would make it possible to describe these events, process them, and share insights with relevant parties. The Actions described below are intended to cover a key set of these events that are often publicly knowable information that currently face this kind of discoverability hurdle.

## Entities

Property       | Data Type  | Description | Source
---------------|------------|-------------|----------
**Assertion**  |            |             | obi:Assertion
@id            | hosted IRI |             |
badge          | BadgeClass |             | obi:badge
**BadgeClass** |            |             | obi:BadgeClass
@id            | hosted IRI |             |
issuer         | Issuer     |             | obi:issuer
**Issuer**     |            |             | obi:Issuer
@id            | hosted IRI |             |

## Actions

Action | IRI | Description | New   |
-------|-----|------------ | ----- |
Defined | http://purl.imsglobal.org/caliper/actions/Defined | Defined a new BadgeClass or Issuer | Yes |
Issued  | http://purl.imsglobal.org/caliper/actions/Issued | Awarded an instance of a BadgeClass to a recipient, perhaps accepting an application | Yes
Demonstrated | http://purl.imsglobal.org/caliper/actions/Demonstrated | Recipient has met criteria for a BadgeClass and should be awarded a badge. | Yes
Modified | http://purl.imsglobal.org/caliper/actions/Modified | Modified or updated a previously defined badge object with new metadata | No
Revoked | http://purl.imsglobal.org/caliper/actions/Revoked | Updated a previously awarded badge to mark it as revoked | Yes
Deleted | http://purl.imsglobal.org/caliper/actions/Deleted | Marked a defined badge object as deleted | No
Registered | http://purl.imsglobal.org/caliper/actions/Registered | Registered a recipient profile with a backpack endpoint or issuer profile with issuer endpoint | Yes
Verified | http://purl.imsglobal.org/caliper/actions/Verified | Verified an Open Badge's authenticity and structural integrity | Yes
Shared | http://purl.imsglobal.org/caliper/actions/Shared | Triggered or authorized a share of a single badge, collection, or other document including badges | No
Endorsed | http://purl.imsglobal.org/caliper/actions/Endorsed | Issued an endorsement or annotation of an Issuer, BadgeClass, or Assertion that should be published | Yes
Accessed | http://purl.imsglobal.org/caliper/actions/Accessed | A consumer accessed and/or viewed badge details about a single Badge record | Yes
Accepted | http://purl.imsglobal.org/caliper/actions/Accepted | Inspected a badge or pathway with completion data and accepted it in exchange for some privilege, opportunity, access, or other benefit granted to the recipient. | Yes
Applied | http://purl.imsglobal.org/caliper/actions/Applied | User submits evidence to an issuer in hopes of earning a badge. | Yes
Assigned | http://purl.imsglobal.org/caliper/actions/Assigned | Set a goal for a prospective recipient to complete | Yes


## Open Badges Event

Event Attribute  | Required | Details | Comments
-----------------|----------|---------|---------
actor            | Yes      |         | Ideally, the actor describes an entity that participates in the Open Badges Ecosystem as an issuer
action           | Yes      |         | 
object           | Yes      |         | Generally a Badge Object (Assertion, BadgeClass or Issuer) or PathwayElement
generated        | No       |         | In the case of `Accepted` or `Endorsed`, the generated object may be a new Assertion
federatedSession | No       |         | 
edApp            | No       |         | 
group            | No       |         | 

# Proposed Open Badges Extension
Additionally, an Issuer should be able to specify preferred Caliper endpoints for external inspectors of their badge objects to publish badge events back to, to ensure the Issuer knows about them.

Example implementation in a badge object:
```json
{
  "ims:TBAcaliperApi": {
    "@context": "https://w3id.org/openbadges/extensions/caliper/context.json",
    "@id": "https://badgerank.com/caliper",
    "actions": ["Verified", "Shared", "Endorsed"]
  }
}
```