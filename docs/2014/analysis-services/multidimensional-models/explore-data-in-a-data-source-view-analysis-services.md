---
title: Durchsuchen von Daten in einer Datenquellen Sicht (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
author: minewiskan
ms.author: owend
ms.openlocfilehash: 28db322a38ae90206ae0c43db1c8c039e6395b8b
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546742"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a>Durchsuchen von Daten in einer Datenquellensicht (Analysis Services)
  Sie können das Dialogfeld **Daten durchsuchen** im Datenquellensicht-Designer von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] verwenden, um Daten für eine Tabelle, eine Sicht oder eine benannte Abfrage in einer Datenquellensicht (data source view; DSV) zu durchsuchen. Wenn Sie die Daten im Datenquellensicht-Designer durchsuchen, können Sie den Inhalt jeder Datenspalte in einer ausgewählten Tabelle, Sicht oder benannten Abfrage anzeigen. Das Anzeigen des tatsächlichen Inhalts hilft Ihnen, zu bestimmen, ob alle Spalten benötigt werden, ob benannte Berechnungen erforderlich sind, um Benutzerfreundlichkeit und Zweckmäßigkeit zu erhöhen, und ob vorhandene benannte Berechnungen oder benannte Abfragen die erwarteten Werte zurückgeben.  
  
 Zum Anzeigen von Daten müssen Sie über eine aktive Verbindung mit der Datenquelle bzw. den Datenquellen für das ausgewählte Objekt in der Datenquellensicht verfügen. Alle benannten Berechnungen in einer Tabelle werden ebenfalls in der Abfrage gesendet.  
  
 Die in einem tabellarischen Format zurückgegebenen Daten, die sortiert und kopiert werden können. Klicken Sie auf die Spaltenüberschriften, um die Zeilen nach dieser Spalte erneut zu sortieren. Sie können auch Daten im Raster hervorheben und STRG+C drücken, um die Auswahl in die Zwischenablage zu kopieren.  
  
 Sie können zudem die Stichprobenmethode und die Anzahl für die Stichprobe steuern. Standardmäßig werden die obersten 5000 Zeilen zurückgegeben.  
  
## <a name="to-browse-data-or-change-sampling-options"></a>So durchsuchen Sie Daten oder ändern Stichprobenoptionen  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das Projekt, oder stellen Sie eine Verbindung mit der Datenbank her, das bzw. die die Datenquellensicht enthält, in der Sie Daten durchsuchen möchten.  
  
2.  Erweitern Sie im Projektmappen-Explorer den Ordner **Datenquellensichten** , und doppelklicken Sie anschließend auf die Datenquellensicht.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Tabelle, Sicht oder benannte Abfrage, die die anzuzeigenden Daten enthält, und klicken Sie anschließend auf **Daten durchsuchen**.  
  
     Die Datenquelle, die der Tabelle, Sicht oder benannten Abfrage in der Datenquellen Sicht zugrunde liegt, sind Abfragen, und die Ergebnisse werden auf der Registerkarte ** \<object name> Tabelle durchsuchen** angezeigt.  
  
4.  Klicken Sie auf der Symbolleiste ** \<object name> Tabelle durchsuchen** auf das Symbol **Stichproben Optionen** .  
  
     Das Dialogfeld **Optionen zum Durchsuchen von Daten** wird geöffnet. In diesem Dialogfeld können Sie die Stichprobenmethode (mehr oder weniger Datensätze als die Standardstichprobengröße von 5000 Zeilen) oder die Anzahl für die Stichprobe angeben.  
  
5.  Klicken Sie nach Bedarf auf **OK** oder **Abbrechen** .  
  
6.  Um die Daten neu zu überprüfen, klicken Sie auf der Symbolleiste der ** \<object name> Tabelle** auf " **Daten neu Sample** ".  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenquellsichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md)  
  
  
