---
title: Konfigurieren eines Standardfeldsatzes für Power View-Berichte (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- ql12.asvs.bidtoolset.deffieldset.f1
ms.assetid: 6836b42f-28b8-4a98-a86d-2c3c109f0189
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 37571e141395afe255329edc10edeaeaed121710
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66066892"
---
# <a name="configure-default-field-set-for-power-view-reports-ssas-tabular"></a>Konfigurieren eines Standardfeldsatzes für Power View-Berichte (SSAS – tabellarisch)
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
 Nach dem Erstellen eines Standardfeldsatzes können Sie die Benutzerfreundlichkeit des Berichtsentwurfs weiter beeinflussen, indem Sie Standardbezeichnungen, Standardbilder, Standardgruppenverhalten oder die Anordnung von Zeilen mit gleichem Wert gruppiert in einer Zeile oder einzeln angeben. Weitere Informationen finden Sie unter [Konfigurieren von Tabellenverhaltenseigenschaften für Power View-Berichte &#40;SSAS – tabellarisch&#41;](power-view-configure-table-behavior-properties-for-reports.md).  
  
  
