---
title: COPY INTO – Transact-SQL (Vorschau)
titleSuffix: (SQL Data Warehouse) - SQL Server
description: Verwenden Sie die COPY-Anweisung in Azure SQL Data Warehouse zum Laden von externen Speicherkonten.
ms.date: 11/07/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COPY_TSQL
- COPY INTO
- COPY
- LOAD
dev_langs:
- TSQL
author: kevinvngo
ms.author: kevin
monikerRange: =sqlallproducts-allversions||=azure-sqldw-latest
ms.openlocfilehash: fc26cc0862c7dfb02276738d9424b860d98644e7
ms.sourcegitcommit: 619917a0f91c8f1d9112ae6ad9cdd7a46a74f717
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73882414"
---
# <a name="copy-transact-sql-preview"></a>COPY – Transact-SQL (Vorschau)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

In diesem Artikel erfahren Sie, wie Sie die COPY-Anweisung in Azure SQL Data Warehouse zum Laden von externen Speicherkonten verwenden. Die COPY-Anweisung bietet die größtmögliche Flexibilität für die Datenerfassung mit hohem Durchsatz in SQL Data Warehouse.

> [!NOTE]  
> Die COPY-Anweisung befindet sich zurzeit in der Public Preview.

## <a name="syntax"></a>Syntax  

```
COPY INTO [schema.]table_name
[(Column_list)] 
FROM ‘<external_location>’ [,...n]
WITH  
 ( 
 [FILE_TYPE = {'CSV' | 'PARQUET' | 'ORC'} ]
 [,FILE_FORMAT = EXTERNAL FILE FORMAT OBJECT ]  
 [,CREDENTIAL = (AZURE CREDENTIAL) ]
 [,ERRORFILE = '[http(s)://storageaccount/container]/errorfile_directory[/]] 
 [,ERRORFILE_CREDENTIAL = (AZURE CREDENTIAL) ]
 [,MAXERRORS = max_errors ] 
 [,COMPRESSION = { 'Gzip' | 'DefaultCodec'|’Snappy’}] 
 [,FIELDQUOTE = ‘string_delimiter’] 
 [,FIELDTERMINATOR =  ‘field_terminator’]  
 [,ROWTERMINATOR = ‘row_terminator’]
 [,FIRSTROW = first_row]
 [,DATEFORMAT = ‘date_format’] 
 [,ENCODING = {'UTF8'|'UTF16'}] 
 [,IDENTITY_INSERT = {‘ON’ | ‘OFF’}]
)
```

## <a name="arguments"></a>Argumente  

*schema_name*  
Ist optional, wenn das Standardschema des Benutzers, der den Vorgang ausführt, das Schema der angegebenen Tabelle ist. Wenn *schema* nicht angegeben wird und das Standardschema des Benutzers, der den COPY-Vorgang ausführt, sich von der angegebenen Tabelle unterscheidet, wird der COPY-Vorgang abgebrochen und eine Fehlermeldung zurückgegeben.  

*table_name*  
Der Name der Tabelle, in die mit COPY Daten kopiert werden sollen. Bei der Zieltabelle kann es sich um eine temporäre oder permanente Tabelle handeln.

*(Spaltenliste)*  
Eine optionale Liste mit einer oder mehreren Spalten, mit denen Quelldatenfelder zum Laden von Daten Zieltabellenspalten zugeordnet werden. *column_list* muss in Klammern eingeschlossen und durch ein Trennzeichen getrennt werden. Die Spaltenliste liegt im folgenden Format vor:

[(Spaltenname [Standardwert] [Feldnummer] [,...n])]

- *Spaltenname*: Der Name der Spalte in der Zieltabelle.
- *Standardwert*: Der Standardwert, durch den alle NULL-Werte in der Eingabedatei ersetzt werden. Der Standardwert gilt für alle Dateiformate. Beim COPY-Vorgang wird versucht, NULL aus der Eingabedatei zu laden, wenn eine Spalte aus der Spaltenliste ausgelassen wird oder ein leeres Eingabedateifeld vorhanden ist.
- *Feldnummer*: Die Feldnummer der Eingabedatei, die dem Namen der Zielspalte zugeordnet wird.
- Die Feldindizierung beginnt bei 1.

