---
title: Bereitstellen von SQL Server-Datentools (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.deploystatus.f1
ms.assetid: 67dde3fe-ba43-41f3-b56c-c656029ee93f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6429fb7f30c748c7ac0a8ab69bc16c3d63b4d3ae
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66067299"
---
# <a name="deploy-from-sql-server-data-tools-ssas-tabular"></a>Bereitstellen in SQL Server-Datentools (SSAS – tabellarisch)
  Verwenden Sie die Aufgaben in diesem Thema, um mit dem Befehl "Bereitstellen" in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]eine Projektmappe für tabellarische Modelle bereitzustellen.  
  
 Abschnitte in diesem Thema:  
  
-   [Konfigurieren der Eigenschaften "Bereitstellungsoptionen" und "Bereitstellungsserver"](#bkmk_deploy)  
  
-   [Bereitstellen einer Projektmappe für tabellarische Modelle](#bkmk_deploy_proc)  
  
-   [Bereitstellungsstatus](#bkmk_deploy_status)  
  
##  <a name="bkmk_deploy"></a> Konfigurieren der Eigenschaften "Bereitstellungsoptionen" und "Bereitstellungsserver"  
 Bevor Sie die Projektmappe für tabellarische Modelle bereitstellen, müssen Sie die Eigenschaft Bereitstellungsoptionen und die Eigenschaft Bereitstellungsserver angeben. Weitere Informationen zu Bereitstellungseigenschaften und -einstellungen finden Sie unter [Bereitstellung von Tabellenmodelllösungen &#40;SSAS – tabellarisch&#41;](tabular-model-solution-deployment-ssas-tabular.md)eine Projektmappe für tabellarische Modelle bereitzustellen.  
  
#### <a name="to-configure-deployment-options-and-deployment-server-properties"></a>So konfigurieren Sie die Eigenschaften "Bereitstellungsoptionen" und "Bereitstellungsserver"  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektnamen, und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  In der  **\<Projektname > Eigenschaften** Dialogfeld im **Bereitstellungsoptionen**, geben Sie Einstellungen aus, wenn diese von den Standardeinstellungen abweichen.  
  
    > [!NOTE]  
    >  Für Modelle, die sich im zwischengespeicherten Modus befinden, ist der **Abfragemodus** immer auf **InMemory**festgelegt.  
  
    > [!NOTE]  
    >  Für Modelle im DirectQuery-Modus können keine **Identitätswechseleinstellungen** angegeben werden.  
  
3.  Legen Sie unter **Bereitstellungsserver**die Einstellungen der Eigenschaften **Server** (Name), **Edition**, **Datenbank** (Name) und **Cubename** fest, falls diese von den Standardeinstellungen abweichen, und klicken Sie anschließend auf **OK**.  
  
> [!NOTE]  
>  Sie können auch die Einstellung der Eigenschaft Standardbereitstellungsserver angeben, damit alle neu erstellten Projekte automatisch auf dem angegebenen Server bereitgestellt werden. Weitere Informationen finden Sie unter [Konfigurieren von Standarddatenmodellierung und Bereitstellungseigenschaften &#40;SSAS – tabellarisch&#41;](properties-ssas-tabular.md)eine Projektmappe für tabellarische Modelle bereitzustellen.  
  
##  <a name="bkmk_deploy_proc"></a> Bereitstellen einer Projektmappe für tabellarische Modelle  
  
#### <a name="to-deploy-a-tabular-model-solution"></a>So stellen Sie eine Projektmappe für tabellarische Modelle bereit  
  
-   In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]auf die **erstellen** Menü klicken Sie auf **bereitstellen \<Projektname >**.  
  
     Im Dialogfeld **Bereitstellen** wird der Status der Metadatenbereitstellung und der Verarbeitung jeder im Modell enthaltenen Tabelle angezeigt (es sei denn, die Eigenschaft „Verarbeitungsoption“ wurde auf „Nicht verarbeiten“ festgelegt). Stellen Sie nach Abschluss des Bereitstellungsprozesses mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine Verbindung mit der Analysis Services-Instanz her, und überprüfen Sie, ob das neue Modelldatenbankobjekt erstellt wurde, oder verwenden Sie die Clientberichterstellungsanwendung, um eine Verbindung mit dem bereitgestellten Modell herzustellen.  
  
##  <a name="bkmk_deploy_status"></a> Bereitstellungsstatus  
 Im Dialogfeld **Bereitstellen** können Sie den Status eines Bereitstellungsvorgangs überwachen. Außerdem kann ein Bereitstellungsvorgang beendet werden.  
  
 **Status**  
 Gibt an, ob der Bereitstellungsvorgang erfolgreich war.  
  
 **Details**  
 Listet die bereitgestellten Metadatenelemente sowie den Status für jedes Metadatenelement auf und stellt eine Meldung über etwaige Probleme bereit.  
  
 **Bereitstellung beenden**  
 Klicken Sie auf diese Option, um den Bereitstellungsvorgang anzuhalten. Diese Option ist nützlich, wenn der Bereitstellungsvorgang zu lange dauert oder wenn es zu viele Fehler gibt.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellung von Tabellenmodelllösungen &#40;SSAS – tabellarisch&#41;](tabular-model-solution-deployment-ssas-tabular.md)   
 [Konfigurieren von Standarddatenmodellierung und Bereitstellungseigenschaften &#40;SSAS – tabellarisch&#41;](properties-ssas-tabular.md)  
  
  
