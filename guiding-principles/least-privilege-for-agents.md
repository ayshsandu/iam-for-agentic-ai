# Principle: Least Privilege for Agents

The Principle of Least Privilege (PoLP) is a cornerstone of security, and it's even more critical for agentic AI. It means that an agent should only be granted the absolute minimum permissions necessary to perform its designated tasks, for the shortest duration possible.

**Why it's crucial for Agents:**
*   **Reduces Blast Radius:** If an agent is compromised, buggy, or makes an error, the potential damage is limited by its restricted permissions. An agent with "read-only" access can't delete data. An agent that can only access "customer_service_info" can't access "financial_records."
*   **Minimizes Attack Surface:** Fewer permissions mean fewer ways an attacker can exploit the agent.
*   **Enhances Trust:** Users and organizations are more likely to trust and adopt agents that demonstrably operate with minimal necessary authority.

**Applying PoLP to Agents:**
1.  **Granular Permissions:** Define fine-grained permissions rather than broad roles. Instead of "admin," think "can_read_user_profile," "can_update_contact_info," "can_initiate_payment_less_than_100."
2.  **Task-Scoped Access:** Permissions should ideally be tied to specific tasks the agent is performing. If an agent is summarizing a document, it doesn't need permission to send emails.
3.  **Time-Limited Access:** Credentials and permissions should expire. Use short-lived access tokens. For longer-running tasks, permissions might be granted only for the duration of that task.
4.  **Context-Aware Permissions:** Consider if permissions can be dynamically adjusted based on context (e.g., an agent might have more permissions when operating on a secure internal network versus externally).
5.  **Default Deny:** Agents should have no permissions by default. All access must be explicitly granted.
6.  **Regular Review:** Periodically review the permissions assigned to agents to ensure they are still necessary and appropriate.

Implementing PoLP requires careful design of the agent's tasks, the resources it interacts with, and the authorization mechanisms in place.