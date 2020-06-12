---
title: Eigenschaften der Attribut Beziehung konfigurieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 241fa2af16377fd2cacf657ec6f99c5ca4bd0c53
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544702"
---
# <a name="configure-attribute-relationship-properties"></a>Konfigurieren von Attributbeziehungseigenschaften
  In der folgenden Tabelle sind die Eigenschaften einer Attributbeziehung aufgeführt und beschrieben.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|attribute|Enthält den Namen des Attributs.|  
|Cardinality|Zeigt die Kardinalität der Beziehung an. Werte sind Many für eine m:1-Beziehung oder One für eine 1:1-Beziehung. Der Standardwert lautet Many. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] hat die Kardinalität-Eigenschaft keine Auswirkung. die Verwendung ist für eine zukünftige Implementierung reserviert.|  
|Name|Enthält den Anzeigenamen des Attributs.|  
|RelationshipType|Gibt an, ob die Elementbeziehungen im Laufe der Zeit geändert werden. Werte sind Rigid, d.h., dass die Beziehungen zwischen Elementen im Laufe der Zeit nicht geändert werden, oder Flexible, d.h., dass die Beziehungen zwischen Elementen im Laufe der Zeit geändert werden. Der Standardwert ist Flexible. Wenn Sie eine Beziehung vom Typ Flexible definieren, werden Aggregationen gelöscht und als Teil eines inkrementellen Updates neu berechnet. Sie werden nicht gelöscht, wenn nur neue Elemente hinzugefügt werden. Wenn Sie eine Beziehung vom Typ Rigid definieren, werden von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Aggregationen beim inkrementellen Aktualisieren der Dimension beibehalten. Wenn eine als Beziehung vom Typ Rigid definierte Beziehung tatsächlich geändert wird, wird während der inkrementellen Verarbeitung von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ein Fehler generiert. Durch das Angeben der entsprechenden Beziehungen und Beziehungseigenschaften wird die Abfrage- und Verarbeitungsleistung erhöht.|  
|Sichtbar|Bestimmt die Sichtbarkeit der Attributbeziehung. Die Werte sind True und False. Der Standardwert lautet "True".|  
  
  
