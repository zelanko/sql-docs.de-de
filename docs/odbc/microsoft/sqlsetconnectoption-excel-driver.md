---
title: SQLSetConnectOption (Excel-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Excel Driver
- Excel driver [ODBC], SQLSetConnectOption
ms.assetid: 528d21d1-4516-4497-9da4-7b87d77e622a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 70bca38a81b59b7113f0873849609837bf8f48ec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071735"
---
# <a name="sqlsetconnectoption-excel-driver"></a>SQLSetConnectOption (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Excel-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Kommentar|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Die SQL_ACCESS_MODE fOption kann entweder SQL_MODE_READ_ONLY oder SQL_MODE_READ_WRITE festgelegt werden. Der Treiber verhindert jedoch nicht Updates, wenn SQL_ACCESS_MODE SQL_MODE_READ_ONLY festgelegt ist.|  
|SQL_AUTOCOMMIT|Der Microsoft Excel-Treiber unterstützt nur SQL_AUTOCOMMIT auf (Standardstatus) festgelegt wird, da sie keine Transaktionen unterstützen.|  
|SQL_CURRENT_QUALIFIER|Unterstützt.|  
|SQL_LOGIN_TIMEOUT|Wird nicht unterstützt.|  
|SQL_OPT_TRACE|Unterstützt.|  
|SQL_OPT_TRACEFILE|Unterstützt.|  
|SQL_PACKET_SIZE|Wird nicht unterstützt.|  
|SQL_QUIET_MODE|Wird nicht unterstützt.|  
|SQL_TRANSLATE_DLL|Wird nicht unterstützt.|  
|SQL_TRANSLATION_OPTION|Wird nicht unterstützt.|  
|SQL_TXN_ISOLATION|Wird nicht unterstützt.|
