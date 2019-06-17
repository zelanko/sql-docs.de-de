---
title: 'Beispiel: Angeben der ID- und IDREFS-Anweisungen | Microsoft-Dokumentation'
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- IDREFS directive
- ID directive
ms.assetid: 99b9f0d8-ecbb-4225-859f-881066c09785
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7636828b19d156c9d4a2c9b8503fd81a9d1ec01d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66175399"
---
# <a name="example-specifying-the-id-and-idrefs-directives"></a>Beispiel: Angeben der ID- und IDREFS-Anweisungen

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Ein Elementattribut kann als Attribut vom Typ **ID** angegeben werden, wobei das **IDREFS** -Attribut dann verwendet werden kann, um darauf zu verweisen. Dies ermöglicht dokumentinterne Links. Das Verfahren ist der Beziehung zwischen Primärschlüssel und Fremdschlüssel in relationalen Datenbanken ähnlich.  
  
 Dieses Beispiel veranschaulicht, wie die **ID** - und die **IDREFS** -Direktive zum Erstellen von Attributen vom Typ **ID** und **IDREFS** verwendet werden können. Da IDs keine ganzzahligen Werte sein können, werden die ID-Werte in diesem Beispiel konvertiert, d. h. sie werden einer Typumwandlung unterzogen, und es werden Präfixe für die ID-Werte verwendet.  
  
 Angenommen, Sie möchten folgende XML-Ausgabe generieren:  
  
```xml
<Customer CustomerID="C1" SalesOrderIDList=" O11 O22 O33..." >
    <SalesOrder SalesOrderID="O11" OrderDate="..." />  
    <SalesOrder SalesOrderID="O22" OrderDate="..." />  
    <SalesOrder SalesOrderID="O33" OrderDate="..." />  
    ...  
</Customer>  
```  
  
Das `SalesOrderIDList`-Attribut des `<Customer>`-Elements ist ein mehrwertiges Attribut, das auf die `SalesOrderID`-Attribute des `<SalesOrder>`-Elements verweist. Um diesen Link herzustellen, muss das `SalesOrderID`-Attribut als `ID`-Typ und das `SalesOrderIDList`-Attribut des `<Customer>`-Elements als `IDREFS`-Typ deklariert werden. Da ein Kunde mehrere Bestellungen aufgeben kann, wird `IDREFS` verwendet.
  
 Elemente des **IDREFS** -Typs können zudem mehr als einen Wert annehmen. Daher müssen Sie jeweils eine SELECT-Klausel verwenden, die dieselben Tag-, Parent- und Schlüsselspalteninformationen wiederverwendet. Mit `ORDER BY` wird dann sichergestellt, dass die Sequenz der Zeilen, aus denen die **IDREFS** -Werte bestehen, unter dem jeweiligen übergeordneten Element gruppiert wird.  
  
 Im Folgenden wird die Abfrage gezeigt, die die gewünschte XML-Ausgabe erstellt. Die Abfrage verwendet die `ID` -Direktive und die `IDREFS` -Direktive, um die Datentypen der Spaltennamen (`SalesOrder!2!SalesOrderID!ID`, `Customer!1!SalesOrderIDList!IDREFS`) zu überschreiben.  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID   [Customer!1!CustomerID],  
        NULL           [Customer!1!SalesOrderIDList!IDREFS],
        NULL           [SalesOrder!2!SalesOrderID!ID],  
        NULL           [SalesOrder!2!OrderDate]  
FROM   Sales.Customer C   

UNION ALL   
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID,  
        'O-'+CAST(SalesOrderID as varchar(10)),   
        NULL,  
        NULL  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID  

UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
        C.CustomerID,  
        NULL,  
        'O-'+CAST(SalesOrderID as varchar(10)),  
        OrderDate  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID
ORDER BY [Customer!1!CustomerID] ,
         [SalesOrder!2!SalesOrderID!ID],  
         [Customer!1!SalesOrderIDList!IDREFS]  
FOR XML EXPLICIT;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des EXPLICIT-Modus mit FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
