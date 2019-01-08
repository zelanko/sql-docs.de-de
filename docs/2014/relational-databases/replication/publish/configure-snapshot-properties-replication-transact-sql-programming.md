---
title: Konfigurieren von Momentaufnahmeeigenschaften (Replikationsprogrammierung mit Transact-SQL) | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server replication], properties
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 880f2f6fc155338aa65637fbc71402ba7ec55821
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52800212"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a>Konfigurieren von Momentaufnahmeeigenschaften (Replikationsprogrammierung mit Transact-SQL)
  Momentaufnahmeeigenschaften können mithilfe gespeicherter Replikationsprozeduren programmgesteuert definiert und geändert werden. Welche gespeicherten Prozeduren verwendet werden, hängt vom Typ der Veröffentlichung ab.  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a>So konfigurieren Sie Momentaufnahmeeigenschaften beim Erstellen einer Momentaufnahme oder einer Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)aus. Geben Sie einen Veröffentlichungsnamen für **@publication**, den Wert **snapshot** oder **continuous** für **@repl_freq**und einen oder mehrere der folgenden Momentaufnahmeparameter ein:  
  
    -   **@alt_snapshot_folder** &ndash; Geben Sie einen Pfad an, wenn von diesem Speicherort, anstatt vom Standardmomentaufnahmeordner oder zusätzlich zu diesem, auf die Momentaufnahme für diese Veröffentlichung zugegriffen wird.  
  
    -   **@compress_snapshot** &ndash; Geben Sie den Wert **true** an, wenn die Momentaufnahmedateien im alternativen Momentaufnahmeordner im [!INCLUDE[msCoName](../../../includes/msconame-md.md)] CAB-Dateiformat komprimiert sind.  
  
    -   **@pre_snapshot_script** &ndash; Geben Sie den Dateinamen und den vollständigen Pfad einer **.sql** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangsmomentaufnahme angewendet wird.  
  
    -   **@post_snapshot_script** &ndash; Geben Sie den Dateinamen und den vollständigen Pfad einer **.sql** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangsmomentaufnahme angewendet wurde.  
  
    -   **@snapshot_in_defaultfolder** &ndash; Geben Sie den Wert **false** an, wenn die Momentaufnahme nur in einem anderen als dem Standardverzeichnis verfügbar ist.  
  
     Weitere Informationen zum Erstellen von Veröffentlichungen finden Sie unter [Create a Publication](create-a-publication.md).  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a>So konfigurieren Sie Momentaufnahmeeigenschaften beim Erstellen einer Momentaufnahme oder einer Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)aus. Geben Sie einen Veröffentlichungsnamen für **@publication**, den Wert **snapshot** oder **continuous** für **@repl_freq**und einen oder mehrere der folgenden Momentaufnahmeparameter ein:  
  
    -   **@alt_snapshot_folder** &ndash; Geben Sie einen Pfad an, wenn von diesem Speicherort, anstatt vom Standardmomentaufnahmeordner oder zusätzlich zu diesem, auf die Momentaufnahme für diese Veröffentlichung zugegriffen wird.  
  
    -   **@compress_snapshot** &ndash; Geben Sie den Wert **true** an, wenn die Momentaufnahmedateien im alternativen Momentaufnahmeordner im CAB-Dateiformat komprimiert sind.  
  
    -   **@pre_snapshot_script** &ndash; Geben Sie den Dateinamen und den vollständigen Pfad einer **.sql** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangsmomentaufnahme angewendet wird.  
  
    -   **@post_snapshot_script** &ndash; Geben Sie den Dateinamen und den vollständigen Pfad einer **.sql** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangsmomentaufnahme angewendet wurde.  
  
    -   **@snapshot_in_defaultfolder** &ndash; Geben Sie den Wert **false** an, wenn die Momentaufnahme nur in einem anderen als dem Standardverzeichnis verfügbar ist.  
  
2.  Weitere Informationen zum Erstellen von Veröffentlichungen finden Sie unter [Create a Publication](create-a-publication.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a>So ändern Sie die Momentaufnahmeeigenschaften einer bestehenden Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)aus. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und einen der folgenden Werte für **@property**an:  
  
    -   **alt_snapshot_folder** &ndash; Geben Sie außerdem einen neuen Pfad zum alternativen Momentaufnahmeordner für **@value**aus.  
  
    -   **compress_snapshot** &ndash; Geben Sie außerdem entweder **true** oder **false** für **@value** an, um zu definieren, ob die Momentaufnahmedateien im alternativen Momentaufnahmeordner im CAB-Dateiformat komprimiert sind.  
  
    -   **pre_snapshot_script** &ndash; Geben Sie außerdem für **@value** den Dateinamen und den vollständigen Pfad einer **.sql** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangsmomentaufnahme angewendet wird.  
  
    -   **post_snapshot_script** &ndash; Geben Sie außerdem für **@value** den Dateinamen und den vollständigen Pfad einer **.sql** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangsmomentaufnahme angewendet wurde.  
  
    -   **snapshot_in_defaultfolder** &ndash; Geben Sie außerdem den Wert **true** oder **false** an, um zu definieren, ob die Momentaufnahme an einem anderen als dem Standardspeicherort verfügbar ist.  
  
2.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)aus. Geben Sie **@publication** und einen oder mehrere der zu ändernden Parameter für die Zeitplanung oder Sicherheitsanmeldeinformationen an.  
  
    > [!IMPORTANT]  
    >  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
3.  Führen Sie den [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) von der Eingabeaufforderung aus, oder starten Sie den Momentaufnahme-Agentauftrag, um eine neue Momentaufnahme zu erzeugen. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a>So ändern Sie die Momentaufnahmeeigenschaften einer bestehenden Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und einen der folgenden Werte für **@property**an:  
  
    -   **alt_snapshot_folder** &ndash; Geben Sie außerdem einen neuen Pfad zum alternativen Momentaufnahmeordner für **@value**aus.  
  
    -   **compress_snapshot** &ndash; Geben Sie außerdem entweder **true** oder **false** für **@value** an, um zu definieren, ob die Momentaufnahmedateien im alternativen Momentaufnahmeordner im CAB-Dateiformat komprimiert sind.  
  
    -   **pre_snapshot_script** &ndash; Geben Sie außerdem für **@value** den Dateinamen und den vollständigen Pfad einer **.sql** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangsmomentaufnahme angewendet wird.  
  
    -   **post_snapshot_script** &ndash; Geben Sie außerdem für **@value** den Dateinamen und den vollständigen Pfad einer **.sql** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangsmomentaufnahme angewendet wurde.  
  
    -   **snapshot_in_defaultfolder** &ndash; Geben Sie außerdem den Wert **true** oder **false** an, um zu definieren, ob die Momentaufnahme an einem anderen als dem Standardspeicherort verfügbar ist.  
  
2.  Führen Sie den [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) von der Eingabeaufforderung aus, oder starten Sie den Momentaufnahme-Agentauftrag, um eine neue Momentaufnahme zu erzeugen. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird eine Veröffentlichung erstellt, die einen alternativen Momentaufnahmeordner und eine komprimierte Momentaufnahme verwendet.  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubaltsnapshot.sql#sp_mergealtsnapshot)]  
  
## <a name="see-also"></a>Siehe auch  
 [Alternative Speicherorte für Momentaufnahmeordner](../alternate-snapshot-folder-locations.md)   
 [Komprimierte Momentaufnahmen](../compressed-snapshots.md)   
 [Ausführen von Skripts vor und nach dem Anwenden der Momentaufnahme](../execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Übertragen von Momentaufnahmen über FTP](../transfer-snapshots-through-ftp.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md)  
  
  
