---
title: Tools und Anwendungen, die in Analysis Services verwendete | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cb258b1d1cc9466d1b1c88255e6edbbb854b5aef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059684"
---
# <a name="tools-and-applications-used-in-analysis-services"></a>In Analysis Services verwendete Tools und Anwendungen
  Suchen Sie nach den Tools und Anwendungen, die Sie benötigen, um Analysis Services-Modelle zu erstellen und zugeordnete Datenbanken in einer Analysis Services-Instanz zu verwalten.  
  
## <a name="analysis-services-model-designers"></a>Analysis Services-Modell-Designer  
 Tabellarische und mehrdimensionale Modelle werden aus Projektvorlagen in einer in der Visual Studio-Shell erstellen Lösung erstellt. Die Projektvorlage stellt die Entwürfe für das Erstellen von Modellen, Cubes, Dimensionen und Rollen bereit, aus denen Analysis Services-Lösung zusammengestellt ist.  
  
### <a name="download-sql-server-data-tools-for-business-intelligence-ssdt-bi"></a>Herunterladen der SQL Server Data Tools für Business Intelligence (SSDT-BI)  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] für Business Intelligence (SSDT-BI), das zuvor als Business Intelligence Development Studio (BIDS) bezeichnet wurde, wird zum Erstellen von Analysis Services-Modellen, Reporting Services-Berichten und Integration Services-Paketen verwendet. Sie können SSDT-BI von folgenden Orten herunterladen:  
  
-   [Herunterladen von SSDT-BI für Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=396526)  
  
-   [Herunterladen von SSDT-BI für Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkID=273673)  
  
 Wenn auf Ihrem Computer eine frühere Version von SSDT-BI oder BIDS installiert ist, wird die neuere Version parallel zur vorherigen Version installiert. Es ist üblich, neuere und ältere Versionen der Entwurfstools auf derselben Arbeitsstation auszuführen, damit Projekte und Projektmappen geändert werden können, die an bestimmte Serverversionen gebunden sind.  
  
> [!NOTE]  
>  Für die Visual Studio 2012- und Visual Studio 2013-Version von SSDT können mehrere Downloadwebsites genutzt werden. Die meisten enthalten keine BI-Projektvorlagen. Über die oben angezeigten Links finden Sie die richtige Version. Die richtige SSDT-BI-Version ist daran zu erkennen, dass der Ordner für Business Intelligence-Projektvorlagen angezeigt wird. Dieser Ordner enthält die Projektvorlagen für Analysis Services, Reporting Services und Integration Services. Abhängig davon, wie SSDT-BI installiert wurde, wird u. U. auch eine zusätzliche Projektvorlage für SQL Server-Datenbanken angezeigt.  
  
 ![Neue Projektvorlagen in SSDT](media/ssdt-biprojects.png "New Project templates in SSDT")  
  
## <a name="administrative-tools"></a>Verwaltungstools  
  
### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 Management Studio ist das primäre Verwaltungstool für alle SQL Server-Funktionen, einschließlich Analysis Services. SQL Server Management Studio ist eine optionale Komponente. Falls diese nicht mit anderen SQL Server-Anwendungen auf der Apps-Seite in Windows Server 2012 angezeigt wird, führen Sie SQL Server-Setup auf, um sie zu Ihrer Installation hinzuzufügen.  
  
### <a name="sql-server-profiler"></a>SQL Server Profiler  
 Auch wenn er offiziell als veraltet eingestuft ist, bietet SQL Server Profiler eine einfache Methode zum Überwachen von Verbindungen, der MDX-Abfrageausführung und anderer Servervorgänge. SQL Server Profiler wird standardmäßig installiert. Sie finden ihn mit SQL Server-Anwendungen bei den Apps in Windows Server 2012.  
  
### <a name="powershell"></a>PowerShell  
 Mithilfe von PowerShell-Befehlen können Sie viele Verwaltungsaufgaben durchführen. Finden Sie unter [Analysis Services PowerShell](analysis-services-powershell.md) für Weitere Informationen.  
  
### <a name="community-and-third-party-tools"></a>Community- und Drittanbietertools  
 Community-Codebeispiele finden Sie auf der [Analysis Services-Codeplex-Seite](http://sqlsrvanalysissrvcs.codeplex.com/) . [Foren](http://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) können hilfreich sein, wenn Sie Empfehlungen für Drittanbietertools suchen, die Analysis Services unterstützen.  
  
  