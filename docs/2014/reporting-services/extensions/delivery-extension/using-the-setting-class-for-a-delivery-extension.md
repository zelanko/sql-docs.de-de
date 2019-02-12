---
title: Verwenden der Setting-Klasse für eine Übermittlungserweiterung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: e8e2e218eb702f2606293596206e43373a6b6a8f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56030711"
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a>Verwenden der Setting-Klasse für eine Übermittlungserweiterung
  Die <xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse befindet sich im <xref:Microsoft.ReportingServices.Interfaces>-Namespace und stellt Informationen zu Erweiterungseinstellungen für eine Übermittlungserweiterung dar. Die <xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse liefert eine Infrastruktur zum Speichern von Informationen über Einstellungen, die für ein ordnungsgemäßes Funktionieren einer Übermittlungserweiterung nötig sind. Beispiel: In einer E-Mail-Übermittlung eines Berichtsserver muss der Benutzer Einstellungen angeben, die spezifisch für die E-Mail-Übermittlung sind, z. B. die Empfängeradresse, die Absenderadresse, die Betreffzeile der E-Mail usw. Zweifellos wird von den benutzerdefinierten Übermittlungsanbietern gefordert, dass ein Benutzer spezifische Einstellungen angibt, damit die Übermittlungserweiterung Benachrichtigungen und Berichte problemlos übermitteln kann.  
  
 Die <xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse wird verwendet, wenn die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A>-Eigenschaft der <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>-Schnittstelle implementiert wird. Die <xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse wird auch für die Verarbeitung der Erweiterungseinstellungsdaten verwendet, die vom Benutzer angegeben werden, wenn ein Abonnement oder eine Benachrichtigung erstellt wird.  
  
 Ein Beispiel zur Verwendungsweise der <xref:Microsoft.ReportingServices.Interfaces.Setting>-Klasse finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Übermittlungserweiterungen](implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
