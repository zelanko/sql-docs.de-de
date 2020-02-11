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
ms.openlocfilehash: a5f28b5d593524288a755f4c9455bba39554d7bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924814"
---
# <a name="namespaces"></a>Namespaces
Das XML-Persistenzformat in ADO verwendet die folgenden vier Namespaces.  
  
## <a name="remarks"></a>Bemerkungen  
 Das XML-Persistenzformat in ADO verwendet die folgenden vier Namespaces.  
  
|Präfix|BESCHREIBUNG|  
|------------|-----------------|  
|s|Verweist auf den "XML-Data"-Namespace, der die Elemente und Attribute enthält, die das Schema des aktuellen Recordsets definieren.|  
|dt|Bezieht sich auf die Spezifikation der Datentyp Definitionen.|  
|rs|Verweist auf den Namespace, der Elemente und Attribute enthält, die für Eigenschaften und Attribute von ADO-Recordsets spezifisch sind.|  
|z|Verweist auf das Schema des aktuellen Rowsets.|  
  
 Ein Client sollte diesen Namespaces, wie in der Spezifikation definiert, keine eigenen Tags hinzufügen. Ein Client sollte z. b. keinen Namespace als "urn: Schemas-Microsoft-com: Rowset" definieren und dann etwas wie "RS: myowntag" schreiben. Weitere Informationen zu Namespaces finden Sie in der [Empfehlung zu W3C-Namespaces in XML](http://www.w3.org/TR/REC-xml-names/).  
  
> [!IMPORTANT]
>  Die ID für das Schemaset muss "Rowsetschema" lauten, und der Namespace, der zum Verweisen auf das Schema des aktuellen Rowsets verwendet wird, muss auf "#RowsetSchema" zeigen.  
  
 Beachten Sie, dass das Präfix des-Namespace-der Teil zwischen dem Doppelpunkt und dem Gleichheitszeichen willkürlich ist.  
  
```  
xmlns:rs="urn:schemas-microsoft-com:rowset"  
```  
  
 Der Benutzer kann dies als beliebiger Name definieren, solange dieser Name konsistent im gesamten XML-Dokument verwendet wird. ADO schreibt immer "s", "RS", "DT" und "z", aber diese Präfix Namen sind nicht in der Lade Komponente hart codiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
