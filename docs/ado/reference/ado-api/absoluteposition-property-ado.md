---
title: AbsolutePosition-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AbsolutePosition
helpviewer_keywords:
- AbsolutePosition property [ADO]
ms.assetid: 79f8ee5e-fc70-46d8-8c29-ebf943c66592
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 467834d2cfd5e56c14d9c7565d6749fa6848251e
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718348"
---
# <a name="absoluteposition-property-ado"></a>AbsolutePosition-Eigenschaft (ADO)
Gibt an, der die Position des ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) aktuellen Datensatz des Objekts.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Für 32-Bit-Code, legt fest oder gibt einen **lange** Wert zwischen 1 und die Anzahl der Datensätze in der **Recordset** Objekt ([RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)), oder gibt Sie eine der der [ PositionEnum](../../../ado/reference/ado-api/positionenum.md) Werte.  
  
 Verwenden Sie für 64-Bit-Code einen Datentyp, der für die Speicherung eines 64-Bit-Werts bereitstellt. Sie können z. B. verwenden Long-Wert oder einen anderen Wert, der 64-Bit-Länge, z. B. DBORDINAL. Verwenden Sie keine **PositionEnum** Werte, da sie auf 32-Bit-Länge beschränkt sind.  
  
## <a name="remarks"></a>Hinweise  
 Zum Festlegen der **AbsolutePosition** -Eigenschaft, die ADO erfordert, dass es sich bei implementiert die OLE DB-Anbieter, die Sie verwenden die [IRowsetLocate:IRowset](https://msdn.microsoft.com/library/windows/desktop/ms721190.aspx) Schnittstelle.  
  
 Zugriff auf die **AbsolutePosition** Eigenschaft eine **Recordset** , die entweder mit geöffnet wurde, einen Vorwärtscursor oder dynamischer Cursor löst den Fehler **AdErrFeatureNotAvailable**. Mit anderen Cursortypen, die richtige Position wird zurückgegeben, solange der OLE DB-Anbieter unterstützt die **IRowsetScroll:IRowsetLocate** Schnittstelle. Wenn der Anbieter nicht unterstützt. die **IRowsetScroll** -Schnittstelle, die Eigenschaft wird festgelegt, um **AdPosUnknown**. Siehe die Dokumentation für Ihren Anbieter, um zu bestimmen, ob es unterstützt **IRowsetScroll**.  
  
 Verwenden der **AbsolutePosition** -Eigenschaft zum Verschieben auf einen Datensatz basierend auf der Ordnungsposition in der **Recordset** -Objekt, oder um die Ordinalposition des aktuellen Datensatzes zu bestimmen. Der Anbieter muss die entsprechende Funktionalität für diese Eigenschaft zur Verfügung stehen unterstützen.  
  
 Wie die [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) Eigenschaft **AbsolutePosition** ist 1-basiert und entspricht 1, wenn der aktuelle Datensatz den ersten Datensatz in ist die **Recordset**. Sie erhalten die Gesamtzahl der Datensätze in der **Recordset** -Objekt aus der [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) Eigenschaft.  
  
 Beim Festlegen der **AbsolutePosition** -Eigenschaft, auch wenn es zu einem Datensatz im aktuellen Cache ist ADO lädt den Cache mit einer neuen Gruppe von Datensätzen, die mit dem angegebenen Datensatz ab. Die [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) Eigenschaft bestimmt die Größe dieser Gruppe.  
  
> [!NOTE]
>  Verwenden Sie nicht die **AbsolutePosition** -Eigenschaft, wie ein Ersatzzeichen Datensatznummer. Die Position eines bestimmten Datensatzes geändert wird, wenn Sie einen vorherigen Datensatz zu löschen. Es gibt auch keine Zusicherung, dass ein bestimmter Datensatz die gleiche hat **AbsolutePosition** Wenn die **Recordset** Objekts erneut abgefragt oder geöffnet wird. Lesezeichen werden weiterhin die empfohlene Methode beibehalten und an einer bestimmten Position zurückgegeben werden und sind die einzige Möglichkeit der Positionierung für alle Arten von **Recordset** Objekte.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [AbsolutePosition und CursorLocation – Beispiel (VB)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vb.md)   
 [AbsolutePosition und CursorLocation – Beispiel (VC++)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vc.md)   
 [AbsolutePage-Eigenschaft (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [RecordCount-Eigenschaft (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
