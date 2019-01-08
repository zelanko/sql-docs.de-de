---
title: Bereitstellen von Analysis Services-tabellenmodellen von SQL Server Data Tools | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 09d859cf8b5c372b9588266b9210837012396ea6
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072137"
---
# <a name="deploy-from-sql-server-data-tools"></a>Bereitstellen in SQL Server Data Tools
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Verwenden Sie die Aufgaben in diesem Thema, um eine Projektmappe für tabellarische Modelle mit dem Bereitstellungsbefehl in SSDT bereitstellen.  
  
##  <a name="bkmk_deploy"></a> Konfigurieren der Eigenschaften "Bereitstellungsoptionen" und "Bereitstellungsserver"  
 Bevor Sie die Projektmappe für tabellarische Modelle bereitstellen, müssen Sie die Eigenschaft Bereitstellungsoptionen und die Eigenschaft Bereitstellungsserver angeben. Weitere Informationen zu Bereitstellungseigenschaften und Einstellungen finden Sie unter [Bereitstellung von tabellenmodelllösungen](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
#### <a name="to-configure-options-and-properties"></a>Zum Konfigurieren von Optionen und Eigenschaften  
  
1.  In SSDT im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektnamen, und klicken Sie dann auf **Eigenschaften**.  
  
2.  In der  **\<Projektname > Eigenschaften** Dialogfeld im **Bereitstellungsoptionen**, geben Sie Einstellungen aus, wenn diese von den Standardeinstellungen abweichen.  
  
    > [!NOTE]  
    >  Für Modelle, die sich im zwischengespeicherten Modus befinden, ist der **Abfragemodus** immer auf **InMemory**festgelegt.  
  
    > [!NOTE]  
    >  Für Modelle im DirectQuery-Modus können keine **Identitätswechseleinstellungen** angegeben werden.  
  
3.  Legen Sie unter **Bereitstellungsserver**die Einstellungen der Eigenschaften **Server** (Name), **Edition**, **Datenbank** (Name) und **Cubename** fest, falls diese von den Standardeinstellungen abweichen, und klicken Sie anschließend auf **OK**.  
  
> [!NOTE]  
>  Sie können auch die Einstellung der Eigenschaft Standardbereitstellungsserver angeben, damit alle neu erstellten Projekte automatisch auf dem angegebenen Server bereitgestellt werden. Weitere Informationen finden Sie unter [konfigurieren Sie die Modellierung und Bereitstellung Standardeigenschaften](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md).  
  
##  <a name="bkmk_deploy_proc"></a> Bereitstellen eines tabellarischen Modells  
  
#### <a name="to-deploy-a-tabular-model"></a>Bereitstellen ein tabellarisches Modells
  
-   In SSDT auf das **erstellen** Menü klicken Sie auf **bereitstellen \<Projektname >**.  
  
     Im Dialogfeld **Bereitstellen** wird der Status der Metadatenbereitstellung und der Verarbeitung jeder im Modell enthaltenen Tabelle angezeigt (es sei denn, die Eigenschaft „Verarbeitungsoption“ wurde auf „Nicht verarbeiten“ festgelegt). Nachdem der Bereitstellungsvorgang abgeschlossen ist, verwenden von SSMS eine Verbindung mit Analysis Services-Instanz, und stellen Sie sicher, dass das neue modelldatenbankobjekt erstellt wurde, oder verwenden Sie die clientberichterstellungsanwendung, um eine Verbindung mit dem bereitgestellten Modell herstellen.  
  
##  <a name="bkmk_deploy_status"></a> Bereitstellungsstatus  
 Im Dialogfeld **Bereitstellen** können Sie den Status eines Bereitstellungsvorgangs überwachen. Außerdem kann ein Bereitstellungsvorgang beendet werden.  
  
 **Status**  
 Gibt an, ob der Bereitstellungsvorgang erfolgreich war.  
  
 **Details**  
 Listet die bereitgestellten Metadatenelemente sowie den Status für jedes Metadatenelement auf und stellt eine Meldung über etwaige Probleme bereit.  
  
 **Bereitstellung beenden**  
 Klicken Sie auf diese Option, um den Bereitstellungsvorgang anzuhalten. Diese Option ist nützlich, wenn der Bereitstellungsvorgang zu lange dauert oder wenn es zu viele Fehler gibt.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellung von tabellenmodelllösungen](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)   
 [Konfigurieren von Standarddatenmodellierung und Bereitstellungseigenschaften](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
  
  
