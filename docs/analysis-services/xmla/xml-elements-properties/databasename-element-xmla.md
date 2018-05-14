---
title: DatabaseName-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9cbf32fcc67c7a9e08d45d6099bf58bf521be6e2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="databasename-element-xmla"></a>DatabaseName-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Identifiziert die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbank, die vom übergeordneten [Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) -Befehl wiederhergestellt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Restore>  
   ...  
   <DatabaseName>...</DatabaseName>  
   ...  
</Restore>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Das **DatabaseName** -Element identifiziert die Datenbank, in die der **Restore** -Befehl eine Sicherungsdatei wiederherstellt. Wenn dieses Element nicht angegeben ist oder eine leere Zeichenfolge enthält, wird der Name der Datenbank verwendet, die in der Sicherungsdatei enthalten ist.  
  
 Wenn die Datenbank bereits auf einer Zielinstanz besteht, tritt ein Fehler auf, es sei denn, das **AllowOverwrite** -Element für den **Restore** -Befehl ist auf **True**gesetzt.  
  
## <a name="see-also"></a>Siehe auch  
 [AllowOverwrite-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
