---
title: Konfigurieren von Momentaufnahmeeigenschaften (gespeicherte Prozedur für die Replikation)
description: Verwenden Sie gespeicherte Prozeduren für die Replikation, um Momentaufnahmeeigenschaften für Momentaufnahme- oder Transaktionsveröffentlichungen zu konfigurieren.
ms.custom: seo-lt-2019
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 0f2aa6766320367af813852a2d1012ab6c7fef29
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96130991"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a>Konfigurieren von Momentaufnahmeeigenschaften (Replikationsprogrammierung mit Transact-SQL)
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Momentaufnahmeeigenschaften können mithilfe gespeicherter Replikationsprozeduren programmgesteuert definiert und geändert werden. Welche gespeicherten Prozeduren verwendet werden, hängt vom Typ der Veröffentlichung ab.  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a>So konfigurieren Sie Momentaufnahmeeigenschaften beim Erstellen einer Momentaufnahme oder einer Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)aus. Geben Sie einen Veröffentlichungsnamen für `@publication`, den Wert **snapshot** oder **continuous** für `@repl_freq` und einen oder mehrere der folgenden Momentaufnahmeparameter ein:  
  
    -   `@alt_snapshot_folder`: Geben Sie einen Pfad an, wenn von diesem Speicherort, anstatt vom Standardmomentaufnahmeordner oder zusätzlich zu diesem, auf die Momentaufnahme für diese Veröffentlichung zugegriffen wird.    
    -   `@compress_snapshot`: Geben Sie den Wert **true** an, wenn die Momentaufnahmedateien im alternativen Momentaufnahmeordner im [!INCLUDE[msCoName](../../../includes/msconame-md.md)] CAB-Dateiformat komprimiert sind.    
    -   `@pre_snapshot_script`: Geben Sie den Dateinamen und den vollständigen Pfad einer **.sql**-Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangsmomentaufnahme angewendet wird.    
    -   `@post_snapshot_script`: Geben Sie den Dateinamen und den vollständigen Pfad einer **.sql**-Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangsmomentaufnahme angewendet wurde.    
    -   `@snapshot_in_defaultfolder`: Geben Sie den Wert **false** an, wenn die Momentaufnahme nur in einem anderen als dem Standardverzeichnis verfügbar ist.  
  
     Weitere Informationen zum Erstellen von Veröffentlichungen finden Sie unter [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a>So konfigurieren Sie Momentaufnahmeeigenschaften beim Erstellen einer Momentaufnahme oder einer Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)aus. Geben Sie einen Veröffentlichungsnamen für `@publication`, den Wert **snapshot** oder **continuous** für `@repl_freq` und einen oder mehrere der folgenden Momentaufnahmeparameter ein:  
  
    -   **alt_snapshot_folder**: Geben Sie einen Pfad an, wenn von diesem Speicherort, anstatt vom Standardmomentaufnahmeordner oder zusätzlich zu diesem, auf die Momentaufnahme für diese Veröffentlichung zugegriffen wird.    
    -   `@compress_snapshot`: Geben Sie den Wert **true** an, wenn die Momentaufnahmedateien im alternativen Momentaufnahmeordner im CAB-Dateiformat komprimiert sind.   
    -   `@pre_snapshot_script`: Geben Sie den Dateinamen und den vollständigen Pfad einer **.sql**-Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangsmomentaufnahme angewendet wird.    
    -   `@post_snapshot_script`: Geben Sie den Dateinamen und den vollständigen Pfad einer **.sql**-Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangsmomentaufnahme angewendet wurde.    
    -   `@snapshot_in_defaultfolder`: Geben Sie den Wert **false** an, wenn die Momentaufnahme nur in einem anderen als dem Standardverzeichnis verfügbar ist.  
  
