---
title: SQLSpecialColumns (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
ms.openlocfilehash: 96b439674c8bda3494b4cefd0c1118602b537cd0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299380"
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Ebene 1  
  
 Ruft den optimalen Satz von Spalten ab, der eine Zeile in der Tabelle eindeutig identifiziert.  
  
 Der Visual FoxPro ODBC-Treiber gibt die Spalten zurück, aus denen sich der Primärschlüssel in der FoxPro-Tabelle zusammensetzt. (Siehe [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) Wenn der Aufgerufene mit *fColType* auf SQL_ROWVER festgelegt ist, werden keine Spalten zurückgegeben. **SQLSpecialColumns** funktioniert nur für Datenquellen, die [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md)sind.  
  
 Weitere Informationen finden Sie unter [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) in der *ODBC-Programmiererreferenz*.
