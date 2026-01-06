# SOC Tier 1 Case Study: Virgin Media Email Phishing and Sender Spoofing

SOC Tier 1 phishing email investigation including authentication review and redirect chain inspection.

## Summary

A phishing email impersonating Virgin Media was received by a user. The message attempted to harvest responses by using a fake interview scheduling lure and a malicious Reply To address. Despite passing SPF DKIM and DMARC checks the message contained multiple high confidence indicators of phishing and was escalated for further analysis.

## Raw Email Details (Sanitized)

From: Impersonated sender identity (redacted)  
Reply To: user@redacted domain.xyz  
To: victim@example.com  
Subject: Generic reply lure (redacted)  
X Mailer: Open Xchange Mailer  
X Originating IP: 93 dot 177 dot 119 dot 241  
Date: Tue 25 Nov 2025 04:28:07 +0000 (UTC)

## Authentication Results

SPF: pass  
DKIM: pass  
DMARC: pass  

Despite passing all authentication checks the Reply To domain is unrelated to Virgin Media and indicates malicious intent.

## SOC Analysis

Incident Type: Phishing (Social Engineering)

### Authentication Review

SPF: Pass  
DKIM: Pass  
DMARC: Pass  

Authentication success indicates the email was sent through a server permitted by the sender domain but it does not validate the true sender identity or intent.

### Key Indicators

- Impersonated sender identity claiming to be Virgin Media  
- Reply To domain mismatch from the impersonated brand  
- Redirect chain behind the call to action button  
- Social engineering lure titled Schedule Interview  
- Suspicious originating IP  
- Brand impersonation of Virgin Media  

Risk: High response harvesting attempt

SOC Action: Escalated to Tier 2 for further investigation

## Link Analysis

Anchor Text: SCHEDULE INTERVIEW  

Actual Link:  
https://tracking.icims.com/f/a/GYUHVdk98d9od2no7oqEwg~~/AAIB5hA~/

### Behavior

The link routes through a tracking and redirect service. The final destination is obscured and the redirect chain is long and tokenized. Attackers commonly abuse legitimate redirect platforms to hide malicious endpoints and to bypass basic link based filtering.

## SOC Conclusion

High risk. The combination of redirect obfuscation brand impersonation and Reply To mismatch warrants escalation. Any user response would be delivered to an attacker controlled mailbox.

## Investigation Notes

Sender identity was spoofed to appear as Virgin Media.  
Authentication success does not confirm legitimacy or safety.  
The redirect chain suggests concealment of the final destination.  
The call to action is designed to prompt immediate user response.  
Indicators collectively confirm malicious intent and response harvesting.

## False Positive Consideration

At first glance the message could appear legitimate because it passes SPF DKIM and DMARC and uses a well known tracking and redirect service. In a real environment both of these factors might reduce suspicion during initial triage. However the Reply To domain does not match Virgin Media the sender identity is impersonated and the redirect behavior intentionally obscures the final destination. These higher value indicators outweigh the initial signs of legitimacy and support a phishing classification instead of treating this as a false positive.

## Explanatory Commentary

Passing SPF DKIM and DMARC only confirms that the email was sent through a legitimate mail server authorized by the sending domain. It does not validate the authenticity of the display name brand or the intent of the message.

Attackers frequently compromise legitimate accounts abuse trusted infrastructure and send phishing emails through reputable relays. This is why authentication results must be considered alongside content indicators header details and redirect behavior.

The Reply To domain redacted domain.xyz is unrelated to Virgin Media and is the strongest indicator of malicious intent in this case. The redirect chain behind the button further reinforces this conclusion by hiding the final destination behind multiple tokenized hops.

## Recommended Response Actions

- Block sender domain where appropriate  
- Block Reply To domain at the email gateway  
- Report to the security team for deeper analysis  
- Advise user not to respond or engage  
- Review logs for similar messages or campaigns  

## SOC Tier 1 Action Plan

Isolation: Advised the user not to engage with the message or click any links.

Domain Reputation Check: Confirmed the Reply To domain has no legitimate association with the impersonated brand.

Blacklisting: Recommended blocking the sender domain and the Reply To domain at the email gateway.

Escalation: Escalated to Tier 2 for deep link analysis to determine the final redirect destination and to identify any additional related messages.

## Evidence Handling Note

Full raw email headers and a line by line header interpretation for this case are maintained in a separate private repository. These materials are available upon request for hiring managers or technical reviewers who wish to review deeper technical analysis and evidence level reasoning.

## Disclaimer

This incident analysis is based on a real phishing email received by the author. All investigation analysis and response actions were performed in a personal non enterprise environment for educational and portfolio building purposes. Any domains email addresses or indicators referenced are limited to publicly observable attacker infrastructure. No confidential proprietary or organizational data is included.

