---
title: PowerPivot-Datenzugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 83dc82da-91fb-4e47-91a8-0e0db67339b8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 75da2776f867ae89da049ba31a9180d21922cd84
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62749361"
---
# <a name="powerpivot-data-access"></a>PowerPivot-Datenzugriff
  In diesem Thema werden die Methoden beschrieben, mit denen Daten aus einer PowerPivot-Arbeitsmappe abgerufen werden, die in einer SharePoint-Bibliothek veröffentlicht ist.  
  
 PowerPivot-Daten werden in einer Excel-Arbeitsmappe gespeichert. Die Verbindungszeichenfolge ist eine URL zu einer Arbeitsmappe auf einer SharePoint-Website.  
  
 PowerPivot-Daten werden am häufigsten von der Arbeitsmappe verwendet, die sie enthält, wie z. B. Daten hinter PivotTables und PivotCharts. Alternativ können PowerPivot-Daten auch als externe Datenquelle verwendet werden, wenn eine Arbeitsmappe, ein Dashboard oder ein Bericht eine Verbindung mit einer getrennten Excel-Datei (XLSX-Datei) in SharePoint herstellen und die Daten für die anschließende Nutzung abrufen. Clienttools, die PowerPivot-Daten in der Regel verwenden, sind Excel, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], andere Reporting Services-Berichte und PerformancePoint.  
  
 Auf dem Desktop verwendet das PowerPivot-Add-In AMO und ADOMD.NET, um die PowerPivot-Daten im Clientarbeitsbereich zu erstellen, zu verarbeiten und abzufragen.  
  
 Auf einer SharePoint-Farm verwendet Excel Services den lokalen MSOLAP-OLE DB-Anbieter, um eine Verbindung mit PowerPivot-Daten herzustellen. Der Anbieter sendet die Verbindungsanforderung an einen PowerPivot für SharePoint-Server in der Farm. Dieser Server lädt die Daten, führt die Abfrage aus, und gibt das Resultset zurück.  
  
##  <a name="queryproc"></a> Abfragen von PowerPivot-Daten in SharePoint  
 Wenn Sie eine PowerPivot-Arbeitsmappe aus einer SharePoint-Bibliothek anzeigen, werden die PowerPivot-Daten in der Arbeitsmappe erkannt, extrahiert und getrennt auf Analysis Services-Serverinstanzen innerhalb der Farm verarbeitet, während die Darstellungsschicht von Excel Services gerendert wird. Sie können die vollständig verarbeitete Arbeitsmappe in einem Browserfenster oder in einer Excel 2010-Desktopanwendung anzeigen, die über das PowerPivot-Add-In verfügt.  
  
 Das folgende Diagramm veranschaulicht, wie eine Anforderung für die Abfrageverarbeitung in der Farm weiterverarbeitet wird. Da PowerPivot-Daten Bestandteil einer Excel 2010-Arbeitsmappe sind, wird eine Anforderung für die Abfrageverarbeitung ausgegeben, wenn ein Benutzer eine Excel-Arbeitsmappe aus einer SharePoint-Bibliothek öffnet und mit einer PivotTable oder einem PivotChart interagiert, die bzw. das PowerPivot-Daten enthält.  
  
 ![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")  
  
 Excel Services und PowerPivot für SharePoint-Komponenten verarbeiten unterschiedliche Bereiche der gleichen Arbeitsmappendatei (.xlsx). Excel Services erkennen PowerPivot-Daten und fordern die Verarbeitung durch einen PowerPivot-Server in der Farm an. Der PowerPivot-Server ordnet die Anforderung einer [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]-Instanz zu, die die Daten aus der Arbeitsmappe in der Inhaltsbibliothek extrahiert und lädt. Im Arbeitsspeicher gespeicherte Daten werden wieder mit der gerenderten Arbeitsmappe zusammengeführt und zur Darstellung in einem Browserfenster zurück an Excel Web Access übergeben.  
  
 Nicht alle Daten in einer PowerPivot-Arbeitsmappe werden durch PowerPivot für SharePoint verarbeitet. Tabellen und Zellendaten in einem Arbeitsblatt werden durch Excel Services verarbeitet. Nur PivotTables, PivotCharts und Slicer, die auf PowerPivot-Daten basieren, werden durch den PowerPivot für SharePoint-Dienst verarbeitet.  
  
## <a name="see-also"></a>Siehe auch  
 [Verbindung mit Analysis Services herstellen](../instances/connect-to-analysis-services.md)   
 [Zugriff auf Daten im tabellarischen Modell](../tabular-models/tabular-model-data-access.md)  
  
  
