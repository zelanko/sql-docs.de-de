---
title: Systemfunktionen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070096"
---
# <a name="system-functions"></a>Systemfunktionen
Die folgende Tabelle enthält die Systemfunktionen, die in der ODBC-Skalarfunktion Menge enthalten sind. Durch Aufrufen von **SQLGetInfo** mit einer *Informationstyp* des SQL_SYSTEM_FUNCTIONS, kann eine Anwendung bestimmen, welche Systemfunktionen durch einen Treiber unterstützt werden.  
  
 Argumente schulungsausgabe als *"exp"* kann der Name einer Spalte, die das Ergebnis eine andere skalare Funktion oder ein Literal sein, in denen der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL dargestellt werden kann _BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP.  
  
 Argumente schulungsausgabe als *Wert* kann eine literale Konstante ist, werden, in denen der zugrunde liegende Datentyp als SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_ dargestellt werden kann TYPE_DATE, SQL_TYPE_TIME und SQL_TYPE_TIMESTAMP.  
  
 Zurückgegebenen Werte werden als ODBC-Datentypen dargestellt.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|**DATENBANK ()** (ODBC 1.0)|Gibt den Namen der Datenbank entspricht dem Verbindungshandle. (Der Name der Datenbank kann auch durch Aufrufen von **SQLGetConnectOption** mit der SQL_CURRENT_QUALIFIER-Verbindungsoption.)|  
|**IFNULL (** _"exp"_ ,_Wert_ **)** (ODBC-1.0)|Wenn *"exp"* null ist, *Wert* zurückgegeben wird. Wenn *"exp"* ist nicht null, *"exp"* zurückgegeben wird. Die möglichen Datentyp oder die Arten von *Wert* muss mit dem Datentyp kompatibel sein *"exp"* .|  
|**BENUTZER ()** (ODBC 1.0)|Gibt den Benutzernamen in das DBMS zurück. (Der Benutzername ist auch verfügbar, mit **SQLGetInfo** durch den Informationstyp angeben: SQL_USER_NAME.) Dies kann sich der Anmeldename sein.|
