---
title: Datentypkonvertierungen | Microsoft Docs
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
ms.openlocfilehash: cd888fe32692494e2b0ceadc1ed872dd96e244a9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305212"
---
# <a name="data-type-conversions"></a>Datentypkonvertierungen
Daten können von einem Typ in einen anderen zu einem von vier Zeiten konvertiert werden: wenn Daten von einer Anwendungsvariablen in eine andere übertragen werden (C nach C), wenn Daten in einer Anwendungsvariablen an einen Anweisungsparameter (C an SQL) gesendet werden, wenn Daten in einer Ergebnissatzspalte in einer Anwendungsvariablen (SQL zu C) zurückgegeben werden und wenn Daten von einer Datenquellenspalte in eine andere übertragen werden (SQL to SQL).  
  
 Jede Konvertierung, die auftritt, wenn Daten von einer Anwendungsvariablen in eine andere übertragen werden, liegt außerhalb des Rahmens dieses Dokuments.  
  
 Wenn eine Anwendung eine Variable an eine Ergebnissatzspalte oder einen Anweisungsparameter bindet, gibt die Anwendung implizit eine Datentypkonvertierung in der Auswahl des Datentyps der Anwendungsvariablen an. Angenommen, eine Spalte enthält ganzzahlige Daten. Wenn die Anwendung eine Ganzzahlvariable an die Spalte bindet, wird angegeben, dass keine Konvertierung durchgeführt wird. Wenn die Anwendung eine Zeichenvariable an die Spalte bindet, gibt sie an, dass die Daten von Ganzzahl in Zeichen konvertiert werden.  
  
 ODBC definiert, wie Daten zwischen den einzelnen SQL- und C-Datentypen konvertiert werden. Grundsätzlich unterstützt ODBC alle vernünftigen Konvertierungen, z. B. Zeichen in Ganzzahl und Ganzzahl zum Float, und unterstützt keine nicht definierten Konvertierungen, z. B. float bis heute. Treiber sind erforderlich, um alle Konvertierungen für jeden von ihnen unterstützten SQL-Datentyp zu unterstützen. Eine vollständige Liste der Konvertierungen zwischen SQL- und C-Datentypen finden Sie unter [Konvertieren von Daten aus SQL-In-C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) und Konvertieren von Daten von C in [SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) in Anhang D: Datentypen.  
  
 ODBC definiert auch eine skalare Funktion zum Konvertieren von Daten von einem SQL-Datentyp in einen anderen. Die **scalar-Funktion CONVERT** wird vom Treiber der zugrunde liegenden skalaren Funktion oder den Funktionen zugeordnet, die definiert sind, um Konvertierungen in der Datenquelle durchzuführen. Da diese Funktion DBMS-spezifischen Funktionen zugeordnet ist, definiert ODBC nicht, wie diese Konvertierungen funktionieren oder welche Konvertierungen unterstützt werden müssen. Eine Anwendung erkennt, welche Konvertierungen von einem bestimmten Treiber und einer bestimmten Datenquelle über die SQL_CONVERT Optionen in **SQLGetInfo**unterstützt werden. Weitere Informationen zur **skalaren Funktion CONVERT** finden Sie unter [Escape-Sequenzen in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) und [Explicit Data Type Conversion Function](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md).
