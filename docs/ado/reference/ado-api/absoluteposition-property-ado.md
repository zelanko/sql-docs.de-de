---
description: AbsolutePosition-Eigenschaft (ADO)
title: AbsolutePosition-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 0ecb3290d73032568af7e0a92baf0c9d1b2628f4
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977158"
---
# <a name="absoluteposition-property-ado"></a>AbsolutePosition-Eigenschaft (ADO)
Gibt die Ordnungsposition des aktuellen Datensatzes eines [Recordset](./recordset-object-ado.md) -Objekts an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Für 32-Bit-Code legt einen **Long** -Wert von 1 bis zur Anzahl der Datensätze im **Recordset** -Objekt ([RecordCount](./recordcount-property-ado.md)) fest oder gibt einen der [positionenum](./positionenum.md) -Werte zurück.  
  
 Verwenden Sie für 64-Bit-Code einen Datentyp, der für die Speicherung eines 64-Bit-Werts bereitstellt. Beispielsweise können Sie einen langen oder einen anderen Wert verwenden, der 64-Bit-Länge ist, z. b. dbordindin. Verwenden Sie keine **positionenum** -Werte, da Sie auf eine 32-Bit-Länge beschränkt sind.  
  
## <a name="remarks"></a>Bemerkungen  
 Um die **AbsolutePosition** -Eigenschaft festzulegen, erfordert ADO, dass der OLE DB-Anbieter, den Sie verwenden, die [IRowsetLocate: IRowset](/previous-versions/windows/desktop/ms721190(v=vs.85)) -Schnittstelle implementiert.  
  
 Durch den Zugriff auf die **AbsolutePosition** -Eigenschaft eines **Recordsets** , das entweder mit einem Vorwärts Cursor oder einem dynamischen Cursor geöffnet wurde, wird der Fehler **adErrFeatureNotAvailable**ausgelöst. Bei anderen Cursor Typen wird die korrekte Position zurückgegeben, solange der OLE DB Anbieter die **IRowsetScroll: IRowsetLocate** -Schnittstelle unterstützt. Wenn der Anbieter die **IRowsetScroll** -Schnittstelle nicht unterstützt, wird die-Eigenschaft auf **adPosUnknown**festgelegt. In der Dokumentation für Ihren Anbieter können Sie feststellen, ob **IRowsetScroll**unterstützt wird.  
  
 Verwenden Sie die **AbsolutePosition** -Eigenschaft, um zu einem Datensatz zu wechseln, der auf seiner Ordinalposition im **Recordset** -Objekt basiert, oder um die Ordinalposition des aktuellen Datensatzes zu bestimmen. Der Anbieter muss die entsprechende Funktionalität unterstützen, damit diese Eigenschaft verfügbar ist.  
  
 Wie die [AbsolutePage](./absolutepage-property-ado.md) -Eigenschaft ist **AbsolutePosition** 1-basiert und entspricht 1, wenn der aktuelle Datensatz der erste Datensatz im **Recordset**ist. Sie können die Gesamtzahl der Datensätze im **Recordset** -Objekt aus der [RecordCount](./recordcount-property-ado.md) -Eigenschaft abrufen.  
  
 Wenn Sie die **AbsolutePosition** -Eigenschaft festlegen, auch wenn Sie sich in einem Datensatz im aktuellen Cache befindet, lädt ADO den Cache mit einer neuen Gruppe von Datensätzen neu, beginnend mit dem von Ihnen angegebenen Datensatz. Die [CacheSize](./cachesize-property-ado.md) -Eigenschaft bestimmt die Größe dieser Gruppe.  
  
> [!NOTE]
>  Sie sollten die **AbsolutePosition** -Eigenschaft nicht als Ersatz Zeichendaten Satz Nummer verwenden. Die Position eines angegebenen Datensatzes ändert sich, wenn Sie einen vorangehenden Datensatz löschen. Außerdem ist nicht sichergestellt, dass ein bestimmter Datensatz dieselbe **AbsolutePosition** hat, wenn das **Recordset** -Objekt angefordert oder erneut geöffnet wird. Lesezeichen sind immer noch die empfohlene Methode zum beibehalten und zurückkehren zu einer gegebenen Position und sind die einzige Möglichkeit der Positionierung für alle Typen von **recordsetobjekten** .  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für AbsolutePosition und Cursor Location-Eigenschaften (VB)](./absoluteposition-and-cursorlocation-properties-example-vb.md)   
 [Eigenschaften von "AbsolutePosition" und "Cursor Location" (VC + +)](./absoluteposition-and-cursorlocation-properties-example-vc.md)   
 [AbsolutePage-Eigenschaft (ADO)](./absolutepage-property-ado.md)   
 [RecordCount-Eigenschaft (ADO)](./recordcount-property-ado.md)