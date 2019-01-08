---
title: 'Erstellen Sie eine Datenbank und Berechtigungen für RevoScaleR-Tutorials: SQL Server-Machine Learning'
description: Exemplarische Vorgehensweise im Lernprogramm zum Erstellen von SQL Server-Datenbank für die R-Tutorials...
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 15032b604d7ea28ad03acb837f997dac3afa84b8
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645269"
---
# <a name="create-a-database-and-permissions-sql-server-and-revoscaler-tutorial"></a>Erstellen Sie eine Datenbank und Berechtigungen (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Lektion eine ist über das Einrichten von SQL Server-Datenbank und Berechtigungen für das Abschließen dieses Lernprogramms erforderlich sind. Verwendung [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) oder eine andere Abfrage-Editor die folgenden Aufgaben ausführen:

> [!div class="checklist"]
> * Erstellen einer neuen Datenbank zum Speichern der Daten für Trainings- und Bewertungsschritte für zwei R-Modellen
> * Erstellen Sie eine datenbankanmeldung für Benutzer mit Berechtigungen zum Erstellen und Verwenden von Datenbankobjekten
  
## <a name="create-the-database"></a>Erstellen der Datenbank

Dieses Lernprogramm erfordert eine Datenbank zum Speichern von Daten und Code. Wenn Sie kein Administrator sind, bitten Sie Ihr Datenbankadministrator die Datenbank und die Anmeldung für Sie erstellt. Sie benötigen Berechtigungen zum Schreiben und Lesen von Daten sowie zum Ausführen von R-Skripts.

1. In SQL Server Management Studio eine Verbindung mit einer R-aktivierten Datenbank-Instanz.

2. Mit der rechten Maustaste **Datenbanken**, und wählen Sie **neue Datenbank**.
  
2. Geben Sie einen Namen für die neue Datenbank ein: RevoDeepDive.
  

## <a name="create-a-login"></a>Erstellen eines Anmeldenamens
  
1. Klicken Sie auf **Neue Abfrage**, und legen Sie die Masterdatenbank als Datenbankkontext fest.
  
2. Führen Sie im Fenster **Abfrage** die folgenden Befehle aus, um die Benutzerkonten zu erstellen und sie der Datenbank zuzuweisen, die für dieses Tutorial verwendet wird. Achten Sie darauf, den Datenbanknamen falls nötig zu ändern.

3. Um die Anmeldung zu überprüfen, wählen Sie die neue Datenbank aus, erweitern Sie **Sicherheit**, und erweitern Sie **Benutzer**.
  
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

Dieses Tutorial veranschaulicht das R-Skript und DDL-Vorgänge, einschließlich erstellen und Löschen von Tabellen und gespeicherten Prozeduren sowie das Ausführen von R-Skript in einem externen Prozess in SQL Server. Weisen Sie in diesem Schritt Berechtigungen, um diese Aufgaben zu ermöglichen.

In diesem Beispiel wird angenommen, eine SQL-Anmeldung (DDUser01), aber wenn Sie eine Windows-Anmeldung erstellt haben, verwenden Sie stattdessen ein.

```sql
USE RevoDeepDive
GO

EXEC sp_addrolemember 'db_owner', 'DDUser01'
GRANT EXECUTE ANY EXTERNAL SCRIPT TO DDUser01
GO
```

## <a name="troubleshoot-connections"></a>Problembehandlung für Verbindungen

Dieser Abschnitt enthält einige häufig auftretende Probleme, denen Sie möglicherweise während der Einrichtung der Datenbank gegenüber stehen.

- **Wie kann ich die Datenbankkonnektivität und SQL-Abfragen überprüfen?**
  
    Bevor Sie R-Code mithilfe des Servers ausführen, möchten Sie möglicherweise überprüfen, ob die Datenbank über Ihre R-Entwicklungsumgebung erreicht werden kann. Sowohl [Server-Explorer in Visual Studio](https://msdn.microsoft.com/library/x603htbk.aspx) als auch [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) sind kostenlose Tools mit leistungsstarker Datenbankkonnektivität und Verwaltungsfunktionen.
  
    Wenn Sie zusätzliche Datenbankverwaltungstools installieren möchten, können Sie eine Testverbindung zur SQL Server-Instanz erstellen, indem Sie den [ODBC-Datenquellen-Administrator](https://msdn.microsoft.com/library/ms714024.aspx) in der Systemsteuerung verwenden. Wenn die Datenbank ordnungsgemäß konfiguriert ist und Sie den richtigen Benutzernamen und das richtige Kennwort eingeben, sollten Sie die zuvor von Ihnen erstellte Datenbank sehen und diese als Ihre Standarddatenbank auswählen.
  
    Häufige Ursachen für Verbindungsfehler sind remote Verbindungen sind nicht für den Server aktiviert und Named Pipes-Protokoll ist nicht aktiviert. Weitere Tipps zur Problembehandlung finden Sie in diesem Artikel: [Beheben von Verbindungsfehlern mit der SQL Server-Datenbank-Engine](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Mein Tabellenname wurde mit dem Präfix DataReader versehen – warum?**
  
    Wenn Sie angeben, das Standardschema für diesen Benutzer als **"db_datareader"**, alle Tabellen und andere neue Objekte, die von diesem Benutzer erstellte haben das Präfix der *Schema* Name. Ein Schema ist wie ein Ordner, den Sie einer Datenbank hinzufügen können, um Objekte zu organisieren. Das Schema definiert außerdem die Berechtigungen eines Benutzers in der Datenbank.
  
    Wenn das Schema mit einem bestimmten Benutzernamen verknüpft ist, wird der Benutzer die _schemabesitzer_. Wenn Sie ein Objekt erstellen, müssen Sie immer es immer in Ihrem eigenen Schema erstellen, außer Sie geben ausdrücklich an, dass es in einem anderen Schema erstellt werden soll.
  
    Beispielsweise wird bei der Erstellung einer Tabelle mit dem Namen **TestData**, und Ihr Standardschema **"db_datareader"**, die Tabelle wird erstellt, mit dem Namen `<database_name>.db_datareader.TestData`.
  
    Aus diesem Grund kann eine Datenbank mehrere Tabellen mit dem gleichen Namen enthalten, solange die Tabellen zu unterschiedlichen Schemas gehören.
   
    Wenn Sie eine Tabelle suchen und führen Sie kein Schema angeben, sucht der Datenbankserver, für ein Schema, das Sie besitzen. Daher müssen Sie keinen Schemanamen angeben, wenn Sie auf Tabellen in einem Schema zugreifen, das mit Ihrem Login verknüpft sind.
  
- **Ich verfüge über keine DDL-Berechtigungen. Kann ich weiterhin das Tutorial ausführen?**
  
    Ja, aber stellen Sie eine Person zum Vorabladen von Daten in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen, und fahren Sie mit der nächsten Lektion fort. Die Funktionen, die DDL-Berechtigungen erforderlich sind in diesem Tutorial nach Möglichkeit hingewiesen.

    Darüber hinaus bitten Sie Ihren Administrator, um Sie über die Berechtigung EXECUTE ANY EXTERNAL SCRIPT gewähren. Es wird für R-skriptausführung benötigt, ob remote oder mithilfe von `sp_execute_external_script`.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen von SQL Server-Datenobjekten mithilfe von RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)