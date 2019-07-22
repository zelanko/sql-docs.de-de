---
title: SSVARIANT-Struktur | Microsoft-Dokumentation
description: SSVARIANT-Struktur in OLE DB Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 09ff4af7026ce75a8668db22910e550dc0c72857
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67995172"
---
# <a name="ssvariant-structure"></a>SSVARIANT-Struktur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die **SSVARIANT** -Struktur, die in "msoledbsql. h" definiert ist, entspricht einem DBTYPE_SQLVARIANT-Wert im OLE DB Treiber für SQL Server.  
  
 **SSVARIANT** ist eine diskriminierende Union. Abhängig vom Wert des vt-Elements kann der Consumer feststellen, welches Element gelesen werden soll. vt-Werte entsprechen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen. Die **SSVARIANT**-Struktur kann daher jeden SQL Server-Typ enthalten. Weitere Informationen zur Datenstruktur für Standard OLE DB Typen finden Sie unter [Typindikatoren](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Remarks  
 Wenn DataTypeCompat auf „80“ festgelegt ist, werden verschiedene **SSVARIANT**-Untertypen zu Zeichenfolgen. Beispielsweise werden die folgenden vt-Werte in **SSVARIANT** als VT_SS_WVARSTRING angezeigt:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Wenn DateTypeCompat auf "0" festgelegt ist, werden diese Typen in ihrer systemeigenen Form angezeigt.  
  
 Weitere Informationen zu SSPROP_INIT_DATATYPECOMPATIBILITY finden Sie unter [Verwenden von Schlüsselwörtern für Verbindungs Zeichenfolgen mit OLE DB-Treiber für SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 Die Datei „msoledbsql.h“ enthält VARIANT-Zugriffsmakros, die das Dereferenzieren der Elementtypen der **SSVARIANT**-Struktur vereinfachen. Beispielsweise können Sie V_SS_DATETIMEOFFSET folgendermaßen verwenden:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Den gesamten Satz von Zugriffs Makros für jedes Element der **SSVARIANT** -Struktur finden Sie in der Datei msoledbsql. h.  
  
 In der folgenden Tabelle werden die Elemente der **SSVARIANT**-Struktur beschrieben:  
  
|Member|OLE DB-Typindikator|OLE DB-C-Datentyp|vt-Wert|Kommentare|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||Gibt den Typ des Werts in der **SSVARIANT**-Struktur an.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|Unterstützt den **tinyint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|sShortIntVal|DBTYPE_I2|**SHORT**|**VT_SS_I2**|Unterstützt den **smallint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|Unterstützt den **int** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Unterstützt den **bigint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Unterstützt den **Real** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Unterstützt den **float** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Unterstützt die Datentypen **Money** und **smallmoney** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Unterstützt den **Bit** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Unterstützt den **uniqueidentifier** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Unterstützt den **numerischen** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datentyp.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Unterstützt den **date**-Datentyp von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Unterstützt die Datentypen " **smalldatetime**", " **DateTime**" und " **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ".|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Unterstützt den **time** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**Byte**) Gibt die Skala für den *tTime2Val* -Wert an.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Unterstützt den **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**Byte**) Gibt die Skalierung für den Wert " *tdatatimeval* " an.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Unterstützt den **DateTimeOffset** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**Byte**) Gibt die Skalierung für den Wert " *tsodatetimeoffsetval* " an.|  
|NCharVal|Kein entsprechender OLE DB-Typindikator.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Unterstützt die Datentypen **NCHAR** und **nvarchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**Kurz**) Gibt die tatsächliche Länge der Zeichenfolge an, auf die *pwchNCharVal* zeigt. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (**Kurz**) Gibt die maximale Länge für die Zeichenfolge an, auf die *pwchNCharVal* zeigt.<br /><br /> *pwchNCharVal* (**WCHAR** \*)-Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member: *rgbReserved*, *dwReserved*und *pwchReserved*.|  
|CharVal|Kein entsprechender OLE DB-Typindikator.|**struct_CharVal**|**VT_SS_WVARSTRING**<br /><br /> **VT_SS_WVARSTRING**|Unterstützt die Datentypen **char** und **varchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**Kurz**) Gibt die tatsächliche Länge der Zeichenfolge an, auf die *pchCharVal* zeigt. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (**Kurz**) Gibt die maximale Länge für die Zeichenfolge an, auf die *pchCharVal* zeigt.<br /><br /> *pchCharVal* (**Char** \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member:<br /><br /> *rgbReserved*, *dwReserved*und *pwchReserved*.|  
|BinaryVal|Kein entsprechender OLE DB-Typindikator.|**struct_BinaryVal**|**VT_SS_VARBINARY**<br /><br /> **VT_SS_BINARY**|Unterstützt die Datentypen **Binary** und **varbinary** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**Kurz**) Gibt die tatsächliche Länge der Daten an, auf die *prgbBinaryVal* verweist.<br /><br /> *sMaxLength* (**Kurz**) Gibt die maximale Länge für die Daten an, auf die *prgbBinaryVal* verweist.<br /><br /> *prgbBinaryVal* (**Byte** \*) Zeiger auf die Binärdaten.<br /><br /> Nicht verwendeter Member: *dwReserved*.|  
|UnknownType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
|BLOBType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
