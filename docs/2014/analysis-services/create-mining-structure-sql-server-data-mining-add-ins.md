---
title: Erstellen der Miningstruktur (SQL Server Data Mining-Add-ins) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining structures, creating
ms.assetid: b8b1eedc-4d6d-4429-a578-e629ec573934
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 415540535e6456dcead8ca749d8fe0f2fbae5150
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148949"
---
# <a name="create-mining-structure-sql-server-data-mining-add-ins"></a>Miningstruktur erstellen (SQL Server Data Mining-Add-Ins)
  ![Miningstruktur-Schaltfläche "erstellen", Data Mining-Menüband](media/dmc-createstruct.gif "Create Mining Structure-Schaltfläche, Data Mining-Menüband")  
  
 Verwenden der **erweitert** -Option in der **Datenmodellierung** gruppieren, wenn Sie ein Dataset für die Analyse verwendet werden, ohne gleichzeitig ein Modell erstellen möchten. Dies ist hilfreich, wenn Sie unterschiedliche Algorithmen ausprobieren möchten.  
  
 Nachdem Sie die Miningstruktur erstellt haben, verwenden Sie die [Modell einer Struktur hinzufügen](add-model-to-structure-data-mining-add-ins-for-excel.md) Assistenten zum Erstellen eines Modells auf Grundlage dieser Struktur. Sie können auch neue Modelle erstellen, mit der **Data Mining erweiterten Abfrage-Editor**.  
  
 Sie können diese Option auch verwenden, wenn Sie Modelle unter Verwendung eines der erweiterten Algorithmen, wie der linearen Regression oder dem Sequenzclustering, erstellen möchten, die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt werden, in den Assistenten jedoch nicht verfügbar sind, oder wenn Sie einen benutzerdefinierten Algorithmus verwenden.  
  
> [!NOTE]  
>  Beim Erstellen der Miningstruktur können Sie auch ein zufällig ausgewähltes Testdataset erstellen, das zum Überprüfen aller Modelle verwendet werden kann. Dies ist hilfreich, da sich die Modellgenauigkeit einfach anhand eines allgemeinen Datasets vergleichen lässt. Wählen Sie einfach die Option **Daten in Trainings- und Testsätze aufteilen** , und geben Sie einen geeigneten Prozentsatz der Daten für Tests, in der Regel etwa 30 Prozent reserviert werden soll.  
  
## <a name="use-the-wizard-to-create-a-mining-structure"></a>Erstellen einer Miningstruktur mit dem Assistenten  
  
1.  In der **Data Mining** des Menübands, klicken Sie auf **erweitert**, und wählen Sie **Create Structure**.  
  
2.  In der **Quelldaten auswählen** Dialogfeld geben die Excel-Bereich, einer Excel-Datentabelle oder einer externen Datenquelle, die die Daten enthält, für die Analyse verwendet werden sollen.  
  
     Klicken Sie auf **Weiter**.  
  
3.  In der **Spalten auswählen** Dialogfeld überprüfen Sie die Liste der Spalten, die in der ausgewählten Datenquelle verfügbar sind.  
  
4.  Klicken Sie auf den Pfeil rechts neben dem Namen der Spalte so ändern Sie die **Verwendung** der Spalte, die Sie aus dieser Werte auswählen:  
  
    -   **Schlüssel**. Für jedes Modell ist mindestens ein Schlüssel erforderlich.  
  
    -   **Schlüsselzeit**. Diese Option ist nur für Vorhersagemodelle verfügbar, in denen sie erforderlich ist.  
  
    -   **Umfassen**. Gibt an, dass die Spalte in der Miningstruktur verfügbar sein soll, aber keine Schlüsselspalte ist.  
  
    -   **Verwenden Sie keine**. Gibt an, dass die Spalte nicht in die Miningstruktur aufgenommen werden soll.  
  
     Beachten Sie, dass Spalten bei der Modellerstellung immer ignoriert werden können. Um später jedoch Spalten hinzuzufügen, müssen Sie die Struktur und das Modell erneut verarbeiten.  
  
