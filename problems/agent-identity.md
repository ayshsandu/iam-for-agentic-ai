# Problem: Agent Identity - Who or What is the Agent?

One of the first questions in agentic AI IAM is: **What exactly *is* the agent we're trying to manage?**

Is it:
*   The underlying AI model?
*   The specific codebase of the agent?
*   A running instance of that code?
*   A particular task being executed by an instance?
*   An entity acting on behalf of a specific user?

**Why it's a problem:**
Without a clear, unique, and verifiable identity for an agent (or its operational context), it's impossible to:
*   Assign specific permissions to it.
*   Reliably audit its actions.
*   Hold it accountable.
*   Revoke its access if it misbehaves or is compromised.
*   Distinguish between multiple agents, or multiple instances of the same agent acting for different purposes or users.

**Considerations:**
*   **Granularity:** Do you need to identify the agent "type" (e.g., "InvoiceProcessingAgent v1.2") or a specific running "instance" (e.g., "InvoiceProcessingAgent_instance_XYZ_for_User_ABC")?
*   **Lifecycle:** How are agent identities created, updated (e.g., new versions), and eventually decommissioned?
*   **Verifiability:** How can other systems (or users) trust that an agent is genuinely the identity it claims?

Addressing agent identity is foundational to building any secure IAM framework for agentic systems.