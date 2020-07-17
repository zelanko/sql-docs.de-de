---
title: Konfigurieren einer Firewall für FILESTREAM-Zugriff | Microsoft-Dokumentation
description: Verwenden Sie FILESTREAM in einer durch eine Firewall geschützten Umgebung, indem Sie die Windows-Dateifreigabeports 139 und 445 öffnen, um die Firewall für den FILESTREAM-Zugriff zu konfigurieren.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e26da4e57a58340cfca240fe99d8a36787528a49
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768042"
---
# <a name="configure-a-firewall-for-filestream-access"></a>Konfigurieren einer Firewall für FILESTREAM-Zugriff
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Um FILESTREAM in einer firewallgeschützten Umgebung verwenden zu können, müssen Client und Server in der Lage sein, DNS-Namen zu dem Server aufzulösen, der die FILESTREAM-Dateien enthält. Es ist für FILESTREAM erforderlich, dass unter Windows die Ports 139 und 445 für Dateifreigabe geöffnet sind.  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a>So öffnen Sie die Ports für die Datenfreigabe auf einem Computer unter Windows 7  
  
1.  Öffnen Sie in der Systemsteuerung **Windows-Firewall**.  
  
2.  Klicken Sie im linken Bereich auf **Erweiterte Einstellungen**. Wenn Sie zur Eingabe eines Administratorkennworts oder einer Bestätigung aufgefordert werden, geben Sie das Kennwort oder eine entsprechende Bestätigung ein.  
  
3.  Klicken Sie im Dialogfeld **Windows-Firewall mit erweiterter Sicherheit** im linken Bereich auf **Eingehende Regeln**, und klicken Sie dann im rechten Bereich auf **Neue Regel**.  
  
4.  Folgen Sie den Anweisungen im Assistenten für neue eingehende Regel, um TCP-Port 139 hinzuzufügen.  
  
5.  Wiederholen Sie den vorherigen Schritt, um TCP-Port 445 hinzuzufügen.  
  
6.  Schließen Sie das Dialogfeld **Windows-Firewall mit erweiterter Sicherheit** .  
  
  
