---
description: sp_describe_first_result_set (Transact-SQL)
title: sp_describe_first_result_set (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_first_result_set
- sp_describe_first_result_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_first_result_set
ms.assetid: f2355a75-3a8e-43e6-96ad-4f41038f6d22
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 451884c5055ee0be3ceeb95f4fe3c9dddb388bc0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469612"
---
# <a name="sp_describe_first_result_set-transact-sql"></a>sp_describe_first_result_set (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt die Metadaten für das erste mögliche Resultset des [!INCLUDE[tsql](../../includes/tsql-md.md)] Batches zurück. Gibt ein leeres Resultset zurück, wenn vom Batch keine Ergebnisse zurückgegeben werden. Löst einen Fehler [!INCLUDE[ssDE](../../includes/ssde-md.md)] aus, wenn der die Metadaten für die erste Abfrage, die durch Ausführen einer statischen Analyse ausgeführt wird, nicht ermitteln kann. Die dynamische Verwaltungs Sicht [sys. dm_exec_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md) gibt die gleichen Informationen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_describe_first_result_set [ @tsql = ] N'Transact-SQL_batch'   
    [ , [ @params = ] N'parameters' ]   
    [ , [ @browse_information_mode = ] <tinyint> ] ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ \@tsql = ] 'Transact-SQL_batch'` Eine oder mehrere- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen. *Transact-SQL_batch* kann vom Datentyp **nvarchar (***n***)** oder **nvarchar (max)** sein.  
  
`[ \@params = ] N'parameters'`\@Parameter stellt eine Deklarations Zeichenfolge für Parameter für den- [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch bereit, die sp_executesql ähnelt. Parameter können **nvarchar (n)** oder **nvarchar (max)** sein.  
  
 Ist eine Zeichenfolge, die die Definitionen aller Parameter enthält, die in die [!INCLUDE[tsql](../../includes/tsql-md.md)] *_batch*eingebettet wurden. Die Zeichenfolge muss eine Unicode-Konstante oder eine Unicode-Variable sein. Jede Parameterdefinition besteht aus einem Parameternamen und einem Datentyp. *n* ist ein Platzhalter, der zusätzliche Parameter Definitionen angibt. Jeder in der-Anweisung angegebene Parameter muss in Parametern definiert werden \@ . Wenn die- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung oder der-Batch in der Anweisung keine Parameter enthält, ist die Angabe von Parametern \@ nicht erforderlich. Der Standardwert für diesen Parameter ist NULL.  
  
`[ \@browse_information_mode = ] tinyint` Gibt an, ob zusätzliche Schlüssel Spalten und Quell Tabellen Informationen zurückgegeben werden. Wenn der Wert auf 1 festgelegt ist, wird jede Abfrage so analysiert, als ob Sie eine for Browse-Option für die Abfrage enthält. Zusätzliche Schlüsselspalten und Quelltabelleninformationen werden zurückgegeben.  
  
-   Bei 0 werden keine Informationen zurückgegeben.  
  
-   Wenn der Wert auf 1 festgelegt ist, wird jede Abfrage so analysiert, als ob Sie eine for Browse-Option für die Abfrage enthält. Damit werden Basistabellennamen als Quellspalteninformationen zurückgegeben.  
  
-   Bei 2 wird jede Abfrage analysiert, als würde sie beim Vorbereiten oder Ausführen eines Cursors verwendet. Damit werden Sichtnamen als Quellspalteninformationen zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **sp_describe_first_result_set** gibt bei Erfolg immer den Status 0 (null) zurück. Wenn die Prozedur einen Fehler auslöst und die Prozedur als RPC aufgerufen wird, wird der Rückgabestatus durch den Fehlertyp aufgefüllt, der in der error_type-Spalte von sys. dm_exec_describe_first_result_set beschrieben wird. Wenn die Prozedur von [!INCLUDE[tsql](../../includes/tsql-md.md)] aufgerufen wird, ist der Rückgabewert immer 0; dies gilt auch bei einem Fehler.  
  
## <a name="result-sets"></a>Resultsets  
 Diese allgemeinen Metadaten werden in den Ergebnismetadaten als Resultset mit einer Zeile für jede Spalte zurückgegeben. Jede Zeile beschreibt den Typ und die NULL-Zulässigkeit der Spalte in dem Format, das im folgenden Abschnitt beschriebenen wird. Wenn die erste Anweisung nicht für alle Steuerelementpfade vorhanden ist, wird ein Resultset mit 0 Zeilen zurückgegeben.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**is_hidden**|**Bit not NULL**|Gibt an, dass es sich bei der Spalte um eine zusätzliche Spalte zum Suchen von Informationen handelt, die nicht im Resultset angezeigt wird.|  
|**column_ordinal**|**int NOT NULL**|Enthält die Ordnungsposition der Spalte im Resultset. Die Position der ersten Spalte wird als 1 angegeben.|  
|**name**|**vom Datentyp sysname NULL**|Enthält den Namen der Spalte, wenn ein Name bestimmt werden kann. Andernfalls enthält Sie NULL.|  
|**is_nullable**|**Bit not NULL**|Enthält den Wert 1, wenn die Spalte NULL-Werte zulässt, 0, wenn die Spalte keinen NULL-Werte zulässt, und 1, wenn nicht ermittelt werden kann, ob die Spalte NULL-Werte zulässt.|  
|**system_type_id**|**int NOT NULL**|Enthält die system_type_id des Datentyps der Spalte, wie in sys. types angegeben. Bei CLR-Typen wird von dieser Spalte der Wert 240 zurückgegeben, obwohl von der system_type_name-Spalte NULL zurückgegeben wird.|  
|**system_type_name**|**nvarchar (256) NULL**|Enthält den Namen und die Argumente (z. B. Länge, Genauigkeit oder Skala), die für den Datentyp der Spalte angegeben wurden. Wenn der Datentyp ein benutzerdefinierter Aliastyp ist, wird der zugrunde liegende Systemtyp hier angegeben. Bei einem benutzerdefinierten CLR-Typ wird NULL in dieser Spalte zurückgegeben.|  
|**max_length**|**smallint not NULL**|Maximale Länge (in Byte) für die Spalte.<br /><br /> -1 = der Spaltendatentyp ist **varchar (max)**, **nvarchar (max)**, **varbinary (max)** oder **XML**.<br /><br /> Bei **Text** Spalten ist der **max_length** Wert 16 oder der Wert, der durch **sp_tableoption ' Text in row '** festgelegt wird.|  
|**precision**|**tinyint not NULL**|Die Genauigkeit der Spalte, wenn sie auf numerischen Werten basiert. Andernfalls wird 0 zurückgegeben.|  
|**scale**|**tinyint not NULL**|Die Skalierung der Spalte, wenn sie auf numerischen Werten basiert. Andernfalls wird 0 zurückgegeben.|  
|**collation_name**|**vom Datentyp sysname NULL**|Name der Sortierung der Spalte, wenn diese zeichenbasiert ist. Andernfalls wird NULL zurückgegeben.|  
|**user_type_id**|**int NULL**|Enthält bei CLR- und Aliastypen die user_type_id des Datentyps der Spalte, wie in sys.types angegeben. Andernfalls NULL.|  
|**user_type_database**|**vom Datentyp sysname NULL**|Enthält bei CLR- und Aliastypen den Namen der Datenbank, in der der Typ definiert wurde. Andernfalls NULL.|  
|**user_type_schema**|**vom Datentyp sysname NULL**|Enthält bei CLR- und Aliastypen den Namen des Schemas, in dem der Typ definiert wurde. Andernfalls NULL.|  
|**user_type_name**|**vom Datentyp sysname NULL**|Enthält bei CLR- und Aliastypen den Namen des Typs. Andernfalls NULL.|  
|**assembly_qualified_type_name**|**nvarchar(4000)**|Gibt bei CLR-Typen den Namen der Assembly und der Klasse zurück, die den Typ definieren. Andernfalls NULL.|  
|**xml_collection_id**|**int NULL**|Enthält die xml_collection_id des Datentyps für die Spalte, wie in sys.columns angegeben. Diese Spalte gibt NULL zurück, wenn der zurückgegebene Typ keiner XML-Schemaauflistung zugeordnet ist.|  
|**xml_collection_database**|**vom Datentyp sysname NULL**|Enthält die Datenbank, in der die XML-Schemaauflistung definiert ist, die diesem Typ zugeordnet wurde. Diese Spalte gibt NULL zurück, wenn der zurückgegebene Typ keiner XML-Schemaauflistung zugeordnet ist.|  
|**xml_collection_schema**|**vom Datentyp sysname NULL**|Enthält das Schema, in dem die XML-Schemaauflistung definiert ist, die diesem Typ zugeordnet wurde. Diese Spalte gibt NULL zurück, wenn der zurückgegebene Typ keiner XML-Schemaauflistung zugeordnet ist.|  
|**xml_collection_name**|**vom Datentyp sysname NULL**|Enthält den Namen der XML-Schemaauflistung, die diesem Typ zugeordnet wurde. Diese Spalte gibt NULL zurück, wenn der zurückgegebene Typ keiner XML-Schemaauflistung zugeordnet ist.|  
|**is_xml_document**|**Bit not NULL**|Gibt 1 zurück, wenn der zurückgegebene Datentyp XML ist und für diesen Typ garantiert ist, dass es sich um ein vollständiges XML-Dokument (einschließlich eines Stammknotens) handelt, nicht um ein XML-Fragment. Andernfalls wird 0 zurückgegeben.|  
|**is_case_sensitive**|**Bit not NULL**|Gibt 1 zurück, wenn die Spalte einen Zeichenfolgentyp darstellt, bei dem die Groß-/Kleinschreibung beachtet wird, andernfalls 0.|  
|**is_fixed_length_clr_type**|**Bit not NULL**|Gibt 1 zurück, wenn die Spalte ein CLR-Typ mit fester Länge ist, andernfalls 0.|  
|**source_server**|**sysname**|Der Name des ursprünglichen Servers, der von der Spalte in diesem Ergebnis zurückgegeben wurde (bei einem Remoteserver). Der Name wird wie in sys. Servers angezeigt. Gibt NULL zurück, wenn die Spalte vom lokalen Server stammt oder der ursprüngliche Server nicht ermittelt werden konnte. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**source_database**|**sysname**|Der Name der ursprünglichen Datenbank, die von der Spalte in diesem Ergebnis zurückgegeben wird. Gibt NULL zurück, wenn die Datenbank nicht ermittelt werden kann. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**source_schema**|**sysname**|Der Name des ursprünglichen Schemas, das von der Spalte in diesem Ergebnis zurückgegeben wird. Gibt NULL zurück, wenn das Schema nicht bestimmt werden kann. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**source_table**|**sysname**|Der Name der ursprünglichen Tabelle, die von der Spalte in diesem Ergebnis zurückgegeben wird. Gibt NULL zurück, wenn die Tabelle nicht bestimmt werden kann. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**source_column**|**sysname**|Der Name der ursprünglichen Spalte, die von der Ergebnisspalte zurückgegeben wird. Gibt NULL zurück, wenn die Spalte nicht bestimmt werden kann. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**is_identity_column**|**Bit NULL**|Gibt 1 zurück, wenn die Spalte eine Identitätsspalte ist, andernfalls 0. Gibt NULL zurück, wenn nicht ermittelt werden kann, ob die Spalte eine Identitätsspalte ist.|  
|**is_part_of_unique_key**|**Bit NULL**|Gibt 1 zurück, wenn die Spalte Teil eines eindeutigen Index (einschließlich UNIQUE- und PRIMARY-Einschränkung) ist, andernfalls 0. Gibt NULL zurück, wenn nicht ermittelt werden kann, ob die Spalte Teil eines eindeutigen Indexes ist. Wird nur aufgefüllt, wenn die Suche nach Informationen erforderlich ist.|  
|**is_updateable**|**Bit NULL**|Gibt 1 zurück, wenn die Spalte aktualisiert werden kann, andernfalls 0. Gibt NULL zurück, wenn nicht ermittelt werden kann, ob die Spalte aktualisiert werden kann.|  
|**is_computed_column**|**Bit NULL**|Gibt 1 zurück, wenn die Spalte eine berechnete Spalte, andernfalls 0. Gibt NULL zurück, wenn nicht ermittelt werden kann, ob die Spalte eine berechnete Spalte ist.|  
|**is_sparse_column_set**|**Bit NULL**|Gibt 1 zurück, wenn die Spalte eine Sparsespalte ist, andernfalls 0. Gibt NULL zurück, wenn nicht ermittelt werden kann, ob die Spalte Teil eines sparsespaltensatzes ist.|  
|**ordinal_in_order_by_list**|**smallint NULL**|Die Position dieser Spalte in der ORDER BY-Liste. Gibt NULL zurück, wenn die Spalte nicht in der ORDER BY-Liste angezeigt wird oder die Order by-Liste nicht eindeutig bestimmt werden kann.|  
|**order_by_list_length**|**smallint NULL**|Die Länge der ORDER BY-Liste. Gibt NULL zurück, wenn keine ORDER BY-Liste vorhanden ist oder die ORDER BY-Liste nicht eindeutig bestimmt werden kann. Beachten Sie, dass dieser Wert für alle Zeilen identisch ist, die von sp_describe_first_result_set zurückgegeben werden **.**|  
|**order_by_is_descending**|**smallint NULL**|Wenn ordinal_in_order_by_list nicht NULL ist, wird von der **order_by_is_descending**-Spalte die Richtung der ORDER BY-Klausel für diese Spalte gemeldet. Andernfalls wird NULL gemeldet.|  
|**tds_type_id**|**int NOT NULL**|Für die interne Verwendung.|  
|**tds_length**|**int NOT NULL**|Für die interne Verwendung.|  
|**tds_collation_id**|**int NULL**|Für die interne Verwendung.|  
|**tds_collation_sort_id**|**tinyint NULL**|Für die interne Verwendung.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_describe_first_result_set** wird sichergestellt, dass, wenn die Prozedur die ersten Resultset-Metadaten für (einen hypothetischen) Batch a zurückgibt und dieser Batch (a) anschließend ausgeführt wird, der Batch entweder (1) einen Optimierungs Zeitfehler auslöst. (2) löst einen Laufzeitfehler aus, (3) gibt kein Resultset zurück, oder (4) gibt ein erstes Resultset mit denselben Metadaten zurück, die von **sp_describe_first_result_set**beschrieben werden.  
  
 Der Name, die NULL-Zulässigkeit und der Datentyp können abweichen. Wenn **sp_describe_first_result_set** ein leeres Resultset zurückgibt, ist die Garantie, dass bei der Batch Ausführung keine Resultsets zurückgegeben werden.  
  
 Diese Garantie setzt voraus, dass keine relevanten Schema Änderungen auf dem Server vorhanden sind. Relevante Schema Änderungen auf dem Server umfassen nicht das Erstellen temporärer Tabellen oder Tabellen Variablen im Batch a zwischen dem Zeitpunkt, an dem **sp_describe_first_result_set** aufgerufen wird, und dem Zeitpunkt, an dem das Resultset während der Ausführung zurückgegeben wird, einschließlich der von Batch B vorgenommenen Schema Änderungen.  
  
 **sp_describe_first_result_set** gibt einen Fehler in einem der folgenden Fälle zurück.  
  
-   , Wenn die Eingabe- \@ zql kein gültiger [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch ist. Die Gültigkeit wird durch analysieren und Analysieren des [!INCLUDE[tsql](../../includes/tsql-md.md)] Batches bestimmt. Fehler, die durch den Batch während der Abfrageoptimierung oder während der Ausführung verursacht werden, werden nicht berücksichtigt, wenn bestimmt wird, ob der [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch gültig ist.  
  
-   \@, Wenn Parameter nicht NULL sind und eine Zeichenfolge enthält, die keine syntaktisch gültige Deklarations Zeichenfolge für Parameter ist, oder, wenn Sie eine Zeichenfolge enthält, die einen Parameter mehrmals deklariert.  
  
-   , Wenn der Eingabe [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch eine lokale Variable mit demselben Namen wie ein in Parametern deklarierter Parameter deklariert \@ .  
  
-   Die Anweisung verwendet eine temporäre Tabelle.  
  
-   Die Abfrage umfasst die Erstellung einer dauerhaften Tabelle, die dann abgefragt wird.  
  
 Wenn alle anderen Überprüfungen erfolgreich sind, werden alle möglichen Ablaufsteuerungspfade im Eingabebatch berücksichtigt. Dabei werden alle Ablauf Steuerungs Anweisungen (goto, if/else) berücksichtigt. while-und [!INCLUDE[tsql](../../includes/tsql-md.md)] try/catch-Blöcke) sowie Prozeduren, dynamische [!INCLUDE[tsql](../../includes/tsql-md.md)] Batches oder Trigger, die durch eine EXEC-Anweisung aus dem Eingabe Batch aufgerufen werden, eine DDL-Anweisung, die bewirkt, dass DDL-Trigger ausgelöst werden, oder eine DML-Anweisung, die bewirkt, dass Trigger für eine Ziel Tabelle oder für eine Tabelle ausgelöst werden, die aufgrund einer kaskadierenden Aktion Bei einer Vielzahl möglicher Steuerelementpfade wird der Algorithmus irgendwann beendet.  
  
 Für jeden Ablauf Steuerungs Pfad wird die erste Anweisung (sofern vorhanden), die ein Resultset zurückgibt, durch **sp_describe_first_result_set**bestimmt.  
  
 Bei mehreren möglichen ersten Anweisungen in einem Batch kann sich das jeweilige Ergebnis im Hinblick auf die Anzahl der Spalten, die Spaltennamen, die NULL-Zulässigkeit und den Datentyp unterscheiden. Im Folgenden wird ausführlicher erläutert, wie diese Unterschiede gehandhabt werden:  
  
-   Wenn sich die Anzahl der Spalten unterscheidet, wird ein Fehler ausgelöst, und es wird kein Ergebnis zurückgegeben.  
  
-   Wenn der Spaltenname abweicht, wird der zurückgegebene Spaltenname auf NULL festgelegt.  
  
-   Wenn die NULL-Zulässigkeit abweicht, sind NULL-Werte in der zurückgegebenen NULL-Zulässigkeit zulässig.  
  
-   Wenn der Datentyp abweicht, wird ein Fehler ausgelöst, und nur in folgenden Fällen wird ein Ergebnis zurückgegeben:  
  
    -   **varchar (a)** in **varchar (a ')** , wobei ein ' >.  
  
    -   **varchar (a)** in **varchar (max)**  
  
    -   **nvarchar (a)** zu **nvarchar (a ')** , wobei ein ' >.  
  
    -   **nvarchar (a)** zu **nvarchar (max)**  
  
    -   **varbinary (a)** in **varbinary (a ')** , wobei ein ' >.  
  
    -   **varbinary (a)** nach **varbinary (max)**  
  
 **sp_describe_first_result_set** unterstützt keine indirekte Rekursion.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Berechtigung zum Ausführen des " \@ parql"-Arguments.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="typical-examples"></a>Typische Beispiele  
  
#### <a name="a-simple-example"></a>A. Einfaches Beispiel  
 Im folgenden Beispiel wird das von einer einzelnen Abfrage zurückgegebene Resultset beschrieben.  
  
```  
sp_describe_first_result_set @tsql = N'SELECT object_id, name, type_desc FROM sys.indexes'  
```  
  
 Im folgenden Beispiel wird das von einer einzelnen Abfrage mit einem Parameter zurückgegebene Resultset veranschaulicht.  
  
```  
sp_describe_first_result_set @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes   
WHERE object_id = @id1'  
, @params = N'@id1 int'  
```  
  
#### <a name="b-browse-mode-examples"></a>B. Beispielen für Durchsuchenmodi  
 In den folgenden drei Beispielen wird der Hauptunterschied zwischen den unterschiedlichen Modi für die Informationssuche veranschaulicht. In den Abfrageergebnissen waren nur die relevanten Spalten enthalten.  
  
 Beispiel mit dem Wert 0, der angibt, dass keine Informationen zurückgegeben werden.  
  
```sql  
CREATE TABLE dbo.t (a int PRIMARY KEY, b1 int);  
GO  
CREATE VIEW dbo.v AS SELECT b1 AS b2 FROM dbo.t;  
GO  
EXEC sp_describe_first_result_set N'SELECT b2 AS b3 FROM dbo.v', null, 0;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|is_hidden|column_ordinal|name|source_schema|source_table|source_column|is_part_of_unique_key|  
|----------------|---------------------|----------|--------------------|-------------------|--------------------|-------------------------------|  
|0|1|b3|NULL|NULL|NULL|NULL|  
  
 Beispiel mit dem Wert 1, der angibt, dass Informationen so zurückgegeben werden, als ob in der Abfrage eine FOR BROWSE-Option eingeschlossen wäre.  
  
