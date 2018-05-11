---
title: Geben Sie-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ef8d986b50eb3d5efc8e490f198862be7400e566
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="type-element-xmla"></a>Type-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Bestimmt den Typ der Verarbeitung, die vom [Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) -Element ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Verarbeiten](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Verarbeitung verfügbaren Optionen auf Objekte in einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], finden Sie unter [Verarbeiten eines mehrdimensionalen Modells &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Der Wert des **Type** -Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*"ProcessFull"*|Löscht alle Daten im betroffenen Objekt und verarbeitet dann das betroffene Objekt.|  
|*"Processadd"*|Fügt dem betroffenen Objekt neue Daten hinzu.|  
|*ProcessUpdate*|Aktualisiert die Daten im betroffenen Objekt.|  
|*ProcessIndexes*|Erstellt Indizes und Aggregationen im betroffenen Objekt oder erstellt diese neu.|  
|*ProcessScriptCache*|Wenn der Cube verarbeitet wird, erstellt der Server den MDX-Skriptcache neu. Wenn nicht, wird ein Fehler ausgelöst.<br /><br /> **Hinweis** Gilt nur für Cube.|  
|*ProcessData*|Verarbeitet Daten nur im betroffenen Objekt.|  
|*ProcessDefault*|Erkennt den Status des betroffenen Objekts und führt die geeignete Verarbeitungsoption am betroffenen Objekt durch, um eine vollständige Optimierung des Objekts zu erreichen und den Status der vollständigen Verarbeitung zurückzugeben.|  
|*ProcessClear*|Löscht die Daten im betroffenen Objekt und allen verknüpften Objekten.|  
|*ProcessStructure*|Verarbeitet nur die Struktur des betroffenen Objekts.|  
|*' ProcessClearStructureOnly '*|Löscht Daten nur aus dem betroffenen Objekt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
