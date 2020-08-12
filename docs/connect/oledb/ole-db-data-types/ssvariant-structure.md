---
title: SSVARIANT-Struktur | Microsoft-Dokumentation
description: SSVARIANT-Struktur im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 0d11a6f839fba1905055aefafa65353008530f8d
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86004523"
---
# <a name="ssvariant-structure"></a>SSVARIANT-Struktur
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die in „msoledbsql.h“ definierte **SSVARIANT**-Struktur entspricht einem DBTYPE_SQLVARIANT-Wert im OLE DB-Treiber für SQL Server.  
  
 **SSVARIANT** ist eine unterscheidende Union. Abhängig vom Wert des vt-Elements kann der Consumer feststellen, welches Element gelesen werden soll. vt-Werte entsprechen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen. Die **SSVARIANT**-Struktur kann daher jeden SQL Server-Typ enthalten. Weitere Informationen zur Datenstruktur für standardmäßige OLE DB-Typen finden Sie unter [Typindikatoren](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn DataTypeCompat auf „80“ festgelegt ist, werden verschiedene **SSVARIANT**-Untertypen zu Zeichenfolgen. Beispielsweise werden die folgenden vt-Werte in **SSVARIANT** als VT_SS_WVARSTRING angezeigt:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Wenn DateTypeCompat auf "0" festgelegt ist, werden diese Typen in ihrer systemeigenen Form angezeigt.  
  
 Weitere Informationen zu SSPROP_INIT_DATATYPECOMPATIBILITY finden Sie unter [Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 Die Datei „msoledbsql.h“ enthält VARIANT-Zugriffsmakros, die das Dereferenzieren der Elementtypen der **SSVARIANT**-Struktur vereinfachen. Beispielsweise können Sie V_SS_DATETIMEOFFSET folgendermaßen verwenden:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Den vollständigen Satz der Zugriffsmakros für jeden Member der **SSVARIANT**-Struktur finden Sie in der Datei „msoledbsql.h“.  
  
 In der folgenden Tabelle werden die Elemente der **SSVARIANT**-Struktur beschrieben:  
  
|Member|OLE DB-Typindikator|OLE DB-C-Datentyp|vt-Wert|Kommentare|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||Gibt den Typ des Werts in der **SSVARIANT**-Struktur an.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|Unterstützt den **tinyint**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.|  
|sShortIntVal|DBTYPE_I2|**SHORT**|**VT_SS_I2**|Unterstützt den **smallint**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|Unterstützt den **int**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Unterstützt den **bigint**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Unterstützt den **real**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Unterstützt den **float**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Unterstützt die Datentypen **money** und **smallmoney**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Unterstützt den **bit**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Unterstützt den **uniqueidentifier**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Unterstützt den **numeric**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Unterstützt den **date**-Datentyp von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Unterstützt die Datentypen **smalldatetime**, **datetime** und **datetime2**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Unterstützt den **time**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**BYTE**) Gibt die Skalierung für den *tTime2Val*-Wert an.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Unterstützt den **datetime2**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**BYTE**) Gibt die Skalierung für den *tsDataTimeVal*-Wert an.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Unterstützt den **datetimeoffset**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**BYTE**) Gibt die Skalierung für den *tsoDateTimeOffsetVal*-Wert an.|  
|NCharVal|Kein entsprechender OLE DB-Typindikator.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Unterstützt die Datentypen **nchar** und **nvarchar**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**SHORT**) Gibt die tatsächliche Länge der Zeichenfolge an, auf die *pwchNCharVal* verweist. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (**SHORT**) Gibt die maximale Länge der Zeichenfolge an, auf die *pwchNCharVal* verweist.<br /><br /> *pwchNCharVal* (**WCHAR** \*) Zeiger auf die Zeichenfolge.<br /><br /> *rgbReserved* (**BYTE[5]** ) gibt die Sortierungsinformationen an.<br /><br /> Nicht verwendete Member: *dwReserved* und *pwchReserved*|  
|CharVal|Kein entsprechender OLE DB-Typindikator.|**struct_CharVal**|**VT_SS_WVARSTRING**<br /><br /> **VT_SS_WVARSTRING**|Unterstützt die Datentypen **char** und **varchar**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**SHORT**) Gibt die tatsächliche Länge der Zeichenfolge an, auf die *pchCharVal* verweist. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (**SHORT**) Gibt die maximale Länge der Zeichenfolge an, auf die *pchCharVal* verweist.<br /><br /> *pwchCharVal* (**CHAR** \*) Zeiger auf die Zeichenfolge.<br /><br /> *rgbReserved* (**BYTE[5]** ) gibt die Sortierungsinformationen an.<br /><br /> Nicht verwendete Member:<br /><br /> *dwReserved* und *pwchReserved*|  
|BinaryVal|Kein entsprechender OLE DB-Typindikator.|**struct_BinaryVal**|**VT_SS_VARBINARY**<br /><br /> **VT_SS_BINARY**|Unterstützt die Datentypen **binary** und **varbinary**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**SHORT**) Gibt die tatsächliche Länge der Daten an, auf die *prgbBinaryVal* verweist.<br /><br /> *sMaxLength* (**SHORT**) Gibt die maximale Länge der Daten an, auf die *prgbBinaryVal* verweist.<br /><br /> *prgbBinaryVal* (**BYTE** \*) Zeiger auf die Binärdaten.<br /><br /> Nicht verwendeter Member: *dwReserved*.|  
|UnknownType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
|BLOBType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
  
