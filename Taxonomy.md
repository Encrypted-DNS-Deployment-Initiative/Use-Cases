# Introduction

This area documents a common set of terminology to be referenced by the use cases, initially populated from Hugh Dixon's User Taxonomy (spotter's guide).

For each role, we will provide:

* Role identifier (with a prefix that reflects its broad category and legitimacy)
* Description

The first letter of the role identifier represents the category:
* I - Individual (acting for themselves)
* O - Organization (or individuals acting for the organization)
* D - Device (executing code defined by the software authors)

The second letter represents legitimacy:
* L - Legitimate (generally seen as good and valid in at least some contexts)
* D - Disputed (less consensus - wanted by some roles but not by others)
* I - Illegitimate (generally seen as something that should not be allowed)

## Note well

Users are very often more than one type, e.g.:
* Same device but both mobile and fixed-line broadband internet access customers
* Parent, employee and adult individual at different times of day.
* One man’s terrorist is another’s freedom fighter

Users have varying priorities between privacy, security and practicality, probably within the same day.


# Taxonomy

Role Identifier |Description
:--- | :---
IL-Child |	Child
IL-Teen	| Teenager, often rebellious
IL-Adult |	Adult
IL-Senior	| Senior Citizen
IL-Parent-9	| Parent of an under-10
IL-Parent-Multi	| Parent of multiple children; e.g. an X-year old and a Y-year old (where X < Y-3 and X < 9)
IL-Parent-Byod	| Parent whose kids have friends who bring devices
IL-Carer	| Adult with duty of care for other diminished-responsibility adult(s)
IL-Employee	| Employee acting for themselves with the consent of the employer but not supervised by them
OL-Employee	| Employee acting for the employer
OL-Admin	| Corporate network admin (generic)
OL-Admin-Financial	| Corporate network admin of financial company required to record employee communications
OL-Admin-Civil	| Non-profit organisation or civil sector network admin
OL-Guestprovider	| Commercial organisation with WiFi for site visitors/guests
IL-Whistleblower	| Employee reporting questionable activities of the employer to a benevolent regime
IL-Dissident	| Dissident in a repressive regime
II-Terrorist	| Terrorist in a benevolent regime
OL-Internetcafe	| Internet cafe owner
OL-Cafewifi	| Café with Wi-Fi owner
OL-Publicwifi	| Public Wi-Fi service operator (large number of hotspots)
OL-ISP-Designer	| ISP network designer that needs to consider traffic routing, capacity and cost
OL-CDN-Designer	| Content Delivery Network designer
OL-Public-DNS	| Public DNS service company, providing recursive resolution generally open to anyone on the internet
OL-Browser	| Browser (generalised internet access) software company
OL-App	| App (specific-use internet access) software company
OD-Tracker	| User-tracking or behaviour-driving company
II-Malware-author	| Malware author
II-Malware-controller	| Malware bot controller
OL-Threat-intel	| Internet/network threat-intelligence company
OL-Registrar	| Domain registrars and registries
II-Attacker-Onpath	| On-path attacker, illegitimate
II-Attacker-Offpath	| Off-path attacker, illegitimate
OL-Telco-Regulator	| Telco operator regulator
OL-Govt	| Elected government representative (non-repressive)
OD-Govt	| Pseudo- or un-elected government representative (mildly repressive)
OI-Govt	| Dictator’s apparatchik (definitely repressive)
OL-Govt-Security	| Governmental security agency (if overseen by OL-Govt)
OL-Govt-Datareg	| User Data protection regulator
OL-Thingco	| IoT device vendors
OL-Contentco	| Content owners
DL-Homedev	| IoT device placed in the home by the homeowner, performing legitimate functions
DD-Homedev	| IoT device placed in the home where its gamut of functions are either unclear or a mix of legitimate and illegitimate
DI-Homedev	| IoT device placed in the home performing illegitimate functions

