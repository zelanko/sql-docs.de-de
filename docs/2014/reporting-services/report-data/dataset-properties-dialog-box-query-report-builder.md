---
title: Dataseteigenschaften (Dialogfeld), Abfrage (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10024"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
caps.latest.revision: 11
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: e3186ee16746b956b9a615102eeac848d68d56bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048002"
---
# <a name="dataset-properties-dialog-box-query-report-builder"></a>Dataseteigenschaften (Dialogfeld), Abfrage (Berichts-Generator)
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Abfrage** aus, um ein freigegebenes Dataset von einem Berichtsserver auszuwählen oder ein eingebettetes Dataset zu erstellen. Für ein eingebettetes Dataset müssen Sie eine Datenquelle auswählen und eine Abfrage erstellen.  
  
 Im Dialogfeld **Dataseteigenschaften** ist Folgendes enthalten:  
  
-   [Dataseteigenschaften (Dialogfeld), Parameter &#40;Berichts-Generator&#41;](../dataset-properties-dialog-box-parameters-report-builder.md)  
  
-   [Dataseteigenschaften (Dialogfeld), Felder &#40;Berichts-Generator&#41;](../dataset-properties-dialog-box-fields-report-builder.md)  
  
-   [Dataseteigenschaften (Dialogfeld), Optionen &#40;Berichts-Generator&#41;](dataset-properties-dialog-box-options-report-builder.md)  
  
-   [Dataseteigenschaften (Dialogfeld), Filter &#40;Berichts-Generator&#41;](../dataset-properties-dialog-box-filters-report-builder.md)  
  
 Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie einen Namen für das Dataset ein. Der Name darf nicht mit dem Namen eines Datenbereichs oder einer Gruppe im Bericht identisch sein.  
  
 **Verwenden Sie ein freigegebenes Dataset.**  
 Wählen Sie diese Option, um ein vordefiniertes Dataset vom Berichtsserver zu verwenden.  
  
 **Durchsuchen**  
 Wechseln zu einem Ordner auf einen Berichtsserver oder einer SharePoint-Site und Auswählen eines freigegebenen Datasets (.rsd).  
  
 **Verwenden Sie ein in den eigenen Bericht eingebettetes Dataset.**  
 Wählen Sie diese Option, um ein Dataset ausschließlich zur Verwendung in diesem Bericht zu erstellen.  
  
 **Datenquelle**  
 Wählen Sie eine Datenquelle als Basis für das Dataset aus. Klicken Sie auf **Neu**, um eine neue Datenquelle zu erstellen.  
  
 **Abfragetyp**  
 Wählen Sie den Typ von Befehl oder Abfrage aus, der für das Dataset verwendet werden soll. Wählen Sie **Text** aus, um eine Abfrage auszuführen und Daten von der Datenbank abzurufen. Wählen Sie **Tabelle** aus, um mit der **TableDirect** -Funktion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle Felder innerhalb einer Tabelle auszuwählen. Wählen Sie **Gespeicherte Prozedur** aus, um eine gespeicherte Prozedur nach Namen auszuführen. Standardmäßig ist**Text** ausgewählt. Diese Einstellung wird für einen Großteil der Abfragen verwendet. Um die ausgewählte Datenquellenabfrage zu bearbeiten, klicken Sie auf **Abfrage-Designer**.  
  
> [!NOTE]  
>  Nicht alle Abfragetypen werden von allen Datenquellen unterstützt. Zum Beispiel wird **Tabelle** nur von den Datenquellentypen **OLE DB** und **ODBC**unterstützt.  
  
 **Dataseteigenschaften**  
 Diese Option wird angezeigt, wenn Sie die Befehlstypoption **Text** auswählen. Geben Sie eine Abfrage ein, oder importieren Sie eine bereits vorhandene Abfrage, indem Sie auf **Importieren**klicken. Klicken Sie auf die **Ausdrucksschaltfläche** (*fx*), um den Ausdruck zu bearbeiten.  
  
> [!NOTE]  
>  Wenn Sie die Abfrage mit einem Abfrage-Designer erstellt haben, wird der Text der Abfrage in diesem Feld angezeigt.  
  
 **Tabellenname**  
 Geben Sie den Namen der Tabelle ein, die Sie als Dataset verwenden möchten. Diese Option wird angezeigt, wenn Sie **Tabelle**auswählen.  
  
 **Auswählen oder Eingeben des Namens einer gespeicherten Prozedur**  
 Geben Sie den Namen der zu verwendenden gespeicherten Prozedur ein, oder wählen Sie ihn aus. Klicken Sie auf die **Ausdrucksschaltfläche** (*fx*), um den Ausdruck zu bearbeiten. Diese Option wird angezeigt, wenn Sie die Befehlstypoption Gespeicherte Prozedur auswählen.  
  
 **Timeout (in Sekunden)**  
 Geben Sie die Anzahl an Sekunden als Timeoutwert für die Abfrage ein. Der Standardwert ist 30 Sekunden. Der angegebene Wert für **Timeout** muss leer oder größer als null sein. Wird das Feld leer gelassen, gibt es für die Abfrage kein Timeout.  
  
 **Felder aktualisieren**  
 Führen Sie diesen Abfragebefehl aus, um die Liste der Felder auf der Seite [Dataseteigenschaften (Dialogfeld), Felder](../dataset-properties-dialog-box-fields-report-builder.md) zu aktualisieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-datasets-ssrs.md)   
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Abfrage-Designer &#40;Berichts-Generator&#41;](../query-designers-report-builder.md)  
  
  