---
title: Konfigurieren von PolyBase für den Zugriff auf externe Daten in MongoDB | Microsoft-Dokumentation
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
ms.openlocfilehash: a51842a1682b5e02db4ea216bddefbabbf0a7f56
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874308"
---
# <a name="configure-polybase-to-access-external-data-in-mongodb"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in MongoDB

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie PolyBase in einer SQL Server-Instanz verwenden, um externe Daten in MongoDB abzufragen.

## <a name="prerequisites"></a>Voraussetzungen

Wenn Sie PolyBase nicht installiert haben, finden Sie weitere Informationen unter [PolyBase installation (Installieren von PolyBase)](polybase-installation.md). Die Voraussetzungen für die Installation werden im entsprechenden Artikel erläutert.

## <a name="configure-an-external-table"></a>Konfigurieren einer externen Tabelle

Um die Daten einer MongoDB-Datenquelle abzufragen, müssen Sie externe Tabellen zum Referenzieren der externen Daten erstellen. Dieser Abschnitt enthält Beispielcode zum Erstellen dieser externen Tabellen.

Es empfiehlt sich, Statistiken für externe Tabellenspalten zu erstellen – insbesondere für diejenigen, die für Joins, Filter und Aggregate verwendet werden. So können Sie eine optimale Abfrageleistung erzielen.

In diesem Abschnitt werden folgende Objekte erstellt:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)
- CREATE EXTERNAL DATA SOURCE (Transact-SQL)
- CREATE EXTERNAL TABLE (Transact-SQL)
- CREATE STATISTICS (Transact-SQL)

1.    Erstellen Sie einen Hauptschlüssel in der Datenbank. Dies ist erforderlich, um das Geheimnis für die Anmeldeinformationen zu verschlüsseln.

      ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
      ```

1.   Erstellen Sie datenbankweite Anmeldeinformationen.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL MongoDBCredentials 
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1.  Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle. Geben Sie einen Speicherort und Anmeldeinformationen für die externe MongoDB-Datenquelle an.

     ```sql
     /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE MongoInstance
    WITH (
    LOCATION = mongodb://MongoServer,
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = MongoDBCredentials
    );
     ```

1. Erstellen von Schemas für externe Daten

     ```sql
     CREATE SCHEMA MongoDB;
     GO
     ```

1.  Erstellen Sie mit [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) externe Tabellen, die die im externen MongoDB-System gespeicherten Daten repräsentieren.

     ```sql
     /*  LOCATION: MongoDB table/view in '<database_name>.<schema_name>.<object_name>' format
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE MongoDB.orders(
     [O_ORDERKEY] DECIMAL(38) NOT NULL,
     [O_CUSTKEY] DECIMAL(38) NOT NULL,
     [O_ORDERSTATUS] CHAR COLLATE Latin1_General_BIN NOT NULL,
     [O_TOTALPRICE] DECIMAL(15,2) NOT NULL,
     [O_ORDERDATE] DATETIME2(0) NOT NULL,
     [O_COMMENT] VARCHAR(79) COLLATE Latin1_General_BIN NOT NULL
     )
     WITH (
     LOCATION='TPCH..ORDERS',
     DATA_SOURCE= MongoDBInstance
     );
     ```

1. Erstellen Sie Statistiken für eine externe Tabelle, um eine optimale Leistung zu erzielen.

     ```sql
      CREATE STATISTICS OrdersOrderKeyStatistics ON MongoDB.orders(O_ORDERKEY) WITH FULLSCAN;
     ```

## <a name="flattening"></a>Vereinfachen
 Die Vereinfachung (Flattening) ist für geschachtelte und wiederholte Daten aus MongoDB-Dokumentsammlungen aktiviert. Der Benutzer muss die Erstellung einer externen Tabelle ermöglichen und explizit ein relationales Schema über MongoDB-Dokumentsammlungen angeben, die möglicherweise geschachtelte und/oder wiederholte Daten besitzen. In zukünftigen Meilensteinen wird die automatische Schemaerkennung über MongoDB-Dokumentsammlungen aktiviert.
Geschachtelte/wiederholte JSON-Datentypen werden wie folgt vereinfacht

* Objekt: unsortierte Schlüssel-/Wertsammlung, die in geschweiften Klammern eingeschlossen wird (geschachtelt)

   - Wir erstellen eine Tabellenspalte für jeden Objektschlüssel

     * Spaltenname: objectname_keyname

* Array: durch Kommas getrennte geordnete Werte, die in eckigen Klammern eingeschlossen sind (wiederholt)

   - Für jedes Arrayelement wird eine neue Tabellenzeile hinzugefügt.

   - Es wird pro Array eine Spalte erstellt, um den Arrayelementindex zu speichern.

     * Spaltenname: arrayname_index

     * Datentyp: bigint

Es können mehrere potenzielle Probleme mit diesem Verfahren auftreten. Zwei davon sind die folgenden:

* Ein leeres wiederholtes Feld maskiert die Daten, die in den vereinfachten Feldern des gleichen Datensatzes enthalten sind.

* Das Vorhandensein mehrerer wiederholter Felder kann zu einer Explosion der Anzahl erzeugter Zeilen führen.

Als Beispiel werten wir das die MongoDB-Beispieldatensammlung „Restaurant“ aus, die im nicht-relationalen JSON-Format gespeichert ist. Jedes Restaurant verfügt über geschachtelte Adressfelder sowie ein Array von Schulnoten, die an verschiedenen Tagen vergeben wurden. In der Abbildung unten wird ein typisches Restaurant mit geschachtelter Adresse und geschachtelten-wiederholten Schulnoten dargestellt.

![MongoDB-Vereinfachung](../../relational-databases/polybase/media/mongo-flattening.png "MongoDB-Vereinfachung für Restaurant")

Die Objektadresse wird wie unten dargestellt vereinfacht:

* Das geschachtelte Feld „restaurant.address.building“ wird zu „restaurant.address_building“.
* Das geschachtelte Feld „restaurant.address.coord“ wird zu „restaurant.address_coord“.
* Das geschachtelte Feld „restaurant.address.street“ wird zu „restaurant.address_street“.
* Das geschachtelte Feld „restaurant.address.zipcode“ wird zu „restaurant.address_zipcode“.

Die Arraynoten werden wie unten dargestellt vereinfacht:
| grades_date | grades_grade  | games_score | 
| ------------- | ------------------------- | -------------- |
|1393804800000 |Ein |2|
|1378857600000|Ein |6|
|135898560000 |Ein |10|
|1322006400000|Ein |9|
|1299715200000 |B |14|

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie in der [Übersicht zu SQL Server-PolyBase](polybase-guide.md).
