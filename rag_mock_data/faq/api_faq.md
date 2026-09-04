# API FAQ

**Q: What are the API rate limits?**
A: Standard tier accounts are limited to 100 requests per minute and 50,000 requests per day. Enterprise tier accounts have a default limit of 1,000 requests per minute, with higher limits available on request. Rate limit headers (`X-RateLimit-Remaining`, `X-RateLimit-Reset`) are included on every response.

**Q: What authentication methods are supported?**
A: The API supports API key authentication for server to server integrations and OAuth 2.0 for applications acting on behalf of a user. API keys should be passed in the `Authorization: Bearer` header and never included in URL query parameters.

**Q: Is there a sandbox environment?**
A: Yes, a full sandbox environment is available at api-sandbox.example.com, mirroring production functionality with test data. Sandbox API keys are prefixed with `sk_test_` and production keys with `sk_live_`.

**Q: What happens if I exceed the rate limit?**
A: Requests exceeding the rate limit receive a 429 status code with a `Retry-After` header indicating how many seconds to wait before retrying. We recommend implementing exponential backoff for retry logic.

**Q: Are there official SDKs?**
A: Official SDKs are maintained for Python, Node.js, Ruby, and Go. Community maintained SDKs exist for several other languages, listed in the developer portal, but are not officially supported by our team.

**Q: How do webhooks work?**
A: Webhooks can be configured in the Developer Settings panel. Each webhook event is signed with an HMAC-SHA256 signature included in the `X-Signature` header, which should be verified against your webhook secret before processing the payload.

**Q: What is the API versioning policy?**
A: The API is versioned via the URL path (e.g., `/v2/`). We provide a minimum of 12 months notice before deprecating a major API version, and deprecated versions continue to function during that notice period with deprecation warnings included in response headers.

**Q: How do I request a higher rate limit?**
A: Submit a request through the developer portal's "Request Limit Increase" form, including your use case and expected volume. Most requests are reviewed within 3 business days.
