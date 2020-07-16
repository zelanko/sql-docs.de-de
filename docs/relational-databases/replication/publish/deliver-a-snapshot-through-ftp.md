---
title: Übermitteln einer Momentaufnahme über FTP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 99872c4f-40ce-4405-8fd4-44052d3bd827
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2ff609e78a0076cd3d6c0ff15348869cc717cfe
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893278"
---
# <a name="deliver-a-snapshot-through-ftp"></a>Übermitteln einer Momentaufnahme über FTP
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird beschrieben, wie in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]eine Momentaufnahme über FTP bereitgestellt wird.  

Standardmäßig werden Momentaufnahmen in Ordnern gespeichert, die als im UNC-Format (Universal Naming Convention) angegebene Dateifreigaben definiert sind. Bei der Replikation haben Sie ebenfalls die Möglichkeit, FTP-Freigaben (FTP, File Transfer Protocol) anstelle der UNC-Freigaben anzugeben. Dazu müssen Sie einen FTP-Server und anschließend eine Veröffentlichung sowie mindestens ein Abonnement über FTP konfigurieren. Informationen dazu, wie ein FTP-Server konfiguriert wird, finden Sie in der Internetinformationsdienste (IIS)-Dokumentation. Wenn Sie FTP-Informationen für eine Veröffentlichung angeben, verwenden die Abonnements dieser Veröffentlichung standardmäßig FTP. FTP wird nur zur Websynchronisierung verwendet, wenn der Computer, auf dem IIS (Internet Information Services, Internetinformationsdienste) ausgeführt wird, vom Verteiler durch eine Firewall getrennt ist. In diesem Fall kann die Momentaufnahme über FTP vom Verteiler an den Computer, auf dem IIS ausgeführt wird, gesendet werden. (Zur Übertragung der Momentaufnahme an den Abonnenten wird immer HTTPS verwendet.)  
  
> [!IMPORTANT]  
>  Es wird empfohlen, vorzugsweise die Microsoft Windows-Authentifizierung und eine UNC-Freigabe statt einer FTP-Freigabe zu verwenden, da FTP-Kennwörter gespeichert werden müssen, und das Kennwort vom Abonnenten oder von dem Computer, auf dem IIS bei der Websynchronisierung ausgeführt wird, als unverschlüsselter Text an den FTP-Server gesendet wird. Außerdem ist es bei der Übertragung über FTP nicht möglich, sicherzustellen, dass ein Abonnent einer gefilterten Mergeveröffentlichung ausschließlich auf die Momentaufnahmen seiner Datenpartition zugreifen kann, da ein einziges Konto den Zugriff auf die gesamte Momentaufnahme-Freigabe kontrolliert.  
  

## <a name="limitations-and-restrictions"></a>Einschränkungen  
  
