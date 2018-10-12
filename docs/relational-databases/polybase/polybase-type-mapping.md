---
title: Typzuordnung mit PolyBase | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9839c46f477fe31d29214eed10dce0d673c9fd00
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732603"
---
# <a name="type-mapping-with-polybase"></a>Typzuordnung mit PolyBase

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die Zuordnung zwischen externen PolyBase-Datenquellen und SQL Server. Sie können diese Informationen verwenden, um externe Tabellen mit dem Transact-SQL-Befehl [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) richtig zu definieren.

## <a name="overview"></a>Übersicht

Beim Erstellen einer externen Tabelle mit PolyBase müssen die Spaltendefinitionen, einschließlich der Datentypen und die Anzahl der Spalten mit den Daten in externen Dateien übereinstimmen. Wenn ein Konflikt besteht, werden die Zeilen der Datei beim Abfragen der tatsächlichen Daten zurückgewiesen.  
  
Für externe Tabellen, die auf Dateien in externen Datenquellen verweisen, müssen die Spalten- und Typdefinitionen dem genauen Schema der externen Datei zugeordnet werden. Beim Definieren von Datentypen, die auf Daten verweisen, die in Hadoop/Hive gespeichert sind, verwenden Sie die folgenden Zuordnungen zwischen Datentypen von SQL und Hive und wandeln Sie den Typ in einen SQL-Datentyp um, wenn Sie daraus auswählen. Die Typen umfassen alle Versionen von Hive, sofern nicht anders angegeben.

> [!NOTE]  
> SQL Server unterstützt den Datenwert *unendlich* von Hive nicht in beliebigen Konvertierungen. PolyBase schlägt mit einem Datentypkonvertierungsfehler fehl.

## <a name="hadoop-type-mapping-reference"></a>Hadoop-Typzuordnungsverweis

| SQL-Datentyp | .NET-Datentyp            | Hive-Datentyp | Hadoop/Java-Datentyp | Kommentare                       |
| ------------- | ------------------------- | -------------- | --------------------- | ------------------------------ |
| TINYINT       | Byte                      | TINYINT        | ByteWritable          | Nur für unsignierte Zahlen.     |
| SMALLINT      | Int16                     | SMALLINT       | ShortWritable         |
| ssNoversion           | Int32                     | ssNoversion            | IntWritable           |
| BIGINT        | Int64                     | BIGINT         | LongWritable          |
| bit           | Boolean                   | boolean        | BooleanWritable       |
| FLOAT         | Double                    | double         | DoubleWritable        |
| REAL          | Single                    | FLOAT          | FloatWritable         |
| money         | Decimal                   | double         | DoubleWritable        |
| SMALLMONEY    | Decimal                   | double         | DoubleWritable        |
| NCHAR         | Zeichenfolge<br /><br /> Char[] | Zeichenfolge         | text                  |
| NVARCHAR      | Zeichenfolge<br /><br /> Char[] | Zeichenfolge         | Textmodus                  |
| char          | Zeichenfolge<br /><br /> Char[] | Zeichenfolge         | Textmodus                  |
| varchar       | Zeichenfolge<br /><br /> Char[] | Zeichenfolge         | Textmodus                  |
| BINARY        | Byte[]                    | BINARY         | BytesWritable         | Gilt für Hive 0.8 und höher. |
| varbinary     | Byte[]                    | BINARY         | BytesWritable         | Gilt für Hive 0.8 und höher. |
| date          | datetime                  | timestamp      | TimestampWritable     |
| smalldatetime | datetime                  | timestamp      | TimestampWritable     |
| datetime2     | datetime                  | timestamp      | TimestampWritable     |
| DATETIME      | datetime                  | timestamp      | TimestampWritable     |
| Uhrzeit          | TimeSpan                  | timestamp      | TimestampWritable     |
| Decimal       | Decimal                   | Decimal        | BigDecimalWritable    | Gilt für Hive 0.11 und höher. |

<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

## <a name="oracle-type-mapping-reference"></a>Oracle-Typzuordnungsverweis

| Oracle-Datentyp              | SQL Server-Typ |
| ----------------------------- | --------------- |
| float                         | float           |
| Decimal                       | Decimal         |
| int                           | int             |
| Long                          | Ntext           |
| Binary Float                  | Real            |
| Char                          | Nchar           |
| Varchar2                      | nvarchar        |
| Raw                           | Varbinary       |
| Long Raw                      | image           |
| Bfile                         | image           |
| Blob                          | image           |
| Clob                          | image           |
| Rowid                         | Varchar         |
| date                          | Datetime2       |
| Timestamp                     | Datetime2       |
| Timestamp with local timezone | Datetime2       |

