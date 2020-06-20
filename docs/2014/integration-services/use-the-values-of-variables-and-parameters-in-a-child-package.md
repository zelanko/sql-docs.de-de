---
title: Verwenden der Werte von Variablen und Parametern in einem untergeordneten Paket | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- configurations [Integration Services]
- packages [Integration Services], configurations
- variables [Integration Services], adding
ms.assetid: 9b939edb-4e17-48e5-8428-855beb10049c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 19f96adc9932b888f3304257fb9a23a22b06cc87
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972610"
---
# <a name="use-the-values-of-variables-and-parameters-in-a-child-package"></a>Verwenden der Werte von Variablen und Parametern in einem untergeordneten Paket
  In diesem Verfahren wird das Erstellen einer Paketkonfiguration beschrieben, die den Konfigurationstyp der übergeordneten Variablen verwendet. Durch diesen Konfigurationstyp kann ein untergeordnetes Paket, das von einem übergeordneten Paket ausgeführt wird, auf eine Variable im übergeordneten Element zugreifen.  
  
> [!NOTE]  
>  Sie können auch Werte an ein untergeordnetes Paket übergeben, indem Sie den Task Paket ausführen konfigurieren, um untergeordneten Paketparametern Variablen oder Parameter für übergeordnete Pakete bzw. Projektparameter zuzuordnen. Weitere Informationen finden Sie unter [Task ' Paket ausführen](control-flow/execute-package-task.md)'.  
  
 Dabei ist das Erstellen der Variablen im übergeordneten Paket vor dem Erstellen der Paketkonfiguration im untergeordneten Paket nicht erforderlich. Sie können dem übergeordneten Paket jederzeit die Variable hinzufügen. Allerdings müssen Sie in der Paketkonfiguration den genauen Namen der übergeordneten Variablen verwenden. Bevor Sie jedoch eine übergeordnete Variablenkonfiguration erstellen können, muss im untergeordneten Paket bereits eine Variable vorhanden sein, die von der Konfiguration aktualisiert werden kann. Weitere Informationen zum Hinzufügen und Konfigurieren von Variablen finden Sie unter [Hinzufügen, Löschen, Ändern des Bereichs von benutzerdefinierten Variablen in einem Paket](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).  
  
 Der Gültigkeitsbereich der Variablen im übergeordneten Paket, das in einer übergeordneten Variablenkonfiguration verwendet wird, kann auf den Task Paket ausführen, auf den Container, in dem der Task enthalten ist, oder auf das Paket festgelegt werden. Wenn in einem Paket mehrere gleichnamige Variablen vorhanden sind, wird die Variable verwendet, die im Gültigkeitsbereich des Tasks Paket ausführen am nächsten liegt. Der Gültigkeitsbereich, der am nächsten am Task Paket ausführen liegt, ist der Task selbst.  
  
### <a name="to-add-a-variable-to-a-parent-package"></a>So fügen Sie einem übergeordneten Paket eine Variable hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket, dem Sie eine Variable hinzufügen möchten, um diese an ein untergeordnetes Paket zu übergeben.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Gehen Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer zum Definieren des Gültigkeitsbereichs der Variablen wie folgt vor:  
  
    -   Um den Gültigkeitsbereich des Pakets festzulegen, klicken Sie an eine beliebige Stelle auf der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** .  
  
    -   Klicken Sie auf den Container, um den Gültigkeitsbereich des übergeordneten Containers des Tasks "Paket ausführen" festzulegen.  
  
    -   Klicken Sie auf den Task, um den Bereich auf den Task "Paket ausführen" festzulegen.  
  
4.  Fügen Sie eine Variable hinzu, und konfigurieren Sie diese.  
  
    > [!NOTE]  
    >  Wählen Sie einen Datentyp aus, der mit den in der Variablen gespeicherten Daten kompatibel ist.  
  
5.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
### <a name="to-add-a-variable-to-a-child-package"></a>So fügen Sie einem untergeordneten Paket eine Variable hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket, dem Sie eine übergeordnete Variablenkonfiguration hinzufügen möchten.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer an eine beliebige Stelle auf der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** , um den Gültigkeitsbereich des Pakets festzulegen.  
  
4.  Fügen Sie eine Variable hinzu, und konfigurieren Sie diese.  
  
    > [!NOTE]  
    >  Wählen Sie einen Datentyp aus, der mit den in der Variablen gespeicherten Daten kompatibel ist.  
  
5.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
### <a name="to-add-a-parent-package-configuration-to-a-child-package"></a>So fügen Sie einem untergeordneten Paket eine übergeordnete Paketkonfiguration hinzu  
  
1.  Öffnen Sie das untergeordnete Paket in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], falls das Paket noch nicht geöffnet ist.  
  
2.  Klicken Sie an eine beliebige Stelle auf der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** .  
  
3.  Klicken Sie im Menü **SSIS** auf **Paketkonfigurationen**.  
  
4.  Wählen Sie im Dialogfeld **Paketkonfigurationsplaner** die Option **Paketkonfigurationen aktivieren**aus, und klicken Sie dann auf **Hinzufügen**.  
  
5.  Klicken Sie auf der Willkommensseite des Paketkonfigurations-Assistenten auf **Weiter**.  
  
6.  Wählen Sie auf der Seite Konfigurationstyp auswählen in der Liste **Konfigurationstyp** die Option **Übergeordnete Paketvariable** aus, und führen Sie eine der folgenden Aktionen aus:  
  
    -   Wählen Sie die Option **Konfigurationseinstellungen direkt angeben**aus, und stellen Sie dann im Feld **Übergeordnete Variable** den Variablennamen des in der Konfiguration zu verwendenden übergeordneten Pakets bereit.  
  
        > [!IMPORTANT]  
        >  Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.  
  
    -   Wählen Sie **Konfigurationsspeicherort ist in einer Umgebungsvariablen gespeichert** aus. Wählen Sie dann in der Liste **Umgebungsvariable**die Umgebungsvariable aus, die den Namen der Variablen enthält.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Erweitern Sie auf der Seite Zieleigenschaft auswählen den Knoten **Variable** , erweitern Sie den Knoten **Eigenschaften** der zu konfigurierenden Variablen, und klicken Sie dann auf die von der Konfiguration festzulegende Eigenschaft.  
  
9. Klicken Sie auf **Weiter**.  
  
10. Ändern Sie optional auf der Seite Assistenten abschließen den Standardnamen der Konfiguration, und überprüfen Sie die Konfigurationsinformationen.  
  
11. Klicken Sie auf **Fertig stellen** , um den Assistenten zu beenden und zum Dialogfeld **Paketkonfigurationsplaner** zurückzukehren.  
  
12. Die neue Konfiguration wird im Dialogfeld **Paketkonfigurationsplaner** im Feld **Konfiguration** aufgelistet.  
  
13. Klicken Sie auf **Schließen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Paket Konfigurationen](../../2014/integration-services/package-configurations.md)   
 [Erstellen von Paket Konfigurationen](../../2014/integration-services/create-package-configurations.md)   
 [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md)   
 [Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md)  
  
  
