---
title: Installieren von SQL Server 2014-Wartungsupdates | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07f438f86a22b866351a0b83ee7634338f3ad2cd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62775343"
---
# <a name="install-sql-server-2014-servicing-updates"></a>Installieren von SQL Server 2014-Wartungsupdates
  Dieses Thema enthält Informationen zum Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. In diesem Abschnitt finden Sie Informationen zu den folgenden Themen:  
  
-   Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] während einer neuen Installation  
  
-   Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , nachdem es bereits installiert wurde.  
  
 Es empfiehlt sich, dass Kunden neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Updates zeitnah bewerten und installieren, um sicherzustellen, dass Systeme mit den letzten Sicherheitsupdates aktualisiert wurden.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-during-a-new-installation"></a>Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] während einer neuen Installation  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup integriert die neuesten Produktupdates in die Installation des Hauptprodukts, sodass das Hauptprodukt und geeignete Updates gleichzeitig installiert werden. Das Produktupdate kann an folgenden Orten nach anwendbaren Updates suchen:  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
-   Windows Server Update Services (WSUS)  
  
-   Ein lokaler Ordner  
  
-   Eine Netzwerkfreigabe  
  
 Nachdem Setup die neuesten Versionen der anwendbaren Updates gefunden hat, lädt es diese herunter und integriert sie in den aktuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationsvorgang. Produktupdate kann ein kumulatives Update, Service Pack oder Service Pack plus kumulatives Update enthalten. Produktupdatefunktionalität ist eine Erweiterung von der [Slipstreamfunktionalität](https://go.microsoft.com/fwlink/?LinkId=219945) , die gab es in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-after-it-has-already-been-installed"></a>Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , nachdem es bereits installiert wurde  
 Auf einer installierten Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], es wird empfohlen, dass Sie alle verfügbaren Updates anwenden: Allgemeiner Verteilungsversionen (GDR - Sicherheit/kritische Updates), Service Packs (SP) als auch der neuesten verfügbaren kumulativen Update (CU).  
  
 Je nach Art der Wartungsupdate sind SQL Server-Updates über Microsoft Update (MU), die im Microsoft Download Center und/oder den Hotfix für Microsoft Support Services Server zur Verfügung. Sicherheits- und wichtige Updates für SQL Server werden automatisch bereitgestellt, von Microsoft Update (in der Lage ist, um diese Updates sehen zu abonnieren, MU, über Windows Update in der Systemsteuerung benötigten sein). Service Packs sind auf MU verfügbar, da Optional/wichtig sowie im Download Center heruntergeladen. Kumulative Updates sind verfügbar, auf dem Microsoft Hotfix-Download-Server im CU Knowledge Base-Artikeln bereitgestellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von SQLServer 2014 vom Installations-Assistenten &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md)   
 [Installieren von Updates an der Eingabeaufforderung](installing-updates-from-the-command-prompt.md) [Hinzufügen von Funktionen zu einer Instanz von SQL Server 2014 &#40;Setup&#41;](add-features-to-an-instance-of-sql-server-setup.md)   
 [Entfernen einer SQL Server 2014-Installation](repair-a-failed-sql-server-installation.md)  
  
  