### <a name="type-mismatch-float"></a>Typenkonflikt (Float)

Oracle unterstützt eine Gleitkommagenauigkeit von 126, was niedriger ist als die von SQL-Server (53). Daher kann **Float (1-53)** direkt zugeordnet werden, aber darüber hinaus kommt es zu Datenverlust durch Abschneidung.

### <a name="type-mismatch-character-types"></a>Typenkonflikt (Zeichentypen)

Für Typen wie z.B. **Long** und **Bfile** unterstützt Oracle eine Datentypgröße von 4 GB. SQL Server unterstützt eine Größe von 2 GB. Ebenso kann Oracle für die Orakeldatentypen **Blob** und **clob** bis zu 128 TB unterstützen, während SQL Server bei **LONGVARBINARY** oder **WLONGVARBINARY** nicht mehr als 2 GB unterstützen kann. Zuordnungstypen mit einer Datentypgröße von mehr als 2 GB können zu einer Datenabschneidung führen.  

### <a name="type-mismatch-timestamp"></a>Typenkonflikt (Timestamp)

**Timestamp** und **Timestamp with local timezone** unterstützt eine Sekundenbruchteil-Genauigkeit von 9. SQL Server unterstützt bei DateTime2 eine Sekundenbruchteil-Genauigkeit von 7.

Simba ordnet **Date**, **Timestamp** und **Timestamp with local zone** dem ODBC-Typ **SQL_TIMESTAMP** und dem SQL Server-Typ **Timestamp** zu. **Timestamp** ist eine automatisch generierte eindeutige Zeilen-ID. Im Idealfall sollte **SQL_TIMESTAMP** SQL Server-Typ **DateTime/DateTime2** oder den Oracle-Datentypen **Date**, **Timestamp** und **Timestamp mit local zone** dem ODBC-Typ **SQL_TYPE_TIMESTAMP** zugeordnet werden.

### <a name="driver-configuration-option"></a>Option für die Treiberkonfiguration

Die Standardpuffergröße für **Long/LOB**-Spalten ist 1024 KB (konfigurierbar).

## <a name="mongo-type-mapping-reference"></a>Mongo-Typzuordnungsverweis

| BSON-Datentyp     | SQL Server-Typ |
| ------------------ | --------------- |
| Double             | float           |
| Zeichenfolge             | nvarchar        |
| Objekt             |
| Array              |
| Binärdaten        | nvarchar        |
| ObjectID          | nvarchar        |
| Boolean            | bit             |
| date               | Datetime2       |
| 32-bit integer     | int             |
| Timestamp          | nvarchar        |
| 64-bit integer     | BigInt          |
| DBPointer          | nvarchar        |
| Javascript         | nvarchar        |
| Max Key            | nvarchar        |
| Min Key            | nvarchar        |
| Symbol             | nvarchar        |
| Regular Expression | nvarchar        |
| Undefined/NULL     | nvarchar        |

### <a name="javascript-with-scope"></a>JavaScript (mit Gültigkeitsbereich)

Der Treiber gibt den Wert als eine Zeichenfolge mit „Nicht unterstütztes JavaScript mit Gültigkeitsbereich“ zurück.

### <a name="type-mismatch-string"></a>Typenkonflikt (string)

MongoDB-Zeichenfolgen werden in den **SQL_WVARCHAR**-Typ mit einer Spaltenstandardgröße von 255 konvertiert. Die Spaltengröße kann im Rahmen der Treiberkonfiguration angepasst werden. Obwohl konfigurierbar, unterstützt **SQL_WVARCHAR** oder der SQL Server-Typ **Varchar** nur maximal 2 GB, während MongoDB Daten bis zu 4 GB speichern kann. Dies kann zu abgeschnittenen Daten führen.

### <a name="mongodb-driver-options"></a>MongoDB-Treiberoptionen

- **Enable double buffering**: Standardmäßig aktiviert.
- **Documents to fetch per block**: Standard 4096.
- **Expose strings as SQL_WVARCHAR**: Standardmäßig ausgewählt. Wenn keine Auswahl getroffen ist, werden die Zeichenfolgen als SQL_VARCHAR verfügbar gemacht.
- **String column size**: Standard 255.
- **Expose Binary as SQL_LONGVARBINARY**: Standardmäßig ausgewählt. Wenn keine Auswahl getroffen wird, wird „Binary“ als SQL_VARBINARY verfügbar gemacht.
- **Binary Column Size**: Standard 32767.
- **Enable passdown**: Standardmäßig ausgewählt.

