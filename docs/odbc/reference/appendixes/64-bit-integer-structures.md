---
title: 64-Bit-Ganzzahl-Strukturen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 93d9e6fd01d6b9ef98ebb10f6728ec4ba205fbb5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996257"
---
# <a name="64-bit-integer-structures"></a>64-Bit-Integerstrukturen
Der C-Typ für die SQL_C_SBIGINT und SQL_C_UBIGINT Datentypbezeichner in Microsoft C-Compiler ist __int64. Wenn ein Compiler als ein Microsoft®-C-Compiler verwendet wird, kann der C-Typ unterscheiden. Wenn der Compiler die 64-Bit-Ganzzahlen nativ unterstützt, sollten den Treiber oder die Anwendung ODBCINT64 werden von den systemeigenen 64-Bit-Ganzzahl-Typ definieren. Wenn der Compiler 64-Bit-Ganzzahlen nicht systemintern unterstützt wird, kann eine Anwendung oder ein Treiber definieren die folgenden Strukturen, um sicherzustellen, dass er Zugriff auf diese Daten hat:  
  
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
  
 Diese Strukturen sollte eine 8-Byte-Grenze ausgerichtet werden, da eine 64-Bit-Ganzzahl, die 8-Byte-Grenze ausgerichtet ist.
