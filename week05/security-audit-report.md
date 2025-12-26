Security Audit Report

System: Ubuntu Linux Server (127.20.10.7)
Operating System: Ubuntu Linux (Server edition)
Audit Date: 19 December 2024
Auditor: oba23592328

Executive Summary

This report documents a comprehensive security audit of an Ubuntu Linux server system hosted at IP address 127.20.10.7. The audit used the Lynis security auditing tool to assess system hardening, identify security warnings, and evaluate compliance with security best practices. Targeted hardening actions were implemented and the audit was re-run to assess their impact.

Key Findings:

Initial hardening index: 68 / 100

Final hardening index: 68 / 100

Improvement: 0 points (0% increase)

Critical vulnerabilities addressed: 2

Services minimised: 0

Although the hardening index did not increase numerically, all identified Lynis warnings were successfully resolved, resulting in an improved security posture.

Audit Methodology
Tools and Techniques

Lynis – Comprehensive system security audit

Manual review – Review of Lynis warnings and configuration impact

Log analysis – Comparison of pre- and post-hardening audit logs

Scope

Operating system configuration

System hardening

Security warnings and recommendations

Logging and audit verification

Initial Security Assessment
Lynis Initial Audit Results

Hardening index: 68 / 100

Total tests performed: 265

Warnings identified: 2

Suggestions made: Multiple

Critical Issues Identified

Unresolved security warnings
Lynis reported two warnings indicating incomplete security hardening, which could expose the system to avoidable risks.

Best-practice recommendations not fully applied
Several optional Lynis recommendations had not yet been implemented, reducing defence-in-depth protection.

Security Hardening Implemented
Lynis Warning Remediation

✓ Reviewed all Lynis warnings

✓ Applied recommended configuration changes

✓ Verified changes using a post-hardening audit

Impact:
All previously reported Lynis warnings were eliminated.

Post-Hardening Assessment
Lynis Final Audit Results

Hardening index: 68 / 100

Total tests performed: 265

Warnings resolved: 2

Remaining warnings: 0

Comparison Analysis
Metric	Initial	After Hardening	Improvement
Hardening Index	68 / 100	68 / 100	No change
Warnings	2	0	Reduced by 2
Suggestions	Multiple	Fewer	Reduced
Tests Performed	265	265	No change
Most Impactful Improvements

Complete removal of all Lynis security warnings

Improved compliance with system hardening best practices

Verification of security improvements through repeat auditing

Remaining Risks and Limitations
Accepted Risks

Hardening index unchanged

Justification: Lynis scoring is weighted; not all fixes result in a higher index score.

Mitigation: All identified warnings were resolved.

Optional recommendations not fully implemented

Justification: Some suggestions are contextual or low risk for this environment.

Mitigation: Recommendations documented for future improvement.

Recommendations for Future Improvement

Implement remaining Lynis suggestions where appropriate

Introduce additional security monitoring tools

Perform periodic security re-audits

Security Control Verification

All implemented security controls were verified as functional on 19 December 2024:

[✓] Lynis audit execution

[✓] Warning remediation

[✓] Audit log comparison and validation

Conclusion

This security audit successfully identified and resolved two security warnings, improving the system’s overall security posture. While the Lynis hardening index remained at 68 / 100, the elimination of all warnings demonstrates a meaningful reduction in security risk.

The most significant improvements were achieved through:

Targeted remediation of Lynis warnings

Validation via post-hardening auditing

Consistent logging and comparison of results

The system is now better aligned with recognised security best practices and provides a stronger baseline for future hardening.
