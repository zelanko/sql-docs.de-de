---
title: Datenbank für RevoScaleR-Tutorials
description: Tutorial zum Erstellen einer SQL Server-Datenbank für R-Tutorials.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 537bfb64562dfad9dbefbce70423892cd6e1e431
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727131"
---
# <a name="create-a-database-and-permissions-sql-server-and-revoscaler-tutorial"></a>Erstellen einer Datenbank und von Berechtigungen (Tutorial zu SQL Server und RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lerneinheit ist Teil des [RevoScaleR-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zum Verwenden von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Lektion 1 enthält Informationen zum Einrichten einer SQL Server-Datenbank und von Berechtigungen, die zur Durchführung dieses Tutorials erforderlich sind. Führen Sie mithilfe von [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) oder einem anderen Abfrage-Editor die folgenden Aufgaben aus:

> [!div class="checklist"]
> * Erstellen einer neuen Datenbank zum Speichern der Daten für das Training und die Bewertung von zwei R-Modellen
> * Erstellen einer Benutzeranmeldung für die Datenbank mit Berechtigungen zum Erstellen und Verwenden von Datenbankobjekten
  
## <a name="create-the-database"></a>Erstellen der Datenbank

Zur Durchführung dieses Tutorial ist eine Datenbank zum Speichern von Daten und Code erforderlich. Bitten Sie Ihren Datenbankadministrator (sofern Sie selbst keiner sind), die Datenbank und den Anmeldenamen für Sie zu erstellen. Sie benötigen Berechtigungen zum Schreiben und Lesen von Daten sowie zum Ausführen von R-Skripts.

1. Stellen Sie in SQL Server Management Studio eine Verbindung mit einer für R aktivierten Datenbankinstanz her.

2. Klicken Sie mit der rechten Maustaste auf **Datenbanken**, und klicken Sie dann auf **Neue Datenbank**.
  
2. Geben Sie einen Namen für die neue Datenbank ein: RevoDeepDive.
  

## <a name="create-a-login"></a>Erstellen eines Anmeldenamens
  
1. Klicken Sie auf **Neue Abfrage**, und legen Sie die Masterdatenbank als Datenbankkontext fest.
  
2. Führen Sie im Fenster **Abfrage** die folgenden Befehle aus, um die Benutzerkonten zu erstellen und sie der Datenbank zuzuweisen, die für dieses Tutorial verwendet wird. Achten Sie darauf, den Datenbanknamen falls nötig zu ändern.

3. Klicken Sie zur Überprüfung des Anmeldenamens auf die neue Datenbank, und erweitern Sie **Sicherheit** und **Benutzer**.
  
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

In diesem Tutorial werden R-Skript- und DDL-Vorgänge beschrieben, einschließlich dem Erstellen und Löschen von Tabellen und gespeicherten Prozeduren sowie dem Ausführen von R-Skripts in einem externen Prozess auf SQL Server. In diesem Schritt weisen Sie Berechtigungen zum Zulassen dieser Aufgaben zu.

In diesem Beispiel wird ein SQL-Anmeldename (DDUser01) verwendet. Wenn Sie jedoch einen Windows-Anmeldenamen erstellt haben, verwenden Sie stattdessen diesen.

```sql
USE RevoDeepDive
GO

EXEC sp_addrolemember 'db_owner', 'DDUser01'
GRANT EXECUTE ANY EXTERNAL SCRIPT TO DDUser01
GO
```

## <a name="troubleshoot-connections"></a>Behandeln von Verbindungsproblemen

Dieser Abschnitt enthält einige häufig auftretende Probleme, denen Sie möglicherweise während der Einrichtung der Datenbank gegenüber stehen.

- **Wie kann ich die Datenbankkonnektivität und SQL-Abfragen überprüfen?**
  
    Bevor Sie R-Code mithilfe des Servers ausführen, möchten Sie möglicherweise überprüfen, ob die Datenbank über Ihre R-Entwicklungsumgebung erreicht werden kann. Sowohl [Server-Explorer in Visual Studio](https://docs.microsoft.com/previous-versions/x603htbk(v=vs.140)) als auch [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) sind kostenlose Tools mit leistungsstarker Datenbankkonnektivität und Verwaltungsfunktionen.
  
    Wenn Sie zusätzliche Datenbankverwaltungstools installieren möchten, können Sie eine Testverbindung zur SQL Server-Instanz erstellen, indem Sie den [ODBC-Datenquellen-Administrator](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator?view=sql-server-2017) in der Systemsteuerung verwenden. Wenn die Datenbank ordnungsgemäß konfiguriert ist und Sie den richtigen Benutzernamen und das richtige Kennwort eingeben, sollten Sie die zuvor von Ihnen erstellte Datenbank sehen und diese als Ihre Standarddatenbank auswählen.
  
    Häufige Ursachen für Verbindungsfehler sind nicht für den Server aktivierte Remoteverbindungen und ein nicht aktiviertes Named Pipes-Protokoll. Weitere Tipps und Informationen zur Problembehandlung finden Sie im folgenden Artikel: [Beheben von Verbindungsfehlern mit der SQL Server-Datenbank-Engine](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Mein Tabellenname wurde mit dem Präfix DataReader versehen – warum?**
  
    Wenn Sie als Standardschema für diesen Benutzer **db_datareader** angeben, werden die Namen aller von diesem Benutzer erstellten Tabellen und neuen Objekte mit dem Präfix *schema* versehen. Ein Schema ist wie ein Ordner, den Sie einer Datenbank hinzufügen können, um Objekte zu organisieren. Das Schema definiert außerdem die Berechtigungen eines Benutzers in der Datenbank.
  
    Wenn das Schema mit einem bestimmten Benutzernamen verknüpft ist, wird dieser Benutzer zum _Schemabesitzer_. Wenn Sie ein Objekt erstellen, müssen Sie immer es immer in Ihrem eigenen Schema erstellen, außer Sie geben ausdrücklich an, dass es in einem anderen Schema erstellt werden soll.
  
    Wenn Sie z. B. eine Tabelle mit dem Namen **TestData** erstellen und Ihr Standardschema **db_datareader** ist, wird die Tabelle mit dem Namen `<database_name>.db_datareader.TestData` erstellt.
  
    Aus diesem Grund kann eine Datenbank mehrere Tabellen mit dem gleichen Namen enthalten, solange die Tabellen zu unterschiedlichen Schemas gehören.
   
    Wenn Sie eine Tabelle suchen und kein Schema angeben, sucht der Datenbankserver nach einem Schema, das Sie besitzen. Daher müssen Sie keinen Schemanamen angeben, wenn Sie auf Tabellen in einem Schema zugreifen, das mit Ihrem Login verknüpft sind.
  
- **Ich verfüge über keine DDL-Berechtigungen. Kann ich weiterhin das Tutorial ausführen?**
  
    Ja, aber Sie sollten jemanden bitten, die Daten vorab in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabellen zu laden, und mit der nächsten Lektion fortfahren. Funktionen, für die DDL-Berechtigungen erforderlich sind, werden im Tutorial nach Möglichkeit aufgerufen.

    Bitten Sie den Administrator zudem, Ihnen die Berechtigung EXECUTE ANY EXTERNAL SCRIPT zu erteilen. Diese Berechtigung benötigen Sie für die Ausführung von R-Skripts, ob als Remoteausführung oder mithilfe von `sp_execute_external_script`.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen von SQL Server-Datenobjekten mithilfe von RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)