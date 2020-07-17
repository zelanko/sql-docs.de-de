---
title: Replikationsmomentaufnahme-Agent | Microsoft-Dokumentation
description: In SQL Server bereitet der Momentaufnahmen-Agent für die Replikation Momentaufnahmendateien vor, speichert diese in einem Ordner und zeichnet Synchronisierungsaufträge in der Verteilungsdatenbank auf.
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, executables
- agents [SQL Server replication], Snapshot Agent
- command prompt [SQL Server replication]
- Snapshot Agent, parameter reference
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 7132154bcb61e84d052891c200589cf157b31f65
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730220"
---
# <a name="replication-snapshot-agent"></a>Replikationsmomentaufnahme-Agent
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../../includes/applies-to-version/sql-asdb.md)]
  Der Replikationsmomentaufnahme-Agent ist eine ausführbare Datei, die Momentaufnahmedateien vorbereitet, die das Schema und die Daten von veröffentlichten Tabellen und Datenbankobjekten enthalten, die Dateien im Momentaufnahmeordner speichert und Synchronisierungsaufträge in der Verteilungsdatenbank aufzeichnet.  
  
> [!NOTE]  
>  - Parameter können in beliebiger Reihenfolge angegeben werden.  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="syntax"></a>Syntax  
  
```  
  
snapshot [ -?]   
-Publisher server_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSize bcp_batch_size]  
[-DefinitionFile def_path_and_file_name]  
[-Distributor server_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostName dynamic_filter_host_name]  
[-DynamicFilterLogin dynamic_filter_login]  
[-DynamicSnapshotLocation dynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiter field_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocks number_of_blocks ]  
[-HRBcpBlockSize block_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageInterval keep_alive_interval]  
[-LoginTimeOut login_time_out_seconds]  
[-MaxBcpThreads number_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Output output_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSize packet_size]  
[-PrefetchTables [0|1] ]  
[-ProfileName profile_name]  
[-PublisherDB publisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-PublisherLogin publisher_login]  
[-PublisherPassword publisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOut query_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiter row_delimiter]  
[-StartQueueTimeout start_queue_timeout_seconds]  
[-UsePerArticleContentsView use_per_article_contents_view]  
```  
  
