---
title: Arbeiten mit Analysis Services-Projekten und-Datenbanken während der Entwicklungs Phase | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762ea6f33a94f65e7dd6895cd038d4a52d40d43e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84535562"
---
# <a name="working-with-analysis-services-projects-and-databases-during-the-development-phase"></a>Arbeiten mit Analysis Services-Projekten und -Datenbanken während der Entwicklungsphase
  Sie können eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank entwickeln, indem Sie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] entweder im Projektmodus oder im Onlinemodus verwenden.  
  
## <a name="single-developer"></a>Einzelner Entwickler  
 Wenn nur ein einzelner Entwickler die gesamte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank und alle Objekte entwickelt, aus denen sie besteht, kann [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] während des Entwicklungszyklus der Business Intelligence-Lösung jederzeit entweder im Projektmodus oder im Onlinemodus verwendet werden. Bei einem einzelnen Entwickler ist die Wahl des Modus nicht von besonderer Bedeutung. Die Wartung einer Offlineprojektdatei unter Einbeziehung eines Quellcodeverwaltungssystems weist viele Vorteile auf, z. B. Archivierung und Rollback. Ein einzelner Entwickler muss sich jedoch nicht damit befassen, Änderungen mit anderen Entwicklern abzustimmen.  
  
## <a name="multiple-developers"></a>Mehrere Entwickler  
 Wenn mehrere Entwickler an einer Business Intelligence-Lösung arbeiten, wird es zu Problemen kommen, falls die Entwickler nicht vorwiegend, oder sogar immer, im Projektmodus mit Quellcodeverwaltung arbeiten. Durch die Quellcodeverwaltung wird sichergestellt, dass zwei Entwickler nicht gleichzeitig Änderungen an demselben Objekt vornehmen.  
  
 Nehmen Sie z. B. an, ein Entwickler arbeitet im Projektmodus und nimmt Änderungen an ausgewählten Objekten vor. Nehmen Sie weiterhin an, dass, während der Entwickler diese Änderungen vornimmt, ein anderer Entwickler im Onlinemodus eine Änderung an der bereitgestellten Datenbank vornimmt. Ein Problem tritt auf, wenn der erste Entwickler versucht, das geänderte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt bereitzustellen. In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] wird nämlich erkannt, dass Objekte innerhalb der bereitgestellten Datenbank geändert wurden, und der Entwickler wird aufgefordert, die gesamte Datenbank zu überschreiben, wodurch auch die Änderungen des zweiten Entwicklers überschrieben werden. Da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nicht in der Lage ist, die Änderungen zwischen der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankinstanz und den Objekten im Projekt, das überschrieben werden soll, aufzulösen, hat der erste Entwickler genau genommen nur die Möglichkeit, alle eigenen Änderungen zu verwerfen und die Änderungen erneut an einem neuen Projekt vorzunehmen, das auf der aktuellen Version der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank basiert.  
  
  
