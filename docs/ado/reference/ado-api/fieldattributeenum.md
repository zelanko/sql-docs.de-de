---
title: FieldAttributeEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldAttributeEnum
helpviewer_keywords:
- FieldAttributeEnum enumeration [ADO]
ms.assetid: 6e34d886-005a-40dc-bd5c-6adcbf81e5cd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db3b72b7bdaf60febdeb41eb6f6e1e86c5064f63
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62653556"
---
# <a name="fieldattributeenum"></a>FieldAttributeEnum
Gibt einen oder mehrere Attribute einer [Feld](../../../ado/reference/ado-api/field-object.md) Objekt.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adFldCacheDeferred**|0x1000|Gibt an, dass der Anbieter die Feldwerte zwischenspeichert und nachfolgende Lesevorgänge aus dem Cache erfolgen.|  
|**adFldFixed**|0x10|Gibt an, dass das Feld-Daten fester Länge enthält.|  
|**adFldIsChapter**|0x2000|Gibt an, dass das Feld einen Kapitelwert enthält, der einem bestimmten untergeordneten Recordset im Zusammenhang mit diesem übergeordneten Felds angibt. Kapitel Felder werden in der Regel mit Daten zu strukturieren oder Filtern verwendet.|  
|**adFldIsCollection**|0x40000|Gibt an, dass das Feld gibt an, dass die Ressource, dargestellt durch den Datensatz eine Auflistung von anderen Ressourcen, z. B. einen Ordner, anstatt eine einfache Ressource, z. B. eine Textdatei.|  
|**adFldKeyColumn**|0x8000|Gibt an, dass das Feld alle oder einen Teil des Primärschlüssels der Spalte angibt.|  
|**adFldIsDefaultStream**|0x20000|Gibt an, dass das Feld den Standarddatenstrom für die Ressource, dargestellt durch den Datensatz enthält. Z. B. möglich der Standarddatenstrom der HTML-Inhalt von einem Stammordner für eine Website, die automatisch bereitgestellt wird, wenn die Stamm-URL angegeben ist.|  
|**adFldIsNullable**|0x20|Gibt an, dass das Feld null-Werte akzeptiert.|  
|**adFldIsRowURL**|0x10000|Gibt an, dass das Feld die URL enthält, die Namen die Ressource aus dem Datenspeicher durch den Eintrag dargestellt wird.|  
|**adFldLong**|0x80|Gibt an, dass das Feld eine lange binäre Feld ist. Außerdem zeigt es an, dass Sie verwenden können, die [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) und [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) Methoden.|  
|**adFldMayBeNull**|0x40|Gibt an, dass Sie null-Werte aus dem Feld lesen können.|  
|**adFldMayDefer**|0x2|Gibt an, dass das Feld, verzögert wird, die Feldwerte werden nicht aus der Datenquelle mit dem gesamten Datensatz, aber nur, wenn Sie explizit darauf zugegriffen werden abgerufen.|  
|**adFldNegativeScale**|0x4000|Gibt an, dass das Feld einen numerischen Wert aus einer Spalte darstellt, die negative Skalierungswerte unterstützt. Die Skalierung wird angegeben, indem die [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) Eigenschaft.|  
|**adFldRowID**|0x100|Gibt an, dass das Feld einen permanenten Zeilenbezeichner, der nicht geschrieben werden kann und keinen inhaltlichen Wert die Zeile (z. B. eine Datensatznummer, eindeutiger Bezeichner usw. enthält) zu identifizieren.|  
|**adFldRowVersion**|0x200|Gibt an, dass das Feld eine Art des Stapels für Datum oder Uhrzeit verwendet, um Updates zu verfolgen enthält.|  
|**adFldUnknownUpdatable**|0x8|Gibt an, dass der Anbieter nicht bestimmen kann, wenn Sie in das Feld schreiben können.|  
|**adFldUnspecified**|-1 "0xFFFFFFFF"|Gibt an, dass der Anbieter die Feldattribute nicht angegeben werden.|  
|**adFldUpdatable**|0x4|Gibt an, dass Sie in das Feld schreiben können.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.FieldAttribute.CACHEDEFERRED|  
|AdoEnums.FieldAttribute.FIXED|  
|AdoEnums.FieldAttribute.ISNULLABLE|  
|AdoEnums.FieldAttribute.LONG|  
|AdoEnums.FieldAttribute.MAYBENULL|  
|AdoEnums.FieldAttribute.MAYDEFER|  
|AdoEnums.FieldAttribute.NEGATIVESCALE|  
|AdoEnums.FieldAttribute.ROWID|  
|AdoEnums.FieldAttribute.ROWVERSION|  
|AdoEnums.FieldAttribute.UNKNOWNUPDATABLE|  
|AdoEnums.FieldAttribute.UNSPECIFIED|  
|AdoEnums.FieldAttribute.UPDATABLE|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Append-Methode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[Attributes-Eigenschaft (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)|
