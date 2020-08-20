---
description: Commit- und Rollbackverhalten
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 309d28dfb2c97fc8f3d8631edc3f0f7b9db85508
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494668"
---
# <a name="commit-and-rollback-behavior"></a>Commit- und Rollbackverhalten
Ein häufiges Verhalten zwischen Server-DBMSs besteht darin, Cursor zu schließen und vorbereitete Anweisungen zu verwerfen, wenn ein Commit oder ein Rollback für eine Anweisung ausgeführt wird. Bei Desktop Datenbanken ist es wahrscheinlicher, dass Cursor geöffnet werden und vorbereitete Anweisungen aufbewahrt werden. Weitere Informationen finden Sie in den Optionen SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktionsbeschreibung und [Auswirkung von Transaktionen auf Cursors und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).
