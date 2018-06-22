---
title: SSVARIANT-Struktur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c8d98a54155179fe481fc0a7202a07e6cbf2aff
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149679"
---
# <a name="ssvariant-structure"></a>SSVARIANT-Struktur
  Die `SSVARIANT`-Struktur, die in sqlncli.h definiert ist, entspricht einem DBTYPE_SQLVARIANT-Wert im OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 `SSVARIANT` ist eine unterscheidende Vereinigung. Abhängig vom Wert des Elements vt kann der Consumer welches Element gelesen bestimmen. VT-Werte entsprechen den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen. Die `SSVARIANT`-Struktur kann daher jeden SQL Server-Typ enthalten. Weitere Informationen über die Datenstruktur für OLE DB-Standardtypen finden Sie unter [Typindikatoren](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Hinweise  
 Wenn DataTypeCompat auf "80" festgelegt ist, werden verschiedene `SSVARIANT`-Untertypen zu Zeichenfolgen. Beispielsweise werden die folgenden vt-Werte in `SSVARIANT` als VT_SS_WVARSTRING angezeigt:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Wenn DateTypeCompat auf "0" festgelegt ist, werden diese Typen in ihrer systemeigenen Form angezeigt.  
  
 Weitere Informationen zu SSPROP_INIT_DATATYPECOMPATIBILITY finden Sie unter [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Die Datei sqlncli.h enthält VARIANT-Zugriffsmakros, die das Dereferenzieren der Elementtypen der `SSVARIANT`-Struktur vereinfachen. Beispielsweise können Sie V_SS_DATETIMEOFFSET folgendermaßen verwenden:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Den vollständigen Satz der Zugriffsmakros für jeden Member der `SSVARIANT`-Struktur finden Sie in der Datei sqlncli.hi.  
  
 In der folgenden Tabelle sind die Elemente der `SSVARIANT`-Struktur beschrieben.  
  
|Member|OLE DB-Typindikator|OLE DB-C-Datentyp|vt-Wert|Kommentare|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Gibt den Typ des Werts in der `SSVARIANT` Struktur.|  
|bTinyIntVal|DBTYPE_UI1|`BYTE`|`VT_SS_UI1`|Unterstützt die `tinyint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.|  
|sShortIntVal|DBTYPE_I2|`SHORT`|`VT_SS_I2`|Unterstützt die `smallint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.|  
|lIntVal|DBTYPE_I4|`LONG`|`VT_SS_I4`|Unterstützt die `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.|  
|llBigIntVal|DBTYPE_I8|`LARGE_INTEGER`|`VT_SS_I8`|Unterstützt die `bigint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.|  
|fltRealVal|DBTYPE_R4|`float`|`VT_SS_R4`|Unterstützt die `real` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.|  
|dblFloatVal|DBTYPE_R8|`double`|`VT_SS_R8`|Unterstützt die `float` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.|  
|cyMoneyVal|DBTYPE_CY|`LARGE_INTEGER`|**VT_SS_MONEY VT_SS_SMALLMONEY**|Unterstützt die `money` und **Smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen.|  
|fBitVal|DBTYPE_BOOL|`VARIANT_BOOL`|`VT_SS_BIT`|Unterstützt die `bit` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.|  
|rgbGuidVal|DBTYPE_GUID|`GUID`|`VT_SS_GUID`|Unterstützt die `uniqueidentifier` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.|  
|numNumericVal|DBTYPE_NUMERIC|`DB_NUMERIC`|`VT_SS_NUMERIC`|Unterstützt die `numeric` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.|  
|dDateVal|DBTYPE_DATE|`DBDATE`|`VT_SS_DATE`|Unterstützt die `date` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|Unterstützt die `smalldatetime`, `datetime`, und `datetime2` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen.|  
|Time2Val|DBTYPE_DBTIME2|`DBTIME2`|`VT_SS_TIME2`|Unterstützt die `time` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tTime2Val* (`DBTIME2`)<br /><br /> *bScale* (`BYTE`) gibt den Maßstab für *tTime2Val* Wert.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_DATETIME2`|Unterstützt die `datetime2` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *TsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (`BYTE`) gibt den Maßstab für *TsDataTimeVal* Wert.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|Unterstützt die `datetimeoffset` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *TsoDateTimeOffsetVal* (`DBTIMESTAMPOFFSET`)<br /><br /> *bScale* (`BYTE`) gibt den Maßstab für *TsoDateTimeOffsetVal* Wert.|  
|NCharVal|Kein entsprechender OLE DB-Typindikator.|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|Unterstützt die `nchar` und **Nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (`SHORT`) gibt an, die tatsächliche Länge der Zeichenfolge an, auf dem *PwchNCharVal* Punkte. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (`SHORT`) gibt die maximale Länge für die Zeichenfolge an, auf die *PwchNCharVal* Punkte.<br /><br /> *PwchNCharVal* (`WCHAR` \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member: *RgbReserved*, *DwReserved*, und *PwchReserved*.|  
|CharVal|Kein entsprechender OLE DB-Typindikator.|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|Unterstützt die `char` und **Varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (`SHORT`) gibt die tatsächliche Länge der Zeichenfolge an, auf dem *PchCharVal* Punkte. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (`SHORT`) gibt die maximale Länge der Zeichenfolge an, auf dem *PchCharVal* Punkte.<br /><br /> *PchCharVal* (`CHAR` \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member:<br /><br /> *RgbReserved*, *DwReserved*, und *PwchReserved*.|  
|BinaryVal|Kein entsprechender OLE DB-Typindikator.|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|Unterstützt die `binary` und **Varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (`SHORT`) gibt die tatsächliche Länge für die Daten auf die *PrgbBinaryVal* Punkte.<br /><br /> *sMaxLength* (`SHORT`) gibt die maximale Länge für die Daten auf die *PrgbBinaryVal* Punkte.<br /><br /> *PrgbBinaryVal* (`BYTE` \*) Zeiger auf die Binärdaten.<br /><br /> Nicht verwendete Member: *DwReserved*.|  
|UnknownType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
|BLOBType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
  
## <a name="see-also"></a>Siehe auch  
 [Datentypen &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  