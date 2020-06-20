---
title: Führen Sie die Schritte nach der Installation aus. Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ed350264ccab56365f4e5cf5074c063b4244fd31
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85007687"
---
# <a name="complete-the-post-installation-steps"></a>Ausführen der Schritte nach der Installation
  Nach der Installation von Distributed Replay müssen Sie die Distributed Replay Controller und -Client-Dienstkonten ändern.  
  
### <a name="to-complete-the-post-installation-steps"></a>So führen Sie die Schritte nach der Installation aus  
  
1.  **Erstellen von Firewallregeln:** Auf den Controller- und Clientcomputern müssen Sie für den entsprechenden Dienst den eingehenden Datenverkehr durch die Firewall zulassen. Geben Sie die Firewallregeln für die ausführbaren Dienstdateien an, die sich in den Installationsordnern befinden.  
  
    1.  Erstellen Sie für den Controllerdienst eine Regel für **DReplayController.exe**. Diese Datei befindet sich im Installationsordner. Mit dem folgenden Befehl aktivieren Sie beispielsweise diese Regel, wobei `%InstallPath%` den Installationsordner des Diensts darstellt:  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  Erstellen Sie für den Clientdienst auf jedem Clientcomputer eine Regel für **DReplayClient.exe**. Diese Datei befindet sich im Installationsordner. Mit dem folgenden Befehl aktivieren Sie beispielsweise diese Regel, wobei `%InstallPath%` den Installationsordner des Diensts darstellt:  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **Jedem Client Berechtigungen für den Zielserver erteilen:** Wenn Sie die Installation des Clientdiensts auf den Clientcomputern abgeschlossen haben, müssen Sie der sysadmin-Rolle für die Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manuell die Clientdienstkonten hinzufügen.  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Sie müssen über Administratorberechtigungen verfügen, um eine der Distributed Replay-Funktionen zu installieren. Nur bei einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung mit sysadmin-Berechtigungen können der sysadmin-Serverrolle des Testservers die Clientdienstkonten hinzugefügt werden. Weitere Informationen zu Sicherheitsüberlegungen für Distributed Replay finden Sie unter [Distributed Replay Security](distributed-replay-security.md).  
  
  
