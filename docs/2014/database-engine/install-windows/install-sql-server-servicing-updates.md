---
title: Installieren von SQL Server 2014-Wartungs Updates | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
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
  
 Nachdem Setup die neuesten Versionen der anwendbaren Updates gefunden hat, lädt es diese herunter und integriert sie in den aktuellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationsvorgang. Produktupdate kann ein kumulatives Update, Service Pack oder Service Pack plus kumulatives Update enthalten. Die Produkt Update Funktionalität ist eine Erweiterung der [slipstreamfunktionalität](https://go.microsoft.com/fwlink/?LinkId=219945) , die in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1 verfügbar war.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-after-it-has-already-been-installed"></a>Installieren von Updates für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , nachdem es bereits installiert wurde  
 Auf einer installierten Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]empfiehlt es sich, alle verfügbaren Updates anzuwenden: allgemeine Verteilungs Releases (Updates der DDR-Sicherheit/kritisch), Service Packs (SP) und das neueste verfügbare kumulative Update (Cu).  
  
 Abhängig vom Typ der Wartungsversion sind SQL Server Updates über Microsoft Update (MU), das Microsoft Download Center und/oder den Support Services-hotfixserver verfügbar. Sicherheits-und kritische Updates für SQL Server werden automatisch von Microsoft Update bereitgestellt (damit Sie diese Updates anzeigen können, müssen Sie sich in mu durch Windows Update in der Systemsteuerung anmelden). Service Packs sind auf Mu als optionale/wichtige Downloads und im Download Center verfügbar. Kumulative Updates sind auf dem Microsoft Hotfix-Download Server verfügbar, der in Cu Knowledge Base-Artikeln bereitgestellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren Sie SQL Server 2014 über den Installations-Assistenten &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md)   
 [Durch das Installieren von Updates von der Eingabeaufforderung](installing-updates-from-the-command-prompt.md) werden [Funktionen zu einer Instanz von SQL Server 2014 &#40;Setup hinzugefügt&#41;](add-features-to-an-instance-of-sql-server-setup.md)   
 [Entfernen einer SQL Server 2014-Installation](repair-a-failed-sql-server-installation.md)  
  
  
