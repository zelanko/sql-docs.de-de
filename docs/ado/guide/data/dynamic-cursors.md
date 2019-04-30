---
title: Dynamische Cursor | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f0d7a19476a00fb88e0b2195c761993f91b7a5d4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161782"
---
# <a name="dynamic-cursors"></a>Dynamische Cursor
Dynamische Cursor erkennen alle Änderungen, die auf die Zeilen im Resultset, unabhängig davon, ob die Änderungen aus, in den Cursor oder von anderen Benutzern außerhalb des Cursors auftreten. Alle INSERT-, Update- und Delete-Anweisungen, die von allen Benutzern werden über den Cursor sichtbar. Der dynamische-Cursor kann Änderungen, die Zeilen, die Reihenfolge und die Werte im Resultset nach dem Öffnen des Cursors erkennen. Updates, die außerhalb des Cursors sind nicht sichtbar, bis sie ein Commit ausgeführt werden (es sei denn, die die Transaktionsisolationsstufe des Cursors "Commit" auf festgelegt ist).  
  
 Nehmen wir beispielsweise an ein dynamischer Cursor ruft zwei Zeilen und einer anderen Anwendung, und klicken Sie dann eine der Zeilen aktualisiert und löscht die andere. Wenn der dynamische Cursor diese Zeilen dann abruft, findet er die gelöschte Zeile nicht, die neuen Werte der aktualisierten Zeile werden jedoch angezeigt.  
  
 Der dynamische Cursor ist eine gute Wahl, wenn Ihre Anwendung alle gleichzeitige Updates, die von anderen Benutzern vorgenommene erkannt werden muss. Verwenden Sie die **AdOpenDynamic CursorTypeEnum** , um anzugeben, dass Sie einen dynamischen Cursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorwärtscursor](../../../ado/guide/data/forward-only-cursors.md)   
 [Statische Cursor](../../../ado/guide/data/static-cursors.md)   
 [KEYSET-Cursor](../../../ado/guide/data/keyset-cursors.md)
