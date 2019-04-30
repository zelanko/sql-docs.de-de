---
title: SQLFreeStmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4aa7e597bcfa80d7d45064c844986018d64617d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63190304"
---
# <a name="sqlfreestmt"></a>'SQLFreeStmt'
  **SQLFreeStmt** wird für ODBC 3.0 und höher nicht empfohlen. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt alle definierten *Option* Werte für **SQLFreeStmt**. Allerdings [SQLCloseCursor](sqlclosecursor.md), [SQLBindParameter](sqlbindparameter.md), [SQLBindCol](sqlbindcol.md), **SQLSetDescField**, und [SQLFreeHandle ](sqlfreehandle.md) ersetzen oder duplizieren Sie die Funktion der **SQLFreeStmt** und sollte stattdessen verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLFreeStmt-Funktion](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
