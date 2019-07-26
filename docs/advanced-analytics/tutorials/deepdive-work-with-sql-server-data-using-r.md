---
title: Erstellen einer Datenbank und von Berechtigungen für revoscaler-Tutorials
description: 'Tutorial: Exemplarische Vorgehensweise zum Erstellen einer SQL Server-Datenbank für R-Tutorials.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: f8ed06135c7e97d0ba66a36615e7379e41c65e8b
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469688"
---
# <a name="create-a-database-and-permissions-sql-server-and-revoscaler-tutorial"></a>Erstellen einer Datenbank und von Berechtigungen (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Lektion 1 bezieht sich auf das Einrichten einer SQL Server Datenbank und der erforderlichen Berechtigungen zum Abschließen dieses Tutorials. Verwenden Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) oder einen anderen Abfrage-Editor, um die folgenden Aufgaben auszuführen:

> [!div class="checklist"]
> * Erstellen Sie eine neue Datenbank zum Speichern der Daten für das Training und die Bewertung von zwei R-Modellen.
> * Erstellen einer Datenbank-Benutzeranmeldung mit Berechtigungen zum Erstellen und Verwenden von Datenbankobjekten
  
## <a name="create-the-database"></a>Erstellen der Datenbank

Für dieses Tutorial ist eine Datenbank zum Speichern von Daten und Code erforderlich. Wenn Sie kein Administrator sind, bitten Sie den Datenbankadministrator, die Datenbank und den Anmelde Namen für Sie zu erstellen. Sie benötigen Berechtigungen zum Schreiben und Lesen von Daten sowie zum Ausführen von R-Skripts.

1. Stellen Sie in SQL Server Management Studio eine Verbindung mit einer R-fähigen Daten Bank Instanz her.

2. Klicken Sie mit der rechten Maustaste auf **Datenbanken**, und wählen Sie **neue Datenbank**
  
2. Geben Sie einen Namen für die neue Datenbank ein: Revodeepdive.
  

## <a name="create-a-login"></a>Erstellen eines Anmeldenamens
  
1. Klicken Sie auf **Neue Abfrage**, und legen Sie die Masterdatenbank als Datenbankkontext fest.
  
2. Führen Sie im Fenster **Abfrage** die folgenden Befehle aus, um die Benutzerkonten zu erstellen und sie der Datenbank zuzuweisen, die für dieses Tutorial verwendet wird. Achten Sie darauf, den Datenbanknamen falls nötig zu ändern.

3. Um den Anmelde Namen zu überprüfen, wählen Sie die neue Datenbank aus, erweitern Sie **Sicherheit**, und erweitern Sie **Benutzer**.
  
**Windows-Benutzer**
  
```sql
 -- Create server user based on Windows account
USE master
GO
CREATE LOGIN [<DOMAIN>\<user_name>] FROM WINDOWS WITH DEFAULT_DATABASE=[RevoDeepDive]

 --Add the new user to tutorial database
USE [RevoDeepDive]
GO
CREATE USER [<user_name>] FOR LOGIN [<DOMAIN>\<user_name>] WITH DEFAULT_SCHEMA=[db_datareader]
```

**SQL-Anmeldename**

```sql
-- Create new SQL login
USE master
GO
CREATE LOGIN [DDUser01] WITH PASSWORD='<type password here>', CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;

-- Add the new SQL login to tutorial database
USE RevoDeepDive
GO
CREATE USER [DDUser01] FOR LOGIN [DDUser01] WITH DEFAULT_SCHEMA=[db_datareader]
```

## <a name="assign-permissions"></a>Zuweisen von Berechtigungen

In diesem Tutorial werden r-Skript-und DDL-Vorgänge veranschaulicht, einschließlich Erstellen und Löschen von Tabellen und gespeicherten Prozeduren und Ausführen von r-Skripts in einem externen Prozess auf SQL Server. Weisen Sie in diesem Schritt permzingen zu, um diese Aufgaben zuzulassen.

In diesem Beispiel wird eine SQL-Anmeldung (DDUser01) angenommen, aber wenn Sie einen Windows-Anmelde Namen erstellt haben, verwenden Sie diesen.

