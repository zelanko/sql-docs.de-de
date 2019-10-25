---
title: Aktivieren von Abfragebenachrichtigungen
description: Erläutert die Verwendung von Abfrage Benachrichtigungen, einschließlich der Anforderungen für die Aktivierung und Verwendung von.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 94b472a1fe040aa3a684d9f7b523ba09c82a651e
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452231"
---
# <a name="enabling-query-notifications"></a>Aktivieren von Abfragebenachrichtigungen

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Anwendungen, die Abfrage Benachrichtigungen nutzen, haben einen allgemeinen Satz an Anforderungen. Ihre Datenquelle muss richtig konfiguriert sein, um SQL-Abfragebenachrichtigungen zu unterstützen, und die Benutzer müssen über die richtigen client- und serverseitigen Berechtigungen verfügen.  
  
Zum Verwenden von Abfrage Benachrichtigungen müssen Sie folgende Schritte ausführen:  
  
- Aktivieren Sie Abfrage Benachrichtigungen für Ihre Datenbank.  
  
- Stellen Sie sicher, dass die Benutzer-ID für die Verbindung mit der Datenbank über die erforderlichen Berechtigungen verfügt.  
  
- Verwenden Sie ein <xref:Microsoft.Data.SqlClient.SqlCommand> Objekt, um eine gültige SELECT-Anweisung mit einem zugeordneten Benachrichtigungs Objekt auszuführen – entweder <xref:Microsoft.Data.SqlClient.SqlDependency> oder <xref:Microsoft.Data.Sql.SqlNotificationRequest>.  
  
- Stellen Sie Code bereit, um die Benachrichtigung zu verarbeiten, wenn sich die überwachten Daten ändern.  
  
## <a name="query-notifications-requirements"></a>Anforderungen für Abfrage Benachrichtigungen  
Abfrage Benachrichtigungen werden nur für SELECT-Anweisungen unterstützt, die eine Liste spezifischer Anforderungen erfüllen. In der folgenden Tabelle finden Sie Links zu den Service Broker-und Abfrage Benachrichtigungs Dokumentation in SQL Server-Onlinedokumentation.  
  
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
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Aktivieren von Abfrage Benachrichtigungen zum Ausführen von Beispielcode  
Führen Sie zum Aktivieren von Service Broker in der **AdventureWorks**-Datenbank mit SQL Server Management Studio die folgende Transact-SQL-Anweisung aus:  
  
`ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
Damit die Abfrage Benachrichtigungs Beispiele ordnungsgemäß ausgeführt werden, müssen die folgenden Transact-SQL-Anweisungen auf dem Datenbankserver ausgeführt werden.  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Berechtigungen für Abfrage Benachrichtigungen  
Benutzer, die Befehle ausführen, die eine Benachrichtigung anfordern, müssen über die Daten Bank Berechtigung abonnieren-Abfrage Benachrichtigungen auf dem Server  
  
Client seitiger Code, der in einer teilweise vertrauenswürdigen Situation ausgeführt wird, erfordert die <xref:Microsoft.Data.SqlClient.SqlClientPermission>.  
  
Der folgende Code erstellt ein <xref:Microsoft.Data.SqlClient.SqlClientPermission>-Objekt, wobei die <xref:System.Security.Permissions.PermissionState> auf <xref:System.Security.Permissions.PermissionState.Unrestricted> festgelegt wird. Der <xref:System.Security.CodeAccessPermission.Demand%2A> erzwingt zur Laufzeit eine <xref:System.Security.SecurityException>, wenn allen Aufrufern in der Aufruf Listen-Berechtigung die Berechtigung nicht erteilt wurde.  
  
[!code-csharp[DataWorks SqlClientPermission_Demand#1](~/../sqlclient/doc/samples/SqlClientPermission_Demand.cs#1)]
  
## <a name="choosing-a-notification-object"></a>Auswählen eines Benachrichtigungs Objekts  
Die Abfragebenachrichtigungs-API stellt zwei Objekte zum Verarbeiten von Benachrichtigungen zur Verfügung: <xref:Microsoft.Data.SqlClient.SqlDependency> und <xref:Microsoft.Data.Sql.SqlNotificationRequest>.
  
### <a name="using-sqldependency"></a>Verwenden von sqlabhängigkeit  
Zum Verwenden der <xref:Microsoft.Data.SqlClient.SqlDependency> muss Service Broker für die verwendete SQL Server-Datenbank aktiviert werden, und Benutzer müssen über Berechtigungen zum Erhalt von Benachrichtigungen verfügen. Service Broker Objekte, z. b. die Benachrichtigungs Warteschlange, sind vordefiniert.  
  
Außerdem wird von <xref:Microsoft.Data.SqlClient.SqlDependency> automatisch ein Arbeits Thread gestartet, um Benachrichtigungen zu verarbeiten, die in der Warteschlange veröffentlicht werden. Außerdem wird die Service Broker Nachricht analysiert und die Informationen als Ereignis Argument Daten verfügbar gemacht. <xref:Microsoft.Data.SqlClient.SqlDependency> müssen initialisiert werden, indem Sie die `Start`-Methode aufrufen, um eine Abhängigkeit zur Datenbank herzustellen. Dies ist eine statische Methode, die nur einmal während der Anwendungs Initialisierung für jede erforderliche Datenbankverbindung aufgerufen werden muss. Die `Stop`-Methode sollte bei der Beendigung der Anwendung für jede vorgenommene Abhängigkeits Verbindung aufgerufen werden.  
  
### <a name="using-sqlnotificationrequest"></a>Verwenden von SqlNotificationRequest  
Im Gegensatz dazu müssen <xref:Microsoft.Data.Sql.SqlNotificationRequest> die gesamte Abhör Infrastruktur selbst implementieren. Außerdem müssen alle unterstützenden Service Broker Objekte (z. b. die Warteschlange, der Dienst und die Nachrichten Typen, die von der Warteschlange unterstützt werden) definiert werden. Diese manuelle Vorgehensweise ist hilfreich, wenn Ihre Anwendung spezielle Benachrichtigungs-oder Benachrichtigungs Verhalten erfordert oder wenn Ihre Anwendung Teil einer größeren Service Broker Anwendung ist.  
  
## <a name="next-steps"></a>Nächste Schritte
- [Abfragebenachrichtigungen in SQL Server](query-notifications-sql-server.md)
