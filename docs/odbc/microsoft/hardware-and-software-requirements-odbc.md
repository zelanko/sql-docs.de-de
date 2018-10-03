---
title: Hardware- und Softwareanforderungen (ODBC) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b3f40621645aad2d1e52cb0a89baa8ff29b01446
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680658"
---
# <a name="hardware-and-software-requirements-odbc"></a>Hardware- und Softwareanforderungen (ODBC)
Dieses Thema enthält Anforderungen für die Verwendung der ODBC-Desktop-Datenbanktreiber.  
  
## <a name="hardware-requirements"></a>Hardwareanforderungen  
 Um die ODBC-Desktop-Datenbanktreiber verwenden zu können, benötigen Sie Folgendes:  
  
-   Ein IBM-kompatibler Computer.  
  
-   Eine Festplatte mit 6 MB an freiem Festplattenspeicher verfügbar ist.  
  
-   Mindestens 16 MB Arbeitsspeicher (RAM).  
  
## <a name="software-requirements"></a>Softwareanforderungen  
 Um Daten mit einem ODBC-Treiber zuzugreifen, benötigen Sie Folgendes:  
  
-   Der ODBC-Treiber.  
  
-   Der 32-Bit-ODBC-Treiber-Manager, Version 3.51 oder höher (Datei "ODBC32.dll").  
  
-   Microsoft Windows 95 oder höher, Windows NT 4.0 oder Windows 2000.  
  
-   Ein Stapelgröße von mindestens 20 KB für eine Anwendung mithilfe eines Microsoft ODBC-Treibers.  
  
 Wenn Microsoft Windows NT 4.0 oder Windows 2000 verwenden, ist der 32-Bit-Treiber threadsicher, aber nur durch die Verwendung von einem globalen Semaphore, dass die Steuerung des Zugriffs auf den Treiber. Gleichzeitige Verwendung des Treibers ist sehr begrenzt unter Windows NT. Alle Zugriffe auf die Jet-ISAM-Ebene werden Singlethread für alle Anwendungen, die mithilfe der Microsoft Jet-Engine.  
  
 Wenn mehrere 16-Bit-Anwendungen auf Windows on Windows (WOW) unter Microsoft Windows NT 4.0 ausgeführt werden soll, müssen die Anwendungen in unterschiedlichen Speicherbereichen ausgeführt werden. (Die gleichen Speicherbereich kann nicht verwendet werden, da ODBC keine mehrere Umgebungen im gleichen Prozess unterstützt.) Um eine Anwendung in einem separaten Speicher ausführen, wählen Sie auf das Symbol der Anwendung im Programm-Manager öffnen die **Datei** Menü **Eigenschaften**, und klicken Sie dann auf **In separaten Speicher ausführen Speicherplatz**.  
  
 Die Verwendung dieser Treiber von 16-Bit-Anwendungen unter Windows 95 wird nicht unterstützt.  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>Treiberspezifische Hardware- und Softwareanforderungen  
  
-   Die MicrosoftAccess und dBASEdrivers kann Änderungen in den Dateien Autoexec erforderlich.
