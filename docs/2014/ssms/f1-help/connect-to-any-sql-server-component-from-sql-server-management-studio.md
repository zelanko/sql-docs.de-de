---
title: Verbindung mit SQL Server-Komponente von SQL Server Management Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b2e90c7befa7e65deb307a272a42fff203af04bb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255292"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a>Herstellen einer Verbindung mit einer beliebigen SQL Server-Komponente aus SQL Server Management Studio
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] stellt die Funktionalität zum Verwalten aller Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]bereit. Mit [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] können Sie eine Verbindung zu folgenden Komponenten herstellen:  
  
-   Eine Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]installiert haben.  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]installiert haben.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]installiert haben.  
  
 Obwohl [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] es Ihnen ermöglicht, mit Abfragen zu arbeiten, ohne zuerst eine Verbindung mit einer Datenquelle herzustellen, ist für die meisten anderen Aufgaben eine Verbindung erforderlich. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] stellt das Dialogfeld **Verbindung mit Server herstellen** bereit, um Verbindungseigenschaften für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten zu konfigurieren. Wenn [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] gestartet wird, wird das Dialogfeld **Verbindung mit Server herstellen** geöffnet, und Sie werden aufgefordert, eine Verbindung mit einem Server herzustellen. Das Dialogfeld **Verbindung mit Server herstellen** behält die Verbindungseinstellungen vom vorherigen Mal bei.  
  
> [!NOTE]  
>  Diese Funktion lässt sich deaktivieren, sodass keine automatische Initialisierung einer Verbindung stattfindet. Weitere Informationen finden Sie unter [Startoptionen für den Datenbank-Engine-Dienst](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
## <a name="saving-connections"></a>Speichern von Verbindungen  
 Sie können Verbindungen mit bestimmten Servern in der Liste der registrierten Server speichern, oder Sie können mit dem Projektmappen-Explorer Verbindungen in Projekten speichern.  
  
### <a name="saving-connections-in-registered-servers"></a>Speichern von Verbindungen in der Liste der registrierten Server  
 Wenn Sie einen Server registrieren, speichert [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] die Verbindungsinformationen in der Liste der registrierten Server. Um eine Verbindung mit einem registrierten Server herzustellen, doppelklicken Sie in der Liste der registrierten Server auf den Servernamen. Daraufhin öffnet der Objekt-Explorer eine Verbindung zum Server.  
  
### <a name="saving-connections-in-solution-explorer"></a>Speichern von Verbindungen im Projektmappen-Explorer  
 Mit dem Projektmappen-Explorer können Sie zugehörige Abfragen, Skripts, Verbindungen und andere Informationen in einem Projekt speichern. Jedes Skriptprojekt enthält einen Knoten namens **Verbindungen**, in dem Sie eine oder mehrere Verbindungen speichern können. Klicken Sie zum Hinzufügen einer Verbindung mit der rechten Maustaste auf **Verbindungen**, und klicken Sie dann auf **Neue Verbindung**. Erweitern Sie zum Zugreifen auf eine gespeicherte Verbindung **Verbindungen** , und doppelklicken Sie auf die Verbindung. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] öffnet ein dieser Verbindung zugeordnetes Abfragefenster. Beim Speichern behalten Skripts die Verknüpfung zu einer bestimmten Verbindung bei.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SQL Server Management Studio](../sql-server-management-studio-ssms.md)   
 [Objekt-Explorers](../object/object-explorer.md)  
  
  
