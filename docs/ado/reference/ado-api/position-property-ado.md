---
title: Position-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Position
helpviewer_keywords:
- Position property [ADO]
ms.assetid: daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 333b06ef76ae6407ca8a5605f1917dc0bb609aca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47615888"
---
# <a name="position-property-ado"></a>Position-Eigenschaft (ADO)
Gibt die aktuelle Position innerhalb einer [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** Wert, der den Offset in Anzahl von Bytes, die von der aktuellen Position vom Anfang des Streams angibt. Der Standardwert ist 0, was das erste Byte im Stream darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Die aktuelle Position kann bis zu einem Zeitpunkt nach dem Ende des Streams verschoben werden. Wenn Sie angeben, dass die aktuelle Position hinter dem Ende des Datenstroms, der die [Größe](../../../ado/reference/ado-api/size-property-ado-stream.md) von der **Stream** Objekt entsprechend erhöht. Auf diese Weise hinzugefügten neue Bytes werden als null sein.  
  
> [!NOTE]
>  **Position** immer misst Bytes. Multiplizieren Sie für Textstreams Mehrbyte-Zeichensätze verwenden die Position von der Zeichengröße, um die Nummer des Zeichens zu bestimmen. Beispielsweise ist das erste Zeichen für einen 2-Byte-Zeichensatz an Position 0 (null) das zweite Zeichen an Position 2, das dritte Zeichen an Position 4 und So weiter.  
  
> [!NOTE]
>  Negative Werte können nicht verwendet werden, so ändern Sie die aktuelle Position in einem **Stream**. Nur positive Zahlen können verwendet werden, für die **Position**.  
  
> [!NOTE]
>  Für schreibgeschützte **Stream** Objekten, die ADO wird kein Fehler zurückgegeben, wenn **Position** wird festgelegt auf einen Wert größer als die **Größe** von der **Stream**. Dies ändert sich die Größe des nicht die **Stream**, oder Ändern der **Stream** Inhalt in keiner Weise. Allerdings auf diese Weise sollte vermieden werden, da dies zu einem bedeutungslos führt **Position**Wert.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Charset-Eigenschaft (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)
