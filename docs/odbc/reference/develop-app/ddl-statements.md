---
title: DDL-Anweisungen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cae06efe6dd11e651e8553fa5c1004c2fa145478
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302991"
---
# <a name="ddl-statements"></a>DDL-Anweisungen
DDL-Anweisungen (Data Definition Language) unterscheiden sich erheblich zwischen DBMS. ODBC SQL definiert Anweisungen für die gängigsten Datendefinitionsvorgänge: Erstellen und Löschen von Tabellen, Indizes und Ansichten; Ändern von Tabellen; und die Erteilung und Aufhebung von Privilegien. Alle anderen DDL-Anweisungen sind datenquellenspezifisch. Daher können interoperable Anwendungen einige Datendefinitionsvorgänge nicht ausführen. Im Allgemeinen ist dies kein Problem, da solche Vorgänge in der Regel sehr DBMS-spezifisch sind und am besten der proprietären Datenbankverwaltungssoftware überlassen werden, die mit den meisten DBMS oder dem Setup-Programm ausgeliefert wird, das mit dem Treiber ausgeliefert wird.  
  
 Ein weiteres Problem bei der Datendefinition besteht darin, dass die Namen des Datentyps zwischen DEN DBMS sehr unterschiedlich sind. SqlGetTypeInfo definiert keine Standarddatentypnamen und zwingt Treiber dazu, sie in DBMS-spezifische Namen zu konvertieren. **SQLGetTypeInfo** bietet Anwendungen die Möglichkeit, DBMS-spezifische Datentypnamen zu ermitteln. Interoperable Anwendungen sollten diese Namen in SQL-Anweisungen verwenden, um Tabellen zu erstellen und zu ändern. Die in [Anhang C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)und [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md)aufgeführten Namen sind nur Beispiele.
