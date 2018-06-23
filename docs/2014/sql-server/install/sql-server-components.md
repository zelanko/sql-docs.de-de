---
title: SQL Server-Komponenten | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Upgrade Advisor, components
- listing components to analyze
- Upgrade Advisor [SQL Server], components
- component analysis [Upgrade Advisor]
- finding components to analyze
- locating components to analyze
- detecting components to analyze
- server names [Upgrade Advisor]
- analyzing system [Upgrade Advisor], component list
- identifying components to analyze
ms.assetid: 539b9525-ce3f-4950-9146-5527a5a297ee
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 85a89e2114cd00b28444cf6ee62d12ff1abdec42
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151731"
---
# <a name="sql-server-components"></a>SQL Server-Komponenten
  Sie können den Analyse-Assistenten auf einem lokalen oder Remotecomputer Computer mit ausführen [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installiert. Der erste Schritt bei der Analyse vor dem Upgrade besteht darin, den Computer und die Komponenten für die Analyse zu identifizieren.  
  
## <a name="options"></a>Tastatur  
 **Computername**  
 Gibt den Namen des zu analysierenden Computers an. Der Upgrade Advisor füllt die **Servernamen** Feld mit dem Namen des lokalen Computers. Sie können auch "." und "localhost" verwenden, um die Verbindung mit dem lokalen Computer herzustellen.  
  
 Wenn Sie einen anderen Computer analysieren, beachten Sie die folgenden Hinweise:  
  
-   Um nicht gruppierte Instanzen zu scannen, geben Sie den Computernamen ein.  
  
-   Um gruppierte Instanzen zu scannen, geben Sie den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusterinstanz ein.  
  
-   Um nicht gruppierte Komponenten zu scannen, die auf einem Knoten eines Clusters installiert sind, geben Sie den Computernamen des Failovercluster-Knotens ein.  
  
    > [!IMPORTANT]  
    >  Geben Sie nicht den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanznamen an.  
  
 Statt den Computernamen anzugeben, können Sie auch die IP-Adresse angeben.  
  
 Wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, müssen Sie den Namen des lokalen Computers angeben. Der Upgrade Advisor scannt nur lokale Berichtsserver.  
  
 **Erkennen**  
 Die **erkennen** Schaltfläche greift auf den angegebenen Computer und die zu analysierenden Komponenten:  
  
-   Wenn Sie auf einem Remotecomputer eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz analysieren, müssen Sie die Remoteregistrierungsdienste auf dem Remotecomputer aktivieren.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird erkannt, wenn eine Instanz von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] in der Registrierung des Computers gefunden wird.  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] wird erkannt, wenn eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in der Registrierung des Computers gefunden wird.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird erkannt, wenn [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in der Registrierung des Computers gefunden wird. Allerdings scannt der Upgrade Advisor nur lokale Berichtsserver.  
  
 **Components**  
 Wählen Sie die zu analysierenden Komponenten aus. Klicken Sie auf die **erkennen** klicken, um alle auf dem Computer installierten Komponenten auszuwählen. Ein Häkchen wird neben den Komponenten angezeigt, die als auf dem Computer installiert erkannt wurden. Sie können die zu analysierenden Komponenten auch manuell auswählen, indem Sie die Kontrollkästchen neben den Komponenten aktivieren bzw. deaktivieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Upgrade Advisor Referenz zur Benutzeroberfläche](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  