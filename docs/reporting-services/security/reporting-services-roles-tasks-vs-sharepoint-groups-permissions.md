---
description: Reporting Services-Rollen/Tasks im Vergleich zu SharePoint-Gruppen/Berechtigungen
title: Reporting Services-Rollen/Tasks im Vergleich zu SharePoint-Gruppen/Berechtigungen | Microsoft-Dokumentation
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- security [Reporting Services], tasks
- roles [Reporting Services], predefined
- SharePoint integration [Reporting Services], permissions
- permissions [Reporting Services], native mode
- security [Reporting Services], predefined roles
- security [Reporting Services], SharePoint integrated mode
ms.assetid: 429f1dbb-183a-4097-bd1b-693da9fe7a36
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2abd5aa8f15a0213a8eccee0965688cf626abc02
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91988146"
---
# <a name="reporting-services-roles-tasks-vs-sharepoint-groups-permissions"></a>Reporting Services-Rollen/Tasks im Vergleich zu SharePoint-Gruppen/Berechtigungen
  In diesem Thema werden rollen- und taskbasierte Autorisierungsfunktionen im einheitlichen Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mit den Sicherheitsfunktionen in SharePoint-Produkten verglichen. In diesem Thema werden die Terminologie und Merkmale von Rollen, Tasks, SharePoint-Gruppen, Berechtigungsstufen und Berechtigungen verglichen.  
  
[!INCLUDE[applies](../../includes/applies-md.md)]

