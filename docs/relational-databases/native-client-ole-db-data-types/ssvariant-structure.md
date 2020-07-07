---
title: SSVARIANT-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d87c4a4537683d9dbb9817a0a3c022f23f2b846
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "85998209"
---
# <a name="ssvariant-structure"></a>SSVARIANT-Struktur
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Die **SSVARIANT** -Struktur, die in sqlncli. h definiert ist, entspricht einem DBTYPE_SQLVARIANT Wert im OLE DB- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anbieter von Native Client.  
  
 **SSVARIANT** ist eine unterscheidende Union. Abhängig vom Wert des vt-Elements kann der Consumer feststellen, welches Element gelesen werden soll. vt-Werte entsprechen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen. Die **SSVARIANT**-Struktur kann daher jeden SQL Server-Typ enthalten. Weitere Informationen zur Datenstruktur für standardmäßige OLE DB-Typen finden Sie unter [Typindikatoren](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Hinweise  
 Wenn DataTypeCompat auf „80“ festgelegt ist, werden verschiedene **SSVARIANT**-Untertypen zu Zeichenfolgen. Beispielsweise werden die folgenden vt-Werte in **SSVARIANT** als VT_SS_WVARSTRING angezeigt:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Wenn DateTypeCompat auf "0" festgelegt ist, werden diese Typen in ihrer systemeigenen Form angezeigt.  
  
 Weitere Informationen zu SSPROP_INIT_DATATYPECOMPATIBILITY finden Sie unter [Verwenden von Schlüsselwörtern für Verbindungs Zeichenfolgen mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Die Datei sqlncli. h enthält Variant-Zugriffs Makros, die das Dereferenzieren der Elementtypen in der **SSVARIANT** -Struktur vereinfachen. Beispielsweise können Sie V_SS_DATETIMEOFFSET folgendermaßen verwenden:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Den gesamten Satz von Zugriffs Makros für jedes Element der **SSVARIANT** -Struktur finden Sie in der Datei sqlncli. Hi.  
  
 In der folgenden Tabelle werden die Elemente der **SSVARIANT**-Struktur beschrieben:  
  
|Member|OLE DB-Typindikator|OLE DB-C-Datentyp|vt-Wert|Kommentare|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||Gibt den Typ des Werts in der **SSVARIANT**-Struktur an.|  
|bTinyIntVal|DBTYPE_UI1|**Hobby**|**VT_SS_UI1**|Unterstützt den **tinyint** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|sShortIntVal|DBTYPE_I2|**Kurzem**|**VT_SS_I2**|Unterstützt den **smallint** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|lIntVal|DBTYPE_I4|**Lange**|**VT_SS_I4**|Unterstützt den **int** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Unterstützt den **bigint** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Unterstützt den **Real** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Unterstützt den **float** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Unterstützt die Datentypen **money** und **smallmoney**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Unterstützt den **Bit** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Unterstützt den **uniqueidentifier** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Unterstützt den **numerischen** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Unterstützt den **Date** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Unterstützt die Datentypen **smalldatetime**, **datetime** und **datetime2**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Unterstützt den **time** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**BYTE**) Gibt die Skalierung für den *tTime2Val*-Wert an.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Unterstützt den **datetime2** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**BYTE**) Gibt die Skalierung für den *tsDataTimeVal*-Wert an.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Unterstützt den **DateTimeOffset** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**BYTE**) Gibt die Skalierung für den *tsoDateTimeOffsetVal*-Wert an.|  
|NCharVal|Kein entsprechender OLE DB-Typindikator.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Unterstützt die Datentypen **nchar** und **nvarchar**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**SHORT**) Gibt die tatsächliche Länge der Zeichenfolge an, auf die *pwchNCharVal* verweist. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (**SHORT**) Gibt die maximale Länge der Zeichenfolge an, auf die *pwchNCharVal* verweist.<br /><br /> *pwchNCharVal* (**WCHAR** \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member: *rgbReserved*, *dwReserved* und *pwchReserved*.|  
|CharVal|Kein entsprechender OLE DB-Typindikator.|**struct_CharVal**|**VT_SS_WVARSTRING**<br /><br /> **VT_SS_WVARSTRING**|Unterstützt die Datentypen **char** und **varchar**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**SHORT**) Gibt die tatsächliche Länge der Zeichenfolge an, auf die *pchCharVal* verweist. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (**SHORT**) Gibt die maximale Länge der Zeichenfolge an, auf die *pchCharVal* verweist.<br /><br /> *pwchCharVal* (**CHAR** \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member:<br /><br /> *rgbReserved*, *dwReserved* und *pwchReserved*.|  
|BinaryVal|Kein entsprechender OLE DB-Typindikator.|**struct_BinaryVal**|**VT_SS_VARBINARY**<br /><br /> **VT_SS_BINARY**|Unterstützt die Datentypen **binary** und **varbinary**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**SHORT**) Gibt die tatsächliche Länge der Daten an, auf die *prgbBinaryVal* verweist.<br /><br /> *sMaxLength* (**SHORT**) Gibt die maximale Länge der Daten an, auf die *prgbBinaryVal* verweist.<br /><br /> *prgbBinaryVal* (**BYTE** \*) Zeiger auf die Binärdaten.<br /><br /> Nicht verwendeter Member: *dwReserved*.|  
|UnknownType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
|BLOBType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