## <a name="arguments"></a>Argumente  
 **-?**  
 Druckt alle verfügbaren Parameter.  
  
 **-Publisher**  _server_name_[ **\\** _instance\_name_]  
 Der Name des Verlegers. Geben Sie „server_name“ für die Standardinstanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Geben Sie _server\_name_ **\\** _instance\_name_ für eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an.  
  
 **-Publication** _publication_  
 Der Name der Veröffentlichung. Dieser Parameter ist nur gültig, wenn die Veröffentlichung so festgelegt ist, dass sie immer eine Momentaufnahme für neue oder neu initialisierte Abonnements zur Verfügung hat.  
  
 **-70Subscribers**  
 Muss verwendet werden, wenn Abonnenten vorhanden sind, auf denen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , Version 7.0, ausgeführt wird.  
  
 **-BcpBatchSize** _bcp_\_ *batch*\_ *size*  
 Die Anzahl von Zeilen, die in einem Massenkopiervorgang gesendet werden sollen. Bei Ausführung eines **bcp in** -Vorgangs entspricht die Batchgröße der Anzahl von Zeilen, die als eine Transaktion an den Server gesendet werden sollen, und ebenso der Anzahl von Zeilen, die gesendet werden müssen, bevor der Verteilungs-Agent eine **bcp** -Statusmeldung protokolliert. Bei Ausführung eines **bcp out** -Vorgangs wird eine feste Batchgröße von 1000 verwendet. Durch den Wert 0 wird angezeigt, dass keine Meldungsprotokollierung ausgeführt wird.  
  
 **-DefinitionFile** _def_path_and_file_name_  
 Der Pfad der Agentdefinitionsdatei. Eine Agentdefinitionsdatei enthält Befehlszeilenargumente für den Agent. Der Inhalt der Datei wird als ausführbare Datei analysiert. Verwenden Sie doppelte Anführungszeichen ("), um Argumentwerte anzugeben, die beliebige Zeichen enthalten.  
  
 **-Distributor** _server_name_[ **\\** _instance\_name_]  
 Der Name des Verteilers. Geben Sie *server_name* für die Standardinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Geben Sie _server\_name_ **\\** _instance\_name_ für eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an.  
  
 **-DistributorDeadlockPriority** [ **-1**|**0**|**1**]  
 Die Priorität der Momentaufnahme-Agent-Verbindung mit dem Verteiler, wenn ein Deadlock auftritt. Dieser Parameter wird angegeben, um Deadlocks zu beheben, die möglicherweise während der Momentaufnahmegenerierung zwischen dem Momentaufnahme-Agent und Benutzeranwendungen auftreten.  
  
|Wert von DistributorDeadlockPriority|BESCHREIBUNG|  
|---------------------------------------|-----------------|  
|**-1**|Bei Auftreten eines Deadlocks auf dem Verteiler haben andere Anwendungen als der Momentaufnahme-Agent Priorität.|  
|**0** (Standard)|Es wird keine Priorität zugewiesen.|  
|**1**|Bei Auftreten eines Deadlocks auf dem Verteiler hat der Momentaufnahme-Agent Priorität.|  
  
 **-DistributorLogin** _distributor_login_  
 Der Anmeldename, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Verteiler herzustellen.  
  
 **-DistributorPassword** _distributor_password_  
 Das Kennwort, das verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Verteiler herzustellen. erforderlich.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Gibt den Sicherheitsmodus des Verteilers an. Der Wert **0** steht für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierungsmodus (Standard), der Wert **1** für den Windows-Authentifizierungsmodus.  
  
 **-DynamicFilterHostName** _dynamic_filter_host_name_  
 Wird verwendet, um einen Wert für [HOST_NAME &#40;Transact-SQL&#41;](../../../t-sql/functions/host-name-transact-sql.md) bei der Filterung festzulegen, wenn eine dynamische Momentaufnahme erstellt wird. Wenn z. B. für einen Artikel die Teilmengenfilterklausel `rep_id = HOST_NAME()` angegeben wird und Sie die **DynamicFilterHostName** -Eigenschaft auf "FBJones" festlegen, bevor Sie den Merge-Agent aufrufen, werden nur Zeilen repliziert, in denen in der Spalte **rep_id** der Wert "FBJones" enthalten ist.  
  
 **-DynamicFilterLogin** _dynamic_filter_login_  
 Wird verwendet, um einen Wert für [SUSER_SNAME &#40;Transact-SQL&#41;](../../../t-sql/functions/suser-sname-transact-sql.md) bei der Filterung festzulegen, wenn eine dynamische Momentaufnahme erstellt wird. Wenn z. B. für einen Artikel die Teilmengenfilterklausel `user_id = SUSER_SNAME()` angegeben wird und Sie die **DynamicFilterLogin** -Eigenschaft auf "rsmith" festlegen, bevor Sie die **Run** -Methode des **SQLSnapshot** -Objekts aufrufen, enthält die Momentaufnahme nur Zeilen, in denen in der Spalte **user_id** der Wert "rsmith" enthalten ist.  
  
 **-DynamicSnapshotLocation** _dynamic_snapshot_location_  
 Der Speicherort, an dem die dynamische Momentaufnahme generiert werden soll.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Dies ist die Verschlüsselungsebene der Transport Layer Security (TLS, früher als Secure Sockets Layer, SSL, bezeichnet), die vom Momentaufnahmen-Agent beim Herstellen von Verbindungen verwendet wird.  
  
|Wert von EncryptionLevel|BESCHREIBUNG|  
|---------------------------|-----------------|  
|**0**|Gibt an, dass TLS nicht verwendet wird.|  
|**1**|Gibt an, dass TLS verwendet wird, der Agent jedoch nicht überprüft, ob das TLS/SSL-Serverzertifikat von einem vertrauenswürdigen Aussteller signiert wurde.|  
|**2**|Gibt an, dass TLS verwendet und das Zertifikat überprüft wird.|  

 > [!NOTE]  
 >  Ein gültiges TLS/SSL-Zertifikat wird mit dem vollqualifizierten Domänennamen der SQL Server-Instanz definiert. Damit der Agent die Verbindung erfolgreich herstellen kann, wenn „-EncryptionLevel“ auf 2 festgelegt ist, sollten Sie einen Alias auf der lokalen SQL Server-Instanz erstellen. Der Parameter „Alias Name“ sollte den Servernamen enthalten, und für den Parameter „Server“ sollte der vollqualifizierte Name der SQL Server-Instanz festgelegt werden.
  
 Weitere Informationen finden Sie unter [Anzeigen und Ändern von Replikationssicherheitseinstellungen](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 **-FieldDelimiter** _field_delimiter_  
 Das Zeichen oder die Zeichenfolge, das bzw. die das Ende eines Felds in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datendatei für das Massenkopieren markiert. Der Standardwert ist \n\<x$3>\n.  
  
 **-HistoryVerboseLevel** [ **1**| **2**| **3**]  
 Gibt den Umfang des Verlaufs an, der während eines Momentaufnahmevorgangs protokolliert wird. Sie können die negativen Auswirkungen der Verlaufsprotokollierung auf die Leistung minimieren, indem Sie den Wert **1**auswählen.  
  
|Wert von <legacyBold>HistoryVerboseLevel</legacyBold>|BESCHREIBUNG|  
|-------------------------------|-----------------|  
|**0**|Statusmeldungen werden entweder an der Konsole ausgegeben oder in eine Ausgabedatei geschrieben. Verlaufsdatensätze werden nicht in der Verteilungsdatenbank protokolliert.|  
|**1**|Aktualisieren Sie immer eine vorherige Verlaufsmeldung mit dem gleichen Status (Start, Status, Erfolg usw.). Wenn kein vorheriger Datensatz mit dem gleichen Status vorhanden ist, fügen Sie einen neuen Datensatz ein.|  
|**2** (Standardwert)|Fügen Sie neue Verlaufsdatensätze ein, es sei denn, der Datensatz bezieht sich z. B. auf Leerlaufmeldungen oder Meldungen zu Aufträgen mit langer Ausführungszeit. In diesen Fällen aktualisieren Sie die vorherigen Datensätze.|  
|**3**|Fügen Sie immer neue Datensätze ein, es sei denn, ein Datensatz bezieht sich auf Leerlaufmeldungen.|  
  
 **-HRBcpBlocks** _number_of_blocks_  
 Die Anzahl von **bcp** -Datenblöcken, die zwischen dem Lese- und dem Schreibthread in die Warteschlange gestellt werden. Der Standardwert lautet "50". **HRBcpBlocks** wird nur mit Oracle-Veröffentlichungen verwendet.  
  
> [!NOTE]  
>  Dieser Parameter wird zur Leistungsoptimierung für **bcp** von einem Oracle-Verleger verwendet.  
  
 -**HRBcpBlockSize**_block\_size_  
 Die Größe jedes einzelnen **bcp** -Datenblocks in Kilobytes (KB). Der Standardwert ist 64 KB. **HRBcpBlocks** wird nur mit Oracle-Veröffentlichungen verwendet.  
  
> [!NOTE]  
>  Dieser Parameter wird zur Leistungsoptimierung für **bcp** von einem Oracle-Verleger verwendet.  
  
 **-HRBcpDynamicBlocks**  
 Gibt an, ob die Größe jedes einzelnen **bcp** -Datenblocks dynamisch zunehmen kann. **HRBcpBlocks** wird nur mit Oracle-Veröffentlichungen verwendet.  
  
> [!NOTE]  
>  Dieser Parameter wird zur Leistungsoptimierung für **bcp** von einem Oracle-Verleger verwendet.  
  
 **-KeepAliveMessageInterval** _keep_alive_interval_  
 Gibt an, wie viele Sekunden der Momentaufnahme-Agent wartet, bevor die Meldung, dass auf eine Back-End-Nachricht gewartet wird, in der [MSsnapshot_history](../../../relational-databases/system-tables/mssnapshot-history-transact-sql.md) -Tabelle protokolliert wird. Der Standardwert beträgt 300 Sekunden.  
  
 **-LoginTimeOut** _login_time_out_seconds_  
 Die Anzahl von Sekunden, nach denen ein Timeout bei der Anmeldung eintritt. Der Standardwert ist **15** Sekunden.  
  
 **-MaxBcpThreads** _number_of_threads_  
 Gibt die Anzahl von Massenkopiervorgängen an, die parallel ausgeführt werden können. Die maximale Anzahl von Threads und gleichzeitig vorhandenen ODBC-Verbindungen entspricht entweder **MaxBcpThreads** oder der Anzahl von Massenkopieranforderungen, die in der Verteilungsdatenbank in der Synchronisierungstransaktion enthalten sind. Dabei gilt der jeweils kleinere Wert. Der Wert von**MaxBcpThreads** muss größer als **0** sein. Es ist keine hartcodierte Obergrenze vorhanden. Der Standardwert ist das Doppelte der Anzahl der Prozessoren.  
  
 \- **MaxNetworkOptimization** [ **0**| **1**]  
 Wird verwendet, wenn irrelevante Löschvorgänge an den Abonnenten gesendet werden. Bei irrelevanten Löschvorgängen handelt es sich um DELETE-Befehle, die für Zeilen, die nicht zur Partition des Abonnenten gehören, an den Abonnenten gesendet werden. Irrelevante Löschvorgänge beeinträchtigen weder die Datenintegrität noch die Konvergenz, allerdings können sie zu unnötigem Netzwerkverkehr führen. Der Standardwert von **MaxNetworkOptimization** lautet **0**. Wenn Sie **MaxNetworkOptimization** auf **1** festlegen, minimieren Sie dadurch das Risiko irrelevanter Löschvorgänge, wodurch der Netzwerkverkehr verringert und eine Netzwerkoptimierung erzielt wird. Gleichzeitig werden bei Festlegung dieses Parameters auf **1** u. U. mehr Metadaten gespeichert, und auf dem Verleger kann es zu Leistungseinbußen kommen, wenn mehrere Ebenen von Joinfiltern und komplexe Teilmengenfilter vorhanden sind. Daher sollten Sie die Replikationstopologie sorgfältig bewerten und **MaxNetworkOptimization** nur dann auf **1** festlegen, wenn durch irrelevante Löschvorgänge mehr Netzwerkverkehr entsteht, als akzeptabel ist.  
  
> [!NOTE]
>  Die Festlegung dieses Parameters auf **1** ist nur dann nützlich, wenn die Option zur Synchronisierungsoptimierung der Mergeveröffentlichung auf **TRUE** festgelegt ist (der Parameter `@keep_partition_changes**` von [sp_addmergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)).  
  
 **-Output** _output_path_and_file_name_  
 Der Pfad der Agentausgabedatei. Wenn kein Dateiname angegeben ist, wird die Ausgabe an die Konsole gesendet. Wenn eine Datei mit dem angegebenen Namen vorhanden ist, wird die Ausgabe an diese Datei angefügt.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Gibt an, ob die Ausgabe ausführlich sein soll.  
  
|Wert von OutputVerboseLevel|BESCHREIBUNG|  
|------------------------------|-----------------|  
|**0**|Nur Fehlermeldungen werden gedruckt.|  
|**1** (Standard)|Alle Statusberichtsmeldungen werden gedruckt (Standard).|  
|**2**|Alle Fehlermeldungen und Statusberichtsmeldungen werden gedruckt, was zum Debuggen nützlich ist.|  
  
 **-PacketSize** _packet_size_  
 Die vom Momentaufnahme-Agent beim Herstellen der Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendete Paketgröße (in Bytes). Der Standardwert ist 8192 Bytes.  
  
> [!NOTE]  
>  Sie sollten die Paketgröße nur dann ändern, wenn Sie sicher sind, dass die Leistung dadurch verbessert werden kann. Für die meisten Anwendungen empfiehlt sich die Standardpaketgröße.  

**-PrefetchTables** [ **0**| **1**]  
 Optionaler Parameter, der angibt, ob die Tabellenobjekte vorab abgerufen und zwischengespeichert werden.  Standardmäßig werden bestimmte Tabelleneigenschaften mithilfe der SMO-Komponente basierend auf einer internen Berechnung vorab abgerufen.  Dieser Parameter kann in Szenarios hilfreich sein, in denen die Ausführung des SMO-Vorabrufvorgangs erheblich länger dauert. Wenn dieser Parameter nicht verwendet wird, wird diese Entscheidung zur Laufzeit basierend auf dem Prozentsatz der Tabellen getroffen, die der Veröffentlichung als Artikel hinzugefügt werden.  
  
|Wert von OutputVerboseLevel|BESCHREIBUNG|  
|------------------------------|-----------------|  
|**0**|Der Aufruf der Prefetch-Methode der SMO-Komponente ist deaktiviert.|  
|**1**|Der Momentaufnahmen-Agent ruft die Prefetch-Methode auf, um einige Tabelleneigenschaften mithilfe von SMO zwischenzuspeichern.|  

 **-ProfileName** _profile_name_  
 Gibt ein Agentprofil an, das für Agentparameter verwendet werden soll. Wenn **ProfileName** den Wert NULL aufweist, wird das Agentprofil deaktiviert. Wenn **ProfileName** nicht angegeben ist, wird das Standardprofil für den Agenttyp verwendet. Weitere Informationen finden Sie unter [Replication Agent Profiles](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 **-PublisherDB** _publisher_database_  
 Der Name der Veröffentlichungsdatenbank. *Der Parameter wird von Oracle-Verlegern nicht unterstützt.*  
  
 **-PublisherDeadlockPriority** [ **-1**|**0**|**1**]  
 Die Priorität der Momentaufnahme-Agent-Verbindung mit dem Verleger, wenn ein Deadlock auftritt. Dieser Parameter wird angegeben, um Deadlocks zu beheben, die möglicherweise während der Momentaufnahmegenerierung zwischen dem Momentaufnahme-Agent und Benutzeranwendungen auftreten.  
  
|Wert von PublisherDeadlockPriority|BESCHREIBUNG|  
|-------------------------------------|-----------------|  
|**-1**|Bei Auftreten eines Deadlocks auf dem Verleger haben andere Anwendungen als der Momentaufnahme-Agent Priorität.|  
|**0** (Standard)|Es wird keine Priorität zugewiesen.|  
|**1**|Bei Auftreten eines Deadlocks auf dem Verleger hat der Momentaufnahme-Agent Priorität.|  
  
 **-PublisherFailoverPartner** _server_name_[ **\\** _instance\_name_]  
 Gibt die Failoverpartnerinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an, die an einer Datenbank-Spiegelungssitzung mit der Veröffentlichungsdatenbank teilnimmt. Weitere Informationen finden Sie unter [Datenbankspiegelung und Replikation &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherLogin** _publisher_login_  
 Der Anmeldename, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Verleger herzustellen.  
  
 **-PublisherPassword**  _publisher_password_  
 Das Kennwort, das verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Verleger herzustellen. erforderlich.  
  
 **-PublisherSecurityMode** [ **0**| **1**]  
 Gibt den Sicherheitsmodus des Verlegers an. Der Wert **0** steht für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung (Standard), der Wert **1** für den Windows-Authentifizierungsmodus.  
  
 **-QueryTimeOut** _query_time_out_seconds_  
 Die Anzahl von Sekunden, nach denen ein Timeout bei der Abfrage eintritt. Die Standardeinstellung ist 1800 Sekunden.  
  
 **-ReplicationType** [ **1**| **2**]  
 Gibt den Typ der Replikation an. Der Wert **1** steht für die Transaktionsreplikation, der Wert **2** für die Mergereplikation.  
  
 **-RowDelimiter** _row_delimiter_  
 Das Zeichen oder die Zeichenfolge, das bzw. die das Ende einer Zeile in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datendatei für das Massenkopieren markiert. Der Standardwert ist \n\<,@g>\n.  
  
 **-StartQueueTimeout** _start_queue_timeout_seconds_  
 Die maximale Anzahl von Sekunden, die der Momentaufnahmen-Agent wartet, wenn die Anzahl gleichzeitig ausgeführter dynamischer Momentaufnahmeprozesse den Grenzwert erreicht, der mit der Eigenschaft `@max_concurrent_dynamic_snapshots` von [sp_addmergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) festgelegt wurde. Wenn der Momentaufnahme-Agent nach Verstreichen der maximalen Anzahl von Sekunden immer noch wartet, wird der Agent beendet. Der Wert 0 bedeutet, dass der Agent unbegrenzt wartet, der Vorgang jedoch abgebrochen werden kann.  
  
 \- **UsePerArticleContentsView** _use_per_article_contents_view_  
 Dieser Parameter wurde als veraltet markiert und wird lediglich aus Gründen der Abwärtskompatibilität unterstützt.  
  
## <a name="remarks"></a>Bemerkungen  
  
> [!IMPORTANT]  
>  Wenn Sie den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent so installiert haben, dass er unter einem lokalen Systemkonto und nicht unter einem Domänenbenutzerkonto (Standard) ausgeführt wird, kann der Dienst nur auf den lokalen Computer zugreifen. Wenn der Momentaufnahme-Agent, der unter dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent ausgeführt wird, so konfiguriert ist, dass beim Anmelden bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]der Windows-Authentifizierungsmodus verwendet wird, schlägt der Momentaufnahme-Agent fehl. Die Standardeinstellung ist die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung.  
  
 Führen Sie zum Starten des Momentaufnahme-Agents von der Eingabeaufforderung **snapshot.exe** aus. Informationen hierzu finden Sie im [Abschnitt zu den ausführbaren Dateien von Replikations-Agents](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations-Agent-Verwaltung](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
