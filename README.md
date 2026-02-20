# n8n-nodes-tribecrm

This is an [n8n](https://n8n.io/) community node for **[Tribe CRM](https://www.tribecrm.nl/)**.

Tribe CRM is a Dutch CRM platform that helps businesses manage their relationships, sales pipeline, tasks, and activities. This node lets you interact with the Tribe CRM API directly from your n8n workflows.

[n8n](https://n8n.io/) is a [fair-code licensed](https://docs.n8n.io/reference/license/) workflow automation platform.

---

## Resources

- [n8n community nodes documentation](https://docs.n8n.io/integrations/community-nodes/)
- [Tribe CRM API documentation](https://api.tribecrm.nl/swagger)

---

## Supported Resources & Operations

| Resource | Operations |
|---|---|
| **Appointment** | Create, Get Many |
| **Contact** | Create, Get Many |
| **Customer** | Create, Get Many, Update |
| **Employee** | Get Current, Get Many |
| **Invoice** | Get Many, Update Phase | ⚠️ Requires Billing module |
| **Lead** | Create, Get Many, Upgrade to Customer |
| **Organization** | Create, Delete, Get Many, Update |
| **Person** | Create, Delete, Get Many, Update |
| **Product** | Get Many |
| **Sales Opportunity** | Create, Get Many, Update |
| **Task** | Create |

All **Get Many** operations support standard OData query parameters: `$filter`, `$select`, `$expand`, `$orderby`, `$top` (limit), and `$skip` (pagination).

---

## Credentials

This node uses **OAuth2 Client Credentials** (service account / machine-to-machine flow). No user login is required.

You will need:

1. A **Client ID** and **Client Secret** — created in the Tribe CRM API Configuration page (Settings → API → Applications)
2. The **Access Token URL** for your environment:
   - Production: `https://auth.tribecrm.nl/oauth2/token`
   - Staging: `https://auth-staging.tribecrm.nl/oauth2/token`
3. The **API Base URL** for your environment:
   - Production: `https://api.tribecrm.nl`
   - Staging: `https://api-staging.tribecrm.nl`

### Setup

1. In n8n, go to **Credentials → New**
2. Search for **Tribe CRM OAuth2 API**
3. Fill in the Access Token URL, Client ID, Client Secret, and API Base URL
4. Click **Save** — n8n will automatically fetch and refresh tokens

---

## Installation

### n8n Cloud / self-hosted (GUI)

1. Go to **Settings → Community Nodes**
2. Enter `n8n-nodes-tribecrm` and install

### Self-hosted (npm)

```bash
npm install n8n-nodes-tribecrm
```

---

## Example: Sync a new lead from a form submission

```
Webhook → Tribe CRM (Create Person) → Tribe CRM (Create Lead)
```

1. Receive form data via Webhook node
2. Create a Person in Tribe CRM with the contact details
3. Create a Lead linked to the new person's organisation

---

## Compatibility

- Requires n8n **1.0.0** or later
- Uses the Tribe CRM OData API (`/v1/odata/`) and Webhooks API (`/v1/webhooks/`)

---

## Author

**Johann Norsa** — [Efficy](https://www.efficy.com/)
[johann.norsa@efficy.com](mailto:johann.norsa@efficy.com)

---

## License

[MIT](LICENSE.md)
