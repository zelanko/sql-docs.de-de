---
title: SSVARIANT-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f60e644d5896fd25ce57df3326a980b9681ea714
ms.sourcegitcommit: 0d6e4cafbb5d746e7d00fdacf8f3ce16f3023306
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49085098"
---
# <a name="ssvariant-structure"></a>SSVARIANT-Struktur
  Die `SSVARIANT`-Struktur, die in sqlncli.h definiert ist, entspricht einem DBTYPE_SQLVARIANT-Wert im OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 `SSVARIANT` ist eine unterscheidende Vereinigung. Abhängig vom Wert des vt-Elements kann der Consumer feststellen, welches Element gelesen werden soll. vt-Werte entsprechen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen. Die `SSVARIANT`-Struktur kann daher jeden SQL Server-Typ enthalten. Weitere Informationen zur Datenstruktur für OLE DB-Standardtypen finden Sie unter [Type Indicators](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Hinweise  
 Wenn DataTypeCompat auf "80" festgelegt ist, werden verschiedene `SSVARIANT`-Untertypen zu Zeichenfolgen. Beispielsweise werden die folgenden vt-Werte in `SSVARIANT` als VT_SS_WVARSTRING angezeigt:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Wenn DateTypeCompat auf "0" festgelegt ist, werden diese Typen in ihrer systemeigenen Form angezeigt.  
  
 Weitere Informationen zu SSPROP_INIT_DATATYPECOMPATIBILITY finden Sie unter [Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Die Datei sqlncli.h enthält VARIANT-Zugriffsmakros, die das Dereferenzieren der Elementtypen der `SSVARIANT`-Struktur vereinfachen. Beispielsweise können Sie V_SS_DATETIMEOFFSET folgendermaßen verwenden:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Den vollständigen Satz der Zugriffsmakros für jeden Member der `SSVARIANT`-Struktur finden Sie in der Datei sqlncli.hi.  
  
 In der folgenden Tabelle sind die Elemente der `SSVARIANT`-Struktur beschrieben.  
  
|Member|OLE DB-Typindikator|OLE DB-C-Datentyp|vt-Wert|Kommentare|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Gibt den Typ des Werts in der `SSVARIANT`-Struktur an.|  
|bTinyIntVal|DBTYPE_UI1|`BYTE`|`VT_SS_UI1`|Unterstützt den `tinyint`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|sShortIntVal|DBTYPE_I2|`SHORT`|`VT_SS_I2`|Unterstützt den `smallint`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|lIntVal|DBTYPE_I4|`LONG`|`VT_SS_I4`|Unterstützt den `int`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|llBigIntVal|DBTYPE_I8|`LARGE_INTEGER`|`VT_SS_I8`|Unterstützt den `bigint`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|fltRealVal|DBTYPE_R4|`float`|`VT_SS_R4`|Unterstützt den `real`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|dblFloatVal|DBTYPE_R8|`double`|`VT_SS_R8`|Unterstützt den `float`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|cyMoneyVal|DBTYPE_CY|`LARGE_INTEGER`|**VT_SS_MONEY VT_SS_SMALLMONEY**|Unterstützt die `money` und **Smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen.|  
|fBitVal|DBTYPE_BOOL|`VARIANT_BOOL`|`VT_SS_BIT`|Unterstützt den `bit`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rgbGuidVal|DBTYPE_GUID|`GUID`|`VT_SS_GUID`|Unterstützt den `uniqueidentifier`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|numNumericVal|DBTYPE_NUMERIC|`DB_NUMERIC`|`VT_SS_NUMERIC`|Unterstützt den `numeric`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|dDateVal|DBTYPE_DATE|`DBDATE`|`VT_SS_DATE`|Unterstützt den `date`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|Unterstützt die Datentypen `smalldatetime`, `datetime` und `datetime2` von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Time2Val|DBTYPE_DBTIME2|`DBTIME2`|`VT_SS_TIME2`|Unterstützt den `time`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tTime2Val* (`DBTIME2`)<br /><br /> *bScale* (`BYTE`) gibt an, für die Dezimalstellen *tTime2Val* Wert.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_DATETIME2`|Unterstützt den `datetime2`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *TsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (`BYTE`) gibt an, für die Dezimalstellen *TsDataTimeVal* Wert.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|Unterstützt den `datetimeoffset`-Datentyp von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *TsoDateTimeOffsetVal* (`DBTIMESTAMPOFFSET`)<br /><br /> *bScale* (`BYTE`) gibt an, für die Dezimalstellen *TsoDateTimeOffsetVal* Wert.|  
|NCharVal|Kein entsprechender OLE DB-Typindikator.|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|Unterstützt die `nchar` und **Nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (`SHORT`) gibt an, die tatsächliche Länge der Zeichenfolge, mit der *PwchNCharVal* Punkte. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (`SHORT`) gibt die maximale Länge für die Zeichenfolge, die die *PwchNCharVal* Punkte.<br /><br /> *PwchNCharVal* (`WCHAR` \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member: *RgbReserved*, *DwReserved*, und *PwchReserved*.|  
|CharVal|Kein entsprechender OLE DB-Typindikator.|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|Unterstützt die `char` und **Varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (`SHORT`) gibt an, die tatsächliche Länge der Zeichenfolge, mit der *PchCharVal* Punkte. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (`SHORT`) gibt die maximale Länge für die Zeichenfolge, die die *PchCharVal* Punkte.<br /><br /> *PchCharVal* (`CHAR` \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member:<br /><br /> *RgbReserved*, *DwReserved*, und *PwchReserved*.|  
|BinaryVal|Kein entsprechender OLE DB-Typindikator.|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|Unterstützt die `binary` und **Varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (`SHORT`) gibt an, die tatsächliche Länge der Daten auf die *PrgbBinaryVal* Punkte.<br /><br /> *sMaxLength* (`SHORT`) gibt die maximale Länge für die Daten auf die *PrgbBinaryVal* Punkte.<br /><br /> *PrgbBinaryVal* (`BYTE` \*) Zeiger auf die binären Daten.<br /><br /> Nicht verwendete Member: *DwReserved*.|  
|UnknownType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
|"Blobtype"|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
  
## <a name="see-also"></a>Siehe auch  
 [Datentypen &#40;OLE-DB&#41;](data-types-ole-db.md)  
  
  
