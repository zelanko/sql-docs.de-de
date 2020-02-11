---
title: Reservierte Schlüsselwörter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC function call reserved words [ODBC]
- reserved keywords [ODBC]
ms.assetid: 8eeede59-a828-44bf-866c-1ca9a77a2c5e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a89a24ddbbe14938824819e24fd9112597168507
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057211"
---
# <a name="reserved-keywords"></a>Reservierte Schlüsselwörter
Die folgenden Wörter sind für die Verwendung in ODBC-Funktionsaufrufen reserviert. Diese Wörter schränken die minimale SQL-Grammatik nicht ein. Um jedoch die Kompatibilität mit Treibern sicherzustellen, die die Kern-SQL-Grammatik unterstützen, sollten Anwendungen die Verwendung dieser Schlüsselwörter vermeiden. Der Wert "#**define** " SQL_ODBC_KEYWORDS enthält eine durch Trennzeichen getrennte Liste dieser Schlüsselwörter.  
  
|||  
|-|-|  
|ABSOLUTE|IS|  
|AKTION|ISOLATION|  
|ADA|JOIN|  
|ADD|KEY|  
|ALL|LANGUAGE|  
|ALLOCATE|LAST|  
|ALTER|LEADING|  
|AND|LEFT|  
|ANY|LEVEL|  
|ARE|LIKE|  
|AS|LOCAL|  
|ASC|LOWER|  
|ASSERTION|MATCH|  
|AT|MAX|  
|AUTHORIZATION|MIN|  
|DURCHSCHN.|MINUTE|  
|BEGIN|MODULE|  
|BETWEEN|MONTH|  
|BIT|NAMES|  
|BIT_LENGTH|NATIONAL|  
|BOTH|NATURAL|  
|BY|NCHAR|  
|CASCADE|NEXT|  
|CASCADED|NO|  
|CASE|Keine|  
|CAST|NICHT|  
|CATALOG|NULL|  
|CHAR|NULLIF|  
|CHAR_LENGTH|NUMERIC|  
|CHARACTER|OCTET_LENGTH|  
|CHARACTER_LENGTH|OF|  
|CHECK|EIN|  
|CLOSE|ONLY|  
|COALESCE|OPEN|  
|COLLATE|OPTION|  
|COLLATION|oder|  
|COLUMN|ORDER|  
|COMMIT|OUTER|  
|CONNECT|OUTPUT|  
|CONNECTION|Lappen|  
|CONSTRAINT|PAD|  
|EINSCHRÄNKUNGEN|PARTIAL|  
|CONTINUE|PASCAL|  
|CONVERT|Gebracht|  
|CORRESPONDING|PRECISION|  
|COUNT|PREPARE|  
|CREATE|PRESERVE|  
|CROSS|PRIMARY|  
|CURRENT|PRIOR|  
|CURRENT_DATE|PRIVILEGES|  
|CURRENT_TIME|PROCEDURE|  
|CURRENT_TIMESTAMP|PUBLIC|  
|CURRENT_USER|READ|  
|CURSOR|real|  
|DATE|REFERENCES|  
|DAY|RELATIVE|  
|DEALLOCATE|RESTRICT|  
|DEC|REVOKE|  
|DECIMAL|RIGHT|  
|DECLARE|ROLLBACK|  
|DEFAULT|ROWS|  
|DEFERRABLE|SCHEMA|  
|DEFERRED|SCROLL|  
|Delete|SECOND|  
|DESC|SECTION|  
|DESCRIBE|SELECT|  
|DESCRIPTOR|SESSION|  
|DIAGNOSTICS|SESSION_USER|  
|DISCONNECT|SET|  
|DISTINCT|GRÖSSE|  
|DOMAIN|SMALLINT|  
|Double|SOME|  
|DROP|SPACE|  
|ELSE|SQL|  
|END|SQLCA|  
|END-EXEC|SQLCODE|  
|ESCAPE|SQLError|  
|EXCEPT|SQLSTATE|  
|EXCEPTION|SQLWARNING|  
|EXEC|SUBSTRING|  
|Führen Sie|SUM|  
|EXISTS|SYSTEM_USER|  
|EXTERNAL|TABLE|  
|EXTRACT|TEMPORARY|  
|FALSE|THEN|  
|FETCH|TIME|  
|FIRST|timestamp|  
|GLEITKOMMAZAHL|TIMEZONE_HOUR|  
|FOR|TIMEZONE_MINUTE|  
|FOREIGN|TO|  
|FORTRAN|TRAILING|  
|FOUND|TRANSACTION|  
|FROM|TRANSLATE|  
|FULL|TRANSLATION|  
|GET|TRIM|  
|GLOBAL|TRUE|  
|GO|UNION|  
|GOTO|UNIQUE|  
|GRANT|UNKNOWN|  
|GROUP|UPDATE|  
|HAVING|UPPER|  
|HOUR|USAGE|  
|IDENTITÄT|USER|  
|IMMEDIATE|USING|  
|IN|VALUE|  
|INCLUDE|VALUES|  
|INDEX|VARCHAR|  
|INDICATOR|VARYING|  
|INITIALLY|VIEW|  
|INNER|WHEN|  
|INPUT|WHENEVER|  
|INSENSITIVE|WHERE|  
|INSERT|WITH|  
|INT|WORK|  
|INTEGER|WRITE|  
|INTERSECT|YEAR|  
|INTERVAL|ZONE|  
|INTO||
