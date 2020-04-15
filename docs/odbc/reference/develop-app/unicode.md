---
title: Unicode | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9824e76cebabb6f5f84505292801a0094e359f0f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302445"
---
# <a name="unicode"></a>Unicode
Unicode definiert die Codierung für Zeichen in vielen Sprachen.  
  
 Weitere Informationen zum Unicode-Standard finden Sie unter [Das Unicode-Konsortium](https://www.unicode.org).  
  
 Unicode definiert einen universellen Zeichensatz. Eine Windows ANSI-Codepage definiert einen Zeichensatz, der in der Regel Zeichen für eine Sprache enthält. Es kann schwieriger sein, eine Anwendung zu schreiben, die für die Verwendung verschiedener Codepages erforderlich ist.  
  
 Unicode erfordert keine Codepage. Jeder Codepunkt wird einem einzelnen Zeichen in einer Sprache zugeordnet.  
  
 Derzeit ist die einzige Unicode-Codierung, die ODBC unterstützt, UCS-2, die eine 16-Bit-Ganzzahl (feste Länge) verwendet, um ein Zeichen darzustellen. Unicode ermöglicht es Anwendungen, in verschiedenen Sprachen zu arbeiten.  
  
 Der ODBC 3.5 (oder höher) Treiber-Manager ist Unicode-fähig. Dies betrifft zwei Hauptbereiche: Funktionsaufrufe und Zeichenfolgendatentypen. Der Treiber-Manager ordnet Funktionszeichenfolgenargumente und Zeichenfolgendaten zu, die von der Anwendung und dem Treiber benötigt werden, die beide entweder Unicode-fähig oder ANSI-aktiviert sein können. Diese beiden Bereiche werden in den Abschnitten [Unicode Function Arguments](../../../odbc/reference/develop-app/unicode-function-arguments.md) und [Unicode Data](../../../odbc/reference/develop-app/unicode-data.md)ausführlich erläutert.  
  
 Der ODBC 3.5 (oder höher) Treiber-Manager unterstützt die Verwendung eines Unicode-Treibers sowohl mit einer Unicode-Anwendung als auch einer ANSI-Anwendung. Es unterstützt auch die Verwendung eines ANSI-Treibers mit einer ANSI-Anwendung. Der Treiber-Manager bietet eine eingeschränkte Unicode-zu-ANSI-Zuordnung für eine Unicode-Anwendung, die mit einem ANSI-Treiber arbeitet.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Unicode-Funktionsargumente](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Unicode-Daten](../../../odbc/reference/develop-app/unicode-data.md)
