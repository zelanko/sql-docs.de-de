---
title: Herstellen einer Verbindung mit einer beliebigen SQL Server-Komponente
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ebc0f4a5ca2be46e607ccd8d18399b7fe0ef6814
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75243927"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a>Herstellen einer Verbindung mit einer beliebigen SQL Server-Komponente aus SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] stellt die Funktionalität zum Verwalten aller Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]bereit. Mit [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] können Sie eine Verbindung zu folgenden Komponenten herstellen:  
  
-   Eine Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)].  
  
-   [https://login.microsoftonline.com/consumers/]([!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)]).  
  
-   [https://login.microsoftonline.com/consumers/]([!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]).  
  
-   [https://login.microsoftonline.com/consumers/]([!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]).  
  
Obwohl [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] es Ihnen ermöglicht, mit Abfragen zu arbeiten, ohne zuerst eine Verbindung mit einer Datenquelle herzustellen, ist für die meisten anderen Aufgaben eine Verbindung erforderlich. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] stellt das Dialogfeld **Verbindung mit Server herstellen** bereit, um Verbindungseigenschaften für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten zu konfigurieren. Wenn [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] gestartet wird, wird das Dialogfeld **Verbindung mit Server herstellen** geöffnet, und Sie werden aufgefordert, eine Verbindung mit einem Server herzustellen. Das Dialogfeld **Verbindung mit Server herstellen** behält die Verbindungseinstellungen vom vorherigen Mal bei.  
  
> [!NOTE]  
> Diese Funktion lässt sich deaktivieren, sodass keine automatische Initialisierung einer Verbindung stattfindet. Weitere Informationen finden Sie unter [Startoptionen für den Datenbank-Engine-Dienst](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
## <a name="saving-connections"></a>Speichern von Verbindungen  
Sie können Verbindungen mit bestimmten Servern in der Liste der registrierten Server speichern, oder Sie können mit dem Projektmappen-Explorer Verbindungen in Projekten speichern.  
  
### <a name="saving-connections-in-registered-servers"></a>Speichern von Verbindungen in der Liste der registrierten Server  
Wenn Sie einen Server registrieren, speichert [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] die Verbindungsinformationen in der Liste der registrierten Server. Um eine Verbindung mit einem registrierten Server herzustellen, doppelklicken Sie in der Liste der registrierten Server auf den Servernamen. Daraufhin öffnet der Objekt-Explorer eine Verbindung zum Server.  
  
### <a name="saving-connections-in-solution-explorer"></a>Speichern von Verbindungen im Projektmappen-Explorer  
Mit dem Projektmappen-Explorer können Sie zugehörige Abfragen, Skripts, Verbindungen und andere Informationen in einem Projekt speichern. Jedes Skriptprojekt enthält einen Knoten namens **Verbindungen**, in dem Sie eine oder mehrere Verbindungen speichern können. Klicken Sie zum Hinzufügen einer Verbindung mit der rechten Maustaste auf **Verbindungen**, und klicken Sie dann auf **Neue Verbindung**. Erweitern Sie zum Zugreifen auf eine gespeicherte Verbindung **Verbindungen** , und doppelklicken Sie auf die Verbindung. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] öffnet ein dieser Verbindung zugeordnetes Abfragefenster. Beim Speichern behalten Skripts die Verknüpfung zu einer bestimmten Verbindung bei.  
  
## <a name="see-also"></a>Weitere Informationen  
[Verwenden von SQL Server Management Studio](../../ssms/use-sql-server-management-studio.md)  
[Objekt-Explorers](../../ssms/object/object-explorer.md)  
  
