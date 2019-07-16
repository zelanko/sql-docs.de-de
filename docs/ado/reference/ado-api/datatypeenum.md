---
title: DataTypeEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataTypeEnum
helpviewer_keywords:
- DataTypeEnum enumeration [ADO]
ms.assetid: 2c57eca6-9336-4b06-ba10-9fef5926b1d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 27386894ce6d1d393505d49b4863a0ba9bf3320b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933225"
---
# <a name="datatypeenum"></a>DataTypeEnum
Gibt an, der den Datentyp des einen [Feld](../../../ado/reference/ado-api/field-object.md), [Parameter](../../../ado/reference/ado-api/parameter-object.md), oder [Eigenschaft](../../../ado/reference/ado-api/property-object-ado.md). Der entsprechende OLE DB-Typindikator wird in Klammern in der Spalte "Beschreibung" in der folgenden Tabelle dargestellt.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**AdArray**|0x2000|Immer ein Flagwert, kombiniert mit einer anderen Data Type Konstanten, die ein Array von den anderen Datentyp angibt. Gilt nicht für ADOX.|  
|**adBigInt**|20|Gibt eine 8-Byte-Ganzzahl mit Vorzeichen (DBTYPE_I8) an.|  
|**adBinary**|128|Gibt einen Binärwert (DBTYPE_BYTES) an.|  
|**adBoolean**|11|Gibt eine **booleschen** Wert (DBTYPE_BOOL).|  
|**adBSTR**|8|Gibt eine Null-terminierte Zeichenfolge (Unicode) (DBTYPE_BSTR) an.|  
|**adChapter**|136|Gibt einen mit 4-Byte-Kapitelwert, der eine Zeile in einem untergeordneten-Rowset (DBTYPE_HCHAPTER) identifiziert.|  
|**adChar**|129|Gibt einen Zeichenfolgenwert (DBTYPE_STR).|  
|**adCurrency**|6|Gibt einen Currency-Wert (DBTYPE_CY). Währung ist eine Festkommazahl mit vier Ziffern rechts vom Dezimaltrennzeichen an. Es wird in eine 8-Byte-Ganzzahl mit Vorzeichen, skaliert mit 10.000 gespeichert.|  
|**adDate**|7|Gibt einen Datumswert (DBTYPE_DATE) an. Der ganzzahlige Teil davon ist die Anzahl der Tage seit dem 30. Dezember 1899 wieder, und der Bruchteil der ist der Bruchteil eines Tages ein Datum als einen Double-Wert gespeichert.|  
|**adDBDate**|133|Gibt einen Datumswert (JJJJMMTT) (DBTYPE_DBDATE).|  
|**adDBTime**|134|Gibt einen Zeitwert (Hhmmss) (DBTYPE_DBTIME).|  
|**adDBTimeStamp**|135|Gibt einen Datums-/Zeitstempel (Yyyymmddhhmmss plus eine Bruchzahl in Milliarden) (DBTYPE_DBTIMESTAMP).|  
|**adDecimal**|14|Gibt an, ein genauer numerischer Wert mit einer festen Genauigkeit und Dezimalstellenanzahl (DBTYPE_DECIMAL).|  
|**adDouble**|5|Gibt einen Gleitkommawert mit doppelter Genauigkeit (DBTYPE_R8) an.|  
|**adEmpty**|0|Gibt keinen Wert (DBTYPE_EMPTY).|  
|**adError**|10|Gibt einen 32-Bit-Fehlercode (DBTYPE_ERROR) an.|  
|**adFileTime**|64|Gibt einen 64-Bit-Wert, der die Anzahl der 100-Nanosekunden-Intervalle seit dem 1. Januar 1601 (darstellt DBTYPE_FILETIME) darstellt.|  
|**adGUID**|72|Gibt einen global eindeutigen Bezeichner (GUID) (DBTYPE_GUID) an.|  
|**adIDispatch**|9|Gibt einen Zeiger auf ein **IDispatch** Schnittstelle für COM-Objekt (zeigt DBTYPE_IDISPATCH).<br /><br /> **Beachten Sie** dieser Datentyp wird von ADO derzeit nicht unterstützt. Verwendung kann zu unvorhersehbaren Ergebnissen führen.|  
|**adInteger**|3|Gibt eine vier-Byte-Ganzzahl mit Vorzeichen (DBTYPE_I4) an.|  
|**adIUnknown**|13|Gibt einen Zeiger auf ein **IUnknown** Schnittstelle für COM-Objekt (DBTYPE_IUNKNOWN).<br /><br /> **Beachten Sie** dieser Datentyp wird von ADO derzeit nicht unterstützt. Verwendung kann zu unvorhersehbaren Ergebnissen führen.|  
|**adLongVarBinary**|205|Gibt an, einem langen Binärwert.|  
|**adLongVarChar**|201|Gibt einen Wert für die lange Zeichenfolge.|  
|**adLongVarWChar**|203|Gibt eine lange Null-terminierte Unicode-Zeichenfolgenwert an.|  
|**adNumeric**|131|Gibt an, ein genauer numerischer Wert mit einer festen Genauigkeit und Dezimalstellen (DBTYPE_NUMERIC).|  
|**adPropVariant**|138|Gibt an, ein Automation-PROPVARIANT (DBTYPE_PROP_VARIANT).|  
|**adSingle**|4|Gibt einen Gleitkommawert mit einfacher Genauigkeit (DBTYPE_R4) an.|  
|**adSmallInt**|2|Gibt eine zwei-Byte-Ganzzahl mit Vorzeichen (DBTYPE_I2) an.|  
|**adTinyInt**|16|Gibt eine 1-Byte-Ganzzahl mit Vorzeichen (DBTYPE_I1) an.|  
|**adUnsignedBigInt**|21|Gibt eine 8-Byte-Ganzzahl ohne Vorzeichen (DBTYPE_UI8) an.|  
|**adUnsignedInt**|19|Gibt eine vier-Byte-Ganzzahl ohne Vorzeichen (DBTYPE_UI4) an.|  
|**adUnsignedSmallInt**|18|Gibt eine 2-Byte-Ganzzahl ohne Vorzeichen (DBTYPE_UI2) an.|  
|**adUnsignedTinyInt**|17|Gibt eine 1-Byte-Ganzzahl ohne Vorzeichen (DBTYPE_UI1) an.|  
|**adUserDefined**|132|Gibt eine benutzerdefinierte Variable (DBTYPE_UDT) an.|  
|**adVarBinary**|204|Gibt einen Binärwert.|  
|**adVarChar**|200|Gibt einen Zeichenfolgenwert an.|  
|**adVariant**|12|Gibt ein Automatisierungsobjekt **Variant** (DBTYPE_VARIANT).<br /><br /> **Beachten Sie** dieser Datentyp wird von ADO derzeit nicht unterstützt. Verwendung kann zu unvorhersehbaren Ergebnissen führen.|  
|**adVarNumeric**|139|Gibt einen numerischen Wert an.|  
|**adVarWChar**|202|Gibt einen Null-terminierte Unicode-Zeichenfolge an.|  
|**adWChar**|130|Gibt einen Null-terminierte Unicode-Zeichenfolge (DBTYPE_WSTR) an.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.DataType.ARRAY|  
|AdoEnums.DataType.BIGINT|  
|AdoEnums.DataType.BINARY|  
|AdoEnums.DataType.BOOLEAN|  
|AdoEnums.DataType.BSTR|  
|AdoEnums.DataType.CHAPTER|  
|AdoEnums.DataType.CHAR|  
|AdoEnums.DataType.CURRENCY|  
|AdoEnums.DataType.DATE|  
|AdoEnums.DataType.DBDATE|  
|AdoEnums.DataType.DBTIME|  
|AdoEnums.DataType.DBTIMESTAMP|  
|AdoEnums.DataType.DECIMAL|  
|AdoEnums.DataType.DOUBLE|  
|AdoEnums.DataType.EMPTY|  
|AdoEnums.DataType.ERROR|  
|AdoEnums.DataType.FILETIME|  
|AdoEnums.DataType.GUID|  
|AdoEnums.DataType.IDISPATCH|  
|AdoEnums.DataType.INTEGER|  
|AdoEnums.DataType.IUNKNOWN|  
|AdoEnums.DataType.LONGVARBINARY|  
|AdoEnums.DataType.LONGVARCHAR|  
|AdoEnums.DataType.LONGVARWCHAR|  
|AdoEnums.DataType.NUMERIC|  
|AdoEnums.DataType.PROPVARIANT|  
|AdoEnums.DataType.SINGLE|  
|AdoEnums.DataType.SMALLINT|  
|AdoEnums.DataType.TINYINT|  
|AdoEnums.DataType.UNSIGNEDBIGINT|  
|AdoEnums.DataType.UNSIGNEDINT|  
|AdoEnums.DataType.UNSIGNEDSMALLINT|  
|AdoEnums.DataType.UNSIGNEDTINYINT|  
|AdoEnums.DataType.USERDEFINED|  
|AdoEnums.DataType.VARBINARY|  
|AdoEnums.DataType.VARCHAR|  
|AdoEnums.DataType.VARIANT|  
|AdoEnums.DataType.VARNUMERIC|  
|AdoEnums.DataType.VARWCHAR|  
|AdoEnums.DataType.WCHAR|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Append-Methode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[CreateParameter-Methode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|  
|[CreateRecordset-Methode (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)|[Type-Eigenschaft (ADO)](../../../ado/reference/ado-api/type-property-ado.md)|
