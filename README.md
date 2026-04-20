
# Android Userland Malicious App Threat Model Case Studies

> Not commonly found in the wild; more theoretical or research-oriented malicious app abuse paths.

| Vulnerability Type | Main Theme | Common Result | References |
|---|---|---|---|
| Arbitrary File Overwrite | Polluted SharedPreferences, vulnerable ContentProvider, Dirty Stream style overwrite paths | Config poisoning, app compromise, privilege escalation, account takeover | [LianKee/SO-CVEs](https://github.com/LianKee/SO-CVEs)<br>ACM Paper – Dirty Stream / Android File Overwrite Research<br>[Secsys-FDU/AF_CVEs/issues](https://github.com/Secsys-FDU/AF_CVEs/issues/)<br>[Microsoft Dirty Stream Attack](https://www.microsoft.com/en-us/security/blog/2024/05/01/dirty-stream-attack-discovering-and-mitigating-a-common-vulnerability-pattern-in-android-apps/) — research by Microsoft Threat Intelligence, credit to [ch0pin](https://github.com/Ch0pin/related_work) for foundational Dirty Stream research and prior work on the technique |
| Task Hijacking | Task stack abuse, exported activity misuse, UI trust abuse | Credential theft, auth interception, phishing → account takeover | [KMov-g/androidapps](https://github.com/KMov-g/androidapps) |
| Egress Phone Call EOP | Privileged telecom abuse, exported system component abuse, dialer intent misuse | Unauthorized calls, privilege escalation, restricted API access | [actuator/cve#privilege-escalation](https://github.com/actuator/cve#privilege-escalation) |

