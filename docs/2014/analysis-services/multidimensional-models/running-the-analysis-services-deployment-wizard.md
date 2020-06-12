---
title: Ausführen des Bereitstellungs-Assistenten für Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, running
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03e142f00192e04d5b17bc2041563cea06199c8b
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545709"
---
# <a name="running-the-analysis-services-deployment-wizard"></a>Ausführen des Bereitstellungs-Assistenten für Analysis Services
  Wenn Sie zum [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellen eines Projekts den Bereitstellungs-Assistenten verwenden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , können Sie den Assistenten wie folgt ausführen:  
  
-   **Interaktiv** Bei interaktiver Ausführung generiert der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf der Basis der durch die Benutzereingabe interaktiv geänderten Eingabedateien ein XML-Bereitstellungsskript. Der Assistent wendet alle Änderungen durch den Benutzer ausschließlich auf das Bereitstellungsskript an. Der Assistent nimmt dabei keine Änderungen an den Eingabedateien vor. Weitere Informationen zu den Eingabedateien finden Sie unter [Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien](deployment-script-files-input-used-to-create-deployment-script.md).  
  
-   **An der Eingabeaufforderung** Wenn Sie an der Eingabeaufforderung ausführen, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generiert der Bereitstellungs-Assistent ein XML for Analysis (XMLA)-Bereitstellungs Skript, das auf den Schaltern basiert, die Sie zum Ausführen des Assistenten verwenden. Der Assistent kann dann einen der folgenden Schritte ausführen: den Benutzer zur Eingabe auffordern und die Eingabedateien entsprechend der Benutzereingabe ändern, eine unbeaufsichtigte Bereitstellung mithilfe der unveränderten Eingabedateien durchführen oder ein Bereitstellungsskript erstellen, das vom Benutzer zu einem späteren Zeitpunkt verwendet werden kann.  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a>Interaktives Ausführen des Bereitstellungs-Assistenten für Analysis Services  
 Wenn Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] interaktiv ausführen, liest er die Werte aus den Eingabedateien und präsentiert Ihnen diese Informationen. Sie können diese Eingabewerte ändern, z. b. Bereitstellungs Ziel, Konfigurationseinstellungen, Bereitstellungs Optionen und Kenn Wörter für Verbindungs Zeichenfolgen, oder Sie unverändert lassen. Wenn Sie Änderungen an den Eingabewerten vornehmen, verwendet der Assistent diese Änderungen beim Generieren des XMLA-Bereitstellungsskripts. Der Assistent nimmt dabei jedoch keine Änderungen an den Werten in der Eingabedatei vor.  
  
> [!NOTE]  
>  Wenn Sie möchten, dass der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Änderungen an den Eingabewerten vornimmt, müssen Sie den Assistenten an der Eingabeaufforderung ausführen und dabei festlegen, dass der Assistent im Antwortmodus ausgeführt wird.  
  
 Nachdem Sie die Eingabewerte überprüft und ggf. geändert haben, generiert der Assistent das XMLA-Bereitstellungsskript. Sie können dieses Bereitstellungsskript entweder sofort auf dem Zielserver ausführen oder zur späteren Verwendung speichern.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a>So führen Sie den Bereitstellungs-Assistenten für Analysis Services interaktiv aus  
  
-   Zeigen Sie im Menü **Start**auf **Alle Programme**, zeigen Sie auf **Microsoft SQL Server**, zeigen Sie auf **Analysis Services**, und klicken Sie dann auf **Bereitstellungs-Assistent**.  
  
     - oder -  
  
-   Doppelklicken Sie im Projekt **Ordner des** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekts auf die *\<project name>* Datei. asdatabase.  
  
    > [!NOTE]  
    >  Wenn Sie die *\<project name>* . asdatabase-Datei nicht finden können, verwenden Sie die Suche, und geben Sie "*. asdatabase" an.  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Ausführen des Bereitstellungs-Assistenten für Analysis Services an der Eingabeaufforderung  
 Der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] kann auch an der Eingabeaufforderung ausgeführt werden. Wenn Sie den Assistenten an der Eingabeaufforderung ausführen, geben Sie den vollständigen Pfad zur ASDATABASE-Datei an, und führen Sie den Assistenten in einem der folgenden Modi aus:  
  
 **Antwortdateimodus**  
 Im Antwortdateimodus können Sie die Eingabedateien interaktiv ändern, die ursprünglich beim Erstellen des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]generiert wurden. Der Assistent speichert diese geänderten Eingabedateien, bevor er das XMLA-Bereitstellungsskript generiert. Die geänderten Eingabedateien werden dann zum Ausgangspunkt beim nächsten Ausführen des Assistenten.  
  
 Verwenden Sie den Schalter **/a** , um den Assistenten im Antwortdatei Modus auszuführen.  
  
 **Unbeaufsichtigter Modus**  
 Im unbeaufsichtigten Modus führt der Assistent auf der Basis der in den Eingabedateien enthaltenen Informationen eine Bereitstellung im Hintergrund aus, ohne dass dabei in irgendeiner Weise eingegriffen werden muss.  
  
 Verwenden Sie den Schalter **/s** , um den Assistenten im unbeaufsichtigten Modus auszuführen. Wenn Sie den Assistenten im unbeaufsichtigten Modus ausführen, werden Meldungen an die Konsole ausgegeben oder an eine Protokolldatei (sofern vorhanden).  
  
 **Ausgabemodus**  
 Im Ausgabemodus generiert der Assistent auf der Basis der Eingabedateien ein XMLA-Bereitstellungsskript, das zu einem späteren Zeitpunkt ausgeführt werden kann.  
  
 Verwenden Sie zum Ausführen des Assistenten im Ausgabemodus den **/o** -Schalter, und geben Sie einen Ausgabe Dateinamen an.  
  
 Weitere Informationen zu diesen Befehlszeilenoptionen finden Sie unter [Bereitstellen von Modelllösungen mit dem Bereitstellungshilfsprogramm](deploy-model-solutions-with-the-deployment-utility.md).  
  
 Im folgenden Verfahren wird beschrieben, wie der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an der Eingabeaufforderung ausgeführt wird.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>So führen Sie den Bereitstellungs-Assistenten für Analysis Services an der Eingabeaufforderung aus  
  
1.  Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zum Ordner C:\Programme\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE.  
  
2.  Geben Sie **Microsoft.AnalysisServices.Deployment.exe** ein und darauf folgend die Schalter für den Modus, in dem der Assistent ausgeführt werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zum Analysis Services Bereitstellungs Skript](understanding-the-analysis-services-deployment-script.md)   
 [Bereitstellen von Modelllösungen mithilfe des Bereitstellungs-Assistenten](deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
