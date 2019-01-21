---
title: Ändern der Optionen für die Initialisierung von Momentaufnahmen für die SQL-Replikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1aa12d4c61f8dae99a948cde69e2370665977227
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54124670"
---
# <a name="modify-snapshot-initialization-options-for-sql-replication"></a>Ändern der Optionen für die Initialisierung von Momentaufnahmen für die SQL-Replikation 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[Zum Initialisieren eines Abonnements mit einer Momentaufnahme](initialize-a-subscription-with-a-snapshot.md) stehen verschiedene Optionen zur Verfügung:

## <a name="specify-snapshot-format-sql-server-management-studio"></a>Angeben des Momentaufnahmeformats (SQL Server Management Studio)
  Geben Sie das Momentaufnahmeformat auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** an. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-specify-snapshot-format"></a>So geben Sie das Momentaufnahmeformat an  
  
1.  Wählen Sie auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** die Option **Natives Format von SQL Server - alle Abonnenten müssen Server mit SQL Server sein** oder **Zeichen - erforderlich, wenn auf einem Verleger oder Abonnenten SQL Server nicht ausgeführt wird** aus.  
  
    > [!NOTE]  
    >  Sie sollten das native Format auswählen, sofern diese Veröffentlichung keine Abonnements für eine SQL Server Compact-Datenbank und keine Nicht-SQL Server-Datenbank unterstützen muss.  
  
2.  Wählen Sie **OK**.   

## <a name="snapshot-folder-locations"></a>Speicherorte für Momentaufnahmeordner

### <a name="default-snapshot-location"></a>Standardspeicherort für Momentaufnahmen
Geben Sie den standardmäßigen Momentaufnahmespeicherort im Verteilungskonfigurations-Assistenten auf der Seite **Snapshotordner** an. Weitere Informationen zum Verwenden dieses Assistenten finden Sie unter [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md). Wenn Sie eine Veröffentlichung auf einem Server erstellen, der nicht als Verteiler konfiguriert ist, geben Sie im Assistenten für neue Veröffentlichung auf der Seite **Momentaufnahmeordner** einen standardmäßigen Momentaufnahmespeicherort an. Weitere Informationen zum Zugreifen auf diesen Assistenten finden Sie unter [Erstellen einer Veröffentlichung](../../relational-databases/replication/publish/create-a-publication.md).  
  
 Ändern Sie den standardmäßigen Momentaufnahmespeicherort im Dialogfeld **Verteilereigenschaften - \<Distributor>** auf der Seite **Verleger**. Weitere Informationen finden Sie unter [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md). Bestimmen Sie den Momentaufnahmeordner für die einzelnen Veröffentlichungen im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>**. Weitere Informationen finden Sie unter [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-modify-the-default-snapshot-location"></a>So ändern Sie den standardmäßigen Momentaufnahmespeicherort  
  
1.  Klicken Sie auf der Seite **Verleger** des Dialogfelds **Verteilereigenschaften - \<Distributor>** auf die Schaltfläche mit den drei Punkten (**…**) für den Verleger, dessen standardmäßiger Momentaufnahmespeicherort geändert werden soll.    
2.  Geben Sie im Dialogfeld **Verlegereigenschaften - \<Publisher>** einen Wert für die Eigenschaft **Standardmomentaufnahmeordner** ein.  
  
    > [!NOTE]  
    >  Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\Computername\Momentaufnahme. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](../../relational-databases/replication/security/secure-the-snapshot-folder.md).    
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
 

### <a name="alternate-snapshot-locations"></a>Alternative Momentaufnahmespeicherorte
Alternative Momentaufnahmespeicherorte ermöglichen Ihnen das Speichern von Momentaufnahmedateien an einem anderen Speicherort oder zusätzlich zum Standardspeicherort, der sich normalerweise auf dem Verteiler befindet. Alternative Speicherorte können sich auf einem anderen Server, in einem Netzlaufwerk oder auf Wechselmedien befinden, z. B. CD-ROMs oder Wechseldatenträgern.  
  
