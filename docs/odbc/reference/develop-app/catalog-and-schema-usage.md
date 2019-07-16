---
title: Katalog- und Schemaverwendung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4e10460df120451502d798376453d69d111051ec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064416"
---
# <a name="catalog-and-schema-usage"></a>Katalog- und Schemaverwendung
Datenquellen unterstützen nicht unbedingt Katalog-und Schemanamen als Name der Objektbezeichner in allen SQL-Anweisungen. Datenquellen können Katalog-und Schemanamen in einer oder mehreren der folgenden Klassen von SQL-Anweisungen unterstützen: Data Manipulation Language (DML)-Anweisungen, Prozeduraufrufe, datendefinitionsanweisungen für die Tabelle, Index-datendefinitionsanweisungen und datendefinitionsanweisungen Berechtigungen. Um die Klassen der SQL-Anweisungen zu ermitteln, in der Katalog und Schema Namen verwendet werden können, eine Anwendung ruft **SQLGetInfo** mit den Optionen SQL_CATALOG_USAGE und SQL_SCHEMA_USAGE.
