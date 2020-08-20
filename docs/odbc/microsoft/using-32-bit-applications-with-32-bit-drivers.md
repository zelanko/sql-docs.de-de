---
description: Verwenden von 32-Bit-Anwendungen mit 32-Bit-Treibern
title: Verwenden von 32-Bit-Anwendungen mit 32-Bit-Treibern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
ms.assetid: 0cdd5788-5642-4280-8d53-b4ec461aafa1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69005071c83047471e76f38160265bc35cdccd4b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471364"
---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>Verwenden von 32-Bit-Anwendungen mit 32-Bit-Treibern
Sie können 32-Bit-Anwendungen mit 32-Bit-Treibern ausführen. Die 32-Bit-Anwendungen und die 32-Bit-Treiber verwenden die Win32-®-API.  
  
## <a name="architecture"></a>Aufbau  
 Die folgende Abbildung zeigt, wie 32-Bit-Anwendungen mit 32-Bit-Treibern kommunizieren. Die Anwendung ruft den 32-Bit-Treiber-Manager auf, der wiederum 32-Bit-Treiber aufruft.  
  
 ![Kommunikation zwischen 32-&#45;Bit-apps und 32-&#45;Bit-Treibern](../../odbc/microsoft/media/sdka6.gif "sdka6")  
  
> [!IMPORTANT]  
>  Verwenden Sie die Installations-DLL des 32-Bit-Thunking nicht auf WindowsNT/Windows 2000. Obwohl Sie denselben Dateinamen wie die 32-Bit-Installer-DLL hat, handelt es sich um eine andere dll.  
  
## <a name="administration"></a>Verwaltung  
 Mit dem ODBC-Datenquellen-Administrator können Sie Datenquellen für 32-Bit-Treiber verwalten. Öffnen Sie zum Öffnen des ODBC-Administrators auf Computern mit Windows 2000 die Windows-Systemsteuerung, doppelklicken Sie auf **Verwaltung**, und doppelklicken Sie dann auf **Datenquellen (ODBC)**. Auf Computern, auf denen frühere Versionen von Microsoft Windows ausgeführt werden, hat das Symbol den Namen **32-Bit-ODBC** oder einfach **ODBC**.  
  
## <a name="components"></a>Komponenten  
 Die ODBC-Komponente enthält die folgenden Dateien zum Ausführen von 32-Bit-Anwendungen mit 32-Bit-Treibern. Diese Komponenten befinden sich im Verzeichnis "\Redist".  
  
|Dateiname|BESCHREIBUNG|  
|---------------|-----------------|  
|Odbc32.dll|32-Bit-Treiber-Manager|  
|Odbccp32.dll|32-Bit-Installationsprogramm-dll|  
|Odbcad32.exe|32-Bit-ODBC-Administrator Programm|  
|Odbcinst. hlp|Hilfedatei des Installationsprogramms|  
|Msvcrt40.dll|C-Lauf Zeit Bibliothek|
