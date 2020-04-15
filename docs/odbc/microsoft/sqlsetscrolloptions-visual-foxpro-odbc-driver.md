---
title: SQLSetScrollOptions (Visual FoxPro ODBC-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19051fc83466bc40d72c029089cfe6ec45c20a08
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299420"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: Teilweise  
  
 ODBC-API-Konformität: Ebene 2  
  
 Legt Optionen fest, die das Verhalten von Cursorn steuern, die einem Anweisungshandle, *hstmt*, zugeordnet sind.  
  
 Der Visual FoxPro ODBC-Treiber unterstützt nur SQL_CONCUR_READ_ONLY. Der *fConcurrency-Wert* SQL_CONCUR_ROWVER wird nicht unterstützt. Der Treiber konvertiert SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC und SQL_CURSOR_KEYSET_DRIVEN mit ODBC_01S02 in SQL_SCROLL_STATIC.  
  
 Weitere Informationen finden Sie unter [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) in der *ODBC-Programmiererreferenz*.
