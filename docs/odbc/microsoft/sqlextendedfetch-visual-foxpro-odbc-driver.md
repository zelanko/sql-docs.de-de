---
title: SQLExtendedFetch (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d58d7885eed1a8ed0611470f29cb24e8072afcb9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053801"
---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: Vollständig  
  
 ODBC-API-Übereinstimmung: Ebene 2  
  
 Ähnlich wie [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) jedoch mehrere Zeilen, die über ein Array für jede Spalte zurückgegeben. Das Resultset ist vorwärts bildlauffähige und rückwärts-scrollfähig des Cursors definiert ist, werden statische, nicht nur vorwärts gerichteten vorgenommen werden kann.  
  
 Standardmäßig gibt der Visual FoxPro-ODBC-Treiber keine Zeilen, die in einer FoxPro-Tabelle als gelöscht markiert zurück. Zeilen zum Löschen markiert, aber noch nicht aus einer Tabelle entfernt wurden, sind nicht in der resultsetcursor enthalten. Sie können dieses Verhalten ändern, indem Sie mit der [SET DELETED](../../odbc/microsoft/set-deleted-command.md) Befehl.  
  
 Weitere Informationen finden Sie unter [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md) in die *ODBC Programmer's Reference*.
