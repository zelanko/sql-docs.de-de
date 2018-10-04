---
title: AbsolutePage-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AbsolutePage
helpviewer_keywords:
- AbsolutePage property [ADO]
ms.assetid: ddb58a35-ec3a-423c-a504-3c65e62c23d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efdbd68bf464fea3a0d59396380b082eb66375b8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47824148"
---
# <a name="absolutepage-property-ado"></a>AbsolutePage-Eigenschaft (ADO)
Gibt an, auf welche Seite des aktuellen Datensatzes gespeichert ist.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Für 32-Bit-Code, legt fest oder gibt einen **lange** Wert zwischen 1 und die Anzahl der Seiten in der [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt ([PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)), oder gibt Sie eine der der [PositionEnum ](../../../ado/reference/ado-api/positionenum.md) Werte.  
  
 Verwenden Sie für 64-Bit-Code einen Datentyp, der für die Speicherung eines 64-Bit-Werts bereitstellt. Beispielsweise können Sie entweder **lange** oder einen anderen Wert, der 64-Bit-Länge, z. B. DBORDINAL werden kann. Verwenden Sie keine **PositionEnum** Werte, da sie auf 32-Bit-Länge beschränkt sind.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft kann verwendet werden, um die Nummer der Seite zu identifizieren, auf der der aktuelle Datensatz gespeichert ist. Er verwendet die [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) Eigenschaft, um die Anzahl der insgesamt Rowset der logisch Aufteilen der **Recordset** Objekt in eine Reihe von Seiten, von denen jeder die Anzahl der Datensätze, die gleich hat **PageSize** (mit Ausnahme der letzten Seite, die dann weniger Datensätze haben kann). Der Anbieter muss die entsprechende Funktionalität für diese Eigenschaft zur Verfügung stehen unterstützen.  
  
-   Beim Abrufen oder Festlegen der **AbsolutePage** -Eigenschaft, die ADO verwendet die [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) Eigenschaft und die [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) -Eigenschaft wie folgt zusammen:  
  
-   Zum Abrufen der **AbsolutePage**, ADO ruft zunächst ab der **AbsolutePosition**, und klicken Sie dann, indem die **PageSize**.  
  
-   Festlegen der **AbsolutePage**, ADO wechselt die **AbsolutePosition** wie folgt: multipliziert es die **PageSize** durch die neue **AbsolutePage** Wert, und klicken Sie dann den Wert 1 hinzugefügt. Daher die aktuelle position in der **Recordset** nach dem erfolgreichen festlegen **AbsolutePage** ist der erste Datensatz in dieser Seite.  
  
 Wie die **AbsolutePosition** Eigenschaft **AbsolutePage** ist 1-basiert und entspricht 1, wenn der aktuelle Datensatz den ersten Datensatz in ist die **Recordset**. Legen Sie diese Eigenschaft auf den ersten Datensatz einer bestimmten Seite verschoben. Abrufen der Gesamtanzahl von Seiten aus der **PageCount** Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [AbsolutePage, PageCount und PageSize Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount und PageSize Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePosition-Eigenschaft (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [PageCount-Eigenschaft (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)   
 [PageSize-Eigenschaft (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)
