---
title: Erstellen oder Anpassen einer datenfeedbibliothek (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data feed library
- data feeds [Analysis Services with SharePoint]
ms.assetid: 699fbeb9-42ab-436b-beba-214db51ea3dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 853798cd1e78757684d16f7b964787dfa13d208a
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175639"
---
# <a name="create-or-customize-a-data-feed-library-powerpivot-for-sharepoint"></a>Erstellen oder Anpassen einer Datenfeedbibliothek (PowerPivot für SharePoint)
  Eine *Datenfeedbibliothek* ist eine zweckgebundene SharePoint-Bibliothek, mit der Sie Atom-Datendienstdokumente (.atomsvc) registrieren und freigeben können. Diese Dokumente enthalten XML-Datenfeeds in [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappen oder anderen Clientanwendungen, die das Atom-Datenfeedformat unterstützen. Eine Datenfeedbibliothek unterscheidet sich von anderen SharePoint-Bibliotheken, da sie folgende Möglichkeiten bietet:

-   Erstellen oder Bearbeiten eines *Datendienstdokuments*, das zum Angeben einer HTTP-Verbindung mit einem bestimmten Feed verwendet wird.

-   Freigeben und Verwalten von Datendienstdokumenten an einem zentralen Speicherort.

-   Visuelle Identifizierung von Datendienst Dokumenten durch ein Symbol, damit Dienst Dokumente leicht von anderen in derselben Bibliothek gespeicherten Dokumenten unterschieden werden können: ![GMNI_IconDataFeed](../media/gmni-icondatafeed.gif "GMNI_IconDataFeed")

 Eine Datenfeedbibliothek enthält immer Datendienstdokumente (ATOMSVC-Dateien) und nie den Datenfeed selbst. Im Gegensatz zu einem Datenfeed, der aus statischen XML-Daten besteht, gibt das Datendienstdokument eine URL zu einem Dienst oder einer Anwendung an, der bzw. die auf Anforderung einen Feed generiert, und stellt wiederverwendbare Verbindungsinformationen für wiederholbare Importvorgänge bereit.

 Dieses Thema enthält folgende Abschnitte:

 [Voraussetzungen](#prereq)

 [Erstellen einer neuen datenfeedbibliothek](#createlib)

 [Hinzufügen des Inhaltstyps für Datenfeeds zu einer Bibliothek](#addtolib)

##  <a name="prereq"></a> Voraussetzungen
 
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Funktion muss für die Websites aktiviert werden, für die Sie die Datenfeedbibliothek erstellen. Wenn der Vorlagentyp für Datenfeedbibliotheken nicht verfügbar ist, liegt dies höchstwahrscheinlich daran, dass diese Voraussetzung nicht erfüllt wurde. Weitere Informationen finden Sie unter [Aktivieren der Power Pivot-Funktions Integration für Website Sammlungen in der zentral Administration](activate-power-pivot-integration-for-site-collections-in-ca.md).

 Sie müssen Websitebesitzer sein, um die Bibliothek erstellen zu können.

##  <a name="createlib"></a>Erstellen einer neuen datenfeedbibliothek
 Das Erstellen einer Datenfeedbibliothek ist der erste Schritt zur Aktivierung von Datenfeeds für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Arbeitsmappen. Da eine Datenfeedbibliothek Anwendungs- und Verwaltungsseiten für Datendienstdokumente bereitstellt, muss diese Bibliothek vorhanden sein, bevor Sie ein neues Dokument erstellen können.

 Eine Datenfeedbibliothek basiert auf einer integrierten Vorlage und einem vorkonfigurierten *Inhaltstyp für Datendienstdokumente* , der Eigenschaften und Verhaltensweisen für ein Datendienstdokument definiert.

1.  Klicken Sie in der oberen linken Ecke der Seite auf **Websiteaktionen** .

2.  Klicken Sie auf **Weitere Optionen**...

3.  Klicken Sie unter Bibliotheken auf **Datenfeedbibliothek**.

4.  Geben Sie Namen, Beschreibung, Start- und Versionseinstellungen ein. Geben Sie auch beschreibende Informationen an, um Benutzern die Identifikation dieser Bibliothek als Speicherort für Datendienstdokumente zu erleichtern.

5.  Klicken Sie auf **Erstellen**.

 Im Schnellstart-Navigationsbereich für die aktuelle Website wird ein Link zur Datenfeedbibliothek angezeigt.

 Nachdem Sie eine Bibliothek erstellt haben, können Sie mit ihrer Hilfe Datendienstdokumente erstellen. Weitere Informationen finden Sie unter [Verwenden von Daten Feeds &#40;PowerPivot für SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md).

##  <a name="addtolib"></a>Hinzufügen des Inhaltstyps für Datenfeeds zu einer Bibliothek
 Wenn Sie keine dedizierte Datenfeedbibliothek erstellen, aber trotzdem Datendienstdokumente von einer SharePoint-Website erstellen und verwalten möchten, können Sie den Inhaltstyp für Datendienstdokumente für eine beliebige Bibliothek manuell hinzufügen und konfigurieren, die Sie zum Freigeben von Datendienstdokumenten (ATOMSVC-Dateien) verwenden möchten.

 Sie müssen mindestens über die Listenverwaltungsberechtigung verfügen, um einen Inhaltstyp hinzuzufügen und zu konfigurieren. Diese Berechtigung ist in die Berechtigungsebene "Entwerfen" und höher integriert.

 Die folgenden Schritte müssen für jede Bibliothek wiederholt werden, in der Sie Dokumente für die Datenfeedregistrierung erstellen oder bearbeiten möchten.

#### <a name="step-1-enable-content-type-management"></a>Schritt 1: Aktivieren der Inhaltstypverwaltung

1.  Öffnen Sie die Dokumentbibliothek, für die Sie mehrere Inhaltstypen aktivieren möchten.

2.  Klicken Sie im SharePoint-Menüband in den Bibliothekstools auf **Bibliothek**.

3.  Klicken Sie auf **Einstellungen**.

4.  Klicken Sie auf **Bibliothekeinstellungen**.

5.  Klicken Sie unter Allgemeine Einstellungen auf **Erweiterte Einstellungen**.

6.  Klicken Sie unter Inhaltstypen im Abschnitt Verwaltung von Inhaltstypen zulassen? auf **Ja**.

7.  Klicken Sie auf **OK**.

#### <a name="step-2-add-the-data-service-document-content-type"></a>Schritt 2: Fügen Sie einen Inhaltstyp für Datendienstdokumente hinzu

1.  Klicken Sie im Abschnitt Inhaltstypen auf **Aus vorhandenen Websiteinhaltstypen hinzufügen**. Falls diese Seite nicht angezeigt wird, wechseln Sie zurück zur Website und klicken unter Bibliothekstools auf **Bibliothek** und dann auf **Bibliothekseinstellungen**.

2.  Klicken Sie unter Inhaltstypen auf **Aus vorhandenen Websiteinhaltstypen hinzufügen**.

3.  Wählen Sie unter Websiteinhaltstypen auswählen aus: die Option **Business Intelligence**aus.

4.  Klicken Sie in der Liste der verfügbaren Websiteinhaltstypen auf **Datendienstdokumente**und dann auf **Hinzufügen** , um den ausgewählten Inhaltstyp in die Liste der hinzuzufügenden Inhaltstypen zu verschieben.

5.  Klicken Sie auf **OK**.

#### <a name="step-3-verify-data-service-document-configuration"></a>Schritt 3: Überprüfen der Datendienstdokumentkonfiguration

1.  Öffnen Sie die Homepage der Website.

2.  Öffnen Sie die Bibliothek.

3.  Klicken Sie im SharePoint-Menüband auf **Dokumente**.

4.  Klicken Sie auf den Pfeil nach unten in Neues Dokument, und wählen Sie **Datendienstdokument**aus. Die Seite Neues Datendienstdokument sollte angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
 [Verwenden von Datenfeeds &#40;PowerPivot für SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md) [Löschen einer Power Pivot-datenfeedbibliothek](delete-a-power-pivot-data-feed-library.md) [Power Pivot-Server Verwaltung und-Konfiguration in](power-pivot-server-administration-and-configuration-in-central-administration.md) [Power Pivot-Daten Feeds](power-pivot-data-feeds.md) der zentral Administration


