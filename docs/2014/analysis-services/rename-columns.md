---
title: 'Lektion 3: Umbenennen von Spalten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fc8ba1a-2b30-4775-9b3b-c09dee711b3e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 80d9cae6deae4059327084f531f6a6d958a39ec6
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66070319"
---
# <a name="lesson-3-rename-columns"></a>Lektion 3: Umbenennen von Spalten
  In dieser Lektion benennen Sie viele der Spalten in jeder importierten Tabelle um. Durch das Umbenennen von Spalten sind diese leichter identifizierbar und navigierbar sowohl im Modell-Designer als auch in einer Clientanwendung bei der Auswahl von Feldern durch Benutzer. Weitere Informationen finden Sie unter [Umbenennen einer Tabelle oder Spalte &#40;SSAS – tabellarisch&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md).  
  
> [!IMPORTANT]  
>  Das Umbenennen von Spalten ist zum Abschluss dieses Lernprogramms nicht notwendig. Übrige Lektionen, insbesondere diejenigen über die Erstellung von Beziehungen und berechneten Spalten und Measures mit DAX-Formeln, verweisen auf die in dieser Lektion beschriebenen Spaltenanzeigenamen. Wenn Sie Spalten umbenennen möchten, sind die DAX-Formeln in den Lektionen 5, 6 und 7 zu bearbeiten, um die ursprünglichen in dieser Lektion bereitgestellten Namen der Quellspalten zu verwenden.  
  
 Geschätzte Zeit zum Abschließen dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 2: Hinzufügen von Daten](lesson-2-add-data.md).  
  
## <a name="rename-columns"></a>Umbenennen von Spalten  
  
#### <a name="to-rename-columns"></a>So benennen Sie Spalten um  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Customer** .  
  
     Wenn Sie auf eine Registerkarte klicken, wird diese Tabelle im Modell-Designer-Fenster aktiv.  
  
2.  Doppelklicken dem **CustomerKey** Spalte benennen, und geben Sie `Customer  Id`, und drücken Sie dann die EINGABETASTE.  
  
    > [!TIP]  
    >  Sie können auch umbenennen eine Spalte in der **Spaltenname** -Eigenschaft in der Spaltenwerts **Eigenschaften** Fenster oder in der Diagrammsicht angezeigt.  
  
