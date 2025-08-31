[Grype](https://github.com/anchore/grype) is used to scan all the vulnerabilities that exist in {{SITENAME}}. Some vulnerabilities reported by Grype are actually not present in {{SITENAME}}, and such vulnerabilities are known as **False Positive Vulnerabilities**. These vulnerabilities are not harmful.

Following is the list of critical-level false positive vulnerabilities reported by Grype:

| Vulnerability Id | Description | Reason |
|-----------------|------------|--------|
| CVE-2021-29940 | An issue was discovered in the through crate through 2021-02-18 for Rust. There is a double free (in through and through_and) upon a panic of the map function. | This vulnerability refers to a **through crate** in **Rust Programming Language**. {{SITENAME}} does not use **Rust** for development. |
| CVE-2016-0949 | Adobe Connect before 9.5.2 allows remote attackers to have an unspecified impact via a crafted parameter in a URL. | These vulnerabilities are present in **Adobe Connect** software. {{SITENAME}} does not use **Adobe Connect**. |
| CVE-2017-11291 | An issue was discovered in Adobe Connect 9.6.2 and earlier versions. A Server-Side Request Forgery (SSRF) vulnerability exists that could be abused to bypass network access controls. | (See above) |
| CVE-2018-12804 | Adobe Connect versions 9.7.5 and earlier have an Authentication Bypass vulnerability. Successful exploitation could lead to session hijacking. | (See above) |
| CVE-2018-12805 | Adobe Connect versions 9.7.5 and earlier have an Insecure Library Loading vulnerability. Successful exploitation could lead to privilege escalation. | (See above) |
| CVE-2018-4923 | Adobe Connect versions 9.7 and earlier have an exploitable OS Command Injection. Successful exploitation could lead to arbitrary file deletion. | (See above) |
| CVE-2021-40719 | Adobe Connect version 11.2.3 (and earlier) is affected by a Deserialization of Untrusted Data vulnerability to achieve arbitrary method invocation when AMF messages are deserialized on an Adobe Connect server. An attacker can leverage this to execute remote code execution on the server. | (See above) |
