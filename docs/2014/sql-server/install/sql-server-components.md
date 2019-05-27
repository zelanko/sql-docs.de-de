---
title: SQL Server-Komponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
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
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 52045095714bfc2be7e929ed27a26a800c860fe6
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092091"
---
# <a name="sql-server-components"></a>SQL Server-Komponenten
  Sie können den Analyse-Assistenten ausführen, für einen lokal oder remote-Computer, die [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installiert. Der erste Schritt bei der Analyse vor dem Upgrade besteht darin, den Computer und die Komponenten für die Analyse zu identifizieren.  
  
## <a name="options"></a>Optionen  
 **Name des Computers**  
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
  
  
