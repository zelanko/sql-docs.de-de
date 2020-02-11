---
title: Datentyp Konvertierungen | Microsoft-Dokumentation
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
ms.openlocfilehash: 590bd488ae87e8e871837c3055a3225794850d00
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077015"
---
# <a name="data-type-conversions"></a>Datentypkonvertierungen
Daten können zu vier Mal von einem Typ in einen anderen konvertiert werden: Wenn Daten in einer Anwendungsvariablen in eine andere übertragen werden (c zu c), wenn Daten in einer Anwendungsvariablen an einen Anweisungs Parameter (c an SQL) gesendet werden, wenn Daten in einer Resultsetspalte in zurückgegeben werden eine Anwendungs Variable (SQL zu C) und beim Übertragen von Daten aus einer Datenquellen Spalte in eine andere (SQL to SQL).  
  
 Alle Konvertierungen, die auftreten, wenn Daten von einer Anwendungsvariablen in eine andere übertragen werden, liegt außerhalb des Gültigkeits Bereichs dieses Dokuments.  
  
 Wenn eine Anwendung eine Variable an eine Resultsetspalte oder einen Anweisungs Parameter bindet, gibt die Anwendung implizit eine Datentyp Konvertierung in der Wahl des Datentyps der Anwendungsvariablen an. Angenommen, eine Spalte enthält ganzzahlige Daten. Wenn die Anwendung eine ganzzahlige Variable an die Spalte bindet, gibt Sie an, dass keine Konvertierung durchgeführt werden soll. Wenn die Anwendung eine Zeichen Variable an die Spalte bindet, gibt Sie an, dass die Daten von einer Ganzzahl in ein Zeichen konvertiert werden sollen.  
  
 ODBC definiert, wie Daten zwischen den einzelnen SQL-und C-Datentypen konvertiert werden. ODBC unterstützt im Grunde alle angemessenen Konvertierungen, wie z. b. Zeichen in Integer und Integer in float, und unterstützt keine falsch definierten Konvertierungen, wie z. b. float-to-date. Treiber sind erforderlich, um alle Konvertierungen für jeden unterstützten SQL-Datentyp zu unterstützen. Eine umfassende Liste der Konvertierungen zwischen SQL-und c-Datentypen finden [Sie unter Konvertieren von Daten aus SQL-in c](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) -Datentypen und [Konvertieren von Daten aus C in SQL-Daten](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) Typen in Anhang D: Datentypen.  
  
 ODBC definiert auch eine Skalarfunktion zum Umrechnen von Daten aus einem SQL-Datentyp in einen anderen. Die **Convert** -Skalarfunktion wird vom Treiber der zugrunde liegenden Skalarfunktion oder den Funktionen, die für die Durchführung von Konvertierungen in der Datenquelle definiert sind, zugeordnet. Da diese Funktion DBMS-spezifischen Funktionen zugeordnet ist, definiert ODBC nicht, wie diese Konvertierungen funktionieren oder welche Konvertierungen unterstützt werden müssen. Eine Anwendung ermittelt mithilfe der SQL_CONVERT Optionen in **SQLGetInfo**, welche Konvertierungen von einem bestimmten Treiber und einer Datenquelle unterstützt werden. Weitere Informationen zur **Convert** -Skalarfunktion finden Sie unter Escapesequenzen [in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) und [explizite Datentyp Konvertierungs Funktion](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md).
