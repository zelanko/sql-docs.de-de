---
title: Dataseteigenschaften (Dialogfeld), Abfrage (Berichts-Generator) | Microsoft-Dokumentation
ms.date: 08/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: reference
f1_keywords:
- "10024"
- sql13.rtp.rptdesigner.datasetproperties.query.f1
- "10160"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e05ae59d963bd9b165d2f6f825955ee276683328
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "66500451"
---
# <a name="dataset-properties-dialog-box-query-report-builder"></a>Dataseteigenschaften (Dialogfeld), Abfrage (Berichts-Generator)
 
Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Abfrage** aus, um ein freigegebenes Dataset von einem Berichtsserver auszuwählen oder ein eingebettetes Dataset zu erstellen. Für ein eingebettetes Dataset müssen Sie eine Datenquelle auswählen und eine Abfrage erstellen.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie einen Namen für das Dataset ein. Der Name darf nicht mit dem Namen eines Datenbereichs oder einer Gruppe im Bericht identisch sein.  
  
 **Verwenden Sie ein freigegebenes Dataset.**  
 Wählen Sie diese Option, um ein vordefiniertes Dataset vom Berichtsserver zu verwenden.  
  
 **Durchsuchen**  
 Wechseln zu einem Ordner auf einen Berichtsserver oder einer SharePoint-Site und Auswählen eines freigegebenen Datasets (.rsd).  
  
 **Verwenden Sie ein in den eigenen Bericht eingebettetes Dataset.**  
 Wählen Sie diese Option, um ein Dataset ausschließlich zur Verwendung in diesem Bericht zu erstellen.  
  
 **Data Source**  
 Wählen Sie eine Datenquelle als Basis für das Dataset aus. Klicken Sie auf **Neu**, um eine neue Datenquelle zu erstellen.  
  
 **Abfragetyp**  
 Wählen Sie den Typ von Befehl oder Abfrage aus, der für das Dataset verwendet werden soll. Wählen Sie **Text** aus, um eine Abfrage auszuführen und Daten von der Datenbank abzurufen. Wählen Sie **Tabelle** aus, um mit der **TableDirect** -Funktion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle Felder innerhalb einer Tabelle auszuwählen. Wählen Sie **Gespeicherte Prozedur** aus, um eine gespeicherte Prozedur nach Namen auszuführen. Standardmäßig ist**Text** ausgewählt. Diese Einstellung wird für einen Großteil der Abfragen verwendet. Um die ausgewählte Datenquellenabfrage zu bearbeiten, klicken Sie auf **Abfrage-Designer**.  
  
> [!NOTE]  
>  Nicht alle Abfragetypen werden von allen Datenquellen unterstützt. Zum Beispiel wird **Tabelle** nur von den Datenquellentypen **OLE DB** und **ODBC**unterstützt.  
  
 **Abfrage**  
 Diese Option wird angezeigt, wenn Sie die Befehlstypoption **Text** auswählen. Geben Sie eine Abfrage ein, oder importieren Sie eine bereits vorhandene Abfrage, indem Sie auf **Importieren**klicken. Klicken Sie auf die **Ausdrucksschaltfläche** (*fx*), um den Ausdruck zu bearbeiten.  
  
> [!NOTE]  
>  Wenn Sie die Abfrage mit einem Abfrage-Designer erstellen, wird der Text der Abfrage in diesem Feld angezeigt.  
  
**Tabellenname**  
Diese Option wird angezeigt, wenn Sie **Tabelle**auswählen. Geben Sie den Namen der Tabelle ein, die Sie als Dataset verwenden möchten.   
  
**Auswählen oder Eingeben des Namens einer gespeicherten Prozedur**  
Diese Option wird angezeigt, wenn Sie die Befehlstypoption Gespeicherte Prozedur auswählen. Geben Sie den Namen der zu verwendenden gespeicherten Prozedur ein, oder wählen Sie ihn aus. Klicken Sie auf die **Ausdrucksschaltfläche** (*fx*), um den Ausdruck zu bearbeiten.   
  
 **Timeout (in Sekunden)**  
 Geben Sie die Anzahl an Sekunden als Timeoutwert für die Abfrage ein. Der Standardwert ist 30 Sekunden. Der angegebene Wert für **Timeout** muss leer oder größer als null sein. Wird das Feld leer gelassen, gibt es für die Abfrage kein Timeout.  
  
 **Felder aktualisieren**  
 Führen Sie diesen Abfragebefehl aus, um die Liste der Felder auf der Seite **Dataseteigenschaften (Dialogfeld), Felder** zu aktualisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
[Berichtsdatasets &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
[Abfrageentwurfstools &#40;SSRS&#41;](query-design-tools-ssrs.md)  
  
  
