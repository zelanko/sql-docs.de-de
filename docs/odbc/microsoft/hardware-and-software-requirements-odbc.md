---
description: Hardware- und Softwareanforderungen (ODBC)
title: Hardware-und Software Anforderungen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- hardware requirements [ODBC], desktop database drivers
- software requirements [ODBC], desktop database drivers
- system requirements [ODBC], desktop database drivers
- requirements [ODBC], desktop database drivers
ms.assetid: 6df2e9cd-de10-4629-97bd-32f2782616c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a0f88c8877161122c11fb65bcdb62fd4e7b684c3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412486"
---
# <a name="hardware-and-software-requirements-odbc"></a>Hardware- und Softwareanforderungen (ODBC)
In diesem Thema werden die Anforderungen für die Verwendung der ODBC Desktop-Datenbanktreiber aufgeführt.  
  
## <a name="hardware-requirements"></a>Hardwareanforderungen  
 Um die ODBC Desktop-Datenbanktreiber zu verwenden, benötigen Sie Folgendes:  
  
-   Ein IBM-kompatibler persönlicher Computer.  
  
-   Eine Festplatte mit 6 MB freiem Speicherplatz.  
  
-   Mindestens 16 MB Arbeitsspeicher (RAM).  
  
## <a name="software-requirements"></a>Softwareanforderungen  
 Für den Zugriff auf Daten mit einem ODBC-Treiber benötigen Sie Folgendes:  
  
-   Der ODBC-Treiber.  
  
-   Der 32-Bit-ODBC-Treiber-Manager, Version 3,51 oder höher (Odbc32.dll).  
  
-   Microsoft Windows 95 oder höher oder Windows NT 4,0 oder Windows 2000.  
  
-   Eine Stapelgröße von mindestens 20 KB für eine Anwendung, die einen Microsoft ODBC-Treiber verwendet.  
  
 Bei Verwendung von Microsoft Windows NT 4,0 oder Windows 2000 ist der 32-Bit-Treiber Thread sicher, aber nur durch die Verwendung eines globalen Semaphors, der den Zugriff auf den Treiber steuert. Die gleichzeitige Verwendung des Treibers ist unter Windows NT sehr eingeschränkt. Der gesamte Zugriff auf die Jet-ISAM-Schicht wird für alle Anwendungen, die das Microsoft Jet-Modul verwenden, mit einem einzigen Thread versehen.  
  
 Wenn Sie mehrere 16-Bit-Anwendungen unter Windows unter Windows (WOW) auf Microsoft Windows NT 4,0 ausführen, müssen die Anwendungen in separaten Speicherbereichen ausgeführt werden. (Der gleiche Speicherplatz kann nicht verwendet werden, da ODBC nicht mehrere Umgebungen im gleichen Prozess unterstützt.) Um eine Anwendung in einem separaten Speicherbereich auszuführen, wählen Sie das Anwendungssymbol im Programm-Manager aus, öffnen Sie das Menü **Datei** , klicken Sie auf **Eigenschaften**, und klicken Sie dann auf **in getrennter Speicherbereich ausführen**.  
  
 Die Verwendung dieser Treiber mit 16-Bit-Anwendungen unter Windows 95 wird nicht unterstützt.  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>Treiber spezifische Hardware-und Software Anforderungen  
  
-   MicrosoftAccess und dbasedrivers erfordern möglicherweise Änderungen an den Autoexec.bat-oder Config.sys Dateien.
