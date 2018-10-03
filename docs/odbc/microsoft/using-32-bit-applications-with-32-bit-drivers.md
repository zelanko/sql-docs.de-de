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
manager: craigg
ms.openlocfilehash: 5c4f0b21bba9e56cad076ae08f5a561cc972d2ff
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696338"
---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>Verwenden von 32-Bit-Anwendungen mit 32-Bit-Treibern
Sie können die 32-Bit-Anwendungen mit 32-Bit-Treiber ausführen. Die 32-Bit-Anwendungen und die 32-Bit-Treiber verwenden das Win32®-API an.  
  
## <a name="architecture"></a>Aufbau  
 Die folgende Abbildung zeigt, wie die 32-Bit-Anwendungen mit 32-Bit-Treiber kommunizieren. Die Anwendung ruft die 32-Bit-Treiber-Manager, das wiederum die 32-Bit-Treibern aufruft.  
  
 ![Wie 32&#45;Kommunikation Bit-Anwendungen mit 32&#45;bit-Treiber](../../odbc/microsoft/media/sdka6.gif "sdka6")  
  
> [!IMPORTANT]  
>  Verwenden Sie die 32-Bit-thunking Installationsprogramm-DLL nicht auf Windows NT/Windows 2000 aus. Obwohl sie denselben Dateinamen wie die 32-Bit-Installationsprogramm-DLL verfügt, ist es eine andere DLL.  
  
## <a name="administration"></a>Verwaltung  
 Sie können Datenquellen für 32-Bit-Treibern mithilfe von ODBC-Datenquellen-Administrator verwalten. Um den ODBC-Administrator auf Computern unter Windows 2000 zu öffnen, öffnen Sie die Windows-Systemsteuerung, doppelklicken Sie auf **Verwaltung**, und doppelklicken Sie dann auf **Datenquellen (ODBC)**. Auf Computern unter früheren Versionen von Microsoft Windows heißt das Symbol **32-Bit-ODBC-** oder einfach **ODBC**.  
  
## <a name="components"></a>Components  
 Die ODBC-Komponente enthält die folgenden Dateien für die Ausführung von 32-Bit-Anwendungen mit 32-Bit-Treiber. Diese Komponenten sind im Verzeichnis \Redist.  
  
|Dateiname|Description|  
|---------------|-----------------|  
|Datei "ODBC32.dll"|32-Bit-Treiber-Manager|  
|ODBCCP32.dll|32-Bit-Installationsprogramm-DLL|  
|Odbcad32.exe|32-Bit-ODBC-Administratorprogramm|  
|Odbcinst.hlp|Installer-Hilfedatei|  
|Msvcrt40.dll|C-Laufzeitbibliothek|
