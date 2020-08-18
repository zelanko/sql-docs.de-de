---
description: SQLExtendedFetch (Visual FoxPro-ODBC-Treiber)
title: Sqlextendecodfetch (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b28af112-fb47-4143-b11e-3b743b2ae1b8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7f938dda4e9e474854d62c50401ee0bf91317983
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449172"
---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: Ebene 2  
  
 Ähnlich wie [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) , gibt jedoch mehrere Zeilen zurück, wobei ein Array für jede Spalte verwendet wird. Das Resultset ist vorwärts ScrollBar und kann rückwärts scrollfähig gemacht werden, wenn der Cursor als statisch und nicht vorwärts definiert ist.  
  
 Standardmäßig gibt der Visual FoxPro-ODBC-Treiber keine Zeilen zurück, die in einer FoxPro-Tabelle als gelöscht markiert sind. Zeilen, die zum Löschen markiert sind, aber noch nicht aus einer Tabelle entfernt wurden, sind im resultsetcursor nicht enthalten. Sie können dieses Verhalten ändern, indem Sie den Befehl Befehl [Löschen](../../odbc/microsoft/set-deleted-command.md) verwenden.  
  
 Weitere Informationen finden Sie unter [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md) in der *ODBC Programmer es Reference*.
