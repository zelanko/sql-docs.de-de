---
title: SQL Server-Monitor (Übersicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlservermonitor.main.f1
helpviewer_keywords:
- SQL Server Monitor [SQL Server]
ms.assetid: 048ae16d-31c3-489a-9f1e-1400a3bacd39
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 889e0c5a54477a1532aa9ec2760fad890a671618
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62755181"
---
# <a name="sql-server-monitor-overview"></a>SQL Server-Monitor (Übersicht)
  SQL Server-Monitor führt keine Überwachungsfunktionen aus, hostet jedoch Module, die diese Funktionen ausführen. Zu den SQL Server-Monitor-Modulen gehören der Replikationsmonitor und der Datenbankspiegelungs-Monitor.  
  
 Wählen Sie das betreffende Modul im Menü **Wechseln zu** aus, um eines dieser Module zu verwenden. Das aktuell ausgewählte Modul ist im Besitz des Inhalts der Navigations- und Detailbereiche, der Benutzerinteraktionen in den Detailbereichen und der Abfragen für Inhalt und Status.  
  
> [!NOTE]  
>  Weitere Informationen zu diesen Monitoren finden Sie unter [Überwachen der Replikation](../../relational-databases/replication/monitoring-replication.md) und [Überwachen der Datenbankspiegelung &#40;SQL Server&#41;](../database-mirroring/database-mirroring-sql-server.md).  
  
## <a name="permissions"></a>Berechtigungen  
  
-   Replikationsmonitor  
  
     Zum Überwachen der Replikation müssen Sie Mitglied der festen Serverrolle **sysadmin** auf dem Verteiler oder Mitglied der festen Datenbankrolle **replmonitor** in der Verteilungsdatenbank sein. Ein Systemadministrator kann jeden Benutzer zur **replmonitor** -Rolle hinzufügen. Anhand dieser Rolle kann ein Benutzer die Replikationsaktivität im Replikationsmonitor anzeigen. Er kann die Replikation jedoch nicht verwalten.  
  
-   Datenbankspiegelungs-Monitor  
  
     Zum Überwachen der Datenbankspiegelung müssen Sie entweder Mitglied der festen Serverrolle **sysadmin** oder der festen Datenbankrolle **dbm_monitor** in der Serverinstanz sein. Wenn Sie Mitglied von **sysadmin** oder **dbm_monitor** auf nur einer der Partnerserverinstanzen sind, kann der Monitor nur mit diesem Partner eine Verbindung herstellen. Der Monitor kann keine Informationen von dem anderen Partner abrufen. Weitere Informationen finden Sie unter [Database Mirroring Monitor Overview](../database-mirroring/database-mirroring-monitor-overview.md).  
  
## <a name="menu-options"></a>Menüoptionen  
 Der SQL Server-Monitor hat ein Menü mit Befehlen, die sich auf den SQL Server-Monitor beziehen. Dieses Menü kann auch Befehle des ausgewählten Moduls enthalten.  
  
 Die folgenden Menüoptionen beziehen sich auf den SQL Server-Monitor.  
  
 **File**  
 Das Menü enthält den Befehl **Beenden** .  
  
 **Aktion**  
 Enthält das Kontextmenü des Knotens, der in der Navigationsstruktur ausgewählt ist.  
  
 **Wechseln zu**  
 Enthält eine Liste mit Überwachungskomponenten:  
  
-   Datenbankspiegelung  
  
-   Replikation  
  
 **So verwenden Sie SQL Server Management Studio zum Überwachen der Datenbankspiegelung**  
  
-   [Starten des Datenbankspiegelungs-Monitors &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Datenbankspiegelung &#40;SQL Server&#41;](../database-mirroring/database-mirroring-sql-server.md)  
  
  
