---
title: Implementieren von SQLGetDiagRec und SQLGetDiagField | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a4b602d5ff4a94d2888395e6a62f03553fb50f98
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68216378"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Implementieren von SQLGetDiagRec und SQLGetDiagField
**SQLGetDiagRec** und **SQLGetDiagField** werden von der Treiber-Manager und jeden Treiber implementiert. Der Treiber-Manager jeden Treiber DiagnoseDatensätze für jede Umgebung, Verbindung, -Anweisung und Deskriptorhandles verwalten und die Datensätze freigeben, nur, wenn Sie mit einer anderen Funktion aufgerufen wird, dass Handle oder das Handle freigegeben wird.  
  
 Obwohl sowohl der Treiber-Manager, und jeder Treiber entsprechend der Rangfolge in den ersten Status-Datensatz festlegen müssen [Sequenz der Statusdatensätze](../../../odbc/reference/develop-app/sequence-of-status-records.md), bestimmt der Treiber-Manager, die endgültige Reihenfolge der Datensätze.  
  
 **SQLGetDiagRec** und **SQLGetDiagField** veröffentlichen DiagnoseDatensätze über sich selbst nicht.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Regeln der Diagnosebehandlung](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Rolle des Treiber-Managers](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Rolle des Treibers](../../../odbc/reference/develop-app/role-of-the-driver.md)
