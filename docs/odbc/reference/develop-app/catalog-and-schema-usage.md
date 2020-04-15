---
title: Katalog- und Schemaverwendung | Microsoft Docs
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
ms.openlocfilehash: 245bd007f070a94689283830ba7a1362e31353e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306251"
---
# <a name="catalog-and-schema-usage"></a>Katalog- und Schemaverwendung
Datenquellen unterstützen Katalog- und Schemanamen nicht unbedingt als Objektnamensbezeichner in allen SQL-Anweisungen. Datenquellen unterstützen möglicherweise Katalog- und Schemanamen in einer oder mehreren der folgenden Klassen von SQL-Anweisungen: DML-Anweisungen (Data Manipulation Language), Prozeduraufrufe, Tabellendefinitionsanweisungen, Indexdefinitionsanweisungen und Berechtigungsdefinitionsanweisungen. Um die Klassen von SQL-Anweisungen zu bestimmen, in denen Katalog- und Schemanamen verwendet werden können, ruft eine Anwendung **SQLGetInfo** mit den SQL_CATALOG_USAGE und SQL_SCHEMA_USAGE Optionen auf.
