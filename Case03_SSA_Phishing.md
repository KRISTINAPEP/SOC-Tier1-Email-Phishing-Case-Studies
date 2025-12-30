# Email Case 03 Social Security Administration Impersonation
SOC Tier 1 Phishing Investigation

---

**Summary**  
This email impersonates the U S Social Security Administration and attempts to lure the recipient into clicking a Download Now button. The message uses fake SSA branding failed authentication and a URL shortener to hide the final destination. The email originates from a residential ISP and instructs the user to download a secure PC app which SSA does not provide. These indicators confirm a high risk phishing attempt designed for malware delivery or credential harvesting.

---

## Raw Email Details Sanitized

From Social Services Administration <redacted sender>  
To redacted recipient  
Subject New Secure Document  
Date Wed 17 Dec 2025 19 30 50 PST  
X Originating IP 67 dot 69 dot 168 dot 64 Residential ISP  
Return Path <redacted sender>  
Content Type text html  
Content Transfer Encoding 7bit  

---

## Authentication Results

SPF fail  
DKIM unknown  
DMARC fail policy none  

**Definitions**  
SPF Validates whether the sending IP is authorized for the domain  
DKIM Confirms the message was not altered in transit  
DMARC Aligns SPF and DKIM with the From domain  

**Why this matters**  
- SPF fail indicates the sending IP is not authorized  
- DKIM unknown means no cryptographic proof of legitimacy  
- DMARC fail confirms the message is fraudulent  
- Residential IP is inconsistent with any U S government infrastructure  

---

## SOC Analysis

**Incident Type**  
Phishing involving government impersonation and possible malware delivery

**Key Indicators**  
- SPF fail  
- DMARC fail  
- DKIM unknown  
- Sender domain unrelated to SSA  
- Residential ISP source IP  
- Fake SSA branding  
- HTML Download Now button  
- URL shortener masking the destination  
- Urgent language  
- Instruction to download a secure PC app  

**Risk**  
High due to malware style download prompt and impersonation

**SOC Action**  
Escalated for deeper link analysis

---

## Link Analysis

**Anchor Text**  
Download Now

**Actual Link Sanitized**  
https colon slash slash ow dot ly slash redacted

**Behavior**  
- URL shortener hides the true destination  
- Likely redirects to malware or a credential harvesting page  
- Not associated with ssa dot gov  
- SSA does not distribute statements through downloadable apps  

**SOC Conclusion**  
This is a malicious link.  
The combination of impersonation URL shortener usage and a download prompt confirms phishing intent.

---

## Body Content Analysis

The email body is a styled HTML template impersonating the Social Security Administration.  
It includes

- SSA logo pulled from a legitimate SSA asset URL  
- Fake updated Social Security statement notice  
- Instruction to use a secure PC app  
- Prominent Download Now button  
- Footer claiming 2025 SSA GOV  

**Why this matters**  
Government agencies do not send statements via third party download links or require software installation.  
A download button is a strong malware indicator.

---

## Investigation Notes

- Sender domain is unrelated to SSA  
- SPF and DMARC both fail  
- Originating IP belongs to a residential ISP  
- HTML template mimics SSA branding but contains inconsistencies  
- URL shortener used to obscure the final payload  
- No legitimate SSA communication uses shortened links  
- Indicators collectively confirm malicious intent  

---

## Explanatory Commentary

Phishing campaigns frequently impersonate government agencies to increase credibility.  
In this case the attacker used a spoofed sender name a fraudulent HTML template a shortened URL and a malware style Download Now button.

Authentication failures combined with a residential source IP and a hidden redirect chain make this a clear phishing attempt.  
The email’s purpose is to deliver malware or harvest personal information under the guise of an SSA statement.

---

## Final Determination  
This email is a phishing attempt impersonating the Social Security Administration.  
The failed authentication results malicious download link spoofed branding and deceptive content confirm malicious intent.  
Escalation is appropriate due to the presence of a hidden redirect chain and a high risk malware delivery vector.
