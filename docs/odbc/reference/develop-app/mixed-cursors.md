---
title: Gemischte Cursor | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mixed cursors [ODBC]
- cursors [ODBC], dynamic
- keyset-driven cursors [ODBC]
- dynamic cursors [ODBC]
- cursors [ODBC], key-set driven
- cursors [ODBC], mixed
ms.assetid: 9beb2db9-0b6d-491d-9529-d64e64e59014
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a91dacf8ea9c0ed0db2c3b64634ddd53b854a534
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307435"
---
# <a name="mixed-cursors"></a>Gemischte Cursor

Ein gemischter Cursor ist eine Kombination aus einem Keyset-gesteuerten Cursor und einem dynamischen Cursor. Es wird verwendet, wenn das Resultset zu groß ist, um Schlüssel für das gesamte Resultset vernünftig zu speichern. Gemischte Cursor werden implementiert, indem ein Keyset erstellt wird, das kleiner als das gesamte Resultset, aber größer als das Rowset ist.  
  
 Solange die Anwendung innerhalb des Keysets scrollt, ist das Verhalten keyset-gesteuert. Wenn die Anwendung außerhalb des Keysets scrollt, ist das Verhalten dynamisch: Der Cursor ruft die angeforderten Zeilen ab und erstellt ein neues Keyset. Nachdem das neue Keyset erstellt wurde, wird das Verhalten innerhalb dieses Keysets auf Keyset-gesteuert zurückgesetzt.  
  
 Angenommen, ein Resultset hat 1.000 Zeilen und verwendet einen gemischten Cursor mit einer Keysetgröße von 100 und einer Rowsetgröße von 10. Wenn das erste Rowset abgerufen wird, erstellt der Cursor ein Keyset, das aus den Schlüsseln für die ersten 100 Zeilen besteht. Anschließend werden die ersten 10 Zeilen wie gewünscht zurückgegeben.  
  
 Angenommen, eine andere Anwendung löscht die Zeilen 11 und 101. Wenn der Cursor versucht, Zeile 11 abzurufen, tritt eine Lücke auf, da er einen Schlüssel für diese Zeile hat, aber keine Zeile vorhanden ist. Dies ist keyset-gesteuertes Verhalten. Wenn der Cursor versucht, Zeile 101 abzurufen, erkennt der Cursor nicht, dass die Zeile fehlt, da sie keinen Schlüssel für die Zeile hat. Stattdessen ruft es die zuvor zeile 102 ab. Dies ist ein dynamisches Cursorverhalten.  
  
 Ein gemischter Cursor entspricht einem Keyset-gesteuerten Cursor, wenn die Keysetgröße der Größe des Resultsets entspricht. Ein gemischter Cursor entspricht einem dynamischen Cursor, wenn die Keysetgröße gleich 1 ist.
