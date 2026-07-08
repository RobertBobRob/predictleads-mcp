# Installing the PredictLeads MCP Server

This is a **hosted, remote MCP server** — there is nothing to clone, build, or run locally. Setup is just registering the remote server with your MCP client and providing credentials.

## Server Details

- **Base URL:** `https://mcp.predictleads.com/`
- **Transport:** HTTP-based MCP connection
- **Authentication:** OAuth2 (Authorization Code or Client Credentials) or HTTP headers

## Step 1: Get Credentials

The user needs a PredictLeads API key and API token:

1. [Sign up](https://predictleads.com/sign_up) for a PredictLeads account (a free/public tier is available).
2. Retrieve the API key and API token from [Your Subscription Plans](https://predictleads.com/subscriptions).

## Step 2: Choose an Authentication Method

### Option A — HTTP Headers (simplest, recommended for most clients)

Register the server with these headers on every request:
X-Api-Key: {your_api_key}
X-Api-Token: {your_api_token}

### Option B — OAuth2 Authorization Code (with Dynamic Client Registration)

If the client supports Dynamic Client Registration, it can register automatically against the PredictLeads OAuth2 authorization endpoints — no manual client setup required.

### Option C — OAuth2 Client Credentials (server-to-server)

Use the following settings:

- Access Token URL: `https://oauth.predictleads.com/token`
- Client ID: `{your_api_key}`
- Client Secret: `{your_api_token}`

## Step 3: Register the Server

Add the PredictLeads MCP server to your client configuration using:

- URL: `https://mcp.predictleads.com/`
- Auth: one of the methods above

No local process, port, or environment variables are needed — the client connects directly over HTTP to the hosted endpoint.

## Step 4: Verify

Once connected, the client should list available PredictLeads tools (one per API endpoint, plus a schema-discovery tool covering the full OpenAPI spec). Test with a simple read-only call, e.g. looking up a company by domain, to confirm credentials are working.

## Limits

Each account has a monthly request limit based on its subscription plan. Exceeding it returns a `402` error. Usage can be tracked on [Your Subscription Plans](https://predictleads.com/subscriptions).

## Troubleshooting

- **401/403 errors:** Double-check the API key/token pair and that they're attached as headers (or used correctly in the OAuth2 flow).
- **402 errors:** The account has hit its monthly request limit; upgrade the plan or wait for the next billing cycle.
- **Further help:** [docs.predictleads.com/mcp_integration](https://docs.predictleads.com/mcp_integration) or PredictLeads support.
