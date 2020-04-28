---
title: SQL-Typbezeichner | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299770"
---
# <a name="sql-type-identifiers"></a>SQL-Typenbezeichner
Jede Datenquelle definiert eigene SQL-Datentypen. In ODBC werden Typbezeichner definiert und die allgemeinen Eigenschaften der SQL-Datentypen beschrieben, die den einzelnen Typbezeichnern zugeordnet werden können. Es ist Treiber spezifisch, wie jeder Datentyp in der zugrunde liegenden Datenquelle einem SQL-Typbezeichner von ODBC zugeordnet wird.  
  
 Beispielsweise ist SQL_CHAR der Typbezeichner für eine Zeichenspalte mit fester Länge, normalerweise zwischen 1 und 254 Zeichen. Diese Merkmale entsprechen dem Char-Datentyp, der in vielen SQL-Datenquellen gefunden wurde. Wenn also eine Anwendung erkennt, dass der Typbezeichner für eine Spalte SQL_CHAR ist, kann Sie davon ausgehen, dass Sie wahrscheinlich mit einer char-Spalte beschäftigt ist. Es sollte jedoch immer noch die Byte Länge der Spalte überprüft werden, bevor davon ausgegangen wird, dass Sie zwischen 1 und 254 Zeichen lang ist. der Treiber für eine nicht-SQL-Datenquelle kann z. b. eine Zeichenspalte mit fester Länge von 500 Zeichen SQL_CHAR oder SQL_LONGVARCHAR zuordnen, da keines von beiden eine genaue Entsprechung ist.  
  
 ODBC definiert eine Vielzahl von SQL-typbezeichgern. Allerdings muss der Treiber nicht alle diese Bezeichner verwenden. Stattdessen werden nur die Bezeichner verwendet, die benötigt werden, um die von der zugrunde liegenden Datenquelle unterstützten SQL-Datentypen verfügbar zu machen. Wenn die zugrunde liegende Datenquelle SQL-Datentypen unterstützt, denen kein Typbezeichner entspricht, kann der Treiber zusätzliche Typbezeichner definieren. Weitere Informationen finden Sie unter [Treiber spezifische Datentypen, deskriptortypen, Informationstypen, Diagnose Typen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Eine umfassende Beschreibung der SQL-Typbezeichner finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md) in Anhang D: Datentypen.
