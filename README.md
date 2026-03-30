# LSEG Search Database

This repository provides a search database for quick lookup of companies covered in the **London Stock Exchange Group (LSEG)** database. The data includes company-level identifiers and attributes that can be used to locate, match, and retrieve records across datasets using LSEG's native identifiers.

---

## Overview

The database offers a structured overview of **27,327,868** companies available in LSEG, including their key identifiers, organisational metadata, instrument counts, and market information. It is intended to serve as a reference and crosswalk table for researchers and practitioners who need to quickly locate a company's LSEG identifiers before conducting further data retrieval or analysis.

![image-20260329124339835](./assets/image-20260329124339835.png)

---

## Data Description

The table below describes all available fields.

### Identifiers

| Variable | Description |
|---|---|
| **OAPermID** | LSEG's permanent and universal entity identifier. Resolvable via [permid.org](https://permid.org) |
| **Orgid** | LSEG internal organisation identifier |
| **PrimaryRIC** | Primary Reuters Instrument Code — the main instrument-level code for primary market |

## Coverage

The database covers **113,200** **listed and delisted** companies in LSEG, where **97,341** (**95,916**) firms have valid stock data (stock trading data). However, LSEG classification classify companys with mistakes. For example, `Alibaba Health Information Technology Ltd` is classfied as bank/financial institution.

![image2](./assets/image2.png)

## Historical Pricing Interday Data

The Historical Pricing Interday Data requested via APIs in this official [Documentation](https://github.com/LSEG-API-Samples/Example.DataLibrary.Python.RequestsComparison/blob/main/Article.md) and [Reference](https://developers.lseg.com/en/article-catalog/article/the-data-library-for-python-quick-reference-guide-access-layer)

```python
url = f'https://api.refinitiv.com/data/historical-pricing/v1/views/interday-summaries/{PrimaryRIC}'

payload = {'interval': 'P1M', 
            'count':15,
            'fields':'BID,ASK,OPEN_PRC,HIGH_1,LOW_1,TRDPRC_1,NUM_MOVES,TRNOVR_UNS',
            'start':'2025-01-01',
            'end':'2025-02-10'}

try:
    response = requests.get(
                            url=url,
                            headers={'Authorization': f'Bearer {access_token}'}, 
                            params=payload,
                            verify=True,
                            allow_redirects=False
                           )
except requests.exceptions.RequestException as e:
    print(f'RDP historical-pricing request exception: {e}')
```

### Sample Price Data

The table below shows a preview of monthly price records.

| OAPermID   | RIC  | CommonName  | DATE_TIME  | TRDPRC_1 | ACVOL_UNS   |
| ---------- | ---- | ----------- | ---------- | -------- | ----------- |
| 4298042021 | IVZ  | Invesco Ltd | 2026/03/31 | 23.20    | 105,667,451 |
| 4298042021 | IVZ  | Invesco Ltd | 2026/02/28 | 26.26    | 110,697,940 |
| 4298042021 | IVZ  | Invesco Ltd | 2026/01/31 | 27.29    | 128,231,099 |
| 4298042021 | IVZ  | Invesco Ltd | 2025/12/31 | 26.27    | 118,235,446 |
| 4298042021 | IVZ  | Invesco Ltd | 2025/11/30 | 24.45    | 72,615,149  |

---

## Usage

This database is intended to be used as a **search and crosswalk table**. A typical use case would be:

1. Search for a company by **CommonName** to retrieve its **OAPermID**, **PrimaryRIC**, or **LEI**.
2. Use the retrieved identifier to query LSEG Workspace / Eikon or other LSEG-connected tools for further data.
3. Match records to other datasets (e.g., Compustat, CRSP) using the identifiers as a bridge key.
4. Use **UltimateParentCompanyOAPermID** to trace corporate ownership hierarchies.

---

## Contact

Please contact Jun He (jun.he@nhh.no) for any questions regarding the data.
