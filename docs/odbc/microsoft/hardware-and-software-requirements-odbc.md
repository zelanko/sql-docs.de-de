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
ms.openlocfilehash: 6c09ddcac1409da08fedeaf946ac7fb9f6ef668e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952443"
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
