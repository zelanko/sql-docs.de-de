---
title: Einrichten des Cursors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 805d8076c853513d86f9a3a92d9342d1224226c9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299800"
---
# <a name="setting-up-the-cursor"></a>Einrichten des Cursors
Die Anwendung kann den Cursortyp vor dem Ausführen einer Anweisung angeben, die ein Resultset erstellt. Dies erfolgt mit dem SQL_ATTR_CURSOR_TYPE-Anweisungs Attribut. Wenn die Anwendung nicht explizit einen Typ angibt, wird ein Vorwärts Cursor verwendet. Zum erhalten eines gemischten Cursors gibt eine Anwendung einen keysetgesteuerten Cursor an, deklariert jedoch eine Keysetgröße, die kleiner als die resultsetgröße ist.  
  
 Für keysetgesteuerte und gemischte Cursor kann die Anwendung auch die Keysetgröße angeben. Dies erfolgt mit dem SQL_ATTR_KEYSET_SIZE-Anweisungs Attribut. Wenn die Keysetgröße auf 0 (Standardwert) festgelegt ist, wird die Größe des Keysets auf die resultsetgröße festgelegt, und ein keysetgesteuerte Cursor wird verwendet. Die Keysetgröße kann geändert werden, nachdem der Cursor geöffnet wurde.  
  
 Die Anwendung kann auch die Rowsetgröße festlegen. Weitere Informationen finden Sie weiter oben in diesem Abschnitt unter [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md).
