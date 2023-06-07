## Mermaid Diagram of distributed Shares Purchasing

The event cascade should mimick a distributed shares purchasing process with the following steps:

1. Issue a request for quotation to two stock broker systems - Swissquotes and Interactive Brokers - for the market order purchasing of 100 shares of Lindt and Spruengli shares. In the root event box list the ISIN, the name of the company, the volume and the type of order (market or limit order)
2. From Swissquotes receive a 10% higher price in the quotation result and from Interactive Brokers the currently valid price approximation (does not need to be accurate). Amend the information in the relevant box with the prices. 
3. Continue only the Interactive Broker stream further in the mermaid diagram as follows:
    a. Issue an order for 150 shares of Lindt and Spruengli
    b. Receive a set of three partial fills for the order
        i. one with 35 shares at the original price
        ii. a second one with 45 shares at a 2% higher price
        iii. a third with 20 shares at yet a 2% higher price
4. Receive a payment confirmation for each of the three partial fills
5. Receive a settlement confirmation for the shares for each of the three partial fills


```mermaid
graph TB
A[Request for Quotation<br/>ISIN: XYZ123<br/>Company: Lindt and Spruengli<br/>Volume: 100 shares<br/>Order Type: Market] --> B{Swissquotes}
A --> C{Interactive Brokers}
B --> D[Quotation Result<br/>Price: +10%]
C --> E[Quotation Result<br/>Price: Approximation]
D --> F[Amend Information<br/>Price: +10%<br/>ISIN: XYZ123]
E --> F[Amend Information<br/>Price: Approximation<br/>ISIN: XYZ123]
F --> G[Issue Order<br/>Volume: 150 shares<br/>ISIN: XYZ123]
G --> H[Partial Fill<br/>35 shares at original price<br/>ISIN: XYZ123]
G --> I[Partial Fill<br/>45 shares at 2% higher price<br/>ISIN: XYZ123]
G --> J[Partial Fill<br/>20 shares at 2% higher price<br/>ISIN: XYZ123]
H --> K[Payment Confirmation<br/>ISIN: XYZ123]
I --> L[Payment Confirmation<br/>ISIN: XYZ123]
J --> M[Payment Confirmation<br/>ISIN: XYZ123]
H --> N[Settlement Confirmation<br/>ISIN: XYZ123]
I --> O[Settlement Confirmation<br/>ISIN: XYZ123]
J --> P[Settlement Confirmation<br/>ISIN: XYZ123]
N --> Q[Order Completed]
O --> Q
P --> Q
```

