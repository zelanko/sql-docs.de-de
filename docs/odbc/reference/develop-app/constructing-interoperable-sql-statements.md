---
title: Erstellen interoperabler SQL-Anweisungen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1eccdef63b7d06a456a07f5f1a9ccad987d2de29
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282514"
---
# <a name="constructing-interoperable-sql-statements"></a>Konstruieren von interoperablen SQL­-Anweisungen
Wie in den vorherigen Abschnitten erwähnt, sollten interoperable Anwendungen die ODBC SQL-Grammatik verwenden. Abgesehen von der Verwendung dieser Grammatik sind jedoch eine Reihe zusätzlicher Probleme mit interoperablen Anwendungen konfrontiert. Was macht eine Anwendung beispielsweise, wenn sie ein Feature verwenden möchte, z. B. äußere Verknüpfungen, das nicht von allen Datenquellen unterstützt wird?  
  
 An dieser Stelle muss der Anwendungsschreiber einige Entscheidungen darüber treffen, welche Sprachfeatures erforderlich und welche optional sind. In den meisten Fällen weigert sich die Anwendung einfach, mit diesem Treiber zu arbeiten, wenn ein bestimmter Treiber eine von der Anwendung benötigte Funktion nicht unterstützt. Wenn die Funktion jedoch optional ist, kann die Anwendung das Feature umgehen. Beispielsweise können die Teile der Schnittstelle deaktiviert werden, die es dem Benutzer ermöglichen, die Funktion zu verwenden.  
  
 Um zu bestimmen, welche Features unterstützt werden, rufen Anwendungen **SQLGetInfo** mit der Option SQL_SQL_CONFORMANCE auf. Die SQL-Konformitätsebene gibt der Anwendung eine umfassende Ansicht, welche SQL unterstützt wird. Um diese Ansicht zu verfeinern, ruft die Anwendung **SQLGetInfo** mit einer reihe anderer Optionen auf. Eine vollständige Liste dieser Optionen finden Sie in der [SQLGetInfo-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlgetinfo-function.md) Schließlich gibt **SQLGetTypeInfo** Informationen zu den von der Datenquelle unterstützten Datentypen zurück. In den folgenden Abschnitten werden eine Reihe möglicher Faktoren aufgeführt, auf die Anwendungen beim Erstellen interoperabler SQL-Anweisungen achten sollten.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Katalog- und Schemaverwendung](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [Katalogposition](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [Bezeichner in Anführungszeichen](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [Groß-/Kleinschreibung von Bezeichnern](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [Escapesequenzen](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [Literalpräfixe und -suffixe](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [Parametermarker in Prozeduraufrufen](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [DDL-Anweisungen](../../../odbc/reference/develop-app/ddl-statements.md)
