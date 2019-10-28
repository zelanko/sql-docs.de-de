---
title: Anzeigen und Lösen von Datenkonflikten für Mergeveröffentlichungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db445d9c80c6a6e2552160dcff721c06d5c107e6
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72907790"
---
# <a name="conflict-resolution-for-merge-replication"></a>Konfliktlösung für die Mergereplikation
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Konflikte bei der Mergereplikation werden anhand des für den jeweiligen Artikel angegebenen Konfliktlösers gelöst. Standardmäßig werden Konflikte ohne Benutzereingriff gelöst. Konflikte können jedoch im Replikationskonflikt-Viewer von [!INCLUDE[msCoName](../../includes/msconame-md.md)] angezeigt und das Ergebnis der Konfliktlösung kann geändert werden.  
  
 Die Konfliktdaten sind im Replikationskonflikt-Viewer für den Zeitraum verfügbar, der als Beibehaltungsdauer der Konflikte (bei einer Standardeinstellung von 14 Tagen) angegeben wurde. Zum Festlegen der Beibehaltungsdauer der Konflikte haben Sie folgende Möglichkeiten:  
  
-   Geben Sie einen Beibehaltungswert für den Parameter `@conflict_retention` von [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) an.  
  
-   Geben Sie den Wert **conflict_retention** für den `@property`-Parameter und einen Beibehaltungswert für den `@value`-Parameter von [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) an.  
  
 Standardmäßig werden Konfliktinformationen an den folgenden Orten gespeichert:    
