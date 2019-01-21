---
title: 'Beispiel: Angeben der ELEMENTXSINIL-Direktive | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENTXSINIL directive
ms.assetid: bbcb6f9e-a51b-4775-9795-947c9d6d758f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 050681b0b215d8dc8625bf6a4480d47c50c89b55
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54256585"
---
# <a name="example-specifying-the-elementxsinil-directive"></a>Beispiel: Angeben der ELEMENTXSINIL-Direktive
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Wenn Sie zum Abrufen einer elementzentrierten XML-Ausgabe die ELEMENT-Direktive angeben, und eine Spalte einen NULL-Wert aufweist, wird das entsprechende Element im EXPLICIT-Modus nicht generiert. Sie können optional die ELEMENTXSINIL-Direktive angeben, um das Generieren von Elementen für NULL-Werte anzufordern, wenn das **xsi:nil** -Attribut auf TRUE festgelegt ist.  
  
 Die folgende Abfrage konstruiert eine XML-Ausgabe, die die Adressen der Mitarbeiter enthält. Für die Spalten `AddressLine2` und `City` ist in den Spaltennamen die `ELEMENTXSINIL` -Direktive angegeben. So werden für NULL-Werte in der `AddressLine2` - und `City` -Spalte des Rowsets Elemente generiert.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID  as [Employee!1!EmpID],  
       BEA.AddressID as [Employee!1!AddressID],  
       NULL        as [Address!2!AddressID],  
       NULL        as [Address!2!AddressLine1!ELEMENT],  
       NULL        as [Address!2!AddressLine2!ELEMENTXSINIL],  
       NULL        as [Address!2!City!ELEMENTXSINIL]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.BusinessEntityAddress AS BEA  
    ON E.BusinessEntityID = BEA.BusinessEntityID  
  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       BEA.AddressID,  
       A.AddressID,  
       AddressLine1,   
       AddressLine2,  
       City   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.BusinessEntityAddress AS BEA  
    ON E.BusinessEntityID = BEA.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BEA.AddressID = A.AddressID  
ORDER BY [Employee!1!EmpID],[Address!2!AddressID]  
FOR XML EXPLICIT;  
```  
  
 Dies ist das Teilergebnis:  
  
 `<Employee xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`  
  
 `EmpID="1" AddressID="249">`  
  
 `<Address AddressID="249">`  
  
 `<AddressLine1>4350 Minute Dr.</AddressLine1>`  
  
 `<AddressLine2 xsi:nil="true" />`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</Employee>`  
  
 `...`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des EXPLICIT-Modus mit FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
