---
title: Arbeiten mit SQL Server-Daten mithilfe von R (SQL und R tieferer) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a59d467417c3471fa643acf9fc65ab45d5dc7a45
ms.sourcegitcommit: df3923e007527ce79e2d05821b62d77ee06fd655
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2018
ms.locfileid: "44375673"
---
# <a name="lesson-1-create-a-database-and-permissions"></a>Lektion 1: Erstellen einer Datenbank und Berechtigungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In dieser Lektion richten Sie die Umgebung Sie und fügen Sie die Daten zum Trainieren der Modelle und führen einige schnelle Zusammenfassungen der Daten. Als Teil des Prozesses müssen Sie diese Aufgaben durchführen:
  
- Erstellen einer neuen Datenbank zum Speichern der Daten für das Training und die Bewertung von zwei R-Modellen.
  
- Erstellen eines Kontos (entweder ein Windows-Benutzer oder ein SQL-Anmeldename), das für die Kommunikation zwischen Ihrer Arbeitsstation und dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Computer verwendet wird.
  
- Erstellen von Datenquellen in R für die Arbeit mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten und Datenbankobjekten.
  
- Verwenden von R-Datenquellen zum Laden von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
- Verwenden von R zum Abrufen einer Liste von Variablen und zum Ändern der Metadaten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle.
  
- Erstellen eines Computekontexts zum Aktivieren von Remoteausführungen von R-Code.
  
- (Optional) Aktivieren der Ablaufverfolgung auf dem entfernten computekontext.
  
## <a name="create-the-database-and-user"></a>Erstellen der Datenbank und die Benutzer

In dieser exemplarischen Vorgehensweise erstellen Sie eine neue Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], und fügen Sie eine SQL-Anmeldung mit Berechtigungen zum Schreiben und Lesen von Daten und zum Ausführen von R-Skripts hinzu.

> [!NOTE]
> Wenn Sie Daten nur lesen, benötigt das Konto, das die R-Skripts ausführt SELECT-Berechtigungen (**"db_datareader"** Rolle) für die angegebene Datenbank. In diesem Tutorial müssen Sie jedoch DDL-Administratorberechtigungen vorbereiten die Datenbank, und klicken Sie zum Erstellen von Tabellen zum Speichern der Bewertungsergebnisse verfügen.
> 
> Wenn Sie nicht der Besitzer der Datenbank sind, benötigen Sie außerdem die Berechtigung EXECUTE ANY EXTERNAL SCRIPT, um R-Skripts ausführen.

1. Wählen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]die Instanz aus, bei der [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] aktiviert ist. Führen Sie einen Rechtsklick auf **Datenbanken**aus, und wählen Sie **Neue Datenbank**aus.
  
