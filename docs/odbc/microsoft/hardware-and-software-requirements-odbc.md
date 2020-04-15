---
title: Hardware- und Softwareanforderungen (ODBC) | Microsoft Docs
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
ms.openlocfilehash: fe69775e379e9a9d661b4ddf81e577b738fcf34d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295240"
---
# <a name="hardware-and-software-requirements-odbc"></a>Hardware- und Softwareanforderungen (ODBC)
In diesem Thema werden die Anforderungen für die Verwendung der ODBC Desktop-Datenbanktreiber aufgeführt.  
  
## <a name="hardware-requirements"></a>Hardwareanforderungen  
 Um die ODBC Desktop-Datenbanktreiber verwenden zu können, benötigen Sie Folgendes:  
  
-   Ein IBM-kompatibler PC.  
  
-   Eine Festplatte mit 6 MB freiem Speicherplatz.  
  
-   Mindestens 16 MB Arbeitsspeicher (RAM) mit zu zufälligem Zugriff.  
  
## <a name="software-requirements"></a>Softwareanforderungen  
 Um mit einem ODBC-Treiber auf Daten zuzugreifen, benötigen Sie Folgendes:  
  
-   Der ODBC-Treiber.  
  
-   Der 32-Bit ODBC Driver Manager, Version 3.51 oder neuer (Odbc32.dll).  
  
-   Microsoft Windows 95 oder höher oder Windows NT 4.0 oder Windows 2000.  
  
-   Eine Stapelgröße von mindestens 20 KB für eine Anwendung, die einen Microsoft ODBC-Treiber verwendet.  
  
 Bei Verwendung von Microsoft Windows NT 4.0 oder Windows 2000 ist der 32-Bit-Treiber threadsicher, jedoch nur durch die Verwendung eines globalen Semaphors, das den Zugriff auf den Treiber steuert. Die gleichzeitige Verwendung des Treibers ist unter Windows NT sehr eingeschränkt. Der gesamte Zugriff auf die Jet ISAM-Schicht wird für alle Anwendungen, die das Microsoft Jet-Modul verwenden, ein threadiert.  
  
 Wenn mehrere 16-Bit-Anwendungen unter Windows unter Windows (WOW) unter Microsoft Windows NT 4.0 ausgeführt werden, müssen die Anwendungen in separaten Arbeitsspeichern ausgeführt werden. (Derselbe Speicherplatz kann nicht verwendet werden, da ODBC mehrere Umgebungen im gleichen Prozess nicht unterstützt.) Um eine Anwendung in einem separaten Speicherbereich auszuführen, wählen Sie das Symbol der Anwendung im Programm-Manager aus, öffnen Sie das **Menü Datei** und klicken Sie auf **Eigenschaften**, und klicken Sie dann auf Ausführen im **separaten Speicherbereich**.  
  
 Die Verwendung dieser Treiber durch 16-Bit-Anwendungen unter Windows 95 wird nicht unterstützt.  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>Treiberspezifische Hardware- und Softwareanforderungen  
  
-   Die MicrosoftAccess- und dBASE-Treiber erfordern möglicherweise Änderungen in den Dateien Autoexec.bat oder Config.sys.
