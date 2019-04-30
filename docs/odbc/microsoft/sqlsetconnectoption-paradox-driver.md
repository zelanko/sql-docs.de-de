---
title: SQLSetConnectOption (Paradox-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLSetConnectOption
ms.assetid: 050ee2be-594e-4dbd-af67-8b6aae756cd1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0fac808000fb2c1fba4993b8a9ee3639d702bb48
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63305679"
---
# <a name="sqlsetconnectoption-paradox-driver"></a>SQLSetConnectOption (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Paradox-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Anmerkung|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Die SQL_ACCESS_MODE fOption kann entweder SQL_MODE_READ_ONLY oder SQL_MODE_READ_WRITE festgelegt werden. Der Treiber verhindert jedoch nicht Updates, wenn SQL_ACCESS_MODE SQL_MODE_READ_ONLY festgelegt ist.|  
|SQL_AUTOCOMMIT|Die Paradox-Treiber unterstützt nur SQL_AUTOCOMMIT auf (Standardstatus) festgelegt wird, da sie keine Transaktionen unterstützen.|  
|SQL_CURRENT_QUALIFIER|Unterstützt.|  
|SQL_LOGIN_TIMEOUT|Wird nicht unterstützt.|  
|SQL_OPT_TRACE|Unterstützt.|  
|SQL_OPT_TRACEFILE|Unterstützt.|  
|SQL_PACKET_SIZE|Wird nicht unterstützt.|  
|SQL_QUIET_MODE|Wird nicht unterstützt.|  
|SQL_TRANSLATE_DLL|Wird nicht unterstützt.|  
|SQL_TRANSLATION_OPTION|Wird nicht unterstützt.|  
|SQL_TXN_ISOLATION|Wird nicht unterstützt.|