```sql  
EXEC sp_describe_first_result_set N'SELECT b2 AS b3 FROM v', null, 1  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|is_hidden|column_ordinal|name|source_schema|source_table|source_column|is_part_of_unique_key|  
|----------------|---------------------|----------|--------------------|-------------------|--------------------|-------------------------------|  
|0|1|b3|dbo|t|B1|0|  
|1|2|a|dbo|t|a|1|  
  
 Beispiel mit dem Wert 2, der angibt, dass die Analyse erfolgt, als ob Sie einen Cursor vorbereiteten.  
  
```sql  
EXEC sp_describe_first_result_set N'SELECT b2 AS b3 FROM v', null, 2  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|is_hidden|column_ordinal|name|source_schema|source_table|source_column|is_part_of_unique_key|  
|----------------|---------------------|----------|--------------------|-------------------|--------------------|-------------------------------|  
|0|1|B3|dbo|v|B2|0|  
|1|2|ROWSTAT|NULL|NULL|NULL|0|  
  
### <a name="examples-of-problems"></a>Beispiele für Probleme  
 In den folgenden Beispielen werden zwei Tabellen für alle Beispiele verwendet. Führen Sie die folgenden Anweisungen aus, um die Beispieltabellen zu erstellen.  
  
```  
CREATE TABLE dbo.t1 (a int NULL, b varchar(10) NULL, c nvarchar(10) NULL);  
CREATE TABLE dbo.t2 (a smallint NOT NULL, d varchar(20) NOT NULL, e int NOT NULL);  
```  
  
