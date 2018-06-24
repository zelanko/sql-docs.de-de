---
title: Workload-Element (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 71a7bfe2fe4d613117c1b52e83a7767a474a791e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059934"
---
# <a name="workload-element-dta"></a>Workload-Element (DTA)
  Gibt die für eine Optimierungssitzung zu verwendende Arbeitsauslastung an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich für jedes `DTAInput` Element.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Starten und Verwenden des Datenbankoptimierungsratgebers](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|**Untergeordnete Elemente**|[Datei Element &#40;DTA&#41;](file-element-dta.md)<br /><br /> [Database-Element für die Arbeitsauslastung &#40;DTA&#41;](database-element-for-workload-dta.md)<br /><br /> [EventString-Element &#40;DTA&#41;](eventstring-element-dta.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die Arbeitsauslastung besteht aus einer Reihe von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, die für eine oder mehrere Datenbanken ausgeführt werden, die Sie optimieren möchten. Der Datenbankoptimierungsratgeber kann [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts, Ablaufverfolgungsdateien und Ablaufverfolgungstabellen als Arbeitsauslastung verwenden.  
  
 Wenn Sie sowohl in einer XML-Eingabedatei als auch mit dem Tool **dta** in der Befehlszeile eine Arbeitsauslastung angeben, wird die in der Befehlszeile angegebene Arbeitsauslastung für die Optimierung verwendet. Alle Optimierungsoptionen, die in der Befehlszeile angegeben sind, überschreiben die in XML-Eingabedateien angegebenen Optionen. Die einzige Ausnahme hiervon sind benutzerdefinierte Konfigurationen, die im Auswertungsmodus in der XML-Eingabedatei eingegeben werden. Angenommen, eine Konfiguration im eingegeben werden die `Configuration` Element der XML-Eingabedatei und die `EvaluateConfiguration` Element auch als eine der Optimierungsoptionen angegeben ist, die in der XML-Eingabedatei angegebenen Optimierungsoptionen werden am eingegebenen Optimierungsoptionen überschrieben die Befehlszeile.  
  
 Die Angabe einer Arbeitsauslastung ist für jede Optimierungssitzung erforderlich.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel gibt die **MyDatabase.MyDBOwner.TuningTable001** -Ablaufverfolgungstabelle für das `Workload` Element. Die **TuningTable001** -Tabelle wurde mithilfe der Optimierungsvorlage von SQL Server Profiler und Speichern der Ablaufverfolgungsausgabe als Tabelle erstellt.  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="see-also"></a>Siehe auch  
 
  [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  