---
title: Überprüfen einer SQL Server-Installation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34e4c29cb28f76c930f1f04152528ca1a8a89dfc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62775233"
---
# <a name="validate-a-sql-server-installation"></a>Überprüfen einer SQL Server-Installation
  Mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ermittlungsberichts können Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version sowie die auf dem Computer installierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen überprüfen. Der **Bericht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Ermittlung installierter Funktionen** zeigt einen Bericht [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]aller [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-,-,- [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ,-,-und-Produkte und-Funktionen an, die auf dem lokalen Server installiert sind. Der Bericht zur Ermittlung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen steht im **-Installationscenter auf der Seite** Tools [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereit.  
  
 **So führen Sie den Bericht zur Ermittlung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen aus**  
  
 Rufen Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationscenter auf. Klicken Sie dazu im **Startmenü** auf **Alle Programme**, **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Versionsname>** > **Konfigurationstools**, und klicken Sie auf **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installationscenter**. Klicken Sie im linken Navigationsbereich des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **-Installationscenter** auf **Tools[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und anschließend auf** Bericht zur Ermittlung installierter **-Funktionen[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], um den Bericht zur Ermittlung der** -Funktionen auszuführen.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ermittlungsbericht wird unter% Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\setup Bootstrap\LOG\\<letzte Setup Sitzung\>gespeichert.  
  
 Sie können den Ermittlungsbericht auch über die Befehlszeile generieren. Führen Sie "Setup. exe/Action = rundiscovery" über eine Eingabeaufforderung aus. Wenn Sie der oben stehenden Befehlszeile den Befehl "/q" hinzufügen, wird keine Benutzeroberfläche angezeigt. der Bericht wird jedoch weiterhin\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unter% Program Files% \120\setup\\ Bootstrap\LOG<letzte Setup Sitzung\>erstellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](view-and-read-sql-server-setup-log-files.md)  
  
  
