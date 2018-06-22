---
title: Nicht mehr unterstützte Funktionen von Master Data Services in SQLServer 2014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3236cce0-cfd9-43f8-8be3-e8c8dff8f162
caps.latest.revision: 12
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 46f5d4de97af6822ba110fe35e81df2d13a526ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149088"
---
# <a name="discontinued-master-data-services-features-in-sql-server-2014"></a>Eingestellte Master Data Services-Funktionen in SQL Server 2014
  In diesem Thema werden die Funktionen von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] beschrieben, die in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]nicht mehr verfügbar sind.  
  
## <a name="includesssql14includessssql14-mdmd-discontinued-features"></a>In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] nicht mehr unterstützte Funktionen  
 Bestimmte Funktionen werden in dieser Version nicht mehr unterstützt.  
  
## <a name="includesssql11includessssql11-mdmd-discontinued-features"></a>In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] nicht mehr unterstützte Funktionen  
  
### <a name="security"></a>Security  
 Um das Zuweisen der Sicherheit einfacher zu machen, können Sie der abgeleiteten Hierarchie, der expliziten Hierarchie und den Attributgruppenobjekten keine Modellobjektberechtigungen mehr zuweisen.  
  
-   Abgeleitete Hierarchieberechtigungen basieren jetzt auf dem Modell. Z. B. wenn ein Benutzer über die Berechtigung für eine abgeleitete Hierarchie verfügen soll, Sie müssen zuweisen **Update** für das Modellobjekt. Sie zuweisen können **Deny** Zugriff auf alle Entitäten, die nicht die Benutzer Zugriff haben soll.  
  
-   Explizite Hierarchieberechtigungen basieren jetzt auf der Entität. Wenn der Benutzer hat z. B. **Update** Berechtigungen für eine Account-Entität, alle explizite Hierarchien für die Entität werden aktualisiert werden.  
  
-   Attributgruppenberechtigungen können nicht mehr zugewiesen werden, der **Benutzer- und Gruppenberechtigungen** Funktionsbereich ". Stattdessen in den **Systemverwaltung** Funktionsbereich ", in dem Attributgruppen erstellt werden, Benutzer und Gruppen können angegeben werden **Update** Berechtigung Attributgruppen. **Nur-Lese** Berechtigungen für Attributgruppen ist nicht mehr verfügbar.  
  
### <a name="staging-process"></a>Stagingprozess  
 Sie können den neuen Stagingprozess nicht für folgende Aufgaben verwenden:  
  
-   Erstellen oder Löschen von Auflistungen  
  
-   Hinzufügen von Mitgliedern zu Auflistungen oder Entfernen von Mitgliedern daraus  
  
-   Erneutes Aktivieren von Mitgliedern und Auflistungen.  
  
 Sie können den [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]-Stagingprozess für die Arbeit mit Auflistungen verwenden.  
  
### <a name="model-deployment-wizard"></a>Modellbereitstellungs-Assistent  
 Pakete, die Daten enthalten, können nicht mehr mit dem Assistenten in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Webanwendung erstellt und bereitgestellt werden. Ein neues Befehlszeilen-Hilfsprogramm kann stattdessen verwendet werden. Weitere Informationen finden Sie unter [Bereitstellen von Modellen &#40;Master Data Services&#41;](deploying-models-master-data-services.md).  
  
 Der Assistent kann dennoch zum Erstellen und Bereitstellen von Paketen verwendet werden, die keine Daten enthalten.  
  
 Außerdem können Pakete nur in der Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bereitgestellt werden, in der sie erstellt wurden. Dies bedeutet, dass in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] erstellte Pakete nicht in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]bereitgestellt werden können. Sie müssen das Paket in einer [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]-Umgebung bereitstellen und dann die Datenbank auf [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] aktualisieren.  
  
### <a name="code-generation-business-rules"></a>Geschäftsregeln zur Codegenerierung  
 Geschäftsregeln, die automatisch Werte für das Code-Attribut generieren, werden jetzt anders verwaltet. Um Werte für das Code-Attribut zu generieren, verwendet Sie zuvor die **Standardattribut für einen generierten Wert** Aktion in der **Systemverwaltung** Funktionsbereich "unter" **Geschäftsregeln** . Im **Systemverwaltung**, müssen Sie bearbeiten, die Entität aus, um automatisch generierte Codewerte zu aktivieren. Weitere Informationen finden Sie unter [Automatische Codeerstellung &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).  
  
 Wenn Sie bei einem [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]-Modellbereitstellungspaket, das eine Regel dieses Typs enthält, die Datenbank auf [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] aktualisieren, wird die Geschäftsregel ausgeschlossen.  
  
### <a name="bulk-updates-and-exporting"></a>Massenaktualisierungen und -export  
 In der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Webanwendung können Sie keine Attributwerte für mehrere Elemente im Stapel mehr aktualisieren. Um massenaktualisierungen auszuführen, verwenden Sie den Stagingprozess oder den [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].  
  
 In der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Webanwendung können Sie keine Elemente mehr nach Excel exportieren. Verwenden Sie zum Arbeiten mit Elementen in Excel die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].  
  
### <a name="transactions"></a>Transaktionen  
 In der **Explorer** Funktionsbereich ", Benutzer können nicht mehr wiederherstellen, ihre eigenen Transaktionen. Zuvor konnten Benutzer Änderungen vorgenommen, Daten in wurden wiederherstellen **Explorer**. Administratoren können weiterhin Transaktionen für alle Benutzer im Wiederherstellen der **Versionsverwaltung** Funktionsbereich ".  
  
 Anmerkungen sind jetzt dauerhaft und können nicht gelöscht werden. Zuvor wurden Anmerkungen als Transaktionen angesehen und durch das Wiederherstellen der Transaktion gelöscht.  
  
### <a name="web-service"></a>Webdienst  
 Der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Webdienst wird jetzt automatisch aktiviert, wie in Silverlight erforderlich. Zuvor musste der Webdienst manuell aktiviert werden.  
  
### <a name="powershell-cmdlets"></a>PowerShell-Cmdlets  
 MDS schließt keine PowerShell-Cmdlets mehr ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Veraltete Master Data Services-Features in SQL Server 2014](deprecated-master-data-services-features.md)  
  
  