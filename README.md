# pdf-invoice-receipt-data-extractor-api

Extract structured JSON fields (invoice number, date, vendor name, vendor email, currency, subtotal, tax/VAT/GST, and grand total) from PDF invoices and receipts via public URL, direct file upload, or raw text.

🔗 **Get your free API key:** [PDF Invoice & Receipt Data Extractor on RapidAPI](YOUR_RAPIDAPI_LISTING_URL) *(50 free requests/month)*

## Endpoints
- **`POST /v1/parse-pdf-url`** — Fetches a PDF from a public HTTPS URL and extracts structured invoice JSON.
- **`POST /v1/parse-pdf-file`** — Accepts a direct `.pdf` file upload (`multipart/form-data`) and returns extracted fields.
- **`POST /v1/parse-invoice-text`** — Parses raw invoice text into structured accounting JSON.

## Quick Start (Python)

```python
import requests

url = "https://YOUR_RAPIDAPI_HOST/v1/parse-invoice-text"

payload = {
"text": "ACME Cloud Services Inc.\nInvoice #INV-2026-8841\nDate: 2026-11-15\nBilling: accounts@acmecloud.io\nSubtotal: \$250.00\nTax (18%): \$45.00\nTotal Due: \$295.00 USD"
}

headers = {
"content-type": "application/json",
"x-rapidapi-key": "YOUR_RAPIDAPI_KEY",
"x-rapidapi-host": "YOUR_RAPIDAPI_HOST"
}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

## Sample Response

```json
{
"page_count": 1,
"vendor_name": "ACME Cloud Services Inc.",
"vendor_email": "accounts@acmecloud.io",
"invoice_number": "INV-2026-8841",
"invoice_date": "2026-11-15",
"currency": "USD",
"subtotal_amount": 250.0,
"tax_amount": 45.0,
"total_amount": 295.0
}
```
