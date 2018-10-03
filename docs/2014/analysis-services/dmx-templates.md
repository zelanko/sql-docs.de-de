---
title: DMX-Vorlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 2a577e52-821d-4bd3-ba35-075a6be285c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4332d78fef98d653029d0913c6b7da8cfe5a75f0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048256"
---
# <a name="dmx-templates"></a>DMX-Vorlagen
  Die Data Mining-Vorlagen ermöglichen Ihnen das schnelle Erstellen komplexer Abfragen. Die allgemeine Syntax für DMX-Abfragen ist zwar umfassend dokumentiert, die Vorlagen erleichtern es Ihnen jedoch, Abfragen durch Klicken und Zeigen auf Argumente und Datenquellen zu erstellen.  
  
## <a name="using-the-templates"></a>Verwenden der Vorlagen  
  
1.  Klicken Sie im Data Mining-Client für Excel können auf **Abfrage**.  
  
2.  Im Assistenten **starten** auf **Weiter**.  
  
3.  Auf der Seite **Modell auswählen**, klicken Sie auf **erweitert**.  
  
     **Tipp:** , wenn Sie beabsichtigen, eine Vorhersageabfrage für ein Modell zu erstellen, können Sie zuerst das Modell auswählen, und klicken Sie dann auf **erweitert**, um die Vorlage mit dem Modellnamen aufzufüllen.  
  
4.  In der **erweiterten Data Mining Query Editor**, klicken Sie auf **DMX-Vorlagen**, und wählen Sie eine Vorlage.  
  
5.  Drücken Sie die EINGABETASTE, um die Vorlage im Bereich DMX-Abfrage zu laden.  
  
6.  Fahren Sie fort, indem Sie auf die Links in der Vorlage klicken. Wählen Sie im angezeigten Dialogfeld eine entsprechende Ausgabe, ein Modell oder einen Parameter aus.  
  
     Wählen Sie für Vorhersageabfragen zuerst das Eingabedataset aus, und ordnen Sie dann die Spalten zu.  
  
7.  Klicken Sie auf **Abfrage bearbeiten** zu Text-Editor-Ansicht wechseln und die Abfrage manuell ändern.  
  
     Beachten Sie jedoch Folgendes: Wenn Sie beim Arbeiten im Abfrage-Editor zwischen Sichten wechseln, werden alle Informationen aus der vorherigen Sicht gelöscht. Speichern Sie daher vor dem Wechseln der Ansicht Ihre Arbeit, indem Sie die DMX-Anweisungen in eine separate Datei kopieren und diese speichern.  
  
8.  Klicken Sie auf **Fertig stellen**. In der **Ziel auswählen** Dialogfeld Feld, an dem das Ergebnis gespeichert werden soll. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Wenn Sie eine Anweisung erfolgreich ausgeführt, die DMX-Anweisung, die Sie sich an den Server gesendet, wird auch in aufgezeichnet der **Ablaufverfolgung** Fenster. Weitere Informationen zum Verwenden des Ablaufverfolgungsfunktionen finden Sie unter [Ablaufverfolgung &#40;Data Mining-Client für Excel&#41;](trace-data-mining-client-for-excel.md).  
  
 Weitere Informationen zur Verwendung der erweiterten Data Mining Query Editor finden Sie unter [Abfrage &#40;SQL Server Data Mining-Add-ins&#41; ](query-sql-server-data-mining-add-ins.md) und [Erweiterter Editor für Data Mining](advanced-data-mining-query-editor.md).  
  
## <a name="list-of-dmx-templates"></a>Liste von DMX-Vorlagen  
 Die folgenden DMX-Vorlagen sind im Data Mining-Client für Excel enthalten.  
  
 **Vorhersage**  
  
 Erstellen Sie mithilfe dieser Vorlagen erweiterte Vorhersageabfragen, u. a. Abfragen, die von den Assistenten der Add-Ins nicht unterstützt werden, z. B. Abfragen, in denen geschachtelte Tabellen oder externe Datenquellen verwendet werden.  
  
-   Gefilterte Vorhersagen  
  
-   Gefilterte geschachtelte Vorhersagen  
  
-   Geschachtelte Vorhersagen  
  
-   Singleton-Vorhersagen  
  
-   Standardvorhersagen  
  
-   Zeitreihenvorhersagen  
  
-   TOP-Vorhersageabfrage  
  
-   TOP-Vorhersageabfrage für geschachtelte Tabelle  
  
 **Erstellen**  
  
 Erstellen Sie mit diesen Vorlagen benutzerdefinierte Modelle oder Datenstrukturen. Sie sind nicht auf von den Assistenten unterstützte Modelle beschränkt – Sie können beliebige Data Mining-Algorithmen verwenden, die von der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz unterstützt werden, mit der Sie verbunden sind (einschließlich von Plug-In-Algorithmen).  
  
-   Miningmodell  
  
-   Miningstruktur  
  
-   Miningstruktur mit zurückgehaltenen Daten  
  
-   Temporäres Modell  
  
-   Temporäre Struktur  
  
 **Modelleigenschaften**  
  
 Erstellen Sie mit diesen Vorlagen Abfragen, mit denen Metadaten zum Modell und zum Trainingssatz abgerufen werden. Sie können auch Details aus dem Modellinhalt abrufen oder ein statistisches Profil der Trainingsdaten abrufen.  
  
-   Miningmodellinhalt  
  
-   Minimum und maximumspaltenwerte  
  
-   Test-/Trainingsfälle der Miningstruktur  
  
-   Diskrete Spaltenwerte  
  
 **Verwaltung**  
  
 Führen Sie mit diesen Vorlagen beliebige von DMX unterstützte Verwaltungsaufgaben aus; hierzu zählen das Importieren und Exportieren von Modellen, das Löschen von Modellen sowie das Leeren von Modellen oder Datenstrukturen.  
  
-   Miningmodell entfernen  
  
-   Struktur und Modelle entfernen  
  
-   Miningstruktur entfernen  
  
-   Miningmodell löschen  
  
-   Miningstruktur löschen  
  
-   Miningmodell umbenennen  
  
-   Miningstruktur umbenennen  
  
-   Miningmodell trainieren  
  
-   Geschachtelte Miningstruktur trainieren  
  
-   Miningstruktur trainieren  
  
### <a name="requirements"></a>Anforderungen  
 In Abhängigkeit der von Ihnen verwendeten Vorlage benötigen Sie möglicherweise Administratorrechte, um auf den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server zugreifen und eine Abfrage ausführen zu können.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)  
  
  
