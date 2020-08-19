---
description: SQLPrimaryKeys (Visual FoxPro-ODBC-Treiber)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96b333e10c7000a8a44e957e33d0c84a3b004f43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483343"
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
