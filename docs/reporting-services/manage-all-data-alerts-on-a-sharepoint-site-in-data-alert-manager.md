---
title: Verwalten aller Datenwarnungen auf einer SharePoint-Website im Datenwarnungs-Manager | Microsoft-Dokumentation
ms.date: 08/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 9c70b0f4-2db8-4c2e-acbf-96e2a55ddc48
author: maggiesMSFT
ms.author: maggies
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 9702ca84fab0da2024db6f6f5e0f510822dcd29e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "65579809"
---
# <a name="manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager"></a>Verwalten aller Datenwarnungen auf einer SharePoint-Website im Datenwarnungs-Manager

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

SharePoint-Warnungsadministratoren können eine Liste der von allen Benutzern der Website erstellten Datenwarnungen und Informationen zu den Warnungen anzeigen. Warnungsadministratoren können auch Warnungen löschen. Das folgende Bild zeigt Warnungsadministratoren die verfügbaren Funktionen im Datenwarnungs-Manager.

 ![Warnungs-Manager für SharePoint-Websiteadministratoren](../reporting-services/media/rs-alertmanagersite.gif "Warnungs-Manager für SharePoint-Websiteadministratoren")

> [!NOTE]
> Die Integration von Reporting Services in SharePoint ist nach SQL Server 2016 nicht mehr möglich.

## <a name="view-a-list-of-alerts-created-by-a-site-user"></a>Anzeigen einer Liste der von einem Websitebenutzer erstellten Warnungen  
  
1.  Wechseln Sie zur SharePoint-Website, auf der Datenwarnungsdefinitionen gespeichert sind.  
  
2.  Klicken Sie auf der Startseite auf **Websiteaktionen**.  
  
3.  Führen Sie einen Bildlauf zum Ende der Liste durch, und klicken Sie auf **Siteeinstellungen**.  
  
4.  Klicken Sie unter **Reporting Services**auf **Datenwarnungen verwalten**.  
  
5.  Klicken Sie neben der Liste **Warnungen anzeigen für folgenden Benutzer** auf den Pfeil nach unten, und wählen Sie den Benutzer aus, dessen Warnungen Sie anzeigen möchten.  
  
6.  Klicken Sie neben der Liste **Warnungen anzeigen für folgenden Bericht** auf den Pfeil nach unten, und wählen Sie eine bestimmte anzuzeigende Warnung aus, oder klicken Sie auf **Alle anzeigen** , um alle vom ausgewählten Benutzer erstellten Warnungen anzuzeigen.  
  
     Eine Tabelle umfasst den Namen, Berichtsnamen, Namen der Person, die die Datenwarnung erstellt hat, die Häufigkeit der Übermittlungen einer Datenwarnung, die letzte Änderung der Datenwarnungsdefinition und den Status der Datenwarnung. Wenn die Datenwarnung nicht generiert oder gesendet werden kann, enthält die Statusspalte Informationen zum Fehler und hilft Ihnen bei der Behebung des Problems.  
  
## <a name="delete-an-alert-definition"></a>Löschen einer Warnungsdefinition  
  
-   Klicken Sie mit der rechten Maustaste auf die zu löschende Datenwarnung, und klicken Sie auf **Löschen**.  
  
    > [!NOTE]  
    >  Nach dem Löschen der Warnung werden keine weiteren Warnmeldungen gesendet. Wenn Sie jedoch die Warnungsdatenbank abfragen, stellen Sie möglicherweise fest, dass die Warnungsdefinition immer noch vorhanden ist. Der Warndienst führt den Cleanup nach einem Zeitplan durch. Die Warnungsdefinition wird beim nächsten Cleanup dauerhaft gelöscht. Das Standardintervall für den Cleanup beträgt 20 Minuten. Dieses und andere Cleanupintervalle sind konfigurierbar. Weitere Informationen finden Sie unter [Reporting Services-Datenwarnungen](../reporting-services/reporting-services-data-alerts.md).  

## <a name="see-also"></a>Weitere Informationen

[Datenwarnungs-Manager für Warnungsadministratoren](../reporting-services/data-alert-manager-for-alerting-administrators.md)   
[Reporting Services-Datenwarnungen](../reporting-services/reporting-services-data-alerts.md)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
