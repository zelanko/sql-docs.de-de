---
title: SQL-Konformitäts Ebenen | Microsoft-Dokumentation
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
ms.openlocfilehash: 7862b2e3a86c6d98a51c73ecb470d59bcfe29dc9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107524"
---
# <a name="sql-conformance-levels"></a>SQL-Übereinstimmungsebenen
Die von einem Treiber unterstützte Ebene der SQL-92-Grammatik wird durch den Wert angegeben, der von einem **SQLGetInfo** -Aufgabentyp mit dem SQL_SQL_CONFORMANCE Informationstyp zurückgegeben wird. Dies gibt an, ob der Treiber dem Eintrag, der in SQL-92 definierten Übergangs-, zwischen-oder vollständigen Ebene entspricht.  
  
 Alle ODBC-Treiber müssen die minimale SQL-Grammatik unterstützen, die in Anhang C: SQL-Grammatik [unter minimale SQL](../../../odbc/reference/appendixes/sql-minimum-grammar.md) -Grammatik beschrieben wird. Diese Grammatik ist eine Teilmenge der Einstiegsebene von SQL-92. Treiber unterstützen möglicherweise zusätzliche SQL und sind mit dem SQL-92-Eintrag, der zwischen-oder der vollständigen Ebene oder der Übergangsstufe "fps 127-2" konform. Treiber, die einer bestimmten Stufe von SQL-92 127-2 oder der Funktion "SQL-" entsprechen, können zusätzliche Features unterstützen, die in einer der höheren Ebenen noch nicht vollständig kompatibel sind. Um zu ermitteln, ob eine Funktion unterstützt wird, sollte eine Anwendung **SQLGetInfo** mit dem entsprechenden Informationstyp aufrufen. Der Konformitäts Grad einer SQL-Funktion wird im entsprechenden Informationstyp beschrieben. (Weitere Informationen finden Sie in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion.)
