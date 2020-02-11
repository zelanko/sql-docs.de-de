---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6b4d14cc65b31a0641149ace931efe46c914ad1b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088158"
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
|Odbc32. dll|32-Bit-Treiber-Manager|  
|Datei odbccp32. dll|32-Bit-Installationsprogramm-dll|  
|Odbcad32. exe|32-Bit-ODBC-Administrator Programm|  
|Odbcinst. hlp|Hilfedatei des Installationsprogramms|  
|Msvcrt40. dll|C-Lauf Zeit Bibliothek|
