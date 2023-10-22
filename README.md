# Bundle-Wallet-API
## Overview
This document outlines the process of testing the Lawyer Billing System API. The API is designed to help lawyers streamline their billing process by parsing CSV files containing billing information and providing detailed invoice data. The API offers endpoints for parsing CSV files and retrieving invoice details.

## API Endpoints
### 1. POST - Parse CSV file content
- **Endpoint:** `{{baseUrl}}/invoice/parse`
- **Description:** Allows you to parse the content of a CSV file encoded in Base64. The CSV file must adhere to the specified format.
- **Request:**
  - **Headers:** Content-Type (application/json)
  - **Body:** 
    ```json
    { 
      "payload": "Base64-encoded CSV content here"
    }
    ```
- **Response:**
  - This endpoint will return a success response with the parsed data in JSON format.

### 2. GET - Get Invoice Parsing Result by ID
- **Endpoint:** `{{baseUrl}}/invoice/{{invoice_id}}`
- **Description:** Retrieve the parse result for a previously parsed CSV invoice by its specified ID.
- **Request:**
  - **Example Request:**
    ```bash
    curl --location -g '{{baseUrl}}/invoice/:invoiceId'
    ```
- **Response:**
  - Returns JSON data with parsed company details and an empty map when the specified ID is not found.
    ```json
    {
      "companies": { "Google": 2400, "Facebook": 500 },
      "id": ""
    }
    ```

### 3. GET - Get Company Details from an Invoice
- **Endpoint:** `{{baseUrl}}/invoice/{{invoice_id}}/company?companyName=Google`
- **Description:** Get a breakdown of the employees, rates, and amounts billed by a company in an invoice result using the ID.
- **Request:**
  - **Example Request:**
    ```bash
    curl --location -g '{{baseUrl}}/invoice/{{invoice_id}}/company?companyName=Google'
    ```
- **Response:**
  - Returns JSON data with detailed company billing information.

## API Testing Results
- **Parse CSV File Content Endpoint:** Successfully parses CSV files and provides parsed data as expected.
- **Get Invoice Parsing Result by ID Endpoint:** Always returns a success response and handles cases where the specified ID is not found.
- **Get Company Details from an Invoice Endpoint:** Provides detailed company billing information as expected.

Overall, the API functions correctly and ensures a streamlined billing process for lawyers, simplifying the creation of invoices.

🎉 API Testing Complete! 🎉
