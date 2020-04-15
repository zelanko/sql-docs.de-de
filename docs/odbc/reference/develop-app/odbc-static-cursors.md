---
title: STATISCHE ODBC-Cursor | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b99566c473e88684e8b092a5ac9fc899e7dce177
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282444"
---
# <a name="odbc-static-cursors"></a>Statische ODBC-Cursor
Ein statischer Cursor ist ein Cursor, bei dem das Resultset statisch zu sein scheint. Es werden in der Regel keine Änderungen erkannt, die nach dem Öffnen des Cursors an der Mitgliedschaft, Der Reihenfolge oder den Werten des Resultsets vorgenommen wurden. Angenommen, ein statischer Cursor ruft eine Zeile ab, und eine andere Anwendung aktualisiert diese Zeile. Wenn der statische Cursor die Zeile erneut abruft, bleiben die angezeigten Werte trotz der von der anderen Anwendung vorgenommenen Änderungen unverändert.  
  
 Statische Cursor können ihre eigenen Aktualisierungen, Löschungen und Einfügungen erkennen, obwohl sie dazu nicht erforderlich sind. Ob ein bestimmter statischer Cursor diese Änderungen erkennt, wird über die SQL_STATIC_SENSITIVITY-Option in **SQLGetInfo**gemeldet. Statische Cursor erkennen niemals andere Aktualisierungen, Löschungen und Einfügungen.  
  
 Das vom Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung angegebene Zeilenstatusarray kann SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO oder SQL_ROW_ERROR für eine zeile enthalten. Es gibt SQL_ROW_UPDATED, SQL_ROW_DELETED oder SQL_ROW_ADDED für Zeilen zurück, die vom Cursor aktualisiert, gelöscht oder eingefügt wurden, vorausgesetzt, dass der Cursor solche Änderungen erkennen kann.  
  
 Statische Cursor werden in der Regel implementiert, indem die Zeilen im Resultset gesperrt oder eine Kopie oder ein Snapshot des Resultsets erstellt werden. Obwohl das Sperren von Zeilen relativ einfach ist, hat es den Nachteil, dass die Parallelität erheblich reduziert wird. Das Erstellen einer Kopie ermöglicht eine größere Parallelität und ermöglicht es dem Cursor, seine eigenen Aktualisierungen, Löschungen und Einfügungen nachzuverfolgen, indem er die Kopie ändert. Eine Kopie ist jedoch teurer zu erstellen und kann von den zugrunde liegenden Daten abweichen, da diese Daten von anderen geändert werden.
