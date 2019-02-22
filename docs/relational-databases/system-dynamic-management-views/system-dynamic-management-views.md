---
title: Dynamische Verwaltungssichten (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database scoped dynamic management objects [SQL Server]
- dynamic management objects [SQL Server], about dynamic management objects
- server state information [SQL Server]
- dynamic management functions [SQL Server]
- metadata [SQL Server], dynamic management objects
- dynamic management views [SQL Server]
- DMVs [SQL Server]
- functions [SQL Server], dynamic management
- server scoped dynamic management objects [SQL Server]
- dynamic management objects [SQL Server]
ms.assetid: cf893ecb-0bf6-4cbf-ac00-8a1099e405b1
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1a61d3826cd7a4421eb621d549dfc49155ddadd0
ms.sourcegitcommit: b3d84abfa4e2922951430772c9f86dce450e4ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662744"
---
# <a name="system-dynamic-management-views"></a>Dynamische Systemverwaltungssichten
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Dynamische Verwaltungssichten (DMVs) und -funktionen geben Serverstatusinformationen zurück, mit denen der Zustand einer Serverinstanz überwacht, Probleme diagnostiziert und die Leistung optimiert werden kann.  
  
> [!IMPORTANT]  
>  Dynamische Verwaltungssichten und -funktionen geben interne, implementierungsspezifische Statusdaten zurück. Die Schemas und die zurückgegebenen Daten können in zukünftigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geändert werden. Deshalb kann es sein, dass dynamische Verwaltungssichten und -funktionen in zukünftigen Versionen nicht mit den dynamischen Verwaltungssichten und -funktionen in dieser Version kompatibel sind. In zukünftigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erweitert Microsoft möglicherweise die Definition der dynamischen Verwaltungssichten, indem am Ende der Spaltenliste z.B. Spalten hinzugefügt werden. Von der Verwendung der Syntax `SELECT * FROM dynamic_management_view_name` im Produktionscode wird abgeraten, da sich die Anzahl der zurückgegebenen Spalten möglicherweise ändert und Ihre Anwendung dadurch beschädigt werden kann.  
  
 Es gibt zwei Arten von dynamischen Verwaltungssichten und -funktionen:  
  
-   Dynamische Verwaltungssichten und -funktionen mit Serverbereich. Sie erfordern die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
-   Dynamische Verwaltungssichten und -funktionen mit Datenbankbereich. Sie erfordern die VIEW DATABASE STATE-Berechtigung für die Datenbank.  
  
## <a name="querying-dynamic-management-views"></a>Abfragen von dynamischen Verwaltungssichten  
 Auf dynamische Verwaltungssichten kann in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen mithilfe zweiteiliger, dreiteiliger oder vierteiliger Namen verwiesen werden. Auf dynamische Verwaltungsfunktionen kann andererseits in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen mithilfe zweiteiliger oder dreiteiliger Namen verwiesen werden. Auf dynamische Verwaltungssichten und -funktionen kann in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen nicht mithilfe einteiliger Namen verwiesen werden.  
  
 Alle dynamischen Verwaltungssichten und -funktionen sind im sys-Schema vorhanden und verwenden die Benennungskonvention dm_*. Wenn Sie eine dynamische Verwaltungssicht oder -funktion verwenden, müssen Sie vor dem Namen der Sicht oder Funktion das sys-Schema als Präfix einfügen. Führen Sie z. B. die folgende Abfrage aus, um die dynamische Verwaltungssicht dm_os_wait_stats abzufragen:  
  
 ```sql
SELECT wait_type, wait_time_ms  
FROM sys.dm_os_wait_stats;  
```  
  
### <a name="required-permissions"></a>Erforderliche Berechtigungen  
 Zum Abfragen einer dynamischen Verwaltungssicht oder -funktion sind die SELECT-Berechtigung für das Objekt und die VIEW SERVER STATE- oder VIEW DATABASE STATE-Berechtigung erforderlich. Auf diese Weise können Sie den Zugriff eines Benutzers oder eines Anmeldenamens selektiv auf dynamische Verwaltungssichten und -funktionen einschränken. Dazu erstellen Sie zunächst den Benutzer in master und verweigern dem Benutzer dann die SELECT-Berechtigung für die dynamischen Verwaltungssichten oder -funktionen, auf die er keinen Zugriff haben soll. Der Benutzer kann dann diese dynamischen Verwaltungssichten oder -funktionen unabhängig vom Datenbankkontext des Benutzers nicht auswählen.  
  
> [!NOTE]  
>  DENY hat Vorrang. Daher kann ein Benutzer, dem die VIEW SERVER STATE-Berechtigung erteilt, aber die VIEW DATABASE STATE-Berechtigung verweigert wurde, zwar Informationen auf Serverebene, aber keine Informationen auf Datenbankebene anzeigen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Dynamische Verwaltungssichten und -funktionen wurden in die folgenden Kategorien unterteilt.  
  
|||  
|-|-|  
|[Always On-Verfügbarkeitsgruppen dynamische Verwaltungssichten und-Funktionen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)|[Eine Speicheroptimierte Tabelle dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)|  
|[Dynamische Verwaltungssichten in Bezug auf Change Data Capture &#40;Transact-SQL&#41;](change-data-capture-sys-dm-cdc-errors.md)|[Objektbezogene dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[Dynamische Verwaltungssichten in Verbindung mit der änderungsnachverfolgung](change-tracking-sys-dm-tran-commit-table.md)|[Abfragen von Abfragebenachrichtigungen verbundene dynamische Verwaltungssichten &#40;Transact-SQL&#41;](query-notifications-sys-dm-qn-subscriptions.md)|  
|[Dynamische Verwaltungssichten in Verbindung mit Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)|[Replikation verbundene dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)|  
|[Objektbezogene dynamische Verwaltungssichten für die datenbankspiegelung &#40;Transact-SQL&#41;](database-mirroring-sys-dm-db-mirroring-auto-page-repair.md)|[Dynamische Verwaltungssichten in Verbindung mit der Ressourcenkontrolle &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)|  
|[Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)|[Sicherheitsbezogene dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[Execution Related Dynamic Management Views and Functions &#40;Transact-SQL&#41; (Dynamische Verwaltungssichten und Funktionen im Zusammenhang mit der Ausführung (Transact-SQL))](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)|[Serverbezogene dynamische Verwaltungssichten und -funktionen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[Dynamische Verwaltungssichten für erweiterte Ereignisse](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)|[Dynamische Verwaltungssichten in Verbindung mit Service Broker &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)|  
|[FileStream und FileTable dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)|[Räumliche Daten beziehen, dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/c542ac38-451f-43a5-bf8c-4edd38bb738e)|  
|[Volltextsuche und semantische Suche, dynamische Verwaltungssichten und Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)|[SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)|  
|[Geografische Replikation, dynamische Verwaltungssichten und-Funktionen &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)|[Dynamische Verwaltungssichten in Verbindung mit SQL Server-Betriebssystem &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)|  
|[Objektbezogene dynamische Verwaltungssichten und-Funktionen Index &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)|[Dynamische Verwaltungssichten für Stretch Database &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/1193efce-a105-49a9-a8b8-26b063485567)|  
|[E/A im Zusammenhang, dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)|[Dynamische Verwaltungssichten und Funktionen in Verbindung mit Transaktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)|  

  
## <a name="see-also"></a>Siehe auch  
 [GRANT – Serverberechtigungen &#40;Transact-SQL&#41;](../../t-sql/statements/grant-server-permissions-transact-sql.md)   
 [GRANT (Datenbankberechtigungen) &#40;&#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)   
 [Systemsichten &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
