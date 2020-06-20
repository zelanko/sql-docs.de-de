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
ms.openlocfilehash: 8dd4e6ce7800c3a0a9db51f6c1a4bddfe7a188c3
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84931691"
---
# <a name="validate-a-sql-server-installation"></a>Überprüfen einer SQL Server-Installation
  Mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ermittlungsberichts können Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version sowie die auf dem Computer installierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen überprüfen. Der **Bericht zur Ermittlung installierter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Funktionen** zeigt einen Bericht aller-, [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] -,-,-, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -und- [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Produkte und-Funktionen an, die auf dem lokalen Server installiert sind. Der Bericht zur Ermittlung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen steht im **-Installationscenter auf der Seite** Tools [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereit.  
  
 **So führen Sie den Bericht zur Ermittlung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen aus**  
  
 Starten Sie das- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installations Center, verwenden Sie das **Startmenü** , zeigen Sie auf **Alle Programme**, zeigen Sie auf ** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name> **, zeigen Sie auf **Konfigurationstools**, und klicken Sie auf ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installations Center**. Klicken Sie im linken Navigationsbereich des **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationscenter** auf **Tools** und anschließend auf **Bericht zur Ermittlung installierter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen**, um den Bericht zur Ermittlung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen auszuführen.  
  
 Der Ermittlungs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bericht wird unter% Program Files% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\setup Bootstrap\LOG \\<letzte Setup Sitzung gespeichert \> .  
  
 Sie können den Ermittlungsbericht auch über die Befehlszeile generieren. Führen Sie "Setup.exe/Action = rundiscovery" über eine Eingabeaufforderung aus. Wenn Sie der oben stehenden Befehlszeile den Befehl "/q" hinzufügen, wird keine Benutzeroberfläche angezeigt. der Bericht wird jedoch weiterhin unter% Program Files% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\setup Bootstrap\LOG \\<letzte Setup Sitzung erstellt \> .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](view-and-read-sql-server-setup-log-files.md)  
  
  
