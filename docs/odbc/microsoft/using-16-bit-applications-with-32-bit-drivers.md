---
title: Verwenden von 16-Bit-Anwendungen mit 32-Bit-Treibern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 16-bit applications
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: 68feb3b7-c01a-4f42-8df9-f9c182d89325
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c919ed8c3f3791720d67ebdcbf5cfbdbea2a0455
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307631"
---
# <a name="using-16-bit-applications-with-32-bit-drivers"></a>Verwenden von 16-Bit-Anwendungen mit 32-Bit-Treibern
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Verwenden Sie stattdessen den 32-Bit-oder 64-Bit-Treiber-Manager.  
  
 Sie können 16-Bit-Anwendungen mit 32-Bit-Treibern auf Ihrem Windows-basierten System ausführen, sofern der 32-Bit-Treiber nicht explizit Win32-API-Funktionen aufruft, die Threads erstellen. Das WOW-Subsystem (Windows on Windows) führt die Anwendungen im 16-Bit-Modus aus und löst 16-Bit-Aufrufe des Betriebssystems auf. ODBC-Thunking-DLLs lösen 16-Bit-Aufrufe von der Anwendung in 32-Bit-Treiber aus. Die 16-Bit-Anwendungen verwenden die Windows-API, und 32-Bit-Treiber verwenden die Win32-API.  
  
## <a name="architecture"></a>Aufbau  
 Die folgende Abbildung zeigt, wie 16-Bit-Anwendungen mit 32-Bit-Treibern kommunizieren. Zwischen dem 16-Bit-Treiber-Manager und den 32-Bit-Treibern handelt es sich um generische thunkende DLLs, die 16-Bit-ODBC-Aufrufe in 32-Bit-ODBC-Aufrufe konvertieren.  
  
 ![Kommunikation von 16&#45;Bit-apps mit 32-&#45;Bit-Treibern](../../odbc/microsoft/media/sdka2.gif "sdka2")  
  
> [!NOTE]  
>  Wenn eine 16-Bit-Anwendung mit einem 32-Bit-Treiber interagiert, gibt der 32-Bit-Treiber-Manager immer "2,0" als Version von ODBC zurück, die vom Treiber unterstützt wird.  
  
## <a name="administration"></a>Verwaltung  
 Mit dem ODBC-Datenquellen-Administrator können Sie Datenquellen für 32-Bit-Treiber verwalten. Öffnen Sie die Windows-Systemsteuerung, doppelklicken Sie auf **Verwaltung**, und doppelklicken Sie dann auf **Datenquellen (ODBC)**, um den ODBC-Administrator auf Computern zu öffnen, auf denen Microsoft® Windows® 2000 ausgeführt wird. Auf Computern, auf denen frühere Versionen von Microsoft Windows ausgeführt werden, hat das Symbol den Namen **32-Bit-ODBC** oder einfach **ODBC**.  
  
 In der folgenden Abbildung wird gezeigt, wie eine 16-Bit-Anwendung eine 32-Bit-Treiber-Setup-DLL aufruft. Zwischen der 16-Bit-Installationsprogramm-dll und der 32-Bit-Treiber-Setup-DLL handelt es sich um eine generische Thunking-DLL, die 16-Bit-Installationsprogramm-DLL-Aufrufe in 32-Bit-Installer  
  
 ![Aufrufen einer 32-&#45;Bit-Treiber-Setup-DLL durch eine 16&#45;Bit-App](../../odbc/microsoft/media/sdka3.gif "sdka3")  
  
 In Windows on Windows (16-Bit-zu-32-Bit-Thunking) konvertiert eine zusätzliche Thunking-DLL mit dem Namen "Ds32gt. dll" 16-Bit-Argument Werte, die über eine 32-Bit-Setup-DLL an 16 Bit übermittelt werden.  
  
## <a name="components"></a>Komponenten  
 Die ODBC-Komponente des MDAC 2,8 SP1 SDK umfasst die folgenden Dateien für die Ausführung von 16-Bit-Anwendungen mit 32-Bit-Treibern. Diese Komponenten befinden sich im Verzeichnis "\Redist".  
  
|Dateiname|BESCHREIBUNG|  
|---------------|-----------------|  
|Odbc16gt. dll|16-Bit-ODBC-DLL für generischen Thunking|  
|Odbc32gt. dll|32-Bit-ODBC-DLL für generischen Thunking|  
|Datei odbccp32. dll|32-Bit-Installationsprogramm-dll|  
|Odbcad32. exe|32-Bit-Administrator Programm|  
|Odbcinst. hlp|Hilfedatei des Installationsprogramms|  
|Ds16gt. dll|Setup für die generische Thunking-DLL von 16-Bit-Treibern|  
|Ctl3d32. dll|32-Bit-dreidimensionale Fenster Stil Bibliothek|  
  
 Außerdem sind die folgenden Dateien zusammen mit dem 16-Bit-ODBC 2,10-Treiber-Manager, die nicht Teil von ODBC 3,51 sind, für erforderlich und sollten mit der 16-Bit-Anwendung installiert werden.  
  
|Dateiname|BESCHREIBUNG|  
|---------------|-----------------|  
|ODBC. dll|16-Bit-Treiber-Manager|  
|Odbcinst. dll|16-Bit-Installationsprogramm-dll|  
|Odbcadm. exe|16-Bit-ODBC-Administrator Programm|
