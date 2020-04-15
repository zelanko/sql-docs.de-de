---
title: SQLTransact (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3910f24578bcbc409a84573e994c0680ed5949b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299220"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Kernebene  
  
 Fordert einen Commit- oder Rollbackvorgang für alle aktiven Vorgänge für alle Anweisungshandles *(hstmt*s) an, die einer Verbindung zugeordnet sind, oder für alle Verbindungen, die mit dem Umgebungshandle, *henv*, verknüpft sind. **SQLTransact** funktioniert nur für Datenquellen, die [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md)sind.  
  
 Wenn ein Commit im manuellen Modus fehlschlägt, bleibt die Transaktion aktiv. Sie können einen Rollback für die Transaktion oder einen erneuten Vorgang des Commits auswählen. Wenn ein Commit-Vorgang im automatischen Transaktionsmodus fehlschlägt, wird ein automatischer Rollback für die Transaktion ausgeführt. Die Transaktion kann nicht inaktiv sein.  
  
 Weitere Informationen finden Sie unter [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) in der *ODBC-Programmiererreferenz*.
