# LSEG Database Overview

This repository provides a search database for quick lookup of companies covered in the **London Stock Exchange Group (LSEG)** database. The data includes company-level identifiers and attributes that can be used to locate, match, and retrieve records across datasets using LSEG's native identifiers.

---

## Overview of Companies & Issuers [Database](https://huggingface.co/datasets/JunHe-S/LSEG/tree/main)

The database offers a structured overview of **27,327,868** companies available in LSEG, including their key identifiers, organisational metadata, instrument counts, and market information. It is intended to serve as a reference and crosswalk table for researchers and practitioners who need to quickly locate a company's LSEG identifiers before conducting further data retrieval or analysis. 

![image-20260329124339835](./assets/image-20260329124339835.png)

The database covers **113,200** **listed and delisted** companies in LSEG, where **97,341** (**95,916**) firms have valid stock data (stock trading data). However, LSEG classification classify companys with mistakes. For example, `Alibaba Health Information Technology Ltd` is classfied as bank/financial institution.

![image2](./assets/image2.png)

Since we have collected OAPermID or RIC for each listed and delisted companies, we can download firms' global ownership, which starts from 1997, by referring to this [documentation](https://developers.lseg.com/en/article-catalog/article/the-data-library-for-python-quick-reference-guide-access-layer). Different from mutual fund or 13f database, LSEG global ownership contains mutual funds, pension funds, insurance funds, incorporation, insiders and other strategic entities with application in paper, [Which investors drive anomaly returns and how? (2026, JFE)](https://www.sciencedirect.com/science/article/pii/S0304405X26000280).

## Overview of LSEG Lipper Fund [Database](https://huggingface.co/datasets/JunHe-S/LSEG/tree/main)

**Between 1900 and 2024, the dataset encompasses 943,096 funds across a broad range of investment vehicles.** The vast majority are Mutual Funds, which account for 750,218 entries, followed by Insurance Funds at 60,677 and Pension Funds at 50,877. Exchange Traded Funds (ETFs) number 43,249, while Hedge Funds make up 20,662 of the total. 

![image2](./assets/image3.png)

However, lipper funds are available from **December-2006** and funds report in different frequency. 

![image2](./assets/image4.png)

---

## Contact

Please contact Jun He (jun.he@nhh.no) for any questions regarding the data.
