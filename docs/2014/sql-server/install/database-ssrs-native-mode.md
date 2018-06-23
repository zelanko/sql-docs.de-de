---
title: Datenbank (SSRS-Modus) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 4c8ff22e9edee8af2af4b948289b56c3078e4232
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056650"
---
# <a name="database-ssrs-native-mode"></a>Datenbank (einheitlicher SSRS-Modus)
  Auf der Seite Setup der Datenbank können Sie die Berichtsserver-Datenbanken erstellen und konfigurieren, die den internen Speicher für eine oder mehrere Berichtsserverinstanzen bereitstellen. Wenn Sie einen Berichtsserver für eine Remoteberichtsserver-Datenbank konfigurieren, müssen Sie verwenden die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager zum Erstellen der Datenbank.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Das Erstellen einer Berichtsserver-Datenbank und die Konfiguration der Verbindung erfolgt in mehreren Schritten. Diese Seite enthält für jeden Tasktyp einen Assistenten, der Sie durch diese Schritte leitet. Berechtigungen und Anmeldungen werden automatisch für Sie erstellt oder aktualisiert. Sie können den Status jedes Schritts auf der Seite Status überwachen. Wenn ein Fehler auftritt, können Sie auf den Fehler klicken, um Informationen zur Fehlerbehebung zu erhalten.  
  
 Eine Berichtsserver-Datenbank muss einen bestimmten Servermodus unterstützen. Der Standardmodus ist der einheitliche Modus; Sie können aber auch eine Berichtsserver-Datenbank für den integrierten SharePoint-Modus erstellen, wenn Sie einen Berichtsserver in einer größeren Bereitstellung eines SharePoint-Produkts oder einer SharePoint-Technologie ausführen. Weitere Informationen finden Sie unter [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 Um diese Seite zu öffnen, starten die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Konfigurations-Manager, und klicken Sie auf **Datenbank** im Navigationsbereich. Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Tastatur  
 **SQL Server-Name**  
 In der aktuellen Berichtsserverdatenbank **SQL Server-Name** gibt den Namen des der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] , die die Berichtsserver-Datenbank ausgeführt wird. Sie können eine Standardinstanz oder eine benannte Instanz auf einem lokalen oder einem Remotecomputer verwenden.  
  
 **Database Name**  
 Gibt den Namen der Berichtsserver-Datenbank an, die die Serverdaten speichert.  
  
 **Berichtsserver-Modus**  
 Zeigt an, ob die Berichtsserver-Datenbank den einheitlichen Modus oder den integrierten SharePoint-Modus unterstützt. Weitere Informationen finden Sie unter [Reporting Services-Berichtsserver](../../../2014/reporting-services/reporting-services-report-server.md).  
  
 **Änderungsdatenbank**  
 Starten Sie einen Assistenten, der Sie durch alle Schritte führt, die zur Erstellung oder Auswahl einer Berichtsserver-Datenbank erforderlich sind.  
  
 **Typ der Anmeldeinformationen**  
 Gibt die Anmeldeinformationen an, die vom Berichtsserver zum Herstellen der Verbindung zur Berichtsserver-Datenbank verwendet werden. Anmeldeinformationen können Sie angeben, gehören das Dienstkonto, ein Windows-Domänenbenutzer, lokaler Windows-Benutzer oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datenbankanmeldung. Weitere Informationen zur Auswahl der Anmeldeinformationen finden Sie unter [Konfigurieren einer Berichtsserver-Datenbankverbindung &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Benutzername**  
 Gibt ein Domänenbenutzerkonto an, bei Verwendung der Windows-Anmeldeinformationen oder eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung bei Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldeinformationen. Wenn Sie Windows-Anmeldeinformationen verwenden, geben sie im folgenden Format:  *\<Domäne >\\< Konto\>*.  
  
 **Kennwort**  
 Gibt das Kennwort für das Konto an.  
  
 **Ändern von Anmeldeinformationen**  
 Starten Sie einen Assistenten, der Sie durch alle Schritte führt, die zur Auswahl eines anderen Kontos oder zum Aktualisieren des Kennworts für das Konto erforderlich sind, über das Sie die Verbindung zur Berichtsserver-Datenbank herstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Berichtsserver-Datenbank im einheitlichen Modus &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services-Konfigurationsmanager-F1-Hilfethemen &#40;SSRS im einheitlichen Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Konfigurieren Sie eine Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  