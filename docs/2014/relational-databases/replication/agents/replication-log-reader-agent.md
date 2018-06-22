---
title: Replikationsprotokolllese-Agents | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Log Reader Agent, executables
- Log Reader Agent, parameter reference
- agents [SQL Server replication], Log Reader Agent
- command prompt [SQL Server replication]
ms.assetid: 5487b645-d99b-454c-8bd2-aff470709a0e
caps.latest.revision: 50
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 8bef914f1fd6a2cd4dff784808e5334d3871d81c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050094"
---
# <a name="replication-log-reader-agent"></a>Replikationsprotokolllese-Agent
  Der Replikationsprotokolllese-Agent ist eine ausführbare Datei, die das Transaktionsprotokoll jeder für die Transaktionsreplikation konfigurierten Datenbank überwacht und die für die Replikation markierten Transaktionen aus dem Transaktionsprotokoll in die Verteilungsdatenbank kopiert.  
  
> [!NOTE]  
>  Parameter können in beliebiger Reihenfolge angegeben werden. Wenn keine optionalen Parameter angegeben werden, werden vordefinierte Werte auf Grundlage des Standardagentprofils verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      logread [-?]   
-Publisherserver_name[\instance_name]   
-PublisherDBpublisher_database   
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-HistoryVerboseLevel [0|1|2]]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-LogScanThresholdscan_threshold]  
[-MaxCmdsInTrannumber_of_commands]  
[-MessageIntervalmessage_interval]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2|3|4]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]   
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherSecurityMode [0|1]]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-QueryTimeOutquery_time_out_seconds]  
[-ReadBatchSizenumber_of_transactions]   
[-ReadBatchThresholdread_batch_threshold]  
[-RecoverFromDataErrors]  
```  
  
## <a name="arguments"></a>Argumente  
 **-?**  
 Zeigt Informationen zur Verwendung an.  
  
 **-Publisher** *Servername*[**\\***Instanzname*]  
 Der Name des Verlegers. Geben Sie *server_name* für die Standardinstanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Geben Sie *server_name***\\***instance_name* für eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an.  
  
 **-PublisherDB** *publisher_database*  
 Der Name der Verlegerdatenbank.  
  
 **-Continuous**  
 Gibt an, ob der Agent fortlaufend versucht, replizierte Transaktionen abzurufen. Wenn dieses Argument angegeben ist, ruft der Agent replizierte Transaktionen in festgelegten Abrufintervallen aus der Quelle ab, selbst wenn keine ausstehenden Transaktionen vorhanden sind.  
  
 **-DefinitionFile** *def_path_and_file_name*  
 Der Pfad der Agentdefinitionsdatei. Eine Agentdefinitionsdatei enthält Befehlszeilenargumente für den Agent. Der Inhalt der Datei wird als ausführbare Datei analysiert. Verwenden Sie doppelte Anführungszeichen ("), um Argumentwerte anzugeben, die beliebige Zeichen enthalten.  
  
 **-Distributor** *Servername*[**\\***Instanzname*]  
 Der Name des Verteilers. Geben Sie *server_name* für die Standardinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Geben Sie *server_name***\\***instance_name* für eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an.  
  
 **-DistributorLogin** *distributor_login*  
 Der Anmeldename des Verteilers.  
  
 **-DistributorPassword** *distributor_password*  
 Das Verteilerkennwort.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Gibt den Sicherheitsmodus des Verteilers an. Der Wert **0** steht für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierungsmodus (Standard), der Wert **1** für den [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Authentifizierungsmodus.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Die Ebene der SSL-Verschlüsselung (Secure Sockets Layer), die vom Protokolllese-Agent beim Herstellen von Verbindungen verwendet wird.  
  
|Wert von EncryptionLevel|Description|  
|---------------------------|-----------------|  
|**0**|Gibt an, dass SSL nicht verwendet wird.|  
|**1**|Gibt an, dass SSL verwendet wird, der Agent jedoch nicht überprüft, ob das SSL-Serverzertifikat von einem vertrauenswürdigen Aussteller signiert wurde.|  
|**2**|Gibt an, dass SSL verwendet und das Zertifikat überprüft wird.|  
  
 Weitere Informationen finden Sie unter [Sicherheitsübersicht &#40;Replikation&#41;](../security/security-overview-replication.md).  
  
 **-ExtendedEventConfigFile** *configuration_path_and_file_name*  
 Gibt den Pfad und den Dateinamen für die erweiterte Ereignis-XML-Konfigurationsdatei an. Die erweiterten Ereignis-Konfigurationsdatei ermöglicht das Konfigurieren von Sitzungen und das Aktivieren der Nachverfolgung für Ereignisse.  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**]  
 Gibt den Umfang des Verlaufs an, der während eines Vorgangs des Protokolllese-Agents protokolliert wird. Sie können die negativen Auswirkungen der Verlaufsprotokollierung auf die Leistung minimieren, indem Sie den Wert **1**auswählen.  
  
|Wert von <legacyBold>HistoryVerboseLevel</legacyBold>|Description|  
|-------------------------------|-----------------|  
|**0**||  
|**1**|Standard. Aktualisieren Sie immer eine vorherige Verlaufsmeldung mit dem gleichen Status (Start, Status, Erfolg usw.). Wenn kein vorheriger Datensatz mit dem gleichen Status vorhanden ist, fügen Sie einen neuen Datensatz ein.|  
|**2**|Fügen Sie neue Verlaufsdatensätze ein, es sei denn, der Datensatz bezieht sich z. B. auf Leerlaufmeldungen oder Meldungen zu Aufträgen mit langer Ausführungszeit. In diesen Fällen aktualisieren Sie die vorherigen Datensätze.|  
  
 **-KeepAliveMessageInterval** *keep_alive_message_interval_seconds*  
 Die Anzahl von Sekunden, bevor vom Verlaufsthread geprüft wird, ob bestehende Verbindungen auf eine Antwort vom Server warten. Dieser Wert kann verringert werden, damit der Protokolllese-Agent vom Überprüfungs-Agent nicht als fehlerverdächtig markiert wird, wenn ein lang andauernder Batch ausgeführt wird. Der Standardwert ist 300 Sekunden.  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 Die Anzahl von Sekunden, nach denen ein Timeout bei der Anmeldung eintritt. Der Standardwert ist 15 Sekunden.  
  
 **-LogScanThreshold** *scan_threshold*  
 Nur interne Verwendung.  
  
 **-MaxCmdsInTran** *number_of_commands*  
 Gibt die maximale Anzahl von Anweisungen an, die in einer Transaktion zusammengefasst werden, wenn der Protokolllese-Agent Befehle in die Verteilungsdatenbank schreibt. Mithilfe dieses Parameters können der Protokolllese-Agent und der Verteilungs-Agent beim Anwenden auf dem Abonnenten umfangreiche Transaktionen (die aus zahlreichen Befehlen bestehen) auf dem Verleger in mehrere kleinere Transaktionen aufteilen. Durch die Angabe dieses Parameters kommt es auf dem Verteiler möglicherweise zu weniger Konflikten, und die Latenzzeit zwischen Verleger und Abonnent kann reduziert werden. Da die ursprüngliche Transaktion in kleineren Einheiten angewendet wird, kann der Abonnent vor Ende der ursprünglichen Transaktion auf Zeilen einer umfangreichen logischen Verleger-Transaktion zugreifen; dies widerspricht der strikten Unteilbarkeit von Transaktionen. **0**ist der Standardwert, durch den die Transaktionsgrenzen des Verlegers beibehalten werden.  
  
> [!NOTE]  
>  Für Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Veröffentlichungen wird dieser Parameter ignoriert. Weitere Informationen finden Sie im Abschnitt "Konfigurieren des Transaktionssatz-Auftrags" unter [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md).  
  
 **-MessageInterval** *Meldungsintervall*  
 Das für die Verlaufsprotokollierung verwendete Zeitintervall. Wenn nach der Protokollierung des letzten Verlaufsereignisses der Wert von **MessageInterval** erreicht wird, wird erneut ein Verlaufsereignis protokolliert.  
  
 Wenn an der Quelle keine replizierte Transaktion vorhanden ist, sendet der Agent eine entsprechende Meldung an den Verteiler. Mit dieser Option wird angegeben, wie lange der Agent wartet, bevor eine weitere Meldung gesendet wird, dass keine Transaktion vorhanden ist. Agents melden immer, dass keine Transaktion vorhanden ist, wenn sie feststellen, dass an der Quelle keine Transaktionen verfügbar sind, nachdem zuvor replizierte Transaktionen verarbeitet wurden. Der Standardwert ist 60 Sekunden.  
  
 **-Output** *output_path_and_file_name*  
 Der Pfad der Agentausgabedatei. Wenn kein Dateiname angegeben ist, wird die Ausgabe an die Konsole gesendet. Wenn eine Datei mit dem angegebenen Namen vorhanden ist, wird die Ausgabe an diese Datei angefügt.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]  
 Gibt an, ob die Ausgabe ausführlich sein soll.  
  
|value|Description|  
|-----------|-----------------|  
|**0**|Nur Fehlermeldungen werden gedruckt.|  
|**1**|Alle Agent-Statusberichtsmeldungen werden gedruckt.|  
|**2** (Standardwert)|Alle Fehlermeldungen und Agent-Statusberichtsmeldungen werden gedruckt.|  
|**3**|Die ersten 100 Bytes jedes replizierten Befehls werden gedruckt.|  
|**4**|Alle replizierten Befehle werden gedruckt.|  
  
 Die Werte 2-4 sind beim Debuggen hilfreich.  
  
 **-PacketSize** *packet_size*  
 Die Paketgröße in Bytes. Der Standardwert ist 4096 (Bytes).  
  
 **-PollingInterval** *polling_interval*  
 Gibt an, wie häufig replizierte Transaktionen aus dem Protokoll abgefragt werden (in Sekunden). Die Standardeinstellung ist 5 Sekunden.  
  
 **-ProfileName** *profile_name*  
 Gibt ein Agentprofil an, das für Agentparameter verwendet werden soll. Wenn **ProfileName** den Wert NULL aufweist, wird das Agentprofil deaktiviert. Wenn **ProfileName** nicht angegeben ist, wird das Standardprofil für den Agenttyp verwendet. Weitere Informationen finden Sie unter [Replication Agent Profiles](replication-agent-profiles.md).  
  
 **-PublisherFailoverPartner** *Servername*[**\\***Instanzname*]  
 Gibt die Failoverpartnerinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an, die an einer Datenbank-Spiegelungssitzung mit der Veröffentlichungsdatenbank teilnimmt. Weitere Informationen finden Sie unter [Datenbankspiegelung und Replikation &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherSecurityMode** [ **0**| **1**]  
 Gibt den Sicherheitsmodus des Verlegers an. Der Wert **0** steht für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung (Standard), der Wert **1** für den Windows-Authentifizierungsmodus.  
  
 **-PublisherLogin** *publisher_login*  
 Der Anmeldename des Verlegers.  
  
 **-PublisherPassword** *publisher_password*  
 Das Kennwort des Verlegers.  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 Die Anzahl von Sekunden, nach denen ein Timeout bei der Abfrage eintritt. Die Standardeinstellung ist 1800 Sekunden.  
  
 **-ReadBatchSize** *number_of_transactions*  
 Die maximale Anzahl von Transaktionen, die pro Verarbeitungszyklus aus dem Transaktionsprotokoll der Veröffentlichungsdatenbank ausgelesen werden. Der Standardwert lautet 500. Der Agent setzt das Lesen von Transaktionen in Batches fort, bis alle Transaktionen aus dem Protokoll gelesen wurden. Der Parameter wird von Oracle-Verlegern nicht unterstützt.  
  
 **-ReadBatchThreshold** *number_of_commands*  
 Die Anzahl von Replikationsbefehlen, die aus dem Transaktionsprotokoll gelesen werden sollen, bevor sie vom Verteilungs-Agent an den Abonnenten ausgegeben werden. Die Standardeinstellung ist 0. Wenn dieser Parameter nicht angegeben wird, liest der Protokolllese-Agent bis zum Ende des Protokolls oder bis zu der Nummer, die in **-ReadBatchSize** (Anzahl von Transaktionen) angegeben wurde.  
  
 **-RecoverFromDataErrors**  
 Gibt an, dass der Protokolllese-Agent weiter ausgeführt wird, wenn in Spaltendaten, die von einem Nicht-SQL Server-Verleger veröffentlicht wurden, Fehler auftreten. Standardmäßig bewirken solche Fehler, dass der Protokolllese-Agent fehlschlägt. Bei Verwendung von **-RecoverFromDataErrors**werden fehlerhafte Spaltendaten entweder als NULL oder als geeigneter Nicht-NULL-Wert repliziert, und in der [MSlogreader_history](/sql/relational-databases/system-tables/mslogreader-history-transact-sql) -Tabelle werden Warnmeldungen protokolliert. Der Parameter wird nur von Oracle-Verlegern unterstützt.  
  
## <a name="remarks"></a>Hinweise  
  
> [!IMPORTANT]  
>  Wenn Sie den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent so installiert haben, dass er unter einem lokalen Systemkonto und nicht unter einem Domänenbenutzerkonto (Standard) ausgeführt wird, kann der Dienst nur auf den lokalen Computer zugreifen. Wenn der Protokolllese-Agent, der unter dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent ausgeführt wird, so konfiguriert ist, dass beim Anmelden bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]der Windows-Authentifizierungsmodus verwendet wird, schlägt der Protokolllese-Agent fehl. Die Standardeinstellung ist die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung. Weitere Informationen zum Ändern von Sicherheitskonten finden Sie unter [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md).  
  
 Führen Sie zum Starten des Protokolllese-Agents von der Eingabeaufforderung **logread.exe** aus. Informationen hierzu finden Sie unter [Ausführbare Konzepte für die Programmierung von Replikations-Agents](../concepts/replication-agent-executables-concepts.md).  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|Der **-ExtendedEventConfigFile** -Parameter wurde hinzugefügt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikations-Agent-Verwaltung](replication-agent-administration.md)  
  
  
