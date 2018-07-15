---
title: Installieren Sie ADOMD.NET auf Web Front-End-Servern, die mit der zentralen Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5fd8c345a0f5b1cafdf675fa5ed57b857d9714b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317540"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a>Installieren von ADOMD.NET auf Web-Front-End-Servern, auf denen die Zentraladministration ausgeführt wird
  Wenn Sie PowerPivot für SharePoint in einer Farm installieren, die die Topologie "Zentraladministration ohne Excel Services oder PowerPivot für SharePoint" aufweist, laden Sie die Microsoft ADOMD.NET-Clientbibliothek herunter und installieren diese, wenn Sie Vollzugriff auf die integrierten Berichte im PowerPivot-Management-Dashboard erhalten möchten. Einige Berichte im Dashboard verwenden ADOMD.NET für den Zugriff auf interne Daten, die Berichtsdaten zur PowerPivot-Abfrageverarbeitung und zum Serverzustand in der Farm liefern.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010  
  
 Bei SharePoint 2013 ist der Anbieter im SQL Server Feature Pack enthalten. Informationen zum Herunterladen von spPowerPivot.msi finden Sie unter [Microsoft SQL Server 2014 Feature Pack](http://www.microsoft.com/download/details.aspx?id=35577)  
  
### <a name="download-and-install-the-client-library"></a>Herunterladen und Installieren der Clientbibliothek  
  
1.  Auf der [Downloadseite für SQL Server 2014 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=296473), suchen Sie Microsoft ADOMD.NET.  
  
2.  Laden Sie das x64-Paket des `SQL_AS_ADOMD.msi`-Installationsprogramms herunter.  
  
3.  Führen Sie die MSI-Datei aus, um die Bibliothek zu installieren.  
  
4.  Setzen Sie IIS zurück, nachdem die Installation beendet wurde. Öffnen Sie eine administratoreingabeaufforderung, und geben **"iisreset"**.  
  
### <a name="verify-installation"></a>Überprüfen der Installation  
  
1.  Wechseln Sie zu Windows\Assembly.  
  
2.  Maustaste auf Microsoft.AnalysisServices.AdomdClient, und wählen Sie **Eigenschaften**.  
  
3.  Klicken Sie auf **Version**.  
  
4.  Stellen Sie sicher, dass die Version 12.00 enthält. \<Buildnummer > und die Beschreibung Microsoft.AnalysisService.AdomdClient lautet.  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Management-Dashboard und -Verwendungsdaten](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)  
  
  
