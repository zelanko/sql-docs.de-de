---
title: SQLDriverConnect (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e270f8c9be42dc109adeaa49acb84f29f2b9511
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307091"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: Ebene 1  
  
 Stellt eine Verbindung mit einer vorhandenen Datenquelle her, bei der es sich entweder um eine [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md) oder um ein Verzeichnis mit [freien Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)handeln kann. Die ODBC-Attribut Schlüsselwörter UID und PWD werden ignoriert. In der folgenden Tabelle sind die zusätzlichen unterstützten Attribut Schlüsselwörter aufgeführt.  
  
|ODBC-Attribut Schlüsselwort|Attributwert|  
|----------------------------|---------------------|  
|DSN||  
|UID|Wird vom Visual FoxPro-ODBC-Treiber ignoriert, es wird jedoch kein Fehler generiert.|  
|PWD|Wird vom Visual FoxPro-ODBC-Treiber ignoriert, es wird jedoch kein Fehler generiert.|  
|Treiber|Der Name und Speicherort des Visual FoxPro-ODBC-Treibers. wird vom Treiber-Manager implementiert.|  
  
|Visual FoxPro-ODBC-Treiber Attribut-Schlüsselwort|Attributwert|  
|-------------------------------------------------|---------------------|  
|Backgroundfetch|"Yes" oder "No"|  
|Sortieren|"Computer" oder eine andere Sortierreihenfolge. Eine Liste der unterstützten Sortierungs Sequenzen finden Sie unter [SET COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|BESCHREIBUNG||  
|Exklusiv|"Yes" oder "No"|  
|SourceDB|Ein voll qualifizierter Pfad zu einem Verzeichnis, das 0 (null) oder mehr [freie Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)enthält, oder der absolute Pfad und Dateiname für eine [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SourceType|"DBC" oder "DBF"|  
|Version||  
  
 Wenn der Name der Datenquelle nicht angegeben wird, fordert der Treiber-Manager den Benutzer zur Eingabe der Informationen auf (abhängig von der Einstellung des Argument " *sdrivercompletion* ") und wird dann fortgesetzt. Wenn weitere Informationen erforderlich sind, zeigt der Visual FoxPro-ODBC-Treiber das Dialogfeld für die Eingabeaufforderung an.  
  
 Weitere Informationen finden Sie unter [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) in der *ODBC Programmer es Reference*.
