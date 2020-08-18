---
description: Systemfunktionen
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1be058f5021c3f03242a09500150acd98cac8e70
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386406"
---
# <a name="system-functions"></a>Systemfunktionen
In der folgenden Tabelle werden die Systemfunktionen aufgelistet, die in der ODBC-skalarfunktionsmenge enthalten sind. Durch den Aufruf von **SQLGetInfo** mit dem *Informationstyp* SQL_SYSTEM_FUNCTIONS kann eine Anwendung bestimmen, welche System Funktionen von einem Treiber unterstützt werden.  
  
 Argumente, die als *Exp* bezeichnet werden, können der Name einer Spalte, das Ergebnis einer anderen Skalarfunktion oder ein Literalwert sein, wobei der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME oder SQL_TYPE_TIMESTAMP dargestellt werden könnte.  
  
 Argumente, die als *Wert* bezeichnet werden, können eine Literalkonstante sein, wobei der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME oder SQL_TYPE_TIMESTAMP dargestellt werden kann.  
  
 Zurückgegebene Werte werden als ODBC-Datentypen dargestellt.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|**Database ()**  (ODBC 1,0)|Gibt den Namen der Datenbank zurück, die dem Verbindungs Handle entspricht. (Der Name der Datenbank ist auch durch Aufrufen von **SQLGetConnectOption** mit der Option SQL_CURRENT_QUALIFIER Connection verfügbar.)|  
|**IFNULL (** _Exp_,_Wert_**)**  (ODBC 1,0)|Wenn *Exp* NULL ist, wird der *Wert* zurückgegeben. Wenn *Exp* nicht NULL ist, wird *Exp* zurückgegeben. Der mögliche Datentyp oder die Art von *Wert* muss mit dem Datentyp von *Exp*kompatibel sein.|  
|**Benutzer ()**  (ODBC 1,0)|Gibt den Benutzernamen im DBMS zurück. (Der Benutzername ist auch über **SQLGetInfo** verfügbar, indem der Informationstyp angegeben wird: SQL_USER_NAME.) Dies kann sich von dem Anmelde Namen unterscheiden.|
