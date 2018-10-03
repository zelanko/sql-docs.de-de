---
title: Verwenden der Report-Klasse für eine Übermittlungserweiterung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 693c0c18b4ffb2f3ab5209c0133588997c11d539
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48159570"
---
# <a name="using-the-report-class-for-a-delivery-extension"></a>Verwenden der Report-Klasse für eine Übermittlungserweiterung
  Die <xref:Microsoft.ReportingServices.Interfaces.Report>-Klasse stellt einen Bericht in der Berichtsserver-Datenbank dar. Jedes Abonnement wird einem bestimmten Bericht zugeordnet. Der Bericht ist in der Benachrichtigung enthalten. Die Übermittlungserweiterung kann das <xref:Microsoft.ReportingServices.Interfaces.Report>-Objekt verwenden, das Bestandteil der Benachrichtigung zum Rendern des Berichts ist. Das <xref:Microsoft.ReportingServices.Interfaces.Report>-Objekt enthält auch berichtsspezifische Eigenschaften, wie die URL zum Bericht auf dem Server und den Namen des Berichts. Diese Eigenschaften können alle als Teil des Übermittlungsanbieters verwendet werden.  
  
 Die <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A>-Methode der <xref:Microsoft.ReportingServices.Interfaces.Report>-Klasse kann zum Rendern eines Berichts verwendet werden. Die <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A>-Methode gibt ein Array von einem oder mehreren <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekten zurück, die zusammen einen gerenderten Bericht ausmachen. Das erste <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekt ist der gerenderte Bericht. Alle anderen <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekte sind Ressourcen, die zusammen mit den Berichtsdaten geliefert werden müssen (z. B. eine HTML-Datei und zugehörige Bilder). Renderingerweiterungen mit einem einzigen Datenstrom (IMAGE, PDF, MHTML und Excel) geben nur ein <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekt im Array zurück.  
  
 Das <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekt, das den Berichtsdatenstrom enthält, kann als Teil einer Übermittlung enthalten sein.  
  
 Ein Beispiel zur Verwendungsweise der <xref:Microsoft.ReportingServices.Interfaces.Report>-Klasse finden Sie unter [SQL Server Reporting Services-Produktbeispiele](http://go.microsoft.com/fwlink/?LinkId=177889)  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Übermittlungserweiterungen](implementing-a-delivery-extension.md)   
 [Reporting Services-Erweiterungsbibliothek](../reporting-services-extension-library.md)   
 [Using the RenderedOutputFile Class for a Delivery Extension (Verwenden der RenderedOutputFile-Klasse für eine Übermittlungserweiterung)](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
