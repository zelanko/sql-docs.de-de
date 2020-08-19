---
description: AbsolutePosition-Eigenschaft (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e406012b917dd6e1694f5914088bac09201ff99e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451752"
---
# <a name="absoluteposition-property-ado"></a>AbsolutePosition-Eigenschaft (ADO)
Gibt die Ordnungsposition des aktuellen Datensatzes eines [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Für 32-Bit-Code legt einen **Long** -Wert von 1 bis zur Anzahl der Datensätze im **Recordset** -Objekt ([RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)) fest oder gibt einen der [positionenum](../../../ado/reference/ado-api/positionenum.md) -Werte zurück.  
  
 Verwenden Sie für 64-Bit-Code einen Datentyp, der für die Speicherung eines 64-Bit-Werts bereitstellt. Beispielsweise können Sie einen langen oder einen anderen Wert verwenden, der 64-Bit-Länge ist, z. b. dbordindin. Verwenden Sie keine **positionenum** -Werte, da Sie auf eine 32-Bit-Länge beschränkt sind.  
  
## <a name="remarks"></a>Bemerkungen  
 Um die **AbsolutePosition** -Eigenschaft festzulegen, erfordert ADO, dass der OLE DB-Anbieter, den Sie verwenden, die [IRowsetLocate: IRowset](https://msdn.microsoft.com/library/windows/desktop/ms721190.aspx) -Schnittstelle implementiert.  
  
 Durch den Zugriff auf die **AbsolutePosition** -Eigenschaft eines **Recordsets** , das entweder mit einem Vorwärts Cursor oder einem dynamischen Cursor geöffnet wurde, wird der Fehler **adErrFeatureNotAvailable**ausgelöst. Bei anderen Cursor Typen wird die korrekte Position zurückgegeben, solange der OLE DB Anbieter die **IRowsetScroll: IRowsetLocate** -Schnittstelle unterstützt. Wenn der Anbieter die **IRowsetScroll** -Schnittstelle nicht unterstützt, wird die-Eigenschaft auf **adPosUnknown**festgelegt. In der Dokumentation für Ihren Anbieter können Sie feststellen, ob **IRowsetScroll**unterstützt wird.  
  
 Verwenden Sie die **AbsolutePosition** -Eigenschaft, um zu einem Datensatz zu wechseln, der auf seiner Ordinalposition im **Recordset** -Objekt basiert, oder um die Ordinalposition des aktuellen Datensatzes zu bestimmen. Der Anbieter muss die entsprechende Funktionalität unterstützen, damit diese Eigenschaft verfügbar ist.  
  
 Wie die [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) -Eigenschaft ist **AbsolutePosition** 1-basiert und entspricht 1, wenn der aktuelle Datensatz der erste Datensatz im **Recordset**ist. Sie können die Gesamtzahl der Datensätze im **Recordset** -Objekt aus der [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) -Eigenschaft abrufen.  
  
 Wenn Sie die **AbsolutePosition** -Eigenschaft festlegen, auch wenn Sie sich in einem Datensatz im aktuellen Cache befindet, lädt ADO den Cache mit einer neuen Gruppe von Datensätzen neu, beginnend mit dem von Ihnen angegebenen Datensatz. Die [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) -Eigenschaft bestimmt die Größe dieser Gruppe.  
  
> [!NOTE]
>  Sie sollten die **AbsolutePosition** -Eigenschaft nicht als Ersatz Zeichendaten Satz Nummer verwenden. Die Position eines angegebenen Datensatzes ändert sich, wenn Sie einen vorangehenden Datensatz löschen. Außerdem ist nicht sichergestellt, dass ein bestimmter Datensatz dieselbe **AbsolutePosition** hat, wenn das **Recordset** -Objekt angefordert oder erneut geöffnet wird. Lesezeichen sind immer noch die empfohlene Methode zum beibehalten und zurückkehren zu einer gegebenen Position und sind die einzige Möglichkeit der Positionierung für alle Typen von **recordsetobjekten** .  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für AbsolutePosition und Cursor Location-Eigenschaften (VB)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vb.md)   
 [Eigenschaften von "AbsolutePosition" und "Cursor Location" (VC + +)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vc.md)   
 [AbsolutePage-Eigenschaft (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [RecordCount-Eigenschaft (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
