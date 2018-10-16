---
title: SSVARIANT-Struktur | Microsoft-Dokumentation
description: SSVARIANT-Struktur in OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 484d8912c205f55dcebfacee01ec0c017b58117c
ms.sourcegitcommit: 0d6e4cafbb5d746e7d00fdacf8f3ce16f3023306
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49085197"
---
# <a name="ssvariant-structure"></a>SSVARIANT-Struktur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Die **SSVARIANT** -Struktur, die im msoledbsql.h definiert ist, entspricht einem DBTYPE_SQLVARIANT-Wert in der OLE DB-Treiber für SQL Server.  
  
 **SSVARIANT** ist eine unterscheidende Vereinigung. Abhängig vom Wert des vt-Elements kann der Consumer feststellen, welches Element gelesen werden soll. vt-Werte entsprechen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen. Die **SSVARIANT**-Struktur kann daher jeden SQL Server-Typ enthalten. Weitere Informationen zur Datenstruktur für OLE DB-Standardtypen finden Sie unter [Type Indicators](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Remarks  
 Wenn DataTypeCompat auf „80“ festgelegt ist, werden verschiedene **SSVARIANT**-Untertypen zu Zeichenfolgen. Beispielsweise werden die folgenden vt-Werte in **SSVARIANT** als VT_SS_WVARSTRING angezeigt:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Wenn DateTypeCompat auf "0" festgelegt ist, werden diese Typen in ihrer systemeigenen Form angezeigt.  
  
 Weitere Informationen zu SSPROP_INIT_DATATYPECOMPATIBILITY finden Sie unter [Schlüsselwörtern für Verbindungszeichenfolgen mit OLE DB-Treiber für SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 Die Datei „msoledbsql.h“ enthält VARIANT-Zugriffsmakros, die das Dereferenzieren der Elementtypen der **SSVARIANT**-Struktur vereinfachen. Beispielsweise können Sie V_SS_DATETIMEOFFSET folgendermaßen verwenden:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Den vollständigen Satz der zugriffsmakros für jedes Element der **SSVARIANT** Struktur, finden Sie in der Datei msoledbsql.h.  
  
 In der folgenden Tabelle werden die Elemente der **SSVARIANT**-Struktur beschrieben:  
  
|Member|OLE DB-Typindikator|OLE DB-C-Datentyp|vt-Wert|Kommentare|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Gibt den Typ des Werts in der **SSVARIANT**-Struktur an.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|Unterstützt die **Tinyint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|sShortIntVal|DBTYPE_I2|**SHORT**|**VT_SS_I2**|Unterstützt die **Smallint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|Unterstützt die **Int** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Unterstützt die **Bigint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Unterstützt die **echte** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Unterstützt die **"float"** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Unterstützt die **Geld** und **Smallmoney** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen.|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Unterstützt die **Bit** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Unterstützt die **Uniqueidentifier** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Unterstützt die **numerischen** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Unterstützt den **date**-Datentyp von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Unterstützt die **Smalldatetime**, **"DateTime"**, und **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen.|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Unterstützt die **Zeit** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**BYTE**) gibt an, für die Dezimalstellen *tTime2Val* Wert.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Unterstützt die **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *TsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**BYTE**) gibt an, für die Dezimalstellen *TsDataTimeVal* Wert.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Unterstützt die **Datetimeoffset** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *TsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**BYTE**) gibt an, für die Dezimalstellen *TsoDateTimeOffsetVal* Wert.|  
|NCharVal|Kein entsprechender OLE DB-Typindikator.|**Struktur _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Unterstützt die **Nchar** und **Nvarchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**kurze**) gibt an, die tatsächliche Länge der Zeichenfolge, mit der *PwchNCharVal* Punkte. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (**kurze**) gibt die maximale Länge für die Zeichenfolge, die die *PwchNCharVal* Punkte.<br /><br /> *PwchNCharVal* (**WCHAR** \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member: *RgbReserved*, *DwReserved*, und *PwchReserved*.|  
|CharVal|Kein entsprechender OLE DB-Typindikator.|**Struktur _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Unterstützt die **Char** und **Varchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**kurze**) gibt an, die tatsächliche Länge der Zeichenfolge, mit der *PchCharVal* Punkte. Beinhaltet nicht den abschließenden Nullwert.<br /><br /> *sMaxLength* (**kurze**) gibt die maximale Länge für die Zeichenfolge, die die *PchCharVal* Punkte.<br /><br /> *PchCharVal* (**CHAR** \*) Zeiger auf die Zeichenfolge.<br /><br /> Nicht verwendete Member:<br /><br /> *RgbReserved*, *DwReserved*, und *PwchReserved*.|  
|BinaryVal|Kein entsprechender OLE DB-Typindikator.|**Struktur _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Unterstützt die **binäre** und **Varbinary** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen.<br /><br /> Beinhaltet die folgenden Member:<br /><br /> *sActualLength* (**kurze**) gibt an, die tatsächliche Länge der Daten auf die *PrgbBinaryVal* Punkte.<br /><br /> *sMaxLength* (**kurze**) gibt die maximale Länge für die Daten auf die *PrgbBinaryVal* Punkte.<br /><br /> *PrgbBinaryVal* (**BYTE** \*) Zeiger auf die binären Daten.<br /><br /> Nicht verwendete Member: *DwReserved*.|  
|UnknownType|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
|"Blobtype"|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|NICHT VERWENDET|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Datentypen &#40;OLE-DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
