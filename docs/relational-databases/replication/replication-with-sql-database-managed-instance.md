---
title: Replikation mit der verwalteten SQL-Datenbank-Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Database replication
- replication, SQL Database
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8dd8931bcc3fdaaa489d0a190c5ce1f6210e5f64
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088649"
---
# <a name="replication-with-sql-database-managed-instance"></a>Replikation mit der verwalteten SQL-Datenbank-Instanz

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Die verwaltete Azure SQL-Datenbank-Instanz (Vorschauversion) unterstützt die Transaktionsreplikation. Die verwaltete Instanz kann Verleger-, Verteiler- und Abonnentendatenbanken hosten.

## <a name="common-configurations"></a>Allgemeine Konfigurationen

Im Allgemeinen müssen sich sowohl der Verleger als auch der Verteiler in der Cloud oder vor Ort befinden. Die folgenden Konfigurationen werden unterstützt:

- **Verleger mit lokalem Verteiler auf einer verwalteten Instanz**

   ![Replication-with-azure-sql-db-single-managed-instance-publisher-distributor](./media/replication-with-sql-database-managed-instance/01-single-instance-asdbmi-pubdist.png)

   Verleger- und Verteilerdatenbanken werden auf einer einzelnen verwalteten Instanz konfiguriert.

- **Verleger mit externem Verteiler auf einer verwalteten Instanz**

   ![Replication-with-azure-sql-db-separate-managed-instances-publisher-distributor](./media/replication-with-sql-database-managed-instance/02-separate-instances-asdbmi-pubdist.png)

   Verleger und Verteiler werden auf zwei verwalteten Instanzen konfiguriert. In dieser Konfiguration:

  - Beide verwaltete Instanzen befinden sich im selben vNET.

  - Beide verwaltete Instanzen befinden sich im selben Speicherort.

- **Verleger und Verteiler befinden sich vor Ort und der Abonnent auf der verwalteten Instanz**

   ![Replication-from-on-premises-to-azure-sql-db-subscriber](./media/replication-with-sql-database-managed-instance/03-azure-sql-db-subscriber.png)

   In dieser Konfiguration ist die Azure SQL-Datenbank ein Abonnent. Diese Konfiguration unterstützt die Migration von lokalen Einrichtungen zu Azure. In der Abonnentenrolle erfordert die SQL-Datenbank keine verwaltete Instanz, Sie können jedoch eine verwaltete SQL-Datenbank-Instanz als Schritt bei der Migration von lokalen Einrichtungen zu Azure verwenden. Weitere Informationen zu Azure SQL-Datenbank-Abonnenten finden Sie unter [Replikation zu SQL-Datenbank](replication-to-sql-database.md).

## <a name="requirements"></a>Anforderungen

Wenn sich Verleger und Verteiler auf Azure SQL-Datenbank befinden, ist Folgendes erforderlich:

- Verwaltete Azure SQL-Datenbank-Instanz.

   >[!NOTE]
   >Azure SQL-Datenbanken, die nicht mit einer verwalteten Instanz konfiguriert wurden, können nur Abonnenten sein.

- Alle Instanzen von SQL Server müssen sich im gleichen vNet befinden.

- SQL-Authentifizierung wird für die Konnektivität zwischen Teilnehmern der Replikation verwendet.

- Eine Azure-Speicherkontofreigabe für das Arbeitsverzeichnis der Replikation.

## <a name="features"></a>Funktionen

Unterstützt:

- Kombination aus Transaktions-und Momentaufnahmereplikation aus lokalen und verwalteten Azure SQL-Datenbank-Instanz-Instanzen.

- Abonnenten können vor Ort, in der Azure SQL-Datenbank oder in Pools für elastische Datenbanken sein.

- Uni- oder bidirektionale Replikation

## <a name="configure-publishing-and-distribution-example"></a>Beispiel zum Konfigurieren der Veröffentlichung und Verteilung