#### <a name="error-because-the-number-of-columns-differ"></a>Fehler aufgrund unterschiedlicher Spaltenanzahl  
 Die Anzahl der Spalten in möglichen ersten Resultsets weicht in diesem Beispiel ab.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    SELECT a FROM t1;  
ELSE  
    SELECT a, b FROM t1;  
SELECT * FROM t; -- Ignored, not a possible first result set.'  
  
```  
  
#### <a name="error-because-the-data-types-differ"></a>Fehler aufgrund abweichender Datentypen  
 Die Spaltentypen unterscheiden sich in verschiedenen möglichen ersten Resultsets.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    SELECT a FROM t1;  
ELSE  
    SELECT a FROM t2;  
```  
  
 Ergebnis: Fehler, nicht übereinstimmende Typen (**int** im Vergleich zu **smallint**).  
  
#### <a name="column-name-cannot-be-determined"></a>Spaltenname kann nicht bestimmt werden  
 Die Spalten in möglichen ersten Resultsets unterscheiden sich hinsichtlich der Länge für identische Typen mit variabler Länge, NULL-Zulässigkeiten und Spaltennamen:  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    SELECT b FROM t1;  
ELSE  
    SELECT d FROM t2; '  
```  
  
 Ergebnis: \<Unknown Column Name> **varchar (20) NULL**  
  
#### <a name="column-name-forced-to-be-identical-through-aliasing"></a>Spaltenname mit durch Aliasing erzwungenem identischem Spaltennamen  
 Analog zum vorherigen, die Namen der Spalten sind jedoch aufgrund von Spaltenaliasing identisch.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    SELECT b FROM t1;  
ELSE  
    SELECT d AS b FROM t2;'  
```  
  
 Ergebnis: b **varchar (20) NULL**  
  
