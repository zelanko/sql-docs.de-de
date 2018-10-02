---
title: WMI-Fehler 0x8007052f | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 668cb77d2e15fc23981f6f32bcac44391567f0df
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810384"
---
# <a name="wmi-provider-error-0x8007052f"></a>WMI-Anbieterfehler 0x8007052f
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|0x8007052f|  
|Ereignisquelle|WMI-Anbieterfehler|  
|Komponente|SQL Server-Konfigurations-Manager|  
|Symbolischer Name|NA|  
|Meldungstext|Anmeldefehler: Eingeschränktes Benutzerkonto. Mögliche Ursachen hierfür sind, dass leere Kennwörter nicht zulässig sind, Einschränkungen der Anmeldezeiten vorliegen oder eine Richtlinieneinschränkung erzwungen wurde.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler kann auftreten, wenn der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager verwendet wird, um zu den integrierten Konten zu wechseln (Netzwerkdienst, Lokaler Dienst oder Lokales System), während [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einem Windows Server 2003-Cluster oder einem Windows Server-Domänencontroller ausgeführt wird. Führen Sie Dienste auf einem Windows Server-Cluster oder einem Windows Server-Domänencontroller nicht unter integrierten Konten aus. Empfehlungen zu Dienstkonten finden Sie unter "Einrichten von Windows-Dienstkonten" in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="user-action"></a>Benutzeraktion  
 Konfigurieren Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] für die Verwendung eines Domänenkontos.  
  
  
