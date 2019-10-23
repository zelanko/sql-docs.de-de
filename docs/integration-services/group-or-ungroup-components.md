---
title: Gruppieren von Komponenten oder Aufheben der Gruppierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- grouping containers
- tasks [Integration Services], grouping
- containers [Integration Services], grouping
- grouping tasks
ms.assetid: 34320838-c271-4f8c-90b3-1254690890bb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 999bdd02c0cbfa2f8d2df6be93b3261c5bdc1dc5
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71296381"
---
# <a name="group-or-ungroup-components"></a>Gruppieren von Komponenten oder Aufheben der Gruppierung

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Die Registerkarten **Ablaufsteuerung**, **Datenfluss**und **Ereignishandler** im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer unterstützen die reduzierbare Gruppierung. Wenn ein Paket viele Komponenten enthält, kann dies zu einer Überlastung der Registerkarten führen. In diesem Fall ist es schwierig, alle Komponenten gleichzeitig anzuzeigen und das gewünschte Element zu finden. Mit der Funktion für reduzierbare Gruppierung kann Platz auf der Arbeitsoberfläche gespart und die Arbeit mit großen Paketen erleichtert werden.  
  
 Sie wählen die Komponenten aus, die Sie gruppieren möchten, gruppieren sie und erweitern bzw. reduzieren dann die Gruppen entsprechend Ihren Anforderungen. Das Erweitern einer Gruppe ermöglicht den Zugriff auf die Eigenschaften der Komponenten in der Gruppe. Die Rangfolgeneinschränkungen, die Tasks und Container verbinden, werden automatisch in die Gruppe eingeschlossen.  
  
 Folgende Überlegungen gelten im Zusammenhang mit dem Gruppieren von Komponenten.  
  
-   Um Komponenten gruppieren zu können, muss die Ablaufsteuerung, der Datenfluss oder der Ereignishandler mehrere Komponenten enthalten.  
  
-   Gruppen können auch geschachtelt werden, wodurch Gruppen innerhalb von Gruppen erstellt werden können. Die Entwurfsoberfläche kann mehrere nicht geschachtelte Gruppen implementieren, eine Komponente kann aber nur einer Gruppe angehören, sofern die Gruppen nicht geschachtelt sind.  
  
-   Wenn ein Paket gespeichert wird, speichert der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer die Gruppierung, diese hat jedoch keine Auswirkung auf die Paketausführung. Die Möglichkeit der Gruppierung von Komponenten ist eine Entwurfszeitfunktion. Das Laufzeitverhalten des Pakets ist nicht davon betroffen.  
  
### <a name="to-group-components"></a>So gruppieren Sie Komponenten  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung**, **Datenfluss**oder **Ereignishandler** .  
  
4.  Wählen Sie auf der Entwurfsoberfläche der Registerkarte die Komponenten aus, die Sie gruppieren möchten, klicken Sie mit der rechten Maustaste auf eine ausgewählte Komponente, und klicken Sie anschließend auf **Gruppieren**.  
  
5.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
### <a name="to-ungroup-components"></a>So heben Sie die Gruppierung von Komponenten auf  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung**, **Datenfluss**oder **Ereignishandler** .  
  
4.  Wählen Sie auf der Entwurfsoberfläche der Registerkarte die Gruppe mit der Komponente aus, deren Gruppierung Sie aufheben möchten, führen Sie einen Rechtsklick aus, und klicken Sie anschließend auf **Gruppierung aufheben**.  
  
5.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung](../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Verbinden von Tasks und Containern mithilfe einer Standardrangfolgeneinschränkung](https://msdn.microsoft.com/library/8f31f15f-98ff-4c35-b41f-8b8cfd148d75)  
  
  
