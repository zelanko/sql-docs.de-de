---
title: SQLFreeEnv-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeEnv
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef89943f95a6492614972c3e89fe2129becc1aa5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086425"
---
# <a name="sqlfreeenv-mapping"></a>SQLFreeEnv-Zuordnung
Wenn eine Anwendung ruft **SQLFreeEnv** über einen ODBC *3.x* Treiber, den Aufruf von  
  
```  
SQLFreeEnv(henv)   
```  
  
 wird zugeordnet  
  
```  
SQLFreeHandle(SQL_HANDLE_ENV,Handle)  
```  
  
 mit der *behandeln* Argument festgelegt wird, mit dem Wert im *Henv*.
