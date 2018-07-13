---
title: Befehl Events Data Columns | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Command Events event category
ms.assetid: 7169f1e2-c6be-4d8c-b147-25719b84bc2c
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2e38ee67b5d8e4f0926ff93c45985b6246d8693f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169531"
---
# <a name="command-events-data-columns"></a>Datenspalten für Befehlsereignisse
  In der folgenden Tabelle sind die Datenspalten für jede Ereignisklasse in der **Befehlsereignisse** -Ereigniskategorie aufgeführt.  
  
 Die **Befehlsereignisse** -Ereigniskategorie weist folgende Ereignisklassen auf:  
  
-   [Command Begin-Klasse](#bkmk_1)  
  
-   [Command End-Klasse](#bkmk_2)  
  
 In den folgenden Tabellen sind die Datenspalten für jede dieser Ereignisklassen aufgeführt.  
  
##  <a name="bkmk_1"></a> Command Begin-Klasse – Datenspalten  
  
|Datenspalte|Description|  
|-----------------|-----------------|  
|ConnectionID|Enthält die eindeutige Verbindungs-ID, die dem Befehlsereignis zugeordnet ist.|  
|TextData|Enthält die eindeutigen Textdaten, die dem Befehlsereignis zugeordnet sind.|  
|ServerName|Enthält den Namen der Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , in der das Befehlsereignis aufgetreten ist.|  
|CurrentTime|Enthält die aktuelle Zeit des Befehlsereignisses.|  
|DatabaseName|Enthält den Namen der Datenbank, in der der Befehl ausgeführt wird.|  
|EventSubclass|Enthält die Ereignisklasse innerhalb des Befehlsereignisses. Die Werte sind:<br /><br /> 0: Create<br />1: Alter<br />2: Delete<br />3: Process<br />4: DesignAggregations<br />5: WBInsert<br />6: WBUpdate<br />7: WBDelete<br />8: Backup<br />9: Restore<br />10: MergePartitions<br />11: Subscribe<br />12: Batch<br />13: BeginTransaction<br />14: CommitTransaction<br />15: RollbackTransaction<br />16: GetTransactionState<br />17: Cancel<br />18: Synchronize<br />19: Import80MiningModels<br />20: Attach<br />21: Detach<br />22: SetAuthContext<br />23: ImageLoad<br />24: ImageSave<br />10000: Other|  
|NTUserName|Enthält den Windows-Benutzernamen, der dem Befehlsereignis zugeordnet ist. Der Benutzername liegt im kanonischen Format vor. Beispiel: engineering.microsoft.com/software/user.|  
|RequestProperties|Enthält die XMLA-Anforderungseigenschaften (XML for Analysis), die dem Befehlsereignis zugeordnet sind.|  
|SPID|Enthält die Serverprozess-ID (SPID), mit der die Benutzersitzung eindeutig identifiziert wird, die dem Befehlsereignis zugeordnet ist. Die SPID entspricht direkt dem von XMLA verwendeten Sitzungs-GUID.|  
|StartTime|Enthält die Zeit, zu der das Befehlsereignis gestartet wurde, falls verfügbar.|  
|SessionType|Enthält die Entität, die den Vorgang verursacht hat.|  
|NTDomainName|Enthält das Windows-Domänenkonto, das dem Objektberechtigungsereignis zugeordnet ist.|  
|ClientProcessID|Enthält die eindeutige Clientprozess-ID, die dem Befehlsereignis zugeordnet ist.|  
  
##  <a name="bkmk_2"></a> Command End-Klasse – Datenspalten  
  
|Datenspalte|Description|  
|-----------------|-----------------|  
|ConnectionID|Enthält die eindeutige Verbindungs-ID, die dem Befehlsereignis zugeordnet ist.|  
|TextData|Enthält die eindeutigen Textdaten, die dem Befehlsereignis zugeordnet sind.|  
|ServerName|Enthält den Namen der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , in der das Befehlsereignis aufgetreten ist.|  
|CurrentTime|Enthält die aktuelle Zeit des Befehlsereignisses. Für das Filtern stehen die Formate *JJJJ*-*MM*-*TT* und *JJJJ*-*MM*-*TT HH*:*MM*:*SS*zur Verfügung.|  
|DatabaseName|Enthält den Namen der Datenbank, in der der Befehl ausgeführt wird.|  
|Duration|Enthält die ungefähre Dauer zwischen dem Command Begin- und dem Command End-Ereignis.|  
|EndTime|Enthält die Zeit, zu der das Befehlsereignis endete. Für das Filtern stehen die Formate *JJJJ*-*MM*-*TT* und *JJJJ*-*MM*-*TT HH*:*MM*:*SS*zur Verfügung.|  
|EventSubclass|Enthält die Ereignisklasse innerhalb des Befehlsereignisses. Die Werte sind:<br /><br /> 0: Create<br />1: Alter<br />2: Delete<br />3: Process<br />4: DesignAggregations<br />5: WBInsert<br />6: WBUpdate<br />7: WBDelete<br />8: Backup<br />9: Restore<br />10: MergePartitions<br />11: Subscribe<br />12: Batch<br />13: BeginTransaction<br />14: CommitTransaction<br />15: RollbackTransaction<br />16: GetTransactionState<br />17: Cancel<br />18: Synchronize<br />19: Import80MiningModels<br />20: Attach<br />21: Detach<br />22: SetAuthContext<br />23: ImageLoad<br />24: ImageSave<br />10000: Other|  
|NTCanonicalUserName|Enthält den Windows-Benutzernamen, der dem Befehlsereignis zugeordnet ist. Der Benutzername liegt im kanonischen Format vor. Beispiel: engineering.microsoft.com/software/user.|  
|NTUserName|Enthält das Windows-Benutzerkonto, das dem Befehlsereignis zugeordnet ist.|  
|SPID|Enthält die Serverprozess-ID (SPID), mit der die Benutzersitzung eindeutig identifiziert wird, die dem Befehlsereignis zugeordnet ist. Die SPID entspricht direkt dem von XMLA verwendeten Sitzungs-GUID.|  
|StartTime|Enthält die Zeit, zu der das End-Befehlsereignis gestartet wurde, falls verfügbar.|  
|CPUTime|Enthält die CPU-Zeit (in Millisekunden), die vom Prozess zwischen dem Begin-Befehlsereignis und dem End-Befehlsereignis verwendet wurde.|  
|Fehler|Enthält die Fehlernummer jedes Fehlers, der dem Befehlsereignis zugeordnet ist.|  
|Schweregrad|Enthält den Schweregrad einer Ausnahme, die dem Befehlsereignis zugeordnet ist. Die Werte sind:<br /><br /> 0 = Erfolg<br /><br /> 1 = Information<br /><br /> 2 = Warnung<br /><br /> 3 = Fehler|  
|Success|Enthält die Erfolgs- bzw. Fehlschlagsinformation des Befehlsereignisses. Die Werte sind:<br /><br /> 0 = Fehler<br /><br /> 1 = Erfolg|  
|SessionType|Enthält die Entität, die die Operation verursacht hat, die dem End-Befehlsereignis zugeordnet ist.|  
|NTDomainName|Enthält das Windows-Domänenkonto, das dem Befehlsereignis zugeordnet ist.|  
|ClientProcessID|Enthält die eindeutige Clientprozess-ID, die dem Befehlsereignis zugeordnet ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Befehlsereignisse – Ereigniskategorie](command-events-event-category.md)  
  
  
