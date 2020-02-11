---
title: Implementieren der iabonptionbaseuiusercontrol-Schnittstelle für eine Übermittlungs Erweiterung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- user controls [Reporting Services]
- ISubscriptionBaseUIUserControl interface
- delivery extensions [Reporting Services], user controls
ms.assetid: a1e9122c-aa0b-45de-b536-4f1202875ab1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2664d71243d98e9b8152c5c5c7ce241a4f3669f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63164354"
---
# <a name="implementing-the-isubscriptionbaseuiusercontrol-interface-for-a-delivery-extension"></a>Implementieren der ISubscriptionBaseUIUserControl-Schnittstelle für eine Übermittlungserweiterung
  
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterungen können eine Implementierung der Abonnement-Benutzeroberfläche für die Sammlung erweiterungsspezifischer Informationen im Berichts-Manager enthalten. Die Benutzeroberfläche wird aufgerufen, wenn ein Benutzer ein neues Abonnement erstellt oder ein vorhandenes ändert. Wenn ein neues Abonnement erstellt wird, zeigt die Benutzeroberfläche passende Standardwerte an und ermöglicht dem Benutzer die Interaktion mit dem Übermittlungsanbieter. Wenn ein Abonnement geändert wird, werden in der Benutzeroberfläche die Informationen des aktuellen Abonnements vorgegeben.  
  
 Die Übermittlungserweiterungen bieten die Abonnement-Benutzeroberfläche als ASP.NET-Benutzersteuerelement an. Wenn die Abonnement-Benutzeroberfläche angezeigt wird, integriert der Berichtsserver das von der Übermittlungserweiterung definierte Benutzersteuerelement. Die Basisschnittstelle, die abstrakte Methoden bereitstellt, die diese Funktionen aktivieren, ist die <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>-Schnittstelle. Diese Schnittstelle stellt sicher, dass allgemeine Vorgänge, z. B. die Überprüfung von Eingabewerten, ordnungsgemäß ausgeführt werden. Außerdem gibt das Basisbenutzer-Steuerelement eine Reihe von Eigenschaften vor, mit denen der Berichtsserver für Konsistenz unter den verschiedenen Abonnenments sorgt. Diese Eigenschaften werden von den Übermittlungserweiterungen benötigt, die in den Berichts-Manager integriert werden.  
  
 Sie können die <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>-Schnittstelle in einen Übermittlungsanbieter integrieren, um eine Abonnement-Benutzeroberfläche für den Berichts-Manager zu erstellen. Die <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>-Schnittstelle bietet eine Infrastruktur, über die Benutzer Werte für die Abonnementeinstellungen eingeben können, mit der die für die Übermittlungserweiterung benötigten Einstellungen verarbeitet und die Einstellungen validiert werden können.  
  
> [!NOTE]  
>  Es ist nicht erforderlich, die <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>-Schnittstelle als Teil der Übermittlungserweiterung zu implementieren. Abonnements mit Übermittlungserweiterungen können stattdessen auch immer über die SOAP-API-Methoden <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> und <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A> erstellt werden. Weitere Informationen zu den SOAP-API-Funktionen für die Abonnement- und Übermittlungsverwaltung finden Sie unter [Abonnement- und Übermittlungsverwaltung](../../report-server-web-service/methods/subscription-and-delivery-methods.md).  
  
 Die <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>-Schnittstelle erweitert <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Das Benutzersteuerelement, das <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> implementiert, muss auch von **System.Web.UI.WebControls.WebControl** erben. Weitere Informationen über die **WebControl**-Klasse finden Sie im [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Entwicklerhandbuch.  
  
 Ein Beispiel zur Verwendungsweise der <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>-Klasse finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Übermittlungserweiterungen](implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
