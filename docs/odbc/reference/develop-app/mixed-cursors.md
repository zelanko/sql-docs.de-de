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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086374"
---
# <a name="mixed-cursors"></a>Gemischte Cursor

Ein gemischte Cursor ist eine Kombination eines keysetgesteuerten Cursors und einen dynamischen Cursor. Es wird verwendet, wenn das Resultset zu groß, um den Schlüssel für das gesamte Resultset angemessen zu speichern ist. Gemischte Cursor werden implementiert, erstellen Sie eine Keyset, die kleiner als das gesamte Resultset jedoch größer als das Rowset ist.  
  
 Solange die Anwendung innerhalb des Keysets einen Bildlauf durchführt, ist das Verhalten keysetgesteuerte. Wenn die Anwendung außerhalb der Keyset einen Bildlauf durchführt, ist das Verhalten dynamischer: Der Cursor die angeforderten Zeilen und erstellt eine neue Keyset. Nachdem das neue Keyset erstellt wurde, wird das Verhalten innerhalb der, dass sich keysetgesteuerte keysetgesteuerte wiederhergestellt.  
  
 Nehmen wir beispielsweise an einem Resultset verfügt über 1.000 Zeilen umfassen und verwendet einen gemischte Cursor ein Keysetgröße von 100 mit einer Rowsetgröße von 10. Wenn das erste Rowset abgerufen wird, erstellt den Cursor eine Keyset, die die Schlüssel für die ersten 100 Zeilen bestehen. Anschließend wird die ersten 10 Zeilen als angefordert zurückgegeben.  
  
 Nehmen wir nun an eine andere Anwendung löscht Zeilen 11 und 101. Wenn der Cursor versucht, die die Zeile 11 abgerufen werden, treten sie eine Lücke, da er verfügt über einen Schlüssel für diese Zeile aber keine Zeile vorhanden ist; Dieses ist Verhalten keysetgesteuerte. Wenn der Cursor, Zeile 101 abzurufen versucht, erkennt der Cursor nicht, dass die Zeile nicht vorhanden ist, da sie nicht über einen Schlüssel für die Zeile verfügt. Stattdessen werden sie abgerufen, was zuvor Zeile 102 war. Dies trifft dynamic-Cursor.  
  
 Ein gemischte Cursor entspricht ein keysetgesteuerter Cursor, wenn die Keysetgröße gleich der Größe des Resultsets ist. Ein gemischte Cursor entspricht ein dynamic-Cursor, wenn die Keysetgröße gleich 1 ist.
