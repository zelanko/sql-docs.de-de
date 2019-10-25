---
title: Ermitteln von Änderungen mit SqlDependency
description: Veranschaulicht, wie Sie erkennen können, wann sich die Abfrageergebnisse von den ursprünglich empfangenen unterscheiden.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 2d2c4c48a9085fa83d6104233be5f2e1c6b11318
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452248"
---
# <a name="detecting-changes-with-sqldependency"></a>Ermitteln von Änderungen mit SqlDependency

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Ein <xref:Microsoft.Data.SqlClient.SqlDependency>-Objekt kann einem <xref:Microsoft.Data.SqlClient.SqlCommand> zugeordnet werden, um zu erkennen, wann sich die Abfrageergebnisse von den ursprünglich abgerufenen unterscheiden. Sie können dem `OnChange`-Ereignis auch einen Delegaten zuweisen, der ausgelöst wird, wenn sich die Ergebnisse für einen zugeordneten Befehl ändern. Sie müssen den-<xref:Microsoft.Data.SqlClient.SqlDependency> dem Befehl zuordnen, bevor Sie den Befehl ausführen. Die `HasChanges`-Eigenschaft des <xref:Microsoft.Data.SqlClient.SqlDependency> kann auch verwendet werden, um zu bestimmen, ob sich die Abfrageergebnisse seit dem ersten Abrufen der Daten geändert haben.

## <a name="security-considerations"></a>Überlegungen zur Sicherheit

Die Abhängigkeits Infrastruktur basiert auf einer <xref:Microsoft.Data.SqlClient.SqlConnection>, die geöffnet wird, wenn <xref:Microsoft.Data.SqlClient.SqlDependency.Start%2A> aufgerufen wird, um Benachrichtigungen zu empfangen, dass sich die zugrunde liegenden Daten für einen bestimmten Befehl geändert haben. Die Fähigkeit eines Clients, den `SqlDependency.Start` aufrufen zu initiieren, wird durch die Verwendung der Attribute <xref:Microsoft.Data.SqlClient.SqlClientPermission> und Code Zugriffssicherheit gesteuert. Weitere Informationen finden Sie unter [Aktivieren von Abfrage Benachrichtigungen](enable-query-notifications.md).

### <a name="example"></a>Beispiel

Die folgenden Schritte veranschaulichen, wie Sie eine Abhängigkeit deklarieren, einen Befehl ausführen und eine Benachrichtigung erhalten, wenn sich das Resultset ändert:

1. Initiieren Sie eine `SqlDependency`-Verbindung mit dem Server.

2. Erstellen Sie <xref:Microsoft.Data.SqlClient.SqlConnection> und <xref:Microsoft.Data.SqlClient.SqlCommand> Objekte, um eine Verbindung mit dem Server herzustellen und eine Transact-SQL-Anweisung zu definieren.

3. Erstellen Sie ein neues `SqlDependency` Objekt, oder verwenden Sie ein vorhandenes Objekt, und binden Sie es an das `SqlCommand` Objekt. Intern wird dadurch ein <xref:Microsoft.Data.Sql.SqlNotificationRequest> Objekt erstellt und bei Bedarf an das Befehls Objekt gebunden. Diese Benachrichtigungs Anforderung enthält einen internen Bezeichner, der dieses `SqlDependency` Objekt eindeutig identifiziert. Außerdem wird der Clientlistener gestartet, wenn er noch nicht aktiv ist.

4. Abonnieren Sie einen Ereignishandler für das `OnChange`-Ereignis des `SqlDependency`-Objekts.

5. Führen Sie den Befehl mit einer der `Execute` Methoden des `SqlCommand`-Objekts aus. Da der Befehl an das Benachrichtigungsobjekt gebunden ist, erkennt der Server, dass er eine Benachrichtigung generieren muss, und die Warteschlangeninformation zeigt auf die Abhängigkeitenwarteschlange.

6. Stoppt die `SqlDependency` Verbindung mit dem Server.

Wenn ein Benutzer anschließend die zugrunde liegenden Daten ändert, erkennt Microsoft SQL Server, dass eine ausstehende Benachrichtigung für eine solche Änderung vorliegt, und sendet eine Benachrichtigung, die verarbeitet und an den Client weitergeleitet wird, indem er die zugrunde liegende `SqlConnection`, die von Aufrufen von `SqlDependency.Start`. Der Clientlistener empfängt die invalidierungsnachricht. Der Clientlistener löst dann das zugeordnete `SqlDependency` Objekt aus und löst das `OnChange`-Ereignis aus.

Das folgende Code Fragment zeigt das Entwurfsmuster, das Sie zum Erstellen einer Beispielanwendung verwenden würden.

```csharp
void Initialization()
{
    // Create a dependency connection.
    SqlDependency.Start(connectionString, queueName);
}

void SomeMethod()
{
    // Assume connection is an open SqlConnection.

    // Create a new SqlCommand object.
    using (SqlCommand command=new SqlCommand(
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",
        connection))
    {

        // Create a dependency and associate it with the SqlCommand.
        SqlDependency dependency=new SqlDependency(command);
        // Maintain the reference in a class member.

        // Subscribe to the SqlDependency event.
        dependency.OnChange+=new
           OnChangeEventHandler(OnDependencyChange);

        // Execute the command.
        using (SqlDataReader reader = command.ExecuteReader())
        {
            // Process the DataReader.
        }
    }
}

// Handler method
void OnDependencyChange(object sender,
   SqlNotificationEventArgs e )
{
  // Handle the event (for example, invalidate this cache entry).
}

void Termination()
{
    // Release the dependency.
    SqlDependency.Stop(connectionString, queueName);
}
```

## <a name="next-steps"></a>Nächste Schritte
- [Abfragebenachrichtigungen in SQL Server](query-notifications-sql-server.md)
