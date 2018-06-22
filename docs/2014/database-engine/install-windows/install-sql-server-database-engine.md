---
title: Über das SQL Server-Datenbankmodul | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
caps.latest.revision: 44
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4316e91e465922ca1f7c428a9f25e781837ec6e4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059878"
---
# <a name="about-the-sql-server-database-engine"></a>Informationen zur SQL Server-Datenbank-Engine
  Bei der Komponente [!INCLUDE[ssDE](../../includes/ssde-md.md)] von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] handelt es sich um den zentralen Dienst zum Speichern, Verarbeiten und Sichern von Daten. Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] bietet gesteuerten Zugriff und eine zügige Transaktionsverarbeitung und erfüllt damit die Anforderungen selbst der anspruchsvollsten datenlastigen Anwendungen des Unternehmens.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt bis zu 50 Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] auf einem einzelnen Computer. Erstellen einer typischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation finden Sie unter [Installieren von SQL Server 2014 vom Installations-Assistenten &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md).  
  
 **Wichtig** Bei einer lokalen Installation müssen Sie Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.  
  
 Wenn Sie im Installations-Assistenten von **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf der Seite Zu installierende Komponenten die Option** -Datenbank-Engine[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auswählen, werden folgenden Funktionen installiert:  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   Replikation – optionale Komponente  
  
-   Volltextsuche – optionale Komponente  
  
-   Data Quality Services – optionale Komponente  
  
    > [!NOTE]  
    >  In dieser Version wird durch Aktivieren des Kontrollkästchens **Data Quality Services** während des Setups DQS (Data Quality Services)-Server nicht installiert. Sie müssen nach der Installation weitere Schritte ausführen, um DQS-Server zu installieren. Weitere Informationen finden Sie unter [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
 In vielen typischen Benutzerszenarien sind die folgenden zusätzlichen Funktionen als Optionen verfügbar:  
  
-   Data Quality Client  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Konnektivitätskomponenten  
  
-   Programmiermodelle  
  
-   Verwaltungstools  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   Dokumentationskomponenten  
  
> [!NOTE]  
>  Standardmäßig werden Beispieldatenbanken und Beispielcode nicht als Teil des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setups installiert. Informationen zur Installation von Beispieldatenbanken und Beispielcode finden Sie auf der [CodePlex-Website](http://go.microsoft.com/fwlink/?LinkId=87843).  
  
## <a name="see-also"></a>Siehe auch  
 [Von den Editionen von SQLServer 2014 unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Editionen und Komponenten von SQLServer 2014](../../sql-server/editions-and-components-of-sql-server-2016.md)   
 [Planen einer SQL Server-Installation](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Lösungen mit hoher Verfügbarkeit &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Aktualisieren auf SQL Server 2014 mithilfe des Installations-Assistenten &#40;Setup&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  