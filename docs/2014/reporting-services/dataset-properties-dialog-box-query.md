---
title: DataSet Properties Dialog Box, Query | Microsoft-Dokumentation
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
- "10160"
- sql12.rtp.rptdesigner.datasetproperties.query.f1
ms.assetid: 1fa34a4b-7de0-4e92-99fa-bc28a206773f
caps.latest.revision: 37
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: db00bf6e36f20da59e548acef394c786a70d40fd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208560"
---
# <a name="dataset-properties-dialog-box-query"></a>Dataseteigenschaften (Dialogfeld), Abfrage
  Wählen Sie **Abfrage** auf die **Dataseteigenschaften** Dialogfeld zum Auswählen einer Datenquelle und eine Abfrage erstellen.  
  
 Im Dialogfeld **Dataseteigenschaften** ist Folgendes enthalten:  
  
-   [Dataset Properties Dialog Box, Parameters (Dataseteigenschaften (Dialogfeld), Parameter)](report-data/dataset-properties-dialog-box-parameters.md)  
  
-   [Dataseteigenschaften (Dialogfeld), Felder](../../2014/reporting-services/dataset-properties-dialog-box-fields.md)  
  
-   [Dataset Properties Dialog Box, Options (Dataseteigenschaften (Dialogfeld), Optionen)](../../2014/reporting-services/dataset-properties-dialog-box-options.md)  
  
-   [Dataset Properties Dialog Box, Filters (Dataseteigenschaften (Dialogfeld), Filter)](report-data/dataset-properties-dialog-box-filters.md)  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie einen Namen für das Dataset ein. Der Name darf nicht mit dem Namen eines Datenbereichs oder einer Gruppe im Bericht identisch sein.  
  
 **Data Source**  
 Wählen Sie eine Datenquelle als Basis für das Dataset aus. Klicken Sie auf **Neu**, um eine neue Datenquelle zu erstellen.  
  
 **Abfragetyp**  
 Wählen Sie den Typ von Befehl oder Abfrage aus, der für das Dataset verwendet werden soll. Wählen Sie **Text** aus, um eine Abfrage auszuführen und Daten von der Datenbank abzurufen. Wählen Sie **Tabelle** aus, um mit der **TableDirect** -Funktion von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] alle Felder innerhalb einer Tabelle auszuwählen. Wählen Sie **Gespeicherte Prozedur** aus, um eine gespeicherte Prozedur nach Namen auszuführen. Standardmäßig ist**Text** ausgewählt. Diese Einstellung wird für einen Großteil der Abfragen verwendet. Um die ausgewählte Datenquellenabfrage zu bearbeiten, klicken Sie auf **Abfrage-Designer**.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Abfrage-Designer &#40;Berichts-Generator&#41;](../../2014/reporting-services/query-designers-report-builder.md)   
 [Abfrage-Designer in Reporting Services](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
