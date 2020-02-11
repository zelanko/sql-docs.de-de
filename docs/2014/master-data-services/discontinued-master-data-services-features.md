---
title: Nicht mehr unterstützte Master Data Services Features in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3236cce0-cfd9-43f8-8be3-e8c8dff8f162
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3f1eb85cb05c8284990d46241ed752515ef5504b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479445"
---
# <a name="discontinued-master-data-services-features-in-sql-server-2014"></a>Eingestellte Master Data Services-Funktionen in SQL Server 2014
  In diesem Thema werden die Funktionen von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] beschrieben, die in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]nicht mehr verfügbar sind.  
  
## <a name="includesssql14includessssql14-mdmd-discontinued-features"></a>
  [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] nicht mehr unterstützte Funktionen  
 Bestimmte Funktionen werden in dieser Version nicht mehr unterstützt.  
  
## <a name="includesssql11includessssql11-mdmd-discontinued-features"></a>
  [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] nicht mehr unterstützte Funktionen  
  
### <a name="security"></a>Sicherheit  
 Um das Zuweisen der Sicherheit einfacher zu machen, können Sie der abgeleiteten Hierarchie, der expliziten Hierarchie und den Attributgruppenobjekten keine Modellobjektberechtigungen mehr zuweisen.  
  
-   Abgeleitete Hierarchieberechtigungen basieren jetzt auf dem Modell. Wenn Sie z. b. möchten, dass ein Benutzer über die Berechtigung für eine abgeleitete Hierarchie verfügt, müssen Sie dem Modell Objekt ein **Update** zuweisen. Anschließend können Sie allen Entitäten, auf die der Benutzer keinen Zugriff haben soll, Zugriff **verweigern** zuweisen.  
  
-   Explizite Hierarchieberechtigungen basieren jetzt auf der Entität. Wenn der Benutzer z. b. über **Aktualisierungs** Berechtigungen für eine Konto Entität verfügt, können alle expliziten Hierarchien der Entität aktualisiert werden.  
  
-   Attribut Gruppenberechtigungen können nicht mehr im Funktionsbereich **Benutzer-und Gruppenberechtigungen** zugewiesen werden. Stattdessen können Benutzern und Gruppen im Funktionsbereich **System Verwaltung** , in dem Attribut Gruppen erstellt werden, die Berechtigung **Aktualisieren** für Attribut Gruppen erteilt werden. Die Schreib **geschützte Berechtigung für** Attribut Gruppen ist nicht mehr verfügbar.  
  
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
 Geschäftsregeln, die automatisch Werte für das Code-Attribut generieren, werden jetzt anders verwaltet. Zuvor haben Sie zum Generieren von Werten für das Code-Attribut im Funktionsbereich **System Verwaltung** unter **Geschäftsregeln**das **default-Attribut für eine generierte Wert** Aktion verwendet. Nun müssen Sie in der **System Verwaltung**die Entität bearbeiten, um automatisch generierte Codewerte zu aktivieren. Weitere Informationen finden Sie unter [Automatische Codeerstellung &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).  
  
 Wenn Sie bei einem [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]-Modellbereitstellungspaket, das eine Regel dieses Typs enthält, die Datenbank auf [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] aktualisieren, wird die Geschäftsregel ausgeschlossen.  
  
### <a name="bulk-updates-and-exporting"></a>Massenaktualisierungen und -export  
 In der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Webanwendung können Sie keine Attributwerte für mehrere Elemente im Stapel mehr aktualisieren. Verwenden Sie zum Ausführen von Massen Aktualisierungen den Stagingprozess [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]oder den.  
  
 In der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Webanwendung können Sie keine Elemente mehr nach Excel exportieren. Verwenden [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]Sie, um mit Membern in Excel zu arbeiten.  
  
### <a name="transactions"></a>Transaktionen  
 Im Funktionsbereich **Explorer** können Benutzer ihre eigenen Transaktionen nicht mehr zurücksetzen. Zuvor konnten Benutzer Änderungen, die Sie an Daten im **Explorer**vorgenommen haben, zurücksetzen. Administratoren können weiterhin Transaktionen für alle Benutzer im Funktionsbereich **Versionsverwaltung** zurücksetzen.  
  
 Anmerkungen sind jetzt dauerhaft und können nicht gelöscht werden. Zuvor wurden Anmerkungen als Transaktionen angesehen und durch das Wiederherstellen der Transaktion gelöscht.  
  
### <a name="web-service"></a>Webdienst  
 Der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Webdienst wird jetzt automatisch aktiviert, wie in Silverlight erforderlich. Zuvor musste der Webdienst manuell aktiviert werden.  
  
### <a name="powershell-cmdlets"></a>PowerShell-Cmdlets  
 MDS schließt keine PowerShell-Cmdlets mehr ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veraltete Master Data Services-Funktionen in SQL Server 2014](deprecated-master-data-services-features.md)  
  
  
