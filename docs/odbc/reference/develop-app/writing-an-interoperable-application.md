---
title: Schreiben einer interoperablen Anwendung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e559eab5787a64b6bdf0850147d7d9128fc435c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208578"
---
# <a name="writing-an-interoperable-application"></a>Schreiben einer interoperablen Anwendung
Wenn eine Anwendung den gleichen Code für mehrere Treiber verwendet, muss dieser Code zwischen Treiber interoperabel sein. In den meisten Fällen ist dies eine einfache Aufgabe. Beispielsweise ist der Code zum Abrufen von Zeilen mit einem Vorwärtscursor für alle Treiber identisch. In einigen Fällen kann dies schwieriger sein. Beispielsweise muss der Code zum Erstellen von Bezeichnern für die Verwendung in SQL-Anweisungen Groß-und Kleinschreibung, Anführungszeichen und ein- und zweiteilige dreiteiligen Benennungskonventionen berücksichtigen.  
  
 Interoperable Code muss im allgemeinen Problemen mit der Unterstützung von Funktionen und Variabilität der Funktion zu bewältigen. *-Funktionsunterstützung* bezieht sich auf, und zwar unabhängig davon, ob ein bestimmtes Feature unterstützt wird. Z. B. nicht alle DBMS Transaktionen unterstützt, und interoperable Code muss ordnungsgemäß funktionieren, unabhängig von der Unterstützung von Transaktionen. *Feature Variabilität* bezieht sich auf die Abweichung in die Art und Weise, in denen eine bestimmte Funktion unterstützt wird. Katalognamen werden z. B. am Anfang von Bezeichnern in einigen DBMS und am Ende von Bezeichnern in anderen platziert.  
  
 Zur Entwurfszeit oder zur Laufzeit können Anwendungen mit Unterstützung von Features und Feature-Variabilität verarbeiten. Um mit Unterstützung von Funktionen und Variabilität zur Entwurfszeit zu arbeiten, ein Entwickler beschäftigt sich mit der Ziel-DBMS und die Treiber und stellt sicher, dass der gleiche Code untereinander interoperabel ist. Dies ist normalerweise die Möglichkeit, in der Anwendungen mit niedriger oder nur eine begrenzte Interoperabilität diese Probleme behandelt.  
  
 Z. B. benötigt Wenn der Entwickler wird sichergestellt, dass eine vertikale Anwendung nur mit vier bestimmten DBMS-Systeme funktionieren und jede dieser DBMS-Transaktionen unterstützt, die Anwendung nicht Code zu prüfen, Unterstützung von Transaktionen zur Laufzeit. Sie können immer davon ausgehen, dass Transaktionen aufgrund der Entscheidung zur Entwurfszeit mit nur vier DBMS-Systeme, verfügbar sind jeweils Transaktionen unterstützt.  
  
 Zur Unterstützung von Funktionen und Variabilität bei der Ausführung zu beheben, muss die Anwendung testen verschiedene Funktionen zur Laufzeit und entsprechend agiert. Dies ist normalerweise die Möglichkeit, in der hochgradig interoperabel Anwendungen diese Probleme behandelt. Feature-Unterstützung Probleme auftreten bedeutet dies, das Schreiben von Code, mit der Funktion optional oder Schreiben von Code, der die Funktion emuliert, wenn es nicht verfügbar ist. Feature-Variabilität Probleme auftreten bedeutet dies, das Schreiben von Code, der alle mögliche Variationen unterstützt.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Überprüfung der Unterstützung von Funktionen und Variabilität](../../../odbc/reference/develop-app/checking-feature-support-and-variability.md)  
  
-   [Funktionen, die überwacht werden müssen](../../../odbc/reference/develop-app/features-to-watch-for.md)