3.  Benennen Sie die verbleibenden Spalten in der Tabelle **Customer** sowie die Spalten in den verbleibenden Tabellen um. Ersetzen Sie dabei den Quellnamen durch den entsprechenden Anzeigenamen:  
  
     **Customer-Tabelle**  
  
    |Quellname|Anzeigename|  
    |-----------------|-------------------|  
    |GeographyKey|Geography Id|  
    |CustomerAlternateKey|Customer Alternate ID|  
    |FirstName|First Name|  
    |MiddleName|Middle Name|  
    |LastName|Last Name|  
    |NameStyle|Name Style|  
    |BirthDate|Birth Date|  
    |MaritalStatus|Marital Status|  
    |EmailAddress|Email Address|  
    |YearlyIncome|Yearly Income|  
    |TotalChildren|Total Children|  
    |NumberChildrenAtHome|Number of Children At Home|  
    |EnglishEducation|Education|  
    |EnglishOccupation|Occupation|  
    |HouseOwnerFlag|Owns House|  
    |NumberCarsOwned|Number of Cars Owned|  
    |AddressLine1|Adresszeile 1|  
    |AddressLine2|Address Line 2|  
    |Phone|Phone Number|  
    |DateFirstPurchase|Date of First Purchase|  
    |CommuteDistance|Commute Distance|  
  
     **Datum**  
  
    |Quellname|Anzeigename|  
    |-----------------|-------------------|  
    |FullDateAlternateKey|date|  
    |DayNumberOfWeek|Day Number of Week|  
    |EnglishDayNameOfWeek|Day Name|  
    |DayNumberOfMonth|Day of Month|  
    |DayNumberOfYear|Day of Year|  
    |WeekNumberOfYear|Week Number of Year|  
    |EnglishMonthName|Month Name|  
    |MonthNumberOfYear|Month|  
    |CalendarQuarter|Calendar Quarter|  
    |CalendarYear|Calendar Year|  
    |CalendarSemester|Calendar Semester|  
    |FiscalQuarter|Fiscal Quarter|  
    |FiscalYear|Fiscal Year|  
    |FiscalSemester|Fiscal Semester|  
  
     **Geography**  
  
    |Quellname|Anzeigename|  
    |-----------------|-------------------|  
    |GeographyKey|Geography Id|  
    |Bundesland/Kanton/PLZ|State Province Code|  
    |StateProvinceName|State Province Name|  
    |CountryRegionCode|Country Region Code|  
    |EnglishCountryRegionName|Country Region Name|  
    |PostalCode|Postal Code|  
    |SalesTerritoryKey|Sales Territory Id|  
  
     **Product**  
  
    |Quellname|Anzeigename|  
    |-----------------|-------------------|  
    |ProductKey|Product Id|  
    |ProductAlternateKey|Product Alternate Id|  
    |ProductSubcategoryKey|Product Subcategory Id|  
    |WeightUnitMeasureCode|Weight Unit Code|  
    |SizeUnitMeasureCode|Size Unit Code|  
    |EnglishProductName|Produktname|  
    |StandardCost|Standard Cost|  
    |FinishedGoodsFlag|Is Finished Product|  
    |SafetyStockLevel|Safety Stock Level|  
    |ReorderPoint|Reorder Point|  
    |ListPrice|List Price|  
    |SizeRange|Size Range|  
    |DaysToManufacture|Days to Manufacture|  
    |ProductLine|Product Line|  
    |Dealer Price|Dealer Price|  
    |ModelName|Model Name|  
    |LargePhoto|Large Photo|  
    |EnglishDescription|Description|  
    |StartDate|Product Start Date|  
    |EndDate|Product End Date|  
    |Status|Product Status|  
  
     **Produktkategorie**  
  
    |Quellname|Anzeigename|  
    |-----------------|-------------------|  
    |ProductCategoryKey|Product Category Id|  
    |ProductCategoryAlternateKey|Product Category Alternate Id|  
    |EnglishProductCategoryName|Product Category Name|  
  
     **Produktunterkategorie**  
  
    |Quellname|Anzeigename|  
    |-----------------|-------------------|  
    |ProductSubcategoryKey|Product Subcategory Id|  
    |ProductSubcategoryAlternateKey|Product Subcategory Alternate Id|  
    |EnglishProductSubcategoryName|Product Subcategory Name|  
    |ProductCategoryKey|Product Category Id|  
  
     **Internetumsätze**  
  
    |Quellname|Anzeigename|  
    |-----------------|-------------------|  
    |ProductKey|Product Id|  
    |CustomerKey|Customer Id|  
    |PromotionKey|Promotion Id|  
    |CurrencyKey|Currency Id|  
    |SalesTerritoryKey|Sales Territory Id|  
    |SalesOrderNumber|Sales Order Number|  
    |SalesOrderLineNumber|Sales Order Line Number|  
    |RevisionNumber|Revision Number|  
    |OrderQuantity|Order Quantity|  
    |UnitPrice|Unit Price|  
    |ExtendedAmount|Extended Amount|  
    |UnitPriceDiscountPct|Unit Price Discount Pct|  
    |DiscountAmount|Discount Amount|  
    |ProductStandardCost|Product Standard Cost|  
    |TotalProductCost|Total Product Cost|  
    |SalesAmount|Sales Amount|  
    |TaxAmt|Tax Amt|  
    |CarrierTrackingNumber|Carrier Tracking Number|  
    |CustomerPONumber|Customer PO Number|  
    |OrderDate|Order Date|  
    |DueDate|Due Date|  
    |ShipDate|Ship Date|  
  
## <a name="next-step"></a>Nächster Schritt  
 Um dieses Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 4: Als Datumstabelle markieren](lesson-3-mark-as-date-table.md).  
  
  
