---
title: Verwenden von Meine Abonnements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddd8eba477d0426fc0bf8eaeac9dcd2c1ec60b78
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66100620"
---
# <a name="use-my-subscriptions"></a>Verwenden von "Meine Abonnements"
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Berichts-Manager enthält eine **Meine Abonnements** Seite, die alle Ihre Abonnements zentral aufgelistet werden. Mithilfe von Meine Abonnements können Sie vorhandene Abonnements anzeigen, ändern und löschen. Abonnements können damit jedoch nicht erstellt werden.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] im einheitlichen Modus|  
  
 In Meine Abonnements können Sie Abonnements nach Ordner, Bericht, Beschreibung, Trigger, letzter Ausführung oder Status sortieren. Alle Werte sind alphabetisch sortiert, außer bei Zuletzt ausgeführt, wo die Werte chronologisch sortiert sind.  
  
 Meine Abonnements zeigt nur die von Ihnen erstellten Abonnements. Abonnements anderer Benutzer werden nicht angezeigt, selbst wenn Sie als Abonnent zu diesen Abonnements hinzugefügt werden, und es werden auch keine datengesteuerten Abonnements angezeigt.  
  
 Sie können nicht basierend auf Besitzernamen, Triggerinformationen, Statusinformationen usw. nach Abonnements suchen. Weitere Informationen finden Sie unter [erstellen, ändern und Löschen von Standardabonnements &#40;Reporting Services im einheitlichen Modus&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).  
  
## <a name="how-to-use-my-subscriptions"></a>Verwenden von Meine Abonnements  
 Die Option Meine Abonnements ist im Berichts-Manager verfügbar. Für den Zugriff auf **Meine Abonnements** klicken Sie auf die globale Symbolleiste des Berichts-Managers.  
  
## <a name="use-windows-powershell-to-list-mysubscriptions"></a>Verwenden von Windows PowerShell zum Auflisten von MySubscriptions  
 ![PowerShell-Inhalt](../media/rs-powershellicon.jpg "PowerShell related content")  
  
 Mit dem folgenden PowerShell-Skript wird die Liste der Abonnements und Abonnementeigenschaften für den aktuellen Benutzer zurückgegeben. Weitere Informationen finden Sie unter [ReportingService2010.ListMySubscriptions-Methode](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).  
  
```  
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datengesteuerte Abonnements](data-driven-subscriptions.md)   
 [Abonnements und Übermittlung &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Create and Manage Subscriptions for Native Mode Report Servers (Erstellen und Verwalten von Abonnements für Berichtsserver im einheitlichen Modus)](../create-manage-subscriptions-native-mode-report-servers.md)  
  
  
