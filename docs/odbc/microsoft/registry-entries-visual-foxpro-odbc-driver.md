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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de287802693adb18e39509fdc0e7577d05984949
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47766548"
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Registrierungseinträge (Visual FoxPro-ODBC-Treiber)
Bei der Installation der Visual FoxPro-ODBC-Treiber aktualisiert das Installationsprogramm der Registrierung Ihres Systems, unter dem Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, um einen neuen Schlüssel namens Microsoft Visual FoxPro-Treiber hinzuzufügen. Unter diesem Schlüssel werden in der folgenden Tabelle beschriebenen Werte hinzugefügt.  
  
|Wertname|Werttyp|value|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|"1"|  
|ConnectFunctions|REG_SZ|"YYN"|  
|Treiber|REG_SZ|Systempfad zur Datei vfpodbc.dll|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|"*.dbf,\*.cdx,\*.fpt"|  
|FileUsage|REG_SZ|"1"|  
|Setup|REG_SZ|Systempfad zur Datei vfpodbc.dll|  
|SQLLevel|REG_SZ|"0"|  
  
 Das Installationsprogramm fügt auch den Schlüssel "Visual FoxPro-Dateien", den standardmäßigen Visual FoxPro-Treiber des Systems HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini Schlüssel darstellt. Unter diesem Schlüssel fügt das Installationsprogramm die Werte in der folgenden Tabelle beschrieben.  
  
|Wertname|Werttyp|value|  
|----------------|----------------|-----------|  
|Treiber|REG_SZ|Systempfad zur Datei vfpodbc.dll|  
  
 Bei jedem eine Visual FoxPro-ODBC-Datenquelle Ihrer ODBC-Konfiguration hinzufügen wird ein neuer Schlüssel hinzugefügt, die für diesen Namen Datenquelle. Die Werte für die Datenquelle entsprechen Werten, die Sie, in Festlegen der **ODBC-Visual FoxPro-Setup** Dialogfeld wie in der folgenden Tabelle aufgeführt.  
  
|Name des Werts (Schlüsselwort)|Werttyp|value|  
|----------------------------|----------------|-----------|  
|Sortieren|REG_SQ|Alle unterstützten Sortierreihenfolge|  
|Description|REG_SZ|Benutzer-Beschreibung der Datenquelle|  
|Treiber||Systempfad zur Datei vfpodbc.dll|  
|Exclusive||Ja oder Nein|  
|BackgroundFetch||Ja oder Nein|  
|SourceDB|REG_SZ|Pfad zu. DBC-Datei|  
|SourceType|REG_SZ|"DBC" oder "DBF"|  
  
 Sie sollten diese Informationen nicht direkt zugreifen. Verwaltung der Registrierung erfolgt durch den ODBC-Administrator, wenn Sie Daten hinzufügen, ändern oder einer Datenquelle löschen.  
  
 Sie können einige dieser Schlüsselwörter und -Werte als Parameter in der [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) ODBC API-Funktion.
