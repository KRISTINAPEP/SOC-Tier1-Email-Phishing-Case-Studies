# SOC Tier 1 Case Study
Email Phishing Compromised Binus ac id Account

**Summary**  
This email originated from the legitimate domain binus ac id and passed SPF and DMARC but DKIM failed.  
The message contained a base64 encoded body and a malicious HTTP link pointing to a suspicious domain tunt bxrosadc com.  
These indicators strongly suggest a compromised account being used to deliver phishing content.

**Raw Email Details Sanitized**  
From Redacted sender at binus ac id  
To Redacted recipient  
Subject Update news  
Date Tue 23 Dec 2025 14 13 23 UTC  
X Originating IP 52 dot 101 dot 127 dot 92 Microsoft outbound protection  
Content Transfer Encoding base64  

**Authentication Results**  
SPF pass  
DKIM perm fail  
DMARC pass policy none  

**SOC Analysis**

**Incident Type**  
Phishing involving a compromised account

**Key Indicators**  
DKIM perm fail  
Base64 encoded body  
Suspicious HTTP link  
Display name mismatch  
Originating IP from Microsoft relay  
Unrelated sender identity  
Social engineering lure referencing images  

**Risk**  
High due to malicious link and compromised account behavior

**SOC Action**  
Escalated for deeper link analysis

**Link Analysis**

**Anchor Text**  
http colon slash slash www dot tunt dot bxrosadc dot com slash

**Actual Link Sanitized**  
http colon slash slash www dot tunt dot bxrosadc dot com slash

**Behavior**  
Plain HTTP with no encryption  
Suspicious domain bxrosadc com  
Randomized subdomain tunt  
Not associated with binus ac id  
Likely part of a malware or credential harvesting chain  

**SOC Conclusion**  
This is a malicious link.  
Combined with DKIM failure and a compromised sender this confirms phishing intent.

**Base64 Body Analysis**  
The email body was encoded in base64.  
This hides readable content and is often used to bypass keyword based filters.  
It is common in low effort phishing or compromised account activity.

**Sanitized decoded snippet**  
Forwarded message  
Images available to view

**Why this matters**  
Legitimate organizations rarely send plain text emails where the entire body is base64 encoded.  
Attackers frequently do this to hide malicious content.

**Investigation Notes**  
Sender identity does not match typical domain usage  
DKIM perm fail contradicts SPF and DMARC pass  
Base64 body is unnecessary for a simple text email  
Malicious link present in the body  
Domain unrelated to sender  
Microsoft relay IP suggests compromised O365 account  
Social engineering lure referencing images  
Indicators collectively confirm malicious intent  

**Explanatory Commentary**  
Passing SPF and DMARC only confirms the email was sent through an authorized server.  
It does not confirm the sender identity or intent.

DKIM perm fail is a critical indicator because  
the message was altered  
the signature did not match  
the sender identity cannot be trusted  

Combined with a malicious link and a base64 encoded body this strongly suggests the account was compromised and used to distribute phishing content.

**Final Determination**  
This email is a phishing attempt delivered through a compromised binus ac id account.  
The DKIM failure malicious link base64 encoded body and suspicious content confirm malicious intent.  
Escalation is appropriate due to the presence of a live malicious URL and authentication anomalies.

**SOC Tier 1 Action Plan**

**Isolation**  
Advised the user not to engage with the message or click any links.

**Domain Reputation Check**  
Confirmed the link domain and sender behavior do not align with legitimate binus ac id activity.

**Blacklisting**  
Recommended blocking the sender domain and the malicious link domain at the email gateway.

**Escalation**  
Escalated for deeper link analysis.

**Disclaimer**  
This incident analysis is based on a real phishing email received by the author.  
All investigation analysis and response actions were performed in a personal non enterprise environment for educational and portfolio building purposes.  
Any domains email addresses or indicators referenced are limited to publicly observable attacker infrastructure.  
No confidential proprietary or organizational data is included.
