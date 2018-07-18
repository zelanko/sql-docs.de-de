---
title: Ausführen des Systemmonitors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9e1b997909da0d21dfbceeb6adfb3607a0e7e7a9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32950185"
---
# <a name="run-system-monitor"></a>Ausführen des Systemmonitors
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Der Systemmonitor verwendet zum Sammeln von Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Informationen Remoteprozeduraufrufe (RPC). Jeder Benutzer, der über die entsprechenden Microsoft Windows-Berechtigungen zum Ausführen des Systemmonitors verfügt, kann dieses Tool für die Überwachung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwenden.  
  
> [!NOTE]  
>  Bei der Verwendung des Systemmonitors können Sie keine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen, die unter Microsoft Windows 98 ausgeführt wird.  
  
 Wie bei allen Leistungsüberwachung ist auch bei der Verwendung des Systemmonitor zum Überwachen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit zusätzlichem Verarbeitungsaufwand zu rechnen. Der tatsächliche Verarbeitungsaufwand in einer bestimmten Instanz hängt von der Hardwareplattform, der Anzahl der Leistungsindikatoren und dem ausgewählten Updateintervall ab. Die Integration des Systemmonitors mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist jedoch so konzipiert, dass die Auswirkungen minimal sein sollten.  
  
> [!NOTE]  
>  Wenn Sie im Snap-In des Systemmonitors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Leistungsindikatoren zur Überwachung ausgewählt haben, werden die Leistungsindikatoren auch dann angezeigt, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht ausgeführt wird.  
  
 Weitere Informationen zum Starten des Systemmonitors finden Sie unter [Starten des Systemmonitors &#40;Windows&#41;](../../relational-databases/performance/start-system-monitor-windows.md).  
  
  
