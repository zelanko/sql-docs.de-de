---
description: SQLSpecialColumns (Visual FoxPro-ODBC-Treiber)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e83568c8370b56decb7c3f7c90cda443b88a72a7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421604"
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: Ebene 1  
  
 Ruft den optimalen Satz von Spalten ab, der eine Zeile in der Tabelle eindeutig identifiziert.  
  
 Der Visual FoxPro-ODBC-Treiber gibt die Spalten zurück, die den Primärschlüssel für die FoxPro-Tabelle bilden. (Siehe [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) Bei einem Aufruf, bei dem *fcoltype* auf SQL_ROWVER festgelegt ist, werden keine Spalten zurückgegeben. **SQLSpecialColumns** funktioniert nur für Datenquellen, bei denen es sich um Daten [Banken](../../odbc/microsoft/visual-foxpro-terminology.md)handelt.  
  
 Weitere Informationen finden Sie unter [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) in der *ODBC Programmer es Reference*.
