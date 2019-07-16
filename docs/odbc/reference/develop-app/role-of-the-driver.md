---
title: Rolle des Treibers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver error checking [ODBC]
- diagnostic information [ODBC], driver error checking
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7c344c1d8b3a4702728807af9dae7ed9ca7c5cd0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020382"
---
# <a name="role-of-the-driver"></a>Rolle des Treibers
Der Treiber überprüft, ob alle Fehler und Warnungen, die vom Treiber-Manager nicht überprüft und ordnet die Statusdatensätze, die es generiert. (Eine ODBC-2. *x* sortiert Treiber nicht Statusdatensätze.) Dies schließt Fehler und Warnungen in das Abschneiden von Daten, die Datenkonvertierung, Syntax und einige Statusübergänge. Der Treiber möglicherweise auch Fehler und Warnungen, die nur teilweise aktiviert der Treiber-Manager überprüfen. Z. B. auch der Treiber-Manager überprüft, ob der Wert des *Vorgang* in **SQLSetPos** ist zulässig, die der Treiber muss überprüfen, ob es unterstützt wird.  
  
 Der Treiber ordnet außerdem *systemeigene Fehler* - d. h. von der Datenquelle zurückgegebenen Fehler – auf SQLSTATEs. Der Treiber kann beispielsweise eine Reihe unterschiedlicher systemeigene Fehler für ungültige SQL-Syntax zum SQLSTATE 42000 (Syntaxfehler oder zugriffsverletzung) zugeordnet werden. Der Treiber gibt die systemeigene Fehlernummer in der SQL_DIAG_NATIVE-Feld des Datensatzes Status zurück. Dokumentation zu Driver sollte angezeigt werden wie Fehler und Warnungen aus der Datenquelle in Argumente zugeordnet werden **SQLGetDiagRec** und **SQLGetDiagField**.
