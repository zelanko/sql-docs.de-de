---
title: Verwenden von 16-Bit-Anwendungen mit 32-Bit-Treibern | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307631"
---
# <a name="using-16-bit-applications-with-32-bit-drivers"></a>Verwenden von 16-Bit-Anwendungen mit 32-Bit-Treibern
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Verwenden Sie stattdessen den 32-Bit- oder 64-Bit-Treiber-Manager.  
  
 Sie können 16-Bit-Anwendungen mit 32-Bit-Treibern auf Ihrem Windows-basierten System ausführen, solange der 32-Bit-Treiber Win32-API-Funktionen, die Threads erstellen, nicht explizit aufruft. Das Windows-unter Windows-Subsystem (WOW) führt die Anwendungen im 16-Bit-Modus aus und löst 16-Bit-Aufrufe an das Betriebssystem auf. ODBC Thunking DLLs lösen 16-Bit-Aufrufe von der Anwendung auf 32-Bit-Treiber. Die 16-Bit-Anwendungen verwenden die Windows-API und 32-Bit-Treiber die Win32-API.  
  
## <a name="architecture"></a>Aufbau  
 Die folgende Abbildung zeigt, wie 16-Bit-Anwendungen mit 32-Bit-Treibern kommunizieren. Zwischen dem 16-Bit-Treiber-Manager und den 32-Bit-Treibern befinden sich generische Thunking-DLLs, die 16-Bit-ODBC-Aufrufe in 32-Bit-ODBC-Aufrufe konvertieren.  
  
 ![Wie 16&#45;-Bit-Apps mit 32&#45;-Bit-Treibern kommunizieren](../../odbc/microsoft/media/sdka2.gif "sdka2")  
  
> [!NOTE]  
>  Jedes Mal, wenn eine 16-Bit-Anwendung mit einem 32-Bit-Treiber interagiert, gibt der 32-Bit-Treiber-Manager immer "2.0" als vom Treiber unterstützte Version von ODBC zurück.  
  
## <a name="administration"></a>Verwaltung  
 Sie können Datenquellen für 32-Bit-Treiber mithilfe des ODBC-Datenquellenadministrators verwalten. Um den ODBC-Administrator auf Computern mit Microsoft® Windows® 2000 zu öffnen, öffnen Sie die Windows-Systemsteuerung, doppelklicken Sie auf **Verwaltungstools**, und doppelklicken Sie dann auf **Datenquellen (ODBC).** Auf Computern, auf denen frühere Versionen von Microsoft Windows ausgeführt wurden, heißt das Symbol **32-Bit ODBC** oder einfach **ODBC**.  
  
 Die folgende Abbildung zeigt, wie eine 16-Bit-Anwendung eine 32-Bit-Treiber-Setup-DLL aufruft. Zwischen der 16-Bit-Installations-DLL und der 32-Bit-Treiber-Setup-DLL befindet sich eine generische Thunking-DLL, die 16-Bit-Installer-DLL-Aufrufe in 32-Bit-Installations-DLL-Aufrufe konvertiert.  
  
 ![Wie eine 16-&#45;-Bit-App eine 32-&#45;-Bit-Treiber-Setup-DLL aufruft](../../odbc/microsoft/media/sdka3.gif "sdka3")  
  
 In Windows unter Windows (16-Bit- bis 32-Bit-Thunking) konvertiert eine zusätzliche Thunking-DLL mit dem Namen Ds32gt.dll 16-Bit-Argumentwerte, die durch eine 32-Bit-Setup-DLL übergeben wurden, zurück in 16-Bit.  
  
## <a name="components"></a>Komponenten  
 Die ODBC-Komponente des MDAC 2.8 SP1 SDK enthält die folgenden Dateien zum Ausführen von 16-Bit-Anwendungen mit 32-Bit-Treibern. Diese Komponenten befinden sich im Verzeichnis .Redist.  
  
|Dateiname|BESCHREIBUNG|  
|---------------|-----------------|  
|Odbc16gt.dll|16-Bit ODBC generische Thunking DLL|  
|Odbc32gt.dll|32-Bit ODBC generische Thunking DLL|  
|Odbccp32.dll|32-Bit-Installer-DLL|  
|Odbcad32.exe|32-Bit-Administratorprogramm|  
|Odbcinst.hlp|Installationshilfedatei|  
|Ds16gt.dll|16-Bit-Treiber-Setup generisches Thunking-DLL|  
|Ctl3d32.dll|32-Bit-Bibliothek im dreidimensionalen Fensterstil|  
  
 Darüber hinaus sind die folgenden Dateien zusammen mit dem 16-Bit ODBC 2.10 Driver Manager, die nicht Teil von ODBC 3.51 sind, von der 16-Bit-Anwendung erforderlich und sollten installiert werden.  
  
|Dateiname|BESCHREIBUNG|  
|---------------|-----------------|  
|Odbc.dll|16-Bit-Treiber-Manager|  
|Odbcinst.dll|16-Bit-Installer-DLL|  
|Odbcadm.exe|16-Bit ODBC Administrator-Programm|
