---
title: Arbeiten mit Analysis Services-Projekten und Datenbanken in Entwicklung | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6525cf60457470dd496a515aa3cbd6ef03450ce8
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="work-with-analysis-services-projects-and-databases-in-development"></a>Arbeiten mit Analysis Services-Projekten und Datenbanken in der Entwicklung
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Sie können eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank entwickeln, indem Sie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] entweder im Projektmodus oder im Onlinemodus verwenden.  
  
## <a name="single-developer"></a>Einzelner Entwickler  
 Wenn nur ein einzelner Entwickler die gesamte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank und alle Objekte entwickelt, aus denen sie besteht, kann [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] während des Entwicklungszyklus der Business Intelligence-Lösung jederzeit entweder im Projektmodus oder im Onlinemodus verwendet werden. Bei einem einzelnen Entwickler ist die Wahl des Modus nicht von besonderer Bedeutung. Die Wartung einer Offlineprojektdatei unter Einbeziehung eines Quellcodeverwaltungssystems weist viele Vorteile auf, z. B. Archivierung und Rollback. Ein einzelner Entwickler muss sich jedoch nicht damit befassen, Änderungen mit anderen Entwicklern abzustimmen.  
  
## <a name="multiple-developers"></a>Mehrere Entwickler  
 Wenn mehrere Entwickler an einer Business Intelligence-Lösung arbeiten, wird es zu Problemen kommen, falls die Entwickler nicht vorwiegend, oder sogar immer, im Projektmodus mit Quellcodeverwaltung arbeiten. Durch die Quellcodeverwaltung wird sichergestellt, dass zwei Entwickler nicht gleichzeitig Änderungen an demselben Objekt vornehmen.  
  
 Nehmen Sie z. B. an, ein Entwickler arbeitet im Projektmodus und nimmt Änderungen an ausgewählten Objekten vor. Nehmen Sie weiterhin an, dass, während der Entwickler diese Änderungen vornimmt, ein anderer Entwickler im Onlinemodus eine Änderung an der bereitgestellten Datenbank vornimmt. Ein Problem tritt auf, wenn der erste Entwickler versucht, das geänderte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt bereitzustellen. In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] wird nämlich erkannt, dass Objekte innerhalb der bereitgestellten Datenbank geändert wurden, und der Entwickler wird aufgefordert, die gesamte Datenbank zu überschreiben, wodurch auch die Änderungen des zweiten Entwicklers überschrieben werden. Da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nicht in der Lage ist, die Änderungen zwischen der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbankinstanz und den Objekten im Projekt, das überschrieben werden soll, aufzulösen, hat der erste Entwickler genau genommen nur die Möglichkeit, alle eigenen Änderungen zu verwerfen und die Änderungen erneut an einem neuen Projekt vorzunehmen, das auf der aktuellen Version der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank basiert.  
  
  
