---
title: Demo Dataset für die Fluggesellschaft Flight für SQL Server python-und R-Tutorials
Description: Erstellen Sie eine Datenbank, die das Fluglinien-DataSet aus R und python enthält. Dieses DataSet wird in Übungen verwendet, die zeigen, wie R-Sprache oder python-Code in einer SQL Server gespeicherten Prozedur eingebunden wird.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/22/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b7f28dd4b3e7e6990e037dbd9afe164d8d0e4bec
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714816"
---
#  <a name="airline-flight-arrival-demo-data-for-sql-server-python-and-r-tutorials"></a>Demo Daten zu Flug Eingangs Flügen für SQL Server python-und R-Tutorials
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Erstellen Sie in dieser Übung eine SQL Server Datenbank zum Speichern importierter Daten aus R-oder python-Datensätzen, die in den Demo Datensätzen integriert sind. R-und python-Distributionen stellen äquivalente Daten bereit, die Sie mit Management Studio in eine SQL Server Datenbank importieren können.

Um diese Übung abzuschließen, sollten Sie über [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) oder ein anderes Tool verfügen, das T-SQL-Abfragen ausführen kann.

Zu den Tutorials und Schnellstarts, die dieses DataSet verwenden, gehören die folgenden:

+  [Erstellen eines python-Modells mithilfe von revoscalepy](use-python-revoscalepy-to-create-model.md)

## <a name="create-the-database"></a>Erstellen der Datenbank

1. Starten Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit einer Datenbank-Engine-Instanz her, die über R oder python  

2. Klicken Sie in Objekt-Explorer mit der rechten Maustaste auf **Datenbanken** , und erstellen Sie eine neue Datenbank namens **FlightData**.

3. Klicken Sie mit der rechten Maustaste auf **FlightData**, klicken Sie auf **Tasks**und dann auf **Flatfile importieren**.

4. Öffnen Sie die Datei "airlinedemodata. csv", die in der R-oder python-Distribution bereitgestellt wird, abhängig von der installierten Sprache.

   Informationen zu R finden Sie unter c:\Programme\Microsoft SQL server\mssql14. ( **airlinedemosmall. CSV).** MSSQLSERVER\R_SERVICES\library\RevoScaleR\SampleData
   
   Für python suchen Sie unter c:\Programme\Microsoft SQL server\mssql14. nach **airlinedemosmall. CSV.** MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\revoscalepy\data\sample_data
  
Wenn Sie die Datei auswählen, werden die Standardwerte für den Tabellennamen und das Schema ausgefüllt.

  ![Assistent zum Importieren von Flatfiles mit Standardwerten für Fluggesellschaften](media/import-airlinedemosmall.png)

Klicken Sie durch die restlichen Seiten, und akzeptieren Sie die Standardwerte, um die Daten zu importieren.


## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie als Überprüfungs Schritt eine Abfrage aus, um zu bestätigen, dass die Daten hochgeladen wurden.

1. Klicken Sie in Objekt-Explorer unter Datenbanken mit der rechten Maustaste auf die **FlightData** -Datenbank, und starten Sie eine neue Abfrage.

2. Führen Sie einige einfache Abfragen aus:

    ```sql
    SELECT TOP(10) * FROM AirlineDemoSmall;
    SELECT COUNT(*) FROM AirlineDemoSmall;
    ```

## <a name="next-steps"></a>Nächste Schritte

In der folgenden Lektion erstellen Sie ein lineares Regressionsmodell, das auf diesen Daten basiert.

+ [Erstellen eines python-Modells mithilfe von revoscalepy](use-python-revoscalepy-to-create-model.md)
