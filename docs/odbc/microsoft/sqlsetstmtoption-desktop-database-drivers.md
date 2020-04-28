---
title: SQLSetStmtOption (Desktop-Datenbanktreiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69b386aee3f95fd047f72510dce7658130ac7aa5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299410"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (Desktop-Datenbanktreiber)

|*fOption*|Kommentare|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Die asynchrone Verarbeitung wird nicht unterstützt. Die SQL_ASYNC_ENABLE-Option "f" gibt SQLSTATE S1C00 (Treiber nicht fähig) zurück.|  
|SQL_KEYSET_SIZE|Die einzige gültige Keysetgröße ist 0, da gemischte und dynamische Cursor nicht unterstützt werden. Wenn dieser Wert auf eine andere Zahl festgelegt ist, wird er in 0 geändert, und der-Rückruf gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01s02 (Optionswert geändert) zurück.|  
|SQL_MAX_ROWS|Die einzige gültige Rowsetgröße ist 0, da die Desktop-Datenbanktreiber das Einschränken der Anzahl der zurückgegebenen Zeilen nicht unterstützen. Wenn dieser Wert auf eine andere Zahl festgelegt ist, wird er in 0 geändert, und der-Rückruf gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01s02 (Optionswert geändert) zurück.|  
|SQL_QUERY_TIMEOUT|Nicht unterstützt.|  
|SQL_ROW_NUMBER|Nicht unterstützt.|  
|SQL_SIMULATE_CURSOR|Nicht unterstützt.|
