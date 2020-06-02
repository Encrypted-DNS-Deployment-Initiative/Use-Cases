## Coffee Shop use case

### Assumptions:   Captive portal
- Coffee shop may wish to filter some content, eg pornography
- Hotel likely to be more proactive in its approach, eg in order to enforce possible data limits, premium options for faster connections etc
- Hotel might go as far as blocking well known cloud DNS sites (whether Do53, DoT or DoH) in order to enforce local policies

### Connecting 
- On trying to connect, a user with anything other than basic Do53 might fail as wont reach the landing page for authentication
- If DoT / DoH selected, might work depending whether fails open or closed, ie if reverts to Do53 if unable to connect to chosen resolver, ditto cloud DNS on Do53. 
 
- If fails open and connects, resulting service may appear slow if every subsequent DNS request tries to revert to DoT / DoH first
 
### UI Feedback to user 
A client UI that states the DNS being used (a la HTTPS padlock) would simplify fault finding in this scenario
 
***
## Development History 
Use case discussion on Split-DNS situations.  Originally developed during EDDI virtual session on 5/13/2020
