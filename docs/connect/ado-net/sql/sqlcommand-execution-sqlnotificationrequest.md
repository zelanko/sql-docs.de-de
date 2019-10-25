---
title: SqlCommand-Ausführung mit SqlNotificationRequest
description: Veranschaulicht das Konfigurieren eines SqlCommand-Objekts für die Arbeit mit einer Abfrage Benachrichtigung.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 892f11e2d81e3a0733a1f0747c0b72c72ebc79fc
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451945"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>SqlCommand-Ausführung mit SqlNotificationRequest

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Eine <xref:Microsoft.Data.SqlClient.SqlCommand> kann so konfiguriert werden, dass eine Benachrichtigung generiert wird, wenn Daten geändert werden, nachdem Sie vom Server abgerufen wurden, und das Resultset anders wäre, wenn die Abfrage erneut ausgeführt würde. Dies ist nützlich für Szenarien, in denen Sie benutzerdefinierte Benachrichtigungs Warteschlangen auf dem Server verwenden möchten, oder wenn Sie keine Live Objekte verwalten möchten.

## <a name="creating-the-notification-request"></a>Erstellen der Benachrichtigungs Anforderung

Sie können ein <xref:Microsoft.Data.Sql.SqlNotificationRequest> Objekt verwenden, um die Benachrichtigungs Anforderung zu erstellen, indem Sie Sie an ein `SqlCommand` Objekt binden. Nachdem die Anforderung erstellt wurde, benötigen Sie das `SqlNotificationRequest`-Objekt nicht mehr. Sie können die Warteschlange nach Benachrichtigungen Abfragen und entsprechend reagieren. Benachrichtigungen können auch dann erfolgen, wenn die Anwendung heruntergefahren und anschließend neu gestartet wird.

Wenn der Befehl mit der zugehörigen Benachrichtigung ausgeführt wird, lösen alle Änderungen im ursprünglichen Resultset das Senden einer Nachricht an die SQL Server-Warteschlange aus, die in der Benachrichtigungsanforderung konfiguriert wurde.

Wie Sie die SQL Server-Warteschlange abrufen können und die Meldung interpretieren müssen, hängt von Ihrer Anwendung ab. Die Anwendung ist dafür verantwortlich, die Warteschlange abzufragen und aufgrund der Meldung zu reagieren.

> [!NOTE]
> Wenn Sie SQL Server Benachrichtigungs Anforderungen mit <xref:Microsoft.Data.SqlClient.SqlDependency> verwenden, erstellen Sie anstelle des Standard Dienst namens ihren eigenen Warteschlangen Namen.

Es sind keine neuen Client seitigen Sicherheitselemente für <xref:Microsoft.Data.Sql.SqlNotificationRequest> vorhanden. Dabei handelt es sich hauptsächlich um eine Server Funktion, und der Server hat spezielle Berechtigungen erstellt, die Benutzer benötigen, um eine Benachrichtigung anzufordern.

### <a name="example"></a>Beispiel

Im folgenden Code Fragment wird veranschaulicht, wie ein <xref:Microsoft.Data.Sql.SqlNotificationRequest> erstellt und einem <xref:Microsoft.Data.SqlClient.SqlCommand> zugeordnet wird.

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
