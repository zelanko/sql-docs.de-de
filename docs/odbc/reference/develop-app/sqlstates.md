---
title: SQLSTATEs | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ad31d9fd07e0b9f7bdf633f8ed546331880787c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149039"
---
# <a name="sqlstates"></a>SQLSTATEs
SQLSTATEs bieten ausführliche Informationen zur Ursache einer Warnung oder Fehler. Die SQLSTATEs in diesem Handbuch basieren auf diesen finden Sie in der ISO/IEF-CLI-Spezifikation, obwohl diese SQLSTATEs, die mit Instant-Messaging beginnen für ODBC spezifisch sind.  
  
 Im Gegensatz zu den Rückgabecodes die SQLSTATEs in diesem Handbuch werden die Richtlinien und Treiber sind nicht erforderlich, um zurückzugeben. Aus diesem Grund während der Treiber bei den entsprechenden SQLSTATE für alle Fehler oder eine Warnung, die sie erkennen, zurückgeben soll, sollten Anwendungen zählen nicht auf die dies immer zu. Die Gründe hierfür sind zwei:  
  
-   **Unvollständigkeit** ; Obwohl dieses Handbuchs eine große Anzahl von Fehlern und Warnungen und mögliche Ursachen für diesen Fehler und Warnungen aufgeführt sind, ist nicht vollständig und wahrscheinlich nie werden Treiber Implementierungen einfach zu viel unterscheiden sich. Alle angegebener Treiber wird wahrscheinlich nicht zurückgegeben werden, alle der SQLSTATEs aufgeführt, die in diesem Handbuch und möglicherweise SQLSTATEs nicht aufgeführt, in diesem Handbuch zurück.  
  
-   **Komplexität** einige Datenbankmodule – insbesondere relationale Datenbank-Engines - zurückgeben buchstäblich Tausenden von Fehlern und Warnungen. Die Treiber für solche Engines sind wahrscheinlich nicht alle diese Fehler und Warnungen an, die SQLSTATEs aufgrund der Aufwand beteiligt, die Inexactness der Zuordnungen, sehr groß ist der resultierende Code und den Tiefstwert des resultierenden Codes, die häufig Programmierung zurückgibt Fehler, die zur Laufzeit nie auftreten sollten. Aus diesem Grund Treiber zugeordnet wie viele Fehler und Warnungen erscheint einleuchtend, und achten Sie darauf, um diese Fehler und Warnungen auf die Anwendungslogik zuzuordnen basiert möglicherweise, wie z. B. SQLSTATE 01004 (Daten wurden abgeschnitten).  
  
 Da SQLSTATEs nicht zuverlässig zurückgegeben werden, wird sie in die meisten Anwendungen nur für den Benutzer zusammen mit ihren zugeordneten diagnosemeldung aus, die häufig zugeschnitten ist, den genauen Fehler oder eine Warnung, die aufgetreten sind, und systemeigener Fehlercode angezeigt. Nur selten eine Beeinträchtigung der Funktionalität in, auf diese Weise besteht, da Anwendungen Programmierlogik trotzdem auf den meisten SQLSTATEs basieren können. Nehmen wir beispielsweise an **SQLExecDirect** SQLSTATE 42000 (Syntaxfehler oder zugriffsverletzung) zurückgibt. Wenn die SQL-Anweisung, die diesen Fehler verursacht hat hart kodierte oder von der Anwendung erstellt, dies ist ein Programmierfehler, und der Code korrigiert werden muss. Wenn die SQL-Anweisung, die vom Benutzer eingegeben wird, dies ist ein Fehler, und die Anwendung hat alles, die was möglich ist, indem der Benutzer das Problem informiert ausgeführt.  
  
 Bei Anwendungen SQLSTATEs Programmierlogik Grundlage, sollten sie für den SQLSTATE nicht zurückgegeben werden sollen oder einem anderen SQLSTATE zurückgegeben werden darauf vorbereitet sein. Genau das SQLSTATEs zuverlässig zurückgegeben werden kann nur auf Erfahrungen mit zahlreichen Treiber basieren. Allerdings ist eine allgemeine Richtlinie, dass SQLSTATEs für Fehler, die in der Treiber oder der Treiber-Manager, im Gegensatz zu der Datenquelle auftreten eher zuverlässig zurückgegeben werden soll. Z. B. die meisten Treiber SQLSTATE HYC00 wahrscheinlich zurückgeben (optionales Feature nicht implementiert), während weniger Treiber wahrscheinlich SQLSTATE 42021 zurückgeben (Spalte ist bereits vorhanden).  
  
 Die folgenden SQLSTATEs anzugeben, zur Laufzeit Fehler oder Warnungen und eignen sich gut auf der Programmierlogik basieren. Allerdings besteht keine Garantie dafür, die alle Treiber, die sie zurückgeben.  
  
-   01004 (Daten wurden abgeschnitten.)  
  
-   01 s 02 (der Optionswert wurde geändert)  
  
-   HY008 (der Vorgang wurde abgebrochen.)  
  
-   HYC00 (optionales Feature nicht implementiert)  
  
-   HYT00 (Timeout ist abgelaufen)  
  
 SQLSTATE HYC00 (optionales Feature nicht implementiert) ist von besonderer Bedeutung, da es die einzige Möglichkeit in der eine Anwendung zu bestimmen ist kann, ob ein Treiber ein bestimmtes Attribut der Anweisung oder eine Verbindung unterstützt.  
  
 Eine vollständige Liste der SQLSTATEs und welche Funktionen, die sie zurückgeben, finden Sie unter [Anhang A: ODBC-Fehlercodes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md). Eine ausführliche Erläuterung der Bedingungen, unter denen möglicherweise jede Funktion ein bestimmtes SQLSTATE zurückgeben, finden Sie in dieser Funktion.
