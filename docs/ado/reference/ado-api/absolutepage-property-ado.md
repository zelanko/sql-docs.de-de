---
description: AbsolutePage-Eigenschaft (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c5c9d802dd6ba373b7bf92f063125f0b656eab8
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759990"
---
# <a name="absolutepage-property-ado"></a>AbsolutePage-Eigenschaft (ADO)
Gibt an, auf welcher Seite sich der aktuelle Datensatz befindet.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Für 32-Bit-Code legt einen **Long** -Wert zwischen 1 und der Anzahl der Seiten im [Recordset](./recordset-object-ado.md) -Objekt ([PageCount](./pagecount-property-ado.md)) fest oder gibt einen der [positionenum](./positionenum.md) -Werte zurück.  
  
 Verwenden Sie für 64-Bit-Code einen Datentyp, der für die Speicherung eines 64-Bit-Werts bereitstellt. Beispielsweise können Sie einen **langen** oder einen anderen Wert verwenden, der 64-Bit-Länge sein kann, z. b. dbordindin. Verwenden Sie keine **positionenum** -Werte, da Sie auf eine 32-Bit-Länge beschränkt sind.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft kann verwendet werden, um die Seitenzahl zu identifizieren, auf der sich der aktuelle Datensatz befindet. Er verwendet die [PageSize](./pagesize-property-ado.md) -Eigenschaft, um die Gesamtanzahl der Rowsets des **Recordset** -Objekts logisch in eine Reihe von Seiten aufzuteilen, von denen jede die Anzahl der Datensätze gleich " **PageSize** " aufweist (außer der letzten Seite, die möglicherweise weniger Datensätze aufweist). Der Anbieter muss die entsprechende Funktionalität unterstützen, damit diese Eigenschaft verfügbar ist.  
  
-   Beim Aktivieren oder Festlegen der **AbsolutePage** -Eigenschaft verwendet ADO die [AbsolutePosition](./absoluteposition-property-ado.md) -Eigenschaft und die [PageSize](./pagesize-property-ado.md) -Eigenschaft wie folgt:  
  
-   Um das **AbsolutePage**-Element abzurufen, ruft ADO zuerst die **AbsolutePosition**ab und dividiert Sie durch die **PageSize**.  
  
-   Um das **AbsolutePage**-Element festzulegen, verschiebt ADO die **AbsolutePosition** wie folgt: es multipliziert die **PageSize** mit dem neuen Wert von **AbsolutePage** und fügt dann dem Wert 1 hinzu. Folglich ist die aktuelle Position im **Recordset** nach erfolgreicher Festlegung von **AbsolutePage** der erste Datensatz auf dieser Seite.  
  
 Wie die **AbsolutePosition** -Eigenschaft ist **AbsolutePage** 1-basiert und entspricht 1, wenn der aktuelle Datensatz der erste Datensatz im **Recordset**ist. Legen Sie diese Eigenschaft fest, um zum ersten Datensatz einer bestimmten Seite zu wechseln. Abrufen der Gesamtzahl der Seiten aus der **PageCount** -Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für AbsolutePage, PageCount und pageSize-Eigenschaften (VB)](./absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [Beispiel für AbsolutePage, PageCount und pageSize-Eigenschaften (VC + +)](./absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePosition-Eigenschaft (ADO)](./absoluteposition-property-ado.md)   
 [PageCount-Eigenschaft (ADO)](./pagecount-property-ado.md)   
 [PageSize-Eigenschaft (ADO)](./pagesize-property-ado.md)