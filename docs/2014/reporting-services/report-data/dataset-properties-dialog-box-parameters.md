---
title: Dataseteigenschaften (Dialogfeld), Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10150"
- sql12.rtp.rptdesigner.datasetproperties.parameters.f1
ms.assetid: 43b00aab-e2c3-4e85-abe1-a2b5a21efeed
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e02a79570258fb15125094709a9fe5f3cf67bb7c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153780"
---
# <a name="dataset-properties-dialog-box-parameters"></a>Dataseteigenschaften (Dialogfeld), Parameter
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Parameter** aus, um Abfrageparameter, einschließlich Abfrageparameter, die einen Link zu Berichtsparametern herstellen, hinzuzufügen, zu ändern und zu löschen.  
  
 Bei jedem Ändern der Abfrage auf der Abfrageregisterkarte wird der Abfragebefehl analysiert. Für jeden Abfrageparameter, der identifiziert wird, wird ein Berichtsparameter mit einem identischen Namen erstellt, bei dem Groß-/Kleinschreibung beachtet werden muss. Standardmäßig wird der Abfrageparameter der Abfrageparameterliste automatisch hinzugefügt und mit dem entsprechenden Berichtsparameter verknüpft.  
  
 Wenn die Standardwerte eines Berichtsparameters von einem anderen Berichtsparameter, der mit einem Abfrageparameter verknüpft ist, abhängig sind, ist die Reihenfolge der Berichtsparameter (wie sie im Dialogfeld **Berichtsparametereigenschaften** angezeigt wird) entscheidend. Berichtsparameter weiter unten in der Liste können auf Berichtsparameter weiter oben in der Liste verweisen. Weitere Informationen zu Berichtsparametern finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="options"></a>Tastatur  
 **Hinzufügen**  
 Fügt der Liste einen neuen Parameter hinzu.  
  
 **Delete**  
 Entfernt den ausgewählten Parameter aus der Liste.  
  
 **Parametername**  
 Geben Sie auf der Registerkarte **Abfrage** des Dialogfelds **Dataseteigenschaften** den Namen eines Abfrageparameters ein, den Sie zum Dataset hinzugefügt haben.  
  
 **Parameterwert**  
 Geben Sie einen Wert für den Abfrageparameter ein. Dies kann ein statischer Wert sein oder ein Ausdruck, der sich auf ein Objekt innerhalb des Berichts bezieht. Der Ausdruck darf sich jedoch nicht auf Berichtselemente oder Felder beziehen. Standardmäßig enthält **Wert** einen Ausdruck, der auf einen Berichtsparameter verweist.  
  
 **Pfeil nach oben**  
 Verschiebt den ausgewählten Parameter in der Liste nach oben.  
  
 **Pfeil nach unten**  
 Verschiebt den ausgewählten Parameter in der Liste nach unten.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md)   
 [Ändern der Reihenfolge von Berichtsparametern &#40;Berichts-Generator und SSRS&#41;](../report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
  
