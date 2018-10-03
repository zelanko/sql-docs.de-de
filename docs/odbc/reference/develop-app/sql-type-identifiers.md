---
title: SQL-Typenbezeichner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- SQL data types [ODBC], identifiers
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: 22f6793b-2f43-4281-b35a-28f48e504dd8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1763ee0cd8c5bc2017160de44b9c047781649eba
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740148"
---
# <a name="sql-type-identifiers"></a>SQL-Typenbezeichner
Jede Datenquelle definiert eine eigene SQL-Datentypen. ODBC definiert Typ-IDs und beschreibt die allgemeinen Eigenschaften der SQL-Datentypen, die jeden Typ-ID zugeordnet werden können. Es ist eine treiberspezifische wie jeden Datentyp in der zugrunde liegenden Datenquelle eine SQL-Typ-ID von ODBC zugeordnet wird.  
  
 SQL_CHAR ist beispielsweise der Typ-ID für eine Spalte mit Zeichen fester Länge, in der Regel zwischen 1 und 254 Zeichen. Diese Eigenschaften entsprechen der CHAR-Datentyp, der in vielen SQL-Datenquellen gefunden. Also, wenn eine Anwendung ermittelt, dass der Typ-ID für eine Spalte SQL_CHAR ist, können sie davon ausgehen, dass es wahrscheinlich mit einer CHAR-Spalte zu verarbeiten. Jedoch sollten sie überprüfen, dass die Bytelänge der Spalte vor dem vorausgesetzt es zwischen 1 und 254 Zeichen ist; der Treiber für eine nicht-SQL-Datenquelle, z. B. kann eine Spalte mit fester Länge Zeichen von 500 Zeichen SQL_CHAR oder SQL_LONGVARCHAR, zugeordnet, da keine der beiden eine genaue Übereinstimmung.  
  
 ODBC definiert eine Vielzahl von SQL-Typ-IDs. Der Treiber ist jedoch nicht erforderlich, können alle diese Bezeichner verwenden. Stattdessen wird nur diese Bezeichner, die die SQL-Datentypen unterstützt verfügbar machen muss von der zugrunde liegenden Datenquelle verwendet. Wenn die zugrunde liegenden Datenquelle unterstützt die SQL-Datentypen zu welche kein Typ-ID entspricht, der Treiber kann zusätzliche Typ-IDs definieren. Weitere Informationen finden Sie unter [treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Eine vollständige Beschreibung der SQL-Typ-IDs, finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D:-Datentypen.
