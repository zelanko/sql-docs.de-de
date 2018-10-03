---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e134b2870c4506e725f2900b83d1118e42b55d15
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828998"
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: vollständige  
  
 ODBC-API-Übereinstimmung: Ebene 1  
  
 Gibt die Liste der vom Parameter angegebenen Tabellennamen die **SQLTables** Anweisung. Wenn kein Parameter angegeben wird, gibt die Namen der Tabellen in der aktuellen Datenquelle gespeichert. Der Treiber gibt zurück, die Informationen als Resultset.  
  
 Enumeration Typs ruft erhalten einen Ergebnis Set-Eintrag für remote-Ansichten oder lokalen parametrisierte Sichten nicht. Allerdings einen Aufruf von **SQLTables** mit einer eindeutigen Tabelle Namensbezeichner findet eine Übereinstimmung mit dieser Ansicht Falls mit diesem Namen vorhanden; Dadurch wird die API zu prüfen, Namenskonflikte vor der Erstellung einer neuen Tabelle verwendet werden.  
  
> [!NOTE]  
>  Der Visual FoxPro-ODBC-Treiber unterscheidet zwischen [Datenbanktabellen](../../odbc/microsoft/visual-foxpro-terminology.md) und [kostenlose Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md), selbst wenn beide Arten von Tabellen im gleichen Verzeichnis auf Ihrem System gespeichert werden. Wenn Ihre Datenquelle ein Verzeichnis mit kostenlosen Tabellen ist, der Visual FoxPro-ODBC-Treiber Katalog oder nicht zurückgeben der Namen von Tabellen, die einer Datenbank zugeordnet sind.  
  
 Weitere Informationen finden Sie unter [SQLTables](../../odbc/reference/syntax/sqltables-function.md) in die *ODBC Programmer's Reference*.
