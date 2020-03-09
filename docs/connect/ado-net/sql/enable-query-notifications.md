---
title: Aktivieren von Abfragebenachrichtigungen
description: Erläutert die Verwendung von Abfragebenachrichtigungen, einschließlich der Anforderungen zu deren Aktivierung und Nutzung.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e587639f5323ea76c975e3a8c35d647a7eb3d891
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896971"
---
# <a name="enabling-query-notifications"></a>Aktivieren von Abfragebenachrichtigungen

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Anwendungen, die Abfragebenachrichtigungen nutzen, weisen eine Reihe gemeinsamer Anforderungen auf. Ihre Datenquelle muss richtig konfiguriert sein, um SQL-Abfragebenachrichtigungen zu unterstützen, und die Benutzer müssen über die richtigen client- und serverseitigen Berechtigungen verfügen.  
  
Voraussetzungen für Abfragebenachrichtigungen:  
  
- Aktivieren Sie Abfragebenachrichtigungen für Ihre Datenbank.  
  
- Stellen Sie sicher, dass die Benutzer-ID für das Herstellen der Verbindung mit der Datenbank über die erforderlichen Berechtigungen verfügt.  
  
- Verwenden Sie ein <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekt, um eine gültige SELECT-Anweisung mit einem zugehörigen Benachrichtigungsobjekt (entweder <xref:Microsoft.Data.SqlClient.SqlDependency> oder <xref:Microsoft.Data.Sql.SqlNotificationRequest>) auszuführen.  
  
- Geben Sie den Code zur Verarbeitung der Benachrichtigung an, wenn sich die überwachten Daten ändern.  
  
## <a name="query-notifications-requirements"></a>Anforderungen für Abfragebenachrichtigungen  
Abfragebenachrichtigungen werden nur für SELECT-Anweisungen unterstützt, die eine Liste bestimmter Anforderungen erfüllen. Die folgende Tabelle enthält Links zur Dokumentation zu Service Broker und Abfragebenachrichtigungen in der SQL Server-Onlinedokumentation.  
  
**SQL Server-Dokumentation**  
  
- [Erstellen einer Abfrage für die Benachrichtigung](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Sicherheitsaspekte für Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [Sicherheit und Schutz (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Sicherheitsaspekte für Notification Services](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [Berechtigungen für Abfragebenachrichtigungen](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Internationale Gesichtspunkte bei Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [Überlegungen zu Lösungsentwürfen (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Entwicklerhandbuch (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Aktivieren von Abfragebenachrichtigungen zum Ausführen von Beispielcode  
Führen Sie zum Aktivieren von Service Broker in der **AdventureWorks**-Datenbank mit SQL Server Management Studio die folgende Transact-SQL-Anweisung aus:  
  
`ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
Damit die Beispiele von Abfragebenachrichtigungen ordnungsgemäß ausgeführt werden können, müssen auf dem Datenbankserver die folgenden Transact-SQL-Anweisungen ausgeführt werden.  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Berechtigungen für Abfragebenachrichtigungen  
Benutzer, die Befehle ausführen, für die eine Benachrichtigung gewünscht wird, müssen auf dem Server die Datenbankberechtigung SUBSCRIBE QUERY NOTIFICATIONS haben.  
  
Clientseitiger Code, der in einer teilweise vertrauenswürdigen Situation ausgeführt wird, erfordert <xref:Microsoft.Data.SqlClient.SqlClientPermission>.  
  
Der folgende Code erstellt ein <xref:Microsoft.Data.SqlClient.SqlClientPermission>-Objekt, wobei <xref:System.Security.Permissions.PermissionState> auf <xref:System.Security.Permissions.PermissionState.Unrestricted> festgelegt wird. <xref:System.Security.CodeAccessPermission.Demand%2A> erzwingt zur Laufzeit <xref:System.Security.SecurityException>, wenn allen Aufrufern, die höher im Aufrufstapel stehen, die Berechtigung nicht erteilt wurde.  
  
[!code-csharp[DataWorks SqlClientPermission_Demand#1](~/../sqlclient/doc/samples/SqlClientPermission_Demand.cs#1)]
  
## <a name="choosing-a-notification-object"></a>Wählen eines Benachrichtigungsobjekts  
Die Abfragebenachrichtigungs-API stellt zwei Objekte zum Verarbeiten von Benachrichtigungen zur Verfügung: <xref:Microsoft.Data.SqlClient.SqlDependency> und <xref:Microsoft.Data.Sql.SqlNotificationRequest>.
  
### <a name="using-sqldependency"></a>Verwenden von SqlDependency  
Zum Verwenden der <xref:Microsoft.Data.SqlClient.SqlDependency> muss Service Broker für die verwendete SQL Server-Datenbank aktiviert werden, und Benutzer müssen über Berechtigungen zum Erhalt von Benachrichtigungen verfügen. Service Broker-Objekte, wie z. B. die Benachrichtigungswarteschlange, sind vordefiniert.  
  
Zusätzlich startet <xref:Microsoft.Data.SqlClient.SqlDependency> automatisch einen Arbeitsthread, um Benachrichtigungen in der Reihenfolge zu verarbeiten, in der sie in die Warteschlange gestellt werden. Außerdem wird die Service Broker-Meldung analysiert, und die Informationen werden als Ereignisargumentdaten verfügbar gemacht. <xref:Microsoft.Data.SqlClient.SqlDependency> muss durch Aufrufen der `Start`-Methode initialisiert werden, um eine Abhängigkeit zur Datenbank einzurichten. Dies ist eine statische Methode, die nur einmal während der Anwendungsinitialisierung für jede erforderliche Datenbankverbindung aufgerufen werden muss. Die `Stop`-Methode muss beim Beenden der Anwendung für jede Abhängigkeitsverbindung, die hergestellt wurde, aufgerufen werden.  
  
### <a name="using-sqlnotificationrequest"></a>Verwenden von SqlNotificationRequest  
Im Gegensatz dazu erfordert <xref:Microsoft.Data.Sql.SqlNotificationRequest>, dass Sie die gesamte Lauschinfrastruktur selbst implementieren. Darüber hinaus müssen alle unterstützenden Service Broker-Objekte wie Warteschlange, Dienst und von der Warteschlange unterstützte Nachrichtentypen definiert werden. Dieser manuelle Ansatz ist nützlich, wenn Ihre Anwendung spezielle Benachrichtigungsmeldungen oder -verhalten erfordert, oder wenn Ihre Anwendung Teil einer größeren Service Broker-Anwendung ist.  
  
## <a name="next-steps"></a>Nächste Schritte
- [Abfragebenachrichtigungen in SQL Server](query-notifications-sql-server.md)