## <a name="known-issues"></a>Bekannte Probleme
### <a name="possible-narrow-string-data-corruption"></a>Mögliche Datenbeschädigung bei schmalen Zeichenfolgen
Vor Version 18.4 des OLE DB-Treibers konnte das Einfügen in eine `sql_variant`-Spalte zu einer Beschädigung der Daten auf dem Server führen, wenn alle der folgenden Bedingungen erfüllt waren:
- Die Codepage des Clientcomputers entsprach nicht der Codepage für die Datenbanksortierung.
- Der einzufügende Clientpuffer enthielt der Clientcodepage entsprechend codierte Zeichen aus schmalen Nicht-ASCII-Zeichenfolgen.
- Eine der folgenden Bedingungen traf zu:
  - Das `pwszDataSourceType`-Feld in der `DBPARAMBINDINFO`-Struktur, das den Parameter beschreibt, der der `sql_variant`-Spalte entspricht, wurde auf `L"DBTYPE_SQLVARIANT"`, `L"DBTYPE_VARIANT"`oder `L"sql_variant"` festgelegt. Einzelheiten dazu finden Sie unter: [ICommandWithParameters::SetParameterInfo](https://docs.microsoft.com/previous-versions/windows/desktop/ms725393(v=vs.85)).

    *or*
  - Die zum Einfügen verwendete parametrisierte SQL-Abfrage wurde vorbereitet.

Genauer gesagt übersetzte der OLE DB-Treiber die Daten vor dem Einfügen nicht gemäß der Codepage für die Datenbanksortierung. Er gab dem Server gegenüber jedoch fälschlicherweise an, dass die Daten gemäß der Codepage für die Datenbanksortierung codiert seien. Dieses Verhalten führte zu einem Konflikt zwischen den Daten und der entsprechenden, in der `sql_variant`-Spalte gespeicherten Codepage.

Ebenso hat der OLE DB-Treiber beim Abrufen dieses Werts Zeichenfolgen nicht der Clientcodepage entsprechend übersetzt. Da die eingefügten Daten jedoch bereits der Clientcodepage entsprechend codiert waren (siehe vorheriger Absatz), konnte die Clientanwendung die Daten richtig interpretieren. Dennoch riefen Anwendungen, die andere Treiber verwendeten, diese Werte in einem beschädigten Format ab. Die Beschädigung trat auf, da andere Treiber die Zeichenfolge gemäß der Codepage für die Datenbanksortierung interpretierten und versuchten, sie der Clientcodepage entsprechend zu übersetzen.

Ab Version 18.4 übersetzt der OLE DB-Treiber schmale Zeichenfolgen vor dem Einfügen gemäß der Codepage für die Datenbanksortierung. Ebenso übersetzt der Treiber die Daten beim Abruf gemäß der Clientcodepage wieder zurück. Daher treten bei Clientanwendungen mit dem oben erwähnten Fehler beim Abrufen von Daten, die mit einer früheren Version des OLE DB-Treibers eingefügt wurden, möglicherweise Probleme auf. Das unten dargelegte [Wiederherstellungsverfahren](#recovery-procedure) soll Sie beim Beheben dieser Probleme unterstützen.

### <a name="recovery-procedure"></a>Wiederherstellungsverfahren
> [!IMPORTANT]  
> Stellen Sie sicher, dass Sie die vorhandenen Daten sichern, bevor Sie die folgenden Wiederherstellungsschritte ausführen.

Wenn bei Ihrer Anwendung nach dem Wechsel zu Version 18.4 des OLE DB-Treibers Probleme beim Abrufen von Daten aus einer `sql_variant`-Spalte auftreten, müssen die beschädigten Daten so geändert werden, dass sie dieselbe Sortierung wie die Datenbank aufweisen, in der die Daten gespeichert sind. Das folgende Skript kann verwendet werden, um einen einzelnen Wert aus einer `sql_variant`-Spalte wiederherzustellen. Das Skript ist eine Vorlage, die Sie an Ihr Szenario anpassen müssen.

> [!IMPORTANT]  
> Da die ursprüngliche Codepage der Daten nicht gespeichert wird, müssen Sie dem Server mitteilen, wie die Daten ursprünglich codiert wurden. Führen Sie hierzu das Skript im Kontext einer Datenbank aus, die über die gleiche Codepage wie der Client verfügt, der die Daten ursprünglich eingefügt hat. Wenn beispielsweise die beschädigten Daten von einem Client eingefügt wurden, der mit der Codepage `932` konfiguriert wurde, muss das folgende Skript im Kontext einer Datenbank mit einer japanischen Sortierung (z. B. `Japanese_XJIS_100_CS_AI`) ausgeführt werden.

```sql
/*
    Description:
        Template that can be used to recover the corrupted value inserted into the sql_variant column.

    Scenario:
        The database is named [YourDatabase] and it contains a table named [YourTable], which contains the corrupted value.
        Schema is named [dbo].
        The corrupted value is stored in a column of type sql_variant named [YourColumn].
        The corrupted value is sql_variant of BaseType char. For details on sql_variant properties, see:
            https://docs.microsoft.com/sql/t-sql/functions/sql-variant-property-transact-sql
*/

-- Base type in sql_variant can hold a maximum of 8000 bytes
-- For details see: 
--  https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql#remarks
DECLARE @bin VARBINARY(8000)

-- In the following lines we convert the sql_variant base type to binary.
-- <FilterExpression>
--      Is a placeholder and must be replaced with an expression that filters a single corrupted value to be recovered.
--      Therefore, the expression must result in a single value being returned only.
SET @bin = (SELECT CAST([YourColumn] AS VARBINARY(8000)) FROM [YourDatabase].[dbo].[YourTable] WHERE <FilterExpression>)

-- In the following lines we store the binary value in char(59) (a fixed-size character data type).
-- IMPORTANT NOTE: 
--      This example assumes the corrupted sql_variant's base type is char(59).
--      You MUST adjust the type (that is, char/varchar) and size to match your scenario exactly.
DECLARE @char CHAR(59)
SET @char = CAST((@bin) AS CHAR(59))
DECLARE @sqlvariant sql_variant

-- The following lines recover the corrupted value by translating the value to the collation of the database.
-- <DBCollation>
--      Must be replaced with the collation (for example, Latin1_General_100_CI_AS_SC_UTF8) of the database holding the data.
SET @sqlvariant = @char collate <DBCollation>

-- Finally, we update the corrupted value with the recovered value.
-- "<FilterExpression>"
--      Is a placeholder and must be replaced with an expression that filters a single corrupted value to be recovered.
--      Therefore, the expression must result in a single value being returned only.
UPDATE [YourDatabase].[dbo].[YourTable] SET [YourColumn] = @sqlvariant WHERE <FilterExpression>
```

## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
