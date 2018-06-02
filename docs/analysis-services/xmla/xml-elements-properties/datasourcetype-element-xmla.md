---
title: DataSourceType-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 015a4cfbb70ddb29216a079dffdfd928029033d3
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34575672"
---
# <a name="datasourcetype-element-xmla"></a>DataSourceType-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Gibt an, ob eine [Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) für angegebene Element ein [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) oder [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) Befehl ist, lokal oder remote.  
  
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
|Standardwert|*Remoteserver*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Speicherort](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das **DataSourceType** -Element bestimmt, ob die Datenquelle, die vom **Location** -Element definiert wird, eine lokale Datenquelle oder eine Remote-Datenquelle enthält. Weitere Informationen zum Sichern und Wiederherstellen von Remotepartitionen finden Sie unter [sichern, wiederherstellen und Synchronisieren von Datenbanken &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*lokale*|Das **Location** -Element definiert eine lokale Datenquelle. Wenn dieser Wert verwendet wird, verwenden die **Restore** - und **Synchronize** -Befehle die Informationen, die im **Location** -Element definiert werden, um die Datenquelle zu aktualisieren. Diese wurde entweder aus der Sicherungsdatei abgerufen, die im **File** -Element für den **Backup** -Befehl angegeben ist, oder aus der Datenbank, die im **Source** -Element für den **Synchronize** -Befehl angegeben ist, der im **DataSourceID** -Element des **Location** -Elements definiert ist.<br /><br /> Dieser Wert ermöglicht es, dass Objekte, die ROLAP-Speicherung (relational OLAP) verwenden, nach der Wiederherstellung und Synchronisierung eine andere Datenbank für ihre Daten und Metadaten verwenden.<br /><br /> Hinweis: ROLAP-Daten, z. B. Daten in Dimensionstabellen oder Rückschreibetabellen werden nicht wiederhergestellt oder synchronisiert. Nur Metadaten für ROLAP-Objekte werden wiederhergestellt oder synchronisiert.|  
|*Remoteserver*|Das **Location** -Element definiert eine Remote-Datenquelle. Wenn dieser Wert verwendet wird, verwenden die **Restore** - und **Synchronize** -Befehle die Informationen, die im **Location** -Element definiert werden, um Remotepartitionen wiederherzustellen oder zu synchronisieren. Diese Partitionen wurden entweder aus der Sicherungsdatei, die im **File** -Element für den **Backup** -Befehl angegeben ist, oder aus der Datenbank, die im **Source** -Element für den **Synchronize** -Befehl angegeben ist, auf die Remoteinstanz, die in der **DataSourceID** des **Location** -Elements identifiziert wird, abgerufen.|  
  
## <a name="see-also"></a>Siehe auch
 [ConnectionString-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)   
 [DataSourceID-Element &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
