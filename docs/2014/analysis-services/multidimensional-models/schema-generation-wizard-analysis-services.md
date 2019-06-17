---
title: Schemagenerierungs-Assistent (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- relational schema [Analysis Services]
ms.assetid: 68bf7ba3-d0cb-437f-9a3e-9edc0999af19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2f8757044ba15f7b8c2567dd88e1ef3637d2e3f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66073071"
---
# <a name="schema-generation-wizard-analysis-services"></a>Schemagenerierungs-Assistent (Analysis Services)
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] unterstützt zwei Methoden der Verwendung relationaler Schemas, wenn OLAP-Objekte innerhalb von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekten oder -Datenbanken definiert werden. Normalerweise erfolgt die Definition von OLAP-Objekten basierend auf einem logischen Datenmodell, das in einer Datenquellensicht innerhalb eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts oder einer Datenbank gebildet wird. Diese Datenquellensicht wird basierend auf Schemaelementen aus einer oder mehreren relationalen Datenquellen (wie in der Datenquellensicht angepasst) definiert.  
  
 Alternativ können Sie zuerst OLAP-Objekte definieren und dann eine Datenquellensicht, eine Datenquelle und das zugrunde liegende relationale Datenbankschema generieren, von dem diese OLAP-Objekte unterstützt werden. Diese relationale Datenbank wird als Themenbereichsdatenbank bezeichnet.  
  
 Dieser Ansatz wird mitunter Top-Down-Entwurf genannt und wird häufig für die Erstellung von Prototypen und die Modellierung zu Analysezwecken verwendet. Wenn Sie diesen Ansatz verwenden, können Sie mit dem Schemagenerierungs-Assistenten die zugrunde liegende Datenquellensicht und die Datenquellenobjekte auf Grundlage der in einem Projekt oder einer Datenbank von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] definierten OLAP-Objekte erstellen.  
  
 Dies ist eine iterative Vorgehensweise. Wahrscheinlich müssen Sie den Assistenten mehrere Male erneut ausführen, während Sie das Design der Dimensionen und Cubes ändern. Bei jeder Ausführung des Assistenten werden die Änderungen in die zugrunde liegenden Objekte integriert und so viele Daten der zugrunde liegenden Datenbanken wie möglich beibehalten.  
  
 Das generierte Schema entspricht einem relationalen SQL Server-Datenbank-Engine-Schema. Der Assistent generiert keine Schemas für andere relationale Datenbankprodukte.  
  
 Die Daten, mit denen die Themenbereichsdatenbank aufgefüllt wird, werden getrennt hinzugefügt, und zwar mit dem Tools und Techniken, die Sie zum Auffüllen einer relationalen SQL Server-Datenbank verwenden. In den meisten Fällen werden die Daten beibehalten, wenn Sie den Assistenten erneut ausführen; es gibt jedoch auch Ausnahmen. Einige Daten müssen beispielsweise gelöscht werden, wenn Sie Dimensionen oder Attribute löschen, in denen diese Daten enthalten sind. Wenn der Schemagenerierungs-Assistent einige Daten aufgrund einer Schemaänderung löschen muss, wird vor dem Löschen der Daten eine Warnung angezeigt, sodass Sie die erneute Generierung abbrechen können.  
  
 In der Regel werden Änderungen an Objekten, die ursprünglich vom Schemagenerierungs-Assistenten generiert wurden, überschrieben, wenn der Schemagenerierungs-Assistent dieses Objekt später erneut generiert. Die wichtigste Ausnahme von dieser Regel stellen Spalten dar, die Sie zu einer vom Schemagenerierungs-Assistenten generierten Tabelle hinzufügen. In diesem Fall behält der Schemagenerierungs-Assistent die zur Tabelle hinzugefügten Spalten sowie die Daten in diesen Spalten bei.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In der folgenden Tabelle sind die zusätzlichen Themen in diesem Abschnitt aufgeführt, in denen die Verwendung des Schemagenerierungs-Assistenten erklärt wird.  
  
|Thema|Description|  
|-----------|-----------------|  
|[Verwenden des Schemagenerierungs-Assistenten &#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md)|Beschreibt, wie das Schema für die Themenbereichs- und Stagingbereichsdatenbanken generiert wird.|  
|[Grundlegendes zu Datenbankschemas](understanding-the-database-schemas.md)|Beschreibt das Schema, das für die Themenbereichs- und Stagingbereichsdatenbanken generiert wird.|  
|[Grundlegendes zur inkrementellen Generierung](understanding-incremental-generation.md)|Beschreibt die Funktionen der inkrementellen Generierung des Schemagenerierungs-Assistenten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellsichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md)   
 [Datenquellen in mehrdimensionalen Modellen](data-sources-in-multidimensional-models.md)   
 [Unterstützte Datenquellen &#40;SSAS – mehrdimensional&#41;](supported-data-sources-ssas-multidimensional.md)  
  
  
