---
title: SqlCommand-Ausführung mit SqlNotificationRequest
description: In diesem Artikel wird das Konfigurieren eines SqlCommand-Objekts für dar Arbeiten mit einer Abfragebenachrichtigung veranschaulicht.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 5477b655554dceaa5f43b7d099e0fc156340f558
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75233814"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>SqlCommand-Ausführung mit SqlNotificationRequest

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Ein <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekt kann so konfiguriert werden, dass eine Benachrichtigung generiert wird, wenn Daten geändert werden, nachdem sie vom Server abgerufen wurden, und wenn sich das Resultset bei einer erneuten Ausführung der Abfrage unterscheidet. Dies ist hilfreich für Szenarios, in denen Sie benutzerdefinierte Benachrichtigungswarteschlangen auf dem Server verwenden möchten, oder wenn Sie Liveobjekte nicht verwalten möchten.

## <a name="creating-the-notification-request"></a>Erstellen der Benachrichtigungsanforderung

Sie können ein <xref:Microsoft.Data.Sql.SqlNotificationRequest>-Objekt verwenden, um die Benachrichtigungsanforderung durch Bindung an ein `SqlCommand`-Objekt zu erstellen. Sobald die Anforderung erstellt wurde, benötigen Sie das `SqlNotificationRequest`-Objekt nicht mehr. Sie können die Warteschlange nach Benachrichtigungen abfragen und entsprechend reagieren. Benachrichtigungen können angezeigt werden, auch wenn die Anwendung selbst heruntergefahren und dann neu gestartet wurde.

Wenn der Befehl mit der zugehörigen Benachrichtigung ausgeführt wird, lösen alle Änderungen im ursprünglichen Resultset das Senden einer Nachricht an die SQL Server-Warteschlange aus, die in der Benachrichtigungsanforderung konfiguriert wurde.

Wie Sie die SQL Server-Warteschlange abrufen können und die Meldung interpretieren müssen, hängt von Ihrer Anwendung ab. Die Anwendung ist dafür verantwortlich, die Warteschlange abzufragen und aufgrund der Meldung zu reagieren.

> [!NOTE]
> Wenn Sie SQL Server-Benachrichtigungsanforderungen mit <xref:Microsoft.Data.SqlClient.SqlDependency> verwenden, erstellen Sie einen eigenen Warteschlangennamen, anstatt den Standarddienstnamen zu verwenden.

Für <xref:Microsoft.Data.Sql.SqlNotificationRequest> gibt es keine neuen clientseitigen Sicherheitselemente. Es handelt sich primär um ein Serverfeature, und der Server hat spezielle Berechtigungen erstellt, die Benutzer haben müssen, um eine Benachrichtigung anzufordern.

### <a name="example"></a>Beispiel

Im folgenden Codefragment wird gezeigt, wie <xref:Microsoft.Data.Sql.SqlNotificationRequest> erstellt und mit <xref:Microsoft.Data.SqlClient.SqlCommand> verbunden wird.

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="next-steps"></a>Nächste Schritte
- [Abfragebenachrichtigungen in SQL Server](query-notifications-sql-server.md)
