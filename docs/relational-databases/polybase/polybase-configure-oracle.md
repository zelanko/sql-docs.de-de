---
title: Konfigurieren von PolyBase für den Zugriff auf externe Daten in Oracle | Microsoft-Dokumentation
description: In diesem Artikel wird die Verwendung von PolyBase zur Erstellung einer externen Datenquelle für den Zugriff auf Oracle-Daten erläutert.
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
ms.reviewer: jroth
manager: craigg
ms.custom: ''
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 0545e320378fe1c9a8951100b9353ff0c4105172
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "64775401"
---
# <a name="configure-polybase-to-access-external-data-in-oracle"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in Oracle

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird erläutert, wie Sie PolyBase in einer SQL Server-Instanz verwenden, um externe Daten in Oracle abzufragen.

## <a name="prerequisites"></a>Voraussetzungen

Wenn Sie PolyBase nicht installiert haben, finden Sie weitere Informationen unter [PolyBase installation (Installieren von PolyBase)](polybase-installation.md).

  Bevor datenbankweit gültige Anmeldeinformationen erstellt werden können, muss ein [Hauptschlüssel](../../t-sql/statements/create-master-key-transact-sql.md) erstellt werden. 

## <a name="configure-an-oracle-external-data-source"></a>Konfigurieren einer externen Oracle-Datenquelle

Um die Daten einer Oracle-Datenquelle abzufragen, müssen Sie externe Tabellen zum Referenzieren der externen Daten erstellen. Dieser Abschnitt enthält Beispielcode zum Erstellen dieser externen Tabellen.

In diesem Abschnitt werden die folgenden Transact-SQL-Befehle verwendet:

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)


1. Erstellen Sie datenbankweit gültige Anmeldeinformationen für den Zugriff auf die Oracle-Quelle.

    ```sql
    /*  specify credentials to external data source
    *  IDENTITY: user name for external source. 
    *  SECRET: password for external source.
    */
    CREATE DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'username', Secret = 'password';
    ```

1. Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle.

    ```sql
    /* 
    * LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    * PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    * CONNECTION_OPTIONS: Specify driver location
    * CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( LOCATION = 'oracle://<server address>[:<port>]',
    -- PUSHDOWN = ON | OFF,
    CREDENTIAL = credential_name)
    ```

1. **Optional:** Erstellen Sie Statistiken für eine externe Tabelle.

    Es wird empfohlen, Statistiken für externe Tabellenspalten zu erstellen – insbesondere für diejenigen, die für Joins, Filter und Aggregate verwendet werden. So können Sie eine optimale Abfrageleistung erzielen.

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
    ```

>[!IMPORTANT] 
>Sobald Sie eine externe Datenquelle erstellt haben, können Sie über den Befehl [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) eine abfragbare Tabelle für diese Quelle erstellen. 

Weitere Informationen und Beispiele finden Sie in den folgenden Artikeln:

- [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
- [Was ist PolyBase?](polybase-guide.md)
