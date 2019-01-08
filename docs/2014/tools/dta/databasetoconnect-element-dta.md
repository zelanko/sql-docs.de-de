---
title: DatabaseToConnect-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DatabaseToConnect element
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4fef2df598d96b33def41f27345f88226fd4c6b5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821924"
---
# <a name="databasetoconnect-element-dta"></a>DatabaseToConnect-Element (DTA)
  Gibt die erste Datenbank an, mit der der Datenbankoptimierungsratgeber beim Optimieren einer Arbeitsauslastung eine Verbindung herstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|`string`, unbegrenzte Länge.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Dies ist optional. Einmalige Verwendung pro `TuningOptions`-Element möglich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[TuningOptions-Element &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Untergeordnete Elemente**|None|  
  
## <a name="remarks"></a>Hinweise  
 Mit `DatabaseToConnect` können Sie den Namen der ersten Datenbank angeben, mit der der Datenbankoptimierungsratgeber beim Starten der Optimierungssitzung eine Verbindung herstellen soll. Sie können mithilfe dieses Elements nur eine Datenbank angeben. Wenn mehrere Datenbanknamen angegeben werden, gibt der Datenbankoptimierungsratgeber einen Fehler zurück.  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung finden Sie unter [Beispiel für eine XML-Eingabedatei mit Inlinearbeitsauslastung &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
