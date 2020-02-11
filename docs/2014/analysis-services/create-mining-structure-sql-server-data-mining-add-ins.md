---
title: Mining Struktur erstellen (SQL Server Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: b8b1eedc-4d6d-4429-a578-e629ec573934
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ae5244110e6b95434f9008fd7dc99cee259acf8c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086819"
---
# <a name="create-mining-structure-sql-server-data-mining-add-ins"></a>Miningstruktur erstellen (SQL Server Data Mining-Add-Ins)
  ![Miningstruktur erstellen (Schaltfläche auf Data Mining-Menüband)](media/dmc-createstruct.gif "Miningstruktur erstellen (Schaltfläche auf Data Mining-Menüband)")  
  
 Verwenden Sie die Option **erweitert** in der Gruppe **Datenmodellierung** , wenn Sie ein Dataset erstellen möchten, das für die Analyse verwendet wird, ohne notwendigerweise ein Modell zu erstellen. Dies ist hilfreich, wenn Sie unterschiedliche Algorithmen ausprobieren möchten.  
  
 Nachdem Sie die Mining Struktur erstellt haben, erstellen Sie mithilfe des Assistenten [zum Hinzufügen von Modellen zu Strukturen](add-model-to-structure-data-mining-add-ins-for-excel.md) ein auf dieser Struktur basierendes Modell. Mithilfe des **erweiterten Data Mining-Abfrage-Editors**können Sie auch neue Modelle erstellen.  
  
 Sie können diese Option auch verwenden, wenn Sie Modelle unter Verwendung eines der erweiterten Algorithmen, wie der linearen Regression oder dem Sequenzclustering, erstellen möchten, die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt werden, in den Assistenten jedoch nicht verfügbar sind, oder wenn Sie einen benutzerdefinierten Algorithmus verwenden.  
  
> [!NOTE]  
>  Beim Erstellen der Miningstruktur können Sie auch ein zufällig ausgewähltes Testdataset erstellen, das zum Überprüfen aller Modelle verwendet werden kann. Dies ist hilfreich, da sich die Modellgenauigkeit einfach anhand eines allgemeinen Datasets vergleichen lässt. Wählen Sie einfach die Option **Daten in Trainings-und Testsätze aufteilen** aus, und geben Sie einen geeigneten Prozentsatz der Daten an, die für den Test reserviert werden sollen, normalerweise etwa 30%  
  
## <a name="use-the-wizard-to-create-a-mining-structure"></a>Erstellen einer Miningstruktur mit dem Assistenten  
  
1.  Klicken Sie im Menüband **Data Mining** auf **erweitert**, und wählen Sie **Struktur erstellen**aus.  
  
2.  Geben Sie im Dialogfeld **Quelldaten auswählen** den Excel-Bereich, die Excel-Datentabelle oder die externe Datenquelle an, die die Daten enthält, die Sie für die Analyse verwenden möchten.  
  
     Klicken Sie auf **Weiter**.  
  
3.  Überprüfen Sie im Dialogfeld **Spalten auswählen** die Liste der Spalten, die in der ausgewählten Datenquelle verfügbar sind.  
  
4.  Klicken Sie auf den Pfeil rechts neben dem Spaltennamen, um die **Verwendung** der Spalte zu ändern, indem Sie die folgenden Werte auswählen:  
  
    -   **Schlüssel**. Für jedes Modell ist mindestens ein Schlüssel erforderlich.  
  
    -   **Schlüsselzeit**. Diese Option ist nur für Vorhersagemodelle verfügbar, in denen sie erforderlich ist.  
  
    -   **Einschließen**. Gibt an, dass die Spalte in der Miningstruktur verfügbar sein soll, aber keine Schlüsselspalte ist.  
  
    -   **Verwenden Sie nicht**. Gibt an, dass die Spalte nicht in die Miningstruktur aufgenommen werden soll.  
  
     Beachten Sie, dass Spalten bei der Modellerstellung immer ignoriert werden können. Um später jedoch Spalten hinzuzufügen, müssen Sie die Struktur und das Modell erneut verarbeiten.  
  
5.  Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)** , um Inhaltstyp, Datentyp und Modellierungsflags festzulegen.  
  
    > [!NOTE]  
    >  Wenn die Spalte numerische Daten enthält, sollten Sie in diesem Dialogfeld stets überprüfen, ob der richtige Datentyp ausgewählt ist. In einigen Fällen möchten Sie die Eingabedaten statt als kontinuierliche Zahl u. U. als Kategorievariablen oder diskrete Werte behandeln, obwohl sie numerisch sind.  
    >   
    >  Eine Spalte für die Postleitzahl kann z. B. standardmäßig als kontinuierlicher Long-Datentyp aufgeführt sein. Um jedoch bessere Ergebnisse zu erzielen, können Sie festlegen, dass sie als diskreter Textwert behandelt wird.  
    >   
    >  Weitere Informationen finden Sie im Abschnitt zu den Inhaltstypen unter [Auswählen von Daten für Data Mining](choosing-data-for-data-mining.md).  
  
     Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
