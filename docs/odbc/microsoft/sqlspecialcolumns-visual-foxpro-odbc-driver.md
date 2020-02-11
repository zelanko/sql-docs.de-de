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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093089"
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: Ebene 1  
  
 Ruft den optimalen Satz von Spalten ab, der eine Zeile in der Tabelle eindeutig identifiziert.  
  
 Der Visual FoxPro-ODBC-Treiber gibt die Spalten zurück, die den Primärschlüssel für die FoxPro-Tabelle bilden. (Siehe [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) Bei einem Aufruf, bei dem *fcoltype* auf SQL_ROWVER festgelegt ist, werden keine Spalten zurückgegeben. **SQLSpecialColumns** funktioniert nur für Datenquellen, bei denen es sich um Daten [Banken](../../odbc/microsoft/visual-foxpro-terminology.md)handelt.  
  
 Weitere Informationen finden Sie unter [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) in der *ODBC Programmer es Reference*.
