---
title: Im Onlinemodus mit einer Analysis Services-Datenbank verbinden | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 612e538ef01040778497242606115a01c6ef6921
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68179006"
---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a>Herstellen in Onlinemodus einer Verbindung mit einer Analysis Services-Datenbank
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Sie können eine direkte Verbindung mit einer vorhandenen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank herstellen und die Objekte in dieser Datenbank direkt ändern. Wenn Sie eine direkte Verbindung mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank herstellen, werden Änderungen an Objekten unmittelbar wirksam, und es wird kein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt innerhalb von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt.  
  
### <a name="to-connect-directly-to-an-analysis-services-database-by-using-sql-server-data-tools"></a>So stellen Sie eine direkte Verbindung zu einer Analysis Services-Datenbank mit SQL Server-Datentools her  
  
1.  Öffnen Sie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Öffnen** , und klicken Sie dann auf **Analysis Services-Datenbank**.  
  
3.  Wählen Sie **Verbindung mit vorhandener Datenbank herstellen**aus.  
  
4.  Geben Sie den Server- und den Datenbanknamen an.  
  
     Sie können den Datenbanknamen entweder eingeben oder den Server abfragen, um die vorhandenen Datenbanken auf dem Server anzuzeigen.  
  
5.  Klicken Sie auf **OK**.  
  
     Sie können nun alle Objekte innerhalb der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank direkt bearbeiten.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Analysis Services-Projekten und -Datenbanken während der Entwicklungsphase](../../analysis-services/multidimensional-models/work-with-analysis-services-projects-and-databases-in-development.md)   
 [Erstellen mehrdimensionaler Modelle mit SQL Server-Datentools &#40;SSDT&#41;](../../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  