#### <a name="error-because-column-types-cannot-be-matched"></a>Fehler aufgrund nicht zuzuordnender Spaltentypen  
 Die Spaltentypen unterscheiden sich in verschiedenen möglichen ersten Resultsets.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    SELECT b FROM t1;  
ELSE  
    SELECT c FROM t1;'  
```  
  
 Ergebnis: Fehler, nicht übereinstimmende Typen (**varchar (10)** und **nvarchar (10)**).  
  
#### <a name="result-set-can-return-an-error"></a>Resultset kann einen Fehler zurückgeben  
 Das erste Resultset ist Fehler oder Resultset.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    RAISERROR(''Some Error'', 16, 1);  
  
ELSE  
    SELECT a FROM t1;  
SELECT e FROM t2; -- Ignored, not a possible first result set.;'  
```  
  
 Ergebnis: a **intnull**  
  
#### <a name="some-code-paths-return-no-results"></a>Einige Codepfade geben keine Ergebnisse zurück  
 Der erste Resultset ist NULL oder ein Resultset.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
IF(1=1)  
    RETURN;  
SELECT a FROM t1;'  
```  
  
 Ergebnis: a **intnull**  
  
#### <a name="result-from-dynamic-sql"></a>Ergebnis von dynamischem SQL  
 Das erste Resultset ist dynamisches SQL, das ermittelt werden kann, da es sich um eine Literalzeichenfolge handelt.  
  
```  
sp_describe_first_result_set @tsql =   
N'EXEC(N''SELECT a FROM t1'');'  
```  
  
 Ergebnis: a **int NULL**  
  
#### <a name="result-failure-from-dynamic-sql"></a>Ergebnisfehler von dynamischem SQL  
 Das erste Resultset ist aufgrund von dynamischem SQL nicht definiert.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
DECLARE @SQL NVARCHAR(max);  
SET @SQL = N''SELECT a FROM t1 WHERE 1 = 1 '';  
IF(1=1)  
    SET @SQL += N'' AND e > 10 '';  
EXEC(@SQL); '  
```  
  
 Ergebnis: Fehler. Das Ergebnis kann aufgrund von dynamischem SQL nicht ermittelt werden.  
  