-   Auf dem Verleger und Abonnenten, wenn die Veröffentlichung mindestens einen Kompatibilitätsgrad von 90RTM aufweist.   
-   Auf dem Verleger, wenn die Veröffentlichung einen geringeren Kompatibilitätsgrad als 80RTM aufweist.   
-   Auf dem Verleger, wenn auf den Abonnenten [!INCLUDE[ssEW](../../includes/ssew-md.md)]ausgeführt wird. Konfliktdaten dürfen nicht auf Abonnenten mit [!INCLUDE[ssEW](../../includes/ssew-md.md)] gespeichert werden.  
  
 Das Speichern von Konfliktinformationen wird von der **conflict_logging** -Veröffentlichungseigenschaft gesteuert. Weitere Informationen finden Sie unter [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) und [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 Konflikte können während der Synchronisierung auch mit dem interaktiven [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Replikationskonfliktlöser gelöst werden. Der interaktive Konfliktlöser ist über die Synchronisierungsverwaltung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows verfügbar. Weitere Informationen finden Sie unter [Synchronisieren eines Abonnements mithilfe der Synchronisierungsverwaltung von Windows &#40;Synchronisierungsverwaltung von Windows&#41;](../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
## <a name="resolve-conflicts"></a>Auflösen von Konflikten  
  
1.  Stellen Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit dem Verleger (oder gegebenenfalls Abonnenten) her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Veröffentlichung, für die Sie die Konflikte anzeigen möchten, und klicken Sie dann auf **Konflikte anzeigen**.  
  
    > [!NOTE]  
    >  Wenn für die **conflict_logging** -Eigenschaft der Wert **'subscriber'** angegeben wurde, ist die Menüoption **Konflikte anzeigen** nicht verfügbar. Starten Sie zum Anzeigen von Konflikten ConflictViewer.exe von der Eingabeaufforderung aus. ConflictViewer.exe wird standardmäßig im folgenden Verzeichnis gespeichert: Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE. Eine Liste der gültigen Startparameter erhalten Sie, wenn Sie ConflictViewer.exe -? ausführen.  
  
4.  Wählen Sie im Dialogfeld **Konflikttabelle auswählen** eine Datenbank, eine Veröffentlichung und eine Tabelle aus, für die Sie die Konflikte anzeigen möchten.  
  
5.  Im Replikationskonflikt-Viewer können Sie folgende Aktionen ausführen:  
  
    -   Filtern Sie Zeilen mit den Schaltflächen rechts vom oberen Raster.  
  
    -   Wählen Sie eine Zeile im oberen Raster aus, um Informationen zur Zeile im unteren Raster anzuzeigen.  
  
    -   Wählen Sie eine oder mehrere Zeilen im oberen Raster aus, und klicken Sie auf **Entfernen**, was dem Klicken auf die Schaltfläche **Gewinner absenden** entspricht (ohne Änderungen an den Daten vorzunehmen).  
  
    -   Klicken Sie auf die Eigenschaftenschaltfläche ( **…** ), um weitere Informationen zu einer am Konflikt beteiligten Zeile anzuzeigen.  
  
    -   Bearbeiten Sie Daten in den Spalten **Konfliktgewinner** oder **Konfliktverlierer** , bevor Sie die Daten absenden (bei einer grauen Spalte sind die Daten schreibgeschützt).  
  
    -   Klicken Sie auf **Gewinner absenden** , um die als Gewinner des Konflikts ausgewiesene Spalte zu akzeptieren.  
  
    -   Klicken Sie auf **Verlierer absenden** , um die Konfliktlösung zu überschreiben und den als Verlierer des Konflikts ausgewiesenen Wert an alle Knoten der Topologie zu senden.  
  
    -   Aktivieren Sie **Details dieses Konflikts protokollieren** , um Konfliktdaten in einer Datei zu protokollieren. Um einen Speicherort für die Datei anzugeben, zeigen Sie auf das Menü **Ansicht** , und klicken Sie dann auf **Optionen**. Geben Sie einen Wert ein, oder klicken Sie auf die Schaltfläche mit den drei Punkten ( **...** ), und wechseln Sie in das entsprechende Verzeichnis. Klicken Sie auf **OK** , um das Dialogfeld **Optionen** zu beenden.  
  
6.  Schließen Sie den Replikationskonflikt-Viewer.  

## <a name="view-conflict-information"></a>Anzeigen von Konfliktinformationen
Wenn Konflikte während einer Mergereplikations aufgelöst werden, werden die Daten aus der verlierenden Zeile in eine Konflikttabelle geschrieben. Diese Konfliktdaten können programmgesteuert mithilfe gespeicherter Replikationsprozeduren angezeigt werden. Weitere Informationen finden Sie unter [Erweiterte Konflikterkennung und -lösung bei der Mergereplikation](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)angegeben wird.  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)aus. Beachten Sie die Werte der folgenden Spalten im Resultset:  
  
    -   **centralized_conflicts** &ndash; 1 zeigt an, dass Konfliktzeilen auf dem Verleger gespeichert werden, und 0 zeigt an, dass Konfliktzeilen nicht auf dem Verleger gespeichert werden.  
  
    -   **decentralized_conflicts** &ndash; 1 zeigt an, dass Konfliktzeilen auf dem Abonnenten gespeichert werden, und 0 zeigt an, dass Konfliktzeilen nicht auf dem Abonnenten gespeichert werden.  
  
        > [!NOTE]  
        >  Das Konfliktprotokollierungsverhalten einer Mergeveröffentlichung wird mithilfe des `@conflict_logging`-Parameters von [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) festgelegt. Der `@centralized_conflicts`-Parameter wurde als veraltet markiert.  
  
     In der folgenden Tabelle werden die Werte dieser Spalten basierend auf dem für `@conflict_logging` festgelegten Wert beschrieben.  
  
    |@conflict_logging-Wert|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**publisher**|1|0|  
    |**subscriber**|0|1|  
    |**both**|1|1|  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Abonnementen für die Abonnementdatenbank [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md)aus. Geben Sie einen Wert für `@publication` an, um nur Konfliktinformationen zu Artikeln zurückzugeben, die zu einer bestimmten Veröffentlichung gehören. Damit werden Konflikttabelleninformationen für Artikel mit Konflikten zurückgegeben. Notieren Sie den Wert von **conflict_table** bei allen Artikeln, die von Interesse sind. Wenn **conflict_table** für einen Artikel den Wert NULL hat, werden nur die Konflikte gelöscht, die in diesem Artikel aufgetreten sind.  
  
3.  (Optional) Überprüfen Sie die Konfliktzeilen für die Artikel, die von Interesse sind. Wählen Sie abhängig von den Werten von **centralized_conflicts** und **decentralized_conflicts** aus Schritt 1 eine der folgenden Vorgehensweisen:  
  
    -   Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md)aus. Geben Sie für den Artikel (aus Schritt 1) eine Konflikttabelle für `@conflict_table` an. (Optional) Geben Sie den Wert `@publication` an, um zurückgegebene Konfliktinformationen auf eine bestimmte Veröffentlichung zu beschränken. Damit werden Zeilendaten und andere Informationen für die verlierende Zeile zurückgegeben.  
  
    -   Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md)aus. Geben Sie für den Artikel (aus Schritt 1) eine Konflikttabelle für `@conflict_table` an. Damit werden Zeilendaten und andere Informationen für die verlierende Zeile zurückgegeben.  
  
