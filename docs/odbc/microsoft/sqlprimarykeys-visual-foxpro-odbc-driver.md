---
title: SQLPrimaryKeys (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
ms.openlocfilehash: 83631d22bd07017c4eba8f6af171443ab8c76d9c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301545"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Ebene 2  
  
 Gibt die Spaltennamen zurück, aus denen der Primärschlüssel für eine Tabelle besteht. Die Visual FoxPro ODBC-Treiberimplementierung von **SQLPrimaryKeys** verhält sich wie folgt:  
  
-   Ignoriert die Argumente *szTableOwner* und *cbTableOwner.*  
  
-   Funktioniert nur für Datenquellen, die [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md)sind. Der Treiber gibt den Fehler "Driver unterstützt diese Funktion nicht" zurück, wenn die Datenquelle ein Verzeichnis [freier Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)ist.  
  
 Weitere Informationen finden Sie unter [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) in der *ODBC-Programmiererreferenz*.
