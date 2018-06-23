---
title: Voraussetzungen für Tutorials (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5326d5e91521e90f7596e3dd0647cb273078fd82
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161738"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>Voraussetzungen für Lernprogramme (Berichts-Generator)
  Die Lernprogramme zum Berichts-Generator setzen voraus, dass Sie Berichte auf einem Berichtsserver oder einer in einen Berichtsserver integrierten SharePoint-Website anzeigen und speichern können. Für Daten werden in allen Lernprogrammen wörtliche Abfragen verwendet, die von einer [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Instanz verarbeitet werden müssen.  
  
 Wenn Sie keinen Zugriff auf einen Berichtsserver, eine Website oder eine Datenquelle haben, können Sie sich mit Berichts-Generator vertraut machen, indem Sie einen Offlinebericht erstellen. Siehe [Tutorial: Create a Quick Chart Report Offline (Report Builder) (Tutorial: Erstellen eines Quick-Diagrammberichts offline (Berichts-Generator))](report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  
  
## <a name="requirements"></a>Anforderungen  
 Für die Ausführung der Lernprogramme zum Berichts-Generator gelten die folgenden Voraussetzungen:  
  
-   Sie müssen Zugriff auf [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Berichts-Generator haben. Sie können den Berichts-Generator in der eigenständigen Version oder der im Berichts-Manager oder auf einer SharePoint-Website verfügbaren ClickOnce-Version ausführen. Bei der ClickOnce-Version ist lediglich der erste Schritt anders, also das Öffnen des Berichts-Generators.  
  
     Um Berichts-Manager zu verwenden, öffnen Sie den Berichts-Manager, und klicken Sie auf **Berichts-Generator**. Standardmäßig lautet die URL für den Berichts-Manager http://\<*Servername*> / reports.  
  
     Wenn Sie eine SharePoint-Website verwenden möchten, navigieren Sie zu der Website, klicken Sie auf der Registerkarte "Dokumente" auf "Neues Dokument", und klicken Sie dann in der Dropdownliste auf "Berichts-Generator-Bericht". Z. B. http://\<Servername >/Sites/MySite/Reports. Der SharePoint-Administrator muss die Funktion "Berichts-Generator-Bericht" für jede Dokumentbibliothek aktivieren.  
  
-   Die URL zu einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] integriert Berichtsserver oder einer SharePoint-Website, eine [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Berichtsserver. Sie benötigen Berechtigungen zum Speichern und Anzeigen von Berichten, freigegebenen Datenquellen, freigegebenen Datasets, Berichtsteilen und Modellen. Standardmäßig lautet die URL für einen Berichtsserver http://\<Servername > / Reportserver. Standardmäßig lautet die URL für eine SharePoint-Website http://\<Sitename > oder http://\<Server > / site.  
  
-   Der Name des eine [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Instanz und Anmeldeinformationen für den schreibgeschützten Zugriff auf eine beliebige Datenbank. In den Datasetabfragen im Lernprogramm werden zwar Literaldaten verwendet, die Abfrage muss jedoch von einer [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] -Instanz verarbeitet werden, um die für ein Berichtsdataset erforderlichen Metadaten zurückzugeben. Die folgende Verbindungszeichenfolge gibt z. B. nur einen Server an: `data source=<servername>`. Sie müssen Lesezugriff auf die Standarddatenbank besitzen, die Ihnen vom Systemadministrator zugewiesen wird, der Ihnen die Berechtigung für den Zugriff auf den Server gewährt. Sie können auch eine Datenbank entsprechend der folgenden Verbindungszeichenfolge angeben: `data source=<servername>;initial catalog=<database>`.  
  
-   Für das Lernprogramm, in dem eine Karte verwendet wird, muss der Berichtsserver zur Unterstützung von Bing Maps als Hintergrund konfiguriert werden. Weitere Informationen finden Sie unter [Planen der Unterstützung für Kartenberichte](plan-for-map-report-support.md) in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dokumentation in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](http://go.microsoft.com/fwlink/?LinkId=154888) auf "MSDN.Microsoft.com".  
  
-   Das Lernprogramm [Lernprogramm: Erstellen von Drillthrough- und Main Berichte &#40;Berichts-Generator&#41;](tutorial-creating-drillthrough-and-main-reports-report-builder.md), verwendet das Contoso Business Intelligence-Demodataset. Dieses Dataset besteht aus dem Data Warehouse ContosoDW und der OLAP (Online Analytical Processing)-Datenbank Contoso_Retail. Die Berichte, die Sie in diesem Lernprogramm erstellen, rufen Berichtsdaten aus dem Contoso Sales-Cube ab. Die OLAP-Datenbank Contoso_Retail kann vom [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=191575)heruntergeladen werden. Sie brauchen lediglich die Datei ContosoBIdemoABF.exe herunterzuladen. Diese Datei enthält die OLAP-Datenbank.  
  
     Die andere Datei, ContosoBIdemoBAK.exe, ist für das Data Warehouse ContosoDW bestimmt, das in diesem Lernprogramm nicht verwendet wird.  
  
     Die Website enthält Anweisungen zum Extrahieren und Wiederherstellen der Sicherungsdatei ContosoRetail.abf in der OLAP-Datenbank Contoso_Retail.  
  
     Sie benötigen Zugriff auf eine Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], auf der die OLAP-Datenbank installiert werden soll.  
  
 Der Berichtsserver-Administrator muss Ihnen die erforderlichen Berechtigungen auf dem Berichtsserver erteilen [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Ordnerpfade, und konfigurieren Sie die Standardoptionen für Berichts-Generator. Weitere Informationen finden Sie unter [Installation, Deinstallation und Unterstützung von Berichts-Generator](install-uninstall-and-report-builder-support.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)  
  
  