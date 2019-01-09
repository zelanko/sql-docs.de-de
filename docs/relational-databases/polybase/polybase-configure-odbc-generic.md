---
title: Konfigurieren von PolyBase für den Zugriff auf externe Daten mit generischen ODBC-Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/16/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 98e06e3199d4ce8750a4a5956aec6d97c141b33b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53214256"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Mit PolyBase in SQL Server 2019 können Sie mithilfe des ODBC-Connectors eine Verbindung mit ODBC-kompatiblen Datenquellen herstellen. 

## <a name="prerequisites"></a>Voraussetzungen

Hinweis: Die Funktion ist nur für SQL Server unter Windows verfügbar. 

Wenn Sie PolyBase nicht installiert haben, finden Sie weitere Informationen unter [PolyBase installation (Installieren von PolyBase)](polybase-installation.md).

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

Die folgenden Objekte werden in diesem Abschnitt erstellt:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) 
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)

1. Erstellen Sie einen Hauptschlüssel für die Datenbank, falls noch keiner vorhanden ist. Dies ist erforderlich, um das Geheimnis für die Anmeldeinformationen zu verschlüsseln.

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password';  
     ```
    ## <a name="arguments"></a>Argumente
    PASSWORD ='password'

    Das zum Verschlüsseln des Datenbank-Hauptschlüssels verwendete Kennwort. „password“ (Kennwort) muss den Anforderungen der Windows-Kennwortrichtlinien des Computers entsprechen, auf dem die Instanz von SQL Server ausgeführt wird.

1. Erstellen Sie datenbankweit gültige Anmeldeinformationen für den Zugriff auf die ODBC-Datenquelle.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL credential_name
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle.

     ```sql
    /*  LOCATION: Location string should be of format '<type>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( 
    LOCATION = odbc://<ODBC server address>[:<port>],
    CONNECTION_OPTIONS = 'SSL=0;sslAllowInvalidCertificates=1;Driver={<Name of Installed Driver>};HOST=%s;AUTHMECH=0',
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = credential_name
    );

     ```


1.  Erstellen Sie mit [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) externe Tabellen, die Daten in der externen Datenquelle repräsentieren.
 
     ```sql
     /*  LOCATION: ODBC data source table/view
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE customer(
     C_CUSTKEY INT NOT NULL,
     C_NAME VARCHAR(25) NOT NULL,
     C_ADDRESS VARCHAR(40) NOT NULL,
     C_NATIONKEY INT NOT NULL,
     C_PHONE CHAR(15) NOT NULL,
     C_ACCTBAL DECIMAL(15,2) NOT NULL,
     C_MKTSEGMENT CHAR(10) NOT NULL,
     C_COMMENT VARCHAR(117) NOT NULL
      )
      WITH (
      LOCATION='customer',
      DATA_SOURCE= external_data_source_name
     );
      ```

1. **Optional:** Erstellen Sie Statistiken für eine externe Tabelle.

    Es empfiehlt sich, Statistiken für externe Tabellenspalten zu erstellen – insbesondere für diejenigen, die für Joins, Filter und Aggregate verwendet werden. So können Sie eine optimale Abfrageleistung erzielen.

     ```sql
      CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
     ```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie in der [Übersicht zu SQL Server-PolyBase](polybase-guide.md).
