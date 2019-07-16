---
title: SQLSpecialColumns (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b690cceecb6c9980f5d84e96bccb1b02f014c026
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093089"
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: Vollständig  
  
 ODBC-API-Übereinstimmung: Ebene 1  
  
 Ruft ab, die optimale Gruppe von Spalten, die eine Zeile in der Tabelle eindeutig identifiziert.  
  
 Der Visual FoxPro-ODBC-Treiber gibt die Spalten, aus denen der Primärschlüssel für die FoxPro-Tabelle zurück. (Finden Sie unter [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) Wenn Sie mit dem Namen *fColType* SQL_ROWVER festgelegt, werden keine Spalten zurückgegeben. **SQLSpecialColumns** funktioniert nur für Datenquellen [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Weitere Informationen finden Sie unter [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) in die *ODBC Programmer's Reference*.
