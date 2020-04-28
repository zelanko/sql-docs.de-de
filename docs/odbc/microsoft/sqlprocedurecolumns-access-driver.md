---
title: Sqlprocedurecolrens (Access-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLProcedureColumns
- SQLProcedureColumns function [ODBC], Access Driver
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be17776ac6b6879140a7c57bede1b3cb539d97be
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299460"
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Zugriffs Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Anwendungsentwickler sollten nach Treiber definierten Spalten suchen, beginnend am Ende des Resultsets, und den Vorgang rückwärts fortsetzen.  
  
|Column|Kommentare|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT oder SQL_RESULT_COL|  
|Ordnungszahl|Dies ist eine Treiber spezifische Spalte, die am Ende des Resultsets zurückgegeben wird. Der SQL-Typ der Spalte ist eine ganze Zahl.|
