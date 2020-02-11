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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030701"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: Ebene 2  
  
 Gibt die Spaltennamen zurück, die den Primärschlüssel für eine Tabelle bilden. Die Implementierung des Visual FoxPro-ODBC-Treibers von **SQLPrimaryKeys** verhält sich wie folgt:  
  
-   Ignoriert das *sztableowner* -Argument und das *cbtableowner* -Argument.  
  
-   Kann nur für Datenbanken verwendet werden, die Daten [Banken](../../odbc/microsoft/visual-foxpro-terminology.md)sind. Der Treiber gibt den Fehler "Treiber wird diese Funktion nicht unterstützt" zurück, wenn es sich bei der Datenquelle um ein Verzeichnis mit [freien Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)handelt.  
  
 Weitere Informationen finden Sie unter [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) in der *ODBC Programmer es Reference*.