Alternative Momentaufnahmespeicherorte werden als Eigenschaft der Veröffentlichung gespeichert. Da der alternative Momentaufnahmespeicherort eine Veröffentlichungseigenschaft ist, sind der Verteilungs-Agent und der Merge-Agent in der Lage, die ordnungsgemäße Momentaufnahme als Teil des Synchronisierungsprozesses zu finden.  
  
Wenn Sie einen alternativen Speicherort für Momentaufnahmeordner angeben oder Momentaufnahmedateien komprimieren möchten, erstellen Sie die Veröffentlichung, ohne die AnfangsMomentaufnahme sofort zu erstellen, legen Sie die Veröffentlichungseigenschaften für den Momentaufnahmespeicherort fest, und führen Sie dann den Momentaufnahme-Agent für diese Veröffentlichung aus. Wenn Sie den alternativen Speicherort nach der Erstellung der Anfangsmomentaufnahme ändern, wird keiner der für die Veröffentlichung generierten Momentaufnahmen an den alternativen Speicherort verschoben. In diesem Fall ist der Merge-Agent bzw. Verteilungs-Agent möglicherweise nicht in der Lage, die Momentaufnahmedateien an dem neuen alternativen Speicherort ausfindig zu machen.  
  
> [!NOTE]  
>  Geben Sie keinen alternativen Speicherort (mithilfe des Dialogfelds **Veröffentlichungseigenschaften** oder [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)) an, der der gleiche ist wie der Standardspeicherort für Momentaufnahmen.  
  
> [!CAUTION]  
>  Verwenden Sie WebSync und alternative Ordnerspeicherorte für Momentaufnahmen nicht gleichzeitig.  
  
#### <a name="use-sql-server-management-studio"></a>Verwenden von SQL Server Management Studio
1.  Gehen Sie auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** wie folgt vor:  
  
    1.  Aktivieren Sie **Dateien im folgenden Ordner speichern**, und klicken Sie dann auf **Durchsuchen** , um ein Verzeichnis auszuwählen, oder geben Sie den Pfad zu dem Verzeichnis ein, in dem Sie die Momentaufnahmedateien speichern möchten.  
  
        > [!NOTE]  
        >  Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\Computername\Momentaufnahme. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
    2.  Deaktivieren Sie **Dateien im Standardordner speichern** , es sei denn Momentaufnahmedateien müssen in beide Speicherorte geschrieben werden.  
  
     Zum Komprimieren von Momentaufnahmedateien aktivieren Sie **Momentaufnahmedateien in diesem Ordner komprimieren**. Die Komprimierung wird in der Regel für Verbindungen mit niedriger Bandbreite und für alternative Momentaufnahmespeicherorte auf Wechselmedien verwendet, z. B. einer CD-ROM.  
  
2.  Wählen Sie **OK**.  
  
#### <a name="use-transact-sql"></a>Verwenden von Transact-SQL 

