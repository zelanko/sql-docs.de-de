---
title: Was&#39;Neues in Analysis Services und Business Intelligence | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a6b59ae2bd1c9d21704d87289b604feefa326f1e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054340"
---
# <a name="what39s-new-in-analysis-services-and-business-intelligence"></a>Was&#39;Neues in Analysis Services und Business Intelligence
  Mit Ausnahme von zusätzlichen Funktionen zur Unterstützung von Power View-Berichte für mehrdimensionale Modelle [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wurde gegenüber der vorherigen Version.  
  
 Weitere Informationen zu anderen [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Produkte und Technologien, die in dieser Version unterschiedlich sind, finden Sie unter [Neuigkeiten in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
## <a name="updates-to-design-tool-installation"></a>Aktualisierte Installation von Entwurfstools  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] für Business Intelligence (SSDT-BI), das zuvor als Business Intelligence Development Studio (BIDS) bezeichnet wurde, wird zum Erstellen von Analysis Services-Modellen, Reporting Services-Berichten und Integration Services-Paketen verwendet. Sie können SSDT-BI von folgenden Orten herunterladen:  
  
-   [Herunterladen von SSDT-BI für Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=396526)  
  
-   [Herunterladen von SSDT-BI für Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkID=273673)  
  
 Wenn auf Ihrem Computer eine frühere Version von SSDT-BI oder BIDS installiert ist, wird die neuere Version parallel zur vorherigen Version installiert. Es ist üblich, neuere und ältere Versionen der Entwurfstools auf derselben Arbeitsstation auszuführen, damit Projekte und Projektmappen geändert werden können, die an bestimmte Serverversionen gebunden sind.  
  
> [!NOTE]  
>  Für die Visual Studio 2012- und Visual Studio 2013-Version von SSDT können mehrere Downloadwebsites genutzt werden. Die meisten enthalten keine BI-Projektvorlagen. Über die oben angezeigten Links finden Sie die richtige Version. Die richtige SSDT-BI-Version ist daran zu erkennen, dass der Ordner für Business Intelligence-Projektvorlagen angezeigt wird. Dieser Ordner enthält die Projektvorlagen für Analysis Services, Reporting Services und Integration Services. Abhängig davon, wie SSDT-BI installiert wurde, wird u. U. auch eine zusätzliche Projektvorlage für SQL Server-Datenbanken angezeigt.  
  
 ![Neue Projektvorlagen in SSDT](media/ssdt-biprojects.png "New Project templates in SSDT")  
  
## <a name="features-recently-added-power-view-for-multidimensional-models"></a>Kürzlich hinzugefügte Funktionen: Power View für mehrdimensionale Modelle  
 Die Möglichkeit zum Erstellen von Power View-Berichten für mehrdimensionale Modelle wurde erstmalig im kumulativen Update 4 für [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1 eingeführt. Die Funktionen von Power View für mehrdimensionale Modelle sind jetzt Bestandteil von [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
 **Power View-Bericht für ein mehrdimensionales Modell**  
  
 ![Power View-Bericht](media/powerviewreport-wn.gif "Power View-Bericht")  
  
 Diese Funktionen unterstützten Organisationen bei der Maximierung bereits getätigter BI-Investitionen, da mehrdimensionale Modelle (auch als OLAP-Cubes bezeichnet) in Verbindung mit den neuesten Clientberichterstellungstools eingesetzt werden können. Auf Grundlage der im mehrdimensionalen Modell enthaltenen Daten können Benutzer auf einfache Weise zahlreiche dynamische Visualisierungen erstellen, von Tabellen und Matrizen bis hin zu Blasendiagrammen und geografischen Karten. Mehrdimensionale Modelle unterstützen jetzt auch Abfragen unter Verwendung von DAX (Data Analysis Expressions).  
  
 Power View für mehrdimensionale Modelle erfordert die integrierte Berichterstellungsfunktion Power View in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (im SharePoint-Modus). Andere Versionen von Power View, insbesondere das Power View-Add-In in Excel 2013, unterstützen keine mehrdimensionalen Modelle.  
  
 Weitere Informationen finden Sie unter [Power View für mehrdimensionale Modelle](http://msdn.microsoft.com/library/dn140246.aspx).  
  
  
