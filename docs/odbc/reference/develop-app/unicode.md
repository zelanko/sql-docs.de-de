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
manager: craigg
ms.openlocfilehash: 1e6201b83b909573476b043cdb1a10543f894def
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62632547"
---
# <a name="unicode"></a>Unicode
Unicode definiert die Codierung für Zeichen in vielen Sprachen.  
  
 Weitere Informationen zu den Unicode-Standard, finden Sie unter [das Unicode Consortium](https://www.unicode.org).  
  
 Unicode definiert einen Satz von universellen Zeichennamen an. Eine Windows-ANSI-Codepage definiert einen Zeichensatz, der Zeichen für eine Sprache in der Regel enthält. Möglicherweise schwieriger, eine Anwendung schreiben, die erforderlich ist, um unterschiedliche Codepages verwenden.  
  
 Unicode ist eine Codepage nicht erforderlich. Jede Codepunkt ist ein einzelnes Zeichen in einer Sprache zugeordnet.  
  
 Derzeit ist die einzige Unicode-Codierung, ODBC unterstützt UCS-2, die eine 16-Bit-Ganzzahl (fester Länge) zur Darstellung eines Zeichens verwendet. Unicode kann Anwendungen in verschiedenen Sprachen arbeiten.  
  
 Der ODBC 3.5 (oder höher)-Treiber-Manager ist das Unicode-aktiviert. Dies wirkt sich auf zwei wichtigen Bereichen: Funktionsaufrufe und string-Datentypen. Die Zeichenfolgenargumente-Funktion "Maps"-Treiber-Manager und die Zeichenfolgendaten nach Bedarf von der Anwendung und Treiber, können beide entweder Unicode oder ANSI-aktiviert sein. Diese beiden Bereiche werden ausführlich in den Abschnitten [Unicode-Funktionsargumente](../../../odbc/reference/develop-app/unicode-function-arguments.md) und [Unicode-Daten](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Der ODBC 3.5 (oder höher)-Treiber-Manager unterstützt die Verwendung eines Unicode-Treibers mit einer Unicode-Anwendung und eine ANSI-Anwendung. Es unterstützt auch die Verwendung von einem ANSI-Treiber mit einer ANSI-Anwendung. Der Treiber-Manager bietet eingeschränkte Unicode-in-ANSI-Zuordnung für eine Unicode-Anwendung, die mit einem ANSI-Treiber verwenden.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Unicode-Funktionsargumente](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Unicode-Daten](../../../odbc/reference/develop-app/unicode-data.md)
