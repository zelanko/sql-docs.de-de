---
title: Kompatibilität mit Desktop-Datenbanktreibern | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89eea7ab112eaefdc73c7cbc72ee3555797c7efd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303521"
---
# <a name="desktop-database-driver-compatibility"></a>Kompatibilität von Desktop-Datenbanktreibern
Unicode ist eine Methode der Softwarezeichencodierung, die alle Zeichen mit einer festen Breite von zwei Bytes behandelt. Diese Methode wird als Alternative zur Windows ANSI-Zeichencodierung verwendet, die, da sie Zeichen in einem Byte darstellt, auf 256 Zeichen beschränkt ist. Da Unicode mehr als 65.000 Zeichen darstellen kann, werden viele Sprachen berücksichtigt, deren Zeichen in der ANSI-Codierung nicht dargestellt werden.  
  
 Der ODBC 3.5 (oder höher) Treiber-Manager ist Unicode-fähig. Dies betrifft zwei Hauptbereiche: Funktionsaufrufe und Zeichenfolgendatentypen. Der Treiber-Manager ordnet Funktionszeichenfolgenargumente und Zeichenfolgendaten zu, die von der Anwendung und dem Treiber benötigt werden, die beide entweder Unicode-fähig oder ANSI-aktiviert sein können.  
  
 Der ODBC 3.5 (oder höher) Treiber-Manager unterstützt die Verwendung eines Unicode-Treibers mit einer Unicode-Anwendung und einer ANSI-Anwendung. Es unterstützt auch die Verwendung eines ANSI-Treibers mit einer ANSI-Anwendung. Der Treiber-Manager bietet eine eingeschränkte Unicode-zu-ANSI-Zuordnung für eine Unicode-Anwendung, die mit einem ANSI-Treiber arbeitet. Dies ermöglicht den Zugriff auf die Jet 3.5-Datenbanken und die Unterstützung aller vorhandenen ISAM-Dateitypen.  
  
 Wenn eine ANSI-Anwendung den ODBC Desktop Database Driver 4.0 verwendet und auf Microsoft Access 4.0 oder höher zugreift, macht der Treiber den Datentyp als SQL_CHAR, SQL_VARCHAR oder SQL_LONGVARCHAR verfügbar, obwohl Jet 4.0 die breite Version unterstützt. Ältere Versionen von Jet unterstützen SQL_WCHAR, SQL_WVARCHAR und SQL_WLONGVARCHAR nicht. Diese Einschränkung gilt auch in Fällen, in denen die alten Formate mit der Jet 4.0 Database Engine verwendet werden.  
  
 Weitere Informationen zu Unicode-Problemen mit ODBC finden Sie unter [Unicode](../../odbc/reference/develop-app/unicode.md) unter Programmierüberlegungen.
