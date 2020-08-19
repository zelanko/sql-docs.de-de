---
description: SQLSetStmtOption (Desktop-Datenbanktreiber)
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
ms.openlocfilehash: 0696ee98dd88f1c23120ef1d96c6e8d93751f76e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449152"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (Desktop-Datenbanktreiber)

|*fOption*|Kommentare|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Die asynchrone Verarbeitung wird nicht unterstützt. Die SQL_ASYNC_ENABLE-Option "f" gibt SQLSTATE S1C00 (Treiber nicht fähig) zurück.|  
|SQL_KEYSET_SIZE|Die einzige gültige Keysetgröße ist 0, da gemischte und dynamische Cursor nicht unterstützt werden. Wenn dieser Wert auf eine andere Zahl festgelegt ist, wird er in 0 geändert, und der-Rückruf gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01s02 (Optionswert geändert) zurück.|  
|SQL_MAX_ROWS|Die einzige gültige Rowsetgröße ist 0, da die Desktop-Datenbanktreiber das Einschränken der Anzahl der zurückgegebenen Zeilen nicht unterstützen. Wenn dieser Wert auf eine andere Zahl festgelegt ist, wird er in 0 geändert, und der-Rückruf gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01s02 (Optionswert geändert) zurück.|  
|SQL_QUERY_TIMEOUT|Wird nicht unterstützt.|  
|SQL_ROW_NUMBER|Wird nicht unterstützt.|  
|SQL_SIMULATE_CURSOR|Wird nicht unterstützt.|