-   Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\ftpserver\home\snapshots. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
-   Zum Übertragen von Momentaufnahmedateien über FTP (File Transfer Protocol) müssen Sie zuerst einen FTP-Server konfigurieren. Weitere Informationen finden Sie in der Dokumentation zu den [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internetinformationsdiensten (IIS).  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
 Implementieren Sie ein virtuelles privates Netzwerk (VPN), wenn Sie FTP-Momentaufnahmeübermittlung über das Internet verwenden, um die Sicherheit zu verbessern. Weitere Informationen finden Sie unter [Veröffentlichen von Daten über das Internet mithilfe von VPN](../../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md).  
  
 Lassen Sie als bewährte Sicherheitsmethode keine anonymen Anmeldungen am FTP-Server zu. Der Momentaufnahme-Agent muss Schreibberechtigungen für das angegebene Verzeichnis und der Verteilungs-Agent oder Merge-Agent muss Leseberechtigungen besitzen. Bei Verwendung von Pullabonnements müssen Sie ein freigegebenes Verzeichnis als UNC-Pfad angeben, wie z.B. \\\ftpserver\home\snapshots. Weitere Informationen finden Sie unter [Schützen des Momentaufnahmeordners](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
 Die Benutzer sollten nach Möglichkeit während der Laufzeit zur Eingabe von Anmeldeinformationen aufgefordert werden. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden, müssen Sie sicherstellen, dass die Datei geschützt ist.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Geben Sie nach dem Konfigurieren des FTP-Servers im Dialogfeld **Veröffentlichungseigenschaften \<Publication>** ein Verzeichnis und Sicherheitsinformationen für diesen Server an. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-ftp-information"></a>So geben Sie FTP-Informationen an  
  
1.  Aktivieren Sie im Dialogfeld **Veröffentlichungseigenschaften – \<Publication>** die Option **Abonnenten das Herunterladen von Momentaufnahmedateien über FTP (File Transfer Protocol) ermöglichen** auf einer der folgenden Seiten:  
  
    -   Seite **FTP-Momentaufnahme** für Momentaufnahmen- und Transaktionsveröffentlichungen sowie Mergeveröffentlichungen für Verleger, auf denen niedrigere Versionen als [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ausgeführt werden  
  
    -   Der Seite **FTP-Momentaufnahme und Internet** , für Mergeveröffentlichungen von Verlegern, auf denen [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher ausgeführt wird.  
  
2.  Geben Sie Werte für **FTP-Servername**, **Portnummer**, **Pfad des FTP-Stammordners**, **Anmeldename**und **Kennwort**an.  
  
     Wenn beispielsweise der FTP-Stammordner \\\ftpserver\home lautet und Momentaufnahmen in \\\ftpserver\home\snapshots gespeichert werden sollen, geben Sie \snapshots\ftp für die Eigenschaft **Pfad des FTP-Stammordners** an (von der Replikation wird beim Erstellen der Momentaufnahmedateien „ftp“ an den Pfad des Momentaufnahmeordners angehängt).  
  
3.  Geben Sie an, dass der Momentaufnahme-Agent die Momentaufnahmedateien in das in Schritt 2 angegebene Verzeichnis schreiben soll. Wenn der Momentaufnahme-Agent beispielsweise die Momentaufnahmedateien in das Verzeichnis \\\ftpserver\home\snapshots\ftp schreiben soll, müssen Sie den Pfad \\\ftpserver\home\snapshots an einer von zwei Stellen angeben:  
  
    -   Dem Standardspeicherort für Momentaufnahmen für den Verteiler, dem diese Veröffentlichung zugeordnet ist.    
    -   Einem alternativen Speicherort für den Momentaufnahmeordner für diese Veröffentlichung. Ein alternativer Speicherort ist erforderlich, wenn die Momentaufnahme komprimiert wird.  

Weitere Informationen zum Ändern der Eigenschaften für den Momentaufnahmeordner finden Sie unter [Momentaufnahmeoptionen](../snapshot-options.md).
  

4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Die Option, Momentaufnahmedateien auf einem FTP-Server verfügbar zu machen, und die entsprechenden FTP-Einstellungen können mithilfe gespeicherter Replikationsprozeduren programmgesteuert festgelegt und geändert werden. Welche Prozedur verwendet wird, hängt vom Typ der Veröffentlichung ab. FTP-Momentaufnahmeübermittlung wird nur bei Pullabonnements verwendet.  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-snapshot-or-transactional-publication"></a>So aktivieren Sie die FTP-Momentaufnahmeübermittlung für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Geben Sie `@publication`, einen **TRUE**-Wert für `@enabled_for_internet` und entsprechende Werte für die folgenden Parameter an:  
  
    -   `@ftp_address` &ndash; die Adresse des FTP-Servers, der für die Übermittlung der Momentaufnahme verwendet wird.  
  
    -   (Optional) `@ftp_port`: der vom FTP-Server verwendete Port.  
  
    -   (Optional) `@ftp_subdirectory`: das Unterverzeichnis des einer FTP-Anmeldung zugewiesenen Standard-FTP-Verzeichnisses. Wenn beispielsweise der FTP-Stammordner „\\\ftpserver\home“ lautet und Momentaufnahmen in „\\\ftpserver\home\snapshots“ gespeichert werden sollen, geben Sie „ **\snapshots\ftp**“ für `@ftp_subdirectory` an (von der Replikation wird beim Erstellen der Momentaufnahmedateien „ftp“ an den Pfad des Momentaufnahmeordners angehängt).  
  
    -   (Optional) `@ftp_login`: das Anmeldekonto, das beim Herstellen einer Verbindung mit dem FTP-Server verwendet wird.  
  
    -   (Optional) `@ftp_password`: das Kennwort für die FTP-Anmeldung.  
  
     Dadurch wird eine Veröffentlichung erstellt, die FTP verwendet. Weitere Informationen finden Sie unter [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-merge-publication"></a>So aktivieren Sie die FTP-Momentaufnahmeübermittlung für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)aus. Geben Sie `@publication`, einen **TRUE**-Wert für `@enabled_for_internet` und entsprechende Werte für die folgenden Parameter an:  
  
    -   `@ftp_address` &ndash; die Adresse des FTP-Servers, der für die Übermittlung der Momentaufnahme verwendet wird.  
  
    -   (Optional) `@ftp_port`: der vom FTP-Server verwendete Port.  
  
    -   (Optional) `@ftp_subdirectory`: das Unterverzeichnis des einer FTP-Anmeldung zugewiesenen Standard-FTP-Verzeichnisses. Wenn beispielsweise der FTP-Stammordner „\\\ftpserver\home“ lautet und Momentaufnahmen in „\\\ftpserver\home\snapshots“ gespeichert werden sollen, geben Sie „ **\snapshots\ftp**“ für `@ftp_subdirectory` an (von der Replikation wird beim Erstellen der Momentaufnahmedateien „ftp“ an den Pfad des Momentaufnahmeordners angehängt).  
  
    -   (Optional) `@ftp_login`: das Anmeldekonto, das beim Herstellen einer Verbindung mit dem FTP-Server verwendet wird.  
  
    -   (Optional) `@ftp_password`: das Kennwort für die FTP-Anmeldung.  
  
     Dadurch wird eine Veröffentlichung erstellt, die FTP verwendet. Weitere Informationen finden Sie unter [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication-that-uses-ftp-snapshot-delivery"></a>So erstellen Sie ein Pullabonnement für eine Momentaufnahme- oder Transaktionsveröffentlichung, die FTP-Snapshotübermittlung verwendet  
  
1.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)aus. Geben Sie `@publisher` und `@publication` an.  
  
    -   Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)aus. Geben Sie `@publisher`, `@publisher_db` und `@publication`, die Windows-Anmeldeinformationen für [!INCLUDE[msCoName](../../../includes/msconame-md.md)], unter denen der Verteilungs-Agent auf dem Abonnenten für `@job_login` und `@job_password` ausgeführt wird, sowie einen **TRUE**-Wert für `@use_ftp` an.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) aus, um das Pullabonnement zu registrieren. Weitere Informationen finden Sie unter [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication-that-uses-ftp-snapshot-delivery"></a>So erstellen Sie ein Pullabonnement für eine Mergeveröffentlichung, die FTP-Momentaufnahmeübermittlung verwendet  
  
1.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)aus. Geben Sie `@publisher` und `@publication` an.  
  
2.  Führen Sie auf dem Abonnenten für die Abonnementdatenbank [sp_addmergepullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)aus. Geben Sie `@publisher`, `@publisher_db` und `@publication`, die Windows-Anmeldeinformationen, unter denen der Verteilungs-Agent auf dem Abonnenten für `@job_login` und `@job_password` ausgeführt wird, sowie einen `true`-Wert für `@use_ftp` an.  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md) aus, um das Pullabonnement zu registrieren. Weitere Informationen finden Sie unter [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
#### <a name="to-change-one-or-more-ftp-snapshot-delivery-settings-for-a-snapshot-or-transactional-publication"></a>So ändern Sie eine oder mehrere Einstellungen der FTP-Momentaufnahmeübermittlung für eine Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)aus. Geben Sie einen der folgenden Werte für `@property` und einen neuen Wert dieser Einstellung für `@value` an:  
  
    -   `ftp_address `: die Adresse des FTP-Servers, der für die Übermittlung der Momentaufnahme verwendet wird.  
  
    -   `ftp_port` &ndash; der vom FTP-Server verwendete Port.  
  
    -   `ftp_subdirectory` &ndash; das Unterverzeichnis des einer FTP-Anmeldung zugewiesenen Standard-FTP-Verzeichnisses.  
  
    -   `ftp_login` &ndash; der Anmeldenamen, der zum Herstellen einer Verbindung mit dem FTP-Server verwendet wird.  
  
    -   `ftp_password` &ndash; das Kennwort für die FTP-Anmeldung.  
  
2.  (Optional) Wiederholen Sie Schritt 1 für jede zu ändernde FTP-Einstellung.  
  
3.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) aus, um die FTP-Momentaufnahmeübermittlung zu deaktivieren. Geben Sie einen `enabled_for_internet`-Wert für `@property` und einen `false`-Wert für `@value` an.  
  
#### <a name="to-change-ftp-snapshot-delivery-settings-for-a-merge-publication"></a>So ändern Sie die Einstellungen der FTP-Momentaufnahmeübermittlung für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)aus. Geben Sie einen der folgenden Werte für `@property` und einen neuen Wert dieser Einstellung für `@value` an:  
  
    -   `ftp_address` &ndash; die Adresse des FTP-Servers, der für die Übermittlung der Momentaufnahme verwendet wird.  
  
    -   `ftp_port` &ndash; der vom FTP-Server verwendete Port.  
  
    -   `ftp_subdirectory` &ndash; das Unterverzeichnis des einer FTP-Anmeldung zugewiesenen Standard-FTP-Verzeichnisses.  
  
    -   `ftp_login` &ndash; der Anmeldenamen, der zum Herstellen einer Verbindung mit dem FTP-Server verwendet wird.  
  
    -   `ftp_password` &ndash; das Kennwort für die FTP-Anmeldung.  
  
2.  (Optional) Wiederholen Sie Schritt 1 für jede zu ändernde FTP-Einstellung.  
  
3.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) aus, um die FTP-Momentaufnahmeübermittlung zu deaktivieren. Geben Sie einen `enabled_for_internet`-Wert für `@property` und einen `false`-Wert für `@value` an.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 Im folgenden Beispiel wird eine Mergeveröffentlichung erstellt, die Abonnenten ermöglicht, über FTP auf die Momentaufnahmedaten zuzugreifen. Beim Zugreifen auf die FTP-Freigabe sollte der Abonnent eine sichere VPN-Verbindung verwenden. **sqlcmd** -Skriptvariablen werden verwendet, um Anmelde- und Kennwortwerte anzugeben. Weitere Informationen finden Sie unter [Verwenden von sqlcmd mit Skriptvariablen](../../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepub_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_1.sql)]  
  
 Im folgenden Beispiel wird ein Abonnement für eine Mergeveröffentlichung erstellt, bei dem der Abonnent die Momentaufnahme über FTP abruft. Beim Zugreifen auf die FTP-Freigabe sollte der Abonnent eine sichere VPN-Verbindung verwenden. **sqlcmd** -Skriptvariablen werden verwendet, um Anmelde- und Kennwortwerte anzugeben. Weitere Informationen finden Sie unter [Verwenden von sqlcmd mit Skriptvariablen](../../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepullsub_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_2.sql)]  
  
 [!code-sql[HowTo#sp_createmergepullsubagent_ftp](../../../relational-databases/replication/codesnippet/tsql/deliver-a-snapshot-throu_3.sql)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
