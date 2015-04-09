# Data extractor for PDF invoices - invoice2data

I wrote this package to support my accounting process.

- extracts text from PDF files
- searches for regex in the result
- saves results as CSV
- optionally renames PDF files to match the content

## Installation

Optionally this uses `pdfminer`, but `pdftotext` works better. You can choose which module to use. No special Python packages are necessary at the moment, except for `pdftotext`.

There is also `tesseract` integration as a fallback, if no text can be extracted. But it may be more reliable to use 

## Usage

Processes a folder of invoices and copies renamed invoices to new folder.
`python -m invoice2data.main folder_with_invoices --copy new_folder`

Processes a single file and dumps whole file for debugging (useful when adding new templates in templates.py)
`python -m invoice2data.main --debug my_invoice.pdf`

Recognize test invoices:
`python -m invoice2data.main invoice2data/test/pdfs --debug`

## Template system

See `invoice2data/templates.py` for existing templates. Just extend the list to add your own. If deployed by a bigger organisation, there should be an interface to edit templates for new suppliers. 80-20 rule.

## Roadmap

Currently this is a proof of concept. If you scan your invoices, this could easily be connected to an OCR system. Biggest weakness is the need to manually enter new regexes. I don't see an easy way to make it "learn" new patterns.

Planned features:

- 