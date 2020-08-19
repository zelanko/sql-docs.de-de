---
description: Dynamische Cursor
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6904bc0b3459f25af955d804ed4764ae57238b90
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453472"
---
# <a name="dynamic-cursors"></a>Dynamische Cursor
Dynamische Cursor erkennen alle Änderungen, die an den Zeilen im Resultset vorgenommen werden, unabhängig davon, ob die Änderungen innerhalb des Cursors oder von anderen Benutzern außerhalb des Cursors auftreten. Alle INSERT-, Update-und DELETE-Anweisungen, die von allen Benutzern durchgeführt werden, sind über den Cursor sichtbar. Der dynamische Cursor kann alle Änderungen erkennen, die an den Zeilen, der Reihenfolge und den Werten im Resultset vorgenommen werden, nachdem der Cursor geöffnet wurde. Updates, die außerhalb des Cursors vorgenommen werden, werden erst angezeigt, wenn ein Commit ausgeführt wird (es sei denn, die Isolationsstufe der Cursor Transaktion ist auf "nicht ausgeführt" festgelegt  
  
 Nehmen wir beispielsweise an, ein dynamischer Cursor ruft zwei Zeilen und eine andere Anwendung ab und aktualisiert dann eine dieser Zeilen und löscht die andere. Wenn der dynamische Cursor diese Zeilen dann abruft, findet er die gelöschte Zeile nicht, die neuen Werte der aktualisierten Zeile werden jedoch angezeigt.  
  
 Der dynamische Cursor ist eine gute Wahl, wenn Ihre Anwendung alle gleichzeitigen Updates erkennen muss, die von anderen Benutzern vorgenommen wurden. Verwenden Sie die " **adOpenDynamic CursorTypeEnum** ", um anzugeben, dass Sie einen dynamischen Cursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorwärts Cursor](../../../ado/guide/data/forward-only-cursors.md)   
 [Statische Cursor](../../../ado/guide/data/static-cursors.md)   
 [KEYSET-Cursor](../../../ado/guide/data/keyset-cursors.md)
