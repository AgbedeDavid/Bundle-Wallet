# Bundle-Wallet-API
Documentation for the Backend API specifications to ensure that the APIs are functioning correctly and that response displays as expected.

POST-Parse CSV file content
{{baseUrl}}/invoice/parse

This endpoint allows you to parse the content of the CSV file encoded in Base64. The CSV file must conform to the specified format.


HEADERS
Content-Type

application/json
Bodyraw

{
    "payload": "RW1wbG95ZWUgSUQsQmlsbGFibGUgUmF0ZSAocGVyIGhvdXIpLFByb2plY3QsRGF0ZSxTdGFydCBUaW1lLEVuZCBUaW1lCjEsMzAwLEdvb2dsZSwyMDE5LTA3LTAxLDA5OjAwLDE3OjAwCjIsMTAwLEZhY2Vib29rLDIwMTktMDctMDEsMTE6MDAsMTY6MDA="
}



GET-Get Invoice Parsing Result by ID
{{baseUrl}}/invoice/{{invoice_id}}

Get the Parse Result for a previously parsed CSV invoice by specified ID. In general, this endpoint will ALWAYS return success irrespective of the ID specified. When a result with the specified ID is not found, the companies will be an empty map.

Example Request
OK
curl

curl --location -g '{{baseUrl}}/invoice/:invoiceId'

200 OK
Example Response

json

{
  "companies": {
    "Google": 2400,
    "Facebook": 500
  },
  "id": "<uuid>"
}

GETGet Company details from an Invoice
{{baseUrl}}/invoice/{{invoice_id}}/company?companyName=Google

Get the breakdown of the employees, rates and amounts billed by a company in an Invoice result using the ID. This endpoint allows you to "drill-down" into the total amount charged by a company for a given invoice parsed.
