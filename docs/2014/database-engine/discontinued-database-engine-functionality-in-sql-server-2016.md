---
title: Nicht mehr unterstützte Datenbank-Engine Funktionen in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- VIA protocol
- unsupported features [SQL Server]
- SQL Mail
- discontinued functionality [SQL Server]
- RESTORE WITH DBO_ONLY
- BACKUP WITH PASSWORD
- user instances enabled
- BACKUP WITH MEDIAPASSWORD
- AWE
- SQL-DMO
- '*= and =*'
- 80 compatibility levels
- COMPUTE BY
- user instance timeout
- sp_dropalias
- COMPUTE
- WITH APPEND
- sys.database_principal_aliases
- sp_dboption
- DATABASEPROPERTY
- FASTFIRSTROW hint
- SET DISABLE_DEF_CNST_CHK
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 14924dedee04345c593683752baff4161c8d270d
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933151"
---
# <a name="discontinued-database-engine-functionality-in-sql-server-2014"></a>Nicht mehr unterstützte Datenbank-Engine-Funktionalität in SQL Server 2014
  In diesem Thema werden die [!INCLUDE[ssDE](../includes/ssde-md.md)] -Funktionen beschrieben, die in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]nicht mehr verfügbar sind.  
  
## <a name="discontinued-features-in-sssql14"></a><a name="SQL14"></a>Nicht mehr unterstützte Features[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 In der folgenden Tabelle sind Funktionen aufgeführt, die nicht mehr in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] enthalten sind.  
  
|Category|Nicht mehr unterstützte Funktion|Ersatz|  
|--------------|--------------------------|-----------------|  
|Kompatibilitätsgrad|Kompatibilitätsgrad 90|Der Kompatibilitätsgrad der Datenbanken muss mindestens auf 100 festgelegt sein. Wird eine Datenbank mit einem Kompatibilitätsgrad unter 100 auf [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] aktualisiert, wird der Kompatibilitätsgrad der Datenbank während des Upgradevorgangs auf 100 festgelegt.|  
  
## <a name="discontinued-features-in-sssql11"></a><a name="Denali"></a>Nicht mehr unterstützte Features[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 In der folgenden Tabelle sind Funktionen aufgeführt, die nicht mehr in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] enthalten sind.  
  
