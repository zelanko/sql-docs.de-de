---
title: Mit der Analysis Services-Bereitstellungs-Assistent | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d459bafe395a10af75f8c0a721f0a8a08f39b3c6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208509"
---
# <a name="running-the-analysis-services-deployment-wizard"></a>Ausführen des Bereitstellungs-Assistenten für Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent kann die folgenden Arten ausgeführt werden:  
  
-   **Interaktiv** bei interaktiver Ausführung der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent generiert ein Bereitstellungsskript basierend auf den Eingabedateien an, wie durch die Benutzereingabe interaktiv geänderten. Der Assistent wendet alle Änderungen durch den Benutzer ausschließlich auf das Bereitstellungsskript an. Der Assistent nimmt dabei keine Änderungen an den Eingabedateien vor. Weitere Informationen zu den Eingabedateien finden Sie unter [Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md).  
  
-   **Über die Eingabeaufforderung** Ausführung an der Eingabeaufforderung die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent generiert ein Skript der Bereitstellung auf der Basis der Schalter, mit denen Sie den Assistenten ausführen. Der Assistent kann dann einen der folgenden Schritte ausführen: den Benutzer zur Eingabe auffordern und die Eingabedateien entsprechend der Benutzereingabe ändern, eine unbeaufsichtigte Bereitstellung mithilfe der unveränderten Eingabedateien durchführen oder ein Bereitstellungsskript erstellen, das vom Benutzer zu einem späteren Zeitpunkt verwendet werden kann.  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a>Interaktives Ausführen des Bereitstellungs-Assistenten für Analysis Services  
 Wenn Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] interaktiv ausführen, liest er die Werte aus den Eingabedateien und präsentiert Ihnen diese Informationen. Sie können diese Eingabe, die Werte wie z. als Bereitstellungsziel, Konfigurationseinstellungen, Bereitstellungsoptionen und Kennwörter für Verbindungszeichenfolgen-, oder lassen sie unverändert. Wenn Sie alle eingegebenen Werte ändern, verwendet der Assistent diese Änderungen beim Generieren des Bereitstellungsskripts an. Der Assistent nimmt dabei jedoch keine Änderungen an den Werten in der Eingabedatei vor.  
  
> [!NOTE]  
>  Wenn Sie möchten, dass der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Änderungen an den Eingabewerten vornimmt, müssen Sie den Assistenten an der Eingabeaufforderung ausführen und dabei festlegen, dass der Assistent im Antwortmodus ausgeführt wird.  
  
 Nachdem Sie die Eingabewerte überprüft und ggf. geändert haben, generiert der Assistent das Bereitstellungsskript an. Sie können dieses Bereitstellungsskript entweder sofort auf dem Zielserver ausführen oder zur späteren Verwendung speichern.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a>So führen Sie den Bereitstellungs-Assistenten für Analysis Services interaktiv aus  
  
-   Klicken Sie auf **starten** > **Microsoft SQL Server** > **Bereitstellungs-Assistent**.  
  
     -oder-  
  
-   In der **Projekte** Ordner die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt, doppelklicken Sie auf die \<Projektname > .asdatabase-Datei.
    > [!NOTE]  
    >  Wenn Sie die Datei .asdatabase nicht sofort finden können, verwenden Sie Suchen, und geben Sie dabei *.asdatabase an. Oder Sie müssen zum Erstellen des Projekts in SSDT.  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Ausführen des Bereitstellungs-Assistenten für Analysis Services an der Eingabeaufforderung  
 Der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] kann auch an der Eingabeaufforderung ausgeführt werden. Wenn Sie den Assistenten an der Eingabeaufforderung ausführen, geben Sie den vollständigen Pfad zur ASDATABASE-Datei an, und führen Sie den Assistenten in einem der folgenden Modi aus:  
  
 **Antwortdateimodus**  
 Im Antwortdateimodus können Sie die Eingabedateien interaktiv ändern, die ursprünglich beim Erstellen des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]generiert wurden. Der Assistent speichert diese geänderten Eingabedateien, bevor Sie das Bereitstellungsskript generieren. Die geänderten Eingabedateien werden dann zum Ausgangspunkt beim nächsten Ausführen des Assistenten.  
  
 Verwenden Sie zum Ausführen des Assistenten im antwortdateimodus den **/a** wechseln.  
  
 **Unbeaufsichtigter Modus**  
 Im unbeaufsichtigten Modus führt der Assistent auf der Basis der in den Eingabedateien enthaltenen Informationen eine Bereitstellung im Hintergrund aus, ohne dass dabei in irgendeiner Weise eingegriffen werden muss.  
  
 Verwenden Sie zum Ausführen des Assistenten im unbeaufsichtigten Modus den **/s** wechseln. Wenn Sie den Assistenten im unbeaufsichtigten Modus ausführen, werden Meldungen an die Konsole ausgegeben oder an eine Protokolldatei (sofern vorhanden).  
  
 **Ausgabemodus**  
 Im Ausgabemodus generiert der Assistent ein Bereitstellungsskript für die spätere Ausführung basierend auf den Eingabedateien.  
  
 Verwenden Sie zum Ausführen des Assistenten im Ausgabemodus den **/o** Schalter, und geben Sie einen Ausgabedateinamen.  
  
 Weitere Informationen zu diesen Befehlszeilenoptionen finden Sie unter [Bereitstellen von Modelllösungen mit dem Bereitstellungshilfsprogramm](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md).  
  
 Im folgenden Verfahren wird beschrieben, wie der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an der Eingabeaufforderung ausgeführt wird.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>So führen Sie den Bereitstellungs-Assistenten für Analysis Services an der Eingabeaufforderung aus  
  
1.  Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zu der C:\Program Files (x86) \Microsoft SQL Server\140\Tools\Binn\ManagementStudio  
  
2.  Geben Sie **Microsoft.AnalysisServices.Deployment.exe** ein und darauf folgend die Schalter für den Modus, in dem der Assistent ausgeführt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zum Analysis Services-Bereitstellungsskript](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)   
 [Bereitstellen von Modelllösungen mithilfe des Bereitstellungs-Assistenten](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
