---
title: Gemischte Cursor | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97da67bca185cd86de944e8bccc86d2b4c149b0d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086374"
---
# <a name="mixed-cursors"></a>Gemischte Cursor

Ein gemischter Cursor ist eine Kombination aus einem keysetgesteuerten Cursor und einem dynamischen Cursor. Sie wird verwendet, wenn das Resultset zu groß ist, um Schlüssel für das gesamte Resultset zu speichern. Gemischte Cursor werden implementiert, indem ein Keyset erstellt wird, das kleiner als das gesamte Resultset, aber größer als das Rowset ist.  
  
 Solange die Anwendung innerhalb des Keysets einen Bildlauf durchführt, ist das Verhalten keysetgesteuert. Wenn die Anwendung einen Bildlauf außerhalb des Keysets durchführt, ist das Verhalten dynamisch: der Cursor Ruft die angeforderten Zeilen ab und erstellt ein neues Keyset. Nachdem das neue Keyset erstellt wurde, wird das Verhalten auf keysetgesteuert innerhalb dieses Keysets zurückgesetzt.  
  
 Nehmen wir beispielsweise an, ein Resultset enthält 1.000 Zeilen und verwendet einen gemischten Cursor mit einer Keysetgröße von 100 und einer Rowsetgröße von 10. Wenn das erste Rowset abgerufen wird, erstellt der Cursor ein Keyset, das aus den Schlüsseln für die ersten 100 Zeilen besteht. Anschließend werden die ersten 10 Zeilen zurückgegeben, wie angefordert.  
  
 Angenommen, eine andere Anwendung löscht die Zeilen 11 und 101. Wenn der Cursor versucht, Zeile 11 abzurufen, wird eine Lücke angezeigt, da Sie über einen Schlüssel für diese Zeile verfügt, aber keine Zeile vorhanden ist. Dies ist ein keysetgesteuerte Verhalten. Wenn der Cursor versucht, Zeile 101 abzurufen, erkennt der Cursor nicht, dass die Zeile fehlt, weil er keinen Schlüssel für die Zeile hat. Stattdessen wird die Zeile abgerufen, die zuvor Zeile 102 war. Dies ist das dynamische Cursor Verhalten.  
  
 Ein gemischter Cursor entspricht einem keysetgesteuerten Cursor, wenn die Keysetgröße gleich der Größe des Resultsets ist. Ein gemischter Cursor entspricht einem dynamischen Cursor, wenn die Keysetgröße gleich 1 ist.
