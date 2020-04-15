---
title: Scrollbare Cursor | Microsoft Docs
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
ms.assetid: 2c8a5f50-9b37-452f-8160-05f42bc4d97e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2762ffc7fa179fc6a68f92c23f92ca12803f5ab7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304211"
---
# <a name="scrollable-cursors"></a>Scrollbare Cursor
In modernen bildschirmbasierten Anwendungen scrollt der Benutzer durch die Daten hin und her. Für solche Anwendungen ist die Rückkehr zu einer zuvor abgerufenen Zeile ein Problem. Eine Möglichkeit besteht darin, den Cursor zu schließen und erneut zu öffnen und dann Zeilen abzurufen, bis der Cursor die gewünschte Zeile erreicht. Eine weitere Möglichkeit besteht darin, das Resultset zu lesen, lokal zwischenzuspeichern und Scrollen in der Anwendung zu implementieren. Beide Möglichkeiten funktionieren nur bei kleinen Ergebnissätzen gut, und letztere Möglichkeit ist schwer umzusetzen. Eine bessere Lösung besteht darin, einen *scrollbaren Cursor* zu verwenden, der sich im Resultset vorwärts und rückwärts bewegen kann.  
  
 Ein *scrollbarer Cursor* wird häufig in modernen bildschirmbasierten Anwendungen verwendet, in denen der Benutzer durch die Daten hin und her scrollt. Anwendungen sollten jedoch nur dann scrollbare Cursor verwenden, wenn vorwärtsgerichtete Cursor die Aufgabe nicht ausführen, da scrollbare Cursor im Allgemeinen teurer sind als nur Vorwärtscursor.  
  
 Die Möglichkeit, rückwärts zu wechseln, wirft eine Frage auf, die nicht für Vorwärtscursor gilt: Sollte ein scrollbarer Cursor Änderungen erkennen, die an zuvor abgerufenen Zeilen vorgenommen wurden? Das heißt, sollte aktualisierte, gelöschte und neu eingefügte Zeilen erkannt werden?  
  
 Diese Frage stellt sich, weil die Definition eines Resultsets - der Satz von Zeilen, der bestimmten Kriterien entspricht - nicht angibt, wann Zeilen überprüft werden, um festzustellen, ob sie diesen Kriterien entsprechen, und auch nicht, ob Zeilen bei jedem Abruf dieselben Daten enthalten müssen. Die frühere Auslassung ermöglicht es scrollbaren Cursorn, festzustellen, ob Zeilen eingefügt oder gelöscht wurden, während letztere es ihnen ermöglicht, aktualisierte Daten zu erkennen.  
  
 Die Fähigkeit, Änderungen zu erkennen, ist manchmal nützlich, manchmal nicht. Beispielsweise benötigt eine Buchhaltungsanwendung einen Cursor, der alle Änderungen ignoriert. Das Ausgleichen von Büchern ist nicht möglich, wenn der Cursor die neuesten Änderungen anzeigt. Auf der anderen Seite benötigt ein Reservierungssystem für Fluggesellschaften einen Cursor, der die neuesten Änderungen an den Daten anzeigt; ohne einen solchen Cursor muss die Datenbank ständig neu abgefragt werden, um die aktuellste Flugverfügbarkeit anzuzeigen.  
  
 Um die Anforderungen verschiedener Anwendungen zu decken, definiert ODBC vier verschiedene Arten von scrollbaren Cursorn. Diese Cursor variieren sowohl in der Ausgabe als auch in ihrer Fähigkeit, Änderungen am Resultset zu erkennen. Beachten Sie, dass ein bildlauffähiger Cursor Änderungen an Zeilen erkennen kann, wenn er versucht, diese Zeilen erneut abzurufen. Es gibt keine Möglichkeit für die Datenquelle, den Cursor über Änderungen an den aktuell abgerufenen Zeilen zu benachrichtigen. Beachten Sie auch, dass die Sichtbarkeit von Änderungen auch durch die Transaktionsisolationsstufe gesteuert wird. Weitere Informationen finden Sie unter [Transaktionsisolation](../../../odbc/reference/develop-app/transaction-isolation.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Scrollbare Cursortypen](../../../odbc/reference/develop-app/scrollable-cursor-types.md)  
  
-   [Verwenden von scrollbaren Cursor](../../../odbc/reference/develop-app/using-scrollable-cursors.md)  
  
-   [Relatives und absolutes Scrollen](../../../odbc/reference/develop-app/relative-and-absolute-scrolling.md)  
  
-   [Lesezeichen](../../../odbc/reference/develop-app/bookmarks-odbc.md)