6.  Klicken Sie auf **Weiter**.  
  
     Je nach Art der verwendeten Daten können Sie den Assistenten nach diesem Schritt abschließen. Springen Sie in diesem Fall zur Seite **Fertig** stellen, um die Mining Struktur zu benennen.  
  
     Bei anderen Modellen haben Sie zusätzlich die Möglichkeit, ein Testdataset zu erstellen.  
  
7.  Geben Sie im Dialogfeld **Daten in Trainings-und Test Datasets aufteilen** an, wie die Daten partitioniert werden sollen. Standardmäßig werden 30 Prozent der Daten für Tests verwendet.  
  
     Geben Sie optional die maximale Anzahl von Zeilen ein, die für Tests verwendet werden sollen.  
  
     Klicken Sie auf **Weiter**.  
  
8.  Geben Sie im Dialogfeld **Fertig** stellen einen Namen und eine Beschreibung für die neue Mining Struktur ein.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
### <a name="related-options"></a>Zugehörige Optionen  
  
|Option|Kommentare|  
|------------|--------------|  
|**Quelldaten auswählen** (Dialogfeld)|Wenn Sie eine Excel-Tabelle auswählen, sollten Sie angeben, ob die Daten bereits über Kopfzeilen verfügen. Wenn Sie diesen Schritt überspringen, wird die erste Datenzeile als Spaltenname verwendet.<br /><br /> Wenn Sie die Option **externe Datenquelle**verwenden, können Sie eine beliebige Art von Daten verwenden, die in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenquelle definiert werden können. Allerdings umfasst das Dialogfeld im Add-In zum Erstellen neuer Datenquellen nicht das gesamte Spektrum der von Analysis Services unterstützten Datenquellen. Daher wird empfohlen, die Datenquellen auf dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server im Voraus zu erstellen und dann eine Verbindung unter Verwendung der Add-Ins herzustellen.|  
|**Datenquellen Abfrage-Editor** (Dialogfeld)|Nachdem Sie eine Verbindung mit der angegebenen Datenquelle hergestellt haben, können Sie Spalten hinzufügen oder eine benutzerdefinierte Abfrage erstellen, um benutzerdefinierte Spalten zu generieren.|  
|**Daten in Trainings- und Testsätze aufteilen**|Ein empfohlener Wert für Trainings-und Testsätze ist 70 Prozent für das Training und 30 Prozent für Tests. Wenn Sie jedoch viele Daten haben, können Sie eine maximale Anzahl von Zeilen für das Testen angeben.|  
|Dialogfeld Fertig stellen|Die Optionen für Drillthroughfunktionen sind in einigen Modelltypen verfügbar und sehr hilfreich, wenn Sie Detailspalten in die Miningstruktur eingeschlossen haben. Wenn Sie beispielsweise ein Clustermodell erstellen, können Sie Details wie den Namen oder die E-Mail-Adresse zwar für Drillthroughs, aber nicht für Analysen einschließen, um die Kontaktaufnahme mit Kunden in einem bestimmten Cluster zu vereinfachen.|  
  
