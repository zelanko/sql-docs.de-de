---
title: Typ-Bezeichner | Microsoft Docs
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
ms.openlocfilehash: a274a19eaa0a2fdf98bcaa9ef42406ee8a6b6461
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306431"
---
# <a name="type-identifiers"></a>Typenbezeichner
Um SQL- und C-Datentypen zu beschreiben, definiert ODBC zwei Sätze von *Typbezeichnern*. Ein Typbezeichner beschreibt den Typ einer SQL-Spalte oder eines C-Puffers. Es handelt **sich um** einen #define Wert und wird in der Regel als Funktionsargument übergeben oder in Metadaten zurückgegeben.  
  
 Der folgende Aufruf von **SQLBindParameter** bindet z. B. eine Variable vom Typ SQL_DATE_STRUCT an einen Datumsparameter in einer SQL-Anweisung. Der C-Typbezeichner SQL_C_TYPE_DATE gibt den Typ der *Date-Variablen* an, und der SQL-Typbezeichner SQL_TYPE_DATE den Typ des dynamischen Parameters angibt.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
