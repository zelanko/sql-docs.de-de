---
title: WMI-Fehler 0x8007052f | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c1668c2b4c96f23283f0eca87fdbac591f52b75f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68211604"
---
# <a name="wmi-error-0x8007052f"></a>WMI-Fehler 0x8007052f
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|0x8007052f|  
|Ereignisquelle|WMI-Anbieterfehler|  
|Komponente|SQL Server-Konfigurations-Manager|  
|Symbolischer Name|NA|  
|Meldungstext|Anmeldefehler: Eingeschränktes Benutzerkonto. Mögliche Ursachen hierfür sind, dass leere Kennwörter nicht zulässig sind, Einschränkungen der Anmeldezeiten vorliegen oder eine Richtlinieneinschränkung erzwungen wurde.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler kann auftreten, wenn der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager verwendet wird, um zu den integrierten Konten zu wechseln (Netzwerkdienst, Lokaler Dienst oder Lokales System), während [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einem Windows Server 2003-Cluster oder einem Windows Server-Domänencontroller ausgeführt wird. Führen Sie Dienste auf einem Windows Server-Cluster oder einem Windows Server-Domänencontroller nicht unter integrierten Konten aus. Empfehlungen zu Dienstkonten finden Sie unter "Einrichten von Windows-Dienstkonten" in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="user-action"></a>Benutzeraktion  
 Konfigurieren Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] für die Verwendung eines Domänenkontos.  
  
  
