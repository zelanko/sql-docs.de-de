---
title: Implementieren von SQLGetDiagRec und SQLGetDiagField | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c090af19a9296e46e3036ca23f6c97298bcb1b8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300140"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Implementieren von SQLGetDiagRec und SQLGetDiagField
**SQLGetDiagRec** und **SQLGetDiagField** werden vom Treiber-Manager und jedem Treiber implementiert. Der Treiber-Manager und jeder Treiber verwalten Diagnosedatensätze für jede Umgebung, verbindung, Anweisung und Deskriptor-Handle, und geben diese Datensätze nur dann frei, wenn eine andere Funktion mit diesem Handle aufgerufen wird oder das Handle freigegeben wird.  
  
 Obwohl sowohl der Treiber-Manager als auch jeder Treiber den ersten Statusdatensatz entsprechend den Rankings in [der Sequenz von Statusdatensätzen](../../../odbc/reference/develop-app/sequence-of-status-records.md)bestimmen müssen, bestimmt der Treiber-Manager die endgültige Sequenz der Datensätze.  
  
 **SQLGetDiagRec** und **SQLGetDiagField** veröffentlichen keine Diagnosedatensätze über sich selbst.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Regeln der Diagnosebehandlung](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Rolle des Treiber-Managers](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Rolle des Treibers](../../../odbc/reference/develop-app/role-of-the-driver.md)
