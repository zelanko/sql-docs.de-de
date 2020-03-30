---
title: Implementieren von Übermittlungserweiterungen | Microsoft-Dokumentation
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4c0004f844d6914cea330d3a0c7332de783116c7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "63193756"
---
# <a name="implementing-a-delivery-extension"></a>Implementieren von Übermittlungserweiterungen
  Mithilfe von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] können Benutzer Berichte erstellen und veröffentlichen, die anschließend an diverse Orte übermittelt werden. Außerdem enthält [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] verschiedene Übermittlungserweiterungen und eine Übermittlungs-API, mit der Entwickler zusätzliche Übermittlungserweiterungen erstellen können, um die Übermittlungsfunktionen in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] noch zu erweitern.  
  
 Eine Beispielimplementierung einer Übermittlungserweiterung finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Delivery Extensions Overview (Übersicht über Übermittlungserweiterungen)](../../../reporting-services/extensions/delivery-extension/delivery-extensions-overview.md)  
 Erläutert, wie eine benutzerdefinierte Übermittlungserweiterung für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] geschrieben wird.  
  
 [Preparing to Implement a Delivery Extension (Vorbereiten der Implementierung von Übermittlungserweiterungen)](../../../reporting-services/extensions/delivery-extension/preparing-to-implement-a-delivery-extension.md)  
 Beschreibt die verfügbaren Schnittstellen und Klassen beim Implementieren einer [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung sowie die Themen, die vor der Implementierung berücksichtigt werden sollten.  
  
 [Creating a Delivery Extension Library (Erstellen einer Bibliothek für Übermittlungserweiterungen)](../../../reporting-services/extensions/delivery-extension/creating-a-delivery-extension-library.md)  
 Beschreibt die Zuordnung eines Namespace für die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung und die Kompilierung der Übermittlungserweiterung in eine DLL-Bibliothek.  
  
 [Implementing the IDeliveryExtension Interface for a Delivery Extension (Implementieren der IDeliveryExtension-Schnittstelle für Übermittlungserweiterungen)](../../../reporting-services/extensions/delivery-extension/implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 Beschreibt die Attribute einer Übermittlungserweiterung und die Art der Implementierung einer eigenen Klasse für die Übermittlungserweiterung.  
  
 [Using a Notification Class for a Delivery Extension (Verwenden einer Notification-Klasse für eine Übermittlungserweiterung)](../../../reporting-services/extensions/delivery-extension/using-a-notification-class-for-a-delivery-extension.md)  
 Beschreibt die Attribute der **Notification**-Klasse und die Verwendungsweise in Ihrer Implementierung der Übermittlungserweiterung  
  
 [Using the Setting Class for a Delivery Extension (Verwenden der Setting-Klasse für eine Übermittlungserweiterung)](../../../reporting-services/extensions/delivery-extension/using-the-setting-class-for-a-delivery-extension.md)  
 Beschreibt die Attribute der **Setting**-Klasse und die Verwendungsweise in Ihrer Implementierung der Übermittlungserweiterung  
  
 [Using the Report Class for a Delivery Extension (Verwenden der Report-Klasse für eine Übermittlungserweiterung)](../../../reporting-services/extensions/delivery-extension/using-the-report-class-for-a-delivery-extension.md)  
 Beschreibt die Attribute der **Report**-Klasse und die Verwendungsweise in Ihrer Implementierung der Übermittlungserweiterung  
  
 [Using the RenderedOutputFile Class for a Delivery Extension (Verwenden der RenderedOutputFile-Klasse für eine Übermittlungserweiterung)](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 Beschreibt die Attribute der **RenderedOutputFile**-Klasse und die Verwendungsweise in Ihrer Implementierung der Übermittlungserweiterung  
  
 [Bereitstellen von Übermittlungserweiterungen](../../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md)  
 Beschreibt, wie Sie eine Übermittlungserweiterung anwenden  
  
 [Debugging Delivery Extension Code (Debuggen von Übermittlungserweiterungscode)](../../../reporting-services/extensions/delivery-extension/debugging-delivery-extension-code.md)  
 Beschreibt, wie Sie Code in der Übermittlungserweiterung debuggen  
  
 [Removing a Delivery Extension (Entfernen von Übermittlungserweiterungen)](../../../reporting-services/extensions/delivery-extension/removing-a-delivery-extension.md)  
 Beschreibt, wie Sie eine Übermittlungserweiterung von einem Berichtsserver entfernen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungen für Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
