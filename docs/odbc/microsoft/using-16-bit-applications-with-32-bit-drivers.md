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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ebd6f25758f73e75fd96abb734bc7b0347d5ee0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63209967"
---
# <a name="using-16-bit-applications-with-32-bit-drivers"></a>Verwenden von 16-Bit-Anwendungen mit 32-Bit-Treibern
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Verwenden Sie stattdessen die 32-Bit oder 64-Bit-Treiber-Manager.  
  
 Sie können 16-Bit-Anwendungen mit 32-Bit-Treibern auf Ihrem Windows-basierten System ausführen, solange die 32-Bit-Treiber nicht explizit Win32-API-Funktionen aufruft, die Threads zu erstellen. Die Windows on Windows (WOW)-Subsystem die Anwendungen in 16-Bit-Modus ausgeführt und löst 16-Bit-Aufrufe des Betriebssystems. ODBC thunking DLLs Resolve-16-Bit-Aufrufe aus der Anwendung auf 32-Bit-Treiber. Die 16-Bit-Anwendungen verwenden die Windows-API und 32-Bit-Treiber verwendet die Win32-API.  
  
## <a name="architecture"></a>Aufbau  
 Die folgende Abbildung zeigt, wie die 16-Bit-Anwendungen mit 32-Bit-Treiber kommunizieren. Sind zwischen den 16-Bit-Treiber-Manager und die 32-Bit-Treiber generische thunking DLLs, die 16-Bit-ODBC-Aufrufe in 32-Bit-ODBC-Aufrufe konvertieren.  
  
 ![Wie 16&#45;Kommunikation Bit-Anwendungen mit 32&#45;bit-Treiber](../../odbc/microsoft/media/sdka2.gif "sdka2")  
  
> [!NOTE]  
>  Jedes Mal, wenn eine 16-Bit-Anwendung mit einem 32-Bit-Treiber interagiert, gibt der 32-Bit-Treiber-Manager immer "2.0" als ODBC-Version vom Treiber unterstützt werden.  
  
## <a name="administration"></a>Verwaltung  
 Sie können Datenquellen für 32-Bit-Treibern mithilfe von ODBC-Datenquellen-Administrator verwalten. Um den ODBC-Administrator auf Computern unter Microsoft® Windows® 2000 öffnen, öffnen Sie die Windows-Systemsteuerung, doppelklicken Sie auf **Verwaltung**, und doppelklicken Sie dann auf **Datenquellen (ODBC)** . Auf Computern unter früheren Versionen von Microsoft Windows heißt das Symbol **32-Bit-ODBC-** oder einfach **ODBC**.  
  
 Die folgende Abbildung zeigt, wie eine 16-Bit-Anwendung eine Setup-DLL für 32-Bit-Treiber aufruft. Zwischen den 16-Bit-Installationsprogramm-DLL und die 32-Bit-Treiber ist die Setup-DLL für einen generischen thunking-DLL, die 16-Bit-Installer-DLL-Aufrufe auf 32-Bit-Installer-DLL-Aufrufe konvertiert.  
  
 ![Wie eine 16&#45;Bit-app Ruft eine 32&#45;-bit-Setup-DLL für Treiber](../../odbc/microsoft/media/sdka3.gif "sdka3")  
  
 In Windows auf Windows (16-Bit zu 32-Bit-thunking) eine zusätzliche thunking-DLL, die mit dem Namen Ds32gt.dll konvertiert, die 16-Bit-Argument-Werte über eine 32-Bit-Setup übergeben DLL zurück an 16-Bit.  
  
## <a name="components"></a>Komponenten  
 Die ODBC-Komponente von MDAC 2.8 SP1 SDK enthält die folgenden Dateien für die Ausführung von 16-Bit-Anwendungen mit 32-Bit-Treiber. Diese Komponenten sind im Verzeichnis \Redist.  
  
|Dateiname|Description|  
|---------------|-----------------|  
|Odbc16gt.dll|16-Bit-ODBC-generische thunking-DLL|  
|Odbc32gt.dll|32-Bit-ODBC-generische thunking-DLL|  
|Odbccp32.dll|32-Bit-Installationsprogramm-DLL|  
|Odbcad32.exe|32-Bit-Programm|  
|Odbcinst.hlp|Installer-Hilfedatei|  
|Ds16gt.dll|generische thunking DLL 16-Bit-Treiber-setup|  
|Ctl3d32.dll|dreidimensionale Fenster 32-Bit-Bibliothek|  
  
 Darüber hinaus die folgenden Dateien zusammen mit der 16-Bit-2.10-ODBC-Treiber-Manager, die nicht Teil von ODBC 3.51 sind, sind erforderlich und sollte mit der 16-Bit-Anwendung installiert werden.  
  
|Dateiname|Beschreibung|  
|---------------|-----------------|  
|Odbc.dll|16-Bit-Treiber-Manager|  
|Odbcinst.dll|16-Bit-Installationsprogramm-DLL|  
|Odbcadm.exe|16-Bit-ODBC-Administratorprogramm|
