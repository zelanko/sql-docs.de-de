---
title: Namespaces | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- namespaces in ADO
ms.assetid: efff5569-db52-451d-a039-2e74870534da
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e352a6c4d548b382d700c54cf0167fadcec8bf7b
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54254545"
---
# <a name="namespaces"></a>Namespaces
Die XML-Speicherformat in ADO verwendet die folgenden vier Namespaces.  
  
## <a name="remarks"></a>Hinweise  
 Die XML-Speicherformat in ADO verwendet die folgenden vier Namespaces.  
  
|Präfix|Description|  
|------------|-----------------|  
|s|Bezieht sich auf der "XML-Daten"-Namespace enthält die Elemente und Attribute, die das Schema der aktuellen Recordset zu definieren.|  
|dt|Bezieht sich auf die Definitionen der Datentypspezifikation.|  
|rs|Bezieht sich auf die enthaltenden Namespace-Elementen und Attributen, die spezifisch für ADO-Recordset-Eigenschaften und Attribute.|  
|z|Bezieht sich auf das Schema des aktuellen Rowsets.|  
  
 Ein Client sollte nicht auf diese Namespaces eine eigene Tags hinzufügen, gemäß der Spezifikation. Ein Client sollte beispielsweise nicht definieren ein Namespaces als "Urn: Schemas-Microsoft-Com:rowset", und klicken Sie dann schreiben Sie etwas wie "Rs: MyOwnTag." Weitere Informationen zu Namespaces finden Sie unter den [W3C Empfehlung zu Namespaces in XML-](http://www.w3.org/TR/REC-xml-names/).  
  
> [!IMPORTANT]
>  Die ID für das Schematag muss "RowsetSchema lauten", und der Namespace, der zum Verweisen auf das Schema des aktuellen Rowsets muss zeigen Sie auf "#RowsetSchema."  
  
 Beachten Sie, dass das Präfix des Namespace - den Teil zwischen dem Doppelpunkt und dem Gleichheitszeichen - beliebige ist.  
  
```  
xmlns:rs="urn:schemas-microsoft-com:rowset"  
```  
  
 Der Benutzer kann definieren, diese Option, um einen beliebigen Namen sein, sofern dieser Name konsistent im gesamten XML-Dokument verwendet wird. ADO schreibt immer "s", "Rs", "dt" und "Z", aber diese Präfixnamen sind nicht hartcodiert die Komponente laden.  
  
## <a name="see-also"></a>Siehe auch  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
