---
title: Commit-und Rollback-Verhalten | Microsoft-Dokumentation
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
ms.openlocfilehash: 643d7d4174df66abfcee274c1f987e8f405d19b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083345"
---
# <a name="commit-and-rollback-behavior"></a>Commit- und Rollbackverhalten
Ein häufiges Verhalten zwischen Server-DBMSs besteht darin, Cursor zu schließen und vorbereitete Anweisungen zu verwerfen, wenn ein Commit oder ein Rollback für eine Anweisung ausgeführt wird. Bei Desktop Datenbanken ist es wahrscheinlicher, dass Cursor geöffnet werden und vorbereitete Anweisungen aufbewahrt werden. Weitere Informationen finden Sie in den Optionen SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktionsbeschreibung und [Auswirkung von Transaktionen auf Cursors und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).
