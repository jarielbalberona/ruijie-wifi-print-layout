# Voucher PDF Generator

This is a PDF-only voucher printer for WiFi voucher exports.

It reads all `.xlsx` files inside `input/`, extracts voucher codes, and creates a legal-size PDF with a fixed 4-column layout. Each voucher is drawn directly on the PDF canvas, so vouchers do not get cut between pages.

## Folder structure

```txt
  assets/
    logo.png
  input/
    Voucher (2).xlsx
  output/
  generate_vouchers_pdf.py
  requirements.txt
```

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Generate PDF

```bash
python generate_vouchers_pdf.py --input-dir input --output-dir output
```

Default output:

```txt
output/wifi-vouchers.pdf
```

Default layout:

- Legal paper
- Landscape
- 4 columns
- 8 rows
- 32 vouchers per page
- Logo + voucher code only

For the uploaded sample with 4,000 vouchers, this creates 125 pages.

## Larger vouchers

Use 7 rows instead of 8 if you want more space per voucher:

```bash
python generate_vouchers_pdf.py --input-dir input --output-dir output --rows 7
```

## Include period and device details

```bash
python generate_vouchers_pdf.py --input-dir input --output-dir output --include-details
```

## Only unused vouchers

```bash
python generate_vouchers_pdf.py --input-dir input --output-dir output --unused-only
```

## Print settings

Use these settings when printing the generated PDF:

- Paper size: Legal, 8.5 x 14 in
- Orientation: Landscape
- Scale: 100% / Actual size
- Margins: printer default or none

Do not use browser scaling like "fit to page" if it changes the PDF size unexpectedly.
