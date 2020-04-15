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
ms.openlocfilehash: cd20624744c9870cf5688c22af751d29d990a2db
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296991"
---
# <a name="ssvariant-structure"></a>SSVARIANT-Struktur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die **SSVARIANT-Struktur,** die in sqlncli.h definiert ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entspricht einem DBTYPE_SQLVARIANT Wert im nativen Client-OLEDB-Anbieter.  
  
 **SSVARIANT** ist eine unterscheidende Union. Abhängig vom Wert des vt-Elements kann der Consumer feststellen, welches Element gelesen werden soll. vt-Werte entsprechen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen. Die **SSVARIANT**-Struktur kann daher jeden SQL Server-Typ enthalten. Weitere Informationen zur Datenstruktur für standardmäßige OLE DB-Typen finden Sie unter [Typindikatoren](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn DataTypeCompat auf „80“ festgelegt ist, werden verschiedene **SSVARIANT**-Untertypen zu Zeichenfolgen. Beispielsweise werden die folgenden vt-Werte in **SSVARIANT** als VT_SS_WVARSTRING angezeigt:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Wenn DateTypeCompat auf "0" festgelegt ist, werden diese Typen in ihrer systemeigenen Form angezeigt.  
  
 Weitere Informationen zu SSPROP_INIT_DATATYPECOMPATIBILITY finden Sie unter [Verwenden von Verbindungszeichenfolgenschlüsselwörtern mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Die Datei sqlncli.h enthält Variantenzugriffsmakros, die das Abverweisen der Elementtypen in der **SSVARIANT-Struktur** vereinfachen. Beispielsweise können Sie V_SS_DATETIMEOFFSET folgendermaßen verwenden:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Den vollständigen Satz von Zugriffsmakros für jedes Element der **SSVARIANT-Struktur** finden Sie in der Datei sqlncli.hi.  
  
 In der folgenden Tabelle werden die Elemente der **SSVARIANT**-Struktur beschrieben:  
  
|Member|OLE DB-Typindikator|OLE DB-C-Datentyp|vt-Wert|Kommentare|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||Gibt den Typ des Werts in der **SSVARIANT**-Struktur an.|  
|bTinyIntVal|DBTYPE_UI1|**Byte**|**VT_SS_UI1**|Unterstützt den **tinyint-Datentyp.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|sShortIntVal|DBTYPE_I2|**kurz**|**VT_SS_I2**|Unterstützt den **Smallint-Datentyp.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|lIntVal|DBTYPE_I4|**Lange**|**VT_SS_I4**|Unterstützt den **int-Datentyp.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Unterstützt den **Bigint-Datentyp.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Unterstützt den **echten** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Unterstützt den Float-Datentyp. **float** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Unterstützt die Datentypen **money** und **smallmoney**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Unterstützt den **Bitdatentyp.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|rgbGuidVal|DBTYPE_GUID|**Guid**|**VT_SS_GUID**|Unterstützt den **UniqueIdentifier-Datentyp.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Unterstützt den **numerischen** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Unterstützt den **Datumsdatentyp.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Unterstützt die Datentypen **smalldatetime**, **datetime** und **datetime2**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Unterstützt den **Zeitdatentyp.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**BYTE**) Gibt die Skalierung für den *tTime2Val*-Wert an.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Unterstützt den **Datentyp datetime2.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**BYTE**) Gibt die Skalierung für den *tsDataTimeVal*-Wert an.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Unterstützt den **Datentyp datetimeoffset.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**BYTE**) Gibt die Skalierung für den *tsoDateTimeOffsetVal*-Wert an.|  
|NCharVal|Kein entsprechender OLE DB-Typindikator.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Unterstützt die Datentypen **nchar** und **nvarchar**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**SHORT**) Gibt die tatsächliche Länge der Zeichenfolge an, auf die *pwchNCharVal* verweist. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (**SHORT**) Gibt die maximale Länge der Zeichenfolge an, auf die *pwchNCharVal* verweist.<br /><br /> *pwchNCharVal* (**WCHAR** \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member: *rgbReserved*, *dwReserved* und *pwchReserved*.|  
|CharVal|Kein entsprechender OLE DB-Typindikator.|**struct_CharVal**|**VT_SS_WVARSTRING**<br /><br /> **VT_SS_WVARSTRING**|Unterstützt die Datentypen **char** und **varchar**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**SHORT**) Gibt die tatsächliche Länge der Zeichenfolge an, auf die *pchCharVal* verweist. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (**SHORT**) Gibt die maximale Länge der Zeichenfolge an, auf die *pchCharVal* verweist.<br /><br /> *pwchCharVal* (**CHAR** \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member:<br /><br /> *rgbReserved*, *dwReserved* und *pwchReserved*.|  
|BinaryVal|Kein entsprechender OLE DB-Typindikator.|**struct_BinaryVal**|**VT_SS_VARBINARY**<br /><br /> **VT_SS_BINARY**|Unterstützt die Datentypen **binary** und **varbinary**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**SHORT**) Gibt die tatsächliche Länge der Daten an, auf die *prgbBinaryVal* verweist.<br /><br /> *sMaxLength* (**SHORT**) Gibt die maximale Länge der Daten an, auf die *prgbBinaryVal* verweist.<br /><br /> *prgbBinaryVal* (**BYTE** \*) Zeiger auf die Binärdaten.<br /><br /> Nicht verwendeter Member: *dwReserved*.|  
|UnknownType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
|BLOBType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
