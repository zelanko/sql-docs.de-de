---
title: Problembehandlung für eine PowerPivot für SharePoint-Installation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: b4881ce3be8ede7d97dc2b71fb464b94b8677ca0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061077"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a>Problembehandlung für eine PowerPivot für SharePoint-Installation
  Wenn Sie anstelle der erwateten Seiten und Funktionen Fehler erhalten, gehen Sie wie folgt vor.  
  
-   Lesen Sie die Versionsanmerkungen zu SharePoint sowie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , um Problemumgehungen für bekannte Installationsprobleme zu finden. Die Versionsanmerkungen werden mit den Installationsmedien sowie auf der Microsoft-Website bereitgestellt, von der Sie die Software heruntergeladen haben.  
  
    -   [Versionsanmerkungen zu SQL Server 2014](http://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).  
  
-   Weitere Informationen finden Sie im TechNet Wiki-Thema [Behandeln von Problemen mit PowerPivot-Installationen (und anderen Add-Ins)](http://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx).  
  
## <a name="issues"></a>Probleme  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a>Miniaturbilder werden im PowerPivot-Katalog als rotes X dargestellt  
 Eine Möglichkeit besteht darin, dass die **PowerPivot-Funktionsintegration für Websitesammlungen** nichtaktiv ist. Führen Sie folgende Schritte aus:  
  
1.  Klicken Sie in der PowerPivot-katalogbibliothek auf **Standorteinstellungen** über das Zahnradsymbol ![SharePoint Einstellungen](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint-Einstellungen") oder **Home** Liste.  
  
2.  Klicken Sie im Abschnitt **Websitesammlungsverwaltung** auf **Websitesammlungs-Features**.  
  
3.  Klicken Sie auf **Websitesammlungs-Features**.  
  
4.  Stellen Sie sicher, dass die **PowerPivot-Funktionsintegration für Websitesammlungen** auf **Aktiv**festgelegt ist.  
  
 Weitere Ursachen dieses Problems finden Sie unter [PowerPivot-Katalog wird ein rotes x für Symbole](http://support.microsoft.com/kb/2361559) (http://support.microsoft.com/kb/2361559).  
  
  