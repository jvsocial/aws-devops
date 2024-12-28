---
layout: post
title:  "Blue/Green Deployments: Quick Study Notes"
date:   2024-12-28 14:59:21 +0000
categories: jekyll update
---
**Blue/Green Deployments: Quick Study Notes**

**Core Concept:** Two identical environments (Blue = Live, Green = New Version). Deploy to Green, test, switch traffic.

**Why Blue/Green?**

*   **Zero Downtime:** Near-instantaneous switch.
*   **Reduced Risk:** Easy rollback to Blue if needed.
*   **Simple Rollbacks:** Just switch traffic back.
*   **Improved Testing:** Production-like environment for testing.

**How it Works (Steps):**

1.  **Set up:** Two identical environments (Blue & Green).
2.  **Deploy:** Deploy new version to Green.
3.  **Test:** Thorough testing in Green.
4.  **Switch Traffic:** Redirect traffic from Blue to Green (Load balancer, DNS).
5.  **Monitor:** Watch Green closely after the switch.
6.  **Repurpose:** Blue becomes the new Green for the next deployment.

**When to Use:**

*   **Frequent Releases:** Ideal for continuous delivery.
*   **Critical Apps:** Where downtime is unacceptable.
*   **Complex Deployments:** Simplifies complex updates.

**When NOT to Use (Consider Alternatives):**

*   **Limited Resources:** Requires double the infrastructure.
*   **Complex Database Migrations:** Backward compatibility is key; requires careful planning.
*   **Stateful Applications:** Requires strategies for state/session management.

**Key Considerations (Questions to Ask):**

*   **Cost:** Can you afford the extra infrastructure?
*   **Complexity:** Is the application complex enough to justify it?
*   **Downtime Tolerance:** How much downtime is acceptable?
*   **Rollback Needs:** How important is quick rollback?

**Post-Switch Actions:**

*   **Monitor:** Closely monitor the new Green environment.
*   **Blue Environment:** Keep Blue as backup (short-term) or repurpose it as the new Green.

**Common Questions & Answers:**

*   **Database Migrations:** Use backward-compatible changes; techniques like schema versioning.
*   **Stateful Apps:** Use session replication, shared storage, or similar methods.
*   **Automation:** Use load balancers, DNS, CI/CD tools to automate the switch.
*   **Blue/Green Naming:** Just a convention; any two names work (A/B, Red/Black).
*   **Deployment to Green Fails:** Fix the issue in Green and redeploy; Blue remains live.

**In essence:** Blue/Green is about minimizing disruption during deployments by having a ready standby environment.
