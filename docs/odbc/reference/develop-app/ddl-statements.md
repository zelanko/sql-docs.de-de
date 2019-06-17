---
title: DDL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9100405c91387faa66b714a94b8259167ae31899
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63267662"
---
# <a name="ddl-statements"></a>DDL-Anweisungen
Anweisungen der Data Definition Language (DDL) variieren erheblich von DBMS-Systeme. ODBC-SQL definiert, Anweisungen für die am häufigsten verwendeten Data Definition-Vorgänge: Erstellen und Löschen von Tabellen, Indizes und Sichten, Ändern von Tabellen; erteilen und Widerrufen von Berechtigungen. Alle anderen DDL-Anweisungen handelt es sich um Daten datenquellenspezifische. Daher können nicht interoperable Anwendungen ausführen können einige Vorgänge ausführen. Im Allgemeinen, dies ist kein Problem, da solche Vorgänge sind tendenziell hoch DBMS-spezifische und sich am besten eignen Links der proprietäre Software für die Verwaltung mit den meisten DBMS, oder das Setup-Programm mit dem Treiber.  
  
 Ein weiteres Problem in der Datendefinition ist dieses Datentyps variieren Namen enorm von DBMS-Systeme. Anstatt standard Datentypnamen definieren und erzwingen Treiber in den Namen des DBMS-spezifische, umwandeln, **SQLGetTypeInfo** bietet eine Möglichkeit für Anwendungen, Typnamen für DBMS-spezifische Daten zu ermitteln. Interoperable Anwendungen ausführen können soll, verwenden diese Namen in der SQL-Anweisungen zum Erstellen und Ändern von Tabellen wurden; die Namen in [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), und [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md), sind nur Beispiele.
