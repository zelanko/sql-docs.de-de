---
title: Ermitteln von Änderungen mit SqlDependency
description: Zeigt, wie Sie ermitteln, ob Abfrageergebnisse von den ursprünglich empfangenen Ergebnissen abweichen.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 391def8939cf730bbef9206764cfe8a5170088a1
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928850"
---
# <a name="detecting-changes-with-sqldependency"></a>Ermitteln von Änderungen mit SqlDependency

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Ein <xref:Microsoft.Data.SqlClient.SqlDependency>-Objekt kann einem <xref:Microsoft.Data.SqlClient.SqlCommand> zugeordnet werden, um zu erkennen, wenn die Abfrageergebnisse von den ursprünglich abgerufenen Ergebnissen abweichen. Darüber hinaus können Sie dem Ereignis `OnChange` einen Delegaten zuweisen, der ausgelöst wird, wenn sich die Ergebnisse für einen zugeordneten Befehl ändern. Sie müssen die <xref:Microsoft.Data.SqlClient.SqlDependency> dem Befehl zuordnen, bevor Sie den Befehl ausführen. Die Eigenschaft `HasChanges` der <xref:Microsoft.Data.SqlClient.SqlDependency> kann auch verwendet werden, um zu ermitteln, ob sich die Abfrageergebnisse seit dem ersten Abruf der Daten geändert haben.

## <a name="security-considerations"></a>Sicherheitshinweise

Für die Abhängigkeiteninfrastruktur ist eine <xref:Microsoft.Data.SqlClient.SqlConnection> erforderlich, die hergestellt wird, sobald <xref:Microsoft.Data.SqlClient.SqlDependency.Start%2A> aufgerufen wird, um Benachrichtigungen zu Änderungen an den zugrunde liegenden Daten für einen bestimmten Befehl zu empfangen. Die Fähigkeit eines Clients, den Aufruf an `SqlDependency.Start` zu initiieren, wird mithilfe von <xref:Microsoft.Data.SqlClient.SqlClientPermission> und Attributen für die Codezugriffssicherheit gesteuert. Weitere Informationen finden Sie unter [Aktivieren von Abfragebenachrichtigungen](enable-query-notifications.md).

### <a name="example"></a>Beispiel

Die folgenden Schritte veranschaulichen, wie Sie eine Abhängigkeit deklarieren, einen Befehl ausführen und eine Benachrichtigung erhalten, sobald sich das Resultset ändert:

1. Initiieren Sie eine `SqlDependency`-Verbindung mit dem Server.

2. Erstellen Sie <xref:Microsoft.Data.SqlClient.SqlConnection>- und <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekte für die Verbindung mit dem Server, und definieren Sie eine Transact-SQL-Anweisung.

3. Erstellen Sie ein neues `SqlDependency`-Objekt, oder verwenden Sie ein vorhandenes Objekt, und binden Sie es an das `SqlCommand`-Objekt. Intern wird dadurch ein <xref:Microsoft.Data.Sql.SqlNotificationRequest>-Objekt erstellt und bei Bedarf an das Befehlsobjekt gebunden. Diese Benachrichtigungsanforderung enthält einen internen Bezeichner, der dieses `SqlDependency`-Objekt eindeutig identifiziert. Außerdem wird der Clientlistener gestartet, sofern er noch nicht aktiv ist.

4. Abonnieren Sie einen Ereignishandler für das `OnChange`-Ereignis des `SqlDependency`-Objekts.

5. Führen Sie den Befehl mit einer der `Execute`-Methoden des `SqlCommand`-Objekts aus. Da der Befehl an das Benachrichtigungsobjekt gebunden ist, erkennt der Server, dass er eine Benachrichtigung generieren muss, und die Warteschlangeninformation zeigt auf die Abhängigkeitenwarteschlange.

6. Beenden Sie die `SqlDependency`-Verbindung mit dem Server.

Wenn ein Benutzer anschließend die zugrunde liegenden Daten ändert, erkennt Microsoft SQL Server, dass eine Benachrichtigung zu einer solchen Änderung aussteht. Er sendet eine Benachrichtigung, die verarbeitet und an den Client weitergeleitet wird. Diese Weiterleitung erfolgt über die zugrunde liegende `SqlConnection`, die durch den Aufruf von `SqlDependency.Start` erstellt wurde. Der Clientlistener empfängt die Invalidierungsnachricht. Anschließend ermittelt der Clientlistener das zugeordnete `SqlDependency`-Objekt und löst das `OnChange`-Ereignis aus.

Das folgende Codefragment zeigt das Entwurfsmuster, mit dem Sie eine Beispielanwendung erstellen würden.

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
