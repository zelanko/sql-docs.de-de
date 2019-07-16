---
title: Überprüfungen des Argumentwerts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- argument value checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 013c8f80a672ed691e7519b318206c406171cfbc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077108"
---
# <a name="argument-value-checks"></a>Überprüfungen des Argumentwerts
Der Treiber-Manager überprüft die folgenden Typen der Argumente. Sofern nicht anders angegeben, gibt der Treiber-Manager SQL_ERROR zurück, auf Fehler in der Argument-Werte.  
  
-   Umgebung, Verbindung und Anweisung Handles darf nicht in der Regel mit null-Zeiger sein. Der Treiber-Manager gibt SQL_INVALID_HANDLE zurück, wenn ein null-Handle gefunden wird.  
  
-   Zeigerargumente, z. B. erforderlichen *OutputHandlePtr* in **SQLAllocHandle** und *CursorName* in **SQLSetCursorName**, nicht möglich NULL-Zeiger.  
  
-   Optionsflags, die nicht-Treiber-spezifische Werte unterstützen, müssen ein gültiger Wert sein. Z. B. *Vorgang* in **SQLSetPos** SQL_POSITION SQL_REFRESH, SQL_UPDATE, SQL_DELETE oder SQL_ADD werden muss.  
  
-   Optionsflags müssen in der Version von ODBC unterstützt, die vom Treiber unterstützt werden. Z. B. *Informationsart* in **SQLGetInfo** SQL_ASYNC_MODE (eingeführt in ODBC-Version 3.0) nicht beim Aufrufen von ODBC 2.0-Treiber.  
  
-   Anzahl von Spalten und Parameter muss größer als 0 oder größer als oder gleich 0 ist, abhängig von der Funktion sein. Der Treiber muss die obere Grenze der diese Argumentwerte, die auf Grundlage des aktuellen Resultsets oder das SQL-Anweisung überprüfen.  
  
-   Längenindikator/Argumente und Daten Puffer Länge Argumente müssen die entsprechenden Werte enthalten. Zum Beispiel das Argument, der angibt, die Länge eines Tabellennamens in **SQLColumns** (*NameLength3*) muss SQL_NTS lauten oder einen Wert größer als 0 sein; *Pufferlänge* in **SQLDescribeCol** muss größer als oder gleich 0 sein. Der Treiber möglicherweise müssen Sie auch diesen Argumenten überprüfen. Beispielsweise können sie überprüfen, *NameLength3* ist kleiner als oder gleich der maximalen Länge von einem Tabellennamen in der Datenquelle.
