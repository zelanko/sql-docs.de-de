---
title: Schnellstart für das Arbeiten mit Eingaben und Ausgaben in R (SQL Server-Machine Learning) | Microsoft-Dokumentation
description: Erfahren Sie in dieser schnellstartanleitung für R-Skript in SQL Server, wie Sie ein- und Ausgaben für die gespeicherte Systemprozedur Sp_execute_external_script strukturieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b41a8c30cd0ecbe040819478c0cadece1b9eb704
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086582"
---
# <a name="quickstart-handle-inputs-and-outputs-using-r-in-sql-server"></a>Schnellstart: Behandeln Sie, Eingaben und Ausgaben, die mithilfe von R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Wenn Sie R-Code in SQL Server ausführen möchten, müssen Sie R-Skript in einer gespeicherten Prozedur umschließen. Sie können eine schreiben oder R-Skript übergeben [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Dieses System gespeicherte Prozedur wird verwendet, um die R-Laufzeit im Kontext von SQL Server zu starten, der Daten an R übergeben wird, verwaltet Sitzungen von Benutzern, sicher, und gibt die Ergebnisse an den Client zurück.

## <a name="prerequisites"></a>Erforderliche Komponenten

Einen vorherigen schnellstartanleitung [Hello World in R und SQL](rtsql-using-r-code-in-transact-sql-quickstart.md), enthält Informationen und links für das Einrichten der R-Umgebung, die im Rahmen dieser schnellstartanleitung benötigt.

<a name="bkmk_SSMSBasics"></a>

## <a name="create-some-simple-test-data"></a>Erstellen einiger einfacher Testdaten

Erstellen Sie eine kleine Tabelle mit Testdaten, indem Sie die folgende T-SQL-Anweisung ausführen:

```sql
CREATE TABLE RTestData ([col1] int not null) ON [PRIMARY]
INSERT INTO RTestData   VALUES (1);
INSERT INTO RTestData   VALUES (10);
INSERT INTO RTestData   VALUES (100) ;
GO
```

Wenn die Tabelle erstellt wurde, verwenden Sie die folgende Anweisung zum Abfragen der Tabelle:
  
```sql
SELECT * FROM RTestData
```

**Ergebnisse**

![Inhalt der RTestData-Tabelle](media/quickstart-r-working-input-outputs-results-1.png)


## <a name="get-the-same-data-using-r-script"></a>Abrufen der gleiche Daten mithilfe eines R-Skripts

Führen Sie die folgende Anweisung aus, nachdem die Tabelle erstellt wurde:

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N' OutputDataSet <- InputDataSet;'
    , @input_data_1 = N' SELECT *  FROM RTestData;'
    WITH RESULT SETS (([NewColName] int NOT NULL));
```

Ruft die Daten aus der Tabelle ab, gibt die Werte mit dem Spaltennamen zurück und macht einen Roundtrip über die R-Laufzeit *NewColName*.

**Ergebnisse**

![rsql_basictut_getsamedataR](media/rsql-basictut-getsamedatar.PNG)


**Kommentare**

+ Der Parameter *@language* definiert die aufzurufende Spracherweiterung, die in diesem Fall R ist.
+ Im Parameter *@script* definieren Sie die Befehle, die an die R-Laufzeit übergeben werden. Ihr gesamtes R-Skript muss von diesem Argument als Unicode-Text umschlossen sein. Sie können den Text auch einer Variablen des Typs **nvarchar** hinzufügen und die Variable anschließend aufrufen.
+ Die von der Abfrage zurückgegebenen Daten werden an die R-Laufzeit übergeben, die die Daten als Datenrahmen an SQL Server zurückgibt.
+ Die Klausel WITH RESULT SETS definiert das Schema der zurückgegeben Datentabelle für SQL Server.

## <a name="change-input-or-output-variables"></a>Ändern der Eingabe- bzw. Ausgabevariablen

Im vorherigen Beispiel wurden die Standardausgabe- und Eingabevariablennamen _InputDataSet_ und _OutputDataSet_ verwendet. Verwenden Sie die Variable *@input_data_1*, um die mit _InputDatSet_ verknüpften Eingabedaten zu definieren.

In diesem Beispiel wurden die Namen der Ausgabe- und der Eingabevariablen für die gespeicherten Prozeduren in *SQL_Out* bzw. *SQL_In* geändert:

```sql
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N' SQL_out <- SQL_in;'
  , @input_data_1 = N' SELECT 12 as Col;'
  , @input_data_1_name  = N'SQL_In'
  , @output_data_1_name =  N'SQL_Out'
  WITH RESULT SETS (([NewColName] int NOT NULL));
