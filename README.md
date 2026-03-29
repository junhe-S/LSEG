# LSEG Search Database

This repository provides a search database for quick lookup of companies covered in the **London Stock Exchange Group (LSEG)** database. The data includes company-level identifiers and attributes that can be used to locate, match, and retrieve records across datasets using LSEG's native identifiers.

---

## Overview

The database offers a structured overview of companies available in LSEG, including their key identifiers, organisational metadata, instrument counts, and market information. It is intended to serve as a reference and crosswalk table for researchers and practitioners who need to quickly locate a company's LSEG identifiers before conducting further data retrieval or analysis.

---

## Data Description

Each record in the database represents a single company/organisation entry. The table below describes all available fields.

### Identifiers

| Variable | Description |
|---|---|
| **OAPermID** | Open PermID — LSEG's permanent, unique, and universal entity identifier. Stable across corporate actions. Resolvable via [permid.org](https://permid.org) |
| **Orgid** | LSEG internal organisation identifier |
| **LEI** | Legal Entity Identifier — global standard identifier for legal entities participating in financial transactions |
| **PrimaryRIC** | Primary Reuters Instrument Code — the main instrument-level code used for market data retrieval in LSEG Workspace / Eikon |

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

## Sample Data

The table below shows a preview of the first five records in the database.

| OAPermID | Orgid | CommonName | Gics | PrimaryRIC | BondsCount | CdsCount | EquitiesCount | FundsCount | FuturesCount | LoanCount | MortgagesCount | OptionsCount | WarrantsCount | OwnershipExists | OrganisationStatus | MktCapCompanyUsd | FilingCountry | Trbc2012 | UltimateParentOrganisationOrgid | UltimateParentCompanyOAPermID | BusinessEntity | PI | DTSubjectName | UltimateParentOrganisationName | DTSimpleType | RCSOrganisationSubTypeLeaf | PEBackedStatus | LEI | RCSCountryHeadquartersLeaf | UIInstrumentsAvailable |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4298040942 | 101073023 | Aruba, Government of | NaN | NaN | 2 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | NaN | Unlisted | NaN | NaN | Government & Government Finance (NEC) | 101073023 | 4298041e+09 | ORGANISATION | 4228870 | Aruba, Government of | Aruba, Government of | Government | National Government | Never | 549300KCP2OHANSCXH27 | Aruba | Bonds |
| 4298042021 | 105243423 | Invesco Ltd | Financials / Financial Services / Capital Markets / ... | IVZ | 0 | 0 | 63 | 0 | 0 | 0 | 0 | 22 | 6 | True | Listed | 1.069254e+10 | United States | Investment Management & Fund Operators (NEC) | 105243423 | 4298042e+09 | ORGANISATION | 10501174 | Invesco Ltd | Invesco Ltd | Public Company | Company | Never | ECPGFXU8A2SHKVVGJI15 | United States | Equities; Warrants; Options; Equity Holdings |
| 4298041637 | 106100491 | SD Guthrie Bhd | Consumer Staples / Food, Beverage & Tobacco / Food ... | SDGU.KL | 2 | 0 | 6 | 0 | 0 | 0 | 0 | 0 | 9 | True | Listed | 1.021124e+10 | Malaysia | Starch, Vegetable Fat & Oil Manufacturing | 95790 | 4296552e+09 | ORGANISATION | 15522305 | SD Guthrie Bhd | Malaysia (Government) | Public Company | Company | Never | NaN | Malaysia | Equities; Bonds; Warrants; Equity Holdings |
| 4298040855 | 105691022 | Zurn Elkay Water Solutions Corp | Industrials / Capital Goods / Building Products / Bu... | ZWS | 0 | 0 | 53 | 0 | 0 | 0 | 0 | 178 | 0 | NaN | Listed | 7.507571e+09 | United States | Construction Supplies & Fixtures (NEC) | 105691022 | 4298041e+09 | ORGANISATION | 12158396 | Zurn Elkay Water Solutions Corp | Zurn Elkay Water Solutions Corp | Public Company | Company | Formerly | 549300AM3633XDFU1Q85 | United States | Equities; Options |
| 4298048507 | 108390356 | Jl Mag Rare-Earth Co Ltd | Industrials / Capital Goods / Electrical Equipment ... | 300748.SZ | 0 | 0 | 29 | 0 | 0 | 0 | 0 | 0 | 0 | NaN | Listed | 5.609531e+09 | China (Mainland) | Commodity Chemicals (NEC) | 105940024 | 5000912e+09 | ORGANISATION | 18610063 | Jl Mag Rare-Earth Co Ltd | Jiangxi Ruide Venture Capital Co Ltd | Public Company | Company | Never | 65560079RZSGJHK7CG66 | China (Mainland) | Equities |

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