```sql
USE RevoDeepDive
GO

EXEC sp_addrolemember 'db_owner', 'DDUser01'
GRANT EXECUTE ANY EXTERNAL SCRIPT TO DDUser01
GO
```

## <a name="troubleshoot-connections"></a>Problembehandlung bei Verbindungen

Dieser Abschnitt enthält einige häufig auftretende Probleme, denen Sie möglicherweise während der Einrichtung der Datenbank gegenüber stehen.

- **Wie kann ich die Datenbankkonnektivität und SQL-Abfragen überprüfen?**
  
    Bevor Sie R-Code mithilfe des Servers ausführen, möchten Sie möglicherweise überprüfen, ob die Datenbank über Ihre R-Entwicklungsumgebung erreicht werden kann. Sowohl [Server-Explorer in Visual Studio](https://docs.microsoft.com/previous-versions/x603htbk(v=vs.140)) als auch [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) sind kostenlose Tools mit leistungsstarker Datenbankkonnektivität und Verwaltungsfunktionen.
  
    Wenn Sie zusätzliche Datenbankverwaltungstools installieren möchten, können Sie eine Testverbindung zur SQL Server-Instanz erstellen, indem Sie den [ODBC-Datenquellen-Administrator](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator?view=sql-server-2017) in der Systemsteuerung verwenden. Wenn die Datenbank ordnungsgemäß konfiguriert ist und Sie den richtigen Benutzernamen und das richtige Kennwort eingeben, sollten Sie die zuvor von Ihnen erstellte Datenbank sehen und diese als Ihre Standarddatenbank auswählen.
  
    Häufige Ursachen für Verbindungsfehler: Remote Verbindungen sind für den Server nicht aktiviert, und das Named Pipes-Protokoll ist nicht aktiviert. Weitere Tipps zur Problembehandlung finden Sie in diesem Artikel: Problembehandlung [beim Herstellen einer Verbindung mit dem SQL Server Datenbank-Engine](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Mein Tabellenname wurde mit dem Präfix DataReader versehen – warum?**
  
    Wenn Sie das Standardschema für diesen Benutzer als **db_datareader**angeben, wird allen Tabellen und anderen neuen, von diesem Benutzer erstellten Objekten der *Schema* Name vorangestellt. Ein Schema ist wie ein Ordner, den Sie einer Datenbank hinzufügen können, um Objekte zu organisieren. Das Schema definiert außerdem die Berechtigungen eines Benutzers in der Datenbank.
  
    Wenn das Schema einem bestimmten Benutzernamen zugeordnet ist, ist der Benutzer der _Schema Besitzer_. Wenn Sie ein Objekt erstellen, müssen Sie immer es immer in Ihrem eigenen Schema erstellen, außer Sie geben ausdrücklich an, dass es in einem anderen Schema erstellt werden soll.
  
    Wenn Sie z. b. eine Tabelle mit dem Namen **testdata**erstellen und das Standardschema **db_datareader**ist, wird die Tabelle mit dem Namen `<database_name>.db_datareader.TestData`erstellt.
  
    Aus diesem Grund kann eine Datenbank mehrere Tabellen mit dem gleichen Namen enthalten, solange die Tabellen zu unterschiedlichen Schemas gehören.
   
    Wenn Sie nach einer Tabelle suchen und kein Schema angeben, sucht der Datenbankserver nach einem Schema, das Sie besitzen. Daher müssen Sie keinen Schemanamen angeben, wenn Sie auf Tabellen in einem Schema zugreifen, das mit Ihrem Login verknüpft sind.
  
- **Ich verfüge über keine DDL-Berechtigungen. Kann ich weiterhin das Tutorial ausführen?**
  
    Ja, aber Sie sollten jemanden bitten, die Daten vorab in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen zu laden und mit der nächsten Lektion fortzufahren. Wenn möglich, werden die Funktionen, die DDL-Berechtigungen erfordern, im Lernprogramm genannt.

    Bitten Sie den Administrator außerdem, Ihnen die Berechtigung zu erteilen, ein externes Skript auszuführen. Sie wird für die Ausführung von R-Skripts benötigt, egal `sp_execute_external_script`ob Remote oder mithilfe von.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen von SQL Server-Datenobjekten mithilfe von RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)