2. Geben Sie einen Namen für die neue Datenbank ein. Sie können einen beliebigen Namen verwenden, denken Sie jedoch daran, alle [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts und R-Skripts in dieser exemplarischen Vorgehensweise dementsprechend zu bearbeiten.
  
    > [!TIP]
    > Klicken Sie mit der rechten Maustaste auf **Datenbanken** , und wählen Sie **Aktualisieren** aus, um den aktualisierten Datenbanknamen anzuzeigen.
  
3. Klicken Sie auf **Neue Abfrage**, und legen Sie die Masterdatenbank als Datenbankkontext fest.
  
4. Führen Sie im Fenster **Abfrage** die folgenden Befehle aus, um die Benutzerkonten zu erstellen und sie der Datenbank zuzuweisen, die für dieses Tutorial verwendet wird. Achten Sie darauf, den Datenbanknamen falls nötig zu ändern.
  
**Windows-Benutzer**
  
```SQL
 -- Create server user based on Windows account
USE master
GO
CREATE LOGIN [<DOMAIN>\<user_name>] FROM WINDOWS WITH DEFAULT_DATABASE=[DeepDive]

 --Add the new user to tutorial database
USE [DeepDive]
GO
CREATE USER [<user_name>] FOR LOGIN [<DOMAIN>\<user_name>] WITH DEFAULT_SCHEMA=[db_datareader]
```

**SQL-Anmeldename**

```SQL
-- Create new SQL login
USE master
GO
CREATE LOGIN DDUser01 WITH PASSWORD='<type password here>', CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;

-- Add the new SQL login to tutorial database
USE [DeepDive]
GO
CREATE USER [DDUser01] FOR LOGIN [DDUser01] WITH DEFAULT_SCHEMA=[db_datareader]
```

5. Um zu bestätigen, dass der Benutzer erstellt wurde, wählen Sie die neue Datenbank aus, und erweitern Sie **Sicherheit**und **Benutzer**.

## <a name="troubleshooting"></a>Problembehandlung

Dieser Abschnitt enthält einige häufig auftretende Probleme, denen Sie möglicherweise während der Einrichtung der Datenbank gegenüber stehen.

- **Wie kann ich die Datenbankkonnektivität und SQL-Abfragen überprüfen?**
  
    Bevor Sie R-Code mithilfe des Servers ausführen, möchten Sie möglicherweise überprüfen, ob die Datenbank über Ihre R-Entwicklungsumgebung erreicht werden kann. Sowohl [Server-Explorer in Visual Studio](https://msdn.microsoft.com/library/x603htbk.aspx) als auch [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) sind kostenlose Tools mit leistungsstarker Datenbankkonnektivität und Verwaltungsfunktionen.
  
    Wenn Sie zusätzliche Datenbankverwaltungstools installieren möchten, können Sie eine Testverbindung zur SQL Server-Instanz erstellen, indem Sie den [ODBC-Datenquellen-Administrator](https://msdn.microsoft.com/library/ms714024.aspx) in der Systemsteuerung verwenden. Wenn die Datenbank ordnungsgemäß konfiguriert ist und Sie den richtigen Benutzernamen und das richtige Kennwort eingeben, sollten Sie die zuvor von Ihnen erstellte Datenbank sehen und diese als Ihre Standarddatenbank auswählen.
  
    Wenn Sie keine Verbindung mit der Datenbank herstellen können, überprüfen Sie ob die Remoteverbindungen für den Server aktiviert sind und ob das Named Pipes-Protokoll aktiviert ist. Weitere Tipps zur Problembehandlung finden Sie in diesem Artikel: [Problembehandlung beim Herstellen einer Verbindung mit der SQL Server-Datenbank-Engine](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Mein Tabellenname wurde mit dem Präfix DataReader versehen – warum?**
  
    Wenn Sie angeben, das Standardschema für diesen Benutzer als **"db_datareader"**, alle Tabellen und andere neue Objekte, die von diesem Benutzer erstellte haben das Präfix der *Schema* Name. Ein Schema ist wie ein Ordner, den Sie einer Datenbank hinzufügen können, um Objekte zu organisieren. Das Schema definiert außerdem die Berechtigungen eines Benutzers in der Datenbank.
  
    Wenn das Schema mit einem bestimmten Benutzernamen verknüpft ist, wird der Benutzer die _schemabesitzer_. Wenn Sie ein Objekt erstellen, müssen Sie immer es immer in Ihrem eigenen Schema erstellen, außer Sie geben ausdrücklich an, dass es in einem anderen Schema erstellt werden soll.
  
    Beispielsweise wird bei der Erstellung einer Tabelle mit dem Namen **TestData**, und Ihr Standardschema **"db_datareader"**, die Tabelle wird erstellt, mit dem Namen `<database_name>.db_datareader.TestData`.
  
    Aus diesem Grund kann eine Datenbank mehrere Tabellen mit dem gleichen Namen enthalten, solange die Tabellen zu unterschiedlichen Schemas gehören.
   
    Wenn Sie eine Tabelle suchen und führen Sie kein Schema angeben, sucht der Datenbankserver, für ein Schema, das Sie besitzen. Daher müssen Sie keinen Schemanamen angeben, wenn Sie auf Tabellen in einem Schema zugreifen, das mit Ihrem Login verknüpft sind.
  
- **Ich verfüge über keine DDL-Berechtigungen. Kann ich weiterhin das Tutorial ausführen?**
  
    Ja. Sie müssen jedoch jemanden bitten, die Daten vorab in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen zu laden und die Abschnitte zu überspringen, in denen Sie neue Tabellen erstellen sollen. Die Funktionen, die DDL-Berechtigungen erforderlich sind in diesem Tutorial nach Möglichkeit hingewiesen.

    Darüber hinaus bitten Sie Ihren Administrator, um Sie über die Berechtigung EXECUTE ANY EXTERNAL SCRIPT gewähren. Es wird für R-skriptausführung benötigt, ob remote oder mithilfe von `sp_execute_external_script`.

## <a name="next-step"></a>Nächster Schritt

[Erstellen von SQL Server-Datenobjekten mithilfe von RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)

## <a name="overview"></a>Übersicht

[Tieferer Einblick in Data Science: Verwenden der RevoScaleR-Pakete](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)



