---
title: Sqlstates | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], sqlstates
- SQLSTATE [ODBC]
ms.assetid: f29fff2e-3d09-4a8c-a2f9-2059062cbebf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be4bca929b8d48c301c6e71917503387004a6ec5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299727"
---
# <a name="sqlstates"></a>SQLSTATEs
Sqlstates stellen ausführliche Informationen zur Ursache einer Warnung oder eines Fehlers bereit. Die SQLStates in diesem Handbuch basieren auf den in der ISO/IEF-CLI-Spezifikation gefundenen Sqlstates, obwohl die SQLStates-Werte, die mit im beginnen, für ODBC spezifisch sind.  
  
 Anders als bei Rückgabecodes sind SQLStates in diesem Handbuch Richtlinien, und Treiber müssen Sie nicht zurückgeben. Obwohl Treiber den richtigen SQLSTATE für alle Fehler oder Warnungen zurückgeben sollten, die Sie erkennen können, sollten die Anwendungen nicht auf diese immer auftretenden Ereignisse warten. Die Gründe für diese Situation sind zweierlei:  
  
-   **Vollständigkeit** Obwohl dieses Handbuch eine große Anzahl von Fehlern und Warnungen sowie mögliche Ursachen für diese Fehler und Warnungen auflistet, ist es nicht abgeschlossen und wahrscheinlich nie. Treiber Implementierungen variieren einfach zu viel. Ein beliebiger Treiber gibt wahrscheinlich nicht alle in diesem Handbuch aufgeführten Sqlstates zurück und gibt möglicherweise Sqlstates zurück, die in diesem manuell nicht aufgeführt sind.  
  
-   **Komplexität** Einige Datenbank-Engines, insbesondere relationale Datenbank-Engines, geben buchstäblich Tausende von Fehlern und Warnungen zurück. Die Treiber für solche Engines ordnen in der Regel nicht alle diese Fehler und Warnungen den Sqlstates zu, weil der Aufwand, die ingenauigkeit der Zuordnungen, die große Größe des resultierenden Codes und der niedrige Wert des resultierenden Codes auftreten, der häufig Programmierfehler zurückgibt, die zur Laufzeit nie auftreten sollten. Daher sollten Treiber so viele Fehler und Warnungen wie sinnvoll zuordnen und sicherstellen, dass diese Fehler und Warnungen, auf denen die Anwendungslogik basieren könnte, zugeordnet werden, z. b. SQLSTATE 01004 (Daten abgeschnitten).  
  
 Da Sqlstates nicht zuverlässig zurückgegeben werden, zeigen die meisten Anwendungen Sie dem Benutzer einfach zusammen mit der zugehörigen Diagnose Meldung an, die häufig auf den spezifischen Fehler bzw. die aufgetretene Warnung und systemeigenen Fehlercode zugeschnitten ist. In diesem Fall gibt es in seltenen Fällen keinen Funktionsverlust, da Anwendungen nicht auf den meisten Sqlstates basieren können. Angenommen, **SQLExecDirect** gibt SQLSTATE 42000 (Syntax Fehler oder Zugriffsverletzung) zurück. Wenn die SQL-Anweisung, die diesen Fehler verursacht hat, hart codiert oder von der Anwendung erstellt wurde, handelt es sich hierbei um einen Programmierfehler, und der Code muss korrigiert werden. Wenn die SQL-Anweisung vom Benutzer eingegeben wird, handelt es sich hierbei um einen Benutzerfehler, und die Anwendung hat alles abgeschlossen, was möglich ist, indem der Benutzer über das Problem informiert wird.  
  
 Wenn Anwendungen eine Basis Programmierlogik auf Sqlstates ausführen, sollten Sie darauf vorbereitet werden, dass SQLSTATE nicht zurückgegeben oder ein anderer SQLSTATE zurückgegeben wird. Genau, welche Sqlstates zuverlässig zurückgegeben werden, kann nur auf einer Vielzahl von Treibern basieren. Eine allgemeine Richtlinie ist jedoch, dass Sqlstates für Fehler, die im Treiber-oder Treiber-Manager auftreten, im Gegensatz zur Datenquelle eher zuverlässig zurückgegeben werden. Beispielsweise geben die meisten Treiber wahrscheinlich SQLSTATE HYC00 (optionales Feature nicht implementiert) zurück, während weniger Treiber wahrscheinlich SQLSTATE 42021 zurückgeben (die Spalte ist bereits vorhanden).  
  
 Die folgenden Sqlstates geben Laufzeitfehler oder-Warnungen an und sind gute Kandidaten für die Basis der Programmierlogik. Allerdings gibt es keine Garantie dafür, dass Sie von allen Treibern zurückgegeben werden.  
  
-   01004 (abgeschnittene Daten)  
  
-   01s02 (Optionswert geändert)  
  
-   HY008 (Vorgang abgebrochen)  
  
-   HYC00 (optionales Feature nicht implementiert)  
  
-   HYT00 (Timeout abgelaufen)  
  
 SQLSTATE HYC00 (optionales Feature nicht implementiert) ist besonders wichtig, da es die einzige Möglichkeit ist, eine Anwendung zu ermitteln, ob ein Treiber eine bestimmte Anweisung oder ein Verbindungs Attribut unterstützt.  
  
 Eine umfassende Liste mit Sqlstates und den Funktionen, die Sie zurückgeben, finden Sie unter [Anhang a: ODBC-Fehler Codes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md). Eine ausführliche Erläuterung der Bedingungen, unter denen jede Funktion möglicherweise einen bestimmten SQLSTATE zurückgibt, finden Sie unter diese Funktion.
