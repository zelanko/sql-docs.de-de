---
title: Dataseteigenschaften (Dialogfeld), Parameter | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: reference
f1_keywords:
- "10150"
- sql13.rtp.rptdesigner.datasetproperties.parameters.f1
- "10023"
ms.assetid: 43b00aab-e2c3-4e85-abe1-a2b5a21efeed
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 66e0d56cbff57a6100ab8c61436ba6bcddf15382
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "65573176"
---
# <a name="dataset-properties-dialog-box-parameters"></a>Dataseteigenschaften (Dialogfeld), Parameter
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Parameter** aus, um Abfrageparameter, einschließlich Abfrageparameter, die einen Link zu Berichtsparametern herstellen, hinzuzufügen, zu ändern und zu löschen.  
  
 Bei jedem Ändern der Abfrage auf der Abfrageregisterkarte wird der Abfragebefehl analysiert. Für jeden Abfrageparameter, der identifiziert wird, wird ein Berichtsparameter mit einem identischen Namen erstellt, bei dem Groß-/Kleinschreibung beachtet werden muss. Standardmäßig wird der Abfrageparameter der Abfrageparameterliste automatisch hinzugefügt und mit dem entsprechenden Berichtsparameter verknüpft.  
  
 Wenn die Standardwerte eines Berichtsparameters von einem anderen Berichtsparameter, der mit einem Abfrageparameter verknüpft ist, abhängig sind, ist die Reihenfolge der Berichtsparameter (wie sie im Dialogfeld **Berichtsparametereigenschaften** angezeigt wird) entscheidend. Berichtsparameter weiter unten in der Liste können auf Berichtsparameter weiter oben in der Liste verweisen. Weitere Informationen zu Berichtsparametern finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="options"></a>Tastatur  
 **Add (Hinzufügen)**  
 Fügt der Liste einen neuen Parameter hinzu.  
  
 **Löschen**  
 Entfernt den ausgewählten Parameter aus der Liste.  
  
 **Parametername**  
 Geben Sie auf der Registerkarte **Abfrage** des Dialogfelds **Dataseteigenschaften** den Namen eines Abfrageparameters ein, den Sie zum Dataset hinzugefügt haben.  
  
 **Parameterwert**  
 Geben Sie einen Wert für den Abfrageparameter ein. Dies kann ein statischer Wert sein oder ein Ausdruck, der sich auf ein Objekt innerhalb des Berichts bezieht. Der Ausdruck darf sich jedoch nicht auf Berichtselemente oder Felder beziehen. Standardmäßig enthält **Wert** einen Ausdruck, der auf einen Berichtsparameter verweist.  
  
 **Pfeil nach oben**  
 Verschiebt den ausgewählten Parameter in der Liste nach oben.  
  
 **Pfeil nach unten**  
 Verschiebt den ausgewählten Parameter in der Liste nach unten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Berichtsdatasets &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Ändern der Reihenfolge von Berichtsparametern &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
  
