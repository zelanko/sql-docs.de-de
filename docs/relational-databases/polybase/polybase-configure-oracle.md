---
title: Konfigurieren von PolyBase für den Zugriff auf externe Daten in Oracle | Microsoft-Dokumentation
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
ms.openlocfilehash: bf8c9e4d9bdc59d60569594006676b6fa766071a
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806560"
---
# <a name="configure-polybase-to-access-external-data-in-oracle"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in Oracle

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie PolyBase in einer SQL Server-Instanz verwenden, um externe Daten in Oracle abzufragen.

## <a name="prerequisites"></a>Voraussetzungen

Wenn Sie PolyBase nicht installiert haben, finden Sie weitere Informationen unter [PolyBase installation (Installieren von PolyBase)](polybase-installation.md).

## <a name="configure-an-external-table"></a>Konfigurieren einer externen Tabelle

Um die Daten einer Oracle-Datenquelle abzufragen, müssen Sie externe Tabellen zum Referenzieren der externen Daten erstellen. Dieser Abschnitt enthält Beispielcode zum Erstellen dieser externen Tabellen. 
 
In diesem Abschnitt werden folgende Objekte erstellt:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)

1. Erstellen Sie einen Hauptschlüssel für die Datenbank, wenn noch keiner vorhanden ist. Dies ist erforderlich, um das Geheimnis für die Anmeldeinformationen zu verschlüsseln.

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password';  
     ```
    ## <a name="arguments"></a>Argumente
    PASSWORD ='password'

    Das zum Verschlüsseln des Datenbank-Hauptschlüssels verwendete Kennwort. „password“ muss den Anforderungen der Windows-Kennwortrichtlinien des Computers entsprechen, auf dem die Instanz von SQL Server ausgeführt wird.

1. Erstellen Sie datenbankweite Anmeldeinformationen.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
      CREATE DATABASE SCOPED CREDENTIAL credential_name
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle. Geben Sie einen externen Speicherort und Anmeldeinformationen für die Oracle-Datenquelle an.

     ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    * CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( 
    LOCATION = oracle://<server address>[:<port>],
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = credential_name
     ```

1.  Erstellen Sie mit [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) externe Tabellen, die die im externen Oracle-System gespeicherten Daten repräsentieren.
 
      ```sql
      /*  LOCATION: Oracle table/view in '<database_name>.<schema_name>.<object_name>' format
     *  DATA_SOURCE: the external data source, created above.
     */
      CREATE EXTERNAL TABLE customers(
      [O_ORDERKEY] DECIMAL(38) NOT NULL,
     [O_CUSTKEY] DECIMAL(38) NOT NULL,
     [O_ORDERSTATUS] CHAR COLLATE Latin1_General_BIN NOT NULL,
     [O_TOTALPRICE] DECIMAL(15,2) NOT NULL,
     [O_ORDERDATE] DATETIME2(0) NOT NULL,
     [O_ORDERPRIORITY] CHAR(15) COLLATE Latin1_General_BIN NOT NULL,
     [O_CLERK] CHAR(15) COLLATE Latin1_General_BIN NOT NULL,
     [O_SHIPPRIORITY] DECIMAL(38) NOT NULL,
     [O_COMMENT] VARCHAR(79) COLLATE Latin1_General_BIN NOT NULL
     )
     WITH (
      LOCATION='customer',
      DATA_SOURCE=  external_data_source_name
     );
     ```

1. **Optional:** Erstellen Sie Statistiken für eine externe Tabelle.

    Es empfiehlt sich, Statistiken für externe Tabellenspalten zu erstellen – insbesondere für diejenigen, die für Joins, Filter und Aggregate verwendet werden. So können Sie eine optimale Abfrageleistung erzielen.

     ```sql
      CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
     ```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie in der [Übersicht zu SQL Server-PolyBase](polybase-guide.md).
