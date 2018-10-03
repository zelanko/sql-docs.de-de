---
title: Desktop-Treiber-Datenbankkompatibilität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], Unicode
- Unicode [ODBC], desktop database drivers
- ODBC desktop database drivers [ODBC], Unicode
- backward compatibility [ODBC], Unicode
- desktop database drivers [ODBC], Unicode
- Jet-based ODBC drivers [ODBC], Unicode
ms.assetid: dd695638-1a0b-4e27-8a6a-9510ebb5a5ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d081d53458ec59eb2ac9f05c5c1d47d6991b5010
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647168"
---
# <a name="desktop-database-driver-compatibility"></a>Kompatibilität von Desktop-Datenbanktreibern
Unicode ist, dass eine Methode zur Software zeichencodierung, die alle Zeichen behandelt, als mit einer festen Breite von zwei Bytes. Diese Methode wird als Alternative zur Windows-ANSI-zeichencodierung, verwendet die da sie Zeichen in ein Byte, darstellen, auf 256 Zeichen beschränkt ist. Da Unicode über 65.000 Zeichen darstellen kann, ermöglicht es vielen Sprachen, deren Zeichen werden nicht dargestellt, in ANSI-Codierung.  
  
 Der ODBC 3.5 (oder höher)-Treiber-Manager ist das Unicode-aktiviert. Dies wirkt sich auf zwei wichtigen Bereichen: Funktionsaufrufe und string-Datentypen. Die Zeichenfolgenargumente-Funktion "Maps"-Treiber-Manager und die Zeichenfolgendaten nach Bedarf von der Anwendung und Treiber, können beide entweder Unicode oder ANSI-aktiviert sein.  
  
 Der ODBC 3.5 (oder höher)-Treiber-Manager unterstützt die Verwendung eines Unicode-Treibers mit einer Unicode-Anwendung und eine ANSI-Anwendung. Es unterstützt auch die Verwendung von einem ANSI-Treiber mit einer ANSI-Anwendung. Der Treiber-Manager bietet eingeschränkte Unicode-in-ANSI-Zuordnung für eine Unicode-Anwendung, die mit einem ANSI-Treiber verwenden. Dies ermöglicht den Zugriff auf die Jet-3.5-Datenbanken und die Unterstützung für alle vorhandenen ISAM-Dateitypen.  
  
 Wenn eine ANSI-Anwendung verwendet den ODBC-Desktop-Datenbank-Treiber 4.0 und greift auf Microsoft Access 4.0 oder höher der Treiber stellt den Datentyp als SQL_CHAR, SQL_VARCHAR oder SQL_LONGVARCHAR, obwohl Jet 4.0 die Breite Version unterstützt. Ältere Versionen von Jet, unterstützen keine SQL_WCHAR, SQL_WVARCHAR und SQL_WLONGVARCHAR. Diese Einschränkung gilt auch in Fällen, in denen die alte Formate mit der Jet 4.0-Datenbank-Engine verwendet werden.  
  
 Weitere Informationen zu Unicode-Probleme mithilfe von ODBC, finden Sie unter [Unicode](../../odbc/reference/develop-app/unicode.md) in Überlegungen zur Programmierung.
