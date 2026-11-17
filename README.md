# ISO 20022 XML Samples for UAE & GCC Payment Rails

A curated collection of clean, valid **ISO 20022 XML test payloads** tailored for UAE and GCC banking integrations—including **UAE IBANs (MOD-97 compliant)**, UAE Central Bank clearing structures, and local SWIFT/BIC codes.

## Online Browser Validators (100% Client-Side)

Need to validate your own XML payloads or generate QA test IBANs without sending sensitive payment data to a backend server? Use our free browser-native utilities:

* **[ISO 20022 XML Message Validator](https://aurigga.com/tools/iso20022-validator.php)** — Validates XML well-formedness, mandatory `pacs.008` / `pain.001` / `camt.053` elements, ISO 4217 currency attributes, BIC syntax, and embedded UAE IBAN checksums locally in your browser.
* **[UAE IBAN & SWIFT/BIC Validator](https://aurigga.com/tools/uae-iban-validator.php)** — Verifies 23-character UAE IBAN structure, identifies the issuing UAE bank from the 3-digit bank code, validates BIC codes, and generates valid QA test IBANs.
* **[Aurigga Free Fintech & Banking Tools](https://aurigga.com/tools/)** — Full directory of client-side GCC banking utilities.

---

## Included Sample Payloads

| File | Schema | Use Case |
| :--- | :--- | :--- |
| `samples/pacs.008-uae-domestic.xml` | `pacs.008.001.08` | FI-to-FI Customer Credit Transfer (`AED`) with UETR, Mashreq (`BOMLAEADXXX`), and Emirates NBD (`EBILAEADXXX`) BICs. |
| `samples/pain.001-uae-batch-payroll.xml` | `pain.001.001.09` | Customer Credit Transfer Initiation with `CtrlSum`, FAB (`NBADAEAAXXX`), and ADCB (`ADCBAEAA`) test IBANs. |
| `samples/camt.053-uae-statement.xml` | `camt.053.001.08` | End-of-day Bank-to-Customer Statement with opening/closing `AED` balances and booked credit entries. |
| `samples/broken-payload-qa-test.xml` | `pacs.008.001.08` | Intentionally malformed test payload (invalid MOD-97 IBAN, lowercase currency code, mismatched `NbOfTxs`) for negative QA testing. |

---

## UAE IBAN Structure Reference

All UAE IBANs follow a fixed **23-character** alphanumeric format:

```text
AE  07  033  1234567890123456
│   │   │    └── 16-digit domestic account number
│   │   └─────── 3-digit UAE bank identifier (e.g., 033 = Mashreq, 026 = Emirates NBD, 035 = FAB, 003 = ADCB)
│   └─────────── 2-digit MOD-97 check digits
└─────────────── ISO 3166-1 alpha-2 country code (AE)
