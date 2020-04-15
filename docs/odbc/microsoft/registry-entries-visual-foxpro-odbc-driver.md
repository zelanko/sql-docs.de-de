---
title: Registrierungseinträge (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304837"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Registrierungseinträge (Visual FoxPro-ODBC-Treiber)
Wenn Sie den Visual FoxPro ODBC-Treiber installieren, aktualisiert das Installationsprogramm die Registrierung Ihres Systems im Registrierungsschlüssel HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBCInst.ini, um einen neuen Schlüssel namens Microsoft Visual FoxPro-Treiber hinzuzufügen. Unter diesem Schlüssel werden die in der folgenden Tabelle beschriebenen Werte hinzugefügt.  
  
|Wertname|Werttyp|Wert|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|„1“|  
|ConnectFunctions|REG_SZ|"YYN"|  
|Treiber|REG_SZ|Systempfad zur Datei vfpodbc.dll|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|"*.dbf,\*.cdx,\*.fpt"|  
|FileUsage|REG_SZ|„1“|  
|Einrichten|REG_SZ|Systempfad zur Datei vfpodbc.dll|  
|SQLLevel|REG_SZ|"0"|  
  
 Das Installationsprogramm fügt auch den Schlüssel "Visual FoxPro-Dateien", der den standardmäßigen Visual FoxPro-Treiber darstellt, zum HKEY_CURRENT_USER-SOFTWARE-ODBC-Odbc.ini-Schlüssel Ihres Systems hinzu. Unter diesem Schlüssel fügt das Installationsprogramm die in der folgenden Tabelle beschriebenen Werte hinzu.  
  
|Wertname|Werttyp|Wert|  
|----------------|----------------|-----------|  
|Treiber|REG_SZ|Systempfad zur Datei vfpodbc.dll|  
  
 Jedes Mal, wenn Sie Ihrer ODBC-Konfiguration eine Visual FoxPro ODBC-Datenquelle hinzufügen, wird ein neuer Schlüssel für diesen Datenquellennamen hinzugefügt. Die Werte für die Datenquelle entsprechen den Werten, die Sie im Dialogfeld **ODBC Visual FoxPro Setup** festgelegt haben, wie in der folgenden Tabelle aufgeführt.  
  
|Wertname (Schlüsselwort)|Werttyp|Wert|  
|----------------------------|----------------|-----------|  
|Sortieren|REG_SQ|Jede unterstützte Sortiersequenz|  
|Beschreibung|REG_SZ|Benutzerbeschreibung der Datenquelle|  
|Treiber||Systempfad zur Datei vfpodbc.dll|  
|Exklusiv||Ja oder Nein|  
|BackgroundFetch||Ja oder Nein|  
|SourceDB|REG_SZ|Pfad zu . DBC-Datei|  
|SourceType|REG_SZ|"DBC" oder "DBF"|  
  
 Sie sollten nicht direkt auf diese Informationen zugreifen; Jede Verwaltung der Registrierung wird vom ODBC-Administrator verwaltet, wenn Sie eine Datenquelle hinzufügen, ändern oder löschen.  
  
 Sie können einige dieser Schlüsselwörter und Werte als Parameter in der [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) ODBC-API-Funktion verwenden.
