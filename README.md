# LSEG Search Database

This repository provides a search database for quick lookup of companies covered in the **London Stock Exchange Group (LSEG)** database. The data includes company-level identifiers and attributes that can be used to locate, match, and retrieve records across datasets using LSEG's native identifiers.

---

## Overview

The database offers a structured overview of companies available in LSEG, including their key identifiers, organisational metadata, instrument counts, and market information. It is intended to serve as a reference and crosswalk table for researchers and practitioners who need to quickly locate a company's LSEG identifiers before conducting further data retrieval or analysis.

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

## Sample Data

The table below shows a preview of the first five records in the database.

<div style="overflow-x: auto;">
<table style="white-space: nowrap;">
  <thead>
    <tr>
      <th>OAPermID</th>
      <th>Orgid</th>
      <th>CommonName</th>
      <th>Gics</th>
      <th>PrimaryRIC</th>
      <th>BondsCount</th>
      <th>CdsCount</th>
      <th>EquitiesCount</th>
      <th>FundsCount</th>
      <th>FuturesCount</th>
      <th>LoanCount</th>
      <th>MortgagesCount</th>
      <th>OptionsCount</th>
      <th>WarrantsCount</th>
      <th>OwnershipExists</th>
      <th>OrganisationStatus</th>
      <th>MktCapCompanyUsd</th>
      <th>FilingCountry</th>
      <th>Trbc2012</th>
      <th>UltimateParentOrganisationOrgid</th>
      <th>UltimateParentCompanyOAPermID</th>
      <th>BusinessEntity</th>
      <th>PI</th>
      <th>DTSubjectName</th>
      <th>UltimateParentOrganisationName</th>
      <th>DTSimpleType</th>
      <th>RCSOrganisationSubTypeLeaf</th>
      <th>PEBackedStatus</th>
      <th>LEI</th>
      <th>RCSCountryHeadquartersLeaf</th>
      <th>UIInstrumentsAvailable</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4298040942</td>
      <td>101073023</td>
      <td>Aruba, Government of</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>Unlisted</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Government &amp; Government Finance (NEC)</td>
      <td>101073023</td>
      <td>4.298041e+09</td>
      <td>ORGANISATION</td>
      <td>4228870</td>
      <td>Aruba, Government of</td>
      <td>Aruba, Government of</td>
      <td>Government</td>
      <td>National Government</td>
      <td>Never</td>
      <td>549300KCP2OHANSCXH27</td>
      <td>Aruba</td>
      <td>Bonds</td>
    </tr>
    <tr>
      <td>4298042021</td>
      <td>105243423</td>
      <td>Invesco Ltd</td>
      <td>Financials/Financial Services/Capital Markets/...</td>
      <td>IVZ</td>
      <td>0</td>
      <td>0</td>
      <td>63</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>22</td>
      <td>6</td>
      <td>True</td>
      <td>Listed</td>
      <td>1.069254e+10</td>
      <td>United States</td>
      <td>Investment Management &amp; Fund Operators (NEC)</td>
      <td>105243423</td>
      <td>4.298042e+09</td>
      <td>ORGANISATION</td>
      <td>10501174</td>
      <td>Invesco Ltd</td>
      <td>Invesco Ltd</td>
      <td>Public Company</td>
      <td>Company</td>
      <td>Never</td>
      <td>ECPGFXU8A2SHKVVGJI15</td>
      <td>United States</td>
      <td>Equities; Warrants; Options; Equity Holdings</td>
    </tr>
    <tr>
      <td>4298041637</td>
      <td>106100491</td>
      <td>SD Guthrie Bhd</td>
      <td>Consumer Staples/Food, Beverage &amp; Tobacco/Food...</td>
      <td>SDGU.KL</td>
      <td>2</td>
      <td>0</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>9</td>
      <td>True</td>
      <td>Listed</td>
      <td>1.021124e+10</td>
      <td>Malaysia</td>
      <td>Starch, Vegetable Fat &amp; Oil Manufacturing</td>
      <td>95790</td>
      <td>4.296552e+09</td>
      <td>ORGANISATION</td>
      <td>15522305</td>
      <td>SD Guthrie Bhd</td>
      <td>Malaysia (Government)</td>
      <td>Public Company</td>
      <td>Company</td>
      <td>Never</td>
      <td>NaN</td>
      <td>Malaysia</td>
      <td>Equities; Bonds; Warrants; Equity Holdings</td>
    </tr>
    <tr>
      <td>4298040855</td>
      <td>105691022</td>
      <td>Zurn Elkay Water Solutions Corp</td>
      <td>Industrials/Capital Goods/Building Products/Bu...</td>
      <td>ZWS</td>
      <td>0</td>
      <td>0</td>
      <td>53</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>178</td>
      <td>0</td>
      <td>NaN</td>
      <td>Listed</td>
      <td>7.507571e+09</td>
      <td>United States</td>
      <td>Construction Supplies &amp; Fixtures (NEC)</td>
      <td>105691022</td>
      <td>4.298041e+09</td>
      <td>ORGANISATION</td>
      <td>12158396</td>
      <td>Zurn Elkay Water Solutions Corp</td>
      <td>Zurn Elkay Water Solutions Corp</td>
      <td>Public Company</td>
      <td>Company</td>
      <td>Formerly</td>
      <td>549300AM3633XDFU1Q85</td>
      <td>United States</td>
      <td>Equities; Options</td>
    </tr>
    <tr>
      <td>4298048507</td>
      <td>108390356</td>
      <td>Jl Mag Rare-Earth Co Ltd</td>
      <td>Industrials/Capital Goods/Electrical Equipment...</td>
      <td>300748.SZ</td>
      <td>0</td>
      <td>0</td>
      <td>29</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>Listed</td>
      <td>5.609531e+09</td>
      <td>China (Mainland)</td>
      <td>Commodity Chemicals (NEC)</td>
      <td>105940024</td>
      <td>5.000912e+09</td>
      <td>ORGANISATION</td>
      <td>18610063</td>
      <td>Jl Mag Rare-Earth Co Ltd</td>
      <td>Jiangxi Ruide Venture Capital Co Ltd</td>
      <td>Public Company</td>
      <td>Company</td>
      <td>Never</td>
      <td>65560079RZSGJHK7CG66</td>
      <td>China (Mainland)</td>
      <td>Equities</td>
    </tr>
  </tbody>
</table>
</div>

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
