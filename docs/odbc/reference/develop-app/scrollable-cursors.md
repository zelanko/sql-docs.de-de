---
description: Scrollbare Cursor
title: Scrollbare Cursor | Microsoft-Dokumentation
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
ms.openlocfilehash: 9c347dcb130a2f1f899f2e1b83ae28289ff0a923
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476482"
---
# <a name="scrollable-cursors"></a>Scrollbare Cursor
In modernen bildschirmbasierten Anwendungen führt der Benutzer einen Bildlauf rückwärts und vorwärts durch die Daten aus. Bei solchen Anwendungen ist das zurückkehren zu einer zuvor abgerufenen Zeile ein Problem. Eine Möglichkeit besteht darin, den Cursor zu schließen und erneut zu öffnen und dann Zeilen abzurufen, bis der Cursor die erforderliche Zeile erreicht. Eine weitere Möglichkeit besteht darin, das Resultset zu lesen, lokal zwischenzuspeichern und den Bildlauf in der Anwendung zu implementieren. Beide Möglichkeiten funktionieren nur mit kleinen Resultsets, und die zweite Möglichkeit ist schwierig zu implementieren. Eine bessere Lösung besteht darin, einen Bild lauffähigen Cursor zu verwenden, der im Resultset rückwärts und vorwärts verschoben *werden* kann.  
  
 Ein Bild lauffähiger *Cursor* wird häufig in modernen bildschirmbasierten Anwendungen verwendet, in denen der Benutzer einen Bildlauf durch die Daten durchführt. Anwendungen sollten jedoch scrollfähige Cursor nur dann verwenden, wenn Vorwärts Cursor den Auftrag nicht ausführen, da scrollbare Cursor in der Regel teurer als Vorwärts Cursor sind.  
  
 Die Möglichkeit, rückwärts zu verschieben, löst eine Frage aus, die für Vorwärts Cursor nicht zutreffend ist: soll ein scrollbarer Cursor Änderungen an zuvor abgerufenen Zeilen erkennen? Das heißt, wenn Sie aktualisierte, gelöschte und neu eingefügte Zeilen erkennen?  
  
 Diese Frage ist darauf zurückzuführen, dass die Definition eines Resultsets-der Satz von Zeilen, der bestimmte Kriterien erfüllt, nicht festgelegt ist, wenn Zeilen überprüft werden, um festzustellen, ob Sie mit diesen Kriterien übereinstimmen, und auch nicht, ob die Zeilen jedes Mal dieselben Daten enthalten müssen, wenn Sie abgerufen werden. Das erste weglassen ermöglicht scrollfähigen Cursorn, zu erkennen, ob Zeilen eingefügt oder gelöscht wurden, während letztere es Ihnen ermöglicht, aktualisierte Daten zu erkennen.  
  
 Die Möglichkeit, Änderungen zu erkennen, ist manchmal nützlich, manchmal nicht. Eine Buchhaltungs Anwendung benötigt z. b. einen Cursor, der alle Änderungen ignoriert. Das Ausgleichen von Büchern ist nicht möglich, wenn der Cursor die neuesten Änderungen anzeigt. Auf der anderen Seite benötigt ein Reservierungssystem für Fluggesellschaften einen Cursor, der die aktuellen Änderungen an den Daten anzeigt. ohne einen solchen Cursor muss die Datenbank fortlaufend angefordert werden, um die aktuelle Flugverfügbarkeit anzuzeigen.  
  
 Zum Abdecken der Anforderungen verschiedener Anwendungen definiert ODBC vier verschiedene Typen von scrollbaren Cursorn. Diese Cursor variieren sowohl in der Kosten als auch in der Lage, Änderungen am Resultset zu erkennen. Beachten Sie Folgendes: Wenn ein Bild lauffähigen Cursor Änderungen an Zeilen erkennen kann, kann er Sie nur erkennen, wenn er versucht, diese Zeilen erneut abzurufen. Es gibt keine Möglichkeit, dass die Datenquelle den Cursor über Änderungen an den derzeit abgerufenen Zeilen benachrichtigt. Beachten Sie auch, dass die Sichtbarkeit von Änderungen auch durch die Transaktions Isolationsstufe gesteuert wird. Weitere Informationen finden Sie unter [Transaktions Isolation](../../../odbc/reference/develop-app/transaction-isolation.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Scrollbare Cursortypen](../../../odbc/reference/develop-app/scrollable-cursor-types.md)  
  
-   [Verwenden von scrollbaren Cursor](../../../odbc/reference/develop-app/using-scrollable-cursors.md)  
  
-   [Relatives und absolutes Scrollen](../../../odbc/reference/develop-app/relative-and-absolute-scrolling.md)  
  
-   [Lesezeichen](../../../odbc/reference/develop-app/bookmarks-odbc.md)
