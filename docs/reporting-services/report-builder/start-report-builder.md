---
title: Starten des Berichts-Generators | Microsoft-Dokumentation
description: Der Berichts-Generator ist eine eigenständige Berichterstellungsumgebung. Beim ersten Start werden Sie vom Microsoft Download Center zum Download aufgefordert.
ms.date: 01/03/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bdb67ef174ec849233826b65a2d90f08e8e4eb7d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "80290761"
---
# <a name="start-report-builder"></a>Starten des Berichts-Generators

[!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] ist eine eigenständige Berichterstellungsumgebung. Sie können darin paginierte Berichte erstellen und in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen oder integrierten SharePoint-Modus veröffentlichen.  

> [!NOTE]
> Die Integration von Reporting Services in SharePoint ist nach SQL Server 2016 nicht mehr möglich.
  
 Beim ersten Starten von [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Webportal oder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im integrierten SharePoint-Modus werden Sie aufgefordert, den Download im Microsoft Download Center durchzuführen. 
 
![report-builder-get-report-builder](../../reporting-services/report-builder/media/report-builder-get-report-builder.png) 
 
 Sie oder ein Administrator können auch [Berichts-Generator aus dem Microsoft Download Center auf Ihrem Computer installieren](https://go.microsoft.com/fwlink/?LinkID=219138). Einzelheiten finden Sie unter „Installieren des Berichts-Generators mit Systems Manager Server“ in [Installieren des Berichts-Generators](../../reporting-services/install-windows/install-report-builder.md) .
 
 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] wird nicht installiert, wenn Sie SQL Server Reporting Services installieren. Sie müssen den Download und die Installation separat durchführen.  
  
 Wenn beim Starten von [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] aus dem Webportal oder von der SharePoint-Website aus eine frühere Version von [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] geöffnet wird, wenden Sie sich an Ihren Administrator. Dieser kann die Version auf dem Webportal oder der SharePoint-Website aktualisieren.  
  
## <a name="to-start-ssrbnoversion-from-the-ssrsnoversion-web-portal"></a>So starten Sie [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] aus dem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Webportal  
  
1.  Geben Sie in der Adressleiste des Webbrowsers die URL für den Berichtsserver ein. Standardmäßig lautet die URL https://\<*Servername*>/Berichte.  
  
2.  Wählen Sie in der oberen Leiste des Webportals **Neu** > **Paginierter Bericht**aus.  
  
     ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png "PBI_SSMRP_NewMenu")  
  
     Bei der ersten Ausführung werden Sie aufgefordert, [Berichts-Generator zu installieren](../../reporting-services/install-windows/install-report-builder.md). 
  
     Bei nachfolgenden Ausführungen wird [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] geöffnet, und Sie können einen paginierten Bericht erstellen oder einen Bericht auf dem Berichtsserver öffnen.  
  
## <a name="to-start-ssrbnoversion-in-sharepoint-integrated-mode"></a>So starten Sie [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] im integrierten SharePoint-Modus  
  
1.  Navigieren Sie zu der SharePoint-Website mit der gewünschten Bibliothek.  
  
2.  Öffnen Sie die Bibliothek.  
  
3.  Klicken Sie auf **Dokumente**.  
  
4.  Klicken Sie im Menü **Neues Dokument** auf **Berichts-Generator-Bericht**.  
  
     Dadurch wird beim ersten Mal der SQL Server-Assistent für den [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] gestartet. Einzelheiten finden Sie unter [Installieren des Berichts-Generators](../../reporting-services/install-windows/install-report-builder.md) .  
  
     [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] wird geöffnet, und Sie können einen paginierten Bericht erstellen oder einen Bericht auf dem Berichtsserver öffnen.  
  
     **Hinweis:** Wenn das Menü **Neues Dokument** die Optionen **Berichts-Generator-Bericht**, **Berichts-Generator-Modell**oder **Berichtsdatenquelle**nicht enthält, müssen die entsprechenden Inhaltstypen der SharePoint-Bibliothek hinzugefügt werden. Weitere Informationen finden Sie unter [Hinzufügen von Reporting Services-Inhaltstypen zu einer SharePoint-Bibliothek](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).  

## <a name="next-steps"></a>Nächste Schritte

[Berichts-Generator in SQL Server](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
[Set default options for Report Builder (Festlegen von Standardoptionen für den Berichts-Generator)](../../reporting-services/report-builder/set-default-options-for-report-builder.md)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
