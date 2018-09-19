---
title: Abfragen und ändern Sie die SQL Server-Daten (SQL und R tieferer) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 57fff9b8ddfd6507876bd6eb174a127d70d0b916
ms.sourcegitcommit: aa9d2826e3c451f4699c0e69c9fcc8a2781c6213
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2018
ms.locfileid: "45975649"
---
# <a name="query-and-modify-the-sql-server-data-sql-and-r-deep-dive"></a>Fragen Sie ab und ändern Sie die SQL Server-Daten (SQL und R tieferer)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil des Tutorials zur Verwendung von Data Science Deep Dive [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Nachdem Sie die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geladen haben, können Sie die Datenquellen, die Sie als Argumente für R-Funktionen in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]erstellt haben, nun dazu verwenden, um grundlegende Informationen zu Variablen abzurufen und Übersichten und Histogramme zu generieren.

In diesem Schritt verwenden erneut Sie die Datenquellen, um einige schnelle Analysen, und klicken Sie dann die Daten zu verbessern.

## <a name="query-the-data"></a>Abfragen der Daten

Rufen Sie zunächst eine Liste der Spalten und ihrer Datentypen ab.

1.  Verwenden Sie die Funktion [RxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) , und geben Sie die Datenquelle, die Sie analysieren möchten.

    Sie können auch verwenden, abhängig von Ihrer Version von RevoScaleR, [RxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Ergebnisse**
    
    *Var 1: custID, Type: integer*
    
    *Var 2: gender, Type: integer*
    
    *Var 3: state, Type: integer*
    
    *Var 4: cardholder, Type: integer*
    
    *Var 5: balance, Type: integer*
    
    *Var 6: numTrans, Type: integer*
    
    *Var 7: numIntlTrans, Type: integer*
    
    *Var 8: creditLine, Type: integer*
    
    *Var 9: fraudRisk, Type: integer*


## <a name="modify-metadata"></a>Ändern von Metadaten

Alle Variablen werden als Integer gespeichert, aber einige Variablen darstellen, aus kategorische Daten sollten namens *faktorvariablen* in r Z. B. die Spalte *Zustand* Zahlen, die als Bezeichner verwendet werden, für die 50 US-Bundesstaaten sowie das District Of Columbia enthält.  Um das Verständnis der Daten zu erleichtern, ersetzen Sie die Zahlen durch eine Liste der Abkürzungen der US-Bundesstaaten.

In diesem Schritt erstellen einen Zeichenfolgenvektor, die die Abkürzungen enthält, und ordnen Sie dann diese kategorischen Werte den ursprünglichen integerbezeichnern. Verwenden Sie die neue Variable in der *ColInfo* Argument auf, um anzugeben, dass diese Spalte als Faktor behandelt werden. Wenn Sie die Daten analysieren, oder verschieben Sie es, die Abkürzungen verwendet werden, und die Spalte wird als Faktor behandelt.

Wenn die Spalte vor der Verwendung als Faktor zu Abkürzungen zugeordnet wird, verbessert dies auch die Leistung. Weitere Informationen finden Sie unter [R und Data-Optimierung](..\r\r-and-data-optimization-r-services.md).

1. Beginnen Sie folgendermaßen, indem Sie eine R-Variable, *stateAbb*, erstellen und den Zeichenfolgenvektor definieren, der ihr zugeordnet werden soll:
  
    ```R
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")
    ```

2. Als Nächstes erstellen Sie ein Spaltenobjekt namens *ccColInfo*, das die Zuordnung der vorhandenen Integer-Werte zu den Kategorieebenen angibt (Abkürzungen der US-Bundesstaaten).
  
    Diese Anweisung erstellt auch Faktorvariablen für „gender“ (Geschlecht) und „cardholder“ (Karteninhaber).
  
    ```R
    ccColInfo <- list(
    gender = list(
              type = "factor",
              levels = c("1", "2"),
              newLevels = c("Male", "Female")
              ),
    cardholder = list(
                  type = "factor",
                  levels = c("1", "2"),
                  newLevels = c("Principal", "Secondary")
                   ),
    state = list(
             type = "factor",
             levels = as.character(1:51),
             newLevels = stateAbb
             ),
    balance = list(type = "numeric")
    )
    ```
  
3. Um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenquelle zu erstellen, die die aktualisierten Daten verwendet, rufen Sie die Funktion **RxSqlServerData** wie zuvor auf, fügen Sie jedoch das Argument *colInfo* hinzu.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - Übergeben Sie für den *table* -Parameter die Variable *sqlFraudTable*, die die zuvor erstellte Datenquelle enthält.
    - Übergeben Sie für den *colInfo* -Parameter die Variable *ccColInfo* , die die Spaltendatentypen und Faktorebenen enthält.

4.  Sie können die **rxGetVarInfo** -Funktion nun dazu verwenden, um die Variablen in der neuen Datenquelle anzuzeigen.
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Ergebnisse**
    
    *Var 1: custID, Type: integer*
    
    *Var 2: Geschlecht 2 Faktorebenen: Männlich "female"*
    
    *Var 3: Status 51 Faktorebenen: AK AL AR-AZ-Zertifizierungsstelle... VT WA WI WV WY*
    
    *Var 4: Karteninhabern 2 Faktorebenen: Prinzipal sekundäre Datenbank*
    
    *Var 5: balance, Type: integer*
    
    *Var 6: numTrans, Type: integer*
    
    *Var 7: numIntlTrans, Type: integer*
    
    *Var 8: creditLine, Type: integer*
    
    *Var 9: fraudRisk, Type: integer*

Die drei von Ihnen angegebenen Variablen (_gender_, _state_und _cardholder_) werden nun wie Faktoren verarbeitet.

## <a name="next-step"></a>Nächster Schritt

[Definieren und Verwenden von Rechenkontexten](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)

## <a name="previous-step"></a>Vorherigen Schritt

[Erstellen von SQL Server-Datenobjekten mithilfe von RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
