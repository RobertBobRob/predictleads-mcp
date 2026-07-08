# PredictLeads MCP Server

The PredictLeads MCP (Model Context Protocol) server lets AI agents access PredictLeads data and services directly. It exposes a structured way to interact with the PredictLeads API and retrieve all information available through it.

Every tool maps to an individual PredictLeads API endpoint with the same available parameters. One additional tool exposes the full OpenAPI schema, so an AI agent can determine which tool to use — and how — for a given prompt.

PredictLeads provides company intelligence data: technology detections, job openings, financing events, SEC filings, GitHub repositories, product launches, company connections, and more.

## Base URL

https://mcp.predictleads.com/

This is a hosted, remote MCP server — no local installation or code is required to run it. Clients connect directly to the base URL above.

## Getting Access

To use the PredictLeads MCP Server, either:

- Authorize your application via OAuth2, or
- [Sign up](https://predictleads.com/sign_up) for a public account and provide your API credentials as HTTP headers.

Your API key and token are available on the [Your Subscription Plans](https://predictleads.com/subscriptions) page.

## Authentication

The MCP Server supports two authentication methods.

### With OAuth2

PredictLeads supports two OAuth2 flows:

- **Authorization Code** — for OAuth2 clients that support [Dynamic Client Registration](https://oauth.net/2/dynamic-client-registration/) for automatic setup.
- **Client Credentials** — for OAuth2 server-to-server integrations, using:
  - Access Token URL: `https://oauth.predictleads.com/token`
  - Client ID: `{your_api_key}`
  - Client Secret: `{your_api_token}`

### With HTTP Headers

For direct access, pass your credentials as request headers:
X-Api-Key: {your_api_key}
X-Api-Token: {your_api_token}

## Request Limits

Each account has monthly request limits based on the chosen subscription plan. You can track usage on the [Your Subscription Plans](https://predictleads.com/subscriptions) page. Once an account reaches its limit, further requests return a `402` HTTP error. Contact [support](https://docs.predictleads.com/mcp_integration/introduction/authentication/with_http_headers#contact) with any questions about limits.

## Client Compatibility

PredictLeads MCP works with any client that supports HTTP-based MCP connections and authenticates via OAuth2 or HTTP headers, including Cline.

## Documentation

Full documentation: [docs.predictleads.com/mcp_integration](https://docs.predictleads.com/mcp_integration)

## Support

Questions or issues: see [support](https://docs.predictleads.com/mcp_integration/introduction/authentication/with_http_headers#contact) or contact PredictLeads directly.
