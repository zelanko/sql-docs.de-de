---
title: Airline-Ankunfts- und Verzögerung-demo-DataSet für SQL Server Python und R-Tutorials | Microsoft-Dokumentation
Description: Create a database containing the Airline dataset from R and Python. This dataset is used in exercises showing how to wrap R language or Python code in a SQL Server stored procedure.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/22/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2ba431ecbc4f7d63415fdf6b351c5135ed0cdd8d
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947437"
---
#  <a name="airline-flight-arrival-demo-data-for-sql-server-python-and-r-tutorials"></a>Fluggesellschaft Eingang Demo Flugdaten für SQL Server Python und R-tutorials
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Erstellen Sie in dieser Übung eine SQL Server-Datenbank zum Speichern von importierter Daten aus R oder Python integrierte Airline Demo Datasets. R und Python-Distributionen bieten die entsprechende Daten, die in einer SQL Server-Datenbank mithilfe von Management Studio importiert werden kann.

Um in dieser Übung abgeschlossen haben, müssen Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) oder ein anderes Tool, das T-SQL-Abfragen ausgeführt werden kann.

Lernprogramme und dieses DataSet mit Schnellstarts umfassen Folgendes:

+  [Erstellen eines Python-Modells mithilfe von revoscalepy](use-python-revoscalepy-to-create-model.md)

## <a name="create-the-database"></a>Erstellen der Datenbank

1. SQL Server Management Studio starten, Verbinden mit einer Datenbank-Engine-Instanz, die Integration von R oder Python.  

2. Klicken Sie im Objekt-Explorer mit der Maustaste **Datenbanken** , und erstellen Sie eine neue Datenbank namens **Flightdata**.

3. Mit der rechten Maustaste **Flightdata**, klicken Sie auf **Aufgaben**, klicken Sie auf **Importieren von Flatfiles**.

4. Öffnen Sie die AirlineDemoData.csv-Datei, die bereitgestellt werden, in der R oder Python-Distribution, je nachdem, welche Sprache Sie installiert.

   Für R, suchen Sie nach **AirlineDemoSmall.csv** unter C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library\RevoScaleR\SampleData
   
   Für Python, suchen Sie nach **AirlineDemoSmall.csv** unter C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\revoscalepy\data\sample_data
  
Wenn Sie die Datei auswählen, werden die Standardwerte für Namen und das Schema ausgefüllt.

  ![Importieren von Flatfile-Assistent zeigt Airline Demo Standardwerte](media/import-airlinedemosmall.png)

Klicken Sie auf den verbleibenden Seiten, um die Standardwerte zu übernehmen, zum Importieren der Daten.


## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie als Schritt zur Überprüfung eine Abfrage aus, um sicherzustellen, dass die Daten hochgeladen wurden.

1. Im Objekt-Explorer unter "Datenbanken", mit der Maustaste der **Flightdata** Datenbank, und starten Sie eine neue Abfrage.

2. Führen Sie einige einfachen Abfragen:

    ```sql
    SELECT TOP(10) * FROM AirlineDemoSmall;
    SELECT COUNT(*) FROM AirlineDemoSmall;
    ```

## <a name="next-steps"></a>Nächste Schritte

In der folgenden Lektion erstellen Sie ein lineares Regressionsmodell, das auf der Grundlage dieser Daten.

+ [Erstellen eines Python-Modells mithilfe von revoscalepy](use-python-revoscalepy-to-create-model.md)
