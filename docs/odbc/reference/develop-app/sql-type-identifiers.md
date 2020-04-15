---
title: SQL-Typbezeichner | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 95bf46844e9ed91aac1ec6cb93a298995f0901d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299770"
---
# <a name="sql-type-identifiers"></a>SQL-Typenbezeichner
Jede Datenquelle definiert ihre eigenen SQL-Datentypen. ODBC definiert Typbezeichner und beschreibt die allgemeinen Merkmale der SQL-Datentypen, die jedem Typbezeichner zugeordnet werden können. Es ist treiberspezifisch, wie jeder Datentyp in der zugrunde liegenden Datenquelle einem SQL-Typbezeichner von ODBC zugeordnet wird.  
  
 SQL_CHAR ist z. B. der Typbezeichner für eine Zeichenspalte mit einer festen Länge, in der Regel zwischen 1 und 254 Zeichen. Diese Merkmale entsprechen dem CHAR-Datentyp, der in vielen SQL-Datenquellen zu finden ist. Wenn also eine Anwendung feststellt, dass der Typbezeichner für eine Spalte SQL_CHAR ist, kann sie davon ausgehen, dass es sich wahrscheinlich um eine CHAR-Spalte handelt. Es sollte jedoch immer noch die Bytelänge der Spalte überprüfen, bevor angenommen wird, dass sie zwischen 1 und 254 Zeichen liegt. Der Treiber für eine Nicht-SQL-Datenquelle kann z. B. eine Zeichenspalte mit fester Länge von 500 Zeichen SQL_CHAR oder SQL_LONGVARCHAR zuordnen, da keines der beiden Zeichen genau übereinstimmt.  
  
 ODBC definiert eine Vielzahl von SQL-Typbezeichnern. Der Treiber muss jedoch nicht alle diese Bezeichner verwenden. Stattdessen werden nur die Bezeichner verwendet, die erforderlich sind, um die SQL-Datentypen verfügbar zu machen, die von der zugrunde liegenden Datenquelle unterstützt werden. Wenn die zugrunde liegende Datenquelle SQL-Datentypen unterstützt, denen kein Typbezeichner entspricht, kann der Treiber zusätzliche Typbezeichner definieren. Weitere Informationen finden Sie unter [Treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Eine vollständige Beschreibung von SQL-Typbezeichnern finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D: Datentypen.
