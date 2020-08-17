---
description: Registrierungseinträge (Visual FoxPro-ODBC-Treiber)
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
ms.openlocfilehash: cc4c5d617590e6435d99756b159c6049551d2d69
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340346"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Registrierungseinträge (Visual FoxPro-ODBC-Treiber)
Wenn Sie den Visual FoxPro-ODBC-Treiber installieren, aktualisiert das Installationsprogramm die Registrierung Ihres Systems im Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, um einen neuen Schlüssel namens Microsoft Visual FoxPro-Treiber hinzuzufügen. Unter diesem Schlüssel werden die in der folgenden Tabelle beschriebenen Werte hinzugefügt.  
  
|Wertname|Werttyp|Wert|  
|----------------|----------------|-----------|  
|Apilevel|REG_SZ|"1"|  
|Connectfunctions|REG_SZ|"Yyn"|  
|Treiber|REG_SZ|System Pfad zur vfpodbc.dll Datei|  
|DriverODBCVer|REG_SZ|"02,50"|  
|Fileextns|REG_SZ|"*. DBF, \* . CDX, \* . f"|  
|Fileusage|REG_SZ|"1"|  
|Einrichten|REG_SZ|System Pfad zur vfpodbc.dll Datei|  
|Sqllevel|REG_SZ|"0"|  
  
 Das Installationsprogramm fügt auch den Schlüssel "Visual FoxPro-Dateien", der den standardmäßigen Visual FoxPro-Treiber darstellt, dem HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini Schlüssel Ihres Systems hinzu. Unter diesem Schlüssel werden die in der folgenden Tabelle beschriebenen Werte durch das Installationsprogramm hinzugefügt.  
  
|Wertname|Werttyp|Wert|  
|----------------|----------------|-----------|  
|Treiber|REG_SZ|System Pfad zur vfpodbc.dll Datei|  
  
 Jedes Mal, wenn Sie eine Visual FoxPro-ODBC-Datenquelle zu ihrer ODBC-Konfiguration hinzufügen, wird ein neuer Schlüssel für den Namen der Datenquelle hinzugefügt. Die Werte für die Datenquelle entsprechen den Werten, die Sie im Dialogfeld **Visual FoxPro-Setup von ODBC** festgelegt haben, wie in der folgenden Tabelle aufgeführt.  
  
|Wertname (Schlüsselwort)|Werttyp|Wert|  
|----------------------------|----------------|-----------|  
|Sortieren|REG_SQ|Jede unterstützte Sortierungs Sequenz|  
|Beschreibung|REG_SZ|Benutzer Beschreibung der Datenquelle|  
|Treiber||System Pfad zur vfpodbc.dll Datei|  
|Exklusiv||Ja oder Nein|  
|Backgroundfetch||Ja oder Nein|  
|SourceDB|REG_SZ|Der Pfad zu. DBC-Datei|  
|SourceType|REG_SZ|"DBC" oder "DBF"|  
  
 Sie sollten nicht direkt auf diese Informationen zugreifen. alle Verwaltungsaufgaben werden vom ODBC-Administrator verarbeitet, wenn Sie eine Datenquelle hinzufügen, ändern oder löschen.  
  
 Sie können einige dieser Schlüsselwörter und Werte als Parameter in der [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) ODBC-API-Funktion verwenden.
