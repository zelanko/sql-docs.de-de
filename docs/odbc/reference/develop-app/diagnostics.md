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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a09f46d3fd6aa2f9b9c7310af6d3ddc90f78389f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305151"
---
# <a name="diagnostics"></a>Diagnose
Funktionen in ODBC geben Diagnoseinformationen auf zwei Arten zurück. Der Rückgabecode gibt den allgemeinen Erfolg oder Misserfolg der Funktion an, während Diagnosedaten Sätze ausführliche Informationen über die Funktion bereitstellen. Mindestens ein Diagnosedaten Satz-der Header Daten Satz-wird zurückgegeben, auch wenn die Funktion erfolgreich ausgeführt wurde.  
  
 Diagnoseinformationen werden zur Entwicklungszeit zum Erfassen von Programmierfehlern verwendet, z. b. ungültige Handles und Syntax Fehler in hart codierten SQL-Anweisungen. Sie wird zur Laufzeit verwendet, um Laufzeitfehler und-Warnungen wie das Abschneiden von Daten, Zugriffs Verletzungen und Syntax Fehler in SQL-Anweisungen abzufangen, die vom Benutzer eingegeben wurden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Rückgabecodes](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Diagnosedatensätze](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Verwenden von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Implementieren von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Beispiele für die Diagnosebehandlung](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
