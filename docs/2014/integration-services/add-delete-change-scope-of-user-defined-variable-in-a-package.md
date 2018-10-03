---
title: Hinzufügen, löschen, Ändern des Bereichs von benutzerdefinierten Variablen in einem Paket | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], adding
ms.assetid: cbf40c7f-3c8a-48cd-aefa-8b37faf8b40e
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: abc9f00432128750e4b61e971038bbc32dd85e86
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125700"
---
# <a name="add-delete-change-scope-of-user-defined-variable-in-a-package"></a>Hinzufügen, Löschen, Ändern des Bereichs von benutzerdefinierten Variablen in einem Paket
  In diesen Verfahren wird beschrieben, wie eine benutzerdefinierte Variable in einem Paket mithilfe des Fensters **Variablen** hinzugefügt oder gelöscht und ihr Bereich geändert wird.  
  
 Weitere Informationen zu Variablenbereichen finden Sie unter [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] bietet außerdem Systemvariablen, die Systeminformationen zur Verfügung stellen, zur Laufzeit in Containern, z. B. Paketen und Ereignishandlern verwendet werden können. Systemvariablen können nicht gelöscht werden.  
  
### <a name="to-add-a-variable"></a>So fügen Sie eine Variable hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das gewünschte [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Gehen Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer zum Definieren des Gültigkeitsbereichs der Variablen wie folgt vor:  
  
    -   Um den Gültigkeitsbereich des Pakets festzulegen, klicken Sie an eine beliebige Stelle auf der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** .  
  
    -   Um den Gültigkeitsbereich auf einen Ereignishandler festzulegen, wählen Sie eine ausführbare Datei und einen Ereignishandler auf der Entwurfsoberfläche der Registerkarte **Ereignishandler** aus.  
  
    -   Um den Gültigkeitsbereich auf einen Task oder Container festzulegen, klicken Sie auf der Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** oder **Ereignishandler** auf einen Task oder Container.  
  
4.  Klicken Sie im Menü **SSIS** auf **Variablen**. Sie können das Fenster **Variablen** auch anzeigen, indem Sie im Dialogfeld **Optionen** auf der Seite **Tastatur** den Befehl View.Variables einer beliebigen Tastenkombination zuordnen.  
  
5.  Klicken Sie im Fenster **Variablen** auf das Symbol **Variable hinzufügen** . Die neue Variable wird der Liste hinzugefügt.  
  
6.  Klicken Sie wahlweise auf das Symbol **Rasteroptionen** , wählen Sie zusätzliche Spalten aus, die im Dialogfeld **Variable Rasteroptionen** angezeigt werden sollen, und klicken Sie dann auf **OK**.  
  
7.  Legen Sie optional die Variableneigenschaften fest. Weitere Informationen finden Sie unter [Festlegen der Eigenschaften von benutzerdefinierten Variablen](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md).  
  
8.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
### <a name="to-delete-a-variable"></a>So löschen Sie eine Variable  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im Menü **SSIS** auf **Variablen**. Sie können das Fenster **Variablen** auch anzeigen, indem Sie im Dialogfeld **Optionen** auf der Seite **Tastatur** den Befehl View.Variables einer beliebigen Tastenkombination zuordnen.  
  
4.  Wählen Sie die zu löschende Variable aus, und klicken Sie dann auf **Variable löschen**.  
  
     Wenn die Variable nicht im Fenster Variablen angezeigt wird, klicken Sie auf **Rasteroptionen** , und wählen Sie dann **Variablen aller Bereiche anzeigen**aus.  
  
5.  Wenn das Dialogfeld **Löschen der Variablen bestätigen** aufgerufen wird, klicken Sie zur Bestätigung auf **Ja** .  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
### <a name="to-change-the-scope-of-a-variable"></a>So ändern Sie den Bereich einer Variablen  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im Menü **SSIS** auf **Variablen**. Sie können das Fenster **Variablen** auch anzeigen, indem Sie im Dialogfeld **Optionen** auf der Seite **Tastatur** den Befehl View.Variables einer beliebigen Tastenkombination zuordnen.  
  
4.  Wählen Sie die Variable aus, und klicken Sie dann auf **Variable verschieben**.  
  
     Wenn die Variable nicht im Fenster Variablen angezeigt wird, klicken Sie auf **Rasteroptionen** , und wählen Sie dann **Variablen aller Bereiche anzeigen**aus.  
  
5.  Wählen Sie im Dialogfeld **Neuen Bereich auswählen** das Paket oder einen Container, Task oder Ereignishandler im Paket aus, um den Gültigkeitsbereich der Variablen zu ändern.  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Integrationsdienste &#40;SSIS&#41; Variablen](integration-services-ssis-variables.md)   
 [Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md)   
 [Legen Sie die Eigenschaften einer benutzerdefinierten Variablen](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)   
 [Verwenden der Werte von Variablen und Parametern in einem untergeordneten Paket](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
  
