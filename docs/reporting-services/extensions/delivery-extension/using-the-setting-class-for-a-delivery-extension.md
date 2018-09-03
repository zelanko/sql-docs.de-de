---
title: Verwenden der Setting-Klasse für eine Übermittlungserweiterung | Microsoft-Dokumentation
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
author: markingmyname
ms.author: maghan
ms.openlocfilehash: edf1bfaa3c1e58169d07f97c956baaef3c631f1f
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43273557"
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a>Verwenden der Setting-Klasse für eine Übermittlungserweiterung
  Die <xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse befindet sich im <xref:Microsoft.ReportingServices.Interfaces>-Namespace und stellt Informationen zu Erweiterungseinstellungen für eine Übermittlungserweiterung dar. Die <xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse liefert eine Infrastruktur zum Speichern von Informationen über Einstellungen, die für ein ordnungsgemäßes Funktionieren einer Übermittlungserweiterung nötig sind. Beispiel: In einer E-Mail-Übermittlung eines Berichtsserver muss der Benutzer Einstellungen angeben, die spezifisch für die E-Mail-Übermittlung sind, z. B. die Empfängeradresse, die Absenderadresse, die Betreffzeile der E-Mail usw. Zweifellos wird von den benutzerdefinierten Übermittlungsanbietern gefordert, dass ein Benutzer spezifische Einstellungen angibt, damit die Übermittlungserweiterung Benachrichtigungen und Berichte problemlos übermitteln kann.  
  
 Die <xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse wird verwendet, wenn die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A>-Eigenschaft der <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>-Schnittstelle implementiert wird. Die <xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse wird auch für die Verarbeitung der Erweiterungseinstellungsdaten verwendet, die vom Benutzer angegeben werden, wenn ein Abonnement oder eine Benachrichtigung erstellt wird.  
  
 Ein Beispiel zur Verwendungsweise der <xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse finden Sie unter [SQL Server Reporting Services-Produktbeispiele](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Implementieren von Übermittlungserweiterungen](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
