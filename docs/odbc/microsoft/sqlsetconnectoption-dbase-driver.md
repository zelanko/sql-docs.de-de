---
title: SQLSetConnectOption (dBASE-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], dBASE Driver
ms.assetid: b1924c33-6820-4566-b716-6897807edd0f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 32bfb4755d308706372c0d863f8246631c122f21
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301521"
---
# <a name="sqlsetconnectoption-dbase-driver"></a>SQLSetConnectOption (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält dBASE-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Comment|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Die SQL_ACCESS_MODE fOption kann entweder auf SQL_MODE_READ_ONLY oder SQL_MODE_READ_WRITE eingestellt werden. Der Treiber verhindert jedoch keine Aktualisierungen, wenn SQL_ACCESS_MODE auf SQL_MODE_READ_ONLY festgelegt ist.|  
|SQL_AUTOCOMMIT|Der dBASE-Treiber unterstützt nur SQL_AUTOCOMMIT auf ON (Standardstatus) festgelegt ist, da er keine Transaktionen unterstützt.|  
|SQL_CURRENT_QUALIFIER|Unterstützt.|  
|SQL_LOGIN_TIMEOUT|Wird nicht unterstützt.|  
|SQL_OPT_TRACE|Unterstützt.|  
|SQL_OPT_TRACEFILE|Unterstützt.|  
|SQL_PACKET_SIZE|Wird nicht unterstützt.|  
|SQL_QUIET_MODE|Wird nicht unterstützt.|  
|SQL_TRANSLATE_DLL|Wird nicht unterstützt.|  
|SQL_TRANSLATION_OPTION|Wird nicht unterstützt.|  
|SQL_TXN_ISOLATION|Wird nicht unterstützt.|
