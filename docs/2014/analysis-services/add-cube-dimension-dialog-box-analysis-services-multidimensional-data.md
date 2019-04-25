---
title: Hinzufügen von Cube (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.addcubedimensiondialog.f1
helpviewer_keywords:
- Add Cube Dimension dialog box
ms.assetid: 625a3b1f-183b-445f-9bb7-96945c324767
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2115fe7f5faf5c68f72b9eaaef452961da3d02fc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62626067"
---
# <a name="add-cube-dimension-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Cubedimension hinzufügen' (Analysis Services – Mehrdimensionale Daten)
  Im Dialogfeld **Cubedimension hinzufügen** von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] können Sie einem Cube einen Verweis auf eine Datenbankdimension hinzufügen. Sie können das Dialogfeld **Cubedimension hinzufügen** folgendermaßen anzeigen:  
  
-   Öffnen Sie Cube-Designer, und klicken Sie im Bereich **Symbolleiste** der Registerkarte **Cubestruktur** oder der Registerkarte **Dimensionsverwendung** auf **Cubedimension hinzufügen** .  
  
-   Öffnen Sie Cube-Designer, klicken Sie mit der rechten Maustaste auf den Bereich **Dimensionen** der Registerkarte **Cubestruktur** , und wählen Sie im Kontextmenü die Option **Cubedimension hinzufügen** aus.  
  
-   Öffnen Sie Cube-Designer, klicken Sie mit der rechten Maustaste auf den Bereich **Raster** der Registerkarte **Dimensionsverwendung** , und wählen Sie im Kontextmenü die Option **Cubedimension hinzufügen** aus.  
  
> [!NOTE]  
>  Jede Cubedimension darf immer nur eine Beziehung zu einer Measuregruppe enthalten. Sie können jedoch mehrere Cubedimensionen erstellen und zum Cube hinzufügen, falls die der Cubedimension zugrunde liegende Datenbankdimension ihrerseits über mehrere Beziehungen mit Measuregruppen in der Datenquellensicht verknüpft ist. Diese Dimensionen werden auch als Dimensionen mit unterschiedlichen Rollen bezeichnet und treten häufig zusammen mit Zeitdimensionen auf.  
  
## <a name="options"></a>Optionen  
 **Dimension auswählen**  
 Wählen Sie eine vorhandene Datenbankdimension aus, um dem ausgewählten Cube eine darauf basierende Cubedimension hinzuzufügen. Von einer Datenbankdimension können verschiedene Cubedimensionen definiert werden.  
  
> [!NOTE]  
>  Wenn einem Cube mehrere auf derselben Datenbankdimension basierende Cubedimensionen hinzufügt werden, werden die zusätzlich hinzugefügten Cubedimensionen auch als Dimensionen mit unterschiedlichen Rollen bezeichnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
