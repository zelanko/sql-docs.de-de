---
title: Neues in Analysis Services und Business Intelligence |&#39;Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/07/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9d66589dd4094614d195757a8dcc7c59175c9540
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938131"
---
# <a name="what39s-new-in-sql-server-2014-analysis-services"></a>Neues&#39;in SQL Server 2014 Analysis Services
  Mit Ausnahme der hinzugefügten Funktionen, die Power View Berichte für mehrdimensionale Modelle unterstützen, [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ist gegenüber der vorherigen Version unverändert.

 Informationen zu anderen [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Produkten und Technologien, die in dieser Version unterschiedlich sind, finden Sie unter [What es New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).

## <a name="updates-to-design-tool-installation"></a>Aktualisierte Installation von Entwurfstools
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] für Business Intelligence (SSDT-BI), das zuvor als Business Intelligence Development Studio (BIDS) bezeichnet wurde, wird zum Erstellen von Analysis Services-Modellen, Reporting Services-Berichten und Integration Services-Paketen verwendet. Sie können SSDT-BI von folgenden Orten herunterladen:

-   [Herunterladen von SSDT-BI für Visual Studio 2013](https://go.microsoft.com/fwlink/p/?LinkId=396526)

-   [Herunterladen von SSDT-BI für Visual Studio 2012](https://go.microsoft.com/fwlink/p/?LinkID=273673)

 Wenn auf Ihrem Computer eine frühere Version von SSDT-BI oder BIDS installiert ist, wird die neuere Version parallel zur vorherigen Version installiert. Es ist üblich, neuere und ältere Versionen der Entwurfstools auf derselben Arbeitsstation auszuführen, damit Projekte und Projektmappen geändert werden können, die an bestimmte Serverversionen gebunden sind.

> [!NOTE]
>  Für die Visual Studio 2012- und Visual Studio 2013-Version von SSDT können mehrere Downloadwebsites genutzt werden. Die meisten enthalten keine BI-Projektvorlagen. Über die oben angezeigten Links finden Sie die richtige Version. Sie wissen, dass Sie über die richtige Version von SSDT-BI verfügen, wenn Sie den Business Intelligence-Projektvorlagen Ordner sehen. Dieser Ordner enthält die Projektvorlagen für Analysis Services, Reporting Services und Integration Services. Abhängig davon, wie SSDT-BI installiert wurde, wird u. U. auch eine zusätzliche Projektvorlage für SQL Server-Datenbanken angezeigt.

 ![Neue Projektvorlagen in SSDT](media/ssdt-biprojects.png "Neue Projektvorlagen in SSDT")

## <a name="features-recently-added-power-view-for-multidimensional-models"></a>Kürzlich hinzugefügte Funktionen: Power View für mehrdimensionale Modelle
 Die Möglichkeit zum Erstellen von Power View-Berichten für mehrdimensionale Modelle wurde erstmalig im kumulativen Update 4 für [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1 eingeführt. Die Funktionen von Power View für mehrdimensionale Modelle sind jetzt Bestandteil von [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].

 **Power View-Bericht für ein mehrdimensionales Modell**

 ![Power View-Bericht](media/powerviewreport-wn.gif "Power View-Bericht")

 Diese Funktionen unterstützten Organisationen bei der Maximierung bereits getätigter BI-Investitionen, da mehrdimensionale Modelle (auch als OLAP-Cubes bezeichnet) in Verbindung mit den neuesten Clientberichterstellungstools eingesetzt werden können. Auf Grundlage der im mehrdimensionalen Modell enthaltenen Daten können Benutzer auf einfache Weise zahlreiche dynamische Visualisierungen erstellen, von Tabellen und Matrizen bis hin zu Blasendiagrammen und geografischen Karten. Mehrdimensionale Modelle unterstützen jetzt auch Abfragen unter Verwendung von DAX (Data Analysis Expressions).

 Power View für mehrdimensionale Modelle erfordert die integrierte Berichterstellungsfunktion von Power View in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (im SharePoint-Modus). Andere Versionen von Power View, insbesondere das Power View-Add-In in Excel 2013, unterstützen keine mehrdimensionalen Modelle.

 Weitere Informationen finden Sie unter [Power View für mehrdimensionale Modelle](https://msdn.microsoft.com/library/dn140246.aspx).


