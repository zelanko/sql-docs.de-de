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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9b7fbc3754121418ea2059ea511f3b247dcff8dd
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706091"
---
# <a name="sqlfreestmt"></a>'SQLFreeStmt'
  **SQLFreeStmt** wird für ODBC 3.0 und höher nicht empfohlen. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt alle definierten *options* Werte für **SQLFreeStmt**. [SQLCloseCursor](sqlclosecursor.md), [SQLBindParameter](sqlbindparameter.md), [SQLBindCol](sqlbindcol.md), **SQLSetDescField**und [SQLFreeHandle](sqlfreehandle.md) ersetzen oder duplizieren jedoch die-Funktion von **SQLFreeStmt** und sollten stattdessen verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLFreeStmt-Funktion](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
