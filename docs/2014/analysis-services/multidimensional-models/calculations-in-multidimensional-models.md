---
title: Berechnungen in mehrdimensionalen Modellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/10/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], creating
- deleting calculations
- calculations [Analysis Services], scripts
- Cube Designer
- modifying scripts
- removing calculations
- calculations [Analysis Services], deleting
- scripts [Analysis Services], calculations
- cubes [Analysis Services], calculations
- solve orders [Analysis Services]
ms.assetid: c21b3459-9bef-45a2-aba5-c992eba5b66e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 838e3a8d2df72d1589fdf76198671fee571e2e62
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75229424"
---
# <a name="calculations-in-multidimensional-models"></a>Berechnungen in mehrdimensionalen Modellen
  Mithilfe der Registerkarte **Berechnungen** des Cube-Designers können Sie berechnete Elemente, benannte Mengen sowie andere MDX-Berechnungen (Multidimensional Expressions) erstellen.  
  
 Die Registerkarte **Berechnungen** setzt sich aus den folgenden drei Bereichen zusammen:  
  
-   Im **Skriptplaner** -Bereich werden die Berechnungen in einem Cube aufgelistet. Mit diesem Bereich können Sie Berechnungen erstellen, strukturieren und für die Bearbeitung auswählen.  
  
-   Im **Berechnungstools** -Bereich werden Metadaten, Funktionen und Vorlagen zum Erstellen von Berechnungen bereitgestellt.  
  
-   Der Berechnungsausdrücke-Bereich unterstützt eine Formularansicht und eine Skriptansicht.  
  
> [!NOTE]  
>  Weitere Informationen zu MDX-Skripts finden [Sie unter Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892). Weitere Informationen finden Sie auf der Microsoft TechNet-Website auf der Seite [SQL Server 2005-Analysis Services](https://go.microsoft.com/fwlink/?LinkId=80853) . Weitere Informationen zu Leistungsproblemen im Zusammenhang mit dem Cubedesign finden Sie unter [SQL Server 2005 Analysis Services Performance Guide](https://download.microsoft.com/download/8/5/e/85eea4fa-b3bb-4426-97d0-7f7151b2011c/ssas2005perfguide.doc).  
  
## <a name="creating-a-new-calculation"></a>Erstellen einer neuen Berechnung  
 Zum Erstellen einer neuen Berechnung klicken Sie im Menü **Cube** auf der Registerkarte **Berechnungen** des Cube-Designers auf eine der Optionen **Neues berechnetes Element**, **Neue benannte Menge**oder **Neuer Skriptbefehl**, abhängig von der Art der Berechnung, die Sie erstellen möchten. Sie können auch auf eine der entsprechenden Schaltflächen auf der Symbolleiste oder mit der rechten Maustaste auf eine beliebige Stelle innerhalb des Bereichs **Skriptplaner** und dann auf einen der Befehle im Kontextmenü klicken. Durch diese Aktion wird dem **Skriptplaner** -Bereich eine neue Berechnung hinzugefügt, und im Berechnungsformular des Berechnungsausdrücke-Bereichs werden entsprechende Felder angezeigt. Wenn Sie ein neues Skript erstellen, wird durch diese Aktion die Skriptansicht im Berechnungsausdrücke-Bereich geöffnet. Weitere Informationen zu den drei Arten von Berechnungen finden Sie unter [Erstellen von berechneten Elementen](create-calculated-members.md), [Erstellen von benannten Mengen](create-named-sets.md)und [Definieren von Zuweisungen und anderen Skriptbefehlen](define-assignments-and-other-script-commands.md).  
  
## <a name="editing-scripts"></a>Bearbeiten von Skripts  
 Bearbeiten Sie die Skripts im Bereich Berechnungs Ausdrücke der Registerkarte **Berechnungen** . Der Bereich Berechnungs Ausdrücke verfügt über zwei Ansichten, die Skript Ansicht und die Formularansicht. In der Formularansicht werden die Ausdrücke und Eigenschaften eines einzelnen Befehls angezeigt. Beim Bearbeiten eines MDX-Skripts nimmt ein Ausdrucksfeld die gesamte Formularansicht ein.  
  
 Die Skriptansicht stellt einen Code-Editor für die Bearbeitung der Skripts bereit. Wird der Berechnungsausdrücke-Bereich in der Skriptansicht angezeigt, ist der **Skriptplaner** -Bereich ausgeblendet. In der Skriptansicht stehen Farbcodierung, Vervollständigen von Klammern, automatische Vervollständigung und MDX-Codebereiche zur Verfügung. Die MDX-Codebereiche können zum Vereinfachen der Bearbeitung reduziert oder erweitert werden.  
  
 Sie können zwischen der Formular- und der Skriptansicht hin- und herwechseln, indem Sie im Menü **Cube** auf **Berechnungen anzeigen in**zeigen und dann auf **Skript** oder **Formular**klicken. Sie können auch auf der Symbolleiste entweder auf **Formularansicht** oder **Skriptansicht** klicken.  
  
## <a name="changing-solve-order"></a>Ändern der Lösungsreihenfolge  
 Berechnungen werden in der Reihenfolge aufgelöst, in der sie im **Skriptplaner** -Bereich aufgelistet sind. Indem Sie mit der rechten Maustaste auf eine beliebige Berechnung klicken und anschließend im Kontextmenü auf **Nach oben** oder **Nach unten** klicken, können Sie die Reihenfolge der Berechnungen ändern. Alternativ können Sie auf eine Berechnung klicken und dann auf der Symbolleiste auf die Schaltfläche **Nach oben** oder **Nach unten** klicken.  
  
 Für berechnete Zellen und berechnete Elemente kann die Reihenfolge manuell überschrieben werden. Weitere Informationen zur Durchlauf- und Lösungsreihenfolge finden Sie unter [Grundlegendes zu Durchlauf- und Lösungsreihenfolge &#40;MDX&#41;](mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
## <a name="deleting-a-calculation"></a>Löschen einer Berechnung  
 Wenn Sie eine vorhandene Berechnung löschen möchten, wählen Sie auf der Registerkarte **Berechnungen** im **Skriptplaner** -Bereich die zu löschende Berechnung aus, und klicken Sie dann im Menü **Bearbeiten** auf **Löschen** , oder klicken Sie auf der Symbolleiste auf **Löschen** . Sie können auch im Bereich **Skriptplaner** mit der rechten Maustaste auf die Berechnung klicken und im Kontextmenü die Option **Löschen** auswählen.  
  
  
