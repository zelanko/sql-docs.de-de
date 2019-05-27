---
title: 'Lektion 8: Definieren von Aktionen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 15459396-83c9-48a0-b10a-99ae38768c79
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8293bb8d1f0465d09b296cbd18702b569f073766
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66078232"
---
# <a name="lesson-8-defining-actions"></a>Lektion 8: Definieren von Aktionen
  In dieser Lektion erfahren Sie, wie Sie Aktionen in Ihrem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt definieren können. Eine Aktion bezeichnet einfach eine in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] gespeicherte MDX-Anweisung (Multidimensional Expressions), die in Clientanwendungen integriert und von Benutzern gestartet werden kann.  
  
> [!NOTE]  
>  Für alle Lektionen in diesem Lernprogramm sind abgeschlossene Projekte online verfügbar. Sie können jede Lektion aufrufen, indem Sie ein abgeschlossenes Projekt aus der vorherigen Lektion als Ausgangspunkt verwenden. [Klicken Sie hier](https://go.microsoft.com/fwlink/?LinkID=221866) , um die Beispielprojekte für dieses Lernprogramm herunterzuladen.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt die in der folgenden Tabelle beschriebenen Typen von Aktionen.  
  
|||  
|-|-|  
|CommandLine|Führt einen Befehl an der Eingabeaufforderung aus.|  
|Dataset|Gibt ein Dataset an eine Clientanwendung zurück.|  
|Drillthrough ausführen|Gibt eine Drillthroughanweisung als Ausdruck zurück, den der Client zur Rückgabe eines Rowsets ausführt.|  
|Html|Führt ein HTML-Skript in einem Internetbrowser aus.|  
|Proprietär|Führt einen Vorgang über eine Schnittstelle aus, die nicht in dieser Tabelle aufgelistet ist.|  
|Bericht|Übermittelt eine parametrisierte, URL-basierte Anforderung an einen Berichtsserver und gibt einen Bericht an eine Clientanwendung zurück.|  
|Rowset|Gibt ein Rowset an eine Clientanwendung zurück.|  
|Anweisung|Gibt einen OLE DB-Befehl zurück.|  
|URL|Zeigt eine dynamische Webseite in einem Internetbrowser an.|  
  
 Aktionen ermöglichen es Benutzern, eine Anwendung zu starten oder andere Schritte innerhalb des Kontexts eines bestimmten Elements auszuführen. Weitere Informationen finden Sie unter [Aktionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) und [Aktionen in mehrdimensionalen Modellen](multidimensional-models/actions-in-multidimensional-models.md).  
  
> [!NOTE]  
>  Beispielaktionen finden Sie in den Aktionsbeispielen auf der Registerkarte Vorlagen im Bereich Berechnungstools oder in den Beispielen des [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW-Data Warehouse-Beispiels. Weitere Informationen zum Installieren dieser Datenbank finden Sie unter [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).  
  
 Diese Lektion enthält den folgenden Task:  
  
 [Definieren und Verwenden einer Drillthroughaktion](lesson-8-1-defining-and-using-a-drillthrough-action.md)  
 In diesem Task definieren, verwenden und ändern Sie eine Drillthroughaktion über die Faktendimensionsbeziehung, die Sie zu einem früheren Zeitpunkt in diesem Lernprogramm definiert haben.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 9: Definieren von Perspektiven und Übersetzungen](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Lernprogrammszenario](analysis-services-tutorial-scenario.md)   
 [Mehrdimensionale Modellierung &#40;Adventure Works-Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md)   
 [Aktionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)   
 [Aktionen in mehrdimensionalen Modellen](multidimensional-models/actions-in-multidimensional-models.md)  
  
  
