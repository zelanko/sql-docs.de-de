---
description: DDL-Anweisungen
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 395abe3eed64f37c000ecff6f0b68a6e0cb1d076
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424732"
---
# <a name="ddl-statements"></a>DDL-Anweisungen
DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) unterscheiden sich stark von DBMSs. ODBC SQL definiert Anweisungen für die gängigsten Daten Definitions Vorgänge: Erstellen und Löschen von Tabellen, Indizes und Sichten. Ändern von Tabellen; und erteilen und widerrufen Berechtigungen. Alle anderen DDL-Anweisungen sind Datenquellen spezifisch. Daher können interoperable Anwendungen einige Daten Definitions Vorgänge nicht ausführen. Im Allgemeinen handelt es sich hierbei nicht um ein Problem, da solche Vorgänge in der Regel sehr DBMS-spezifisch sind und sich am besten an die proprietäre Software für die Datenbankverwaltung befinden, die mit den meisten DBMSs oder dem Installationsprogramm des Treibers ausgeliefert wurde.  
  
 Ein weiteres Problem bei der Datendefinition besteht darin, dass sich die Datentyp Namen bei DBMSs enorm unterscheiden. Anstatt standardmäßige Datentyp Namen zu definieren und Treiber zu erzwingen, um Sie in DBMS-spezifische Namen zu konvertieren, bietet **SQLGetTypeInfo** eine Möglichkeit für Anwendungen, DBMS-spezifische Datentyp Namen zu ermitteln. Interoperable Anwendungen sollten diese Namen in SQL-Anweisungen verwenden, um Tabellen zu erstellen und zu ändern. die Namen, die in [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)und [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md)aufgeführt sind, sind nur Beispiele.
