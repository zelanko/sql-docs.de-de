---
title: Unicode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC]
- Unicode [ODBC], about Unicode
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7e0044a2e2efbf0d8921a07ed4679806ba50bcd1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087566"
---
# <a name="unicode"></a>Unicode
Unicode definiert die Codierung für Zeichen in vielen Sprachen.  
  
 Weitere Informationen zum Unicode-Standard finden Sie [im Unicode-Konsortium](https://www.unicode.org).  
  
 Unicode definiert einen universellen Zeichensatz. Eine Windows-ANSI-Codepage definiert einen Zeichensatz, der in der Regel Zeichen für eine Sprache enthält. Es kann schwieriger sein, eine Anwendung zu schreiben, die für die Verwendung unterschiedlicher Codepages erforderlich ist.  
  
 Unicode erfordert keine Codepage. Jeder Codepunkt wird einem einzelnen Zeichen in einer Sprache zugeordnet.  
  
 Derzeit ist die einzige Unicode-Codierung, die von ODBC unterstützt wird, UCS-2, das eine 16-Bit-Ganzzahl (mit fester Länge) zur Darstellung eines Zeichens verwendet. Mit Unicode können Anwendungen in verschiedenen Sprachen arbeiten.  
  
 Der Treiber-Manager für ODBC 3,5 (oder höher) ist Unicode-aktiviert. Dies wirkt sich auf zwei Hauptbereiche aus: Funktionsaufrufe und Zeichen folgen Datentypen. Der Treiber-Manager ordnet Funktions Zeichenfolgen-Argumente und Zeichen folgen Daten gemäß den Anforderungen der Anwendung und des Treibers zu, von denen beide entweder Unicode-aktiviert oder ANSI-fähig sind. Diese beiden Bereiche werden ausführlich in den Abschnitten, in [Unicode-Funktions Argumenten](../../../odbc/reference/develop-app/unicode-function-arguments.md) und in [Unicode-Daten](../../../odbc/reference/develop-app/unicode-data.md)erläutert.  
  
 Der Treiber-Manager von ODBC 3,5 (oder höher) unterstützt die Verwendung eines Unicode-Treibers sowohl für eine Unicode-Anwendung als auch für eine ANSI-Anwendung. Außerdem wird die Verwendung eines ANSI-Treibers mit einer ANSI-Anwendung unterstützt. Der Treiber-Manager bietet eingeschränkte Unicode-zu-ANSI-Zuordnung für eine Unicode-Anwendung, die mit einem ANSI-Treiber arbeitet.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Unicode-Funktionsargumente](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Unicode-Daten](../../../odbc/reference/develop-app/unicode-data.md)
