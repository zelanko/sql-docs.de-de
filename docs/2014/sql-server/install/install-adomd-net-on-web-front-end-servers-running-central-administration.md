---
title: Installieren von ADOMD.net auf Web-Front-End-Servern, die die zentral Administration ausführen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b77948b3ae5b27d7ecb82c277424057fe39ff7a0
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68891038"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a>Installieren von ADOMD.NET auf Web-Front-End-Servern, auf denen die Zentraladministration ausgeführt wird
  Wenn Sie PowerPivot für SharePoint in einer Farm installieren, die die Topologie "Zentraladministration ohne Excel Services oder PowerPivot für SharePoint" aufweist, laden Sie die Microsoft ADOMD.NET-Clientbibliothek herunter und installieren diese, wenn Sie Vollzugriff auf die integrierten Berichte im PowerPivot-Management-Dashboard erhalten möchten. Einige Berichte im Dashboard verwenden ADOMD.NET für den Zugriff auf interne Daten, die Berichtsdaten zur PowerPivot-Abfrageverarbeitung und zum Serverzustand in der Farm liefern.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010  
  
 Bei SharePoint 2013 ist der Anbieter im SQL Server Feature Pack enthalten. Weitere Informationen zum Herunterladen von sppowerpivot. msi finden Sie unter [Microsoft SQL Server 2014 Feature Pack](https://www.microsoft.com/download/details.aspx?id=35577)  
  
### <a name="download-and-install-the-client-library"></a>Herunterladen und Installieren der Clientbibliothek  
  
1.  Suchen Sie auf der [Seite "SQL Server 2014 Feature Pack](https://go.microsoft.com/fwlink/?LinkID=296473)" nach Microsoft ADOMD.net.  
  
2.  Laden Sie das x64-Paket des `SQL_AS_ADOMD.msi`-Installationsprogramms herunter.  
  
3.  Führen Sie die MSI-Datei aus, um die Bibliothek zu installieren.  
  
4.  Setzen Sie IIS zurück, nachdem die Installation beendet wurde. Öffnen Sie eine Administrator Eingabeaufforderung, und geben Sie **iisreset**ein.  
  
### <a name="verify-installation"></a>Überprüfen der Installation  
  
1.  Wechseln Sie zu Windows\Assembly.  
  
2.  Klicken Sie mit der rechten Maustaste auf Microsoft. AnalysisServices. AdomdClient, und wählen Sie **Eigenschaften**aus.  
  
3.  Klicken Sie auf **Version**.  
  
4.  Vergewissern Sie sich, dass die Version 12,00 enthält. \<Buildnummer > und die Beschreibung lautet Microsoft. analysisservice. AdomdClient.  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Management-Dashboard und -Verwendungsdaten](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data)  
  
  
