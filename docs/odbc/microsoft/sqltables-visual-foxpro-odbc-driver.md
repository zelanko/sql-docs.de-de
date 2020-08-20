---
description: SQLTables (Visual FoxPro-ODBC-Treiber)
title: SQLTables (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 089208ab612984283e3f87c4ad03aca0ccfa2b38
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471552"
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: Ebene 1  
  
 Gibt die Liste der Tabellennamen zurück, die durch den-Parameter in der **SQLTables** -Anweisung angegeben werden. Wenn kein Parameter angegeben wird, gibt die in der aktuellen Datenquelle gespeicherten Tabellennamen zurück. Der Treiber gibt die Informationen als Resultset zurück.  
  
 Enumerationstyp Aufrufe empfangen keinen resultseteintrag für Remote Sichten oder lokale parametrisierte Sichten. Ein **SQLTables** -Befehl mit einem eindeutigen tabellenbezeichnerspezifizierer findet jedoch eine Entsprechung für eine solche Sicht, wenn Sie mit diesem Namen vorhanden ist. Dadurch kann die API verwendet werden, um vor der Erstellung einer neuen Tabelle Nachnamens Konflikten zu suchen.  
  
> [!NOTE]  
>  Der Visual FoxPro-ODBC-Treiber unterscheidet sich zwischen [Datenbanktabellen](../../odbc/microsoft/visual-foxpro-terminology.md) und [freien Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md), auch wenn beide Tabellentypen im selben Verzeichnis auf dem System gespeichert sind. Wenn es sich bei der Datenquelle um ein Verzeichnis mit freien Tabellen handelt, werden die Namen von Tabellen, die einer Datenbank zugeordnet sind, vom Visual FoxPro-ODBC-Treiber nicht katalogisiert oder zurückgegeben.  
  
 Weitere Informationen finden Sie unter [SQLTables](../../odbc/reference/syntax/sqltables-function.md) in der *ODBC Programmer es Reference*.
