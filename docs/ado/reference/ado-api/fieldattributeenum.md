---
description: FieldAttributeEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: fd8910f07b5f30170e8addd90fa41ab3299fbda5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443762"
---
# <a name="fieldattributeenum"></a>FieldAttributeEnum
Gibt ein oder mehrere Attribute eines [Feld](../../../ado/reference/ado-api/field-object.md) Objekts an.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adfldcachedeferred**|0x1000|Gibt an, dass der Anbieter Feldwerte zwischenspeichert und nachfolgende Lesevorgänge aus dem Cache durchgeführt werden.|  
|**adfldfixed**|0x10|Gibt an, dass das Feld Daten fester Länge enthält.|  
|**adfldischapter**|0x2000|Gibt an, dass das Feld einen Kapitel Wert enthält, der ein bestimmtes untergeordnetes Recordset angibt, das mit diesem übergeordneten Feld verknüpft ist. In der Regel werden Kapitel Felder mit Daten Strukturierung oder Filtern verwendet.|  
|**adfldiscollection**|0x40000|Gibt an, dass das Feld angibt, dass die durch den Datensatz dargestellte Ressource eine Auflistung anderer Ressourcen, z. b. ein Ordner, und keine einfache Ressource (z. b. eine Textdatei) ist.|  
|**adfldkeycolumn**|0x8000|Gibt an, dass das Feld den gesamten oder einen Teil des Primärschlüssels der Spalte angibt.|  
|**adfldisdefaultstream**|0x20000|Gibt an, dass das Feld den Standardstream für die durch den Datensatz dargestellte Ressource enthält. Der Standarddaten Strom kann z. b. der HTML-Inhalt eines Stamm Ordners auf einer Website sein, der automatisch bedient wird, wenn die Stamm-URL angegeben wird.|  
|**adfldisnullable**|0x20|Gibt an, dass das Feld NULL-Werte akzeptiert.|  
|**adfldisrowurl**|0x10000|Gibt an, dass das Feld die URL enthält, die die Ressource aus dem Datenspeicher benennt, der durch den Datensatz dargestellt wird.|  
|**adfldlong**|0x80|Gibt an, dass das Feld ein langes binäres Feld ist. Gibt auch an, dass Sie die [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) -Methode und die [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) -Methode verwenden können.|  
|**adfldmaybenull**|0x40|Gibt an, dass Sie NULL-Werte aus dem Feld lesen können.|  
|**adfldmayverzögert**|0x2|Gibt an, dass das Feld verzögert ist, d. h. die Feldwerte werden nicht aus der Datenquelle mit dem gesamten Datensatz abgerufen, sondern nur, wenn Sie explizit darauf zugreifen.|  
|**adfldnegativescale**|0x4000|Gibt an, dass das Feld einen numerischen Wert aus einer Spalte darstellt, die negative Skalierungs Werte unterstützt. Die Skala wird durch die [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) -Eigenschaft angegeben.|  
|**adfldrowid**|0x100|Gibt an, dass das Feld einen beständigen Zeilen Bezeichner enthält, in den nicht geschrieben werden kann, und der keinen sinnvollen Wert aufweist, außer um die Zeile zu identifizieren (z. b. eine Datensatznummer, einen eindeutigen Bezeichner usw.|  
|**adfldrow-Version**|0x200|Gibt an, dass das Feld eine Art Zeit oder einen Datumsstempel enthält, die zum Nachverfolgen von Updates verwendet wird.|  
|**adfldunknownupdatable**|0x8|Gibt an, dass der Anbieter nicht bestimmen kann, ob Sie in das Feld schreiben können.|  
|**adfldunangegebene**|-1 0xFFFFFFFF|Gibt an, dass der Anbieter die Feld Attribute nicht angibt.|  
|**adfldupdatable**|0x4|Gibt an, dass Sie in das Feld schreiben können.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstant|  
|--------------|  
|Adoumums. fieldattribute. cachedeferred|  
|Adoumums. fieldattribute. Fixed|  
|Adoumums. fieldattribute. IsNullable|  
|Adoumums. fieldattribute. Long|  
|Adoumums. fieldattribute. maybenull|  
|Adoumums. fieldattribute. mayverzögern|  
|Adoumums. fieldattribute. negativescale|  
|Adoerums. fieldattribute. ROWID|  
|Adoumums. fieldattribute. rowversion|  
|Adoumums. fieldattribute. unknownupdatable|  
|Adoumums. fieldattribute. nicht angegeben|  
|Adoumums. fieldattribute. Updatable|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Append-Methode (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
    :::column-end:::
    :::column:::
        [Attributes-Eigenschaft (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)  
    :::column-end:::
:::row-end:::
