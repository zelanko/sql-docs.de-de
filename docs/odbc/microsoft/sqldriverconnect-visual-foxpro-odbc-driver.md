---
title: SQLDriverConnect (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307091"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Ebene 1  
  
 Stellt eine Verbindung zu einer vorhandenen Datenquelle her, die entweder eine [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md) oder ein Verzeichnis [freier Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)sein kann. Die ODBC-Attributschlüsselwörter UID und PWD werden ignoriert. In der folgenden Tabelle sind die zusätzlichen unterstützten Attributschlüsselwörter aufgeführt.  
  
|ODBC-Attributschlüsselwort|Attributwert|  
|----------------------------|---------------------|  
|DSN||  
|UID|Vom Visual FoxPro ODBC-Treiber ignoriert, generiert jedoch keinen Fehler.|  
|PWD|Vom Visual FoxPro ODBC-Treiber ignoriert, generiert jedoch keinen Fehler.|  
|Treiber|Der Name und der Speicherort des Visual FoxPro ODBC-Treibers; vom Treiber-Manager implementiert.|  
  
|Visual FoxPro ODBC-Treiberattributschlüsselwort|Attributwert|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|"Ja" oder "Nein"|  
|Sortieren|"Maschine" oder andere Sortierreihenfolge. Eine Liste der unterstützten Sortiersequenzen finden Sie unter [SET COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Beschreibung||  
|Exklusiv|"Ja" oder "Nein"|  
|SourceDB|Ein vollqualifizierter Pfad zu einem Verzeichnis, das null oder mehr [freie Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)oder den absoluten Pfad und Dateinamen für eine [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md)enthält.|  
|SourceType|"DBC" oder "DBF"|  
|Version||  
  
 Wenn der Datenquellenname nicht angegeben ist, fordert der Treiber-Manager den Benutzer zur Eingabe der Informationen auf (abhängig von der Einstellung des *fDriverCompletion-Arguments)* und fährt dann fort. Wenn weitere Informationen erforderlich sind, zeigt der Visual FoxPro ODBC-Treiber das Eingabeaufforderungsdialogfeld an.  
  
 Weitere Informationen finden Sie unter [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) in der *ODBC-Programmiererreferenz*.
