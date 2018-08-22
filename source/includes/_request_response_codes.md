# Response codes

> The response code portions of the response body:

```json
{
  code: 1200,
  message: 'Looks good.',
  ...
}
```

```json
{
  code: 2501,
  message: "Address state State must be a valid 2 character state abbreviation",
  invalid_records: [
    {
      "name": "John Smith",
      "company": "Test Co.",
      "address_1": "123 Test St.",
      "address_2": null,
      "city": "Bothell",
      "state": "Washington",
      "postal_code": "98021",
      "country": "US",
      "phone": "(555)555-5555"
    }
  ],
  ...
}
```

There are various response codes that the API will return to give you a 
programmatic answer:

Code | Meaning
---- | -------
1200 | Everything was OK.
1404 | Not found. If the call expected an ID as a url parameter, please ensure that it is correct.
1500 | There was an unexpected error and engineers are taking a look. Please resubmit your request later.
2501 | There was a problem with an address. The order has not been submitted.
2502 | There was a problem with one or more of the variant ID's you submitted. Please review them and make sure that they belong to your store. The order has not been submitted.
2503 | Stock was too low for one or more of the variants you are trying to order. Please contact Brilliant to increase stock levels. The order has not been submitted.
2504 | One or more of the order item entries is specifying the same variant id. Please make the order item entries unique and adjust the quantity instead. The order has not been submitted.
2505 | The payload you submitted for an order is missing an order_items section or it is empty. The order has not been submitted.
2506 | One or more of the variants you are trying to order are inactive. Check into the possibility of re-activating them, or remove these variants from your payload.
3501 | Validation passed, however, we could not insert your order because we ran into some internal issues. The engineers have been notified and will work on the issue. Please resubmit your payload later.
3502 | An unexpected issue occurred and engineers have been notified. Please resubmit your payload later.
3503 | There was an issue with the payload and the API couldn't handle it appropriately. Engineers have been notified. Please resubmit your payload later.