2.  Weitere Informationen zum Erstellen von Veröffentlichungen finden Sie unter [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a>So ändern Sie die Momentaufnahmeeigenschaften einer bestehenden Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)aus. Geben Sie einen Wert **1** für `@force_invalidate_snapshot` und einen der folgenden Werte für `@property` an:  
  
    -   **alt_snapshot_folder**: Geben Sie außerdem einen neuen Pfad zum alternativen Momentaufnahmeordner für `@value` an.    
    -   **compress_snapshot**: Geben Sie außerdem entweder **true** oder **false** für `@value` an, um zu definieren, ob die Momentaufnahmedateien im alternativen Momentaufnahmeordner im CAB-Dateiformat komprimiert sind.    
    -   **pre_snapshot_script**: Geben Sie außerdem für `@value` den Dateinamen und den vollständigen Pfad einer **.sql**-Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangsmomentaufnahme angewendet wird.    
    -   **post_snapshot_script**: Geben Sie außerdem für `@value` den Dateinamen und den vollständigen Pfad einer **.sql**-Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangsmomentaufnahme angewendet wurde.    
    -   **snapshot_in_defaultfolder** &ndash; Geben Sie außerdem den Wert **true** oder **false** an, um zu definieren, ob die Momentaufnahme an einem anderen als dem Standardspeicherort verfügbar ist.  
  
2.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)aus. Geben Sie `@publication` und einen oder mehrere der zu ändernden Parameter für die Zeitplanung oder Sicherheitsanmeldeinformationen an.  
  
    > [!IMPORTANT]  
    >  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
3.  Führen Sie den [Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md) von der Eingabeaufforderung aus, oder starten Sie den Momentaufnahme-Agentauftrag, um eine neue Momentaufnahme zu erzeugen. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a>So ändern Sie die Momentaufnahmeeigenschaften einer bestehenden Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)aus. Geben Sie einen Wert **1** für `@force_invalidate_snapshot` und einen der folgenden Werte für `@property**` an:  
  
    -   **alt_snapshot_folder**: Geben Sie außerdem einen neuen Pfad zum alternativen Momentaufnahmeordner für `@value` an.    
    -   **compress_snapshot**: Geben Sie außerdem entweder **true** oder **false** für `@value` an, um zu definieren, ob die Momentaufnahmedateien im alternativen Momentaufnahmeordner im CAB-Dateiformat komprimiert sind.    
    -   **pre_snapshot_script**: Geben Sie außerdem für `@value` den Dateinamen und den vollständigen Pfad einer **.sql**-Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, bevor die Anfangsmomentaufnahme angewendet wird.    
    -   **post_snapshot_script**: Geben Sie außerdem für `@value` den Dateinamen und den vollständigen Pfad einer **.sql**-Datei an, die während der Initialisierung auf dem Abonnenten ausgeführt wird, nachdem die Anfangsmomentaufnahme angewendet wurde.    
    -   **snapshot_in_defaultfolder** &ndash; Geben Sie außerdem den Wert **true** oder **false** an, um zu definieren, ob die Momentaufnahme an einem anderen als dem Standardspeicherort verfügbar ist.  
  
2.  Führen Sie den [Replication Snapshot Agent](../../../relational-databases/replication/agents/replication-snapshot-agent.md) von der Eingabeaufforderung aus, oder starten Sie den Momentaufnahme-Agentauftrag, um eine neue Momentaufnahme zu erzeugen. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird eine Veröffentlichung erstellt, die einen alternativen Momentaufnahmeordner und eine komprimierte Momentaufnahme verwendet.  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../relational-databases/replication/codesnippet/tsql/configure-snapshot-prope_1.sql)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ändern von Momentaufnahmeoptionen](../../../relational-databases/replication/snapshot-options.md)   
 [Ausführen von Skripts vor und nach dem Anwenden der Momentaufnahme](../../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Übertragen von Momentaufnahmen über FTP](../../../relational-databases/replication//publish/deliver-a-snapshot-through-ftp.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)  
  
  
