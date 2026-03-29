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

### Company Information

| Variable | Description |
|---|---|
| **CommonName** | Common or trade name of the company |
| **DTSubjectName** | Datastream subject name for the entity |
| **DTSimpleType** | Datastream simple type classification |
| **BusinessEntity** | Type of business entity |
| **OrganisationStatus** | Current status of the organisation (e.g., active, inactive) |
| **FilingCountry** | Country in which the company files regulatory documents |
| **RCSCountryHeadquartersLeaf** | Country of headquarters based on LSEG's RCS classification |
| **PI** | Private/public indicator |
| **PEBackedStatus** | Indicates whether the company is private equity-backed |

### Classification

| Variable | Description |
|---|---|
| **Gics** | Global Industry Classification Standard (GICS) sector/industry code |
| **Trbc2012** | Thomson Reuters Business Classification (TRBC) 2012 code |
| **RCSOrganisationSubTypeLeaf** | LSEG RCS organisation sub-type classification at the leaf level |

### Parent / Ownership

| Variable | Description |
|---|---|
| **UltimateParentOrganisationOrgid** | Orgid of the ultimate parent organisation |
| **UltimateParentCompanyOAPermID** | OAPermID of the ultimate parent company |
| **UltimateParentOrganisationName** | Name of the ultimate parent organisation |
| **OwnershipExists** | Indicates whether ownership data is available for the entity |

### Market & Financials

| Variable | Description |
|---|---|
| **MktCapCompanyUsd** | Company market capitalisation in USD |

### Instrument Counts

The following fields indicate the number of instruments of each type associated with the company in LSEG.

| Variable | Description |
|---|---|
| **BondsCount** | Number of bonds |
| **CdsCount** | Number of credit default swaps (CDS) |
| **EquitiesCount** | Number of equity instruments |
| **FundsCount** | Number of funds |
| **FuturesCount** | Number of futures |
| **LoanCount** | Number of loans |
| **MortgagesCount** | Number of mortgages |
| **OptionsCount** | Number of options |
| **WarrantsCount** | Number of warrants |
| **UIInstrumentsAvailable** | Indicates whether instruments are available via the LSEG UI |

---

## Coverage

The database covers **113,200** **listed and delisted** companies in LSEG, where **97,341** (**80,410**) firms have valid stock observations (stock trading data). PS: some equities only have bid-ask quotes but trading data.

The following query was used to extract the core company universe from the database:

```python
import sqlite3
import pandas as pd

query = """
    SELECT OAPermID, PrimaryRIC, CommonName, OrganisationStatus, RCSOrganisationSubTypeLeaf, Trbc2012, RCSCountryHeadquartersLeaf
    FROM tr_company
    WHERE OrganisationStatus IN ('Delisted', 'Listed')
      AND NOT (
          RCSOrganisationSubTypeLeaf LIKE '%Government%'
          OR RCSOrganisationSubTypeLeaf LIKE '%Bank%'
          OR RCSOrganisationSubTypeLeaf LIKE '%Organization%'
          OR RCSOrganisationSubTypeLeaf LIKE '%Investment%'
          OR RCSOrganisationSubTypeLeaf LIKE '%REIT%'
          OR RCSOrganisationSubTypeLeaf LIKE '%University%'
          OR RCSOrganisationSubTypeLeaf LIKE '%Agency%'
          OR RCSOrganisationSubTypeLeaf LIKE '%Unknown%'
          OR RCSOrganisationSubTypeLeaf LIKE '%Charity%'
          OR RCSOrganisationSubTypeLeaf LIKE '%Vehicle%'
      )
      AND DTSimpleType IN ('Private Company', 'Public Company')
"""

with sqlite3.connect('../../database.sqlite') as conn:
    df = pd.read_sql(query, conn)
```

The Trend of Live Stocks:

![download](./assets/download-4792507.png)

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
