---
title: Im Dialogfeld Eigenschaften von Berichtseigenschaften Verweise | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10530"
- sql12.rtp.rptdesigner.reportproperties.references.f1
ms.assetid: 4639d368-9918-4bb1-9953-7a724ca78dea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e57e0eb15c8c0ae7e326927ab14493f21c52cc14
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66104294"
---
# <a name="report-properties-dialog-box-references"></a>Berichtseigenschaften (Dialogfeld), Verweise
  Wählen Sie die Registerkarte **Verweise** im Dialogfeld **Berichtseigenschaften** , um Verweise auf benutzerdefinierte oder andere externe Assemblys sowie benutzerdefinierte Klasseninstanzen hinzuzufügen oder zu entfernen, die von Ausdrücken in der Berichtsdefinition verwendet werden.  
  
## <a name="options"></a>Optionen  
 **Assemblys hinzufügen oder entfernen**  
 Führt die Assemblys auf, auf die der Bericht verweist. Die Assembly muss auf dem Computer, auf dem das Tool zum Entwerfen des Berichts installiert ist, und auf dem Berichtsserver verfügbar sein. Der Name des Verweises muss mit dem Inhalt der  **\<CodeModule >** -Tags in der Berichtsdefinitionssprache (RDL)-Datei übereinstimmen.  
  
 **Hinzufügen**  
 Klicken Sie auf diese Option, um eine Assembly hinzuzufügen. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...), zum Öffnen der **öffnen** Dialogfeld und die für die berichtsverarbeitung und ausdrucksauswertung erforderlichen Assemblys auszuwählen.  
  
 **Löschen**  
 Um einen Assemblyverweis aus der Liste zu entfernen, wählen Sie den Assemblynamen aus, und klicken Sie auf die Schaltfläche **Entfernen** .  
  
 **Klassen hinzufügen oder entfernen**  
 Führt die vom Bericht verwendeten Klasseninstanzen auf. Die Klassenliste wird nur von instanzbasierten Elementen, nicht von statischen Elementen, verwendet.  
  
 **Hinzufügen**  
 Klicken Sie auf diese Schaltfläche, um einen Klassenverweis hinzuzufügen. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...), zum Öffnen der **öffnen** Dialogfeld und die für die berichtsverarbeitung und ausdrucksauswertung erforderlichen Klassen auszuwählen.  
  
 **Löschen**  
 Um die Klasseninstanz zu löschen, wählen Sie sie aus, und klicken Sie auf die Schaltfläche **Entfernen** .  
  
 **Nach oben**  
 Für Klassen mit Abhängigkeiten können Sie diesen Verweis in der Liste nach oben verschieben.  
  
 **Nach unten**  
 Für Klassen mit Abhängigkeiten können Sie diesen Verweis in der Liste nach unten verschieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerdefinierter Code und Assemblyverweise in Ausdrücken in Berichts-Designer (SSRS)](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)   
 [Verweise auf Berichts- und Gruppenvariablensammlungen &#40;Berichts-Generator und SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
