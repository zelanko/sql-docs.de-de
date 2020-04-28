---
title: Last-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- last function [XQuery]
- fn:last function
ms.assetid: dc92086e-3b01-4b0b-9f54-3bbf306cf7ae
author: rothja
ms.author: jroth
ms.openlocfilehash: 04cb465c5180b829ff7d125c1695c3865c3f33c7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68039006"
---
# <a name="context-functions---last-xquery"></a>Kontextfunktionen – last (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt die Anzahl der Elemente in der Sequenz zurück, die zurzeit verarbeitet wird. Insbesondere wird der ganzzahlige Index des letzten Elements in der Sequenz zurückgegeben. Das erste Element in der Sequenz besitzt den Indexwert 1.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:last() as xs:integer  
```  
  
## <a name="remarks"></a>Bemerkungen  
 In SQL Server kann **FN: Last ()** nur im Kontext eines kontextabhängigen Prädikats verwendet werden. Insbesondere kann die Funktion nur innerhalb von Klammern (`[ ]`) verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Dieses Thema stellt XQuery-Beispiele für XML-Instanzen bereit, die in verschiedenen Spalten vom Typ **XML** in der AdventureWorks-Datenbank gespeichert sind.  
  
### <a name="a-using-the-last-xquery-function-to-retrieve-the-last-two-manufacturing-steps"></a>A. Verwenden der last()-Funktion von XQuery zum Abrufen der letzten beiden Fertigungsschritte  
 Die folgende Abfrage ruft die letzten beiden Fertigungsschritte für ein bestimmtes Produktmodell ab. Der Wert, die Anzahl der Fertigungsschritte, die von der **Last ()** -Funktion zurückgegeben wird, wird in dieser Abfrage verwendet, um die letzten beiden Fertigungsschritte abzurufen.  
  
```  
SELECT ProductModelID, Instructions.query('   
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  <LastTwoManuSteps>  
   <Last-1Step>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[(last()-1)]/text() }  
   </Last-1Step>  
   <LastStep>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[last()]/text() }  
   </LastStep>  
  </LastTwoManuSteps>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 In der vorherigen Abfrage gibt die **Last ()** -Funktion in`/AWMI:root//AWMI:Location)[1]/AWMI:step[last()]` /die Anzahl der Fertigungsschritte zurück. Dieser Wert wird zum Abrufen des letzten Fertigungsschritts am Arbeitsplatzstandort verwendet.  
  
 Dies ist das Ergebnis:  
  
```  
ProductModelID Result    
-------------- -------------------------------------  
7      <LastTwoManuSteps>  
         <Last-1Step>  
            When finished, inspect the forms for defects per   
            Inspection Specification .  
         </Last-1Step>  
         <LastStep>Remove the frames from the tool and place them   
            in the Completed or Rejected bin as appropriate.  
         </LastStep>  
       </LastTwoManuSteps>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [XQuery-Funktionen für den xml-Datentyp](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
