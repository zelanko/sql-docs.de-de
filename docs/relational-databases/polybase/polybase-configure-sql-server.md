---
title: Konfigurieren von PolyBase für den Zugriff auf externe Daten in SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 90b535714eea3a00ecffd2cf010187fbcd676a82
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806640"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie PolyBase in einer SQL Server-Instanz verwenden, um externe Daten in einer anderen SQL Server-Instanz abzufragen.

## <a name="prerequisites"></a>Voraussetzungen

Wenn Sie PolyBase nicht installiert haben, finden Sie weitere Informationen unter [PolyBase installation (Installieren von PolyBase)](polybase-installation.md). Die Voraussetzungen für die Installation werden im entsprechenden Artikel erläutert.

## <a name="configure-an-external-table"></a>Konfigurieren einer externen Tabelle

Um die Daten einer SQL Server-Datenquelle abzufragen, müssen Sie externe Tabellen zum Referenzieren der externen Daten erstellen. Dieser Abschnitt enthält Beispielcode zum Erstellen dieser externen Tabellen. 
 
Es empfiehlt sich, Statistiken für externe Tabellenspalten zu erstellen – insbesondere für diejenigen, die für Joins, Filter und Aggregate verwendet werden. So können Sie eine optimale Abfrageleistung erzielen.

In diesem Abschnitt werden folgende Objekte erstellt:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) 
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)

1. Erstellen Sie einen Hauptschlüssel in der Datenbank. Dies ist erforderlich, um das Geheimnis für die Anmeldeinformationen zu verschlüsseln.

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
     ```

1. Erstellen Sie datenbankweite Anmeldeinformationen.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL SqlServerCredentials   
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle. Geben Sie einen Speicherort der externen Datenquelle sowie Anmeldeinformationen für SQL Server an.

     ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE SQLServerInstance
    WITH ( 
    LOCATION = sqlserver://SqlServer,
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = SQLServerCredentials
    );

     ```

1. Erstellen von Schemas für externe Daten

     ```sql
     CREATE SCHEMA sqlserver;
     GO
     ```

1.  Erstellen Sie mit [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) externe Tabellen, die in einer externen SQL Server-Instanz gespeicherte Daten repräsentieren.
 
     ```sql
     /*  LOCATION: sql server table/view in 'database_name.schema_name.object_name' format
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE sqlserver.customer(
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
      LOCATION='tpch_10.dbo.customer',
      DATA_SOURCE=SqlServerInstance
     );
      ```

1. Erstellen Sie Statistiken für eine externe Tabelle.

     ```sql
      CREATE STATISTICS CustomerCustKeyStatistics ON sqlserver.customer (C_CUSTKEY) WITH FULLSCAN; 
     ```

## <a name="sql-server-connector-compatible-types"></a>Mit dem SQL Server-Connector kompatible Typen

Zu anderen Datenquellen, die von einer SQL Server-Verbindung erkannt werden, kann eine Verbindung hergestellt werden. Mithilfe des PolyBase-Connectors für SQL Server können Sie externe Tabellen in **Azure SQL Data Warehouse und Azure SQL-Datenbank** erstellen. Führen Sie dazu die oben genannten Schritte aus. Stellen Sie sicher, dass die datenbankweit gültigen Anmeldeinformationen, die Serveradresse, der Port und die Standortzeichenfolge in Korrelation stehen mit denen der kompatiblen Datenquelle, mit der Sie eine Verbindung herstellen möchten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie in der [Übersicht zu SQL Server-PolyBase](polybase-guide.md).
