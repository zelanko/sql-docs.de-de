---
title: SQLSetConnectOption (Access-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], Access Driver
ms.assetid: 58399bc4-d0b1-4eaa-a474-c92b2d5855ea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bea124a78e2a180180c59de3577fe1db7637e110
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67897784"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Access-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Kommentar|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Die SQL_ACCESS_MODE fOption kann entweder SQL_MODE_READ_ONLY oder SQL_MODE_READ_WRITE festgelegt werden. Der Treiber verhindert jedoch nicht Updates, wenn SQL_ACCESS_MODE SQL_MODE_READ_ONLY festgelegt ist.|  
|SQL_AUTOCOMMIT|Wenn die Microsoft Access-Treiber verwendet wird, kann die SQL_AUTOCOMMIT-Option auf SQL_AUTOCOMMIT_ON oder SQL_AUTOCOMMIT_OFF, festgelegt werden, da es sich bei der Microsoft Access-Treiber unterstützt die Transaktionen [1].|  
|SQL_CURRENT_QUALIFIER|Unterstützt.|  
|SQL_LOGIN_TIMEOUT|Wird nicht unterstützt.|  
|SQL_OPT_TRACE|Unterstützt.|  
|SQL_OPT_TRACEFILE|Unterstützt.|  
|SQL_PACKET_SIZE|Wird nicht unterstützt.|  
|SQL_QUIET_MODE|Wird nicht unterstützt.|  
|SQL_TRANSLATE_DLL|Wird nicht unterstützt.|  
|SQL_TRANSLATION_OPTION|Wird nicht unterstützt.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION ist immer SQL_TXN_READ_COMMITTED.|  
  
 [1] Atomarische Transaktionen werden von der Microsoft Access-Treiber nicht unterstützt. Wenn Sie eine Transaktion mit dem Microsoft Access-Treiber zu committen, vorhanden ist eine endliche Verzögerung zwischen dem Zeitpunkt, der die Transaktion ein Commit ausgeführt wird und die Zeit, die die Werte geschrieben werden auf dem Datenträger. Diese Verzögerung richtet sich nach einer Verzögerung, die inhärenten in das Microsoft Jet-Modul. Das Timeout der Seite werden kleiner als ein Mindestwert, nicht, auch wenn die Option ' pagetimeout ' unter diesen Wert festgelegt ist. Daher besteht keine Garantie dafür, die Daten ein Commit ausgeführt ist stabil, da Änderungen können, während der Verzögerung vorgenommen werden.
