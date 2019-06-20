---
title: Commit- und Rollbackverhalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bad1706e7283c0b0a5111e93c9dfd7ae494c8ef4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63125496"
---
# <a name="commit-and-rollback-behavior"></a>Commit- und Rollbackverhalten
Ein gemeinsames Verhalten für Server-DBMS ist zum Schließen der Cursor und vorbereitete Anweisungen zu verwerfen, wenn eine Anweisung ein Commit oder Rollback ausgeführt. Desktopdatenbanken sind eher Cursor geöffnet ist und Beibehalten von vorbereiteten Anweisungen. Weitere Informationen finden Sie unter den SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Optionen in der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) funktionsbeschreibung und [Auswirkung von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).
