# Authentication

There are three ways to authenticate:

1.  Obtain an authorization cookie by calling the REST connections resource with your API user ID and password. The cookie authorizes the user to make calls to the REST API for the duration specified in Administration Settings > Security Policies > Session timeout. The cookie expiration time is reset with this duration after every call to the REST API.
2.  Include the **apiAccessKeyId** and **apiSecretAccessKey** in the request header, which re-authenticates the user with each request.
3.  For CORS-enabled APIs only: Include a 'single-use' token in the request header, which re-authenticates the user with each request. See below for more details.

In the API reference material, we demonstrate the use of the **apiAccessKeyId** and **apiSecretAccessKey** in the CURL examples. Otherwise we generally assume that you are using the cookie.

## Token Authentication for CORS-Enabled APIs

The CORS mechanism enables REST API calls to Zuora to be made directly from your customer's browser, with all credit card and security information transmitted directly to Zuora. This minimizes your PCI compliance burden, allows you to implement advanced validation on your payment forms, and makes your payment forms look just like any other part of your website.

For security reasons, instead of using cookies, an API request via CORS uses **tokens** for authentication.