```

Haben Sie erhalten den Fehler "Objekt SQL\_in wurde nicht gefunden"? Das liegt daran, dass R Groß- und Kleinschreibung beachtet. Im Beispiel verwendet das R-Skript die Variablen *SQL_in* und *SQL_out*, aber die Parameter der gespeicherten Prozedur verwenden die Variablen *SQL_In* und *SQL_Out*.

Versuchen Sie es beheben **nur** der *SQL_In* Variable *@script* und führen Sie die gespeicherte Prozedur erneut aus.

Nutzen Sie jetzt eine **verschiedene** Fehler:

```Error
EXECUTE statement failed because its WITH RESULT SETS clause specified 1 result set(s), but the statement only sent 0 result set(s) at run time.
```

Wir haben Sie diesen Fehler angezeigt, da Sie davon ausgehen können, um ihn anzuzeigen, häufig, wenn Sie neuen R-Code zu testen. Es bedeutet, dass das R-Skript erfolgreich ausgeführt wurde, aber SQL Server hat keine Daten empfangen oder falsche oder unerwartete Daten empfangen.

In diesem Fall gibt das Ausgabeschema (die Zeile, in der **WITH** am Anfang steht) an, dass eine Spalte ganzzahliger Daten zurückgegeben werden sollte, aber da die Daten von R in eine andere Variable eingefügt wurden, konnten keine Daten an SQL Server zurückgegeben werden; daher tritt ein Fehler auf. um den Fehler zu beheben, korrigieren Sie den zweiten Variablennamen ein.

**Beachten Sie diese Anforderungen.**

- Variablennamen müssen den Regeln für zulässige SQL-Bezeichner entsprechen.
- Die Reihenfolge der Parameter ist wichtig. Sie müssen die erforderlichen Parameter *@input_data_1* und *@output_data_1* zuerst angeben, bevor Sie die optionalen Parameter *@input_data_1_name* und *@output_data_1_name* verwenden können.
- Nur eine Eingabedataset kann als Parameter übergeben werden, und Sie können nur ein Dataset zurückgeben. Allerdings können Sie andere Datasets innerhalb Ihres R-Codes aufrufen und Ausgaben und andere Typen zusätzlich zum Dataset zurückgeben. Sie können auch das Schlüsselwort OUTPUT zu einem beliebigen Parameter hinzufügen, damit es mit den Ergebnissen zurückgegeben wird. Später in diesem Tutorial finden Sie ein einfaches Beispiel.
- Die `WITH RESULT SETS`-Anweisung definiert das Schema für die Daten zu Gunsten von SQL Server. Sie müssen Daten, die mit SQL kompatibel sind, für die von R zurückgegebenen Spalten zur Verfügung stellen. Sie können die Schemadefinition auch zur Umbenennung von Spalten verwenden; Sie müssen nicht die Spaltennamen aus dem R-Datenrahmen verwenden. In einigen Fällen ist diese Klausel optional. Sie können Sie weglassen, und sehen Sie, was passiert.

## <a name="generate-results-using-r"></a>Generieren der Ergebnisse mithilfe von R

Sie können Werte auch nur mit dem R-Skript generieren und die Zeichenfolge der Eingabeabfrage in _@input_data_1_ leer lassen. Alternativ können Sie eine gültige SQL SELECT-Anweisung als Platzhalter und die SQL-Ergebnisse nicht in einem R-Skript verwenden.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
   , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
   , @input_data_1 = N' SELECT 1 as Temp1'
   WITH RESULT SETS (([Col1] char(20) NOT NULL));
```

**Ergebnisse**

![Ergebnisse der Abfrage mit @script als Eingabe](media/quickstart-r-working-input-outputs-results-3.png)

## <a name="next-steps"></a>Nächste Schritte

Überprüfen Sie einige der Probleme, die auftreten können, wenn das Übergeben von Daten zwischen R und SQL Server, z. B. implizite Konvertierungen und Unterschiede bei tabellarischen Daten zwischen R und SQL.

> [!div class="nextstepaction"]
> [Schnellstart: Behandeln von Datentypen und Objekte](../tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)