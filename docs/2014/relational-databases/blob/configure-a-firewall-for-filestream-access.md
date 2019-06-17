---
title: Konfigurieren einer Firewall für FILESTREAM-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fff59c773e4c96b8d14cf604c1a9a3e2b31869f4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66010312"
---
# <a name="configure-a-firewall-for-filestream-access"></a>Konfigurieren einer Firewall für FILESTREAM-Zugriff
  Um FILESTREAM in einer firewallgeschützten Umgebung verwenden zu können, müssen Client und Server in der Lage sein, DNS-Namen zu dem Server aufzulösen, der die FILESTREAM-Dateien enthält. Es ist für FILESTREAM erforderlich, dass unter Windows die Ports 139 und 445 für Dateifreigabe geöffnet sind.  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a>So öffnen Sie die Ports für die Datenfreigabe auf einem Computer unter Windows 7  
  
1.  Öffnen Sie in der Systemsteuerung **Windows-Firewall**.  
  
2.  Klicken Sie im linken Bereich auf **Erweiterte Einstellungen**. Wenn Sie zum Eingeben eines Administratorkennworts oder zu einer Bestätigung aufgefordert werden, geben Sie das Kennwort ein, oder nehmen Sie die Bestätigung vor.  
  
3.  Klicken Sie im Dialogfeld **Windows-Firewall mit erweiterter Sicherheit** im linken Bereich auf **Eingehende Regeln**, und klicken Sie dann im rechten Bereich auf **Neue Regel**.  
  
4.  Folgen Sie den Anweisungen im Assistenten für neue eingehende Regel, um TCP-Port 139 hinzuzufügen.  
  
5.  Wiederholen Sie den vorherigen Schritt, um TCP-Port 445 hinzuzufügen.  
  
6.  Schließen Sie das Dialogfeld **Windows-Firewall mit erweiterter Sicherheit** .  
  
  
