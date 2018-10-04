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
manager: craigg
ms.openlocfilehash: 3eeafa338fea31741609e6f9a9b32a4128ebd87d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765608"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: vollständige  
  
 ODBC-API-Übereinstimmung: Auf Ebene 2  
  
 Gibt den Namen der Spalten, die den Primärschlüssel für eine Tabelle bilden. Der Visual FoxPro-ODBC-Treiber-Implementierung des **SQLPrimaryKeys** verhält sich wie folgt:  
  
-   Ignoriert die *SzTableOwner* und *CbTableOwner* Argumente.  
  
-   Funktioniert nur für Datenquellen [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md). Gibt der Treiber dem Fehler "Driver unterstützt diese Funktion nicht" ist die Datenquelle in einem Verzeichnis [kostenlose Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Weitere Informationen finden Sie unter [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) in die *ODBC Programmer's Reference*.
