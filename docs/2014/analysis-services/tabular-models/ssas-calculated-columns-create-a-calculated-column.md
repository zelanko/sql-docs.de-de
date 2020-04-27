---
title: Erstellen einer berechneten Spalte (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.as.daxref.CreataCalculatedColumn.f1
ms.assetid: 59440510-2d76-41dc-9b55-edc15259f9da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 60218cb5f50777ac07e9a2805d224d80bef7975d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66066523"
---
# <a name="create-a-calculated-column-ssas-tabular"></a>Erstellen einer berechneten Spalte (SSAS – tabellarisch)
  Mithilfe berechneter Spalten können Sie dem Modell neue Daten hinzufügen. Anstatt Werte in die Spalte einfügen oder importieren zu müssen, erstellen Sie eine DAX-Formel, die die Zeilen Ebenen Werte der Spalte definiert. Die Werte in den einzelnen Zeilen einer berechneten Spalte werden berechnet und aufgefüllt, wenn Sie eine gültige Formel erstellen und die EINGABETASTE drücken. Die berechnete Spalte kann anschließend wie jeder andere Datenspalte einer Berichterstellungs- oder Analyseanwendung hinzugefügt werden. In diesem Thema wird beschrieben, wie eine neue berechnete Spalte mithilfe der DAX-Bearbeitungsleiste im Modell-Designer erstellt wird.  
  
#### <a name="to-create-a-new-calculated-column"></a>So erstellen Sie eine neue berechnete Spalte  
  
1.  Wählen Sie im Modell-Designer in der Datensicht die Tabelle aus, der Sie eine berechnete Spalte hinzufügen möchten, und klicken Sie dann auf das Menü **Spalte** und auf **Spalte hinzufügen**.  
  
     In der leeren Spalte am äußersten rechten Rand wird**Spalte hinzufügen** hervorgehoben, und der Cursor wird in die Bearbeitungsleiste verschoben.  
  
     Klicken Sie mit der rechten Maustaste auf eine vorhandene Spalte, und klicken Sie dann auf **Spalte einfügen**, um zwischen zwei vorhandenen Spalten eine neue Spalte zu erstellen.  
  
2.  Führen Sie in der Bearbeitungsleiste einen der folgenden Schritte aus:  
  
    -   Geben Sie ein Gleichheitszeichen gefolgt von einer Formel ein.  
  
    -   Geben Sie ein Gleichheitszeichen gefolgt von einer DAX-Funktion, den Argumenten und Parametern ein, die von der Funktion benötigt werden.  
  
    -   Klicken Sie auf die Funktionsschaltfläche (**fx**), und wählen Sie dann im Dialogfeld **Funktion einfügen** eine Kategorie und eine Funktion aus. Klicken Sie abschließend auf **OK**. Geben Sie in der Bearbeitungsleiste die übrigen Argumente und Parameter ein, die von der Funktion benötigt werden.  
  
3.  Drücken Sie die EINGABETASTE, um die Formel zu übernehmen.  
  
     Die gesamte Spalte wird mit der Formel aufgefüllt, d. h., für jede Zeile wird ein Wert berechnet.  
  
> [!TIP]  
>  Sie können AutoVervollständigen für DAX-Formeln auch mitten in einer vorhandenen Formel mit geschachtelten Funktionen verwenden. Ausgehend vom Text unmittelbar vor der Einfügemarke werden Werte in der Dropdownliste angezeigt. Der Text nach der Einfügemarke bleibt unverändert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berechnete Spalten &#40;tabellarischen SSAS-&#41;](ssas-calculated-columns.md)   
 [Measures &#40;SSAS – tabellarisch&#41;](measures-ssas-tabular.md)  
  
  
