---
title: Importieren Sie ein Integration Services-Projekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 3301c328-b0f5-4517-915c-93713413e453
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8fb6b68cbb30e9bbf19f854cf1dd1e7e0dd19d25
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768042"
---
# <a name="import-an-integration-services-project"></a>Importieren eines Integration Services-Projekts
  Erstellen Sie mithilfe des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-**Assistenten zum Importieren von Projekten** ein Projekt aus einer vorhandenen Bereitstellungsdatei (ISPAC-Datei) oder aus einem Projekt, das für den Integration Services-Katalog bereitgestellt wurde. Diese Funktion ist besonders nützlich, wenn Sie das Originalexemplar des Projekts nicht haben, aber ein Projekt aus einer ISPAC-Datei oder einem SSISDB-Katalog erstellen möchten.  
  
### <a name="to-import-a-project"></a>So importieren Sie ein Projekt  
  
1.  Klicken Sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]im Menü **Datei** > **auf** Neu **Projekt** .  
  
2.  Erweitern Sie im Bereich **Installierte Vorlagen** des Fensters **Neues Projekt** **Business Intelligence**, und klicken Sie auf **Integration Services**.  
  
3.  Wählen Sie **Integration Services-Assistent zum Importieren von Projekten** aus der Liste der Projekttypen aus.  
  
4.  Geben Sie einen Namen für das neu zu erstellende Projekt im Textfeld **Name** ein.  
  
5.  Geben Sie den Pfad oder Speicherort für das Projekt im Textfeld **Speicherort** ein, oder klicken Sie auf **Durchsuchen** , um ihn auszuwählen.  
  
6.  Geben Sie einen Namen für die Projektmappe im Textfeld **Projektmappenname** ein.  
  
7.  Klicken Sie auf **OK** , um das Dialogfeld **Integration Services-Assistent zum Importieren von Projekten** zu starten.  
  
8.  Klicken Sie auf **Weiter** , um zur Seite **Quelle auswählen** zu wechseln.  
  
9. Wenn Sie aus einer **ISPAC-Datei** importieren, geben Sie den Pfad einschließlich Dateinamen im Textfeld **Pfad** ein. Klicken Sie auf **Durchsuchen** , um zu dem Ordner zu navigieren, in dem die Projektmappe gespeichert werden soll. Geben Sie den Dateinamen im Textfeld **Dateiname** ein, und klicken Sie auf **Öffnen**.  
  
     Wenn Sie aus einem **Integration Services-Katalog**importieren, geben Sie den Datenbankinstanznamen im Textfeld **Servername** ein, oder klicken Sie auf **Durchsuchen** und wählen Sie die Datenbankinstanz aus, die den Katalog enthält.  
  
     Klicken Sie auf **Durchsuchen** neben dem Textfeld **Pfad** , erweitern Sie den Ordner im Katalog, wählen Sie das Projekt aus, das Sie importieren möchten, und klicken Sie auf **OK**.  
  
     Klicken Sie auf **Weiter** , um zur Seite **///Überprüfen** zu wechseln.  
  
10. Überprüfen Sie die Informationen, und klicken Sie auf **Importieren** , um ein Projekt auf Grundlage des vorhandenen Projekts zu erstellen, das Sie ausgewählt haben.  
  
11. Optional: Klicken Sie auf **Bericht speichern** , um die Ergebnisse in einer Datei zu speichern.  
  
12. Klicken Sie auf **Schließen** , um das Dialogfeld **Integration Services-Assistent zum Importieren von Projekten** zu schließen.  
  
  
