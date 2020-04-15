---
title: Verwenden von 32-Bit-Anwendungen mit 32-Bit-Treibern | Microsoft Docs
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
ms.openlocfilehash: 31512f9339b9d46225bb4f1198cb617a48509acb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307601"
---
# <a name="using-32-bit-applications-with-32-bit-drivers"></a>Verwenden von 32-Bit-Anwendungen mit 32-Bit-Treibern
Sie können 32-Bit-Anwendungen mit 32-Bit-Treibern ausführen. Die 32-Bit-Anwendungen und die 32-Bit-Treiber verwenden die Win32®-API.  
  
## <a name="architecture"></a>Aufbau  
 Die folgende Abbildung zeigt, wie 32-Bit-Anwendungen mit 32-Bit-Treibern kommunizieren. Die Anwendung ruft den 32-Bit-Treiber-Manager auf, der wiederum 32-Bit-Treiber aufruft.  
  
 ![Wie 32&#45;-Bit-Apps mit 32&#45;-Bit-Treibern kommunizieren](../../odbc/microsoft/media/sdka6.gif "sdka6")  
  
> [!IMPORTANT]  
>  Verwenden Sie die 32-Bit-Thunking-Installations-DLL unter WindowsNT/Windows2000 nicht. Obwohl es den gleichen Dateinamen wie die 32-Bit-Installations-DLL hat, ist es eine andere DLL.  
  
## <a name="administration"></a>Verwaltung  
 Sie können Datenquellen für 32-Bit-Treiber mithilfe des ODBC-Datenquellenadministrators verwalten. Um den ODBC-Administrator auf Computern mit Windows 2000 zu öffnen, öffnen Sie die Windows-Systemsteuerung, doppelklicken Sie auf **Verwaltungstools**, und doppelklicken Sie dann auf **Datenquellen (ODBC).** Auf Computern, auf denen frühere Versionen von Microsoft Windows ausgeführt wurden, heißt das Symbol **32-Bit ODBC** oder einfach **ODBC**.  
  
## <a name="components"></a>Komponenten  
 Die ODBC-Komponente enthält die folgenden Dateien zum Ausführen von 32-Bit-Anwendungen mit 32-Bit-Treibern. Diese Komponenten befinden sich im Verzeichnis .Redist.  
  
|Dateiname|BESCHREIBUNG|  
|---------------|-----------------|  
|Odbc32.dll|32-Bit-Treiber-Manager|  
|Odbccp32.dll|32-Bit-Installer-DLL|  
|Odbcad32.exe|32-Bit ODBC Administrator-Programm|  
|Odbcinst.hlp|Installationshilfedatei|  
|Msvcrt40.dll|C-Laufzeitbibliothek|