:::row:::
    :::column:::
        [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus  
        SharePoint 2010 und SharePoint 2013  
    :::column-end:::
    :::column:::
        [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus  
    :::column-end:::
:::row-end:::



  
 **In diesem Thema:**  
  
-   [Vergleich zwischen Berechtigungstools und zugehöriger Terminologie](#bkmk_compare_tools_terms)  
  
-   [Vergleich zwischen Rollen im einheitlichen Modus und SharePoint-Gruppen](#bkmk_compare_roles_groups)  
  
-   [Vergleich zwischen Tasks im einheitlichen Modus und SharePoint-Berechtigungen](#bkmk_compare_tasks_permissions)  
  
##  <a name="compare-permission-tools-and-terminology"></a><a name="bkmk_compare_tools_terms"></a> Vergleich zwischen Berechtigungstools und zugehöriger Terminologie  
 **Einheitlicher Modus:** Die Berechtigungsobjekte von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus (Rollen und Tasks) werden in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] erstellt und im Berichts-Manager für einzelne Benutzer konfiguriert.  
  
 **SharePoint-Modus:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] werden die SharePoint-Berechtigungsfunktionen genutzt. SharePoint-Gruppen und -Berechtigungen werden auf der folgenden Seite für **Siteeinstellungen** verwaltet.  
  
 In der folgenden Tabelle werden die Objekte und Konzepte von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus und SharePoint im Hinblick auf Berechtigungen verglichen.  
  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus|SharePoint|  
|---------------------------------------------|----------------|  
|**Rolle:** beispielsweise „Inhalts-Manager“.|**Gruppe:** beispielsweise die Standardgruppe „Viewers“ (Anzeigende Benutzer).|  
|---|**Berechtigungsstufe der Gruppe:** beispielsweise „View Only“ (Nur anzeigen) für die Gruppe „Viewers“ (Anzeigende Benutzer).|  
|**Tasks:** Beispielsweise „Berichte verwalten“.|**Berechtigungen:** Die Gruppe mit der Berechtigung „View Only“ (Nur anzeigen) enthält beispielsweise listenbezogene Berechtigungen für die Elemente, Versionen und Anwendungsseiten von Ansichten.|  
  
 Weitere Informationen zu SharePoint-Berechtigungen finden Sie unter [Berechtigungsstufen und Berechtigungen](https://support.office.com/article/Understand-groups-and-permissions-on-a-SharePoint-site-258E5F33-1B5A-4766-A503-D86655CF950D) und [Bestimmen von Berechtigungsstufen und Gruppen in SharePoint 2013](/SharePoint/sites/determine-permission-levels-and-groups-in-sharepoint-server).  
  
##  <a name="compare-native-mode-roles-and-sharepoint-groups"></a><a name="bkmk_compare_roles_groups"></a> Vergleich zwischen Rollen im einheitlichen Modus und SharePoint-Gruppen  
 Die folgende Tabelle enthält eine Gegenüberstellung der vordefinierten Rollendefinitionen in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus und der SharePoint-Standardgruppen. Wenn die SharePoint-Gruppen nicht mit der von Ihnen gewünschten Rolle übereinstimmen, können Sie eine benutzerdefinierte Gruppe erstellen und in SharePoint Berechtigungsstufen zuweisen.  
  
 **Hinweis**: Die verfügbaren SharePoint-Standardgruppen hängen von der Websitevorlage ab, die verwendet wird, um die SharePoint-Website zu erstellen.  
  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Rolle|SharePoint-Gruppen|  
|--------------------------------------|-----------------------|  
|**Browser**<br /><br /> Ansicht|Verwenden Sie die Gruppe **Besucher** , um Berechtigungen zum Anzeigen von Berichten zu erteilen. Die Gruppe **Besucher** verfügt über die Berechtigungsstufe Lesen, mit der Gruppenmitglieder Seiten, Listenelemente und Dokumente anzeigen können.|  
|**Inhalts-Manager**<br /><br /> Volle Berechtigungen für alle Elemente und Vorgänge auf Elementebene, einschließlich Berechtigungen zum Festlegen der Sicherheit.|Mit der Gruppe **Besitzer** gewähren Sie volle Kontrolle über die Verwaltung von Berichtsserverelementen auf einer SharePoint-Website. Die Gruppe **Besitzer** verfügt über die Berechtigungen Vollzugriff, mit denen Gruppenmitglieder Änderungen am Websiteinhalt, einzelnen Webseiten oder der Funktionalität vornehmen können. Der Vollzugriff sollte nur Websiteadministratoren gewährt werden.|  
|**Meine Berichte**|Es ist keine entsprechende Gruppe vorhanden. **Meine Berichte** wird auf einem Berichtsserver, der im SharePoint-Modus ausgeführt wird, nicht unterstützt. Wenn Sie eine entsprechende Funktionalität wünschen, können Sie die Funktionen für Meine Website [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] in  verwenden.|  
|**Publisher**<br /><br /> Berichte, Berichtsmodelle, freigegebene Datenquellen und Ressourcen hinzufügen, aktualisieren, anzeigen und löschen.|Mit der Gruppe **Mitglieder** erteilen Sie Berechtigungen zum Hinzufügen von Elementen, Bearbeiten von Elementen und Aktualisieren von Verweisen auf abhängige Elemente auf einer SharePoint-Website. Die Gruppe **Mitglieder** verfügt über die Berechtigungsebene Teilnehmen, mit der Gruppenmitglieder Seiten anzeigen, Elemente hinzufügen und aktualisieren sowie Änderungen zur Genehmigung übermitteln können.|  
|**Report Builder**<br /><br /> Berichte anzeigen, einzelne Abonnements selbst verwalten und Berichte im Berichts-Generator öffnen.|Der Berichtsdefinition Berichts-Generator entspricht keine vordefinierte Berechtigungsebene oder SharePoint-Gruppe. In der Standardeinstellung verfügen Benutzer, die der Gruppe **Mitglieder** oder **Besitzer** angehören, über die Berechtigung zum Verwenden des Berichts-Generators. Wenn Sie den Berichts-Generator anderen Benutzern zur Verfügung stellen möchten, sollten Sie benutzerdefinierte Sicherheitseinstellungen erstellen, um eine Berechtigungsebene bereitzustellen, die den Funktionen der Berichts-Generator-Rolle ähnelt. Weitere Informationen finden Sie unter [Festlegen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../../reporting-services/security/set-permissions-for-report-server-items-on-a-sharepoint-site.md).|  
|-|Verwenden Sie die Gruppe **Anzeigende Benutzer** , um Berechtigungen zum Anzeigen gerenderter Berichte zu erteilen. Mitglieder der Gruppe **Anzeigende Benutzer** sind nicht in der Lage, den Inhalt von Berichtselementen herunterzuladen oder anzuzeigen.<br /><br /> **Hinweis:** Ab SQL Server 2012 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]hat die Gruppe **Viewer** keine Berechtigungen zur Erstellung von Abonnements.|  
|**Systembenutzer** und **Systemadministrator**|Diese Rollen sind für einen Berichtsserver, der im SharePoint-Modus ausgeführt wird, nicht erforderlich. **Systembenutzer** und **Systemadministrator** entsprechen den SharePoint-Berechtigungen auf Farm- oder Webanwendungsebene. Der Berichtsserver stellt keine Funktionalität bereit, die eine Autorisierung auf dieser Ebene erfordert.|  
  
##  <a name="comparing-native-mode-tasks-and-sharepoint-permissions"></a><a name="bkmk_compare_tasks_permissions"></a> Vergleich zwischen Tasks im einheitlichen Modus und SharePoint-Berechtigungen  
 Die folgende Tabelle enthält eine Gegenüberstellung der Tasks von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus und SharePoint-Berechtigungen. In der Spalte **Typ** ist angegeben, ob sich der Task im einheitlichen Modus auf eine Systemrolle oder Standardrolle und zugehörige Elemente bezieht. Mit Systemrollen werden Berechtigungen auf Systemebene verwaltet, beispielsweise freigegebene Zeitpläne.  
  
|Task im einheitlichen Modus|Rollentyp|Entsprechende SharePoint-Berechtigung|  
|----------------------|---------------|--------------------------------------|  
|Berichte lesen|Artikel|Elemente bearbeiten, Elemente anzeigen|  
|Verknüpfte Berichte erstellen|Artikel|Wird nicht unterstützt.|  
|Alle Abonnements verwalten|Artikel|Verwalten von Warnungen|  
|Datenquellen verwalten|Artikel|Elemente hinzufügen, Elemente bearbeiten, Elemente löschen, Elemente anzeigen|  
|Ordner verwalten|Artikel|Elemente hinzufügen, Elemente bearbeiten, Elemente löschen, Elemente anzeigen|  
|Einzelne Abonnements verwalten|Artikel|Elemente bearbeiten<br /><br /> Vor [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]lautete die erforderliche Berechtigungsstufe "Warnungen erstellen".|  
|Verwalten von Modellen|Artikel|Elemente hinzufügen, Elemente bearbeiten, Elemente löschen, Elemente anzeigen|  
|Berichtsverlauf verwalten|Artikel|Elemente bearbeiten, Versionen anzeigen, Versionen löschen|  
|Berichte verwalten|Artikel|Elemente hinzufügen, Elemente bearbeiten, Elemente löschen, Elemente anzeigen|  
|Ressourcen verwalten|Artikel|Elemente hinzufügen, Elemente bearbeiten, Elemente löschen, Elemente anzeigen|  
|Sicherheit für einzelne Elemente festlegen|Artikel|Verwalten von Berechtigungen|  
|Datenquellen anzeigen|Artikel|Elemente anzeigen|  
|Ordner anzeigen|Artikel|Elemente anzeigen|  
|Modelle anzeigen|Artikel|Elemente anzeigen|  
|Berichte anzeigen|Artikel|Elemente anzeigen|  
|Ressourcen anzeigen|Artikel|Elemente anzeigen|  
||||  
|Berichtsdefinitionen ausführen|System|Elemente anzeigen|  
|Ereignisse generieren|System|Website verwalten|  
|Aufträge verwalten|System|Keine (nicht unterstützt)|  
|Berichtsservereigenschaften verwalten|System|Keine (nicht zutreffend) Es wird vom Berichtsserver nicht kontrolliert, ob ein Benutzer über die Berechtigung zum Anzeigen der Integrationseinstellungen in der Zentraladministration verfügt.|  
|Verwalten von Rollen|System|Berechtigungen verwalten|  
|Freigegebene Zeitpläne verwalten|System|Website verwalten, öffnen|  
|Berichtsserversicherheit verwalten|System|Keine (nicht zutreffend) Für den Berichtsserver werden auf einem Server, der im integrierten SharePoint-Modus ausgeführt wird, keine Rollenzuweisungen auf Systemebene verwendet.|  
|Berichtsservereigenschaften anzeigen|System|Keine (nicht zutreffend) Es wird vom Berichtsserver nicht kontrolliert, ob ein Benutzer über die Berechtigung zum Anzeigen der Integrationseinstellungen in der Zentraladministration verfügt.|  
|Freigegebene Zeitpläne anzeigen|System|Elemente öffnen|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../../reporting-services/security/set-permissions-for-report-server-items-on-a-sharepoint-site.md)   
 [Festlegen von Berechtigungen für Berichtsservervorgänge in einer SharePoint-Webanwendung](../../reporting-services/security/set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md)   
 [Erteilen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Rollendefinitionen](../../reporting-services/security/role-definitions.md)   
 [Vordefinierte Rollen](../../reporting-services/security/role-definitions-predefined-roles.md)  
  
