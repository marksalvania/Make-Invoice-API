# Make Invoice API
Simple HTTP API to create invoice PDFs.

- [About](#about)
- [Getting Started](#getting-started)
- [API Reference](#api-reference)
- [Support](#support)
- [Terms of Use and Privacy Policy](#terms-of-use-and-privacy-policy)

## About

Make your own invoice generator through our API and download PDF quickly. Create and pay your customers in fastest way. Expand your site capability to create invoice for your users and send directly to their client/customer email. 

Our API only have one endpoint that returns a PDF as a response and downloaded.

### Endpoint
https://www.make-invoice.com/invoices/create-pdf

### Getting Started

curl https://www.make-invoice.com/invoices/create-pdf \
  -d invoiceNo="123" \
  -d BilledTo="Sample 123, Address" \
  -d PaymentMethod="Paypal" \
  -d BillingAddress="Ship to address, Test sample" \
  -d BillDate="Aug. 4, 2020" \
  -d BillDueDate="Aug. 4, 2020" \
  -d Notes="This is a sample notes and can also accept <br/>" \
  -d tax="10 " \
  -d Terms="This is a sample terms and can also accept <br/>" \
  -d items="{Array object}" \
  -d currency="$" \
  -d companylogo="https://www.make-invoice.com/public/assets/images/logo2x.png" \
  -d template="freelancer" \
  -d EmailAdd="your@email.com" \
  -d headercolor="dark" \
  -d TypeGen="invoice" \
> invoice.pdf

### JSON Input

JSON input is also accepted with the `Content-Type` header set to `application/json`

```
curl https://www.make-invoice.com/invoices/create-pdf \
  -H "Content-Type: application/json" \
  -d '{
        "invoiceNo": "321",
        "BilledTo": "Sample billing address of client",
        "PaymentMethod": "Paypal",
        "BillingAddress": "This is a sample billing address",
        "BillDate": "2021-04-17",
        "BillDueDate": "2021-04-10",
        "Notes": "This is my notes accepts<br />space html tag",
        "tax": "10",
        "Terms": "This is my terms accepts<br />space html tag",
        "items": [
            {
                "date": "2021-05-14",
                "task": "First Task",
                "hours": "3",
                "rate": "23",
                "total": "69.00"
            }
        ],
        "currency": "$",
        "companylogo": "https://www.make-invoice.com/public/assets/images/logo2x.png",
        "template": "freelancer",
        "EmailAdd": null,
        "headercolor": "dark",
        "TypeGen": "invoice"
      }' \
> invoice.pdf
```

We currently have translations available in:
- English

## API Reference

### Line Items

Line items are represented as an array of objects. Here's an example:

```json
{
  "items": [
    {
      "date": "2021-05-14",
        "task": "First Task",
        "hours": "3",
        "rate": "23",
        "total": "69.00"
    }
    {
      "date": "2021-05-14",
      "task": "second Task",
      "hours": "3",
      "rate": "23",
      "total": "69.00"
    }
  ]
}
```

### Invoice

When a value is null or zero, the field will return a default value like "Not available". The exception to this are the required fields `BilledTo`, `BillingAddress`, `date`, and `items`.

 invoiceNo="123" \
  -d BilledTo="Sample 123, Address" \
  -d PaymentMethod="Paypal" \
  -d BillingAddress="Ship to address, Test sample" \
  -d BillDate="Aug. 4, 2020" \
  -d BillDueDate="Aug. 4, 2020" \
  -d Notes="This is a sample notes and can also accept <br/>" \
  -d tax="10 " \
  -d Terms="This is a sample terms and can also accept <br/>" \
  -d items="{Array object}" \
  -d currency="$" \
  -d companylogo="https://www.make-invoice.com/public/assets/images/logo2x.png" \
  -d template="freelancer" \
  -d EmailAdd="your@email.com" \
  -d headercolor="dark" \
  -d TypeGen="invoice" \

|Parameter|Description|Default Value
|:--------|:----------|:------------
`invoiceNo`|Invoice No|*null*
`BilledTo`|Your organization billing address and contact info|*null*
`PaymentMethod`|Your payment method|*null*
`ShipTo`|Shipping address - multiple lines ok|*null*
`BillDate`|Bill date of your invoice|*null*
`BillDueDate`|Bill due date of your invoice|*null*
`Notes`|Notes and only optional|Not Available
`tax`|Tax rate|0
`Terms`|Payment terms summary|Not Available
`items`|Array of objects for items|*null*
`currency`|Your main currency|$
`companylogo`|Your company logo|blank
`template`|Relies on type of the template|freelancer
`EmailAdd`|Your email address|blank
`headercolor`|Top header background color|light
`TypeGen`|Type of template|invoice

### Subtotal & Grand Total readonly fields

We have a field like Subtotal, Tax amount and Grand total in read only mode it has automatic calculations for all numbers input in the form.

## Support

Having any issues? or do you have any suggestions you would like to add in the system? You are very welcome to give us your feedback!.

You can check these useful links that maybe can help to answer your questions

- [Help](https://www.make-invoice.com/help)
- [How to use](https://www.make-invoice.com/how-to-use)
- [Guidelines](https://www.make-invoice.com/guide)

## Terms of Use and Privacy Policy

Using www.make-invoice.com is subject to the [Privacy Policy and Terms of Use](https://www.make-invoice.com/privacy-policy).
