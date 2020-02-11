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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1a33d449396b5cc80e8d29767708d2f9f16736fa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987849"
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Zugriffs Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Anwendungsentwickler sollten nach Treiber definierten Spalten suchen, beginnend am Ende des Resultsets, und den Vorgang rückwärts fortsetzen.  
  
|Column|Kommentare|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT oder SQL_RESULT_COL|  
|Ordnungszahl|Dies ist eine Treiber spezifische Spalte, die am Ende des Resultsets zurückgegeben wird. Der SQL-Typ der Spalte ist eine ganze Zahl.|
