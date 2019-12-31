---
title: In Analysis Services verwendete Tools und Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c04742d0e0a84dd35e300bace9107685685ef75b
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228899"
---
# <a name="tools-and-applications-used-in-analysis-services"></a>In Analysis Services verwendete Tools und Anwendungen
  Suchen Sie nach den Tools und Anwendungen, die Sie benötigen, um Analysis Services-Modelle zu erstellen und zugeordnete Datenbanken in einer Analysis Services-Instanz zu verwalten.  
  
## <a name="analysis-services-model-designers"></a>Analysis Services-Modell-Designer  
 Tabellarische und mehrdimensionale Modelle werden aus Projektvorlagen in einer in der Visual Studio-Shell erstellen Lösung erstellt. Die Projektvorlage stellt die Entwürfe für das Erstellen von Modellen, Cubes, Dimensionen und Rollen bereit, aus denen Analysis Services-Lösung zusammengestellt ist.  
  
### <a name="download-sql-server-data-tools-for-business-intelligence-ssdt-bi"></a>Herunterladen der SQL Server Data Tools für Business Intelligence (SSDT-BI)  
 
  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] für Business Intelligence (SSDT-BI), das zuvor als Business Intelligence Development Studio (BIDS) bezeichnet wurde, wird zum Erstellen von Analysis Services-Modellen, Reporting Services-Berichten und Integration Services-Paketen verwendet. Sie können SSDT-BI von folgenden Orten herunterladen:  
  
-   [Herunterladen von SSDT-BI für Visual Studio 2013](https://go.microsoft.com/fwlink/p/?LinkId=396526)  
  
-   [Herunterladen von SSDT-BI für Visual Studio 2012](https://go.microsoft.com/fwlink/p/?LinkID=273673)  
  
 Wenn auf Ihrem Computer eine frühere Version von SSDT-BI oder BIDS installiert ist, wird die neuere Version parallel zur vorherigen Version installiert. Es ist üblich, neuere und ältere Versionen der Entwurfstools auf derselben Arbeitsstation auszuführen, damit Projekte und Projektmappen geändert werden können, die an bestimmte Serverversionen gebunden sind.  
  
> [!NOTE]  
>  Für die Visual Studio 2012- und Visual Studio 2013-Version von SSDT können mehrere Downloadwebsites genutzt werden. Die meisten enthalten keine BI-Projektvorlagen. Über die oben angezeigten Links finden Sie die richtige Version. Sie wissen, dass Sie über die richtige Version von SSDT-BI verfügen, wenn Sie den Business Intelligence-Projektvorlagen Ordner sehen. Dieser Ordner enthält die Projektvorlagen für Analysis Services, Reporting Services und Integration Services. Abhängig davon, wie SSDT-BI installiert wurde, wird u. U. auch eine zusätzliche Projektvorlage für SQL Server-Datenbanken angezeigt.  
  
 ![Neue Projektvorlagen in SSDT](media/ssdt-biprojects.png "Neue Projektvorlagen in SSDT")  
  
## <a name="administrative-tools"></a>Verwaltungstools  
  
### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 Management Studio ist das primäre Verwaltungstool für alle SQL Server-Funktionen, einschließlich Analysis Services. SQL Server Management Studio ist eine optionale Komponente. Falls diese nicht mit anderen SQL Server-Anwendungen auf der Apps-Seite in Windows Server 2012 angezeigt wird, führen Sie SQL Server-Setup auf, um sie zu Ihrer Installation hinzuzufügen.  
  
### <a name="sql-server-profiler"></a>SQL Server Profiler  
 Auch wenn er offiziell als veraltet eingestuft ist, bietet SQL Server Profiler eine einfache Methode zum Überwachen von Verbindungen, der MDX-Abfrageausführung und anderer Servervorgänge. SQL Server Profiler wird standardmäßig installiert. Sie finden ihn mit SQL Server-Anwendungen bei den Apps in Windows Server 2012.  
  
### <a name="powershell"></a>PowerShell  
 Mithilfe von PowerShell-Befehlen können Sie viele Verwaltungsaufgaben durchführen. Weitere Informationen finden Sie unter [Analysis Services PowerShell](analysis-services-powershell.md) .  
  
### <a name="community-and-third-party-tools"></a>Community- und Drittanbietertools  
 Community-Codebeispiele finden Sie auf der [Analysis Services-Codeplex-Seite](https://sqlsrvanalysissrvcs.codeplex.com/) . [Foren](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) können hilfreich sein, wenn Sie Empfehlungen für Drittanbieter Tools suchen, die Analysis Services unterstützen.  
