---
title: Registrierungseinträge (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- registry keys [ODBC]
- Visual FoxPro ODBC driver [ODBC], registry entries
- keys [ODBC]
- FoxPro ODBC driver [ODBC], registry entries
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bd2d419a94c45a872789e095b014159b41d7c217
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304837"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Registrierungseinträge (Visual FoxPro-ODBC-Treiber)
Wenn Sie den Visual FoxPro-ODBC-Treiber installieren, aktualisiert das Installationsprogramm die Registrierung Ihres Systems im Registrierungsschlüssel HKEY_LOCAL_MACHINE \software\odbc\odbcinst.ini, um einen neuen Schlüssel namens Microsoft Visual FoxPro-Treiber hinzuzufügen. Unter diesem Schlüssel werden die in der folgenden Tabelle beschriebenen Werte hinzugefügt.  
  
|Wertname|Werttyp|Wert|  
|----------------|----------------|-----------|  
|Apilevel|REG_SZ|"1"|  
|Connectfunctions|REG_SZ|"Yyn"|  
|Treiber|REG_SZ|System Pfad zur Datei vfpodbc. dll|  
|DriverODBCVer|REG_SZ|"02,50"|  
|Fileextns|REG_SZ|"*. DBF,\*. CDX,\*. f"|  
|Fileusage|REG_SZ|"1"|  
|Setup|REG_SZ|System Pfad zur Datei vfpodbc. dll|  
|Sqllevel|REG_SZ|"0"|  
  
 Das Installationsprogramm fügt auch den Schlüssel "Visual FoxPro-Dateien", der den standardmäßigen Visual FoxPro-Treiber darstellt, dem HKEY_CURRENT_USER \software\odbc\odbc.ini-Schlüssel Ihres Systems hinzu. Unter diesem Schlüssel werden die in der folgenden Tabelle beschriebenen Werte durch das Installationsprogramm hinzugefügt.  
  
|Wertname|Werttyp|Wert|  
|----------------|----------------|-----------|  
|Treiber|REG_SZ|System Pfad zur Datei vfpodbc. dll|  
  
 Jedes Mal, wenn Sie eine Visual FoxPro-ODBC-Datenquelle zu ihrer ODBC-Konfiguration hinzufügen, wird ein neuer Schlüssel für den Namen der Datenquelle hinzugefügt. Die Werte für die Datenquelle entsprechen den Werten, die Sie im Dialogfeld **Visual FoxPro-Setup von ODBC** festgelegt haben, wie in der folgenden Tabelle aufgeführt.  
  
|Wertname (Schlüsselwort)|Werttyp|Wert|  
|----------------------------|----------------|-----------|  
|Sortieren|REG_SQ|Jede unterstützte Sortierungs Sequenz|  
|BESCHREIBUNG|REG_SZ|Benutzer Beschreibung der Datenquelle|  
|Treiber||System Pfad zur Datei vfpodbc. dll|  
|Exklusiv||Ja oder Nein|  
|Backgroundfetch||Ja oder Nein|  
|SourceDB|REG_SZ|Der Pfad zu. DBC-Datei|  
|SourceType|REG_SZ|"DBC" oder "DBF"|  
  
 Sie sollten nicht direkt auf diese Informationen zugreifen. alle Verwaltungsaufgaben werden vom ODBC-Administrator verarbeitet, wenn Sie eine Datenquelle hinzufügen, ändern oder löschen.  
  
 Sie können einige dieser Schlüsselwörter und Werte als Parameter in der [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) ODBC-API-Funktion verwenden.