Geben Sie beim [Konfigurieren von Momentaufnahmeeigenschaften &#40;Replikationsprogrammierung mit Transact-SQL&#41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md) für den Wert **snapshot_in_defaultfolder** FALSE an. 

## <a name="compressed-snapshots"></a>Komprimierte Momentaufnahmen
  Das Komprimieren von Momentaufnahmedateien empfiehlt sich, wenn Sie Momentaufnahmen in einem langsamen Netzwerk übertragen, oder wenn Sie große Momentaufnahmen auf einem Wechseldatenträger speichern möchten, die sonst keinen Platz darauf hätten. Das Komprimieren von Momentaufnahmedateien ist in diesen Fällen zwar hilfreich, durch die Komprimierung dauert das Generieren und Anwenden der Momentaufnahme jedoch länger.  
  
 Komprimierte Momentaufnahmedateien werden im [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB-Dateiformat geschrieben, mit dem Dateien von bis zu 2 GB komprimiert werden können (Momentaufnahmedateien mit über 2 GB können nicht komprimiert werden). Dateien müssen zum Komprimieren in einen alternativen Momentaufnahmeordner geschrieben werden (in den Standardmomentaufnahmeordner geschriebene Dateien können nicht komprimiert werden). 
  
 Dateien werden dort dekomprimiert, wo der Verteilungs-Agent oder der Merge-Agent ausgeführt wird; in der Regel werden Pullabonnements mit komprimierten Momentaufnahme verwendet, sodass Dateien auf dem Abonnenten dekomprimiert werden. Wenn der Abonnent eine komprimierte Datei empfängt, wird die Datei zunächst an einem temporären Speicherort abgelegt. Nachdem die komprimierte Datei auf den Abonnenten kopiert wurde, werden die Momentaufnahmedateien in der Datei jeweils nacheinander vom CAB-Hilfsprogramm dekomprimiert. Der auf dem Abonnenten benötigte Speicherplatz entspricht der Größe der komprimierten Datei plus der größten dekomprimierten Datei.  
  
> [!NOTE]  
>  Komprimierte Momentaufnahmen können in einigen Fällen die Leistung beim Übertragen der Momentaufnahmedateien im Netzwerk verbessern. Beim Komprimieren der Momentaufnahme fällt jedoch zusätzlicher Verarbeitungsaufwand für den Momentaufnahme-Agent an, wenn die Momentaufnahmedateien erstellt werden, sowie für den Verteilungs-Agent oder den Merge-Agent, wenn die Momentaufnahmedateien angewendet werden. Dies könnte das Erstellen von Momentaufnahmen verlangsamen und den Zeitaufwand für das Anwenden einer Momentaufnahme in manchen Fällen erhöhen. Darüber hinaus kann das Übertragen komprimierter Momentaufnahmen bei einem Netzwerkausfall nicht wieder aufgenommen werden, weshalb sie sich nicht für unzuverlässige Netzwerke eignen. Wägen Sie die Vor- und Nachteile sorgfältig ab, wenn Sie komprimierte Momentaufnahmen in einem Netzwerk verwenden.  
  
### <a name="use-sql-server-management-studio"></a>Verwenden von SQL Server Management Studio
1.  Gehen Sie auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** wie folgt vor:  
  
    1.  Aktivieren Sie **Dateien im folgenden Ordner speichern**, und klicken Sie dann auf **Durchsuchen** , um ein Verzeichnis auszuwählen, oder geben Sie den Pfad zu dem Verzeichnis ein, in dem Sie die Momentaufnahmedateien speichern möchten.  
  
        > [!NOTE]  
        >  Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad (Universal Naming Convention) angeben, wie z.B. \\\Computername\Momentaufnahme. Weitere Informationen finden Sie unter [Sichern des Momentaufnahmeordners](security/secure-the-snapshot-folder.md).  
  
    2.  Deaktivieren Sie **Dateien im Standardordner speichern** , es sei denn Momentaufnahmedateien müssen in beide Speicherorte geschrieben werden.  
  
        > [!NOTE]  
        >  Wenn dieses Kontrollkästchen aktiviert ist, werden die im Standardordner gespeicherten Dateien nicht komprimiert. Komprimierte Dateien können nur im alternativen im vorigen Schritt angegebenen Speicherort gespeichert werden.  
  
2.  Wählen Sie **Momentaufnahmedateien in diesem Ordner komprimieren**aus.    
3.  Wählen Sie **OK**.   

### <a name="use-transact-sql"></a>Verwenden von Transact-SQL

Wenn Sie [Momentaufnahmeeigenschaften konfigurieren](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md), geben Sie für den Wert **compress_snapshot** **TRUE** an. 

## <a name="execute-scripts-before-and-after-snapshot-is-applied"></a>Ausführen von Skripts vor und nach dem Anwenden der Momentaufnahme
Sie können angeben, ob Skripts auf dem Abonnenten vor oder nach dem Anwenden der Momentaufnahme ausgeführt werden. Skripts können für verschiedene Zwecke verwendet werden, z. B. zum Erstellen von Anmeldungen und Schemas (Objektbesitzer) auf den einzelnen Abonnenten.  
  
 Sie geben einen Dateispeicherort für jedes Skript an, und der Momentaufnahme-Agent kopiert jeweils bei der Verarbeitung der Momentaufnahme die Skriptdateien in den aktuellen Momentaufnahmeordner. Der Verteilungs-Agent oder der Merge-Agent führt das Vor-Momentaufnahme-Skript vor allen Skripts für replizierte Objekte aus, wenn eine Momentaufnahme angewendet wird. Der Verteilungs-Agent oder der Merge-Agent führt das Nach-Momentaufnahme-Skript nach der Momentaufnahme aus, nachdem alle anderen Skripts für replizierte Objekte und Daten angewendet wurden. Nachdem die Momentaufnahmeanwendung abgeschlossen ist und Skriptdateien erfolgreich ausgeführt wurden, werden die Skriptdateien aus dem Arbeitsverzeichnis auf dem Abonnenten entfernt.  
  
 Das Skript wird ausgeführt, indem das Hilfsprogramm **sqlcmd** gestartet wird. Führen Sie das Skript vor der Bereitstellung mithilfe von **sqlcmd** aus, um sicherzustellen, dass es erwartungsgemäß ausgeführt wird. Der Inhalt von Skripts, die vor und nach dem Anwenden der Momentaufnahme ausgeführt werden, muss wiederholbar sein. Wenn Sie z. B. eine Tabelle im Skript erstellen, müssen Sie zuerst ihr Vorhandensein überprüfen und daraufhin die entsprechende Aktion vornehmen. Das Skript muss wiederholbar sein, denn beim erneuten Initialisieren eines Abonnements, für das das Skript bereits angewendet wurde, wird das Skript erneut angewendet, wenn die neue Momentaufnahme während der erneuten Initialisierung angewendet wird.  
  
 Falls Sie die Momentaufnahmedatei komprimieren (indem sie in das CAB-Dateiformat von [!INCLUDE[msCoName](../../includes/msconame-md.md)] kopiert wird), werden die Skripts ebenfalls komprimiert und in der CAB-Datei platziert. Nachdem die komprimierte Momentaufnahmedatei zum Abonnenten übertragen und in ein Arbeitsverzeichnis auf dem Abonnenten dekomprimiert wurde, werden als Vor-Momentaufnahme-Skripts gekennzeichnete Skripts ausgeführt. Genauso werden alle Nach-Momentaufnahme-Skripts dekomprimiert und auf dem Abonnenten als letzter Schritt der Anwendung der Momentaufnahme ausgeführt.  

### <a name="execute-a-script"></a>Ausführen eines Skripts 

1.  Gehen Sie auf der Seite **Momentaufnahme** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** wie folgt vor:    
    -   Wenn Sie ein Skript angeben möchten, das vor dem Anwenden der Momentaufnahme ausgeführt werden soll, klicken Sie auf **Durchsuchen** , um zum entsprechenden Skript zu navigieren, oder geben Sie im Textfeld **Dieses Skript vor Anwenden der Momentaufnahme ausführen** den Pfad zum gewünschten Skript ein.  
  
        > [!NOTE]  
        >  Der Verteilungs-Agent bzw. Merge-Agent muss für das von Ihnen angegebene Verzeichnis Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\computername\scripts\myscript.sql.  
  
    -   Wenn Sie ein Skript angeben möchten, das nach dem Anwenden der Momentaufnahme ausgeführt werden soll, klicken Sie auf **Durchsuchen** , um zum entsprechenden Skript zu navigieren, oder geben Sie im Textfeld **Dieses Skript nach Anwenden der Momentaufnahme ausführen** den UNC-Pfad zum gewünschten Skript ein.   
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  


## <a name="see-also"></a>Weitere Informationen  
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Übermitteln einer Momentaufnahme über FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)   
 [Konfigurieren von Momentaufnahmeeigenschaften &#40;Replikationsprogrammierung mit Transact-SQL&#41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)     
  
  
