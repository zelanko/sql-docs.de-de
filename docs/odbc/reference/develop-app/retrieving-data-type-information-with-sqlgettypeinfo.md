---
title: Abrufen von Daten geben Informationen mit SQLGetTypeInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC], identifiers
- SQLGetTypeInfo function [ODBC], retrieving data type information
- retrieving data type information [ODBC]
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: d4f8b152-ab9e-4d05-a720-d10a08a6df81
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44c1edaadc1a30dd27556c52bb7dc7a8f297ae48
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645918"
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>Abrufen von Datentypinformationen mit SQLGetTypeInfo
Da die Zuordnungen von zugrunde liegenden SQL-Datentypen zu ODBC-Typ-IDs ungefähre sind, handelt es sich bei ODBC bietet eine Funktion (**SQLGetTypeInfo**) beschrieben, über die ein Treiber vollständig kann jeder SQL-Datentyp in der Datenquelle. Diese Funktion gibt ein Resultset, das jeder Zeile die Eigenschaften eines einzelnen Datentyps, wie z. B. Name, Typ-ID, Genauigkeit, Dezimalstellen und NULL-Zulässigkeit beschreibt.  
  
 Diese Informationen werden in der Regel von generischen Anwendungen verwendet, mit denen den Benutzer zum Erstellen und Ändern von Tabellen. Solche Anwendungen rufen **SQLGetTypeInfo** auf die Datentypinformationen abrufen und dann vorzulegen einiger oder aller an dem Benutzer. Solche Anwendungen müssen zwei Dinge achten:  
  
-   Zu einer single-Typ-ID, dies kann schwierig zu bestimmen, welcher Datentyp verwenden, kann mehr als eine SQL-Datentyp zuordnen. Um dieses Problem zu beheben, wird das Resultset vom Typ-ID und dann entsprechend der Nähe der Typbezeichner-Definition zuerst sortiert. Darüber hinaus haben Daten Datenquelle definierten Datentypen Vorrang vor den benutzerdefinierten Datentypen. Nehmen wir beispielsweise an, dass eine Datenquelle definiert, die ganze Zahl und LEISTUNGSINDIKATOR-Datentypen, um identisch sein, außer dass LEISTUNGSINDIKATOR automatisch erhöht wird. Angenommen Sie auch, dass der benutzerdefinierte Typ WHOLENUM ein Synonym für die ganze Zahl. Jeder dieser Typen ist SQL_INTEGER zugeordnet. In der **SQLGetTypeInfo** Resultset, ganze Zahl zuerst angezeigt, gefolgt von WHOLENUM festgestellt wird und klicken Sie dann. WHOLENUM wird nach Ganzzahl angezeigt, da sie eine benutzerdefinierte, aber bevor Zähler, da er mehr eng entspricht die Definition der SQL_INTEGER Typbezeichner.  
  
-   ODBC definiert den Datentypnamen für die Verwendung in nicht **CREATE TABLE** und **ALTER TABLE** Anweisungen. Stattdessen sollte die Anwendung den Namen, die zurückgegeben werden, in der Spalte TYPE_NAME des Resultsets vom verwenden **SQLGetTypeInfo**. Der Grund dafür ist, dass obwohl die meisten SQL variiert nicht viel über DBMS, Datentypnamen erheblich variieren. Anstatt zu zwingen, Treiber für SQL-Anweisungen analysiert, und Ersetzen Sie standard Datentypnamen mit speziellen DBMS-Daten-Typnamen, erfordert-ODBC-Anwendungen für die DBMS-spezifische-Namen im vornherein verwenden.  
  
 Beachten Sie, dass **SQLGetTypeInfo** unbedingt beschreibt nicht alle von den Datentypen, die eine Anwendung auftreten kann. Insbesondere können Resultsets nicht direkt von der Datenquelle unterstützte Datentypen enthalten. Beispielsweise sind die Datentypen der Spalten in Resultsets von Katalogfunktionen zurückgegeben von ODBC definiert, und diese Datentypen können nicht von der Datenquelle unterstützt werden. Um die Merkmale der Datentypen in einem Resultset zu ermitteln, die eine Anwendung ruft **SQLColAttribute**.
