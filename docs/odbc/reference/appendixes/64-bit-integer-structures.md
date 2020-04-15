---
title: 64-Bit Ganzzahlstrukturen | Microsoft Docs
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
ms.openlocfilehash: 1ecbe4dae4c1bd21ac3d542ee0d9b18169df0116
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307511"
---
# <a name="64-bit-integer-structures"></a>64-Bit-Integerstrukturen
Der C-Typ für die SQL_C_SBIGINT- und SQL_C_UBIGINT-Datentypbezeichner für Microsoft C-Compiler ist _int64. Wenn ein anderer Compiler als ein Microsoft® C-Compiler verwendet wird, kann der C-Typ unterschiedlich sein. Wenn der Compiler nativ 64-Bit-Ganzzahlen unterstützt, sollte der Treiber oder die Anwendung ODBCINT64 als systemeigenen 64-Bit-Ganzzahltyp definieren. Wenn der Compiler keine 64-Bit-Ganzzahlen nativ unterstützt, kann eine Anwendung oder ein Treiber die folgenden Strukturen definieren, um sicherzustellen, dass sie Zugriff auf diese Daten hat:  
  
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
  
 Diese Strukturen sollten an einer 8-Byte-Grenze ausgerichtet werden, da eine 64-Bit-Ganzzahl an der 8-Byte-Grenze ausgerichtet ist.
