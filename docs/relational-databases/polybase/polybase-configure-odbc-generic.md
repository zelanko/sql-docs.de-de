---
title: Konfigurieren von PolyBase für den Zugriff auf externe Daten mit generischen ODBC-Typen | Microsoft-Dokumentation
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 697de72ce644ffdce721745b33cde3372edfb2c8
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71710660"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit PolyBase in SQL Server 2019 können Sie mithilfe des ODBC-Connectors eine Verbindung mit ODBC-kompatiblen Datenquellen herstellen. 

## <a name="prerequisites"></a>Voraussetzungen

Hinweis: Die Funktion ist nur für SQL Server unter Windows verfügbar. 

Wenn Sie PolyBase nicht installiert haben, finden Sie weitere Informationen unter [PolyBase installation (Installieren von PolyBase)](polybase-installation.md).

 Bevor datenbankweit gültige Anmeldeinformationen erstellt werden können, muss ein [Hauptschlüssel](../../t-sql/statements/create-master-key-transact-sql.md) erstellt werden. 

Laden Sie zuerst den ODBC-Treiber aus der Datenquelle herunter, mit der Sie eine Verbindung für jeden PolyBase-Knoten herstellen möchten, und installieren Sie ihn. Sobald der Treiber installiert ist, können Sie ihn unter „ODBC Data Source Administrator“ (ODBC-Datenquellenadministrator) anzeigen und testen.

![PolyBase-Erweiterungsgruppen](../../relational-databases/polybase/media/polybase-odbc-admin.png) 

> **WICHTIG!**
> 
> Um die Abfrageleistung zu verbessern, stellen Sie sicher, dass für den Treiber Verbindungspooling aktiviert ist. Dies erfolgt über „ODBC Data Source Administrator“ (ODBC-Datenquellenadministrator).
> 
> **Hinweis**
> 
> Der Treibername (eingekreistes Beispiel oben) muss beim Erstellen der externen Datenquelle angegeben werden (Schritt 3 unten).

## <a name="create-an-external-table"></a>Erstellen einer externen Tabelle

Um die Daten einer ODBC-Datenquelle abzufragen, müssen Sie externe Tabellen zum Verweisen auf externe Daten erstellen. Dieser Abschnitt enthält einen Beispielcode zum Erstellen externer Tabellen.

In diesem Abschnitt werden die folgenden Transact-SQL-Befehle verwendet:

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Erstellen Sie datenbankweit gültige Anmeldeinformationen für den Zugriff auf die ODBC-Quelle.

    ```sql
    /*  specify credentials to external data source
    *  IDENTITY: user name for external source. 
    *  SECRET: password for external source.
    */
    CREATE DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'username', Secret = 'password';
    ```

1. Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle.

    ```sql
    /*  LOCATION: Location string should be of format '<type>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( LOCATION = odbc://<ODBC server address>[:<port>],
    CONNECTION_OPTIONS = 'Driver={<Name of Installed Driver>};
    ServerNode = <name of server  address>:<Port>',
    -- PUSHDOWN = ON | OFF,
    CREDENTIAL = credential_nam );
    ```

1. **Optional:** Erstellen Sie Statistiken für eine externe Tabelle.

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

Für eine optimale Abfrageleistung wird empfohlen, Statistiken für externe Tabellenspalten zu erstellen – insbesondere für diejenigen, die für Joins, Filter und Aggregate verwendet werden.

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
    ```

>[!IMPORTANT] 
>Sobald Sie eine externe Datenquelle erstellt haben, können Sie über den Befehl [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) eine abfragbare Tabelle für diese Quelle erstellen. 

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie in der [Übersicht zu SQL Server-PolyBase](polybase-guide.md).
