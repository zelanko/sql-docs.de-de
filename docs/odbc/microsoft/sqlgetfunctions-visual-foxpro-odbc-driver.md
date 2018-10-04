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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628608"
---
# <a name="sqlgetfunctions-visual-foxpro-odbc-driver"></a>SQLGetFunctions (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: vollständige  
  
 ODBC-API-Übereinstimmung: Ebene 1  
  
 Gibt "true" für alle unterstützten Funktionen.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt alle ODBC-API-Kern und Ebene 1 Funktionen. Die folgende Tabelle gibt an, ob die Treiber eine bestimmte Ebene-2-Funktion unterstützt.  
  
|*Funktion*|Supported|  
|----------------|---------------|  
|SQL_API_SQLBROWSECONNECT|nein|  
|SQL_API_SQLCOLUMNPRIVELEGES|nein|  
|SQL_API_SQLDATASOURCES|Benutzerkontensteuerung|  
|SQL_API_SQLDESCRIBEPARAM|nein|  
|SQL_API_SQLDRIVERS|Benutzerkontensteuerung|  
|SQL_API_SQLEXTENDEDFETCH|Benutzerkontensteuerung|  
|SQL_API_SQLFOREIGNKEYS|nein|  
|SQL_API_SQLMORERESULTS|Benutzerkontensteuerung|  
|SQL_API_SQLNATIVESQL|nein|  
|SQL_API_SQLNUMPARAMS|Benutzerkontensteuerung|  
|SQL_API_SQLPARAMOPTIONS|Benutzerkontensteuerung|  
|SQL_API_SQLPRIMARYKEYS|Benutzerkontensteuerung|  
|SQL_API_SQLPROCEDURECOLUMNS|nein|  
|SQL_API_SQLPROCEDURES|nein|  
|SQL_API_SQLSETPOS|Benutzerkontensteuerung|  
|SQL_API_SQLSETSCROLLOPTIONS|Benutzerkontensteuerung|  
|SQL_API_SQLTABLEPRIVILEGES|nein|  
  
 Weitere Informationen finden Sie unter [SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md) in die *ODBC Programmer's Reference*.
