---
title: 'Zugreifen auf externe Daten: Generische ODBC-Typen: PolyBase'
description: Mit PolyBase in SQL Server können Sie mithilfe des ODBC-Connectors eine Verbindung mit kompatiblen Datenquellen herstellen. Installieren Sie den ODBC-Treiber, und erstellen Sie externe Tabellen.
ms.date: 02/19/2020
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: c8bf01e39fb68d2315df2a441f7b2b4fefa81872
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246520"
---
# <a name="configure-polybase-to-access-external-data-with-odbc-generic-types"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten mit generischen ODBC-Typen

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Mit PolyBase in SQL Server 2019 können Sie mithilfe des ODBC-Connectors eine Verbindung mit ODBC-kompatiblen Datenquellen herstellen.

In diesem Artikel finden Sie Beispiele zur Verwendung eines ODBC-Treibers. Wenden Sie sich für spezifische Beispiele an Ihren ODBC-Anbieter. Die entsprechenden Verbindungszeichenfolgenoptionen finden Sie in der ODBC-Treiberdokumentation für die Datenquelle. Die in diesem Artikel veranschaulichten Beispiele gelten möglicherweise nicht für alle ODBC-Treiber.

## <a name="prerequisites"></a>Voraussetzungen

>[!NOTE]
>Dieses Feature erfordert SQL Server unter Windows.

* [PolyBase-Installation](polybase-installation.md)

* Bevor datenbankweit gültige Anmeldeinformationen erstellt werden können, muss ein [Hauptschlüssel](../../t-sql/statements/create-master-key-transact-sql.md) erstellt werden.

## <a name="install-the-odbc-driver"></a>Installieren des ODBC-Treibers

Laden Sie zunächst den ODBC-Treiber der Datenquelle herunter, mit der Sie eine Verbindung auf den PolyBase-Knoten herstellen möchten, und installieren Sie ihn. Sobald der Treiber installiert ist, können Sie ihn unter **ODBC Data Source Administrator** (ODBC-Datenquellenadministrator) anzeigen und testen.

![PolyBase-Erweiterungsgruppen](../../relational-databases/polybase/media/polybase-odbc-admin.png) 

Im obigen Beispiel ist der Name des Treibers rot eingekreist. Verwenden Sie diesen Namen beim Erstellen der externen Datenquelle.

> [!IMPORTANT]
> Aktivieren Sie das Verbindungspooling, um die Abfrageleistung zu verbessern. Dies erfolgt über **ODBC Data Source Administrator** (ODBC-Datenquellenadministrator).

## <a name="create-an-external-table"></a>Erstellen einer externen Tabelle

Um die Daten einer ODBC-Datenquelle abzufragen, müssen Sie externe Tabellen zum Verweisen auf externe Daten erstellen. Dieser Abschnitt enthält einen Beispielcode zum Erstellen externer Tabellen.

In diesem Abschnitt werden die folgenden Transact-SQL-Befehle verwendet:

* [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
* [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
* [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Erstellen Sie datenbankweit gültige Anmeldeinformationen für den Zugriff auf die ODBC-Quelle.

    ```sql
    CREATE DATABASE SCOPED CREDENTIAL <credential_name> WITH IDENTITY = '<username>', Secret = '<password>';
    ```

    Im folgenden Beispiel werden Anmeldeinformationen namens `credential_name` mit der Identität `username` und einem komplexen Kennwort erstellt.

    ```sql
    CREATE DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'username', Secret = 'BycA4ZjrE#*2W%!';
    ```

1. Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle.

    ```sql
    CREATE EXTERNAL DATA SOURCE <external_data_source_name>
    WITH ( LOCATION = 'odbc://<ODBC server address>[:<port>]',
    CONNECTION_OPTIONS = 'Driver={<Name of Installed Driver>};
    ServerNode = <name of server  address>:<Port>',
    -- PUSHDOWN = [ON] | OFF,
    CREDENTIAL = <credential_name> );
    ```

    Im folgenden Beispiel wird eine externe Datenquelle erstellt:
    * Sie wird `external_data_source_name` benannt.
    * Sie befindet sich auf dem ODBC-Server `SERVERNAME` auf Port `4444`.
    * Sie stellt eine Verbindung mit `CData ODBC Driver For SAP 2015` her. Dies ist der Treiber, der im Abschnitt [Installieren des ODBC-Treibers](#install-the-odbc-driver) erstellt wurde.
    * Auf `ServerNode` `sap_server_node` Port `5555`
    * Sie wird so konfiguriert, dass die Verarbeitung an den Server weitergegeben wird (`PUSHDOWN = ON`).
    * Die `credential_name`-Anmeldeinformationen werden verwendet.

    ```sql
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( LOCATION = 'odbc://SERVERNAME:4444',
    CONNECTION_OPTIONS = 'Driver={CData ODBC Driver For SAP 2015};
    ServerNode = sap_server_node:5555',
    PUSHDOWN = ON,
    CREDENTIAL = credential_name );
    ```

1. **Optional:** Erstellen Sie Statistiken für eine externe Tabelle.

    Für eine optimale Abfrageleistung wird empfohlen, Statistiken für externe Tabellenspalten zu erstellen – insbesondere für diejenigen, die für Joins, Filter und Aggregate verwendet werden.

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
    ```

>[!IMPORTANT]
>Sobald Sie eine externe Datenquelle erstellt haben, verwenden Sie den Befehl [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md), um eine abfragbare Tabelle für diese Quelle zu erstellen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie in der [Übersicht zu SQL Server-PolyBase](polybase-guide.md).
