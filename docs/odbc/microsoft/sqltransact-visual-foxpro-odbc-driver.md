---
title: SQLtransact (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e554a8669b6e6e95e234a5b939477a8bb2f7b8cc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948864"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: kernstufe  
  
 Fordert einen Commit-oder Rollback-Vorgang für alle aktiven Vorgänge für alle Anweisungs Handles (*hstmt*s) an, die einer Verbindung zugeordnet sind, oder für alle Verbindungen, die dem Umgebungs Handle, *HENV*, zugeordnet sind. **SQLTransact** funktioniert nur für Datenquellen, bei denen es sich um Daten [Banken](../../odbc/microsoft/visual-foxpro-terminology.md)handelt.  
  
 Wenn ein Commit im manuellen Modus fehlschlägt, bleibt die Transaktion aktiv. Sie können für die Transaktion ein Rollback ausführen oder den Commit-Vorgang wiederholen. Wenn ein Commitvorgang im automatischen Transaktionsmodus fehlschlägt, wird für die Transaktion automatisch ein Rollback ausgeführt. die Transaktion kann nicht inaktiv sein.  
  
 Weitere Informationen finden Sie unter [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) in der *ODBC Programmer es Reference*.
