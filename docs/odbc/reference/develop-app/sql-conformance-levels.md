---
title: SQL-Konformitätsstufen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 3529df2c-a09b-4c16-9c60-eae7a06d903a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 875330ac78588566b4b1c212f7a65d2841127a61
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301381"
---
# <a name="sql-conformance-levels"></a>SQL-Übereinstimmungsebenen
Die von einem Treiber unterstützte SQL-92-Grammatikebene wird durch den Wert angegeben, der von einem Aufruf von **SQLGetInfo** mit dem SQL_SQL_CONFORMANCE-Informationstyp zurückgegeben wird. Dies gibt an, ob der Treiber den in SQL-92 definierten Ebenen Entry, FIPS Transitional, Intermediate oder Full entspricht.  
  
 Alle ODBC-Treiber müssen die in [SQL Minimum Grammar](../../../odbc/reference/appendixes/sql-minimum-grammar.md) in Anhang C: SQL Grammar beschriebene Mindestsql-Grammatik unterstützen. Diese Grammatik ist eine Teilmenge der Einstiegsebene von SQL-92. Treiber unterstützen möglicherweise zusätzliche SQL und sind der SQL-92-Einstiegs-, Zwischen- oder Vollebene oder der FIPS 127-2-Übergangsebene entsprechend. Treiber, die eine bestimmte SQL-92- oder FIPS 127-2-Stufe erfüllen, können zusätzliche Funktionen in einer der höheren Ebenen unterstützen, aber nicht vollständig an diese Ebene angepasst sein. Um zu bestimmen, ob ein Feature unterstützt wird, sollte eine Anwendung **SQLGetInfo** mit dem entsprechenden Informationstyp aufrufen. Die Konformitätsstufe eines SQL-Features wird im entsprechenden Informationstyp beschrieben. (Siehe [sqlGetInfo-Funktionsbeschreibung.)](../../../odbc/reference/syntax/sqlgetinfo-function.md)
