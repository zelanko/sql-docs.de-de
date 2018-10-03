---
title: Datentypkonvertierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], conversions
- SQL data types [ODBC], conversions
- converting data [ODBC]
- converting data types [ODBC]
- C data types [ODBC], conversions
ms.assetid: d311fe1c-d882-4136-9fa5-220a4121e04c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 84710ffd69ea377c979adf94af1394d8436ef10b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786338"
---
# <a name="data-type-conversions"></a>Datentypkonvertierungen
Daten konvertiert werden können von einem Typ in einen anderen mindestens vier Wiederholungsversuche: beim Datenaustausch aus einer Anwendungsvariablen in eine andere (C, C), wenn Daten in eine Anwendungsvariable gesendet werden, auf einen Anweisungsparameter (C zu SQL), wenn Daten in einer Resultsetspalte zurückgegeben werden eine Anwendungsvariable (SQL zu C), und wenn Daten aus einer Spalte für die Datenquelle eine andere (SQL, SQL) übertragen werden.  
  
 Jede Konvertierung, die auftritt, wenn Daten aus einer Anwendung-Variable auf einen anderen übertragen werden, liegt außerhalb des Bereichs dieses Dokuments.  
  
 Wenn eine Anwendung einen Parameter für das Set Ergebnis der Spalte "oder"-Anweisung eine Variable gebunden, gibt die Anwendung implizit eine datentypkonvertierung bei der Auswahl des Datentyps der Anwendungsvariablen. Nehmen wir beispielsweise an, dass eine Spalte ganzzahlige Daten enthält. Wenn die Anwendung eine ganzzahlige Variable an die Spalte gebunden wird, gibt es an, dass keine Konvertierung ausgeführt werden; Wenn die Anwendung eine Zeichenvariable auf die Spalte gebunden wird, gibt an, dass es sich bei die Daten aus Ganzzahl in Zeichen konvertiert werden.  
  
 ODBC definiert, wie Daten zwischen jeder SQL- und C-Datentyp konvertiert werden. Im Grunde ODBC unterstützt alle angemessene Konvertierungen wie die Zeichen, ganze Zahl und die ganze Zahl, "float", und die Standardschaltfläche Konvertierungen wie "float", um das Datum wird nicht unterstützt. Treiber sind erforderlich, um alle Konvertierungen für die einzelnen SQL-Datentypen zu unterstützen, die sie unterstützen. Eine vollständige Liste von Konvertierungen zwischen SQL und C-Datentypen, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) und [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) in Anhang D:-Datentypen.  
  
 ODBC definiert auch eine skalare Funktion zum Konvertieren von Daten von einem SQL-Datentyp in einen anderen. Die **konvertieren** Skalarfunktion vom Treiber auf die zugrunde liegenden skalaren Funktion oder Funktionen, die definiert, um das Durchführen von Konvertierungen in der Datenquelle zugeordnet ist. Da die DBMS-spezifische Funktionen dieser Funktion zugeordnet ist, werden keine ODBC definiert, wie diese Konvertierungen zu arbeiten oder welche Konvertierungen unterstützt werden müssen. Eine Anwendung ermittelt, welche Konvertierungen von einer bestimmten Treiber und die Datenquelle über die SQL_CONVERT-Optionen in Microsoft Intune **SQLGetInfo**. Weitere Informationen zu den **konvertieren** skalare Funktion ist, finden Sie unter [Escapesequenzen in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) und [Explicit Data Type Conversion Function](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md).
