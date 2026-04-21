
# Android Malicious App Threat Model Bulk CVE Case Studies

> Focused on userland Android vulnerabilities involving non-system* apps with emphasis on recurring exploitation patterns, privilege escalation paths & trust boundary failures.

| Vulnerability Type | Main Theme | Common Result | References |
|---|---|---|---|
| Dirty Stream Attack (Arbitrary File Overwrite → Remote Code Execution) | `DISPLAY_NAME` / `_display_name` abuse, unsafe `ContentResolver.query()` trust, attacker-controlled filename → path traversal overwrite | Internal file overwrite, config poisoning, privilege escalation, account takeover | [Secsys-FDU/AF_CVEs/issues](https://github.com/Secsys-FDU/AF_CVEs/issues/)<br>[Microsoft Dirty Stream Attack](https://www.microsoft.com/en-us/security/blog/2024/05/01/dirty-stream-attack-discovering-and-mitigating-a-common-vulnerability-pattern-in-android-apps/) with foundational Dirty Stream research credited to [ch0pin](https://github.com/Ch0pin/related_work) |
| Arbitrary File Overwrite (AFO) | SharedPreferences pollution, vulnerable `ContentProvider`, cross-layer exploitation, config poisoning, unsafe internal file handling | App compromise, privilege escalation, account takeover, code execution chains | [LianKee/SO-CVEs](https://github.com/LianKee/SO-CVEs)<br>ACM Paper: Android File Overwrite Research |
| Task Hijacking | Task stack abuse, exported activity misuse, UI trust abuse | Credential theft, auth interception, phishing → account takeover | [KMov-g/androidapps](https://github.com/KMov-g/androidapps) |
| Egress Phone Call EOP | Privileged telecom abuse, exported system component abuse, dialer intent misuse | Unauthorized calls, privilege escalation, restricted API access | [actuator/cve#privilege-escalation](https://github.com/actuator/cve#privilege-escalation) |

A large part of my methodology for identifying Android trust boundary failures & privilege escalation paths was heavily influenced by Ryan Johnson’s prior research on preinstalled and privileged Android app exploitation.

___________

###

A recurring pattern in Android CVEs published by **fxizenta (VulDB User)** is hard-coded trusted backend credentials.

Keys:
`SEGMENT_WRITE_KEY`, `SegmentWriteKey`, `UPLOADCARE_PRIVATE_KEY`

Examples:

> “Such manipulation of the argument `SEGMENT_WRITE_KEY` leads to use of hard-coded cryptographic key.”

> “Such manipulation of the argument `UPLOADCARE_PRIVATE_KEY` leads to use of hard-coded cryptographic key.”

CVEs:
CVE-2026-5452, CVE-2026-5453, CVE-2026-5454, CVE-2026-5455, CVE-2026-5458, CVE-2026-5462

Primitive:

> embedded trusted credential → APK extraction → attacker-controlled requests treated as legitimate
