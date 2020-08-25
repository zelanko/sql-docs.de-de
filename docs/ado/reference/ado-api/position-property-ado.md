---
description: Position-Eigenschaft (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: be31e95a3929243602baaa10c5a36a9348f812b8
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773179"
---
# <a name="position-property-ado"></a>Position-Eigenschaft (ADO)
Gibt die aktuelle Position innerhalb eines [Streamobjekts](./stream-object-ado.md) an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der den Offset der aktuellen Position vom Anfang des Streams in Byte Anzahl angibt, oder gibt ihn zurück. Der Standardwert ist 0 (null), der das erste Byte im Stream darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die aktuelle Position kann an einen Punkt nach dem Ende des Streams verschoben werden. Wenn Sie die aktuelle Position über das Ende des Streams hinaus angeben, wird die [Größe](./size-property-ado-stream.md) des Daten **Strom** Objekts entsprechend angehoben. Alle neuen bytes, die auf diese Weise hinzugefügt werden, sind NULL.  
  
> [!NOTE]
>  **Position** misst immer bytes. Multiplizieren Sie für Textstreams, die Multibytezeichen-Zeichensätze verwenden, die Position nach der Zeichengröße, um die Zeichen Nummer zu ermitteln. Beispielsweise befindet sich das erste Zeichen für einen 2-Byte-Zeichensatz an Position 0, das zweite Zeichen an Position 2, das dritte Zeichen an Position 4 usw.  
  
> [!NOTE]
>  Negative Werte können nicht verwendet werden, um die aktuelle Position in einem **Stream**zu ändern. Nur positive Zahlen können für die **Position**verwendet werden.  
  
> [!NOTE]
>  Bei schreibgeschützten **Streamobjekten** gibt ADO keinen Fehler zurück, wenn die **Position** auf einen Wert festgelegt ist, der größer als die **Größe** des **Streams**ist. Dadurch wird die Größe des **Streams**nicht geändert, oder die Daten **Strom** Inhalte können auf irgendeine Weise geändert werden. Dies sollte jedoch vermieden werden, da dies zu einem bedeutungslosen **Positions**Wert führt.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Charset-Eigenschaft (ADO)](./charset-property-ado.md)