---
title: SQLPrimaryKeys (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e85e60cde86c9483e69a8c43de14ef64eb914119
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030701"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: Vollständig  
  
 ODBC-API-Übereinstimmung: Ebene 2  
  
 Gibt den Namen der Spalten, die den Primärschlüssel für eine Tabelle bilden. Der Visual FoxPro-ODBC-Treiber-Implementierung des **SQLPrimaryKeys** verhält sich wie folgt:  
  
-   Ignoriert die *SzTableOwner* und *CbTableOwner* Argumente.  
  
-   Funktioniert nur für Datenquellen [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md). Gibt der Treiber dem Fehler "Driver unterstützt diese Funktion nicht" ist die Datenquelle in einem Verzeichnis [kostenlose Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Weitere Informationen finden Sie unter [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) in die *ODBC Programmer's Reference*.
