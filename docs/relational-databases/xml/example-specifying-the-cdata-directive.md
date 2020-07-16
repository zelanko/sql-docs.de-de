---
title: 'Beispiel: Angeben der CDATA-Anweisung | Microsoft-Dokumentation'
description: Sehen Sie sich ein Beispiel für das Angeben der CDATA-Direktive an, um die angegebenen Daten in einem CDATA-Abschnitt zu umschließen.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- CDATA directive
ms.assetid: 949071e6-787f-480d-bb86-3ac16a027af1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1e0c768d68c1bf7bb8d5c08b3967b4172fbdca36
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85632629"
---
# <a name="example-specifying-the-cdata-directive"></a>Beispiel: Angeben der CDATA-Anweisung
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Wird die Direktive auf **CDATA**festgelegt, werden die enthaltenen Daten nicht entitätscodiert, sondern in den CDATA-Abschnitt eingefügt. Die **CDATA** -Attribute müssen namenlos sein.  
  
 In der folgenden Abfrage wird die Produktmodell-Zusammenfassungsbeschreibung von einem CDATA-Abschnitt umgeben.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        '<Summary>This is summary description</Summary>'     
            as [ProductModel!1!!CDATA] -- no attribute name so ELEMENT assumed  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 Dies ist das Ergebnis:  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
   <![CDATA[<Summary>This is summary description</Summary>]]>  
</ProductModel>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des EXPLICIT-Modus mit FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
