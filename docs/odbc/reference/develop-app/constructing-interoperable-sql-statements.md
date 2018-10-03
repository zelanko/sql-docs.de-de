---
title: Erstellen von interoperablen SQL­Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], constructing statements
ms.assetid: dee6f7e2-bcc4-4c74-8c7c-12aeda8a90eb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc8072a6d7291a546f0f12256aa4b336da037a83
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809168"
---
# <a name="constructing-interoperable-sql-statements"></a>Konstruieren von interoperablen SQL­-Anweisungen
Wie in den vorherigen Abschnitten erwähnt, sollten interoperable Anwendungen ausführen können, die ODBC-SQL-Grammatik verwenden. Eine Reihe von zusätzlichen Problemen werden jedoch über die Verwendung dieser Grammatik von interoperablen Anwendungen konfrontiert. Was tun z. B. eine Anwendung, um eine Funktion, z. B. outer Join verwenden, die von allen Datenquellen nicht unterstützt wird?  
  
 An diesem Punkt muss der Autor der Anwendung Entscheidungen zur die Language-Funktionen erforderlich sind und welche optional sind. In den meisten Fällen Wenn Sie ein bestimmter Treiber eine Funktion, die erforderlich sind, von der Anwendung nicht unterstützt drosselungszeitraums verweigert die Anwendung einfach mit diesen Treiber ausführen. Wenn die Funktion optional ist, kann die Anwendung jedoch rund um die Funktion funktioniert. Es kann z. B. die Teile der Schnittstelle deaktivieren, mit die den Benutzer das Feature verwenden zu können.  
  
 Um zu bestimmen, welche Funktionen unterstützt werden, Anwendungen, die durch den Aufruf starten **SQLGetInfo** mit der Option SQL_SQL_CONFORMANCE. Der SQL-Konformitätsgrad ermöglicht es der Anwendung einen umfassenden Einblick, von dem SQL unterstützt wird. Diese Ansicht, die Anwendung ruft optimieren **SQLGetInfo** mit eine beliebige Anzahl anderer Optionen. Eine vollständige Liste dieser Optionen, finden Sie unter den [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) funktionsbeschreibung. Zum Schluss **SQLGetTypeInfo** gibt Informationen zu den Datentypen, die von der Datenquelle unterstützten Daten zurück. Den folgenden Abschnitten werden einer Reihe von möglichen Faktoren, denen Anwendungen in ziehen beim Erstellen von interoperabler SQL-Anweisungen Betracht sollten.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Katalog- und Schemaverwendung](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [Katalogposition](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [Bezeichner in Anführungszeichen](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [Groß-/Kleinschreibung von Bezeichnern](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [Escapesequenzen](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [Literalpräfixe und -suffixe](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [Parametermarkierungen in Prozeduraufrufen](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [DDL-Anweisungen](../../../odbc/reference/develop-app/ddl-statements.md)
