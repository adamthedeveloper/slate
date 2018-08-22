# Errors

The Storefront API uses the following HTTP error codes:

Error Code | Meaning
---------- | -------
401 | Unauthorized -- Your API key is wrong or disabled.
404 | Not Found.
429 | Too Many Requests -- You've hit your throttling limit. Please lower the frequency of your requests.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
