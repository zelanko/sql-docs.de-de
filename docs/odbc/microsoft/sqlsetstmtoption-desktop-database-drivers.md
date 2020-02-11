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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 20043c96771bf888defa2c8fbeb028aaa18f5abc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905347"
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
