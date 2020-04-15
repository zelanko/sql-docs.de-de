---
title: SQLSetStmtOption (Desktop-Datenbanktreiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299410"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (Desktop-Datenbanktreiber)

|*fOption*|Kommentare|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Die asynchrone Verarbeitung wird nicht unterstützt. Die SQL_ASYNC_ENABLE fOption gibt SQLSTATE S1C00 zurück (Treiber nicht fähig).|  
|SQL_KEYSET_SIZE|Die einzige gültige Keysetgröße ist 0, da gemischte und dynamische Cursor nicht unterstützt werden. Wenn dieser Wert auf eine andere Zahl festgelegt ist, wird er auf 0 geändert, und der Aufruf gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01S02 (Optionswert geändert) zurück.|  
|SQL_MAX_ROWS|Die einzige gültige Rowsetgröße ist 0, da die Desktopdatenbanktreiber keine Begrenzung der Anzahl der zurückgegebenen Zeilen unterstützen. Wenn dieser Wert auf eine andere Zahl festgelegt ist, wird er auf 0 geändert, und der Aufruf gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01S02 (Optionswert geändert) zurück.|  
|SQL_QUERY_TIMEOUT|Wird nicht unterstützt.|  
|SQL_ROW_NUMBER|Wird nicht unterstützt.|  
|SQL_SIMULATE_CURSOR|Wird nicht unterstützt.|
