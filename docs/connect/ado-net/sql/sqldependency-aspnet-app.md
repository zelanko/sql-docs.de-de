---
title: SqlDependency in einer ASP.NET-Anwendung
description: Veranschaulicht die Verwendung von Abfrage Benachrichtigungen aus einer ASP.NET-Anwendung.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 2115d087d837118b99ee3ffded9cae0003b6d4e0
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451965"
---
# <a name="sqldependency-in-an-aspnet-application"></a>SqlDependency in einer ASP.NET-Anwendung

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Im Beispiel in diesem Abschnitt wird gezeigt, wie <xref:Microsoft.Data.SqlClient.SqlDependency> indirekt mithilfe des ASP.net <xref:System.Web.Caching.SqlCacheDependency>-Objekts verwendet wird. Das <xref:System.Web.Caching.SqlCacheDependency>-Objekt verwendet eine <xref:Microsoft.Data.SqlClient.SqlDependency>, um Benachrichtigungen zu überwachen und den Cache ordnungsgemäß zu aktualisieren.  
  
> [!NOTE]
>  Im Beispielcode wird davon ausgegangen, dass Sie Abfrage Benachrichtigungen aktiviert haben, indem Sie die Skripts unter [Aktivieren von Abfrage Benachrichtigungen](enable-query-notifications.md)ausführen.  
  
## <a name="about-the-sample-application"></a>Informationen zur Beispielanwendung  
In der Beispielanwendung wird eine einzelne ASP.NET-Webseite verwendet, um Produktinformationen aus der SQL Server-**AdventureWorks**-Datenbank in einem <xref:System.Web.UI.WebControls.GridView>-Steuerelement anzuzeigen. Wenn die Seite geladen wird, schreibt der Code die aktuelle Uhrzeit in ein <xref:System.Web.UI.WebControls.Label>-Steuerelement. Anschließend wird ein <xref:System.Web.Caching.SqlCacheDependency> Objekt definiert und Eigenschaften für das <xref:System.Web.Caching.Cache> Objekt festgelegt, um die Cache Daten bis zu drei Minuten zu speichern. Der Code stellt dann eine Verbindung mit der Datenbank her und ruft die Daten ab. Wenn die Seite geladen wird und die Anwendung ausgeführt wird, ruft ASP.NET Daten aus dem Cache ab. Diese können Sie überprüfen, indem Sie feststellen, dass sich die Zeit auf der Seite nicht ändert. Wenn sich die überwachten Daten ändern, erklärt ASP.NET den Cache für ungültig und füllt das `GridView`-Steuerelement mit neuen Daten erneut auf. dabei wird die im Steuerelement `Label` angezeigte Zeit aktualisiert.  
  
## <a name="creating-the-sample-application"></a>Erstellen der Beispielanwendung  
Führen Sie die folgenden Schritte aus, um die Beispielanwendung zu erstellen und auszuführen:  
  
1. Erstellen Sie eine neue ASP.NET-Website.  
  
2. Fügen Sie der Seite "default. aspx" ein <xref:System.Web.UI.WebControls.Label> und ein <xref:System.Web.UI.WebControls.GridView>-Steuerelement hinzu.  
  
3. Öffnen Sie das Klassenmodul der Seite, und fügen Sie die folgenden Anweisungen hinzu:  
  
    ```csharp  
    using Microsoft.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. Fügen Sie den folgenden Code in das `Page_Load`-Ereignis der Seite ein:  
  
    [!code-csharp[DataWorks SqlDependency_Start#1](~/../sqlclient/doc/samples/SqlDependency_Start.cs#1)]
  
5. Fügen Sie zwei Hilfsmethoden hinzu, `GetConnectionString` und `GetSQL`. Die definierte Verbindungszeichenfolge verwendet die integrierte Sicherheit. Sie müssen sicherstellen, dass das verwendete Konto über die erforderlichen Datenbankberechtigungen verfügt und dass für die Beispieldatenbank **AdventureWorks** Benachrichtigungen aktiviert sind.
  
    [!code-csharp[DataWorks SqlDependency_Start#2](~/../sqlclient/doc/samples/SqlDependency_Start.cs#2)]
  
### <a name="testing-the-application"></a>Testen der Anwendung  
Die Anwendung speichert die Daten, die im Webformular angezeigt werden, und aktualisiert Sie alle drei Minuten, wenn keine Aktivitäten vorhanden sind. Wenn eine Änderung an der Datenbank vorgenommen wird, wird der Cache sofort aktualisiert. Führen Sie die Anwendung von Visual Studio aus, wodurch die Seite in den Browser geladen wird. Die angezeigte Cache Aktualisierungszeit gibt an, wann der Cache zuletzt aktualisiert wurde. Warten Sie drei Minuten, und aktualisieren Sie dann die Seite, wodurch ein Post Back Ereignis auftritt. Beachten Sie, dass sich die auf der Seite angezeigte Zeit geändert hat. Wenn Sie die Seite in weniger als drei Minuten aktualisieren, bleibt die auf der Seite angezeigte Uhrzeit unverändert.  
  
Aktualisieren Sie nun die Daten in der Datenbank mithilfe eines Transact-SQL-Befehls, und aktualisieren Sie die Seite. Die angezeigte Zeit zeigt nun an, dass der Cache mit den neuen Daten aus der Datenbank aktualisiert wurde. Beachten Sie Folgendes: Obwohl der Cache aktualisiert wird, ändert sich die auf der Seite angezeigte Zeit erst, wenn ein Post Back Ereignis auftritt.  
  
## <a name="next-steps"></a>Nächste Schritte
- [Abfragebenachrichtigungen in SQL Server](query-notifications-sql-server.md)