Wenn keine Spaltenliste angegeben wird, ordnet COPY die Spalten auf Grundlage der Quell- und Zielordnung zu: Eingabefeld 1 wird Zielspalte 1 zugeordnet, Feld 2 wird Spalte 2 zugeordnet usw.

*Externe Speicherorte*</br>
Speicherorte, wo die Dateien bereitgestellt werden, die die Daten enthalten. Derzeit werden Azure Data Lake Storage (ADLS) Gen2 und Azure Blob Storage unterstützt:

- *Externer Speicherort* für Blob Storage: https://<account>.blob.core.windows.net/<container>/<path>
- *Externer Speicherort* für ADLS Gen2: https://<account>. dfs.core.windows.net/<container>/<path>

> [!NOTE]  
> Der Blobendpunkt ist nur der Abwärtskompatibilität wegen für ADLS Gen2 verfügbar. Verwenden Sie den **dfs**-Endpunkt für ADLS Gen2, um eine optimale Leistung zu erzielen.

- *Konto*: Der Speicherkontoname

- *Container*: Der Blobcontainername

- *Pfad*: Der Ordner- oder Dateipfad für die Daten. Der Speicherort beginnt im Container. Wenn ein Ordner angegeben wird, ruft COPY alle Dateien aus dem Ordner und seinen Unterordnern ab. COPY ignoriert ausgeblendete Ordner, und es werden keine Dateien zurückgegeben, die mit einem Unterstrich (_) oder einem Punkt (.) beginnen, es sei denn, sie werden explizit im Pfad angegeben. Dieses Verhalten gilt auch dann, wenn ein Pfad mit einem Platzhalter angegeben wird.

Platzhalter können im Pfad enthalten sein, wobei gilt:

