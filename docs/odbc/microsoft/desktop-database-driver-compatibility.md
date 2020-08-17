---
description: Kompatibilität von Desktop-Datenbanktreibern
title: Kompatibilität der Desktop-Datenbanktreiber | Microsoft-Dokumentation
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
ms.openlocfilehash: 6b15ec35a01b61eef401f217733917a80bbe32b4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340776"
---
# <a name="desktop-database-driver-compatibility"></a>Kompatibilität von Desktop-Datenbanktreibern
Unicode ist eine Methode der Software Zeichencodierung, die alle Zeichen als eine festgelegte Breite von zwei Bytes behandelt. Diese Methode wird als Alternative zur Windows-ANSI-Zeichencodierung verwendet, die auf 256 Zeichen beschränkt ist, da Sie Zeichen in einem Byte darstellt. Da Unicode mehr als 65.000 Zeichen darstellen kann, werden viele Sprachen untersucht, deren Zeichen nicht in ANSI-Codierung dargestellt werden.  
  
 Der Treiber-Manager für ODBC 3,5 (oder höher) ist Unicode-aktiviert. Dies wirkt sich auf zwei Hauptbereiche aus: Funktionsaufrufe und Zeichen folgen Datentypen. Der Treiber-Manager ordnet Funktions Zeichenfolgen-Argumente und Zeichen folgen Daten gemäß den Anforderungen der Anwendung und des Treibers zu, von denen beide entweder Unicode-aktiviert oder ANSI-fähig sind.  
  
 Der Treiber-Manager von ODBC 3,5 (oder höher) unterstützt die Verwendung eines Unicode-Treibers sowohl für eine Unicode-Anwendung als auch für eine ANSI-Anwendung. Außerdem wird die Verwendung eines ANSI-Treibers mit einer ANSI-Anwendung unterstützt. Der Treiber-Manager bietet eingeschränkte Unicode-zu-ANSI-Zuordnung für eine Unicode-Anwendung, die mit einem ANSI-Treiber arbeitet. Dadurch wird der Zugriff auf die Jet 3,5-Datenbanken und die Unterstützung aller vorhandenen ISAM-Dateitypen ermöglicht.  
  
 Wenn eine ANSI-Anwendung den ODBC Desktop-Datenbanktreiber 4,0 verwendet und auf Microsoft Access 4,0 oder höher zugreift, macht der Treiber den Datentyp als SQL_CHAR, SQL_VARCHAR oder SQL_LONGVARCHAR verfügbar, obwohl Jet 4,0 die Wide-Version unterstützt. Ältere Versionen von Jet unterstützen SQL_WCHAR, SQL_WVARCHAR und SQL_WLONGVARCHAR nicht. Diese Einschränkung gilt auch für Fälle, in denen die alten Formate mit dem Jet 4,0-Datenbank-Engine verwendet werden.  
  
 Weitere Informationen zu Unicode-Problemen mit ODBC finden Sie unter Überlegungen zu [Unicode](../../odbc/reference/develop-app/unicode.md) in der Programmierung.
