---
title: Verwalten von Servern mit SQL Server Management Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 095c9f205a98b5ac2ecd5a40ab66448ad9e21176
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308870"
---
# <a name="administer-servers-with-sql-server-management-studio"></a>Verwalten von Servern mit SQL Server Management Studio
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ist eine funktionsreiche, integrierte Verwaltungsclient erfüllen die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Anforderungen des Administrators. In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]werden administrative Tasks mit dem Objekt-Explorer ausgeführt, mit dem Sie eine Verbindung mit einem beliebigen Server der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Produktfamilie herstellen und dessen Inhalt grafisch dargestellt durchsuchen können. Ein Server kann eine Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] oder [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sein.  
  
 Zu den Toolkomponenten von [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] zählen registrierte Server, der Objekt-Explorer, der Projektmappen-Explorer, der Vorlagen-Explorer, die Seite Details zum Objekt-Explorer und das Dokumentenfenster. Um ein Tool anzuzeigen, klicken Sie im Menü **Ansicht** auf den Namen des Tools. Um den Abfrage-Editor anzuzeigen, klicken Sie auf der Symbolleiste auf die Schaltfläche **Neue Abfrage** .  
  
> [!IMPORTANT]  
>  Der Netzwerkverkehr zwischen [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] und [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist standardmäßig unverschlüsselt. Sie sollten in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] nur mit vertraulichen Daten (einschließlich Kennwörtern) arbeiten, wenn Sie eine verschlüsselte Verbindung hergestellt haben. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &amp;#40;SQL Server-Konfigurations-Manager&amp;#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 Verwenden Sie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] für Folgendes:  
  
-   Registrieren von Servern.  
  
-   Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssAS](../includes/ssas-md.md)], [!INCLUDE[ssRS](../includes/ssrs-md.md)] oder [!INCLUDE[ssIS](../includes/ssis-md.md)].  
  
-   Konfigurieren von Servereigenschaften.  
  
-   Verwalten von Datenbank- und [!INCLUDE[ssAS](../includes/ssas-md.md)] -Objekten wie Cubes, Dimensionen und Assemblys.  
  
-   Erstellen von Objekten wie Datenbanken, Tabellen, Cubes, Datenbankbenutzer und Anmeldenamen.  
  
-   Verwalten von Dateien und Dateigruppen.  
  
-   Anfügen oder Trennen von Datenbanken.  
  
-   Starten von Skriptingtools.  
  
-   Verwalten der Sicherheit.  
  
-   Anzeigen von Systemprotokollen.  
  
-   Überwachen der aktuellen Aktivität.  
  
-   Konfigurieren der Replikation.  
  
-   Verwalten von Volltextindizes.  
  
 Um [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] oder den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent zu starten und zu beenden, verwenden Sie den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)   
 [Anzeigen oder Ändern von Servereigenschaften &#40;SQL Server&#41;](../database-engine/configure-windows/view-or-change-server-properties-sql-server.md)  
  
  