## <a name="conflict-where-delete-failed"></a>Konflikt durch Fehler beim Löschen   
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)aus. Beachten Sie die Werte der folgenden Spalten im Resultset:  
  
    -   **centralized_conflicts** &ndash; 1 zeigt an, dass Konfliktzeilen auf dem Verleger gespeichert werden, und 0 zeigt an, dass Konfliktzeilen nicht auf dem Verleger gespeichert werden.  
  
    -   **decentralized_conflicts** &ndash; 1 zeigt an, dass Konfliktzeilen auf dem Abonnenten gespeichert werden, und 0 zeigt an, dass Konfliktzeilen nicht auf dem Abonnenten gespeichert werden.  
  
        > [!NOTE]  
        >  Das Konfliktprotokollierungsverhalten einer Mergeveröffentlichung wird mithilfe des `@conflict_logging`-Parameters von [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) festgelegt. Der `@centralized_conflicts`-Parameter wurde als veraltet markiert.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Abonnementen für die Abonnementdatenbank [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md)aus. Geben Sie einen Wert für `@publication` an, um nur Konflikttabelleninformationen zu Artikeln zurückzugeben, die zu einer bestimmten Veröffentlichung gehören. Damit werden Konflikttabelleninformationen für Artikel mit Konflikten zurückgegeben. Notieren Sie den Wert von **source_object** bei allen Artikeln, die von Interesse sind. Wenn **conflict_table** für einen Artikel den Wert NULL hat, werden nur die Konflikte gelöscht, die in diesem Artikel aufgetreten sind.  
  
3.  (Optional) Überprüfen Sie die Konfliktinformationen für Löschkonflikte. Wählen Sie abhängig von den Werten von **centralized_conflicts** und **decentralized_conflicts** aus Schritt 1 eine der folgenden Vorgehensweisen:  
  
    -   Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md)aus. Geben Sie den Namen der Quelltabelle (aus Schritt 1) an, in der der Konflikt bezüglich `@source_object` aufgetreten ist. (Optional) Geben Sie den Wert `@publication` an, um zurückgegebene Konfliktinformationen auf eine bestimmte Veröffentlichung zu beschränken. Damit werden auf dem Verleger gespeicherte Informationen zu Löschkonflikten zurückgegeben.  
  
    -   Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md)aus. Geben Sie den Namen der Quelltabelle (aus Schritt 1) an, in der der Konflikt bezüglich `@source_object` aufgetreten ist. (Optional) Geben Sie den Wert `@publication` an, um zurückgegebene Konfliktinformationen auf eine bestimmte Veröffentlichung zu beschränken. Damit werden auf dem Abonnenten gespeicherte Informationen zu Löschkonflikten zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Konflikterkennung und -lösung der Mergereplikation](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Angeben eines Mergeartikelkonfliktlösers](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
  
