---
title: -Element (XMLA) sperren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Lock Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Lock
- microsoft.xml.analysis.lock
- http://schemas.microsoft.com/analysisservices/2003/engine#Lock
helpviewer_keywords:
- Lock command
ms.assetid: a819e805-4793-43bb-8af3-16a19f8bdab3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aee5d603c2708cb42b666d3cc0c9acc5ea208f0b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079520"
---
# <a name="lock-element-xmla"></a>Lock-Element (XMLA)
  Sperrt ein bestimmtes Objekt auf eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Lock>  
      <ID>...</ID>  
      <Object>...</Object>  
      <Mode>...</Mode>  
   </Lock>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[ID](../xml-elements-properties/id-element-xmla.md), [Modus](../xml-elements-properties/mode-element-xmla.md), [Objekt](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `Lock` -Befehl sperrt die gemeinsame oder exklusive Nutzung innerhalb des Kontexts der gerade aktiven Transaktion ein Objekt. Nur Datenbankadministratoren oder Serveradministratoren können explizit einen `Lock`-Befehl ausgeben. Eine Sperre in einem Objekt verhindert, dass ein Commit für Transaktionen ausgeführt wird, bevor die Sperre entfernt wurde. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt zwei Arten von Sperren: gemeinsame Sperren und exklusive Sperren. Weitere Informationen zu der von unterstützten Sperrentypen [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], finden Sie unter [Mode-Element &#40;XMLA&#41;](../xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ermöglicht nur die Sperrung von Datenbanken. Die `Object` -Element muss einen Objektverweis auf enthalten eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank. Wenn das `Object`-Element nicht angegeben ist oder wenn das `Object`-Element auf ein Objekt verweist, bei dem es sich nicht um eine Datenbank handelt, tritt ein Fehler auf.  
  
 Andere Befehle geben implizit eine `Lock` Befehl eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Datenbank. Jeder Vorgang, der Daten oder Metadaten aus einer Datenbank, z. B. eine liest `Discover` Methode oder ein `Execute` ausgeführte Methode ein `Statement` Befehl, gibt implizit eine gemeinsame Sperre für die Datenbank. Jede Transaktion, die Daten- oder Metadatenänderungen an ein Objekt auf einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Datenbank übermittelt (z. B. eine `Execute`-Methode, die einen `Alter`-Befehl ausführt), gibt implizit eine exklusive Sperre der Datenbank aus.  
  
 Alle Sperren werden im Kontext der aktuellen Transaktion abgehalten. Wenn die aktuelle Transaktion ausgeführt oder für diese ein Rollback durchgeführt wird, werden alle Sperren, die innerhalb der Transaktion definiert sind, automatisch aufgehoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Element Entsperren &#40;XMLA&#41;](lock-element-xmla.md)   
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
