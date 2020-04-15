---
title: Diagnose | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a09f46d3fd6aa2f9b9c7310af6d3ddc90f78389f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305151"
---
# <a name="diagnostics"></a>Diagnose
Funktionen in ODBC geben Diagnoseinformationen auf zwei Arten zurück. Der Rückgabecode gibt den Gesamterfolg oder Misserfolg der Funktion an, während Diagnosedatensätze detaillierte Informationen über die Funktion bereitstellen. Mindestens ein Diagnosedatensatz - der Headerdatensatz - wird zurückgegeben, auch wenn die Funktion erfolgreich ist.  
  
 Diagnoseinformationen werden zur Entwicklungszeit verwendet, um Programmierfehler wie ungültige Handles und Syntaxfehler in hartcodierten SQL-Anweisungen abzufangen. Es wird zur Laufzeit verwendet, um Laufzeitfehler und Warnungen wie Datenkürzungen, Zugriffsverletzungen und Syntaxfehler in SQL-Anweisungen abzufangen, die vom Benutzer eingegeben wurden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Rückgabecodes](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Diagnosedatensätze](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Verwenden von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Implementieren von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Beispiele für die Diagnosebehandlung](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