5.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)**  Schaltfläche, um den Inhaltstyp, Datentyp und Modellierungsflags festlegen.  
  
    > [!NOTE]  
    >  Wenn die Spalte numerische Daten enthält, sollten Sie in diesem Dialogfeld stets überprüfen, ob der richtige Datentyp ausgewählt ist. In einigen Fällen möchten Sie die Eingabedaten statt als kontinuierliche Zahl u. U. als Kategorievariablen oder diskrete Werte behandeln, obwohl sie numerisch sind.  
    >   
    >  Eine Spalte für die Postleitzahl kann z. B. standardmäßig als kontinuierlicher Long-Datentyp aufgeführt sein. Um jedoch bessere Ergebnisse zu erzielen, können Sie festlegen, dass sie als diskreter Textwert behandelt wird.  
    >   
    >  Weitere Informationen finden Sie im Abschnitt zu Inhaltstypen in [auswählen von Daten für Data Mining](choosing-data-for-data-mining.md).  
  
     Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
6.  Klicken Sie auf **Weiter**.  
  
     Je nach Art der verwendeten Daten können Sie den Assistenten nach diesem Schritt abschließen. In diesem Fall direkt zu den **Fertig stellen** Seite, um die Miningstruktur zu benennen.  
  
     Bei anderen Modellen haben Sie zusätzlich die Möglichkeit, ein Testdataset zu erstellen.  
  
7.  In der **Daten in Trainings- und Testsätze aufteilen** Dialogfeld Feld, die angeben, wie die Daten partitioniert werden soll. Standardmäßig werden 30 Prozent der Daten für Tests verwendet.  
  
     Geben Sie optional die maximale Anzahl von Zeilen ein, die für Tests verwendet werden sollen.  
  
     Klicken Sie auf **Weiter**.  
  
8.  In der **Fertig stellen** Dialogfeld, geben Sie einen Namen und eine Beschreibung für die neue Miningstruktur.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
### <a name="related-options"></a>Zugehörige Optionen  
  
|Option|Kommentare|  
|------------|--------------|  
|**Wählen Sie die Quelldaten** (Dialogfeld)|Wenn Sie eine Excel-Tabelle auswählen, sollten Sie angeben, ob die Daten bereits über Kopfzeilen verfügen. Wenn Sie diesen Schritt überspringen, wird die erste Datenzeile als Spaltenname verwendet.<br /><br /> Bei Verwendung die Option **externen Datenquelle**, können Sie beliebige Daten, die in definiert werden, können ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenquelle. Allerdings umfasst das Dialogfeld im Add-In zum Erstellen neuer Datenquellen nicht das gesamte Spektrum der von Analysis Services unterstützten Datenquellen. Daher wird empfohlen, die Datenquellen auf dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server im Voraus zu erstellen und dann eine Verbindung unter Verwendung der Add-Ins herzustellen.|  
|**Data Source-Abfrage-Editor** (Dialogfeld)|Nachdem Sie eine Verbindung mit der angegebenen Datenquelle hergestellt haben, können Sie Spalten hinzufügen oder eine benutzerdefinierte Abfrage erstellen, um benutzerdefinierte Spalten zu generieren.|  
|**Teilen Sie Daten in Trainings- und Testsätze auf**|Ein empfohlene Wert für das Training und Testsätze ist 70 Prozent für das Training und 30 Prozent Testzwecken; Wenn Sie eine große Datenmenge verfügen, können Sie eine maximale Anzahl von Zeilen für das Testen angeben.|  
|Dialogfeld Fertig stellen|Die Optionen für Drillthroughfunktionen sind in einigen Modelltypen verfügbar und sehr hilfreich, wenn Sie Detailspalten in die Miningstruktur eingeschlossen haben. Wenn Sie beispielsweise ein Clustermodell erstellen, können Sie Details wie den Namen oder die E-Mail-Adresse zwar für Drillthroughs, aber nicht für Analysen einschließen, um die Kontaktaufnahme mit Kunden in einem bestimmten Cluster zu vereinfachen.|  
  
