---
title: Beispiellizenztopologien und-Kosten für SQL Server 2014 Self-Service-Business Intelligence | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 682b8711-407a-48d1-9807-415d4c24dad6
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4672647d8e9caae94e3b64fc43c3b687aa010920
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185799"
---
# <a name="example-license-topologies-and-costs--for-sql-server-2014-self-service-business-intelligence"></a>Beispiellizenztopologien und -kosten für SQL Server-Self-Service-Business Intelligence 2014
  In diesem Thema werden allgemeine Informationen zum Auswählen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Business Intelligence Edition oder die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition. Dieses Thema enthält einige lokale Beispieltopologien für Microsoft-Self-Service-Business Intelligence (BI). Die Beispiele enthalten die Editionen und Lizenzen, mit denen Sie das Gleichgewicht zwischen Kosten und Leistung verbessern können. Die Topologien, die Anzahl der Server und die Kosten der Lizenzierung werden **nur beispielhaft**dargestellt. Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und Microsoft SharePoint 2013 weisen einige Änderungen hinsichtlich der Lizenzierung auf. Es werden jetzt mehr Optionen zur Lizenzierung von Servern, Benutzern und Geräten zur Verfügung gestellt. Die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Lizenzierung unterstützt die gleichen Business Intelligence-bezogenen Szenarien.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ist in der Business Intelligence-Editionen verfügbar und ermöglicht die kernbasierte Lizenzierung in einigen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   In SharePoint 2013 wurde die Share Point-Server-Lizenzierung für das Extranet und das Internet vereinfacht, und die Optionen für SharePoint Online wurden verbessert.  
  
 Informieren Sie sich vor dem Kauf im Abschnitt "Erwerben" des jeweiligen Produkts, und wenden Sie sich an den zuständigen Vertreter von Microsoft oder einen Händler vor Ort, um genauere Informationen bezüglich Ihrer Lizenzierungsanforderungen zu erhalten. Weitere Informationen zu den neuesten Lizenzierungsplänen und -kosten finden Sie in den folgenden Themen:  
  
