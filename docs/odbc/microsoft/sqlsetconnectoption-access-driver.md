---
title: SQLSetConnectOption (Zugriffstreiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8e5f15575d34031d9886219af5677b4fc5f1d5aa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301533"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Access Driver-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Comment|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Die SQL_ACCESS_MODE fOption kann entweder auf SQL_MODE_READ_ONLY oder SQL_MODE_READ_WRITE eingestellt werden. Der Treiber verhindert jedoch keine Aktualisierungen, wenn SQL_ACCESS_MODE auf SQL_MODE_READ_ONLY festgelegt ist.|  
|SQL_AUTOCOMMIT|Wenn der Microsoft Access-Treiber verwendet wird, kann die Option SQL_AUTOCOMMIT entweder auf SQL_AUTOCOMMIT_ON oder SQL_AUTOCOMMIT_OFF festgelegt werden, da der Microsoft Access-Treiber Transaktionen unterstützt[1].|  
|SQL_CURRENT_QUALIFIER|Unterstützt.|  
|SQL_LOGIN_TIMEOUT|Wird nicht unterstützt.|  
|SQL_OPT_TRACE|Unterstützt.|  
|SQL_OPT_TRACEFILE|Unterstützt.|  
|SQL_PACKET_SIZE|Wird nicht unterstützt.|  
|SQL_QUIET_MODE|Wird nicht unterstützt.|  
|SQL_TRANSLATE_DLL|Wird nicht unterstützt.|  
|SQL_TRANSLATION_OPTION|Wird nicht unterstützt.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION ist immer SQL_TXN_READ_COMMITTED.|  
  
 [1] Atomare Transaktionen werden vom Microsoft Access-Treiber nicht unterstützt. Beim Übertragen einer Transaktion mit dem Microsoft Access-Treiber besteht zwischen dem Zeitpunkt, zu dem der Vorgang festgeschrieben wird, und dem Zeitpunkt, zu dem die Werte auf den Datenträger geschrieben werden, eine endliche Verzögerung. Diese Verzögerung wird durch eine Verzögerung bestimmt, die dem Microsoft Jet-Modul innewohnt. Das Seitentimeout darf nicht kleiner als ein Mindestwert sein, auch wenn die Option PageTimeout unterhalb dieses Werts festgelegt ist. Daher gibt es keine Garantie, dass die festgeschriebenen Daten stabil sind, da während der Verzögerung Änderungen vorgenommen werden können.
