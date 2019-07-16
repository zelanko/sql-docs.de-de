---
title: Statische ODBC-Cursor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], static
- static cursors [ODBC]
ms.assetid: 28cb324c-e1c3-4b5c-bc3e-54df87037317
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bcb7c39d39492b91c0b62c5eff2229eb5f61df6b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67987839"
---
# <a name="odbc-static-cursors"></a>Statische ODBC-Cursor
Ein statischer Cursor ist in der das Resultset angezeigt wird, statisch sein. Es wird nicht in der Regel Änderungen erkannt, die vorgenommen wurden, um die Mitgliedschaft, Reihenfolge oder Werte im Resultset nach der der Cursor geöffnet wird. Nehmen wir beispielsweise an ein statischer Cursor abruft, eine Zeile und eine andere Anwendung wird diese Zeile aktualisiert. Wenn der statische Cursor die Zeile refetches, sind die Werte, die es erkennt unverändert, obwohl die Änderungen, die von der anderen Anwendung vorgenommen wurden.  
  
 Statische Cursor können eigene Updates, löschungen und einfügungen erkennen, obwohl sie nicht dazu erforderlich sind. Gibt an, ob ein bestimmter statischer Cursor für diese Änderungen erkennt, wird über die Feedbackoption im SQL_STATIC_SENSITIVITY in gemeldet **SQLGetInfo**. Statische Cursor erkennen nie anderen updates, Lösch- und Einfügevorgänge.  
  
 Die vom Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung angegebenen zeilenstatusarray kann SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO oder SQL_ROW_ERROR für jede Zeile enthalten. Es zurückgibt SQL_ROW_UPDATED, SQL_ROW_DELETED oder SQL_ROW_ADDED, für die Zeilen aktualisiert, gelöscht oder eingefügt, indem Sie den Mauszeiger, vorausgesetzt, dass der Cursor solche Änderungen erkennen kann.  
  
 Statische Cursor werden in der Regel implementiert, durch das Sperren von Zeilen im Resultset oder durch Erstellen einer Kopie oder Momentaufnahme des Ergebnisses festgelegt. Sperren von Zeilen relativ einfach ist, hat aber den Nachteil deutlich weniger. Erstellen einer Kopie ermöglicht mehr Parallelität und können den Cursor zu verfolgen eigene Updates, löschungen und fügt ein durch die Kopie ändern. Eine Kopie ist jedoch teurer zu machen und können aus den zugrunde liegenden Daten abweichen, wenn die Daten von anderen Benutzern geändert werden.
