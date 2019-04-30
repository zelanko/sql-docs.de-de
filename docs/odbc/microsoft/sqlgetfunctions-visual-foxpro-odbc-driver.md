---
title: SQLGetFunctions (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8102932a-88b3-49d8-bf7a-c766f54878c0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0ae7b8eb0468dd401009ef58c83b87606b0679a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63313066"
---
# <a name="sqlgetfunctions-visual-foxpro-odbc-driver"></a>SQLGetFunctions (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Vollständig  
  
 ODBC-API-Übereinstimmung: Ebene 1  
  
 Gibt "true" für alle unterstützten Funktionen.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt alle ODBC-API-Kern und Ebene 1 Funktionen. Die folgende Tabelle gibt an, ob die Treiber eine bestimmte Ebene-2-Funktion unterstützt.  
  
|*Funktion*|Supported|  
|----------------|---------------|  
|SQL_API_SQLBROWSECONNECT|Nein|  
|SQL_API_SQLCOLUMNPRIVELEGES|Nein|  
|SQL_API_SQLDATASOURCES|Ja|  
|SQL_API_SQLDESCRIBEPARAM|Nein|  
|SQL_API_SQLDRIVERS|Ja|  
|SQL_API_SQLEXTENDEDFETCH|Ja|  
|SQL_API_SQLFOREIGNKEYS|Nein|  
|SQL_API_SQLMORERESULTS|Ja|  
|SQL_API_SQLNATIVESQL|Nein|  
|SQL_API_SQLNUMPARAMS|Ja|  
|SQL_API_SQLPARAMOPTIONS|Ja|  
|SQL_API_SQLPRIMARYKEYS|Ja|  
|SQL_API_SQLPROCEDURECOLUMNS|Nein|  
|SQL_API_SQLPROCEDURES|Nein|  
|SQL_API_SQLSETPOS|Ja|  
|SQL_API_SQLSETSCROLLOPTIONS|Ja|  
|SQL_API_SQLTABLEPRIVILEGES|Nein|  
  
 Weitere Informationen finden Sie unter [SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md) in die *ODBC Programmer's Reference*.
