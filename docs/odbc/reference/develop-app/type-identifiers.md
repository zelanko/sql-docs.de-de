---
description: Typenbezeichner
title: Typbezeichner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ed41716cd351631578d01027663aa9e0f028c7d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487443"
---
# <a name="type-identifiers"></a>Typenbezeichner
Um SQL-und C-Datentypen zu beschreiben, definiert ODBC zwei Sätze von *typbezeichlen*. Ein Typbezeichner beschreibt den Typ einer SQL-Spalte oder eines C-Puffers. Dabei handelt es sich um einen **#define** Wert, der im Allgemeinen als Funktions Argument und in den Metadaten zurückgegeben wird.  
  
 Der folgende Befehl von **SQLBindParameter** bindet z. b. eine Variable vom Typ SQL_DATE_STRUCT an einen Datums Parameter in einer SQL-Anweisung. Der C-Typbezeichner SQL_C_TYPE_DATE gibt den Typ der *Datums* Variablen an, und der SQL-Typbezeichner SQL_TYPE_DATE den Typ des dynamischen Parameters angibt.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
