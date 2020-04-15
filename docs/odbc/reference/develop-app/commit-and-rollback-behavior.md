---
title: Commit- und Rollbackverhalten | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c67c29b295160a2908152b22c7a349ce4c0f9f50
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299130"
---
# <a name="commit-and-rollback-behavior"></a>Commit- und Rollbackverhalten
Ein häufiges Verhalten unter Server-DBMSs besteht darin, Cursor zu schließen und vorbereitete Anweisungen zu verwerfen, wenn eine Anweisung festgeschrieben oder zurückgesetzt wird. Desktopdatenbanken halten Cursor eher offen und bereiten Anweisungen vor. Weitere Informationen finden Sie in den Optionen SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR in der [SQLGetInfo-Funktionsbeschreibung](../../../odbc/reference/syntax/sqlgetinfo-function.md) und [den Auswirkungen von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).
