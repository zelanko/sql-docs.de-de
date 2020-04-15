---
title: SQLGetFunctions (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af7ad2368847ff271dcf81759d6fa06b8a79fb0a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298610"
---
# <a name="sqlgetfunctions-visual-foxpro-odbc-driver"></a>SQLGetFunctions (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Ebene 1  
  
 Gibt TRUE für alle unterstützten Funktionen zurück.  
  
 Der Visual FoxPro ODBC-Treiber unterstützt alle FUNKTIONEN VON ODBC API Core und Level 1. Die folgende Tabelle gibt an, ob der Treiber eine bestimmte Level 2-Funktion unterstützt.  
  
|*Funktion*|Unterstützt|  
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
  
 Weitere Informationen finden Sie unter [SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md) in der *ODBC-Programmiererreferenz*.
