---
title: 'Sqlrutils - Hilfsfunktionen: SQL Server Machine Learning Services'
description: Verwenden Sie die Sqlrutils-Funktionsbibliothek in SQL Server 2016 R Services und SQL Server 2017-Machine Learning Services mit R, um gespeicherte Prozeduren mit R-Skript zu generieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7ccc3ad494658fc7a8f9c67472aecb1c4cddb7da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641754"
---
# <a name="sqlrutils-r-library-in-sql-server"></a>Sqlrutils (R-Bibliothek in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Das **sqlrutils** -Paket bietet einen Mechanismus, mit dem R-Benutzer ihre R-Skripts in eine gespeicherte T-SQL-Prozedur einbinden, diese gespeicherte Prozedur für eine Datenbank registrieren und die gespeicherte Prozedur aus einer R-Entwicklungsumgebung ausführen können. 

Durch Konvertieren Ihres R-Codes, sodass er in einer einzelnen gespeicherten Prozedur ausgeführt wird, können Sie SQL Server R Services effektiver nutzen, wozu es erforderlich ist, dass das R-Skript als Parameter für [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)eingebettet wird. Das **sqlrutils** -Paket unterstützt Sie dabei, dieses eingebettete R-Skript zu erstellen und zugehörige Parameter entsprechend festzulegen.

Das **sqlrutils** -Paket führt die folgenden Aufgaben aus:

- Es speichert das generierte T-SQL-Skript als Zeichenfolge in einer R-Datenstruktur.
- Es generiert optional eine SQL-Datei für das T-SQL-Skript, die Sie bearbeiten oder ausführen können, um eine gespeicherte Prozedur zu erstellen.
- Es registriert die neu erstellte gespeicherte Prozedur für die SQL Server-Instanz aus Ihrer R-Entwicklungsumgebung.

Sie können die gespeicherte Prozedur auch aus einer R-Umgebung ausführen, indem Sie wohlgeformte Parameter übergeben und die Ergebnisse verarbeiten. Oder Sie können die gespeicherte Prozedur aus SQL Server verwenden, um allgemeine Datenbankintegrationsszenarios wie ETL, Modelltraining und Massenbewertung zu unterstützen.

  > [!NOTE]
  > Wenn Sie beabsichtigen, die gespeicherte Prozedur aus einer R-Umgebung auszuführen, indem Sie die *executeStoredProcedure* -Funktion aufrufen, müssen Sie einen ODBC 3.8-Anbieter verwenden, z.B. ODBC Driver 13 for SQL Server.  
  
## <a name="full-reference-documentation"></a>Vollständige Referenz-Dokumentation

Die **Sqlrutils** Bibliothek wird in mehreren Microsoft-Produkte verteilt, aber wird, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt erhalten. Da die Funktionen identisch sind, [Dokumentation für einzelne Sqlrutils-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) in nur einem Ort unter veröffentlicht wird die [R Verweis](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) für Microsoft Machine Learning Server. Sollten Sie jede Produkt-spezifische Verhalten vorhanden ist, wird Diskrepanzen auf der Hilfeseite für die Funktion angegeben.

## <a name="functions-list"></a>Funktionsliste

Der folgende Abschnitt enthält eine Übersicht über die Funktionen, die Sie aufrufen können, aus der **Sqlrutils** Paket entwickeln Sie eine gespeicherte Prozedur mit eingebetteten R-Code. Details zu den Parametern für jede Methode oder Funktion finden Sie in der R-Hilfe für das Paket: `help(package="sqlrutils")`

|Funktion | Description |
|------|-------------|
|[executeStoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/executestoredprocedure)| Ausführen einer gespeicherten SQL-Prozedur.|
|[getInputParameters](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/getinputparameters)| Ruft eine Liste der Eingabeparameter für die gespeicherte Prozedur.| 
|[InputData](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/inputdata)| Definiert die Datenquelle in SQL Server, die in dem R-Datenrahmen verwendet wird. Sie geben den Namen des Datenrahmens (data.frame), in dem die Eingabedaten gespeichert werden sollen, und eine Abfrage, mit der die Daten abgerufen werden, oder einen Standardwert an. Es werden nur einfache SELECT-Abfragen unterstützt. | 
|[InputParameter](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/inputparameter)| Definiert einen einzelnen Eingabeparameter, der in das T-SQL-Skript eingebettet wird. Sie müssen den Namen des Parameters und dessen R-Datentyp angeben.| 
|[OutputData](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/outputdata)| Generiert ein Zwischendatenobjekt, das erforderlich ist, wenn Ihre R-Funktion eine Liste zurückgibt, die einen Datenrahmen (data.frame) enthält. Das *OutputData* -Objekt wird verwendet, um den Namen eines einzelnen „data.frame“ zu speichern, das aus der Liste abgerufen wurde.| 
|[OutputParameter](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/outputparameter) | Generiert ein Zwischendatenobjekt, das erforderlich ist, wenn Ihre R-Funktion eine Liste zurückgibt. Im *OutputParameter* -Objekt werden der Name und der Datentyp eines einzelnen Elements der Liste gespeichert, wobei vorausgesetzt wird, dass das Element **kein** Datenrahmen ist. |
|[registerStoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/registerstoredprocedure) | Registrieren Sie die gespeicherte Prozedur mit einer Datenbank.|
|[setInputDataQuery](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/setinputdataquery)| Weisen Sie eine Abfrage an einen Eingabedaten-Parameter der gespeicherten Prozedur.| 
|[setInputParameterValue](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/setinputparametervalue)| Weisen Sie einen Wert für einen Eingabeparameter der gespeicherten Prozedur.| 
|[StoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/storedprocedure)| Eine gespeicherte Prozedur-Objekt.|


