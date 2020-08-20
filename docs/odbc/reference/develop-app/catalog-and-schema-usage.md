---
description: Katalog- und Schemaverwendung
title: Katalog-und Schema Verwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2506810c477e9d75e1d3b38f38185d22edf9d010
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494690"
---
# <a name="catalog-and-schema-usage"></a>Katalog- und Schemaverwendung
Datenquellen unterstützen nicht notwendigerweise Katalog-und Schema Namen als Objektnamen Bezeichner in allen SQL-Anweisungen. Datenquellen unterstützen möglicherweise Katalog-und Schema Namen in einer oder mehreren der folgenden Klassen von SQL-Anweisungen: DML-Anweisungen (Data Manipulation Language, Daten Bearbeitungs Sprache), Prozedur Aufrufe, Tabellen Definitions Anweisungen, Index Definitions Anweisungen und Berechtigungs Definitions Anweisungen. Zum Ermitteln der Klassen von SQL-Anweisungen, in denen Katalog-und Schema Namen verwendet werden können, ruft eine Anwendung **SQLGetInfo** mit den Optionen SQL_CATALOG_USAGE und SQL_SCHEMA_USAGE auf.
