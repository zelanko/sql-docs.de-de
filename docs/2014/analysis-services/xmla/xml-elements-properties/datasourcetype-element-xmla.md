---
title: DataSourceType-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSourceType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSourceType
- microsoft.xml.analysis.datasourcetype
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceType
helpviewer_keywords:
- DataSourceType element
ms.assetid: f5a348b1-911b-4139-832e-4bcb6d80a728
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 54e374aad3980582f0653bc2e36c519b87d4a27b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169130"
---
# <a name="datasourcetype-element-xmla"></a>DataSourceType-Element (XMLA)
  Gibt an, ob eine [Speicherort](location-element-xmla.md) für die angegebene Element ein [wiederherstellen](../xml-elements-commands/restore-element-xmla.md) oder [synchronisieren](../xml-elements-commands/synchronize-element-xmla.md) Befehl ist, lokal oder remote.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Location>  
   ...  
   <DataSourceType>...</DataSourceType>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Remote*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Speicherort](location-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das `DataSourceType`-Element bestimmt, ob die Datenquelle, die vom `Location`-Element definiert wird, eine lokale Datenquelle oder eine Remote-Datenquelle enthält. Weitere Informationen zum Sichern und Wiederherstellen von Remotepartitionen finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*lokale*|Die `Location` -Element definiert eine lokale Datenquelle. Wenn dieser Wert verwendet wird, verwenden die `Restore`- und `Synchronize`-Befehle die Informationen, die im `Location`-Element definiert werden, um die Datenquelle zu aktualisieren. Diese wurde entweder aus der Sicherungsdatei abgerufen, die im `File`-Element für den `Backup`-Befehl angegeben ist, oder aus der Datenbank, die im `Source`-Element für den `Synchronize`-Befehl angegeben ist, der im `DataSourceID`-Element des `Location`-Elements definiert ist.<br /><br /> Dieser Wert ermöglicht es, dass Objekte, die ROLAP-Speicherung (relational OLAP) verwenden, nach der Wiederherstellung und Synchronisierung eine andere Datenbank für ihre Daten und Metadaten verwenden. **Hinweis:** ROLAP-Daten, z. B. Daten in Dimensionstabellen oder Rückschreibetabellen werden nicht wiederhergestellt oder synchronisiert. Nur Metadaten für ROLAP-Objekte werden wiederhergestellt oder synchronisiert.|  
|*Remote*|Das `Location`-Element definiert eine Remote-Datenquelle. Wenn dieser Wert wird verwendet, die `Restore` und `Synchronize` Befehle verwenden Sie die Informationen, die definiert, der `Location` Element wiederherstellen oder Synchronisieren von Remotepartitionen, abgerufen aus die Sicherungsdatei, die im angegebenen die `File` Element der `Backup` Befehl oder der Datenbank die `Source` -Element für die `Synchronize` Befehl, auf die Remoteinstanz identifiziert, die der `DataSourceID` von der `Location` Element.|  
  
## <a name="see-also"></a>Siehe auch  
 [ConnectionString-Element &#40;XMLA&#41;](connectionstring-element-xmla.md)   
 [DataSourceID-Element &#40;XMLA&#41;](id-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
