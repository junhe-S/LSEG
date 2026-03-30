# LSEG Database Overview

This repository provides a search database for quick lookup of companies covered in the **London Stock Exchange Group (LSEG)** database. The data includes company-level identifiers and attributes that can be used to locate, match, and retrieve records across datasets using LSEG's native identifiers.

---

## Overview of Companies & Issuers [Database](https://huggingface.co/datasets/JunHe-S/LSEG/tree/main)

The database offers a structured overview of **27,327,868** companies available in LSEG, including their key identifiers, organisational metadata, instrument counts, and market information. It is intended to serve as a reference and crosswalk table for researchers and practitioners who need to quickly locate a company's LSEG identifiers before conducting further data retrieval or analysis. 

![image-20260329124339835](./assets/image-20260329124339835.png)

The database covers **113,200** **listed and delisted** companies in LSEG, where **97,341** (**95,916**) firms have valid stock data (stock trading data). However, LSEG classification classify companys with mistakes. For example, `Alibaba Health Information Technology Ltd` is classfied as bank/financial institution.

![image2](./assets/image2.png)

Since we have collected `OAPermID` or `RIC` for each listed and delisted companies, we can download firms' global ownership, which starts from 1997, by referring to this [documentation](https://developers.lseg.com/en/article-catalog/article/the-data-library-for-python-quick-reference-guide-access-layer) and [python module](https://pypi.org/project/lseg-data/). 

```python
import lseg.data as ld 
fields = ['TR.FundPortfolioName','TR.FundInvestorType','TR.FdAdjPctOfShrsOutHeld',
          'TR.FundAdjShrsHeld','TR.FdAdjSharesHeldValue','TR.FundHoldingsDate']
 
own = ld.get_data('MSFT.O', fields,{'SDate':-25,'EDate':-24,'Frq':'D'})
own = own[own["Fund Shares Held (Adjusted)"]!=0].reset_index(drop=True)
own
```

![image5](./assets/image5.png)

**Notice**: LSEG provided all of data on WRDS, which requires extra subscription. Meanwhile, WRDS-13F, which mainly focus on the US market, should provide more data since it starts from 1978. Recently, [Which Investors Drive Anomaly Returns and How? (2026, JFE)](https://www.sciencedirect.com/science/article/pii/S0304405X26000280) applies this in their paper.



## Overview of LSEG Lipper Fund [Database](https://huggingface.co/datasets/JunHe-S/LSEG/tree/main)

**Between 1900 and 2024, the dataset encompasses 943,096 funds across a broad range of investment vehicles.** The vast majority are Mutual Funds, which account for 750,218 entries, followed by Insurance Funds at 60,677 and Pension Funds at 50,877. Exchange Traded Funds (ETFs) number 43,249, while Hedge Funds make up 20,662 of the total. 

![image2](./assets/image3.png)

However, lipper funds are available from **December-2006** and funds report in different frequency. 

![image2](./assets/image4.png)

Since many institutions have no budget for `emaxx` database,  Lipper Fund is a good alternative database as it provides info of `bonds` held by these institutions. Although LESG provides snap of bond ownership, it is only front-edge data and can not be extracted from API.

## Overview of LSEG SDC [Database](https://huggingface.co/datasets/JunHe-S/LSEG/tree/main)

Although it is provided in WRDS, many institutions do not have enough budget for it (including mine). Alternatively, you can download it from SEC platform on LSEG Workspace ( ... maybe need subscription). SDC provides databases including M&A, Bonds Issuance, (syndicated) Loans and IPO, which are popular in Academia. The information is almost the same as ones In `search` section but SDC provides more detailed records.

**Notice**: Loan Dealscan Database on WRDS can connect with LSEG directly via `PermID` code and I notice that many researchers ignore this fact. 

## Overview of LSEG Bond/Trace [Database](https://huggingface.co/datasets/JunHe-S/LSEG/tree/main)

Although it is provided in WRDS, many institutions do not have enough budget for it (including mine). Alternatively, you can inspect some information from LSEG, which provides up to 3-month Trace data and all quote information.



## Contact

Please contact Jun He (jun.he@nhh.no) for any questions regarding the data.
