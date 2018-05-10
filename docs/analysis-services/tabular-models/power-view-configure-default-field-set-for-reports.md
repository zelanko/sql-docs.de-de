---
title: Konfigurieren eines Standardfeldsatzes für Power View-Berichte | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9eaa7171430db4b133b03411f2de910692d0b9df
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2018
---
# <a name="power-view---configure-default-field-set-for-reports"></a>Power View: Konfigurieren eines Standardfeldsatzes für Berichte
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Ein Standardfeldsatz ist eine vordefinierte Liste von Spalten und Measures, die einem [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] -Berichtszeichenbereich automatisch hinzugefügt werden, wenn Sie in der Berichtsfeldliste die Tabelle auswählen. Ersteller tabellarischer Modelle können ein Standardfeld generieren, das für die Berichtsautoren, die das Modell für ihre Berichte verwenden, auf die Eliminierung redundanter Schritte abzielt. Wenn Sie beispielsweise wissen, dass die meisten Berichtsautoren, die Kundenkontaktdaten verwenden, immer einen Kontaktnamen, eine primäre Telefonnummer, eine E-Mail-Adresse und einen Unternehmensnamen benötigen, können Sie diese Spalten im Voraus auswählen, sodass sie dem Berichtszeichenbereich immer hinzugefügt werden, sobald der Autor auf die Kundenkontakttabelle klickt.  
  
> [!NOTE]  
>  Ein Standardfeldsatz gilt nur für ein tabellarisches Modell, das in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]als Datenmodell verwendet wird. Standardfeldsätze werden in Excel-Pivotberichten nicht unterstützt.  
  
## <a name="creating-a-default-field-set"></a>Erstellen eines Standardfeldsatzes  
 Sie können bestimmen, welche Felder ggf. standardmäßig eingefügt werden, wenn eine bestimmte Tabelle in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]ausgewählt wird. Sie können auch die Reihenfolge bestimmen, in der die Felder in der Liste angezeigt werden. Sie können einen Standardfeldsatz angeben, indem Sie Berichtseigenschaften im tabellarischen Modellprojekt festlegen.  
  
#### <a name="to-add-a-default-field-set"></a>So fügen Sie einen Standardfeldsatz hinzu  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]auf die Tabelle (Registerkarte), für die Sie eine Standardfeldliste konfigurieren.  
  
2.  Klicken Sie im **Eigenschaftenfenster** in der Eigenschaft **Standardfeldsatz** auf **Zum Bearbeiten klicken**.  
  
3.  Wählen Sie im Standardfeldsatz ein oder mehrere Felder aus. Sie können jedes beliebige Feld, einschließlich Measures, in der Tabelle auswählen. Halten Sie die UMSCHALTTASTE gedrückt, um mehrere aufeinander folgende Felder auszuwählen, bzw. die STRG-TASTE, um einzelne Felder auszuwählen.  
  
4.  Klicken Sie auf **Hinzufügen** , um die Felder dem Standardfeldsatz hinzuzufügen.  
  
5.  Mithilfe der NACH-OBEN-TASTE und der NACH-UNTEN-TASTE können Sie die Reihenfolge in der Feldliste festlegen. Felder werden dem Bericht in der Reihenfolge hinzugefügt, in der sie im Feldsatz definiert sind.  
  
6.  Wiederholen Sie diese Schritte für weitere Tabellen in der Arbeitsmappe.  
  
## <a name="next-step"></a>Nächster Schritt  
 Nach dem Erstellen eines Standardfeldsatzes können Sie die Benutzerfreundlichkeit des Berichtsentwurfs weiter beeinflussen, indem Sie Standardbezeichnungen, Standardbilder, Standardgruppenverhalten oder die Anordnung von Zeilen mit gleichem Wert gruppiert in einer Zeile oder einzeln angeben. Weitere Informationen finden Sie unter [Konfigurieren von Tabellenverhaltenseigenschaften für Power View-Berichte](../../analysis-services/tabular-models/power-view-configure-table-behavior-properties-for-reports.md).  
  
  
