---
description: 64-Bit-Integerstrukturen
title: 64-Bit-ganzzahlige Strukturen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 13c57fc582b23c3ca10768c930d44ae758f1d3d6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471243"
---
# <a name="64-bit-integer-structures"></a>64-Bit-Integerstrukturen
Der C-Typ für die SQL_C_SBIGINT-und SQL_C_UBIGINT-Datentyp Bezeichner auf Microsoft C-Compilern ist _int64. Wenn ein anderer Compiler als ein Microsoft® C-Compiler verwendet wird, kann der c-Typ anders sein. Wenn der Compiler ganzzahlige 64-Bit-Ganzzahlen unterstützt, sollte der Treiber oder die Anwendung ODBCINT64 als nativer 64-Bit-ganzzahligen Typ definieren. Wenn der Compiler keine ganzzahligen 64-Bit-Zahlen unterstützt, kann eine Anwendung oder ein Treiber die folgenden Strukturen definieren, um sicherzustellen, dass er Zugriff auf diese Daten hat:  
  
```  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLUINTEGER dwHighWord;  
} SQLUBIGINT  
  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLINTEGER sdwHighWord;  
} SQLBIGINT  
```  
  
 Diese Strukturen sollten auf eine 8-Byte-Begrenzung ausgerichtet werden, da eine 64-Bit-Ganzzahl an der 8-Byte-Grenze ausgerichtet ist.
