---
title: SQLSTATEs | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299727"
---
# <a name="sqlstates"></a>SQLSTATEs
SQLSTATEs stellen detaillierte Informationen zur Ursache einer Warnung oder eines Fehlers bereit. Die SQLSTATEs in diesem Handbuch basieren auf den in der ISO/IEF CLI-Spezifikation gefundenen, obwohl die SQLSTATEs, die mit IM beginnen, für ODBC spezifisch sind.  
  
 Im Gegensatz zu Rückgabecodes sind die SQLSTATEs in diesem Handbuch Richtlinien, und Treiber müssen sie nicht zurückgeben. Daher sollten Treiber zwar die richtige SQLSTATE für fehlerfähige Fehler oder Warnungen zurückgeben, die sie erkennen können, Anwendungen sollten daher nicht damit rechnen, dass dies immer der Fall ist. Die Gründe für diese Situation sind zweierlei:  
  
-   **Unvollständigkeit** Obwohl dieses Handbuch eine große Anzahl von Fehlern und Warnungen und mögliche Ursachen für diese Fehler und Warnungen auflistet, ist es nicht vollständig und wird es wahrscheinlich nie sein; Treiberimplementierungen variieren einfach zu sehr. Jeder bestimmte Treiber gibt wahrscheinlich nicht alle in diesem Handbuch aufgeführten SQLSTATEs zurück und gibt möglicherweise SQLSTATEs zurück, die nicht in diesem Handbuch aufgeführt sind.  
  
-   **Komplexität** Einige Datenbank-Engines - insbesondere relationale Datenbank-Engines - geben buchstäblich Tausende von Fehlern und Warnungen zurück. Die Treiber für solche Module sind unwahrscheinlich, dass sie alle diese Fehler und Warnungen SQLSTATEs zuordnen, da der Aufwand, die Ungenauigkeit der Zuordnungen, die Größe des resultierenden Codes und der niedrige Wert des resultierenden Codes häufig Programmierfehler zurückgegeben werden, die zur Laufzeit nie auftreten sollten. Daher sollten Treiber so viele Fehler und Warnungen zuordnen, wie vernünftig erscheinen, und sicherstellen, dass sie die Fehler und Warnungen zuordnen, auf denen die Anwendungslogik basieren könnte, z. B. SQLSTATE 01004 (Daten abgeschnitten).  
  
 Da SQLSTATEs nicht zuverlässig zurückgegeben werden, zeigen die meisten Anwendungen sie dem Benutzer zusammen mit der zugehörigen Diagnosemeldung an, die häufig auf den aufgetretenen Fehler oder die Warnung und den systemeigenen Fehlercode zugeschnitten ist. Dabei kann die Funktionalität nur selten beeinträchtigt werden, da Anwendungen die Programmierlogik ohnehin nicht auf den meisten SQLSTATEs basieren können. Angenommen, **SQLExecDirect** gibt SQLSTATE 42000 zurück (Syntaxfehler oder Zugriffsverletzung). Wenn die SQL-Anweisung, die diesen Fehler verursacht hat, hartcodiert oder von der Anwendung erstellt wird, ist dies ein Programmierfehler, und der Code muss behoben werden. Wenn die SQL-Anweisung vom Benutzer eingegeben wird, ist dies ein Benutzerfehler, und die Anwendung hat alles getan, was möglich ist, indem sie den Benutzer über das Problem informiert hat.  
  
 Wenn Anwendungen die Programmierlogik auf SQLSTATEs basieren, sollten sie darauf vorbereitet sein, dass SQLSTATE nicht zurückgegeben wird oder dass eine andere SQLSTATE zurückgegeben wird. Welche SQLSTATEs zuverlässig zurückgegeben werden, kann nur auf Erfahrungen mit zahlreichen Treibern basieren. Eine allgemeine Richtlinie ist jedoch, dass SQLSTATEs für Fehler, die im Treiber oder Treiber-Manager auftreten, im Gegensatz zur Datenquelle, mit größerer Wahrscheinlichkeit zuverlässig zurückgegeben werden. Beispielsweise geben die meisten Treiber wahrscheinlich SQLSTATE HYC00 zurück (Optionale Funktion ist nicht implementiert), während weniger Treiber wahrscheinlich SQLSTATE 42021 zurückgeben (Spalte ist bereits vorhanden).  
  
 Die folgenden SQLSTATEs weisen auf Laufzeitfehler oder Warnungen hin und sind gute Kandidaten für die Programmierungslogik. Es gibt jedoch keine Garantie, dass alle Fahrer sie zurückgeben.  
  
-   01004 (Daten abgeschnitten)  
  
-   01S02 (Optionswert geändert)  
  
-   HY008 (Vorgang abgebrochen)  
  
-   HYC00 (Optionale Funktion nicht implementiert)  
  
-   HYT00 (Timeout abgelaufen)  
  
 SQLSTATE HYC00 (Optionale Funktion nicht implementiert) ist besonders wichtig, da es die einzige Möglichkeit ist, wie eine Anwendung bestimmen kann, ob ein Treiber eine bestimmte Anweisung oder ein Verbindungsattribut unterstützt.  
  
 Eine vollständige Liste der SQLSTATEs und der enfolgenden Funktionen finden Sie in [Anhang A: ODBC-Fehlercodes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md). Eine detaillierte Erläuterung der Bedingungen, unter denen jede Funktion eine bestimmte SQLSTATE zurückgeben kann, finden Sie in dieser Funktion.
