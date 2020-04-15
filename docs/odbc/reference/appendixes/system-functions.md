---
title: Systemfunktionen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- system functions [ODBC]
- functions [ODBC], system functions
ms.assetid: 36614b4c-e037-43ef-8692-67f4861b144d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca71687887444cafc502c15683f3972cf6308e6b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302831"
---
# <a name="system-functions"></a>Systemfunktionen
In der folgenden Tabelle sind Systemfunktionen aufgeführt, die im ODBC-Skalarfunktionssatz enthalten sind. Durch Aufrufen von **SQLGetInfo** mit einem *Informationstyp* von SQL_SYSTEM_FUNCTIONS kann eine Anwendung bestimmen, welche Systemfunktionen von einem Treiber unterstützt werden.  
  
 Argumente, die als *exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein Literal sein, bei dem der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME oder SQL_TYPE_TIMESTAMP dargestellt werden kann.  
  
 Argumente, die als *Wert* bezeichnet werden, können eine literale Konstante sein, wobei der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME oder SQL_TYPE_TIMESTAMP dargestellt werden kann.  
  
 Die zurückgegebenen Werte werden als ODBC-Datentypen dargestellt.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|**DATENBANK( )** (ODBC 1.0)|Gibt den Namen der Datenbank zurück, die dem Verbindungshandle entspricht. (Der Name der Datenbank ist auch verfügbar, indem **SQLGetConnectOption** mit der SQL_CURRENT_QUALIFIER-Verbindungsoption aufgerufen wird.)|  
|**IFNULL(** _exp_,_wert_**)** (ODBC 1.0)|Wenn *exp* null ist, wird *der Wert* zurückgegeben. Wenn *exp* nicht null ist, wird *exp* zurückgegeben. Der mögliche Datentyp oder *der Werttyp* müssen mit dem Datentyp *exp*kompatibel sein.|  
|**USER( )** (ODBC 1.0)|Gibt den Benutzernamen im DBMS zurück. (Der Benutzername ist auch über **SQLGetInfo** verfügbar, indem der Informationstyp angegeben wird: SQL_USER_NAME.) Dies kann sich vom Anmeldenamen unterscheiden.|
