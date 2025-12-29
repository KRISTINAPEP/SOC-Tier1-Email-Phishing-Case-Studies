SOC Tier 1 Case Study: Email Phishing Virgin Media Spoof
SOC Tier 1 phishing email investigation including header analysis, authentication review, and redirect chain inspection.

Summary

Raw Email Details (Sanitized)

From: Impersonated sender identity (redacted)
Reply To: user@redacted domain.xyz
To: victim@example.com
Subject: Generic reply lure (redacted)
X Mailer: Open Xchange Mailer
X Originating IP: 93.177.119.241
Date: Tue 25 Nov 2025 04:28:07 +0000 (UTC)

Authentication Results
SPF: pass
DKIM: pass
DMARC: pass

Despite passing all authentication checks the Reply To domain is unrelated to Virgin Media and indicates malicious intent.

SOC Analysis

Incident Type
Phishing (Social Engineering)

Authentication Review
SPF: Pass
DKIM: Pass
DMARC: Pass

Key Indicators
Impersonated sender identity
Reply To domain mismatch
Redirect chain behind the call to action button
Social engineering lure titled Schedule Interview
Suspicious originating IP
Brand impersonation of Virgin Media

Risk
High response harvesting attempt

SOC Action
Escalated to Tier 2 for further investigation

Link Analysis

Anchor Text
SCHEDULE INTERVIEW

Actual Link <a>
https://tracking.icims.com/f/a/GYUHVdk98d9od2no7oqEwg~~/AAIB5hA~/

Behavior
The link routes through a tracking and redirect service
The final destination is obscured
The redirect chain is long and tokenized
Attackers commonly abuse legitimate redirect platforms to hide malicious endpoints

SOC Conclusion
High risk. The combination of redirect obfuscation impersonation and Reply To mismatch warrants escalation.

Investigation Notes
Sender identity spoofed to appear as Virgin Media
Authentication success does not confirm legitimacy
Redirect chain suggests concealment of final destination
Call to action designed to prompt immediate user action
Indicators collectively confirm malicious intent
Any user response would be delivered to an attacker controlled domain

Explanatory Commentary
Passing SPF DKIM and DMARC only confirms that the email was sent through a legitimate mail server. It does not validate the sender identity or intent.

Attackers frequently
compromise legitimate accounts
abuse trusted infrastructure
send phishing emails through reputable relays

The Reply To domain redacted domain.xyz is unrelated to Virgin Media and is the strongest indicator of malicious intent. The redirect chain behind the button further reinforces this conclusion.

Recommended Response Actions 
Block sender domain
Block Reply To domain
Report to security team for deeper analysis
Advise user not to respond or engage
Review logs for similar messages

SOC Tier 1 Action Plan

Isolation
Advised the user not to engage with the message or click any links.

Domain Reputation Check
Confirmed the Reply To domain has no legitimate association with the impersonated brand.

Blacklisting
Recommended blocking the sender domain and the Reply To domain at the email gateway.

Escalation
Escalated to Tier 2 for deep link analysis to determine the final redirect destination.

Disclaimer
This incident analysis is based on a real phishing email received by the author. All investigation analysis and response actions were performed in a personal non enterprise environment for educational and portfolio building purposes. Any domains email addresses or indicators referenced are limited to publicly observable attacker infrastructure. No confidential proprietary or organizational data is included.  
