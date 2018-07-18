---
title: Importieren von Daten mit einer nativen Abfrage (Analysis Services) | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1716b3b6e5794d8dbb8d9ee0195ed642db6df054
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37981102"
---
# <a name="import-data-by-using-a-native-query"></a>Importieren von Daten mit einer nativen Abfrage
[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]
Für tabellarische Modelle mit Kompatibilitätsgrad 1400 ermöglicht die neue Daten abrufen-Benutzeroberfläche in Visual Studio Analysis Services-Projekten immense Flexibilität beim wie Sie kombinieren können Ihre Daten während des Imports. Dieser Artikel beschreibt das Herstellen einer Verbindung mit einer Datenquelle und zum Erstellen von nativen SQL-Abfrage zum Importieren von Daten angeben.

Um die in diesem Artikel beschriebenen Aufgaben ausführen zu können, stellen Sie sicher, dass Sie die neueste Version von SSDT nutzen. Wenn Sie Visual Studio 2017 verwenden, stellen Sie sicher, dass Sie heruntergeladen und installiert im September 2017 haben oder höher Microsoft Analysis Services-Projekten VSIX.

[Herunterladen und installieren](../../ssdt/download-sql-server-data-tools-ssdt.md)

[Herunterladen von Microsoft Analysis Services-Projekten VSIX](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)

## <a name="create-a-datasource-connection"></a>Erstellen Sie eine Datasource-Verbindung
Wenn Sie noch keine Verbindung mit Ihrer Datenquelle haben, müssen Sie eine erstellen.

1. In Visual Studio > **tabellarischer Modell-Explorer**, mit der rechten Maustaste **Datenquellen**, und klicken Sie dann auf **neue Datenquelle**.
2. In **Datenabruf**, wählen Sie den Datenquellentyp, und klicken Sie dann auf **Connect**. Führen Sie zusätzliche Schritte erforderlich, um eine Verbindung mit Ihrer Datenquelle herstellen.


## <a name="enter-a-query-as-a-named-expression"></a>Geben Sie eine Abfrage als ein benannter Ausdruck
1. In **tabellarischer Modell-Explorer**, mit der rechten Maustaste **Ausdrücke** > **Ausdrücke bearbeiten**.
2. In **Abfrage-Editor**, klicken Sie auf **Abfrage** > **neue Abfrage** > **leere Abfrage**
3. Geben Sie in der Bearbeitungsleiste
    ```
    = Value.NativeQuery(#"DATA SOURCE NAME", "SELECT * FROM …")
    ```
4. Zum Erstellen einer Tabelle in **Abfragen**mit der rechten Maustaste auf die Abfrage, und wählen Sie dann **neue Tabelle erstellen**. Die neue Tabelle müssen den gleichen Namen wie die Abfrage.


## <a name="example"></a>Beispiel
Diese native Abfrage erstellt eine Tabelle im Modell, das alle Spalten aus der Dimension.Employee-Tabelle in der Datenquelle enthält.

```
= Value.NativeQuery(#"SQL/myserver;WideWorldImportersDW", "SELECT * FROM Dimension.Employee")
```
![Abfrage-Editor](media/ssas-import-query-example.png)


Nach dem Importieren wird eine Tabelle namens "Employees" in das Modell erstellt.   

![Abfrage-Editor](media/ssas-import-query-example-table.png)


## <a name="see-also"></a>Siehe auch  
 [Value.NativeQuery](https://msdn.microsoft.com/library/mt736917.aspx)   
 [Identitätswechsel](../../analysis-services/tabular-models/impersonation-ssas-tabular.md)   

  
