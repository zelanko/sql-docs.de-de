---
title: Vorbereiten der Implementierung von Übermittlungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
caps.latest.revision: 33
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a6a93d48d1962800b4fba7598019561a83dcc5b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37307390"
---
# <a name="preparing-to-implement-a-delivery-extension"></a>Vorbereiten der Implementierung von Übermittlungserweiterungen
  Bevor Sie die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung implementieren, sollten Sie definieren, welche Schnittstellen implementiert werden sollen. Sie müssen zuerst überlegen, wie die Übermittlungserweiterung verwendet werden soll, welche Einstellungen benötigt werden und welche speziellen Funktionen Sie implementieren müssen, um die Berichtsbenachrichtigungen zu übermitteln.  
  
 Jede [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung muss die folgenden Funktionen enthalten:  
  
-   Eine <xref:Microsoft.ReportingServices.Interfaces.IExtension>-Schnittstellenimplementierung, die die Erweiterung und einen lokalisierten Erweiterungsnamen darstellt.  
  
-   Eine <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>-Implementierung, die eine Übermittlungserweiterung erstellt, mit der die Berichtsbenachrichtigungen an die Endbenutzer übermittelt werden können.  
  
-   Die Fähigkeit, bestimmte Benutzerdaten für ein Abonnement zu verarbeiten.  
  
 Jede Übermittlungserweiterung kann auf folgende Funktionen erweitert werden:  
  
-   Eine [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]-Implementierung von Benutzersteuerelementen, anhand der Endbenutzer mithilfe des Berichts-Managers Berichtsabonnements erstellen, die diese Übermittlungserweiterung verwenden.  
  
 In der folgenden Tabelle werden die verfügbaren Schnittstellen und Klassen für Übermittlungserweiterungen beschrieben.  
  
|Schnittstelle oder Klasse|Description|  
|------------------------|-----------------|  
|<xref:Microsoft.ReportingServices.Interfaces.IExtension> -Schnittstelle|Stellt eine Erweiterung in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dar.|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> -Schnittstelle|Stellt eine Übermittlungserweiterung in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dar.|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> -Schnittstelle|Enthält auch Informationen zum Berichtsserver, die von den Übermittlungserweiterungen benötigt werden (z. B. eine Liste der verfügbaren Renderingerweiterungen).|  
|<xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse|Stellt eine Einstellung für eine Erweiterung dar.|  
|<xref:Microsoft.ReportingServices.Interfaces.Notification>-Klasse|Enthält Abonnementinformationen, mithilfe der die Übermittlungserweiterungen Berichte übermitteln.|  
|<xref:Microsoft.ReportingServices.Interfaces.Report>-Klasse|Stellt berichtsspezifische Informationen und Methoden dar, anhand derer die Übermittlungserweiterungen Berichte an die Benutzer übermitteln können.|  
|<xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Klasse|Stellt die Ausgabe von einer Renderingerweiterung dar. Ein <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekt enthält die dazugehörigen Informationen zu Dateiname und Dateityp, die von der Übermittlungserweiterung benötigt werden, um den von der Renderingerweiterung zurückgegebenen Datenstrom zu verarbeiten.|  
|<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> -Schnittstelle|Ein Benutzersteuerelement, mit dem Abonnementinformationen, die für die Übermittlungserweiterung spezifisch sind, vom Benutzer im Berichts-Manager abgerufen werden können (z. B. eine E-Mail-Adresse oder der Pfad zu einer Dateifreigabe).|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungen für Reporting Services](../reporting-services-extensions.md)   
 [Implementieren von Übermittlungserweiterungen](implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
