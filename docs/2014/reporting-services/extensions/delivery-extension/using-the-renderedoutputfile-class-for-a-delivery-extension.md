---
title: Verwenden der RenderedOutputFile-Klasse für eine Übermittlungserweiterung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1dcbf250a367326e5cad528384e533a9ac9d945b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63180621"
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a>Verwenden der RenderedOutputFile-Klasse für eine Übermittlungserweiterung
  Die <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Klasse stellt einen Datenstrom und Informationen zu den zugehörigen Eigenschaften des Datenstroms dar. Die **Daten**-Eigenschaft der <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Klasse wird verwendet, um einen gerenderten Bericht oder eine Berichtsressource als **Stream**-Objekt darzustellen.  
  
 Die <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A>-Methode des **Bericht**-Objekts gibt ein Array von einem oder mehreren <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekten zurück, die zusammen einen einzelnen gerenderten Bericht ausmachen. Das erste <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekt ist der gerenderte Bericht. Alle anderen <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekte sind Ressourcen, die zusammen mit den Berichtsdaten geliefert werden müssen (z. B. eine HTML-Datei und zugehörige Bilder). Renderingerweiterungen mit einem einzigen Datenstrom (IMAGE, PDF, MHTML und EXCEL) geben nur ein <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Objekt im Array zurück.  
  
 Ein Beispiel zur Verwendungsweise der <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>-Klasse finden Sie unter [SQL Server Reporting Services-Produktbeispiele](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Übermittlungserweiterungen](implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
