---
title: Erstellen von interoperablen SQL-Anweisungen | Microsoft-Dokumentation
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
ms.openlocfilehash: 87ad7b8b36c80d86e0c3ac0335dd6f348a30c7bc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002243"
---
# <a name="constructing-interoperable-sql-statements"></a>Konstruieren von interoperablen SQL­-Anweisungen
Wie in den vorherigen Abschnitten erwähnt, sollten interoperable Anwendungen die ODBC-SQL-Grammatik verwenden. Abgesehen von der Verwendung dieser Grammatik werden von interoperablen Anwendungen jedoch einige zusätzliche Probleme verursacht. Was bewirkt eine Anwendung beispielsweise, wenn Sie eine Funktion verwenden möchten, z. b. äußere Joins, die nicht von allen Datenquellen unterstützt wird?  
  
 An diesem Punkt muss der anwendungswriter einige Entscheidungen darüber treffen, welche sprach Features erforderlich und welche optional sind. In den meisten Fällen kann die Anwendung nur mit diesem Treiber ausgeführt werden, wenn ein bestimmter Treiber keine von der Anwendung benötigte Funktion unterstützt. Wenn das Feature jedoch optional ist, kann die Anwendung das Feature umgehen. Beispielsweise können diese Teile der Schnittstelle deaktiviert werden, die dem Benutzer die Verwendung der Funktion ermöglichen.  
  
 Um zu ermitteln, welche Features unterstützt werden, beginnen Anwendungen mit dem Aufruf von **SQLGetInfo** mit der Option SQL_SQL_CONFORMANCE. Die SQL-Kompatibilitäts Ebene gibt der Anwendung einen allgemeinen Überblick darüber, welche SQL unterstützt wird. Um diese Ansicht zu verfeinern, ruft die Anwendung **SQLGetInfo** mit einer beliebigen Anzahl anderer Optionen auf. Eine umfassende Liste dieser Optionen finden Sie in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion. Schließlich gibt **SQLGetTypeInfo** Informationen zu den Datentypen zurück, die von der Datenquelle unterstützt werden. In den folgenden Abschnitten werden einige mögliche Faktoren aufgelistet, die Anwendungen beim Erstellen interoperabel SQL-Anweisungen beobachten sollten.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Katalog- und Schemaverwendung](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [Katalogposition](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [Bezeichner in Anführungszeichen](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [Groß-/Kleinschreibung von Bezeichnern](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [Escapesequenzen](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [Literalpräfixe und -suffixe](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [Parametermarker in Prozeduraufrufen](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [DDL-Anweisungen](../../../odbc/reference/develop-app/ddl-statements.md)