- Bei der Pfadnamensübereinstimmung mit dem Platzhalter wird Groß-/Kleinschreibung beachtet
- Platzhalter können mithilfe des umgekehrten Schrägstrichs (\\) mit Escapezeichen versehen werden.
- Die Platzhaltererweiterung wird rekursiv angewendet. Alle CSV-Dateien unter Customer1 (einschließlich der Unterverzeichnisse von Customer1) werden z. B. im folgenden Beispiel geladen: „Account/Container/Customer1/*. csv“

> [!NOTE]  
> Um die optimale Leistung zu erzielen, sollten Sie keine Platzhalter angeben, die auf eine größere Anzahl von Dateien erweitert werden. Listen Sie nach Möglichkeit mehrere Dateispeicherorte auf, anstatt Platzhalter anzugeben.

Es können nur mehrere Dateispeicherorte aus demselben Speicherkonto und Container über eine durch Trennzeichen getrennte Liste angegeben werden, wie z. B.:

- ‘ https://<account>.blob.core.windows.net/<container>/<path>’, ‘ https://<account>.blob.core.windows.net/<container>/<path>’…

*FILE_TYPE = { ‘CSV’ | ‘PARQUET’ | ‘ORC’ }*</br>
*FILE_TYPE* gibt das Format der externen Daten an.

- CSV: Gibt eine CSV-Datei an, die dem Standard [RFC 4180](https://tools.ietf.org/html/rfc4180) entspricht.
- PARQUET: Gibt ein Parquet-Format an.
- ORC: Gibt ein ORC-Format (ORC = Optimized Row Columnar) an.

>[!NOTE]  
> Der Dateityp „durch Trennzeichen getrennter Text“ in Polybase wird durch das Dateiformat „CSV“ ersetzt, in dem das standardmäßige Kommatrennzeichen über den FIELDTERMINATOR-Parameter konfiguriert werden kann. 

*FILE_FORMAT = Formatname_der_externen_Datei*</br>
*FILE_FORMAT* gilt nur für Parquet- und ORC-Dateien und gibt den Namen des externen Dateiformatobjekts an, das den Dateityp und die Komprimierungsmethode für die externen Daten enthält. Verwenden Sie zum Erstellen eines externen Dateiformats [CREATE EXTERNAL FILE FORMAT](create-external-file-format-transact-sql.md?view=azure-sqldw-latest).

*CREDENTIAL (IDENTITY = ‘’, SECRET = ‘’)*</br>
*CREDENTIAL* gibt den Authentifizierungsmechanismus für den Zugriff auf das externe Speicherkonto an. Authentifizierungsmethoden sind:

|                          |                CSV                |              Parquet              |                ORC                |
| :----------------------: | :-------------------------------: | :-------------------------------: | :-------------------------------: |
|  **Azure Blob Storage**  | SAS/MSI/SERVICE PRINCIPAL/KEY/AAD |              SAS/KEY              |              SAS/KEY              |
| **Azure Data Lake Gen2** | SAS/MSI/SERVICE PRINCIPAL/KEY/AAD | SAS/MSI/SERVICE PRINCIPAL/KEY/AAD | SAS/MSI/SERVICE PRINCIPAL/KEY/AAD |

Bei der Authentifizierung mit AAD oder bei einem öffentlichen Speicherkonto muss CREDENTIAL nicht angegeben werden. 

- Authentifizieren mit Shared Access Signature (SAS) *IDENTITY: Eine Konstante mit dem Wert von „Shared Access Signature“* 
  *SECRET: Die * [*Signatur für den gemeinsamen Zugriff*](/azure/storage/common/storage-sas-overview#what-is-a-shared-access-signature) *ermöglicht den delegierten Zugriff auf Ressourcen in Ihrem Speicherkonto.*
  Erforderliche Mindestberechtigungen: READ und LIST

- Authentifizieren mit [*Dienstprinzipalen*](/azure/sql-data-warehouse/sql-data-warehouse-load-from-azure-data-lake-store#create-a-credential)

  *IDENTITY: <ClientID>@<OAuth_2.0_Tokenendpunkt>* 
  *SECRET: AAD-Anwendungsdienstprinzipal-Schlüssel* Mindestens erforderliche RBAC-Rollen: Mitwirkender von Speicherblobdaten, Besitzer von Speicherblobdaten oder Leser von Speicherblobdaten

  > [!NOTE]  
  > Verwenden des OAuth 2.0-Tokenendpunkts **V1**

- Authentifizieren mit dem Speicherkontoschlüssel *IDENTITY: Eine Konstante mit dem Wert von „Speicherkontoschlüssel“* 
  *SECRET: Speicherkontoschlüssel*
  
- Authentifizieren mit [verwalteter Identität](/azure/sql-data-warehouse/load-data-from-azure-blob-storage-using-polybase#authenticate-using-managed-identities-to-load-optional) (VNET-Dienstendpunkte) *IDENTITY: Eine Konstante mit dem Wert von „verwalteter Identität“* Mindestens erforderliche RBAC-Rollen: Mitwirkender von Speicherblobdaten, Besitzer von Speicherblobdaten oder Leser von Speicherblobdaten für den bei AAD registrierten SQL-Datenbank-Server 
  
- Authentifizieren mit einem AAD-Benutzer *CREDENTIAL ist nicht erforderlich* Mindestens erforderliche RBAC-Rollen: Mitwirkender von Speicherblobdaten, Besitzer von Speicherblobdaten oder Leser von Speicherblobdaten für den AAD-Benutzer

*ERRORFILE = Verzeichnisspeicherort*</br>
*ERRORFILE* gilt nur für CSV. Gibt in der COPY-Anweisung das Verzeichnis an, in das die abgelehnten Zeilen und die entsprechende Fehlerdatei geschrieben werden sollen. Der vollständige Pfad vom Speicherkonto oder der relative Pfad zum Container kann angegeben werden. Ist der angegebene Pfad nicht vorhanden, wird ein Pfad für Sie erstellt. Es wird ein untergeordnetes Verzeichnis mit dem Namen „_rejectedrows“ erstellt. Mit dem „_ “-Zeichen wird sichergestellt, dass das Verzeichnis für andere Datenverarbeitungsvorgänge übergangen wird, es sei denn, es ist explizit im LOCATION-Parameter angegeben. 

In diesem Verzeichnis befindet sich ein Ordner, der ausgehend von der Zeit der Lastübermittlung im Format „JahrMonatTag-StundeMinuteSekunde“ erstellt wurde (z.B. 20180330-173205). In diesen Ordner werden zwei Dateitypen geschrieben: die Ursachendatei (Fehler) und die Datendatei (Zeile), denen jeweils queryID, distributionID und eine Datei-GUID vorangestellt werden. Da die Daten und die Ursache in getrennten Dateien gespeichert sind, haben die zugehörigen Dateien ein entsprechendes Präfix.

Wenn ERRORFILE den vollständigen Pfad des Speicherkontos definiert hat, wird ERRORFILE_CREDENTIAL zum Herstellen einer Verbindung mit dem Speicher verwendet. Andernfalls wird der für CREDENTIAL angegebene Wert verwendet.

*ERRORFILE_CREDENTIAL = (IDENTITY= ‘’, SECRET = ‘’)*</br>
*ERRORFILE_CREDENTIAL* gilt nur für CSV-Dateien. Unterstützte Datenquellen und Authentifizierungsmethoden sind:

- Azure Blob Storage – SAS/SERVICE PRINCIPAL/KEY/AAD
- Azure Data Lake Gen2 – SAS/MSI/SERVICE PRINCIPAL/KEY/AAD
  
- Authentifizieren mit Shared Access Signatures (SAS)
  - *IDENTITY: Eine Konstante mit dem Wert von „Shared Access Signature“*
  - *SECRET: Die* [*Signatur für den gemeinsamen Zugriff*](/azure/storage/common/storage-dotnet-shared-access-signature-part-1#what-is-a-shared-access-signature) *ermöglicht den delegierten Zugriff auf Ressourcen in Ihrem Speicherkonto.*
  - Erforderliche Mindestberechtigungen: READ, LIST, WRITE, CREATE, DELETE
  
- Authentifizieren mit [*Dienstprinzipalen*](/azure/sql-data-warehouse/sql-data-warehouse-load-from-azure-data-lake-store#create-a-credential)
  - *IDENTITY: <ClientID>@<OAuth_2.0_Tokenendpunkt>*
  - *SECRET: AAD-Anwendungsdienstprinzipal-Schlüssel*
  - Mindestens erforderliche RBAC-Rollen: Mitwirkender von Speicherblobdaten oder Besitzer von Speicherblobdaten
  
> [!NOTE]  
> Verwenden des OAuth 2.0-Tokenendpunkts **V1**

- Authentifizieren mit dem Speicherkontoschlüssel
  - *IDENTITY: Eine Konstante mit dem Wert von „Speicherkontoschlüssel“*
  - *SECRET: Speicherkontoschlüssel*
  
- Authentifizieren mit [verwalteter Identität](/azure/sql-data-warehouse/load-data-from-azure-blob-storage-using-polybase#authenticate-using-managed-identities-to-load-optional) (VNET-Dienstendpunkte)
  - *IDENTITY: Eine Konstante mit dem Wert von „Verwalteter Identität“*
  - Mindestens erforderliche RBAC-Rollen: Mitwirkender von Speicherblobdaten oder Besitzer von Speicherblobdaten für den bei AAD registrierten SQL-Datenbank-Server
  
- Authentifizieren mit einem AAD-Benutzer
  - *CREDENTIAL ist nicht erforderlich*
  - Mindestens erforderliche RBAC-Rollen: Mitwirkender von Speicherblobdaten oder Besitzer von Speicherblobdaten für den AAD-Benutzer

> [!NOTE]  
> Wenn Sie das gleiche Speicherkonto für die ERRORFILE-Datei verwenden und den ERRORFILE-Pfad relativ zum Stamm des Containers angeben, müssen Sie ERROR_CREDENTIAL nicht angeben.

*MAXERRORS = maximale_Fehlerzahl*</br>
*MAXERRORS* gibt die maximale Anzahl von abgelehnten Zeilen an, die in den geladenen Daten zulässig sind, bevor der COPY-Vorgang abgebrochen wird. Jede Zeile, die beim COPY-Vorgang nicht importiert werden kann, wird ignoriert und zählt dabei als ein Fehler. Wenn „max_errors“ nicht angegeben ist, wird der Standardwert 0 verwendet.

*COMPRESSION = { 'DefaultCodec '| ’Snappy’ | ‘GZIP’ | ‘NONE’}*</br>
*COMPRESSION* ist optional und gibt die Datenkomprimierungsmethode für die externen Daten an.

- CSV unterstützt GZIP.
- Parquet unterstützt GZIP und Snappy.
- ORC unterstützt DefaultCodec und Snappy.
- Zlib ist die Standardkomprimierung für ORC.

Mit dem COPY-Befehl wird der Komprimierungstyp automatisch auf Grundlage der Dateierweiterung erkannt, wenn dieser Parameter nicht angegeben ist:

- .gz – **GZIP**
- .snappy – **Snappy**
- .deflate – **DefaultCodec**

 *FIELDQUOTE = 'Feldquote'*</br>
*FIELDQUOTE* gilt für CSV und gibt ein einzelnes Zeichen an, das als Anführungszeichen (Zeichenfolgen-Trennzeichen) in der CSV-Datei verwendet wird. Wenn dies nicht angegeben ist, wird das Anführungszeichen (") so verwendet, wie es im Standard RFC 4180 definiert ist. Erweiterte ASCII-Zeichen werden bei UTF-8 für FIELDQUOTE nicht unterstützt.

> [!NOTE]  
> FIELDQUOTE-Zeichen werden in Zeichenfolgenspalten mit Escapezeichen versehen, wenn ein doppeltes FIELDQUOTE-Zeichen (Trennzeichen) vorhanden ist. 

*FIELDTERMINATOR = 'Feldabschlusszeichen'*</br>
*FIELDTERMINATOR* Gilt nur für CSV. Gibt das Feldabschlusszeichen an, das in der CSV-Datei verwendet wird. Das Feldabschlusszeichen kann mehrere Zeichen aufweisen. Das Standard-Feldabschlusszeichen ist ein (,).
Weitere Informationen finden Sie unter [Angeben von Feld- und Zeilenabschlusszeichen (SQL Server)](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md?view=sql-server-2017).

ROW TERMINATOR = 'Zeilenabschlusszeichen'</br>
*ROW TERMINATOR* gilt nur für CSV. Gibt das Zeilenabschlusszeichen an, das in der CSV-Datei verwendet wird. Das Zeilenabschlusszeichen kann mehrere Zeichen aufweisen. Standardmäßig ist das Zeilenabschlusszeichen „\r\n“. 

Der COPY-Befehl stellt beim Angeben von „\n“ (Zeilenumbruch) das \r-Zeichen voran, woraus „\r\n“ resultiert. Um nur das Zeichen „\n“ anzugeben, verwenden Sie die Hexadezimalschreibweise (0x0A). Geben Sie bei der Angabe von Zeilenabschlusszeichen aus mehreren Zeichen in Hexadezimalschreibweise nicht „0x“ zwischen den einzelnen Zeichen an.

Weitere Anleitungen zum Angeben von Zeilenabschlusszeichen finden Sie in der folgenden [Dokumentation](https://docs.microsoft.com/sql/relational-databases/import-export/specify-field-and-row-terminators-sql-server?view=sql-server-2017#using-row-terminators).

*FIRSTROW  = Erste_Zeile_int*</br>
*FIRSTROW* gilt für CSV und gibt die Zeilennummer an, die zuerst in allen Dateien für den COPY-Befehl gelesen wird. Die Werte beginnen mit 1, dem Standardwert. Wenn der Wert auf 2 festgelegt ist, wird die erste Zeile in jeder Datei (Kopfzeile) beim Laden der Daten übersprungen. Zeilen werden basierend auf dem Vorhandensein von Zeilenabschlusszeichen übersprungen.

*DATEFORMAT = { ‘mdy’ | ‘dmy’ | ‘ymd’ | ‘ydm’ | ‘myd’ | ‘dym’ }*</br>
DATEFORMAT gilt nur für CSV und gibt das Datumsformat der Datumszuordnung zu SQL Server-Datumsformaten an. Eine Übersicht über alle Datums- und Uhrzeitdatentypen und zugehörigen Funktionen für Transact-SQL finden Sie unter [Datums- und Uhrzeitdatentypen und zugehörige Funktionen (Transact-SQL)](../functions/date-and-time-data-types-and-functions-transact-sql.md?view=sql-server-ver15). DATEFORMAT im COPY-Befehl hat Vorrang vor [auf Sitzungsebene konfiguriertem DATEFORMAT](set-dateformat-transact-sql.md?view=sql-server-ver15).

*ENCODING = ‘UTF8’ | ‘UTF16’*</br>
*ENCODING* gilt nur für CSV. Der Standardwert ist UTF8. Gibt den Datencodierungsstandard für die Dateien an, die vom COPY-Befehl geladen werden. 

*IDENTITY_INSERT = ‘ON’ | ‘OFF’*</br>
IDENTITY_INSERT gibt an, ob die Identitätswerte oder Werte in der importierten Datendatei für die Identitätsspalte verwendet werden sollen. Wenn IDENTITY_INSERT auf OFF gesetzt ist (Standard), werden die Identitätswerte für diese Spalte überprüft, aber nicht importiert. SQL DW weist automatisch eindeutige Werte auf Basis des Ausgangswerts und der inkrementellen Werte zu, die bei der Tabellenerstellung angegeben werden. Beachten Sie das folgende Verhalten beim COPY-Befehl:

- Wenn IDENTITY_INSERT auf OFF gesetzt ist und die Tabelle eine Identitätsspalte aufweist
  - Es muss eine Spaltenliste angegeben werden, die der Identitätsspalte kein Eingabefeld zuordnet.
- Wenn IDENTITY_INSERT auf ON gesetzt ist und die Tabelle eine Identitätsspalte aufweist
  - Wenn eine Spaltenliste übermittelt wird, muss sie der Identitätsspalte ein Eingabefeld zuordnen.
- Der Standardwert wird für die IDENTITY COLUMN in der Spaltenliste nicht unterstützt.
- IDENTITY_INSERT kann nur jeweils für eine Tabelle festgelegt werden.

### <a name="permissions"></a>Berechtigungen  

Der Benutzer, der den COPY-Befehl ausführt, muss über die folgenden Berechtigungen verfügen: 

- [ADMINISTER DATABASE BULK OPERATIONS](grant-database-permissions-transact-sql.md?view=azure-sqldw-latest#remarks)
- [INSERT](grant-database-permissions-transact-sql.md?view=azure-sqldw-latest#remarks)

Erfordert die Berechtigungen INSERT und ADMINISTER BULK OPERATIONS. In Azure SQL Data Warehouse sind INSERT- und ADMINISTER DATABASE BULK OPERATIONS-Berechtigungen erforderlich.

## <a name="examples"></a>Beispiele  

### <a name="a-load-from-a-public-storage-account"></a>A. Laden aus einem öffentlichen Speicherkonto

Das folgende Beispiel ist die einfachste Form des COPY-Befehls, bei der Daten aus einem öffentlichen Speicherkonto geladen werden. In diesem Beispiel entsprechen die Standardwerte der COPY-Anweisung dem Format der Zeilenelement-CSV-Datei.

```sql
COPY INTO dbo.[lineitem] FROM 'https://unsecureaccount.blob.core.windows.net/customerdatasets/folder1/lineitem.csv’
```

Die Standardwerte des COPY-Befehls lauten wie folgt:

- DATEFORMAT = DATEFORMAT (Datumsformat) der Sitzung 

- MAXERRORS = 0

- COMPRESSION Standard ist nicht komprimiert

- FIELDQUOTE = “” 

- FIELDTERMINATOR = “,” 

- ROWTERMINATOR = „\n“

> [!IMPORTANT]
> COPY behandelt „\n“ intern als „\r\n“. Weitere Informationen finden Sie im Abschnitt [ROWTERMINATOR]().

- FIRSTROW = 1

- ENCODING = „UTF8“

- FILE_TYPE = „CSV“

- IDENTITY_INSERT = „OFF“

### <a name="b-load-authenticating-via-share-access-signature-sas"></a>B. Laden der Authentifizierung über SAS (Share Access Signature)

Im folgenden Beispiel werden Dateien geladen, in denen der Zeilenvorschub als ein Zeilenabschlusszeichen verwendet wird, z. B. eine UNIX-Ausgabe. In diesem Beispiel wird zur Authentifizierung bei Azure Blob Storage auch ein SAS-Schlüssel verwendet.

```sql
COPY INTO test_1
FROM 'https://myaccount.blob.core.windows.net/myblobcontainer/folder1/'
WITH (
    FILE_TYPE = 'CSV',
    CREDENTIAL=(IDENTITY= 'Shared Access Signature', SECRET='<Your_SAS_Token>'),
    --CREDENTIAL should look something like this:
    --CREDENTIAL=(IDENTITY= 'Shared Access Signature', SECRET='?sv=2018-03-28&ss=bfqt&srt=sco&sp=rl&st=2016-10-17T20%3A14%3A55Z&se=2021-10-18T20%3A19%3A00Z&sig=IEoOdmeYnE9%2FKiJDSHFSYsz4AkNa%2F%2BTx61FuQ%2FfKHefqoBE%3D'),
    FIELDQUOTE = '"',
    FIELDTERMINATOR=';',
    ROWTERMINATOR='0X0A',
    ENCODING = 'UTF8',
    DATEFORMAT = 'ymd',
    MAXERRORS = 10,
    ERRORFILE = '/errorsfolder/',--path starting from the storage container
    IDENTITY_INSERT = ‘ON’
)
```

### <a name="c-load-with-a-column-list-with-default-values-authenticating-via-storage-account-key"></a>C. Laden mit einer Spaltenliste mit Standardwerten zur Authentifizierung über den Speicherkontoschlüssel

In diesem Beispiel werden Dateien mit Angabe einer Spaltenliste mit Standardwerten geladen. 

```sql
--Note when specifying the column list, input field numbers start from 1
COPY INTO test_1 (Col_one default 'myStringDefault' 1, Col_two default 1 3)
FROM 'https://myaccount.blob.core.windows.net/myblobcontainer/folder1/'
WITH (
    FILE_TYPE = 'CSV',
    CREDENTIAL=(IDENTITY= 'Storage Account Key', SECRET='<Your_Account_Key>'),
    --CREDENTIAL should look something like this:
    --CREDENTIAL=(IDENTITY= 'Storage Account Key', SECRET='x6RWv4It5F2msnjelv3H4DA80n0PQW0daPdw43jM0nyetx4c6CpDkdj3986DX5AHFMIf/YN4y6kkCnU8lb+Wx0Pj+6MDw=='),
    FIELDQUOTE = '"',
    FIELDTERMINATOR=',',
    ROWTERMINATOR='0x0A',
    ENCODING = 'UTF8',
    FIRSTROW = 2
)
```

### <a name="d-load-parquet-or-orc-using-existing-file-format-object"></a>D. Laden von Parquet oder ORC mithilfe eines vorhandenen Dateiformatobjekts

 In diesem Beispiel wird ein Platzhalter verwendet, um alle Parquet-Dateien in einem Ordner zu laden. 

```sql
COPY INTO test_parquet
FROM 'https://myaccount.blob.core.windows.net/myblobcontainer/folder1/*.parquet'
WITH (
    FILE_FORMAT = myFileFormat
    CREDENTIAL=(IDENTITY= 'Shared Access Signature', SECRET='<Your_SAS_Token>')
)
```

### <a name="e-load-specifying-wild-cards-and-multiple-files"></a>E. Laden mit Angabe von Platzhaltern und mehreren Dateien

```sql
COPY INTO t1
FROM 
'https://myaccount.blob.core.windows.net/myblobcontainer/folder0/*.txt', 
    'https://myaccount.blob.core.windows.net/myblobcontainer/folder1'
WITH ( 
    FILE_TYPE = 'CSV'
    CREDENTIAL=(IDENTITY= '<client_id>@<OAuth_2.0_Token_EndPoint>',SECRET='<key>'),
    FIELDTERMINATOR = '|'
)
```

## <a name="see-also"></a>Siehe auch  

 [Datenladestrategien für Azure SQL Data Warehouse](/azure/sql-data-warehouse/design-elt-data-loading>) 
