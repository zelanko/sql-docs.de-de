---
title: 'Lektion 2: Erstellen von Datenfunktionen mithilfe von R-und T-SQL-Funktionen'
description: Tutorial zum Hinzufügen von Berechnungen zu gespeicherten Prozeduren für die Verwendung in R Machine Learning-Modellen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 7570c6769a780c5a6d98bdfc762092524bf5000c
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345929"
---
# <a name="lesson-2-create-data-features-using-r-and-t-sql"></a>Lektion 2: Erstellen von Datenfunktionen mithilfe von R und T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Tutorials für SQL-Entwickler zur Verwendung von R in SQL Server.

In diesem Schritt erfahren Sie, wie Sie Funktionen aus Rohdaten mithilfe einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktion erstellen. Sie rufen anschließend die Funktion aus einer gespeicherten Prozedur auf, um eine Tabelle zu erstellen, die die Funktionswerte enthält.

## <a name="about-feature-engineering"></a>Informationen zu Featureentwicklung

Nachdem Sie eine Zeit damit verbracht haben, Daten zu durchsuchen, haben Sie einige Einsichten in die Daten gesammelt und sind nun bereit, mit der *Featureentwicklung*fortzufahren. Dieser Prozess der Erstellung aussagekräftiger Features aus den Rohdaten ist ein wichtiger Schritt bei der Erstellung von analytischen Modellen.

In diesem DataSet basieren die Entfernungs Werte auf der gemeldeten Verbrauchseinheit und stellen nicht notwendigerweise die geografische Entfernung oder die tatsächliche Entfernung dar. Aus diesem Grund müssen Sie die direkte Entfernung zwischen den Abhol- und den Zielorten berechnen, indem Sie die verfügbaren Koordinaten in im Quell-Dataset NYC Taxi verwenden. Sie erreichen dies, indem Sie die [Haversine-Formel](https://en.wikipedia.org/wiki/Haversine_formula) in einer benutzerdefinierten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktion verwenden.

Verwenden Sie eine benutzerdefinierte T-SQL-Funktion, _fnCalculateDistance_, um die Entfernung mithilfe der Haversine-Formel zu berechnen, und verwenden Sie eine zweite benutzerdefinierte T-SQL-Funktion, _fnEngineerFeatures_, um eine Tabelle mit allen Funktionen zu erstellen.

Der Gesamtprozess lautet wie folgt:

- Erstellen der T-SQL-Funktion, mit der die Berechnungen durchführt werden

- Rufen Sie die Funktion auf, um die Funktionsdaten zu generieren

- Speichern der Featuredaten in einer Tabelle

## <a name="calculate-trip-distance-using-fncalculatedistance"></a>Berechnen der Fahrt Distanz mithilfe von fncalculatedistance

Die Funktion _fncalculatedistance_ sollte im Rahmen der Vorbereitung für dieses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tutorial heruntergeladen und mit registriert worden sein. Nehmen Sie sich einen Moment Zeit, um den Code anzuzeigen.
  
1. Erweitern Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Programmierbarkeit**, erweitern Sie **Funktionen** und anschließend **Skalarwertfunktionen**.   

2. Klicken Sie mit der rechten Maustaste auf _fnCalculateDistance_, und wählen Sie **Ändern** aus, um das [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript in einem neuen Abfragefenster zu öffnen.
  
    ```sql
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function that calculates the direct distance between two geographical coordinates.  
    RETURNS float  
    AS  
    BEGIN  
      DECLARE @distance decimal(28, 10)  
      -- Convert to radians  
      SET @Lat1 = @Lat1 / 57.2958  
      SET @Long1 = @Long1 / 57.2958  
      SET @Lat2 = @Lat2 / 57.2958  
      SET @Long2 = @Long2 / 57.2958  
      -- Calculate distance  
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))  
      --Convert to miles  
      IF @distance <> 0  
      BEGIN  
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);  
      END  
      RETURN @distance  
    END
    GO
    ```
  
    - Die Funktion ist eine Skalarwertfunktion, die einen einzelnen Datenwert eines vordefinierten Typs zurückgibt.
  
    - Sie übernimmt die Werte der Längen- und Breitengrade als Eingaben, die sie von den Abhol- und Zielorten der Fahrten erhält. Die Haversine-Formel wandelt Orte ins Bogenmaß um und verwendet diese Werte, um die direkte Entfernung zwischen zwei Orten in Meilen zu berechnen.

## <a name="generate-the-features-using-fnengineerfeatures"></a>Generieren der Features mithilfe von _fnengineerfeatures_

Um die berechneten Werte einer Tabelle hinzuzufügen, die zum Trainieren des Modells verwendet werden kann, verwenden Sie eine andere Funktion, _fnengineerfeatures_. Die neue Funktion Ruft die zuvor erstellte T-SQL-Funktion _fncalculatedistance_auf, um die direkte Entfernung zwischen den Pick-up-und Dropdown-Speicherorten zu erhalten. 

1. Nehmen Sie sich ein paar Minuten Zeit, um den Code für die benutzerdefinierte T-SQL-Funktion _fnEngineerFeatures_zu überprüfen, die für Sie als Teil der Vorbereitung für diese exemplarische Vorgehensweise erstellt wurde.
  
    ```sql
    CREATE FUNCTION [dbo].[fnEngineerFeatures] (  
    @passenger_count int = 0,  
    @trip_distance float = 0,  
    @trip_time_in_secs int = 0,  
    @pickup_latitude float = 0,  
    @pickup_longitude float = 0,  
    @dropoff_latitude float = 0,  
    @dropoff_longitude float = 0)  
    RETURNS TABLE  
    AS
      RETURN
      (
      -- Add the SELECT statement with parameter references here
      SELECT
        @passenger_count AS passenger_count,
        @trip_distance AS trip_distance,
        @trip_time_in_secs AS trip_time_in_secs,
        [dbo].[fnCalculateDistance](@pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude) AS direct_distance
  
      )
    GO
    ```

    + Diese Tabellenwert Funktion, die mehrere Spalten als Eingaben annimmt und eine Tabelle mit mehreren Merkmals Spalten ausgibt.

    + Der Zweck dieser Funktion besteht darin, neue Features für die Erstellung eines Modells zu erstellen.

2.  Um zu überprüfen, ob diese Funktion funktioniert, verwenden Sie diese, um die geografische Entfernung für die Fahrten zu berechnen, bei denen die gemessene Entfernung den Wert 0 hat, die Pick-und Dropdown-Standorte jedoch unterschiedlich sind.
  
    ```sql
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    Wie Sie sehen können, entspricht die vom Taxameter angezeigte Entfernung nicht immer der geografischen Distanz. Daher ist die Featureentwicklung so wichtig. Sie können diese verbesserten Daten Features verwenden, um ein Machine Learning-Modell mithilfe von R zu trainieren.

## <a name="next-lesson"></a>Nächste Lektion

[Lektion 3: Trainieren und Speichern eines Modells mit T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[Lektion 1: Durchsuchen und Visualisieren von Daten mithilfe von R und gespeicherten Prozeduren](sqldev-explore-and-visualize-the-data.md)
