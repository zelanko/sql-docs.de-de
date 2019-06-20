---
title: Diagnose | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72e79d377371277720e2fcc15a31ce715693d832
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63242299"
---
# <a name="diagnostics"></a>Diagnose
Funktionen in ODBC werden Diagnoseinformationen auf zwei Arten zurückgeben. Der Rückgabecode gibt an, den Erfolg oder Fehler bei der Funktion an, während der DiagnoseDatensätze detaillierte Informationen über die Funktion bereitstellen. Mindestens ein Diagnosedatensatz - Headerdatensatz - wird zurückgegeben, auch wenn die Funktion erfolgreich ist.  
  
 Diagnoseinformationen wird zum Zeitpunkt der Entwicklung zum Abfangen von Programmierfehlern wie ungültigen Handles und Syntaxfehlern in hartcodierten SQL-Anweisungen. Es wird zur Laufzeit verwendet, zum Abfangen von Laufzeitfehlern und-Warnungen wie z. B. das Abschneiden von Daten, zugriffsverletzungen und Syntaxfehler in SQL-Anweisungen, die vom Benutzer eingegeben werden.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Rückgabecodes](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Diagnosedatensätze](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Verwenden von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Implementieren von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Beispiele für die Diagnosebehandlung](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