|Category|Nicht mehr unterstützte Funktion|Ersatz|  
|--------------|--------------------------|-----------------|  
|Sichern und Wiederherstellen|Die **Sicherung von {Database &#124; Log} mit Kennwort** und **Backup {Database &#124; log} with MEDIAPASSWORD** wird eingestellt. **Restore {Database &#124; log} with [Media] Password**wird weiterhin als veraltet markiert.|Keine|  
|Sichern und Wiederherstellen|**{Database &#124; Log} wiederherstellen... mit DBO_ONLY**|**{Database &#124; Log} wiederherstellen...... mit RESTRICTED_USER**|  
|Kompatibilitätsgrad|Kompatibilitätsgrad 80|Der Kompatibilitätsgrad der Datenbanken muss mindestens auf 90 festgelegt sein.|  
|Konfigurationsoptionen|`sp_configure 'user instance timeout'` und `'user instances enabled'`|Verwenden Sie die Funktion Lokale Datenbank. Weitere Informationen finden Sie unter [sqllocaldb-Hilfsprogramm](../tools/sqllocaldb-utility.md) .|  
|Verbindungsprotokolle|Die Unterstützung für das VIA-Protokoll wird eingestellt.|Verwenden Sie stattdessen TCP.|  
|Datenbankobjekte|`WITH APPEND`-Klausel für Trigger|Erstellen Sie den ganzen Trigger neu.|  
|Datenbankoptionen|`sp_dboption`|`ALTER DATABASE`|  
|E-Mail|SQL Mail|Verwenden Sie Datenbank-E-Mail. Weitere Informationen finden Sie unter [Datenbank-E-Mail](../relational-databases/database-mail/database-mail.md) und [Verwenden von Datenbank-E-Mail anstelle von SQL Mail](../relational-databases/policy-based-management/use-database-mail-instead-of-sql-mail.md).|  
|Speicherverwaltung|Unterstützung für 32-Bit-AWE (Address Windowing Extensions) und für das Hinzufügen von 32-Bit-Speicher im laufenden Systembetrieb (Hot Add Memory).|Verwenden Sie ein 64-Bit-Betriebssystem.|  
|Metadaten|`DATABASEPROPERTY`|`DATABASEPROPERTYEX`|  
|Programmierbarkeit|SQL Server-Distributed Management Objects (SQL-DMO)|SQL Server Management Objects (SMO)|  
|Abfragehinweise|`FASTFIRSTROW`-Hinweis|`OPTION (FAST`*n* `)` .|  
|Remoteserver|Das Erstellen neuer Remoteserver durch Benutzer mithilfe von `sp_addserver` wird eingestellt. `sp_addserver` mit der Option "local" bleibt erhalten. Während des Upgrades beibehaltene oder durch Replikation erstellte Remoteserver können verwendet werden.|Ersetzen Sie Remoteserver mithilfe von Verbindungsservern.|  
|Sicherheit|`sp_dropalias`|Ersetzen Sie Aliase durch eine Kombination von Benutzerkonten und Datenbankrollen. Verwenden Sie `sp_dropalias`, um Aliase in aktualisierten Datenbanken zu entfernen.|  
|Sicherheit|Der Versions Parameter von **PWDCOMPARE** , der einen Wert aus einer Anmeldung vor 2000 darstellt, wird nicht mehr unterstützt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|Keine|  
|Service Broker-Programmierbarkeit in SMO|Die **Microsoft. SqlServer. Management. Smo. Broker. brokerpriority** -Klasse implementiert nicht mehr die **Microsoft. SqlServer. Management. Smo. iobjectberechtigungs** -Schnittstelle.||  
|SET-Optionen|`SET DISABLE_DEF_CNST_CHK`|Keine.|  
|Systemtabellen|sys.database_principal_aliases|Verwenden Sie anstelle von Aliasen Rollen.|  
|Transact-SQL|`RAISERROR` im Format `RAISERROR integer 'string'` wird eingestellt.|Schreiben Sie die Anweisung mithilfe der aktuellen **RAISERROR (...)** -Syntax um.|  
|Transact-SQL-Syntax|`COMPUTE / COMPUTE BY`|Verwenden Sie `ROLLUP`|  
|Transact-SQL-Syntax|Verwendung von **\*=** und **=&#42;**|Verwenden Sie die ANSI-Joinsyntax. Weitere Informationen finden Sie unter [from (Transact-SQL).](https://msdn.microsoft.com/library/ms177634\(SQL.105\).aspx)|  
|XEvents|databases_data_file_size_changed, databases_log_file_size_changed<br /><br /> eventdatabases_log_file_used_size_changed<br /><br /> locks_lock_timeouts_greater_than_0<br /><br /> locks_lock_timeouts|Ersetzt durch database_file_size_change event, database_file_size_change<br /><br /> database_file_size_change-Ereignis<br /><br /> lock_timeout_greater_than_0<br /><br /> lock_timeout|  
  
 **Zusätzliche XEvent-Änderungen**  
  
 **resource_monitor_ring_buffer_record**:  
  
-   Entfernte Felder: single_pages_kb, multiple_pages_kb  
  
-   Hinzugefügte Felder: target_kb, pages_kb  
  
 **memory_node_oom_ring_buffer_recorded**:  
  
-   Entfernte Felder: single_pages_kb, multiple_pages_kb  
  
-   Hinzugefügte Felder: target_kb, pages_kb  
  
## <a name="see-also"></a>Weitere Informationen  
 [Als veraltet markierte Funktionen der Datenbank-Engine in SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