## <a name="how-to-use-sqlrutils"></a>Gewusst wie: Verwenden von sqlrutils

Die **Sqlrutils** Bibliotheksfunktionen müssen ausführen auf einem Computer mit SQL Server-Machine Learning mit R. Wenn Sie auf einer Clientarbeitsstation arbeiten, legen Sie einen remotecomputekontext UMSCHALT-Ausführung mit SQL Server. Der Workflow für die Verwendung dieses Pakets enthält die folgenden Schritte aus:

+ Definieren Sie die Parameter der gespeicherten Prozedur (Eingaben, Ausgaben oder beides) 
+ Generieren Sie und registrieren Sie die gespeicherte Prozedur    
+ Ausführen der gespeicherten Prozedur  

Laden Sie in einer R-Sitzung **Sqlrutils** über die Befehlszeile durch Eingabe `library(sqlrutils)`.

> [!Note]
> Sie können diese Bibliothek beim Computer laden, die nicht SQL Server (z. B. auf eine Instanz des R-Client) installiert ist, wenn Sie zu SQL Server computekontext, und führen Sie den Code in diesen computekontext.


### <a name="define-stored-procedure-parameters-and-inputs"></a>Definieren von Parametern gespeicherter Prozeduren und Eingaben

`StoredProcedure` ist der Hauptkonstruktor, der zum Erstellen der gespeicherten Prozedur verwendet wird. Dieser Konstruktor generiert eine gespeicherte Prozedur als *SQL Server-Objekt* und erstellt optional eine Textdatei, die eine Abfrage enthält, die dazu verwendet werden kann, die gespeicherte Prozedur mit einem T-SQL-Befehl zu generieren. 

Außerdem kann die *StoredProcedure* -Funktion dazu verwendet werden, die gespeicherte Prozedur für die angegebene Instanz und Datenbank zu registrieren.

+ Verwenden Sie das `func` Argument, um eine gültige R-Funktion anzugeben. Alle Variablen, die in der Funktion verwendet werden, müssen entweder innerhalb der Funktion definiert sein oder als Eingabeparameter bereitgestellt werden. Diese Parameter können maximal einen Datenrahmen enthalten.

+ Die R-Funktion muss entweder einen Datenrahmen, eine benannte Liste oder NULL zurückgeben. Gibt die Funktion eine Liste zurück, darf die Liste maximal einen Datenrahmen (data.frame) enthalten.

+ Verwenden Sie das Argument `spName` , um den Namen der zu erstellenden gespeicherten Prozedur anzugeben.

+ Sie können optionale Eingabe- und Ausgabeparameter mithilfe der Objekte übergeben, die mit diesen Hilfsfunktionen erstellt wurden: `setInputData`, `setInputParameter`und `setOutputParameter`.

+  Verwenden Sie optional `filePath` , um den Pfad und den Namen der zu erstellenden SQL-Datei bereitzustellen. Sie können diese Datei für die SQL Server-Instanz ausführen, um die gespeicherte Prozedur mit T-SQL zu generieren.

+ Um den Server und die Datenbank festzulegen, in der die gespeicherte Prozedur gespeichert werden soll, verwenden Sie die Argumente `dbName` und  `connectionString`.

+ Wenn Sie eine Liste des *InputData* - und des *InputParameter* -Objekts abrufen möchten, die zum Erstellen eines bestimmten *StoredProcedure* -Objekts verwendet wurden, rufen Sie `getInputParameters`auf. 

+ Um die gespeicherte Prozedur für die angegebene Datenbank zu registrieren, verwenden Sie `registerStoredProcedure`.

Dem Objekt für die gespeicherte Prozedur sind üblicherweise weder Daten noch Werte zugeordnet, es sei denn, es wurde ein Standardwert angegeben. Daten werden erst abgerufen, wenn die gespeicherte Prozedur ausgeführt wird. 

### <a name="specify-inputs-and-execute"></a>Angeben von Eingaben und ausführen

+ Verwenden Sie `setInputDataQuery` , um einem *InputParameter* -Objekt eine Abfrage zuzuweisen. Wenn Sie beispielsweise ein Objekt für die gespeicherte Prozedur in R erstellt haben, können Sie `setInputDataQuery` verwenden, um Argumente an die *StoredProcedure* -Funktion zu übergeben, damit die gespeicherte Prozedur mit den gewünschten Eingaben ausgeführt wird.

+ Verwenden Sie `setInputValue` , wenn Sie einem Parameter, der als ein *InputParameter* -Objekt gespeichert ist, bestimmte Werte zuweisen möchten. Sie können dann das Parameterobjekt und dessen Wertzuweisung an die *StoredProcedure* -Funktion übergeben, um die gespeicherte Prozedur mit den festgelegten Werten auszuführen.

+ Verwenden Sie `executeStoredProcedure` , wenn Sie eine gespeicherte Prozedur ausführen möchten, die als ein *StoredProcedure* -Objekt definiert ist. Rufen Sie diese Funktion nur auf, wenn Sie eine gespeicherte Prozedur aus R-Code ausführen. Verwenden Sie diese Funktion nicht, wenn Sie die gespeicherte Prozedur aus SQL Server mithilfe von T-SQL ausführen.

> [!NOTE]
> Die *executeStoredProcedure* -Funktion erfordert einen ODBC 3.8-Anbieter, z.B. ODBC Driver 13 for SQL Server.  

## <a name="see-also"></a>Siehe auch

[Gewusst wie: Erstellen einer gespeicherten Prozedur mithilfe von sqlrutils](how-to-create-a-stored-procedure-using-sqlrutils.md)

