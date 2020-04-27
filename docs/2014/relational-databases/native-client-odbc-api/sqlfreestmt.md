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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63190304"
---
# <a name="sqlfreestmt"></a>'SQLFreeStmt'
  **SQLFreeStmt** wird für ODBC 3.0 und höher nicht empfohlen. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt alle definierten *options* Werte für **SQLFreeStmt**. [SQLCloseCursor](sqlclosecursor.md), [SQLBindParameter](sqlbindparameter.md), [SQLBindCol](sqlbindcol.md), **SQLSetDescField**und [SQLFreeHandle](sqlfreehandle.md) ersetzen oder duplizieren jedoch die-Funktion von **SQLFreeStmt** und sollten stattdessen verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLFreeStmt-Funktion](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