### <a name="schema-related-driver-configurations"></a>Schemabezogene Treiberkonfigurationen

- **LoadMetadataTable**: Standardmäßig aus der Datenbank. Fordert den Treiber auf, die Schemadefinition aus der angegeben JSON-Datei zu laden.
- **LocalMetadataFile**: Beim Auslesen aus einer Datei muss der vollständige Pfad angegeben werden.
- **Stichprobenmethode**:  
  - **default forward**: Treiber prüft die Daten aus dem letzten Datensatz.
  - **backward**: Treiber prüft die Daten aus dem letzten Datensatz.
- **SamplingLimit**: Standardmäßig 100 (maximale Anzahl von Datensätzen, die der Treiber abfragen kann, um eine temporäre Schemadefinition zu generieren). Wenn 0 festgelegt wurde, prüft der Treiber jedes Dokument.
- **SamplingStepSize**: Standardmäßig 1 (Intervall, in dem der Treiber beim Prüfen der Datenbank die Datensätze abliest, um eine temporäre Schemadefinition zu erzeugen). Wenn beispielsweise 2 festgelegt ist, wird jeder 2. Datensatz in der Datenbank geprüft.

## <a name="teradata-type-mapping-reference"></a>Teradata-Typzuordnungsverweis

| Teradata-Datentyp               | SQL Server-Typ |
| -------------------------------- | --------------- |
| int                              | int             |
| Small Int                        | SmallInt        |
| Big Int                          | BigInt          |
| Byte Int                         | TinyInt         |
| Decimal                          | Decimal         |
| float                            | float           |
| Byte                             | Binär (Binary)          |
| Varbyte                          | Varbinary       |
| Blob                             | image           |
| Char                             | Nchar           |
| Clob                             | Ntext           |
| Varchar                          | nvarchar        |
| Graphic                          | Nchar           |
| JSON                             | Ntext           |
| Vargraphic                       | nvarchar        |
| date                             | date            |
| Uhrzeit                             | Uhrzeit            |
| Time with Time Zone              | Uhrzeit            |
| Timestamp                        | Datetime2       |
| Interval Year                    |
| Interval year to month           |
| Interval Month                   |
| Interval Day                     |
| Interval Day to Hour             |
| Interval Day to Minute           |
| Interval Day to Second           |
| Interval Hour                    |
| Interval Hour to Minute          |
| Interval Hour to Second          |
| Interval Minute                  |
| Interval Minute to Second        |
| Interval Second                  |
| Period (DATE)                    |
| Period (TIME)                    |
| Period (TIME with Timezone)      |
| Period (Timestamp)               |
| Period (Timestamp with Timezone) |

### <a name="period-data-type"></a>Period-Datentyp

Der **Period**-Datentyp stellt eine Dauer dar, die durch eine Anfangs- und Endbindung gekennzeichnet ist. Im Wesentlichen ist es ein Tupel. Es gibt keinen entsprechenden SQL Server-Typ für **Period**.

### <a name="time-with-time-zone-and-timestamp"></a>Time with Time Zone and Timestamp

**Time with Time Zone** und **Timestamp** enthalten den Zeitzonenversatz, der während der Übersetzung verloren geht. Dies kann durch die Zuordnung von **SQL_Type_Time/SQL_Type_Timestamp** zu **datetimeoffset** anstatt zu **Time/DateTime2** behoben werden.

### <a name="byteint"></a>ByteInt

Simba ordnet Teradata-Typ **ByteInt**, der Werte zwischen 0-255 aufnehmen kann, **TinyInt** zu, der Werte zwischen -127 und 127 aufnehmen kann. Dies kann zu einem Abschneidevorgang führen.  

### <a name="clob"></a>CLOB

Der **CLOB**-Datentyp mit **LATIN**-Zeichensatz sollten 2097088000 Zeichen annehmen können. Bei über 1073741823 wird die Größe des Puffers allerdings negativ.  

### <a name="driver-configuration-options"></a>Option für die Treiberkonfiguration

- **DATE**-Daten für **TIMESTAMP**-Parameter verwenden.
- Benutzerdefinierten Katalogmodus für 2.X-Anwendungen aktivieren.
- Leere Zeichenfolge in Spalte **CREATE_PARAMS** für **SQL_TIMESTAMP** zurückgegeben.
- Max. **CHAR/VARCHAR**-Länge als 32 K zurückgeben.

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Verwendung finden Sie im Transact-SQL-Referenzartikel für [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
