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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8e5f15575d34031d9886219af5677b4fc5f1d5aa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301533"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Zugriffs Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Kommentar|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Die SQL_ACCESS_MODE fOption kann entweder auf SQL_MODE_READ_ONLY oder SQL_MODE_READ_WRITE festgelegt werden. Der Treiber hindert Updates jedoch nicht, wenn SQL_ACCESS_MODE auf SQL_MODE_READ_ONLY festgelegt ist.|  
|SQL_AUTOCOMMIT|Wenn der Microsoft Access-Treiber verwendet wird, kann die SQL_AUTOCOMMIT-Option entweder auf SQL_AUTOCOMMIT_ON oder SQL_AUTOCOMMIT_OFF festgelegt werden, da der Microsoft Access-Treiber Transaktionen [1] unterstützt.|  
|SQL_CURRENT_QUALIFIER|Unterstützt.|  
|SQL_LOGIN_TIMEOUT|Nicht unterstützt.|  
|SQL_OPT_TRACE|Unterstützt.|  
|SQL_OPT_TRACEFILE|Unterstützt.|  
|SQL_PACKET_SIZE|Nicht unterstützt.|  
|SQL_QUIET_MODE|Nicht unterstützt.|  
|SQL_TRANSLATE_DLL|Nicht unterstützt.|  
|SQL_TRANSLATION_OPTION|Nicht unterstützt.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION ist immer SQL_TXN_READ_COMMITTED.|  
  
 [1] atomarische Transaktionen werden vom Microsoft Access-Treiber nicht unterstützt. Beim Ausführen eines Commits für eine Transaktion mithilfe des Microsoft Access-Treibers besteht eine begrenzte Verzögerung zwischen dem Commit der Transaktion und dem Zeitpunkt, zu dem die Werte auf den Datenträger geschrieben werden. Diese Verzögerung wird durch eine Verzögerung in der Microsoft Jet-Engine festgelegt. Das Seiten Timeout ist nicht kleiner als ein Minimalwert, auch wenn die Option PageTimeout unter diesem Wert festgelegt ist. Folglich gibt es keine Garantie dafür, dass die Daten mit einem Commit stabil sind, da während der Verzögerung Änderungen vorgenommen werden können.
