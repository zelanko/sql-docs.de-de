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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 553e718e0759e47701e7f8c04561693358d5dc52
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81289082"
---
# <a name="writing-an-interoperable-application"></a>Schreiben einer interoperablen Anwendung
Wenn eine Anwendung denselben Code für mehr als einen Treiber verwendet, muss dieser Code unter diesen Treibern interoperabel sein. In den meisten Fällen ist dies eine einfache Aufgabe. Beispielsweise ist der Code zum Abrufen von Zeilen mit einem Vorwärts Cursor für alle Treiber identisch. In einigen Fällen kann dies schwieriger sein. Der Code zum Erstellen von Bezeichnern für die Verwendung in SQL-Anweisungen muss beispielsweise bezeichnerfälle, Anführungszeichen und einteilige, zweiteilige und dreiteilige Benennungs Konventionen in Erwägung gezogen werden.  
  
 Im Allgemeinen muss der interoperable Code Probleme mit der Featureunterstützung und der Funktions Variabilität meistern. Die *Funktions Unterstützung* bezieht sich darauf, ob ein bestimmtes Feature unterstützt wird. Beispielsweise müssen nicht alle DBMSs-Unterstützungs Transaktionen und der interoperable Code unabhängig von der Transaktionsunterstützung ordnungsgemäß funktionieren. Die *Funktions Variabilität* bezieht sich auf Abweichungen in der Art und Weise, in der eine bestimmte Funktion unterstützt wird. Katalognamen werden z. b. am Anfang der Bezeichner in einigen DBMSs und am Ende von Bezeichnerzeichen in anderen platziert.  
  
 Anwendungen können die Featureunterstützung und die Funktions Variabilität zur Entwurfszeit oder zur Laufzeit behandeln. Um die Featureunterstützung und Varianz zur Entwurfszeit zu behandeln, untersucht ein Entwickler die Ziel-DBMSs und-Treiber und stellt sicher, dass der gleiche Code zwischen Ihnen interoperabel ist. Dabei handelt es sich im Allgemeinen um die Art und Weise, in der Anwendungen mit geringer oder eingeschränkter Interoperabilität diese Probleme beheben.  
  
 Wenn der Entwickler beispielsweise sicherstellt, dass eine vertikale Anwendung nur mit vier bestimmten DBMSs funktioniert und jeder dieser DBMSs Transaktionen unterstützt, benötigt die Anwendung keinen Code zum Überprüfen der Transaktionsunterstützung zur Laufzeit. Es kann immer angenommen werden, dass Transaktionen aufgrund der Entwurfszeit Entscheidung zur Verwendung von nur vier DBMSs verfügbar sind, von denen jede Transaktionen unterstützt.  
  
 Um die Featureunterstützung und Varianz zur Laufzeit zu behandeln, muss die Anwendung zur Laufzeit auf verschiedene Funktionen testen und entsprechend reagieren. Dies ist im Allgemeinen die Art und Weise, in der hochgradig interoperable Anwendungen diese Probleme behandeln. Bei Problemen mit der Featureunterstützung bedeutet dies, dass Sie Code schreiben, der die Funktion als optional macht, oder Code schreiben, der die Funktion emuliert, wenn Sie nicht verfügbar ist. Bei Problemen mit der featurevarianz bedeutet dies das Schreiben von Code, der alle möglichen Variationen unterstützt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Überprüfung der Funktionsunterstützung und Variabilität](../../../odbc/reference/develop-app/checking-feature-support-and-variability.md)  
  
-   [Zu überwachende Funktionen](../../../odbc/reference/develop-app/features-to-watch-for.md)
