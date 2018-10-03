---
title: Verschieben einer Arbeitsauslastungsgruppe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties_moveworkloadgroup.f1
helpviewer_keywords:
- workload groups [SQL Server], move
- Resource Governor, workload group move
ms.assetid: f2068636-6e53-486a-a6fc-c12de2a38424
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7dd9fada1ffac50b11c4384f6ede19eac4ea069a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112880"
---
# <a name="move-a-workload-group"></a>Verschieben von Arbeitsauslastungsgruppen
  Arbeitsauslastungsgruppen der Ressourcenkontrolle können Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mit Transact-SQL in einen anderen Ressourcenpool verschieben.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **Zum Verschieben einer Arbeitsauslastungsgruppe mit:**  [SQL Server Management Studio](#MoveWGSSMS), [Transact-SQL](#MoveWGTSQL)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
 Sie können keine Arbeitsauslastungsgruppen verschieben, wenn für die Ressourcenkontrolle ein Konfigurationsvorgang aussteht.  
  
###  <a name="LimitationsRestrictions"></a> Einschränkungen  
 Sie können keine Arbeitsauslastungsgruppen verschieben, wenn für die Ressourcenkontrolle ein Konfigurationsvorgang aussteht. Sie können feststellen, ob eine ausstehende Konfiguration vorliegt, indem Sie die dynamische Verwaltungssicht [sys.dm_resource_governor_configuration &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) abfragen, um den aktuellen Status von „is_configuration_pending“ zu erhalten.  
  
###  <a name="Permissions"></a> Berechtigungen  
 Zum Verschieben einer Arbeitsauslastungsgruppe ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="MoveWGSSMS"></a> Verschieben einer Arbeitsauslastungsgruppe in SQL Server Management Studio  
 **So verschieben Sie eine Arbeitsauslastungsgruppe in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**  
  
1.  Erweitern Sie im Objekt-Explorer den Knoten **Verwaltung** , bis der erweiterte Eintrag **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Resource Governor** , und klicken Sie dann auf **Eigenschaften**. Damit öffnen Sie die Seite **Eigenschaften des Resource Governors** .  
  
3.  Klicken Sie im Fenster **Ressourcenpools** auf den Ressourcenpool mit der zu verschiebenden Arbeitsauslastungsgruppe. Im Fenster **Arbeitsauslastungsgruppen** werden nun die Arbeitsauslastungsgruppen in diesem Ressourcenpool aufgeführt.  
  
4.  Klicken Sie im Fenster **Arbeitsauslastungsgruppen** mit der rechten Maustaste links neben der zu verschiebenden Arbeitsauslastungsgruppe auf den Pfeil nach rechts, und klicken Sie auf **Verschieben nach**. Daraufhin wird das Fenster **Arbeitsauslastungsgruppe verschieben** angezeigt.  
  
5.  Verfügbare Ressourcenpools werden im Fenster angezeigt. Klicken Sie auf den Namen des Ressourcenpools, in den Sie die Arbeitsauslastungsgruppe verschieben möchten, und klicken Sie dann auf **OK** , um diese Aktion durchzuführen.  
  
6.  Diese Aktion wird erst abgeschlossen, wenn Sie auf **OK**klicken. Wenn Sie auf **OK**klicken, wird die Anweisung ALTER RESOURCE GOVERNOR RECONFIGURE ausgeführt.  
  
7.  Schlägt der Erstellungs- oder Neukonfigurierungsvorgang für den Ressourcenpool oder die Arbeitsauslastungsgruppe fehl, wird unter dem Titel der Eigenschaftenseite eine zusammenfassende Fehlermeldung angezeigt. Klicken Sie auf den Abwärtspfeil an der Fehlermeldung, um eine ausführliche Fehlermeldung anzuzeigen.  
  
##  <a name="MoveWGTSQL"></a> Verschieben einer Arbeitsauslastungsgruppe mit Transact-SQL  
 **So verschieben Sie eine Arbeitsauslastungsgruppe mit Transact-SQL**  
  
1.  Führen Sie die `ALTER WORKLOAD GROUP`-Anweisung aus, und geben Sie dabei den Namen der zu verschiebenden Arbeitsauslastungsgruppe sowie die Ressource an, in die diese verschoben werden soll.  
  
2.  Führen Sie die **ALTER RESOURCE GOVERNOR RECONFIGURE** -Anweisung aus.  
  
### <a name="example-transact-sql"></a>Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die Arbeitsauslastungsgruppe `groupAdhoc` in den Standardressourcenpool verschoben.  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Resource Governor](resource-governor.md)   
 [Aktivieren der Ressourcenkontrolle](enable-resource-governor.md)   
 [Erstellen eines Ressourcenpools](create-a-resource-pool.md)   
 [Erstellen einer Arbeitsauslastungsgruppe](create-a-workload-group.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
