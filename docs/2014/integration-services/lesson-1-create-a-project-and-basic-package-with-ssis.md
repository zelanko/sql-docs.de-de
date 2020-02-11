---
title: 'Lektion 1: Erstellen des Projekts und Basispakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 652cf44f70e890b3203ed27890d06f98d70b7f1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62767502"
---
# <a name="lesson-1-creating-the-project-and-basic-package"></a>Lektion 1: Erstellen des Projekts und Basispakets
  In dieser Lektion erstellen Sie ein einfaches ETL-Paket, durch das Daten aus einer einzelnen Flatfilequelle extrahiert, Daten mithilfe zweier Transformationskomponenten für die Suche transformiert und diese Daten in die **FactCurrency** -Faktentabelle in **AdventureWorksDW2012**geschrieben werden. Als Teil dieser Lektion lernen Sie das Erstellen neuer Pakete, das Hinzufügen und Konfigurieren von Datenquellen- und Datenzielverbindungen sowie das Arbeiten mit neuen Ablaufsteuerungs- und Datenflusskomponenten.  
  
> [!IMPORTANT]  
>  Dieses Lernprogramm erfordert die **AdventureWorksDW2012** -Beispieldatenbank. Weitere Informationen zum Installieren und Bereitstellen von **AdventureWorksDW2012**finden Sie unter [Microsoft SQL Server Product Samples: Reporting Services](https://archive.codeplex.com/?p=msftrsprodsamples).  
  
## <a name="understanding-the-package-requirements"></a>Grundlegendes zu Paketanforderungen  
 Dieses Lernprogramm erfordert Microsoft SQL Server Data Tools.  
  
 Weitere Informationen zum Installieren von SQL Server Data Tools finden Sie unter [Herunterladen von SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017).  
  
 Vor dem Erstellen eines Pakets benötigen Sie ein durchgehendes Verständnis der Formatierung in Quelldaten und dem Ziel. Nachdem Sie sich mit beiden dieser Datenformate vertraut gemacht haben, können Sie die Transformationen definieren, die zum Zuordnen der Quelldaten zum Ziel erforderlich sind.  
  
### <a name="looking-at-the-source"></a>Untersuchen der Quelle  
 Für dieses Lernprogramm bestehen die Quelldaten aus einer Reihe von historischen Währungsdaten in der Flatfile SampleCurrencyData.txt. Die Quelldaten bestehen aus den vier folgenden Spalten: der Durchschnittsrate der Währung, einem Währungsschlüssel, einem Datenschlüssel und der Tagesendrate.  
  
 Im Folgenden sehen Sie ein Beispiel der in der Datei SampleCurrencyData.txt enthaltenen Quelldaten:  
  
 `1.00070049USD9/3/05 0:001.001201442`  
  
 `1.00020004USD9/4/05 0:001`  
  
 `1.00020004USD9/5/05 0:001.001201442`  
  
 `1.00020004USD9/6/05 0:001`  
  
 `1.00020004USD9/7/05 0:001.00070049`  
  
 `1.00070049USD9/8/05 0:000.99980004`  
  
 `1.00070049USD9/9/05 0:001.001502253`  
  
 `1.00070049USD9/10/05 0:000.99990001`  
  
 `1.00020004USD9/11/05 0:001.001101211`  
  
 `1.00020004USD9/12/05 0:000.99970009`  
  
 Für das Arbeiten mit Flatfile-Quelldaten ist das Verständnis darüber wichtig, wie vom Flatfile-Verbindungs-Manager die Flatfiledaten interpretiert werden. Wenn die Flatfilequelle aus Unicode besteht, definiert der Flatfile-Verbindungs-Manager alle Spalten als [DT_WSTR] mit einer Standardspaltenbreite von 50. Wenn die Flatfilequelle ANSI-codiert ist, werden die Spalten als [DT_STR] mit einer Spaltenbreite von 50 definiert. Wahrscheinlich müssen Sie diese Standards ändern, um die Zeichenfolgen-Spaltentypen Ihren Daten anzupassen. Dafür müssen Sie den Datentyp des Zieles untersuchen, wohin die Daten geschrieben werden, und dann den entsprechenden Typ innerhalb des Flatfile-Verbindungs-Managers auswählen.  
  
### <a name="looking-at-the-destination"></a>Untersuchen des Zieles  
 Das endgültige Ziel für die Quelldaten ist die **FactCurrency** -Faktentabelle in **AdventureWorksDW**. Die **FactCurrency** -Faktentabelle weist vier Spalten auf und hat Beziehungen zu zwei Dimensionstabellen, wie in der folgenden Tabelle angezeigt.  
  
|Spaltenname|Datentyp|Nachschlagetabelle|Suchspalte|  
|-----------------|---------------|------------------|-------------------|  
|AverageRate|float|Keine|Keine|  
|CurrencyKey|int (FK)|DimCurrency|CurrencyKey (PK)|  
|DateKey|int (FK)|DimDate|DateKey (PK)|  
|EndOfDayRate|float|Keine|Keine|  
  
### <a name="mapping-source-data-to-be-compatible-with-the-destination"></a>Zuordnen der Quelldaten zum Ziel aus Kompatibilitätsgründen  
 Die Analyse der Quell- und Zieldatenformate ergibt, dass Suchvorgänge für die Werte **CurrencyKey** und **DateKey** notwendig sein werden. Die Transformationen, von denen diese Suchvorgänge ausgeführt werden, rufen die Werte **CurrencyKey** und **DateKey** ab, indem die alternativen Schlüssel aus den Dimensionstabellen **DimCurrency** und **DimDate** verwendet werden.  
  
|Flatfilespalte|Tabellenname|Spaltenname|Datentyp|  
|----------------------|----------------|-----------------|---------------|  
|0|FactCurrency|AverageRate|float|  
|1|DimCurrency|CurrencyAlternateKey|nchar (3)|  
|2|DimDate|FullDateAlternateKey|date|  
|3|FactCurrency|EndOfDayRate|float|  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Erstellen eines neuen Integration Services-Projekts](lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [Schritt 2: Hinzufügen und Konfigurieren eines Verbindungs-Managers für Flatfiles](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [Schritt 3: Hinzufügen und Konfigurieren eines OLE DB-Verbindungs-Managers](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [Schritt 4: Hinzufügen eines Datenflusstasks zum Paket](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [Schritt 5: Hinzufügen und Konfigurieren der Flatfilequelle](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [Schritt 6: Hinzufügen und Konfigurieren von Suchtransformationen](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [Schritt 7: Hinzufügen und Konfigurieren des OLE DB-Ziels](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [Schritt 8: Vereinfachen des Layouts des Lektion 1-Pakets](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [Schritt 9: Testen des Lektion 1-Lernprogrammpakets](lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
 [Schritt 1: Erstellen eines neuen Integration Services-Projekts](lesson-1-1-creating-a-new-integration-services-project.md)  
  
  
