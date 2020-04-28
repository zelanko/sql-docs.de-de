---
title: Ermitteln installierter Oracle-Komponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], determining installed components
ms.assetid: 3b018f6a-9db0-4aa1-8ec4-afc5f76d7cad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 73a406487ea6a4e1ab00e0320923b0b276a359a6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303491"
---
# <a name="determining-installed-oracle-components"></a>Bestimmen der installierten Oracle-Komponenten
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Navigieren Sie zum Verzeichnis "\orainst" unter dem Oracle-Basisverzeichnis, um die auf Ihrem System installierten Oracle-Komponenten (und deren Versionen) zu ermitteln. Öffnen Sie eine der folgenden Textdateien: NT. RGS, Win95. RGS oder Win98. rgs.  
  
 Das Dateiformat ähnelt dem folgenden:  
  
```  
0 ntinstall     all    "orainst"  "3.3.1.0.0C"  "Oracle Installer"  
20 w32tcp80     adp80  "tcp80"    "8.0.5.0.0"   "Oracle TCP/IP Pro"  
23 w32nmp80     adp80  "nmp80"    "8.0.5.0.0"   "Oracle Named Pipe"  
26 w32util80    all    "util80"   "8.0.5.0.0"   "Oracle8 Utilities"  
34 w32rsf80     all    "rsf80"    "8.0.5.0.0"   "Required Support"  
47 w32netclt80  net80  "netc80"   "8.0.5.0.0"   "Oracle Net8 Client"  
69 w32plus80    all    "plus80"   "8.0.5.0.0"   "SQL*Plus"  
```  
  
 Die RGS-Dateien enthalten außerdem Installationsinformationen und Beschreibungen der einzelnen Komponenten.