-   [Lizenzierungsinformationen – SQLServer 2014](http://www.microsoft.com/licensing/about-licensing/sql2014.aspx)  
  
-   [SharePoint 2013-Lizenzierung](http://office.microsoft.com/sharepoint/sharepoint-licensing-overview-collaboration-software-FX103789438.aspx).  
  
 **In diesem Thema:**  
  
-   [SQL Server Business Intelligence-Komponenten](#bkmk_bi_components)  
  
-   [SQL Server 2014-Lizenzierungszusammenfassung](#bkmk_sql_server_license)  
  
-   [SharePoint 2013-Lizenzierungszusammenfassung](#bkmk_sharepoint_license)  
  
-   [Topologie mit 3 Ebenen mit separaten PowerPivot-Servern](#bkmk_3tier_powerpivot)  
  
-   [Topologie mit 3 Ebenen](#bkmk_3tier)  
  
-   [Topologie mit 2 Ebenen](#bkmk_2tier)  
  
-   [Referenz-und Communityinhalte](#bkmk_reference)  
  
##  <a name="bkmk_bi_components"></a> SQL Server Business Intelligence-Komponenten  
 In diesem Thema liegt der Schwerpunkt auf SQL Server- und SharePoint-Server-Technologien. Die Kosten und Beispiele veranschaulichen nicht ausdrücklich Microsoft Windows Server- oder Microsoft Office-Komponenten, die Sie für eine vollständige Client- und Serverlösung benötigen. Die SQL Server-Business Intelligence-Komponenten, die in diesem Thema behandelt werden, sind SQL Server Reporting Services im SharePoint-Modus und PowerPivot für SharePoint. Die Komponenten umfassen folgende Funktionen:  
  
-   Interaktive PowerPivot-Arbeitsmappen im Browser  
  
-   Interaktive [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Berichte in SharePoint.  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Katalog, planmäßige Datenaktualisierung, Management-Dashboard  
  
-   Reporting Services im SharePoint-Modus einschließlich Datenwarnungen  
  
 Weitere Informationen finden Sie in der Funktionsübersicht in [installieren Sie SQL Server BI Features in SharePoint &#40;PowerPivot und Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md).  
  
## <a name="license-summary"></a>Lizenzzusammenfassung  
 In diesem Abschnitt werden die Zulassungsbestimmungen für SQL Server und SharePoint zusammengefasst. Die Informationen stellen eine allgemeine Zusammenfassung dar und decken nur die Szenarien ab, die in den Topologiediagrammen und Kostenbeispielen in diesem Dokument verwendet werden. Überprüfen Sie die Inhaltslinks auf detailliertere Lizenzierungsinformationen. Die Beispielpreise basieren auf Microsoft Open License Program (MOLP)-Preisen.  
  
 Üblicherweise wird **Enterprise Edition** für Server mit der SQL Server-Datenbank-Engine verwendet, und **Business Intelligence Edition** wird für Server mit Reporting Services oder PowerPivot für SharePoint verwendet. Die **Anzahl der Benutzer** und die **Anzahl der Serverkerne** in Ihrer Bereitstellung beeinflussen jedoch die Kosten der Bereitstellung sowie die Entscheidung der zu verwendenden Edition.  
  
###  <a name="bkmk_sql_server_license"></a> SQL Server 2014-Lizenzierungszusammenfassung  
  
-   Der SQL Server Enterprise Edition verwendet die kernbasierte Lizenzierung. Kernbasierte Lizenzen werden in **Zwei-Kern** -Paketen verkauft.  
  
-   Die SQL Server BI-Edition verwendet sowohl Server- als auch Client-Zugriffslizenzen (CAL).  
  
-   CAL-Lizenzen basieren auf den einzelnen Benutzer oder Geräten, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verbunden sind, und sind unabhängig von der Anzahl der Server, mit denen eine Verbindung besteht.  
  
-   Bei der kernbasierten Lizenzierung müssen alle Kerne im Server durch eine Lizenz abgedeckt sein. Für jeden physischen Prozessor im Server sind mindestens **vier** kernbasierte Lizenzen erforderlich.  
  
 In der folgenden Tabelle werden die Lizenzdetails zusammengefasst, die für Bereitstellungsentwürfe und die Lizenzkostenschätzung verwendet werden. **HINWEIS:**  Die angezeigten Preise dienen lediglich der Veranschaulichung.  
  
|SQL Server-Editionen|SQL Server-Lizenz + Client-Zugriffslizenz (CAL)|Kernbasierte SQL Server-Lizenz|  
|-------------------------|---------------------------------------------------------|-----------------------------------|  
|Enterprise|Nicht verfügbar|**(Ja)** $6874 X [Anzahl der Kerne X [Kernfaktor]|  
|Business Intelligence|**(Ja)** $8592 + $199 pro CAL|Nicht verfügbar|  
|Standard|**(Ja)**|**(Ja)**|  
  
 Weitere Informationen zum Beispiel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beispiellizenzpreisen, finden Sie unter:  
  
-   [Lizenzierung von virtuellen Umgebungen](http://www.microsoft.com/licensing/about-licensing/virtualization.aspx) (http://www.microsoft.com/licensing/about-licensing/virtualization.aspx).  
  
-   [SQL Server 2014-Lizenzierung Datenblatt – Microsoft-Homepage](http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf) (http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf).  
  
-   [SQL Server 2014-Editionen und Lizenzierung](http://www.microsoft.com/licensing/about-licensing/sql2014.aspx#tab=2)  
  
1.  **SQL Server-Annahmen und weitere Lizenzierungsinformationen:**  
  
2.  In den Diagrammen in diesem Thema wird die Enterprise Edition von SQL Server für Datenbankserver verwendet. Es stehen daher alle Funktionen für Hochverfügbarkeit wie AlwaysOn-Verfügbarkeitsgruppen bereit. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
3.  Die Server in diesem Beispiel sind jeweils 2 Intel Xeon-Prozessoren mit 6 Kernen, daher liegt ein **SQL Server-Kernfaktor** von **1** bei der Berechnung der Lizenzierungskosten zugrunde. Weitere Informationen zu Kernfaktoren und Lizenzierungskosten finden Sie unter [SQL Server-Prozessorkern-Faktortabelle](http://download.microsoft.com/download/9/B/F/9BF63163-D8F9-4339-90AA-EBC9AAFC49AD/SQL2012_CoreFactorTable_Mar2012.pdf) (http://download.microsoft.com/download/0/C/8/0C85665B-11EA-4FF5-B37C-8CC21CF95AC4/BizTalk%202013_CoreFactorTable_**3.19.2013**. v4.pdf).  
  
###  <a name="bkmk_sharepoint_license"></a> SharePoint 2013-Lizenzierungszusammenfassung  
 In der folgenden Liste ist das Lizenzmodell aufgeführt, das für den Bereitstellungsentwurf und Lizenzkostenschätzung verwendet wird. Die angezeigten Preise dienen lediglich der Veranschaulichung.  
  
1.  Eine SharePoint-Server-Lizenz ist für jede Instanz von Microsoft SharePoint Server erforderlich.  
  
2.  Um SharePoint Enterprise für alle Endbenutzer oder Endgeräte zu lizenzieren, kaufen Sie eine Microsoft SharePoint Server 2013 **Standard-CAL-Lizenz** zusätzlich zur Microsoft SharePoint Server 2013 **Enterprise-CAL-Lizenz**.  
  
3.  SharePoint-CAL-Lizenzen werden pro Benutzer oder Gerät gekauft, die auf den SharePoint-Server zugreifen. Es ist nicht erforderlich, CAL-Lizenzen für jeden Server zu erwerben.  
  
 Angenommen, Ihre Umgebung besteht aus 2 Instanzen mit 100 Benutzern, und Ihre angegebenen Kosten lauten wie folgt:  
  
-   Microsoft SharePoint Server 2013-Standard-CAL-Lizenz: **$107,99**  
  
-   Microsoft SharePoint Server 2013 Enterprise CAL-Lizenz: **$94.99**  
  
-   Microsoft SharePoint Server 2013-Lizenz: **$6,412.99**  
  
 Die Kosten in diesem Fall würden sich auf **$33.123,98**belaufen.  
  
-   CAL-Lizenz: ($107,99 +$94,99) X 100) =$20.298,00  
  
-   Server-Lizenz: ($6.412,99 X 2) =$12.825,98  
  
 **SharePoint-Annahmen und weitere Lizenzierungsinformationen:**  
  
 Die Beispielbereitstellungen sind allesamt Intranetumgebungen, daher ist eine SharePoint-CAL-Lizenzierung erforderlich.  
  
-   [Vollständige SharePoint-Liste der Lizenzierung](http://technet.microsoft.com/en-in/library/jj819267.aspx#bkmk_FeaturesOnPremise) (http://technet.microsoft.com/en-in/library/jj819267.aspx#bkmk_FeaturesOnPremise).  
  
-   [Informationen zum Kauf von SharePoint](http://sharepoint.microsoft.com/en-in/Pages/buy.aspx) (http://sharepoint.microsoft.com/en-in/Pages/buy.aspx).  
  
##  <a name="bkmk_3tier_powerpivot"></a> 3-tier-Topologie mit separaten [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Server  
 Dieses Beispiel veranschaulicht, dass bei 800 oder weniger Benutzern die Verwendung der SQL Server BI-Edition für die SharePoint-Anwendungsserver und [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint-Server am günstigsten ist. Ab 800 Benutzern ist jedoch die SQL Server Enterprise Edition günstiger. Die kernbasierte Lizenzierung ist unabhängig von der Anzahl der Benutzer. Beim Vergleich der Lizenzierungskosten für kernbasierte und CAL-Lizenzen gibt es daher einen Schwellenwert, wenn die Anzahl der Benutzer steigt. Jenseits dieses Schwellenwerts ist die Enterprise Edition die günstigere Lösung. Um den Kostenschwellenwert zu ermitteln, vergleichen Sie Kosten für die Anzahl der zu lizenzierenden Kerne mit der Anzahl der benötigten CAL-Lizenzen für Endbenutzer oder Endgeräte.  
  
-   Dieses Beispiel umfasst eine Intranetbereitstellung. Die SharePoint-CAL-Lizenzierung betrifft daher SharePoint 2013.  
  
-   Die Anwendungsrolle (2) umfasst SQL Server Reporting Services im SharePoint-Modus.  
  
     Die SharePoint-Dienstanwendungsdatenbanken werden auf Datenbankrollenservern (4) ausgeführt.  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint wird auf drei (3) separaten Servern ausgeführt. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint 2013 wird außerhalb der SharePoint-Farm ausgeführt und können auf Servern, die keine Verbesserung der Leistung eine SharePoint-Installation enthalten installiert werden.  
  
-   Die Datenbankrolle (4) verwendet SQL Server Enterprise. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktion AlwaysOn-Verfügbarkeitsgruppen ist somit verfügbar.  
  
 ![bi_license_3tiers_and_ASseparate](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseparate.gif "bi_license_3tiers_and_ASseparate")  
  
 Bei 100 Benutzern ist die SQL Server BI-Edition kostengünstiger.  
  
 ![bi_license_3tiers_and_ASseperate_calcs](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseperate-calcs.gif "bi_license_3tiers_and_ASseperate_calcs")  
  
 Bei 300 Benutzern ist die SQL Server Enterprise Edition jedoch günstiger.  
  
 ![bi_license_3tiers_and_ASseperate_calcs2](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseperate-calcs2.gif "bi_license_3tiers_and_ASseperate_calcs2")  
  
##  <a name="bkmk_3tier"></a> Topologie mit 3 Ebenen  
 Dieses Beispiel veranschaulicht, dass es bei 100 oder weniger Benutzern kostengünstiger ist, SQL BI-Edition für Server mit SQL Server-BI-Funktionen zu verwenden. Ab 500 Benutzern ist jedoch die SQL Server Enterprise Edition günstiger.  
  
-   Dieses Beispiel umfasst eine Intranetbereitstellung. Die SharePoint-CAL-Lizenzierung betrifft daher SharePoint 2013.  
  
-   Analysis Services im PowerPivot-Modus (2) wird außerhalb der Farm ausgeführt; PowerPivot wird jedoch **auf demselben physischen** Server in der anderen Anwendungsrolle ausgeführt.  
  
-   Die Datenbankrolle (3) verwendet SQL Server Enterprise, damit die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Funktion AlwaysOn-Verfügbarkeitsgruppen ist verfügbar.  
  
 ![bi_license_3tiers](../../../2014/sql-server/install/media/bi-license-3tiers.gif "bi_license_3tiers")  
  
 Bei 100 Benutzern ist die SQL Server BI-Edition kostengünstiger.  
  
 ![bi_license_3tiers_calcs1](../../../2014/sql-server/install/media/bi-license-3tiers-calcs1.gif "bi_license_3tiers_calcs1")  
  
 Bei 500 Benutzern sind die SQL Server Enterprise Edition jedoch günstiger.  
  
 ![bi_license_3tiers_calcs3](../../../2014/sql-server/install/media/bi-license-3tiers-calcs3.gif "bi_license_3tiers_calcs3")  
  
##  <a name="bkmk_2tier"></a> Topologie mit 2 Ebenen  
 Bei nur 2 Ebenen wird SQL Server Enterprise Edition verwendet, sodass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktion AlwaysOn-Verfügbarkeitsgruppen für die SQL Server-Datenbank-Engine verfügbar ist. Ein Vergleich der Kosten zwischen den SQL Server-Editionen ist daher nicht sinnvoll. Die einzige Variable ist die SharePoint-CAL-Preiskalkulation basierend auf der Anzahl der Benutzer.  
  
-   Dieses Beispiel umfasst eine Intranetbereitstellung. Die SharePoint-CAL-Lizenzierung betrifft daher SharePoint 2013.  
  
-   Analysis Services im PowerPivot-Modus wird außerhalb der Farm ausgeführt, aber PowerPivot wird auf den gleichen physischen Servern (2) wie die SQL-Server-Datenbank-Engine ausgeführt.  
  
 ![bi_license_2tiers](../../../2014/sql-server/install/media/bi-license-2tiers.gif "bi_license_2tiers")  
  
 ![bi_license_2tiers_calcs1](../../../2014/sql-server/install/media/bi-license-2tiers-calcs1.gif "bi_license_2tiers_calcs1")  
  
##  <a name="bkmk_reference"></a> Referenz-und Communityinhalte  
  
### <a name="license-tools"></a>Lizenz-Tools  
  
-   [Microsoft License Advisor](http://mla.microsoft.com/default.aspx) (http://mla.microsoft.com/default.aspx).  
  
-   [ClientAccess-Lizenz (CAL) Entscheidungs-Tool](http://www.microsoft.com/licensing/CalTool/) (http://www.microsoft.com/licensing/CalTool/).  
  
-   [Microsoft Business-Hub: Informationen zum Kauf](http://www.microsoftbusinesshub.com/How_To_Buy#) (http://www.microsoftbusinesshub.com/How_To_Buy#).  
  
### <a name="microsoft-license-information"></a>Microsoft-Lizenzinformationen  
  
-   [Informationen zu Lizenzierung: Clientzugriffslizenzen und Management-Lizenzen](http://www.microsoft.com/licensing/about-licensing/client-access-license.aspx) (http://www.microsoft.com/licensing/about-licensing/client-access-license.aspx).  
  
-   [Informationen zu Lizenzierung: Produktlizenzierungsdetails Suche](http://www.microsoftvolumelicensing.com/default.aspx) (http://www.microsoftvolumelicensing.com/default.aspx).  
  
-   [Volumenlizenzierung: Preise und Bezugsquellen](http://www.microsoft.com/licensing/how-to-buy/how-to-buy.aspx) (http://www.microsoft.com/licensing/how-to-buy/how-to-buy.aspx).  
  
### <a name="community-content"></a>Community-Inhalt  
  
-   [SQL Server 2014 Developer Edition Licensing](http://sqlmag.com/sql-server-2014/sql-server-2014-developer-edition-licensing).  
  
-   [SQL Server 2014-Lizenzierung Änderungen](http://www.brentozar.com/archive/2014/04/sql-server-2014-licensing-changes)(http://www.brentozar.com/archive/2014/04/sql-server-2014-licensing-changes).  
  
-   [Änderungen für SQLServer 2014-Lizenzierung](https://www.directionsonmicrosoft.com/sites/default/files/PDFs/Licensing_Changes_for_SQL_Server_2014.pdf)(https://www.directionsonmicrosoft.com/sites/default/files/PDFs/Licensing_Changes_for_SQL_Server_2014.pdf).  
  
-   [Schätzen der SharePoint 2013-Lizenzierungskosten](http://www.degdigital.com/blog/sharepoint-2013-licensing-for-dummies/) (http://www.degdigital.com/blog/sharepoint-2013-licensing-for-dummies/).  
  
-   [Microsoft Volume Licensing Kunden](http://www.microsoft.com/licensing/existing-customers/community.aspx) (http://www.microsoft.com/licensing/existing-customers/community.aspx).  
  
  
