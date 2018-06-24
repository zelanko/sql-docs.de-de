---
title: Bereitstellen von Analysis Services-Projekten (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2f0debea4f36bdf5eb5a3a5ac654bbaf9c6bd322
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050210"
---
# <a name="deploy-analysis-services-projects-ssdt"></a>Bereitstellen von Analysis Services-Projekten (SSDT)
  Während der Entwicklung eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]stellen Sie das Projekt häufig auf einem Entwicklungsserver bereit, um die vom Projekt definierte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank zu erstellen. Dies ist erforderlich, um das Projekt zu testen. Hierbei werden z. B. Zellen im Cube durchsucht, Dimensionselemente durchsucht oder KPI-Formeln (Key Performance Indicators) überprüft.  
  
## <a name="deploying-a-project"></a>Bereitstellen eines Projekts  
 Sie können ein Projekt eigenständig oder alle Projekte innerhalb der Projektmappe zusammen bereitstellen. Beim Bereitstellen eines Projekts werden nacheinander die folgenden Aktionen ausgeführt. Zuerst wird das Projekt erstellt. In diesem Schritt werden die Ausgabedateien erstellt, die die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank und die Objekte, aus denen sie besteht, definieren. Danach wird der Zielserver überprüft. Abschließend werden die Zieldatenbank und ihre Objekte auf dem Zielserver erstellt. Während der Bereitstellung werden vorher vorhandene Datenbanken vollständig von der Bereitstellungs-Engine durch die Inhalte des Projekts ersetzt, es sei denn, diese Objekte wurden durch das Projekt im Rahmen einer früheren Bereitstellung erstellt.  
  
 Nach der erstbereitstellung, wird die Datei IncrementalSnapshot.xml im generiert die \<Projektname > \obj-Ordner. Anhand dieser Datei wird bestimmt, ob die Datenbank oder ihre Objekte auf dem Zielserver außerhalb des Projekts verändert wurden. Ist dies der Fall, werden Sie aufgefordert, alle Objekte in der Zieldatenbank zu überschreiben. Wenn alle Änderungen innerhalb des Projekts vorgenommen wurden und die inkrementelle Bereitstellung für das Projekt konfiguriert wurde, werden nur die Änderungen auf dem Zielserver bereitgestellt.  
  
 Die Projektkonfiguration und die zugehörigen Einstellungen bestimmen die Bereitstellungseigenschaften, die für die Bereitstellung des Projekts verwendet werden. Bei einem freigegebenen Projekt kann jeder Entwickler seine eigene Konfiguration mit eigenen Projektkonfigurationsoptionen verwenden. So kann z. B. jeder Entwickler einen anderen Testserver angeben, um unabhängig von anderen Entwicklern arbeiten zu können.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen ein Analysis Services-Projekts &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md)  
  
  