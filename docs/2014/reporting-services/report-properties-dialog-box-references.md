---
title: Im Dialogfeld Eigenschaften von Berichtseigenschaften Verweise | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10530"
- sql12.rtp.rptdesigner.reportproperties.references.f1
ms.assetid: 4639d368-9918-4bb1-9953-7a724ca78dea
caps.latest.revision: 39
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: abc6ea1f5322303f8a4429f226e44fd32c018962
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299720"
---
# <a name="report-properties-dialog-box-references"></a>Berichtseigenschaften (Dialogfeld), Verweise
  Wählen Sie die Registerkarte **Verweise** im Dialogfeld **Berichtseigenschaften** , um Verweise auf benutzerdefinierte oder andere externe Assemblys sowie benutzerdefinierte Klasseninstanzen hinzuzufügen oder zu entfernen, die von Ausdrücken in der Berichtsdefinition verwendet werden.  
  
## <a name="options"></a>Tastatur  
 **Assemblys hinzufügen oder entfernen**  
 Führt die Assemblys auf, auf die der Bericht verweist. Die Assembly muss auf dem Computer, auf dem das Tool zum Entwerfen des Berichts installiert ist, und auf dem Berichtsserver verfügbar sein. Der Name des Verweises muss mit dem Inhalt der  **\<CodeModule >** -Tags in der Berichtsdefinitionssprache (RDL)-Datei übereinstimmen.  
  
 **Hinzufügen**  
 Klicken Sie auf diese Option, um eine Assembly hinzuzufügen. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...), um das Dialogfeld **Öffnen** aufzurufen und die für die Berichtsverarbeitung und Ausdrucksauswertung erforderlichen Assemblys auszuwählen.  
  
 **Delete**  
 Um einen Assemblyverweis aus der Liste zu entfernen, wählen Sie den Assemblynamen aus, und klicken Sie auf die Schaltfläche **Entfernen** .  
  
 **Klassen hinzufügen oder entfernen**  
 Führt die vom Bericht verwendeten Klasseninstanzen auf. Die Klassenliste wird nur von instanzbasierten Elementen, nicht von statischen Elementen, verwendet.  
  
 **Hinzufügen**  
 Klicken Sie auf diese Schaltfläche, um einen Klassenverweis hinzuzufügen. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten (...), um das Dialogfeld **Öffnen** aufzurufen und die für die Berichtsverarbeitung und Ausdrucksauswertung erforderlichen Klassen auszuwählen.  
  
 **Delete**  
 Um die Klasseninstanz zu löschen, wählen Sie sie aus, und klicken Sie auf die Schaltfläche **Entfernen** .  
  
 **Nach oben**  
 Für Klassen mit Abhängigkeiten können Sie diesen Verweis in der Liste nach oben verschieben.  
  
 **Nach unten**  
 Für Klassen mit Abhängigkeiten können Sie diesen Verweis in der Liste nach unten verschieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerdefinierter Code und Assemblyverweise in Ausdrücken in Berichts-Designer (SSRS)](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)   
 [Verweise auf Berichts- und Gruppenvariablensammlungen &#40;Berichts-Generator und SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
