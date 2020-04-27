---
title: Power Pivot-Datenzugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 83dc82da-91fb-4e47-91a8-0e0db67339b8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97f5d2045601f72c3536fbf2d4e469eb5eb20fbe
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66071253"
---
# <a name="powerpivot-data-access"></a>PowerPivot-Datenzugriff
  In diesem Thema werden die Methoden beschrieben, mit denen Daten aus einer PowerPivot-Arbeitsmappe abgerufen werden, die in einer SharePoint-Bibliothek veröffentlicht ist.  
  
 PowerPivot-Daten werden in einer Excel-Arbeitsmappe gespeichert. Die Verbindungszeichenfolge ist eine URL zu einer Arbeitsmappe auf einer SharePoint-Website.  
  
 PowerPivot-Daten werden am häufigsten von der Arbeitsmappe verwendet, die sie enthält, wie z. B. Daten hinter PivotTables und PivotCharts. Alternativ können PowerPivot-Daten auch als externe Datenquelle verwendet werden, wenn eine Arbeitsmappe, ein Dashboard oder ein Bericht eine Verbindung mit einer getrennten Excel-Datei (XLSX-Datei) in SharePoint herstellen und die Daten für die anschließende Nutzung abrufen. Clienttools, die PowerPivot-Daten in der Regel verwenden, sind Excel, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], andere Reporting Services-Berichte und PerformancePoint.  
  
 Auf dem Desktop verwendet das PowerPivot-Add-In AMO und ADOMD.NET, um die PowerPivot-Daten im Clientarbeitsbereich zu erstellen, zu verarbeiten und abzufragen.  
  
 Auf einer SharePoint-Farm verwendet Excel Services den lokalen MSOLAP-OLE DB-Anbieter, um eine Verbindung mit PowerPivot-Daten herzustellen. Der Anbieter sendet die Verbindungsanforderung an einen PowerPivot für SharePoint-Server in der Farm. Dieser Server lädt die Daten, führt die Abfrage aus, und gibt das Resultset zurück.  
  
##  <a name="querying-powerpivot-data-in-sharepoint"></a><a name="queryproc"></a>Abfragen von Power Pivot-Daten in SharePoint  
 Wenn Sie eine PowerPivot-Arbeitsmappe aus einer SharePoint-Bibliothek anzeigen, werden die PowerPivot-Daten in der Arbeitsmappe erkannt, extrahiert und getrennt auf Analysis Services-Serverinstanzen innerhalb der Farm verarbeitet, während die Darstellungsschicht von Excel Services gerendert wird. Sie können die vollständig verarbeitete Arbeitsmappe in einem Browserfenster oder in einer Excel 2010-Desktopanwendung anzeigen, die über das PowerPivot-Add-In verfügt.  
  
 Das folgende Diagramm veranschaulicht, wie eine Anforderung für die Abfrageverarbeitung in der Farm weiterverarbeitet wird. Da PowerPivot-Daten Bestandteil einer Excel 2010-Arbeitsmappe sind, wird eine Anforderung für die Abfrageverarbeitung ausgegeben, wenn ein Benutzer eine Excel-Arbeitsmappe aus einer SharePoint-Bibliothek öffnet und mit einer PivotTable oder einem PivotChart interagiert, die bzw. das PowerPivot-Daten enthält.  
  
 ![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")  
  
 Excel Services und PowerPivot für SharePoint-Komponenten verarbeiten unterschiedliche Bereiche der gleichen Arbeitsmappendatei (.xlsx). Excel Services erkennen PowerPivot-Daten und fordern die Verarbeitung durch einen PowerPivot-Server in der Farm an. Der PowerPivot-Server ordnet die Anforderung einer [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]-Instanz zu, die die Daten aus der Arbeitsmappe in der Inhaltsbibliothek extrahiert und lädt. Im Arbeitsspeicher gespeicherte Daten werden wieder mit der gerenderten Arbeitsmappe zusammengeführt und zur Darstellung in einem Browserfenster zurück an Excel Web Access übergeben.  
  
 Nicht alle Daten in einer PowerPivot-Arbeitsmappe werden durch PowerPivot für SharePoint verarbeitet. Tabellen und Zellendaten in einem Arbeitsblatt werden durch Excel Services verarbeitet. Nur PivotTables, PivotCharts und Slicer, die auf PowerPivot-Daten basieren, werden durch den PowerPivot für SharePoint-Dienst verarbeitet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbindung mit Analysis Services herstellen](../instances/connect-to-analysis-services.md)   
 [Zugriff auf Daten im tabellarischen Modell](../tabular-models/tabular-model-data-access.md)  
  
  
