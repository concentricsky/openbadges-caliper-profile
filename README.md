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
**PathwayElement** |        |             | pathways:PathwayElement
@id            | hosted IRI |             |
name           | xsd:string |             | schema:name
description    | xsd:string |             | schema:description
alignmentUrl   |            |             | schema:targetUrl

## Actions

Action              | IRI       | Description
--------------------|-----------|------------
DefinedIssuer       | TBA       | Defined a new Issuer Profile
DefinedBadge        | TBA       | Defined a new BadgeClass
IssuedBadge         | TBA       | Awarded an instance of a BadgeClass to a recipient, perhaps accepting an application
MetCriteria         | TBA       | Recipient has met criteria for a BadgeClass and should be awarded a badge.
Updated             | TBA       | Updated a previously defined badge object with new metadata
RevokedBadge        | TBA       | Updated a previously awarded badge to mark it as revoked
Deleted             | TBA       | Marked a defined badge object as deleted
Registered          | TBA       | Registered a recipient profile with a backpack endpoint or issuer profile with issuer endpoint
Requested           | TBA       | Requested a badge object or related resource from an issuer or repository
Verified            | TBA       | Verified an Open Badge's authenticity and structural integrity
Shared              | TBA       | Triggered or authorized a share of a single badge, collection, or other document including badges
Endorsed            | TBA       | Issued an endorsement or annotation of an Issuer, BadgeClass, or Assertion that should be published
Displayed           | TBA       | Displayed badge details on a single badge to a consumer
Accepted            | TBA       | Inspected a badge or pathway with completion data and accepted it in exchange for some privilege, opportunity, access, or other benefit granted to the recipient.
Applied             | TBA       | User submits evidence to an issuer in hopes of earning a badge.
AssignedToObjective | TBA       | Set BadgeClass as related to prospective opportunity, privilege, objective, learning pathway, skill or competency definition

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
