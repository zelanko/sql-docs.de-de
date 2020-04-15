---
title: Schreiben einer interoperabelen Anwendung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: 8b42b8ae-7862-4b63-a0b3-2a204e0c43a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 553e718e0759e47701e7f8c04561693358d5dc52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289082"
---
# <a name="writing-an-interoperable-application"></a>Schreiben einer interoperablen Anwendung
Wenn eine Anwendung denselben Code für mehr als einen Treiber verwendet, muss dieser Code zwischen diesen Treibern interoperabel sein. In den meisten Fällen ist dies eine einfache Aufgabe. Beispielsweise ist der Code zum Abrufen von Zeilen mit einem Vorwärtscursor für alle Treiber identisch. In einigen Fällen kann dies schwieriger sein. Beispielsweise muss der Code zum Erstellen von Bezeichnern für die Verwendung in SQL-Anweisungen Bezeichner-Groß-/Kleinschreibung, Quotierung und einteilige, zweiteilige und dreiteilige Namenskonventionen berücksichtigen.  
  
 Im Allgemeinen muss interoperabler Code mit Problemen der Funktionsunterstützung und der Funktionsvariabilität fertig werden. *Feature-Unterstützung* bezieht sich darauf, ob ein bestimmtes Feature unterstützt wird oder nicht. Beispielsweise unterstützen nicht alle DBMS Transaktionen, und interoperabler Code muss unabhängig von der Transaktionsunterstützung ordnungsgemäß funktionieren. *Featurevariabilität* bezieht sich auf Variationen in der Art und Weise, in der ein bestimmtes Feature unterstützt wird. Katalognamen werden z. B. am Anfang von Bezeichnern in einigen DBMS und am Ende von Bezeichnern in anderen platziert.  
  
 Anwendungen können sich mit Feature-Unterstützung und Funktionsvariabilität zur Entwurfszeit oder zur Laufzeit befassen. Um die Funktionsunterstützung und Variabilität zur Entwurfszeit zu behandeln, betrachtet ein Entwickler die Ziel-DBMS und Treiber und stellt sicher, dass derselbe Code zwischen ihnen interoperabel ist. Dies ist im Allgemeinen die Art und Weise, wie Anwendungen mit geringer oder begrenzter Interoperabilität mit diesen Problemen umgehen.  
  
 Wenn der Entwickler beispielsweise garantiert, dass eine vertikale Anwendung nur mit vier bestimmten DBMS funktioniert, und wenn jeder dieser DBMS Transaktionen unterstützt, benötigt die Anwendung keinen Code, um zur Laufzeit nach Transaktionsunterstützung zu suchen. Es kann immer davon ausgegangen werden, dass Transaktionen aufgrund der Entwurfszeitentscheidung verfügbar sind, nur vier DBMS zu verwenden, von denen jede Transaktionen unterstützt.  
  
 Um mit Feature-Unterstützung und Variabilität zur Laufzeit umgehen zu können, muss die Anwendung zur Laufzeit auf verschiedene Funktionen testen und entsprechend handeln. Dies ist im Allgemeinen die Art und Weise, wie hoch interoperable Anwendungen mit diesen Problemen umgehen. Bei Feature-Support-Problemen bedeutet dies das Schreiben von Code, der das Feature optional macht, oder das Schreiben von Code, der das Feature emuliert, wenn es nicht verfügbar ist. Bei Featurevariabilitätsproblemen bedeutet dies das Schreiben von Code, der alle möglichen Variationen unterstützt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Überprüfung der Funktionsunterstützung und Variabilität](../../../odbc/reference/develop-app/checking-feature-support-and-variability.md)  
  
-   [Zu überwachende Funktionen](../../../odbc/reference/develop-app/features-to-watch-for.md)
