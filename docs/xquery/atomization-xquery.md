---
title: Atomisierung (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, atomization
- atomization [XQuery]
ms.assetid: e3d7cf2f-c6fb-43c2-8538-4470a6375af5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bddb70c6c79ab983d1931bb17c741ff0dd531857
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047594"
---
# <a name="atomization-xquery"></a>Atomisierung (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Atomisierung ist das Verfahren, durch das der typisierte Wert eines Elements extrahiert wird. Dieses Verfahren wird unter bestimmten Umständen implizit verwendet. Bestimmte XQuery-Operatoren, wie z. B. arithmetische und Vergleichsoperatoren, sind von diesem Verfahren abhängig. Z. B. Wenn Sie arithmetische Operatoren direkt auf Knoten anwenden, der typisierte Wert eines Knotens wird zuerst abgerufen durch den Aufruf implizit die [datenfunktion](../xquery/data-accessor-functions-data-xquery.md). Auf diese Weise wird der atomare Wert dem arithmetischen Operator als Operand übergeben.  
  
 Die folgende Abfrage gibt beispielsweise den Gesamtwert der LaborHours-Attribute zurück. In diesem Fall **data()** implizit auf die Attributknoten angewendet wird.  
  
```  
declare @x xml  
set @x='<ROOT><Location LID="1" SetupTime="1.1" LaborHours="3.3" />  
<Location LID="2" SetupTime="1.0" LaborHours="5" />  
<Location LID="3" SetupTime="2.1" LaborHours="4" />  
</ROOT>'  
-- data() implicitly applied to the attribute node sequence.  
SELECT @x.query('sum(/ROOT/Location/@LaborHours)')  
```  
  
 Obwohl nicht erforderlich ist, können Sie auch explizit angeben der **data()** Funktion:  
  
```  
SELECT @x.query('sum(data(ROOT/Location/@LaborHours))')  
```  
  
 Ein anderes Beispiel für die implizite Atomisierung ist das Verwenden von arithmetischen Operatoren. Die **+** Operator erfordert atomarer Werte und **data()** implizit angewendet, um den atomaren Wert des LaborHours-Attributs abrufen. Die Abfrage wird angegeben, für die Instructions-Spalte, der die **Xml** Typ in der ProductModel-Tabelle. Die folgende Abfrage gibt das LaborHours-Attribut dreimal zurück. Beachten Sie in der Abfrage Folgendes:  
  
-   Bei der Konstruktion des OriginalLaborHours-Attributs wird die Atomisierung implizit auf die von (`$WC/@LaborHours`) zurückgegebene Singleton-Sequenz angewendet. Der typisierte Wert des LaborHours-Attributs wird anschließend dem OriginalLaborHours-Attribut zugewiesen.  
  
-   Bei der Konstruktion des UpdatedLaborHoursV1-Attributs macht der arithmetische Operator atomare Werte erforderlich. Aus diesem Grund **data()** implizit auf das von zurückgegebene LaborHours-Attributs angewendet wird (`$WC/@LaborHours`). Anschließend wird dem Attribut der atomare Wert 1 hinzugefügt. Die Konstruktion des updatedlaborhoursv2 zeigt die explizite Anwendung von **data()** , ist jedoch nicht erforderlich.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in /AWMI:root/AWMI:Location[1]  
        return  
            <WC OriginalLaborHours = "{ $WC/@LaborHours }"  
                UpdatedLaborHoursV1 = "{ $WC/@LaborHours + 1 }"   
                UpdatedLaborHoursV2 = "{ data($WC/@LaborHours) + 1 }" >  
            </WC>') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Dies ist das Ergebnis:  
  
```  
<WC OriginalLaborHours="2.5"   
    UpdatedLaborHoursV1="3.5"   
    UpdatedLaborHoursV2="3.5" />  
```  
  
 Aus der Atomisierung ergibt sich eine Instanz eines einfachen Datentyps, ein leeres Dataset oder ein Fehler bezüglich des statischen Typs.  
  
 Atomisierung tritt auch in Funktionen, Rückgabewerte von Funktionen, die an Parametern **cast()** Ausdrücke und Sortierung Ausdrücke, die in der Order by-Klausel übergeben.  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery-Grundlagen](../xquery/xquery-basics.md)   
 [Vergleichsausdrücke &#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)   
 [XQuery Functions against the xml Data Type (XQuery-Funktionen für den xml-Datentyp)](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
