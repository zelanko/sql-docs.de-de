---
title: SQLTransact (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 1581cb7ecc694dc9adcbb03d83cf73a6ba41dbed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270043"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Vollständig  
  
 ODBC-API-Übereinstimmung: Kern-Ebene  
  
 Fordert einen Commit oder Rollback-Vorgang für alle aktiven Vorgänge für alle Anweisungshandles (*Befehls beschäftigt*s) für alle Verbindungen, die das Umgebungshandle zugeordnet oder eine Verbindung zugeordnet ist *Henv*. **SQLTransact** funktioniert nur für Datenquellen [Datenbanken](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Die Transaktion bleibt aktiv, wenn ein Commit im manuellen Modus fehlschlägt, Sie können auch ein Rollback der Transaktion oder wiederholen den Commitvorgang. Wenn ein Commitvorgang im Transaktionsmodus für automatische fehlschlägt, wird die Transaktion automatisch zurückgesetzt; die Transaktion darf nicht inaktiv sein.  
  
 Weitere Informationen finden Sie unter [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) in die *ODBC Programmer's Reference*.
