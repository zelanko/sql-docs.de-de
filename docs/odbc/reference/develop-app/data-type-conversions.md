---
description: Datentypkonvertierungen
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 92c31cb12c7bb02cf8e108251ae5ebd6f12aed5e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429342"
---
# <a name="data-type-conversions"></a>Datentypkonvertierungen
Daten können jeweils von einem Typ in einen anderen konvertiert werden: Wenn Daten von einer Anwendungsvariablen in eine andere übertragen werden (c zu c), wenn Daten in einer Anwendungsvariablen an einen Anweisungs Parameter (c an SQL) gesendet werden, wenn Daten in einer Resultsetspalte in einer Anwendungsvariablen (SQL an c) zurückgegeben werden und Daten aus einer Datenquellen Spalte in eine andere übertragen werden (SQL an SQL).  
  
 Alle Konvertierungen, die auftreten, wenn Daten von einer Anwendungsvariablen in eine andere übertragen werden, liegt außerhalb des Gültigkeits Bereichs dieses Dokuments.  
  
 Wenn eine Anwendung eine Variable an eine Resultsetspalte oder einen Anweisungs Parameter bindet, gibt die Anwendung implizit eine Datentyp Konvertierung in der Wahl des Datentyps der Anwendungsvariablen an. Angenommen, eine Spalte enthält ganzzahlige Daten. Wenn die Anwendung eine ganzzahlige Variable an die Spalte bindet, gibt Sie an, dass keine Konvertierung durchgeführt werden soll. Wenn die Anwendung eine Zeichen Variable an die Spalte bindet, gibt Sie an, dass die Daten von einer Ganzzahl in ein Zeichen konvertiert werden sollen.  
  
 ODBC definiert, wie Daten zwischen den einzelnen SQL-und C-Datentypen konvertiert werden. ODBC unterstützt im Grunde alle angemessenen Konvertierungen, wie z. b. Zeichen in Integer und Integer in float, und unterstützt keine falsch definierten Konvertierungen, wie z. b. float-to-date. Treiber sind erforderlich, um alle Konvertierungen für jeden unterstützten SQL-Datentyp zu unterstützen. Eine umfassende Liste der Konvertierungen zwischen SQL-und c-Datentypen finden [Sie unter Konvertieren von Daten aus SQL-in c](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) -Datentypen und [Konvertieren von Daten aus C in SQL-Daten](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) Typen in Anhang D: Datentypen.  
  
 ODBC definiert auch eine Skalarfunktion zum Umrechnen von Daten aus einem SQL-Datentyp in einen anderen. Die **Convert** -Skalarfunktion wird vom Treiber der zugrunde liegenden Skalarfunktion oder den Funktionen, die für die Durchführung von Konvertierungen in der Datenquelle definiert sind, zugeordnet. Da diese Funktion DBMS-spezifischen Funktionen zugeordnet ist, definiert ODBC nicht, wie diese Konvertierungen funktionieren oder welche Konvertierungen unterstützt werden müssen. Eine Anwendung ermittelt mithilfe der SQL_CONVERT Optionen in **SQLGetInfo**, welche Konvertierungen von einem bestimmten Treiber und einer Datenquelle unterstützt werden. Weitere Informationen zur **Convert** -Skalarfunktion finden Sie unter Escapesequenzen [in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) und [explizite Datentyp Konvertierungs Funktion](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md).
