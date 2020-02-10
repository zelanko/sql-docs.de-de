---
title: Dataseteigenschaften (Dialog Feld), Abfrage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10160"
- sql12.rtp.rptdesigner.datasetproperties.query.f1
ms.assetid: 1fa34a4b-7de0-4e92-99fa-bc28a206773f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aead5d8e5c85b67333f10bee4e73e2bb1a8633ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109365"
---
# <a name="dataset-properties-dialog-box-query"></a>Dataseteigenschaften (Dialogfeld), Abfrage
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Abfrage** aus, um eine Datenquelle auszuwählen und eine Abfrage zu erstellen.  
  
 Im Dialogfeld **Dataseteigenschaften** ist Folgendes enthalten:  
  
-   [Dataseteigenschaften (Dialogfeld), Parameter](report-data/dataset-properties-dialog-box-parameters.md)  
  
-   [Dataseteigenschaften (Dialogfeld), Felder](../../2014/reporting-services/dataset-properties-dialog-box-fields.md)  
  
-   [Dataseteigenschaften (Dialogfeld), Optionen](../../2014/reporting-services/dataset-properties-dialog-box-options.md)  
  
-   [Dataseteigenschaften (Dialogfeld), Filter](report-data/dataset-properties-dialog-box-filters.md)  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie einen Namen für das Dataset ein. Der Name darf nicht mit dem Namen eines Datenbereichs oder einer Gruppe im Bericht identisch sein.  
  
 **Data Source**  
 Wählen Sie eine Datenquelle als Basis für das Dataset aus. Klicken Sie auf **Neu**, um eine neue Datenquelle zu erstellen.  
  
 **Abfragetyp**  
 Wählen Sie den Typ von Befehl oder Abfrage aus, der für das Dataset verwendet werden soll. Wählen Sie **Text** aus, um eine Abfrage auszuführen und Daten von der Datenbank abzurufen. Wählen Sie **Tabelle** aus, um mit der **TableDirect** -Funktion von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] alle Felder innerhalb einer Tabelle auszuwählen. Wählen Sie **Gespeicherte Prozedur** aus, um eine gespeicherte Prozedur nach Namen auszuführen. Standardmäßig ist **Text** ausgewählt, der für die meisten Abfragen verwendet wird. Um die ausgewählte Datenquellenabfrage zu bearbeiten, klicken Sie auf **Abfrage-Designer**.  
  
> [!NOTE]  
>  Nicht alle Abfragetypen werden von allen Datenquellen unterstützt. Zum Beispiel wird **Tabelle** nur von den Datenquellentypen **OLE DB** und **ODBC**unterstützt.  
  
 **Abfrage**  
 Diese Option wird angezeigt, wenn Sie die Befehlstypoption **Text** auswählen. Geben Sie eine Abfrage ein, oder importieren Sie eine bereits vorhandene Abfrage, indem Sie auf **Importieren**klicken. Klicken Sie auf die **Ausdrucks** Schaltfläche (*FX*), um den Ausdruck zu bearbeiten.  
  
> [!NOTE]  
>  Wenn Sie die Abfrage mit einem Abfrage-Designer erstellt haben, wird der Text der Abfrage in diesem Feld angezeigt.  
  
 **Tabellenname**  
 Geben Sie den Namen der Tabelle ein, die Sie als Dataset verwenden möchten. Diese Option wird angezeigt, wenn Sie **Tabelle**auswählen.  
  
 **Name der gespeicherten Prozedur auswählen oder eingeben**  
 Geben Sie den Namen der zu verwendenden gespeicherten Prozedur ein, oder wählen Sie ihn aus. Klicken Sie auf die **Ausdrucks** Schaltfläche (*FX*), um den Ausdruck zu bearbeiten. Diese Option wird angezeigt, wenn Sie die Befehlstypoption Gespeicherte Prozedur auswählen.  
  
 **Timeout (in Sekunden)**  
 Geben Sie die Anzahl von Sekunden bis zum Timeout der Abfrage ein. Der Standardwert ist 30 Sekunden. Der angegebene Wert für **Timeout** muss leer oder größer als null sein. Wird das Feld leer gelassen, gibt es für die Abfrage kein Timeout.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Abfrage-Designer &#40;Berichts-Generator&#41;](../../2014/reporting-services/query-designers-report-builder.md)   
 [Abfrage-Designer in Reporting Services](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
