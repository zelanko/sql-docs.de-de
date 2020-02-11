---
title: System Funktionen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e0c7817d37e14ad07b9cc64f59691c27cf665177
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070096"
---
# <a name="system-functions"></a>Systemfunktionen
In der folgenden Tabelle werden die Systemfunktionen aufgelistet, die in der ODBC-skalarfunktionsmenge enthalten sind. Durch den Aufruf von **SQLGetInfo** mit dem *Informationstyp* SQL_SYSTEM_FUNCTIONS kann eine Anwendung bestimmen, welche System Funktionen von einem Treiber unterstützt werden.  
  
 Argumente, die als *Exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein Literalwert sein, wobei der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME oder SQL_TYPE_TIMESTAMP dargestellt werden könnte.  
  
 Argumente, die als *Wert* bezeichnet werden, können eine Literalkonstante sein, wobei der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME oder SQL_TYPE_TIMESTAMP dargestellt werden kann.  
  
 Zurückgegebene Werte werden als ODBC-Datentypen dargestellt.  
  
|Funktion|BESCHREIBUNG|  
|--------------|-----------------|  
|**Database ()** (ODBC 1,0)|Gibt den Namen der Datenbank zurück, die dem Verbindungs Handle entspricht. (Der Name der Datenbank ist auch durch Aufrufen von **SQLGetConnectOption** mit der Option SQL_CURRENT_QUALIFIER Connection verfügbar.)|  
|**IFNULL (** _Exp_,_Wert_**)** (ODBC 1,0)|Wenn *Exp* NULL ist, wird der *Wert* zurückgegeben. Wenn *Exp* nicht NULL ist, wird *Exp* zurückgegeben. Der mögliche Datentyp oder die Art von *Wert* muss mit dem Datentyp von *Exp*kompatibel sein.|  
|**Benutzer ()** (ODBC 1,0)|Gibt den Benutzernamen im DBMS zurück. (Der Benutzername ist auch über **SQLGetInfo** verfügbar, indem der Informationstyp angegeben wird: SQL_USER_NAME.) Dies kann sich von dem Anmelde Namen unterscheiden.|
