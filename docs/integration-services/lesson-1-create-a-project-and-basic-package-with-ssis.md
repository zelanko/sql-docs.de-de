---
title: 'Lektion 1: Erstellen eines Projekts und Basispakets mit SSIS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff31579a425f9e86fed11811c9d0a42c3113ee15
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "79288134"
---
# <a name="lesson-1-create-a-project-and-basic-package-with-ssis"></a>Lektion 1: Erstellen eines Projekts und Basispakets mit SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



In dieser Lektion erstellen Sie ein einfaches ETL-Paket, durch das Daten aus einer einzelnen Flatfilequelle extrahiert, mithilfe zweier Transformationen zum Suchen transformiert und anschließend in eine Kopie der **FactCurrencyRate**-Faktentabelle in die Beispieldatenbank **AdventureWorksDW2012** geschrieben werden. Als Teil dieser Lektion lernen Sie das Erstellen neuer Pakete, das Hinzufügen und Konfigurieren von Datenquellen- und Datenzielverbindungen sowie das Arbeiten mit neuen Ablaufsteuerungs- und Datenflusskomponenten.  
  
Vor dem Erstellen eines Pakets müssen Sie die Formatierung kennen, die in den Quelldaten und im Ziel verwendet wird. Dann können Sie die Transformationen definieren, die zum Zuordnen der Quelldaten zum Ziel erforderlich sind.  

## <a name="prerequisites"></a>Voraussetzungen

Dieses Tutorial basiert auf Microsoft SQL Server Data Tools, mehreren Beispielpaketen und einer Beispieldatenbank.

* Informationen zum Installieren von SQL Server Data Tools finden Sie unter [Herunterladen und Installieren von SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md).  
  
* So laden Sie alle Lektionspakete für dieses Tutorial herunter:

    1.  Navigieren Sie zu den [Integration Services tutorial files (Integration Services-Tutorialdateien)](https://www.microsoft.com/download/details.aspx?id=56827).

    2.  Klicken Sie auf die Schaltfläche **Download** (Herunterladen).

    3.  Wählen Sie die Datei **Creating a Simple ETL Package.zip**, und klicken Sie dann auf **Next** (Weiter).

    4.  Entpacken Sie den Inhalt der Datei nach dem Herunterladen in ein lokales Verzeichnis.  

* Informationen zum Installieren und Bereitstellen der Beispieldatenbank **AdventureWorksDW2012** finden Sie unter [Install and configure AdventureWorks sample database – SQL (Installieren und Konfigurieren der AdventureWorks-Beispieldatenbank)](../samples/adventureworks-install-configure.md).
  
## <a name="look-at-the-source-data"></a>Sichten der Quelldaten
Für dieses Tutorial bestehen die Quelldaten aus historischen Währungsdaten in der Flatfile **SampleCurrencyData.txt**. Die Quelldaten bestehen aus den vier folgenden Spalten: der Durchschnittsrate der Währung, einem Währungsschlüssel, einem Datenschlüssel und der Tagesendrate.  
  
Im Folgenden sehen Sie ein Beispiel der Quelldaten in der Datei „SampleCurrencyData.txt“:  
  
<pre>1.00070049USD9/3/05 0:001.001201442  
1.00020004USD9/4/05 0:001  
1.00020004USD9/5/05 0:001.001201442  
1.00020004USD9/6/05 0:001  
1.00020004USD9/7/05 0:001.00070049  
1.00070049USD9/8/05 0:000.99980004  
1.00070049USD9/9/05 0:001.001502253  
1.00070049USD9/10/05 0:000.99990001  
1.00020004USD9/11/05 0:001.001101211  
1.00020004USD9/12/05 0:000.99970009</pre>  
  
Für das Arbeiten mit Flatfile-Quelldaten ist es wichtig zu verstehen, wie die Flatfiledaten vom Flatfile-Verbindungs-Manager interpretiert werden. Wenn die Flatfilequelle aus Unicode besteht, definiert der Flatfile-Verbindungs-Manager alle Spalten als [DT_WSTR] mit einer Standardspaltenbreite von 50. Wenn die Flatfilequelle ANSI-codiert ist, werden die Spalten als [DT_STR] mit einer Standardspaltenbreite von 50 definiert. Wahrscheinlich müssen Sie diese Standardeinstellungen ändern, um die Zeichenfolgen-Spaltentypen an Ihre Daten anzupassen. Sehen Sie sich den Datentyp des Ziels an, und wählen Sie diesen Typ dann im Verbindungs-Manager für Flatfiles aus.  
  
## <a name="look-at-the-destination-data"></a>Sichten der Zieldaten
Das Ziel für die Quelldaten ist eine Kopie der **FactCurrencyRate**-Faktentabelle in **AdventureWorksDW**. Die **FactCurrencyRate**-Faktentabelle weist vier Spalten auf und hat Beziehungen zu zwei Dimensionstabellen, wie der folgenden Tabelle zu entnehmen ist.  
  
|Spaltenname|Datentyp|Nachschlagetabelle|Suchspalte|  
|---------------|-------------|----------------|-----------------|  
|AverageRate|float|Keine|Keine|  
|CurrencyKey|int (FK)|DimCurrency|CurrencyKey (PK)|  
|DateKey|int (FK)|DimDate|DateKey (PK)|  
|EndOfDayRate|float|Keine|Keine|  
  
## <a name="map-the-source-data-to-the-destination"></a>Zuordnen der Quelldaten zum Ziel  
Die Analyse der Quell- und Zieldatenformate ergibt, dass Suchvorgänge für die Werte **CurrencyKey** und **DateKey** notwendig sind. Die Transformationen, von denen diese Suchvorgänge ausgeführt werden, rufen diese Werte mithilfe der alternativen Schlüssel aus den Dimensionstabellen **DimCurrency** und **DimDate** ab.  
  
|Flatfilespalte|Tabellenname|Spaltenname|Datentyp|  
|--------------------|--------------|---------------|-------------|  
|0|FactCurrencyRate|AverageRate|float|  
|1|DimCurrency|CurrencyAlternateKey|nchar (3)|  
|2|DimDate|FullDateAlternateKey|date|  
|3|FactCurrencyRate|EndOfDayRate|float|  
  
## <a name="lesson-tasks"></a>Aufgaben der Lektion  
Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Erstellen eines neuen Integration Services-Projekts](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [Schritt 2: Hinzufügen und Konfigurieren eines Verbindungs-Managers für Flatfiles](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [Schritt 3: Hinzufügen und Konfigurieren eines OLE DB-Verbindungs-Managers](../integration-services/lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [Schritt 4: Hinzufügen eines Datenflusstasks zum Paket](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [Schritt 5: Hinzufügen und Konfigurieren der Flatfilequelle](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [Schritt 6: Hinzufügen und Konfigurieren von Suchtransformationen](../integration-services/lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [Schritt 7: Hinzufügen und Konfigurieren des OLE DB-Ziels](../integration-services/lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [Schritt 8: Vereinfachen des Layouts des Pakets aus Lektion 1](../integration-services/lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [Schritt 9: Testen des Tutorialpakets aus Lektion 1](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
[Schritt 1: Erstellen eines neuen Integration Services-Projekts](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
