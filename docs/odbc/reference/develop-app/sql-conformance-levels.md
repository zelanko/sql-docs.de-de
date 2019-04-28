---
title: SQL-Übereinstimmungsebenen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2e8ce5aeeb94a4f7a33b22054adc8067e0654ac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62690206"
---
# <a name="sql-conformance-levels"></a>SQL-Übereinstimmungsebenen
Die Ebene der SQL-92-Grammatik, die vom Treiber unterstützt wird angegeben, durch den Wert durch einen Aufruf zurückgegebenen **SQLGetInfo** mit dem Typ der SQL_SQL_CONFORMANCE-Informationen. Dies gibt an, ob der Treiber den Eintrag, FIPS Transitional, zwischen- oder Full-Ebenen, die in SQL-92 definierten entspricht.  
  
 Alle ODBC-Treiber müssen die minimale SQL-Grammatik, die in beschriebenen unterstützen [minimale SQL-Grammatik](../../../odbc/reference/appendixes/sql-minimum-grammar.md) in Anhang C: SQL-Grammatik. Diese Grammatik ist eine Teilmenge der Ebene der SQL-92-Eintrag. Treiber möglicherweise zusätzliche SQL unterstützt und werden konform, die auf die SQL-92-Eintrag, zwischen- oder vollständige oder die FIPS 127-2-Übergang-Ebene. Treiber, die einer bestimmten Ebene der SQL-92 oder FIPS 127-2-Standards entsprechen, können zusätzliche Features eines höheren Ebenen unterstützt noch nicht vollständig Standardkonformität auf dieser Ebene. Um zu bestimmen, ob ein Feature unterstützt wird, sollte eine Anwendung aufrufen **SQLGetInfo** mit dem Typ der entsprechenden Informationen. Der Konformitätsgrad des eine SQL-Funktion wird in den entsprechenden Informationstyp beschrieben. (Finden Sie unter den [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) funktionsbeschreibung.)