###  <a name="Bkmk_strctcolumn"></a>Festlegen der Spalten Verwendung im Assistenten zum Erstellen von Mining Strukturen  
 Wenn Sie eine neue Miningstruktur erstellen, können Sie festlegen, welche Spalten in der Datenquelle in die Miningstruktur aufgenommen und wie diese Spalten verwendet werden sollen. Denken Sie daran, dass eine Miningstruktur mehrere Miningmodelle unterstützen kann.  
  
|Werte|BESCHREIBUNG|  
|------------|-----------------|  
|**Darunter**|Gibt an, dass die Spalte Daten enthält, die für Analysen oder für Vorhersagen verwendet werden können.|  
|**Schlüssel**|Gibt an, dass die Spalte eine Transaktions-ID, eine Reihen-ID oder einen anderen für die Verarbeitung erforderlichen Schlüssel enthält.<br /><br /> Für alle Algorithmen ist eine Schlüsselspalte erforderlich. Bei einigen Algorithmen ist jedoch nur ein einziger Schlüssel zulässig, während andere Algorithmen mehrere Schlüssel zulassen.<br /><br /> Wenn die Spalte einen Schlüssel enthält, jedoch nicht für die Verarbeitung erforderlich ist, wählen Sie **nicht verwenden**aus.|  
|**Key Time**|Gibt an, dass die Spalte ein Datum oder einen anderen numerischen Wert enthält, der verwendet werden kann, um Elemente in einer Zeitreihe eindeutig zu identifizieren.|  
|**Nicht verwenden**|Gibt an, dass die Spalte ignoriert werden soll. Die Daten in der Spalte werden nicht verarbeitet.|  
  
 Damit der Algorithmus ein Modell richtig verarbeiten kann, muss Folgendes angegeben werden: die Schlüsselspalte, mit der jede Zeile eindeutig bestimmt wird, die Zielspalte für das Erstellen von Vorhersagen (wenn Sie ein vorhersagbares Modell erstellen) und die Spalten, die als Eingabespalten verwendet werden sollen, um die Beziehungen zu erstellen, anhand derer die Zielspalte vorhergesagt wird.  
  
-   Spalten, die als **nicht verwenden** angegeben sind, sind in der Mining Struktur nicht vorhanden.  
  
     Wenn Sie Spalten hinzufügen, die unnötig sind oder ungültige Werte enthalten, kann sich dies negativ auf die Ergebnisse einer Analyse auswirken. Stellen Sie daher sicher, dass nur relevante Spalten eingeschlossen werden. Denken Sie jedoch daran, dass die Spalten, die Sie in der Miningstruktur nicht verwenden, für die Abfrage nicht verfügbar sind.  
  
-   Spalten **, die als includetyp angegeben** werden, werden in die Mining Struktur eingeschlossen und können später für die Analyse oder Vorhersage in den Mining Modellen verwendet werden.  
  
     Wenn Sie nicht sicher sind, ob Sie die Spalte benötigen, können Sie sie in jedem Fall in die Miningstruktur aufnehmen und anschließend ein Miningmodell erstellen, in dem diese Spalte nicht verwendet wird. Sie könnten beispielsweise für die spätere Bezugnahme eine Telefonnummernspalte in Ihre Daten aufnehmen, aber dann ein Clustermodell erstellen, das die Telefonnummern ignoriert. Nach dem Erstellen der Cluster können Sie eine Abfrage erstellen, die die Telefonnummern der Personen zurückgibt, die zu einem bestimmten Cluster gehören.  
  
-   Alle Algorithmen erfordern eine **Schlüssel** Spalte. Die Werte in der Schlüsselspalte müssen eindeutig sein. Eine **Key Time** -Spalte ist nur für Vorhersage-oder Zeitreihen Modelle erforderlich. .  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Zum Erstellen einer Data Mining-Struktur müssen Sie über eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verfügen. Eine Verbindung ist auch erforderlich, wenn Sie mit temporären Strukturen arbeiten. Weitere Informationen zum Erstellen oder Ändern einer Verbindung finden Sie unter Herstellen einer Verbindung [mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)  
  
  