#### <a name="result-set-specified-by-user"></a>Vom Benutzer angegebenes Resultset  
 Das erste Resultset wird manuell vom Benutzer angegeben.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
DECLARE @SQL NVARCHAR(max);  
SET @SQL = N''SELECT a FROM t1 WHERE 1 = 1 '';  
IF(1=1)  
    SET @SQL += N'' AND e > 10 '';  
EXEC(@SQL)  
    WITH RESULT SETS(  
        (Column1 BIGINT NOT NULL)  
    ); '  
```  
  
 Ergebnis: column1 **bigint not NULL**  
  
#### <a name="error-caused-by-a-ambiguous-result-set"></a>Von einem mehrdeutigen Resultset verursachter Fehler  
 In diesem Beispiel wird davon ausgegangen, dass ein anderer Benutzer mit dem Namen User1 eine Tabelle mit dem Namen T1 im Standardschema S1 mit Spalten (a **int not NULL**) aufweist.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
    IF(@p > 0)  
    EXECUTE AS USER = ''user1'';  
    SELECT * FROM t1;'  
, @params = N'@p int'  
```  
  
 Ergebnis: Fehler. T1 kann entweder dbo. T1 oder S1. T1 mit einer unterschiedlichen Anzahl von Spalten sein.  
  
#### <a name="result-even-with-ambiguous-result-set"></a>Ergebnis auch bei mehrdeutigem Resultset  
 Verwenden Sie die gleichen Annahmen wie im vorherigen Beispiel.  
  
```  
sp_describe_first_result_set @tsql =   
N'  
    IF(@p > 0)  
    EXECUTE AS USER = ''user1'';  
    SELECT a FROM t1;'  
```  
  
 Ergebnis: a **int NULL** , weil dbo. T1. a und S1. T1. a den Typ **int** und eine andere NULL-Zulässigkeit aufweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_describe_undeclared_parameters &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)   
 [sys. dm_exec_describe_first_result_set &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)   
 [sys. dm_exec_describe_first_result_set_for_object &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md)  
 
