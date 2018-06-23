---
title: Hinzufügen von Cube (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.addcubedimensiondialog.f1
helpviewer_keywords:
- Add Cube Dimension dialog box
ms.assetid: 625a3b1f-183b-445f-9bb7-96945c324767
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ff89f880df12126f173f1f5ad47d1841e532262d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162387"
---
# <a name="add-cube-dimension-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Cubedimension hinzufügen' (Analysis Services – Mehrdimensionale Daten)
  Im Dialogfeld **Cubedimension hinzufügen** von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie einem Cube einen Verweis auf eine Datenbankdimension hinzufügen. Sie können das Dialogfeld **Cubedimension hinzufügen** folgendermaßen anzeigen:  
  
-   Öffnen Sie Cube-Designer, und klicken Sie im Bereich **Symbolleiste** der Registerkarte **Cubestruktur** oder der Registerkarte **Dimensionsverwendung** auf **Cubedimension hinzufügen** .  
  
-   Öffnen Sie Cube-Designer, klicken Sie mit der rechten Maustaste auf den Bereich **Dimensionen** der Registerkarte **Cubestruktur** , und wählen Sie im Kontextmenü die Option **Cubedimension hinzufügen** aus.  
  
-   Öffnen Sie Cube-Designer, klicken Sie mit der rechten Maustaste auf den Bereich **Raster** der Registerkarte **Dimensionsverwendung** , und wählen Sie im Kontextmenü die Option **Cubedimension hinzufügen** aus.  
  
> [!NOTE]  
>  Jede Cubedimension darf immer nur eine Beziehung zu einer Measuregruppe enthalten. Sie können jedoch mehrere Cubedimensionen erstellen und zum Cube hinzufügen, falls die der Cubedimension zugrunde liegende Datenbankdimension ihrerseits über mehrere Beziehungen mit Measuregruppen in der Datenquellensicht verknüpft ist. Diese Dimensionen werden auch als Dimensionen mit unterschiedlichen Rollen bezeichnet und treten häufig zusammen mit Zeitdimensionen auf.  
  
## <a name="options"></a>Tastatur  
 **Dimension auswählen**  
 Wählen Sie eine vorhandene Datenbankdimension aus, um dem ausgewählten Cube eine darauf basierende Cubedimension hinzuzufügen. Von einer Datenbankdimension können verschiedene Cubedimensionen definiert werden.  
  
> [!NOTE]  
>  Wenn einem Cube mehrere auf derselben Datenbankdimension basierende Cubedimensionen hinzufügt werden, werden die zusätzlich hinzugefügten Cubedimensionen auch als Dimensionen mit unterschiedlichen Rollen bezeichnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  