---
title: Mit der Analysis Services-Bereitstellungs-Assistent | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: d8fd34a7e614c1c1bb247f84846e090d22ea053e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66073037"
---
# <a name="running-the-analysis-services-deployment-wizard"></a>Ausführen des Bereitstellungs-Assistenten für Analysis Services
  Wenn Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zum Bereitstellen eines [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts verwenden, gibt es folgende Möglichkeiten, um diesen Assistenten auszuführen:  
  
-   **Interaktiv** Bei interaktiver Ausführung generiert der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf der Basis der durch die Benutzereingabe interaktiv geänderten Eingabedateien ein XML-Bereitstellungsskript. Der Assistent wendet alle Änderungen durch den Benutzer ausschließlich auf das Bereitstellungsskript an. Der Assistent nimmt dabei keine Änderungen an den Eingabedateien vor. Weitere Informationen zu den Eingabedateien finden Sie unter [Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien](deployment-script-files-input-used-to-create-deployment-script.md).  
  
-   **Über die Eingabeaufforderung** Ausführung an der Eingabeaufforderung die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent generiert einen XML for Analysis (XMLA)-Bereitstellungsskript, die auf der Basis der Schalter, mit denen Sie den Assistenten ausführen. Der Assistent kann dann einen der folgenden Schritte ausführen: den Benutzer zur Eingabe auffordern und die Eingabedateien entsprechend der Benutzereingabe ändern, eine unbeaufsichtigte Bereitstellung mithilfe der unveränderten Eingabedateien durchführen oder ein Bereitstellungsskript erstellen, das vom Benutzer zu einem späteren Zeitpunkt verwendet werden kann.  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a>Interaktives Ausführen des Bereitstellungs-Assistenten für Analysis Services  
 Wenn Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] interaktiv ausführen, liest er die Werte aus den Eingabedateien und präsentiert Ihnen diese Informationen. Sie können diese Eingabe, die Werte wie z. als Bereitstellungsziel, Konfigurationseinstellungen, Bereitstellungsoptionen und Kennwörter für Verbindungszeichenfolgen-, oder lassen sie unverändert. Wenn Sie Änderungen an den Eingabewerten vornehmen, verwendet der Assistent diese Änderungen beim Generieren des XMLA-Bereitstellungsskripts. Der Assistent nimmt dabei jedoch keine Änderungen an den Werten in der Eingabedatei vor.  
  
> [!NOTE]  
>  Wenn Sie möchten, dass der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Änderungen an den Eingabewerten vornimmt, müssen Sie den Assistenten an der Eingabeaufforderung ausführen und dabei festlegen, dass der Assistent im Antwortmodus ausgeführt wird.  
  
 Nachdem Sie die Eingabewerte überprüft und ggf. geändert haben, generiert der Assistent das XMLA-Bereitstellungsskript. Sie können dieses Bereitstellungsskript entweder sofort auf dem Zielserver ausführen oder zur späteren Verwendung speichern.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a>So führen Sie den Bereitstellungs-Assistenten für Analysis Services interaktiv aus  
  
-   Zeigen Sie im Menü **Start**auf **Alle Programme**, zeigen Sie auf **Microsoft SQL Server**, zeigen Sie auf **Analysis Services**, und klicken Sie dann auf **Bereitstellungs-Assistent**.  
  
     -oder-  
  
-   In der **Projekte** Ordner die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt, doppelklicken Sie auf die  *\<Projektname >* asdatabase-Datei.  
  
    > [!NOTE]  
    >  Wenn Sie nicht finden können die  *\<Projektname >* asdatabase-Datei, verwenden Sie suchen, und geben Sie dabei *.asdatabase an.  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Ausführen des Bereitstellungs-Assistenten für Analysis Services an der Eingabeaufforderung  
 Der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] kann auch an der Eingabeaufforderung ausgeführt werden. Wenn Sie den Assistenten an der Eingabeaufforderung ausführen, geben Sie den vollständigen Pfad zur ASDATABASE-Datei an, und führen Sie den Assistenten in einem der folgenden Modi aus:  
  
 **Antwortdateimodus**  
 Im Antwortdateimodus können Sie die Eingabedateien interaktiv ändern, die ursprünglich beim Erstellen des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]generiert wurden. Der Assistent speichert diese geänderten Eingabedateien, bevor er das XMLA-Bereitstellungsskript generiert. Die geänderten Eingabedateien werden dann zum Ausgangspunkt beim nächsten Ausführen des Assistenten.  
  
 Verwenden Sie zum Ausführen des Assistenten im antwortdateimodus den **/a** wechseln.  
  
 **Unbeaufsichtigter Modus**  
 Im unbeaufsichtigten Modus führt der Assistent auf der Basis der in den Eingabedateien enthaltenen Informationen eine Bereitstellung im Hintergrund aus, ohne dass dabei in irgendeiner Weise eingegriffen werden muss.  
  
 Verwenden Sie zum Ausführen des Assistenten im unbeaufsichtigten Modus den **/s** wechseln. Wenn Sie den Assistenten im unbeaufsichtigten Modus ausführen, werden Meldungen an die Konsole ausgegeben oder an eine Protokolldatei (sofern vorhanden).  
  
 **Ausgabemodus**  
 Im Ausgabemodus generiert der Assistent auf der Basis der Eingabedateien ein XMLA-Bereitstellungsskript, das zu einem späteren Zeitpunkt ausgeführt werden kann.  
  
 Verwenden Sie zum Ausführen des Assistenten im Ausgabemodus den **/o** Schalter, und geben Sie einen Ausgabedateinamen.  
  
 Weitere Informationen zu diesen Befehlszeilenoptionen finden Sie unter [Bereitstellen von Modelllösungen mit dem Bereitstellungshilfsprogramm](deploy-model-solutions-with-the-deployment-utility.md).  
  
 Im folgenden Verfahren wird beschrieben, wie der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an der Eingabeaufforderung ausgeführt wird.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>So führen Sie den Bereitstellungs-Assistenten für Analysis Services an der Eingabeaufforderung aus  
  
1.  Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zum Ordner C:\Programme\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE.  
  
2.  Geben Sie **Microsoft.AnalysisServices.Deployment.exe** ein und darauf folgend die Schalter für den Modus, in dem der Assistent ausgeführt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zum Analysis Services-Bereitstellungsskript](understanding-the-analysis-services-deployment-script.md)   
 [Bereitstellen von Modelllösungen mithilfe des Bereitstellungs-Assistenten](deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
