---
title: Bildlauffähige Cursor | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70d02b933104a3106d95f6760cbdcf0abb347716
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47791553"
---
# <a name="scrollable-cursors"></a>Scrollbare Cursor
In modernen bildschirmbasierte Anwendungen verschiebt der Benutzer rückwärts und Vorwärts durch die Daten an. Für solche Anwendungen ist die Rückgabe an einer zuvor abgerufenen Zeile ein Problem. Eine Möglichkeit ist, zu schließen und öffnen den Cursor und rufen Sie Zeilen an, bis der Cursor über die erforderliche Zeile erreicht. Eine andere Möglichkeit ist das Resultset zu lesen, lokal zwischengespeichert und Durchführen eines Bildlaufs in der Anwendung zu implementieren. Beide Möglichkeiten funktionieren, auch nur mit kleinen Resultsets ein, und die zweite Möglichkeit ist schwierig zu implementieren. Eine bessere Lösung ist die Verwendung einer *bildlauffähigen Cursor* die rückwärts und im Resultset weiterleiten können.  
  
 Ein *bildlauffähigen Cursor* wird häufig in modernen bildschirmbasierte Anwendungen, in dem der Benutzer hin-und durch die Daten scrollt, verwendet. Allerdings sollten Anwendungen scrollfähige Cursor verwenden, wenn Vorwärtscursor nicht den Auftrag werden als scrollbare Cursor im Allgemeinen teurer als Vorwärtscursor werden.  
  
 Die Möglichkeit, rückwärts zu bewegen, löst eine gilt nicht für Vorwärtscursor Frage: sollte ein bildlauffähiger Cursor erkennen Änderungen an zuvor abgerufenen Zeilen? Erkennen es sollte, also aktualisierte, gelöschte und neu eingefügte Zeilen?  
  
 Diese Frage tritt auf, da die Definition eines Ergebnisses festgelegt – die Menge der Zeilen, die bestimmten Kriterien entsprechen, nicht vorschreiben, wenn Zeilen überprüft werden, um festzustellen, ob sie die diesem Kriterium entsprechen, noch wird mit dem Status Gibt an, ob Zeilen enthalten die gleichen Daten jedes Mal müssen sie abgerufen werden. Die erste Auslassung ermöglicht es scrollfähige Cursor erkennen, ob Zeilen eingefügt oder werden, gelöscht während Letzteres möglich, dass sie das Erkennen von aktualisierten Daten vereinfacht wurden.  
  
 Die Fähigkeit zum Erkennen von Änderungen ist manchmal hilfreich, manchmal nicht. Eine buchhaltungsanwendung benötigt beispielsweise einen Cursor, der alle Änderungen werden ignoriert; Bücher Lastenausgleich ist nicht möglich, wenn der Cursor die neuesten Änderungen angezeigt werden. Andererseits, benötigt ein Fluglinien-Reservierungssystem, einen Cursor, der zeigt, die neuesten Änderungen an den Daten; ohne einen Cursor müssen sie die Datenbank, um die aktuellste Verfügbarkeit der Flug anzeigen kontinuierlich erneut abfragen.  
  
 Um die Anforderungen unterschiedlicher Anwendungen abzudecken, definiert ODBC vier verschiedene Typen von scrollfähige Cursor. Diese Cursor sowohl auf Kosten variieren, und auf ihre Fähigkeit zum Erkennen von Änderungen auf das Ergebnis festgelegt. Beachten Sie, dass wenn Sie ein bildlauffähiger Cursor über Änderungen an Zeilen erkennen kann, nur diese erkannt werden können, wenn er versucht, diese Zeilen erneut abzurufen. Es gibt keine Möglichkeit für die Datenquelle den Cursor über Änderungen an den derzeit abgerufenen Zeilen informieren. Beachten Sie auch, dass die Sichtbarkeit der Änderungen auch von der Transaktionsisolationsstufe gesteuert wird. Weitere Informationen finden Sie unter [Transaktionsisolation](../../../odbc/reference/develop-app/transaction-isolation.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Scrollbare Cursortypen](../../../odbc/reference/develop-app/scrollable-cursor-types.md)  
  
-   [Verwenden von scrollbaren Cursorn](../../../odbc/reference/develop-app/using-scrollable-cursors.md)  
  
-   [Relatives und absolutes Scrollen](../../../odbc/reference/develop-app/relative-and-absolute-scrolling.md)  
  
-   [Lesezeichen](../../../odbc/reference/develop-app/bookmarks-odbc.md)
