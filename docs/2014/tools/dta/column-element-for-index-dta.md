---
title: Column-Element für Index (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef7972014dff498172b9c016b3a7debb79a054fa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149850"
---
# <a name="column-element-for-index-dta"></a>Column-Element für Index (DTA)
  Gibt die Spalten an, für die der Index für eine benutzerspezifische Konfiguration erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|Spaltenattribut|Description|  
|----------------------|-----------------|  
|`Type`|Dies ist optional. Gibt den Indexspaltentyp an. Mit einem **string** -Datentyp können Sie dieses Attribut mit einem der folgenden zulässigen Werte angeben:<br /><br /> `KeyColumn`:<br />                  Gibt an, dass durch einen Indexschlüssel auf die Spalte verwiesen wird. Verwenden Sie die folgende Syntax, um dieses Attribut festzulegen:<br />`<Column Type="KeyColumn">`<br />Weitere Informationen zu Schlüsselspalten finden Sie unter [Beschreibung von gruppierten und nicht gruppierten Indizes](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).<br /><br /> `IncludedColumn`: Gibt an, dass die Spalte eine eingeschlossene Spalte ist (statt einer Schlüsselspalte). Verwenden Sie die folgende Syntax, um dieses Attribut festzulegen:<br />`<Column Type="IncludedColumn">`<br />Weitere Informationen zu eingeschlossenen Spalten finden Sie unter [Erstellen von Indizes mit eingeschlossenen Spalten](../../relational-databases/indexes/create-indexes-with-included-columns.md).|  
|`SortOrder`|Dies ist optional. Gibt die Sortierreihenfolge der Spalte an. Mit einem **string** -Datentyp können Sie die Sortierreihenfolge wie folgt als **Aufsteigend** oder **Absteigend** angeben:<br /><br /> `<Column SortOrder="Ascending">`|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Angabe von bis zu 1024 Spalten für das `Index`-Element möglich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Index-Element &#40;DTA&#41;](index-element-dta.md)|  
|**Untergeordnete Elemente**|[Name-Element für Spalte &#40;DTA&#41;](name-element-for-column-dta.md)|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Beispiel für eine XML-Eingabedatei mit benutzerdefinierter Konfiguration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