###  <a name="Bkmk_strctcolumn"></a> Festlegen der Spaltenverwendung der Strukturerstellungs-Assistenten  
 Wenn Sie eine neue Miningstruktur erstellen, können Sie festlegen, welche Spalten in der Datenquelle in die Miningstruktur aufgenommen und wie diese Spalten verwendet werden sollen. Denken Sie daran, dass eine Miningstruktur mehrere Miningmodelle unterstützen kann.  
  
|Werte|Description|  
|------------|-----------------|  
|**Einschließen**|Gibt an, dass die Spalte Daten enthält, die für Analysen oder für Vorhersagen verwendet werden können.|  
|**Key**|Gibt an, dass die Spalte eine Transaktions-ID, eine Reihen-ID oder einen anderen für die Verarbeitung erforderlichen Schlüssel enthält.<br /><br /> Für alle Algorithmen ist eine Schlüsselspalte erforderlich. Bei einigen Algorithmen ist jedoch nur ein einziger Schlüssel zulässig, während andere Algorithmen mehrere Schlüssel zulassen.<br /><br /> Wenn die Spalte einen Schlüssel enthält, aber nicht für die Verarbeitung erforderlich ist, wählen Sie **nicht verwenden**.|  
|**Die Schlüsselzeit**|Gibt an, dass die Spalte ein Datum oder einen anderen numerischen Wert enthält, der verwendet werden kann, um Elemente in einer Zeitreihe eindeutig zu identifizieren.|  
|**Verwenden Sie keine**|Gibt an, dass die Spalte ignoriert werden soll. Die Daten in der Spalte werden nicht verarbeitet.|  
  
 Damit der Algorithmus ein Modell richtig verarbeiten kann, muss Folgendes angegeben werden: die Schlüsselspalte, mit der jede Zeile eindeutig bestimmt wird, die Zielspalte für das Erstellen von Vorhersagen (wenn Sie ein vorhersagbares Modell erstellen) und die Spalten, die als Eingabespalten verwendet werden sollen, um die Beziehungen zu erstellen, anhand derer die Zielspalte vorhergesagt wird.  
  
-   Spalten, die als ausstellerbindung **verwenden Sie keine** wird nicht in der Miningstruktur vorhanden sein.  
  
     Wenn Sie Spalten hinzufügen, die unnötig sind oder ungültige Werte enthalten, kann sich dies negativ auf die Ergebnisse einer Analyse auswirken. Stellen Sie daher sicher, dass nur relevante Spalten eingeschlossen werden. Denken Sie jedoch daran, dass die Spalten, die Sie in der Miningstruktur nicht verwenden, für die Abfrage nicht verfügbar sind.  
  
-   Spalten, die als angegeben sind die **Include** Typ in die Miningstruktur aufgenommen und können später für die Analyse oder Vorhersage in den Miningmodellen verwendet werden.  
  
     Wenn Sie nicht sicher sind, ob Sie die Spalte benötigen, können Sie sie in jedem Fall in die Miningstruktur aufnehmen und anschließend ein Miningmodell erstellen, in dem diese Spalte nicht verwendet wird. Sie könnten beispielsweise für die spätere Bezugnahme eine Telefonnummernspalte in Ihre Daten aufnehmen, aber dann ein Clustermodell erstellen, das die Telefonnummern ignoriert. Nach dem Erstellen der Cluster können Sie eine Abfrage erstellen, die die Telefonnummern der Personen zurückgibt, die zu einem bestimmten Cluster gehören.  
  
-   Alle Algorithmen erfordern eine **Schlüssel** Spalte. Die Werte in der Schlüsselspalte müssen eindeutig sein. Ein **Key Time** Spalte ist nur erforderlich, für die Planung oder zeitreihenmodelle. zugreifen.  
  
### <a name="requirements"></a>Anforderungen  
 Zum Erstellen einer Data Mining-Struktur müssen Sie über eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verfügen. Eine Verbindung ist auch erforderlich, wenn Sie mit temporären Strukturen arbeiten. Weitere Informationen zum Erstellen oder Ändern einer Verbindung finden Sie unter [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)  
  
  