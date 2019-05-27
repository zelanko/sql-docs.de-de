---
title: Ändern von Tabellen-, Spalten- oder zeilenfilterzuordnungen (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2124c526-5772-4f84-a019-9dd3e906e8dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dfee215fef54f942bc7b47cff684cc35c509075c
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66067638"
---
# <a name="change-table-column-or-row-filter-mappings-ssas-tabular"></a>Ändern von Tabellen-, Spalten- oder Zeilenfilterzuordnungen (SSAS – tabellarisch)
  In diesem Thema wird beschrieben, wie Tabellen-, Spalten- oder Zeilenfilterzuordnungen im Dialogfeld **Tabelleneigenschaften bearbeiten** in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]geändert werden.  
  
 Die Optionen im Dialogfeld **Tabelleneigenschaften bearbeiten** variieren, je nachdem, ob Daten ursprünglich durch Auswahl von Tabellen aus einer Liste oder mithilfe einer SQL-Abfrage importiert wurden. Wenn die Daten ursprünglich durch Auswahl aus einer Liste importiert wurden, wird das Dialogfeld **Tabelleneigenschaften bearbeiten** im Tabellenvorschaumodus angezeigt. In diesem Modus wird nur eine Teilmenge angezeigt, die auf die ersten 50 Zeilen der Quelltabelle beschränkt ist. Wenn die Daten ursprünglich durch Verwendung einer SQL-Anweisung importiert wurden, wird im Dialogfeld **Tabelleneigenschaften bearbeiten** nur eine SQL-Anweisung angezeigt. Mithilfe einer SQL-Abfrageanweisung können Sie eine Teilmenge der Zeilen abrufen, indem Sie entweder einen Filter entwerfen oder die SQL-Anweisung manuell bearbeiten.  
  
 Wenn Sie die Quelle in eine Tabelle ändern, die andere Spalten als die aktuelle Tabelle enthält, wird eine entsprechende Warnmeldung angezeigt. Sie müssen dann die Spalten auswählen, die Sie in die aktuelle Tabelle einfügen möchten, und auf **Speichern**klicken. Sie können die gesamte Tabelle ersetzen, indem Sie das Kontrollkästchen links von der Tabelle aktivieren.  
  
> [!NOTE]  
>  Wenn die Tabelle über mehrere Partitionen verfügt, können Sie die Zeilenfilterzuordnungen nicht im Dialogfeld Tabelleneigenschaften bearbeiten ändern. Verwenden Sie zum Ändern der Zeilenfilterzuordnungen für Tabellen mit mehreren Partitionen den Partitions-Manager. Weitere Informationen finden Sie unter [Partitionen &#40;SSAS – tabellarisch&#41;](partitions-ssas-tabular.md).  
  
#### <a name="to-change-table-column-or-row-filter-mappings"></a>So ändern Sie Tabellen-, Spalten- oder Zeilenfilterzuordnungen  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle und dann auf das Menü **Tabelle** und auf **Tabelleneigenschaften**.  
  
2.  Suchen Sie im Dialogfeld **Tabelleneigenschaften bearbeiten** nach der Spalte, die die Filterkriterien enthält, und klicken Sie dann rechts von der Spaltenüberschrift auf den Pfeil nach unten.  
  
3.  Führen Sie im Menü **AutoFilter** einen der folgenden Schritte aus:  
  
    -   Wählen Sie in der Liste der Spaltenwerte mindestens einen Wert aus, nach dem gefiltert werden soll, bzw. heben Sie die Auswahl auf, und klicken Sie auf OK.  
  
         Wenn die Anzahl der Werte sehr groß ist, kann es sein, dass einzelne Elemente nicht in der Liste angezeigt werden. Stattdessen wird eine Meldung angezeigt, dass zu viele Elemente zum Anzeigen vorhanden sind.  
  
    -   Klicken Sie je nach Typ der Spalte auf **Zahlenfilter** oder **Textfilter** , und klicken Sie anschließend auf einen der Vergleichsoperatorbefehle (wie „Ist gleich“), oder klicken Sie auf „Benutzerdefinierter Filter“. Erstellen Sie im Dialogfeld **Benutzerdefinierter Filter** den Filter, und klicken Sie dann auf **OK**.  
  
         Falls Sie erneut beginnen möchten, klicken Sie auf **Zeilenfilter löschen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabelleneigenschaften bearbeiten (Dialogfeld) &#40;SSAS&#41;](../edit-table-properties-dialog-box-ssas.md)  
  
  
