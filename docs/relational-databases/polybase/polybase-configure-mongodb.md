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
ms.openlocfilehash: 68fb5c69d30e9ba30f27bcd23347ed5543c7e792
ms.sourcegitcommit: f62f70298651d6223fa5d215b6a7a0d2ffecbd0d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "51947585"
---
# <a name="configure-polybase-to-access-external-data-in-mongodb"></a>Konfigurieren von PolyBase für den Zugriff auf externe Daten in MongoDB

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie PolyBase in einer SQL Server-Instanz verwenden, um externe Daten in MongoDB abzufragen.

## <a name="prerequisites"></a>Voraussetzungen

Wenn Sie PolyBase nicht installiert haben, finden Sie weitere Informationen unter [PolyBase installation (Installieren von PolyBase)](polybase-installation.md).

## <a name="configure-an-external-table"></a>Konfigurieren einer externen Tabelle

Um die Daten einer MongoDB-Datenquelle abzufragen, müssen Sie externe Tabellen zum Referenzieren der externen Daten erstellen. Dieser Abschnitt enthält Beispielcode zum Erstellen dieser externen Tabellen.

In diesem Abschnitt werden folgende Objekte erstellt:

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

1.   Erstellen Sie datenbankweit gültige Anmeldeinformationen für den Zugriff auf die MongoDB-Quelle.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL credential_name 
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1.  Erstellen Sie mit [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) eine externe Datenquelle.

     ```sql
     /*  LOCATION: Location string should be of format '<type>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH (
    LOCATION = mongodb://<server>[:<port>],
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = credential_name
    );
     ```

1.  Erstellen Sie mit [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) externe Tabellen, welche die im externen MongoDB-System gespeicherten Daten repräsentieren.

     ```sql
     /*  LOCATION: MongoDB table/view in '<database_name>.<schema_name>.<object_name>' format
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE customers(
     [O_ORDERKEY] DECIMAL(38) NOT NULL,
     [O_CUSTKEY] DECIMAL(38) NOT NULL,
     [O_ORDERSTATUS] CHAR COLLATE Latin1_General_BIN NOT NULL,
     [O_TOTALPRICE] DECIMAL(15,2) NOT NULL,
     [O_ORDERDATE] DATETIME2(0) NOT NULL,
     [O_COMMENT] VARCHAR(79) COLLATE Latin1_General_BIN NOT NULL
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


## <a name="flattening"></a>Vereinfachen
 Die Vereinfachung (Flattening) ist für geschachtelte und wiederholte Daten aus MongoDB-Dokumentsammlungen aktiviert. Der Benutzer muss `create an external table` aktivieren und ein relationales Schema über MongoDB-Dokumentsammlungen explizit angeben, die möglicherweise geschachtelte und/oder wiederholte Daten besitzen. In zukünftigen Meilensteinen wird die automatische Schemaerkennung über MongoDB-Dokumentsammlungen aktiviert.
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

## <a name="cosmos-db-connection"></a>Cosmos DB-Verbindung

Mithilfe der Cosmos DB-API und des PolyBase-Connectors für MongoDB können Sie eine externe Tabelle einer **Cosmos DB-Instanz** erstellen. Führen Sie dazu die oben genannten Schritte aus. Stellen Sie sicher, dass die datenbankweit gültigen Anmeldeinformationen, die Serveradresse, der Port und die Standortzeichenabfolge die des Cosmos DB-Servers widerspiegeln. 

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PolyBase finden Sie in der [Übersicht zu SQL Server-PolyBase](polybase-guide.md).
