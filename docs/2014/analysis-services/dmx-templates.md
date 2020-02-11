---
title: DMX-Vorlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2a577e52-821d-4bd3-ba35-075a6be285c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3bf7682ce42422efb0e47e4272e53933eba92a4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66081563"
---
# <a name="dmx-templates"></a>DMX-Vorlagen
  Die Data Mining-Vorlagen ermöglichen Ihnen das schnelle Erstellen komplexer Abfragen. Die allgemeine Syntax für DMX-Abfragen ist zwar umfassend dokumentiert, die Vorlagen erleichtern es Ihnen jedoch, Abfragen durch Klicken und Zeigen auf Argumente und Datenquellen zu erstellen.  
  
## <a name="using-the-templates"></a>Verwenden der Vorlagen  
  
1.  Klicken Sie im Data Mining-Client für Excel auf **Abfrage**.  
  
2.  Klicken Sie auf der **Start** Seite des Assistenten auf **weiter**.  
  
3.  **Wählen Sie**auf der Seite Modell aus, und klicken Sie auf **erweitert**.  
  
     **Tipp:** Wenn Sie eine Vorhersage Abfrage für ein Modell erstellen, können Sie zuerst das Modell auswählen und dann auf **erweitert**klicken, um die Vorlage vorab mit dem Modellnamen aufzufüllen.  
  
4.  Klicken Sie im **erweiterten Data Mining-Abfrage-Editor**auf **DMX-Vorlagen**, und wählen Sie eine Vorlage aus.  
  
5.  Drücken Sie die EINGABETASTE, um die Vorlage im Bereich DMX-Abfrage zu laden.  
  
6.  Fahren Sie fort, indem Sie auf die Links in der Vorlage klicken. Wählen Sie im angezeigten Dialogfeld eine entsprechende Ausgabe, ein Modell oder einen Parameter aus.  
  
     Wählen Sie für Vorhersageabfragen zuerst das Eingabedataset aus, und ordnen Sie dann die Spalten zu.  
  
7.  Klicken Sie auf **Abfrage bearbeiten** , um zur Text-Editor-Ansicht zu wechseln und die Abfrage manuell zu ändern.  
  
     Beachten Sie jedoch Folgendes: Wenn Sie beim Arbeiten im Abfrage-Editor zwischen Sichten wechseln, werden alle Informationen aus der vorherigen Sicht gelöscht. Speichern Sie daher vor dem Wechseln der Ansicht Ihre Arbeit, indem Sie die DMX-Anweisungen in eine separate Datei kopieren und diese speichern.  
  
8.  Klicken Sie auf **Fertig stellen**. Geben Sie im Dialogfeld **Ziel auswählen** an, wo das Ergebnis gespeichert werden soll. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Wenn Sie eine-Anweisung erfolgreich ausgeführt haben, wird die DMX-Anweisung, die Sie an den Server gesendet haben, auch im Ablauf **Verfolgungs** Fenster aufgezeichnet. Weitere Informationen zum Verwenden der Ablauf Verfolgungs Funktion finden Sie unter Ablauf [Verfolgung &#40;Data Mining-Client für Excel&#41;](trace-data-mining-client-for-excel.md).  
  
 Weitere Informationen zur Verwendung des erweiterten Data Mining-Abfrage-Editors finden Sie unter [Abfrage &#40;SQL Server Data Mining-Add-ins&#41;](query-sql-server-data-mining-add-ins.md) und erweiterter [Data Mining-Abfrage-Editor](advanced-data-mining-query-editor.md).  
  
## <a name="list-of-dmx-templates"></a>Liste von DMX-Vorlagen  
 Die folgenden DMX-Vorlagen sind im Data Mining-Client für Excel enthalten.  
  
 **Vorher**  
  
 Erstellen Sie mithilfe dieser Vorlagen erweiterte Vorhersageabfragen, u. a. Abfragen, die von den Assistenten der Add-Ins nicht unterstützt werden, z. B. Abfragen, in denen geschachtelte Tabellen oder externe Datenquellen verwendet werden.  
  
-   Gefilterte Vorhersagen  
  
-   Gefilterte geschachtelte Vorhersagen  
  
-   Geschachtelte Vorhersagen  
  
-   Singleton-Vorhersagen  
  
-   Standardvorhersagen  
  
-   Zeitreihen Vorhersagen  
  
-   TOP-Vorhersageabfrage  
  
-   TOP-Vorhersageabfrage für geschachtelte Tabelle  
  
 **Stelle**  
  
 Erstellen Sie mit diesen Vorlagen benutzerdefinierte Modelle oder Datenstrukturen. Sie sind nicht auf die Modelle beschränkt, die von den Assistenten unterstützt werden. Sie können jeden beliebigen Data Mining Algorithmus verwenden [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , der von der Instanz von unterstützt wird, mit der Sie verbunden sind, einschließlich Plug-in-Algorithmen.  
  
-   Mining Modell  
  
-   Miningstruktur  
  
-   Miningstruktur mit zurückgehaltenen Daten  
  
-   Temporäres Modell  
  
-   Temporäre Struktur  
  
 **Modelleigenschaften**  
  
 Erstellen Sie mit diesen Vorlagen Abfragen, mit denen Metadaten zum Modell und zum Trainingssatz abgerufen werden. Sie können auch Details aus dem Modellinhalt abrufen oder ein statistisches Profil der Trainingsdaten abrufen.  
  
-   Mining Modell Inhalt  
  
-   Minimale und maximale Spaltenwerte  
  
-   Test-/Trainingsfälle der Miningstruktur  
  
-   Diskrete Spaltenwerte  
  
 **Verwaltung**  
  
 Führen Sie mit diesen Vorlagen beliebige von DMX unterstützte Verwaltungsaufgaben aus; hierzu zählen das Importieren und Exportieren von Modellen, das Löschen von Modellen sowie das Leeren von Modellen oder Datenstrukturen.  
  
-   Miningmodell entfernen  
  
-   Struktur und Modelle löschen  
  
-   Miningstruktur entfernen  
  
-   Miningmodell löschen  
  
-   Miningstruktur löschen  
  
-   Miningmodell umbenennen  
  
-   Miningstruktur umbenennen  
  
-   Miningmodell trainieren  
  
-   Geschachtelte Miningstruktur trainieren  
  
-   Miningstruktur trainieren  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 In Abhängigkeit der von Ihnen verwendeten Vorlage benötigen Sie möglicherweise Administratorrechte, um auf den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server zugreifen und eine Abfrage ausführen zu können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)  
  
  
