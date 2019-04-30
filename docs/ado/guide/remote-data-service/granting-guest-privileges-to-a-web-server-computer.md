---
title: Gewähren von Gastberechtigungen für einen Webservercomputer | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21c4eae0608e433ed3ca7888091a7c658726192d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63214777"
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Gewähren von Gastberechtigungen für einen Webservercomputer
Das anonyme Konto der Web-Server (IUSR_*ComputerName*) muss hinzugefügt werden, zur lokalen Gruppe Gäste auf dem Webservercomputer von RDS.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Gewähren von Gastberechtigungen auf eine Web-Server-computer  
  
1.  Klicken Sie auf dem Computer Microsoft Windows 2000 Server auf **starten**, zeigen Sie auf **Programme**, zeigen Sie auf **Verwaltung**, und klicken Sie dann auf **Computer Management**.  
  
2.  In der Konsolenstruktur in **lokale Benutzer und Gruppen**, klicken Sie auf **Gruppen**.  
  
3.  Wählen Sie die **Gäste** lokale Gruppe. Von der **Aktion** Menü wählen **Eigenschaften**.  
  
4.  In der **Gäste Eigenschaften** Dialogfeld klicken Sie auf **hinzufügen**.  
  
5.  Wenn das anonyme Konto der Web-Server nicht, in der Liste angezeigt wird der **Benutzer oder Gruppen auswählen** Dialogfeld geben den Namen (IUSR_*ComputerName*) in das untere Textfeld ein, und klicken Sie dann auf **hinzufügen** .  
  
6.  Klicken Sie auf **OK**.


