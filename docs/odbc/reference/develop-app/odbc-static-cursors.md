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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987839"
---
# <a name="odbc-static-cursors"></a>Statische ODBC-Cursor
Ein statischer Cursor ist ein Wert, in dem das Resultset statisch erscheint. Sie erkennt in der Regel keine Änderungen, die an der Mitgliedschaft, der Reihenfolge oder den Werten des Resultsets vorgenommen wurden, nachdem der Cursor geöffnet wurde. Angenommen, ein statischer Cursor Ruft eine Zeile ab, und eine andere Anwendung aktualisiert dann diese Zeile. Wenn der statische Cursor die Zeile wiederholt, werden die angezeigten Werte trotz der Änderungen, die von der anderen Anwendung vorgenommen wurden, unverändert.  
  
 Statische Cursor können Ihre eigenen Updates, Löschungen und Einfügungen erkennen, obwohl dies nicht erforderlich ist. Ob ein bestimmter statischer Cursor diese Änderungen erkennt, wird über die SQL_STATIC_SENSITIVITY-Option in **SQLGetInfo**gemeldet. Statische Cursor erkennen nie andere Updates, Löschungen und Einfügungen.  
  
 Das vom SQL_ATTR_ROW_STATUS_PTR Statement-Attribut angegebene Zeilen Status Array kann SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO oder SQL_ROW_ERROR für jede Zeile enthalten. Es gibt SQL_ROW_UPDATED, SQL_ROW_DELETED oder SQL_ROW_ADDED für Zeilen zurück, die vom Cursor aktualisiert, gelöscht oder eingefügt wurden, vorausgesetzt, dass der Cursor solche Änderungen erkennen kann.  
  
 Statische Cursor werden in der Regel durch Sperren der Zeilen im Resultset oder durch Erstellen einer Kopie oder Momentaufnahme des Resultsets implementiert. Obwohl das Sperren von Zeilen relativ einfach ist, hat dies den Nachteil, dass die Parallelität erheblich reduziert wird. Das Erstellen einer Kopie ermöglicht eine größere Parallelität und ermöglicht dem Cursor, seine eigenen Aktualisierungen, Löschungen und Einfügungen durch Ändern der Kopie nachzuverfolgen. Allerdings ist eine Kopie kostengünstiger und kann von den zugrunde liegenden Daten abweichen, da diese Daten von anderen Personen geändert werden.