1. [Erstellen Sie eine verwaltete Azure SQL-Datenbank-Instanz](http://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-create-tutorial-portal) im Portal.

1. [Erstellen Sie ein Azure-Speicherkonto](http://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account) für das Arbeitsverzeichnis. Kopieren Sie die Speicherschlüssel. Weitere Informationen finden Sie unter [Anzeigen und Kopieren von Speicherzugriffsschlüsseln](http://docs.microsoft.com/azure/storage/common/storage-create-storage-account#manage-your-storage-access-keys).

1. Erstellen Sie eine Datenbank für den Verleger.

   Ersetzen Sie in den folgenden Beispielskripts `<Publishing_DB>` durch den Namen der Datenbank.

1. Erstellen Sie einen Datenbankbenutzer mit SQL-Authentifizierung für den Verteiler. Weitere Informationen finden Sie in [Erstellen eines Datenbankbenutzers](http://docs.microsoft.com/azure/sql-database/sql-database-security-tutorial#creating-database-users). Verwenden Sie ein sicheres Kennwort.

   Verwenden Sie in den folgenden Beispielskripts `<SQL_USER>` und `<PASSWORD>` als Benutzer und Kennwort für diese SQL Server-Kontodatenbank.

1. [Stellen Sie eine Verbindung zur verwalteten SQL-Datenbank-Instanz her](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ssms).

1. Führen Sie die folgende Abfrage aus, um den Verteiler und die Verteilungsdatenbank hinzuzufügen.

   ```sql
   USE [master]
   GO
   EXEC sp_adddistributor @distributor = @@ServerName;
   EXEC sp_adddistributiondb @database = N'distribution';
   ```

1. Um einen Verleger für die Verwendung einer bestimmten Verteilungsdatenbank zu konfigurieren, aktualisieren und starten Sie die folgende Abfrage.

   Ersetzen Sie `<SQL_USER>` und `<PASSWORD>` durch das SQL Server-Konto und das Kennwort.

   Ersetzen Sie `\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>` durch den Wert für Ihr Speicherkonto. 

   Ersetzen Sie `<STORAGE_CONNECTION_STRING>` durch den Wert für Ihr Zugriffsschlüssel.

   Nachdem Sie die folgende Abfrage aktualisiert haben, führen Sie sie aus. 

   ```sql
   USE [master]
   EXEC sp_adddistpublisher @publisher = @@ServerName,
                @distribution_db = N'distribution',
                @security_mode = 0,
                @login = N'<SQL_USER>',
                @password = N'<PASSWORD>',
                @working_directory = N'\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>',
                @storage_connection_string = N'<STORAGE_CONNECTION_STRING>';
   GO
   ```

1. Konfigurieren Sie den Verleger für die Replikation. 

    Ersetzen Sie in der folgenden Abfrage `<Publishing_DB>` mit dem Namen Ihrer Verlegerdatenbank.

    Ersetzen Sie `<Publication_Name>` durch den Namen für die Veröffentlichung.

    Ersetzen Sie `<SQL_USER>` und `<PASSWORD>` durch das SQL Server-Konto und das Kennwort.

    Nachdem Sie die folgende Abfrage aktualisiert haben, führen Sie sie aus, um die Veröffentlichung zu erstellen.

   ```sql
   USE [<Publishing_DB>]
   EXEC sp_replicationdboption @dbname = N'<Publishing_DB>',
                @optname = N'publish',
                @value = N'true';

   EXEC sp_addpublication @publication = N'<Publication_Name>',
                @status = N'active';

   EXEC sp_changelogreader_agent @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>';

   EXEC sp_addpublication_snapshot @publication = N'<Publication_Name>',
                @frequency_type = 1,
                @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>'
   ```

1. Fügen Sie den Artikel, das Abonnement und den Pushabonnement-Agent hinzu. 

   Um diese Objekte hinzuzufügen, aktualisieren Sie das folgende Skript.

   Ersetzen Sie `<Object_Name>` durch den Namen des Replikationsobjekts.

   Ersetzen Sie `<Object_Schema>` durch den Namen des Quellschemas. 

   Ersetzen Sie die anderen Parameter in spitzen Klammern `<>` entsprechend der Werte in den vorhergehenden Skripts. 

   ```sql
   EXEC sp_addarticle @publication = N'<Publication_Name>',
                @type = N'logbased',
                @article = N'<Object_Name>',
                @source_object = N'<Object_Name>',
                @source_owner = N'<Object_Schema>'

   EXEC sp_addsubscription @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @destination_db = N'<Subscribing_DB>',
                @subscription_type = N'Push'

   EXEC sp_addpushsubscription_agent @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @subscriber_db = N'<Subscribing_DB>',
                @subscriber_security_mode = 0,
                @subscriber_login = N'<SQL_USER>',
                @subscriber_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>', 
                @job_password = N'<PASSWORD>'
   GO
   ```

## <a name="limitations"></a>Einschränkungen

Die folgenden Features werden nicht unterstützt:

- Aktualisierbare Abonnements

- Aktive Georeplikation

## <a name="see-also"></a>Weitere Informationen finden Sie unter

- [Was ist eine verwaltete Instanz (Vorschauversion)?](http://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)