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
ms.openlocfilehash: 4c7dd645fed073f73132c6993f12925a885a8e0e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85038040"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a>Konfigurieren von Momentaufnahmeeigenschaften (Replikationsprogrammierung mit Transact-SQL)
  Momentaufnahmeeigenschaften können mithilfe gespeicherter Replikationsprozeduren programmgesteuert definiert und geändert werden. Welche gespeicherten Prozeduren verwendet werden, hängt vom Typ der Veröffentlichung ab.  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a>So konfigurieren Sie Momentaufnahmeeigenschaften beim Erstellen einer Momentaufnahme oder einer Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)aus. Geben Sie einen Veröffentlichungsnamen für **@publication** , den Wert **Snapshot** oder **Continuous** für **@repl_freq** und einen oder mehrere der folgenden Momentaufnahme bezogenen Parameter an:  
  
    -   **@alt_snapshot_folder**-Geben Sie einen Pfad an, wenn der Zugriff auf die Momentaufnahme für diese Veröffentlichung von diesem Speicherort anstelle von oder zusätzlich zum Momentaufnahme-Standardordner erfolgt.  
  
    -   **@compress_snapshot**-Geben Sie den Wert **true** an, wenn die Momentaufnahme Dateien im alternativen Momentaufnahme Ordner im [!INCLUDE[msCoName](../../../includes/msconame-md.md)] CAB-Dateiformat komprimiert werden.  
  
    -   **@pre_snapshot_script**-Geben Sie den Dateinamen und den vollständigen Pfad einer **SQL** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangs Momentaufnahme angewendet wird.  
  
    -   **@post_snapshot_script**-Geben Sie den Dateinamen und den vollständigen Pfad einer **SQL** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangs Momentaufnahme angewendet wurde.  
  
    -   **@snapshot_in_defaultfolder**-Geben Sie den Wert **false** an, wenn die Momentaufnahme nur an einem nicht standardmäßigen Speicherort verfügbar ist.  
  
     Weitere Informationen zum Erstellen von Veröffentlichungen finden Sie unter [Create a Publication](create-a-publication.md).  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a>So konfigurieren Sie Momentaufnahmeeigenschaften beim Erstellen einer Momentaufnahme oder einer Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)aus. Geben Sie einen Veröffentlichungsnamen für **@publication** , den Wert **Snapshot** oder **Continuous** für **@repl_freq** und einen oder mehrere der folgenden Momentaufnahme bezogenen Parameter an:  
  
    -   **@alt_snapshot_folder**-Geben Sie einen Pfad an, wenn der Zugriff auf die Momentaufnahme für diese Veröffentlichung von diesem Speicherort anstelle von oder zusätzlich zum Momentaufnahme-Standardordner erfolgt.  
  
    -   **@compress_snapshot**-Geben Sie den Wert **true** an, wenn die Momentaufnahme Dateien im alternativen Momentaufnahme Ordner im CAB-Dateiformat komprimiert werden.  
  
    -   **@pre_snapshot_script**-Geben Sie den Dateinamen und den vollständigen Pfad einer **SQL** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangs Momentaufnahme angewendet wird.  
  
    -   **@post_snapshot_script**-Geben Sie den Dateinamen und den vollständigen Pfad einer **SQL** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangs Momentaufnahme angewendet wurde.  
  
    -   **@snapshot_in_defaultfolder**-Geben Sie den Wert **false** an, wenn die Momentaufnahme nur an einem nicht standardmäßigen Speicherort verfügbar ist.  
  
2.  Weitere Informationen zum Erstellen von Veröffentlichungen finden Sie unter [Create a Publication](create-a-publication.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a>So ändern Sie die Momentaufnahmeeigenschaften einer bestehenden Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)aus. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und einen der folgenden Werte für an **@property** :  
  
    -   **alt_snapshot_folder** : Geben Sie auch einen neuen Pfad zum alternativen Momentaufnahme Ordner für an **@value** .  
  
    -   **compress_snapshot** : Geben Sie auch den Wert **true** oder **false** für **@value** an, um anzugeben, ob die Momentaufnahme Dateien im alternativen Momentaufnahme Ordner im CAB-Dateiformat komprimiert werden.  
  
    -   **pre_snapshot_script** : Geben Sie auch **@value** den Dateinamen und den vollständigen Pfad einer **SQL** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangs Momentaufnahme angewendet wird.  
  
    -   **post_snapshot_script** : Geben Sie auch **@value** den Dateinamen und den vollständigen Pfad einer **SQL** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangs Momentaufnahme angewendet wurde.  
  
    -   **snapshot_in_defaultfolder** &ndash; Geben Sie außerdem den Wert **true** oder **false** an, um zu definieren, ob die Momentaufnahme an einem anderen als dem Standardspeicherort verfügbar ist.  
  
2.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)aus. Geben **@publication** Sie einen oder mehrere der Parameter für die Zeitplanung oder die Sicherheits Anmelde Informationen an, die geändert werden.  
  
    > [!IMPORTANT]  
    >  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
3.  Führen Sie den [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) von der Eingabeaufforderung aus, oder starten Sie den Momentaufnahme-Agentauftrag, um eine neue Momentaufnahme zu erzeugen. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a>So ändern Sie die Momentaufnahmeeigenschaften einer bestehenden Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und einen der folgenden Werte für an **@property** :  
  
    -   **alt_snapshot_folder** : Geben Sie auch einen neuen Pfad zum alternativen Momentaufnahme Ordner für an **@value** .  
  
    -   **compress_snapshot** : Geben Sie auch den Wert **true** oder **false** für **@value** an, um anzugeben, ob die Momentaufnahme Dateien im alternativen Momentaufnahme Ordner im CAB-Dateiformat komprimiert werden.  
  
    -   **pre_snapshot_script** : Geben Sie auch **@value** den Dateinamen und den vollständigen Pfad einer **SQL** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangs Momentaufnahme angewendet wird.  
  
    -   **post_snapshot_script** : Geben Sie auch **@value** den Dateinamen und den vollständigen Pfad einer **SQL** -Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangs Momentaufnahme angewendet wurde.  
  
    -   **snapshot_in_defaultfolder** &ndash; Geben Sie außerdem den Wert **true** oder **false** an, um zu definieren, ob die Momentaufnahme an einem anderen als dem Standardspeicherort verfügbar ist.  
  
2.  Führen Sie den [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) von der Eingabeaufforderung aus, oder starten Sie den Momentaufnahme-Agentauftrag, um eine neue Momentaufnahme zu erzeugen. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird eine Veröffentlichung erstellt, die einen alternativen Momentaufnahmeordner und eine komprimierte Momentaufnahme verwendet.  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubaltsnapshot.sql#sp_mergealtsnapshot)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Alternative Speicherorte für Momentaufnahme Ordner](../alternate-snapshot-folder-locations.md)   
 [Komprimierte Momentaufnahmen](../compressed-snapshots.md)   
 [Ausführen von Skripts vor und nach dem Anwenden der Momentaufnahme](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Übertragen von Momentaufnahmen über FTP](../transfer-snapshots-through-ftp.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md)  
  
  
