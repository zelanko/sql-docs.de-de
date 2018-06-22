---
title: 'Lektion 4: Speichern von Lieferantendaten in MDS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bacd9eaf-4d12-4f25-aec7-d785dec1b623
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 40f09aa6544bc38378e547c5b6e94dd26956a549
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150711"
---
# <a name="lesson-4-storing-supplier-data-in-mds"></a>Lektion 4: Speichern von Lieferantendaten in MDS
  Master Data Services (MDS) sind die SQL Server-Lösung für die Masterdatenverwaltung. Master Data Management (MDM) beschreibt die Anstrengungen einer Organisation, nicht transaktionale Listen mit Daten zu ermitteln und zu definieren.  
  
 Modelle stellen die höchste Organisationsebene in Master Data Services dar und organisieren die Struktur der Masterdaten. Eine MDS-Implementierung kann ein oder viele Modelle aufweisen, wobei jedes Modell ähnliche Daten gruppiert. Die Masterdaten werden im Allgemeinen in vier Kategorien unterteilt: Personen, Orte, Gegenstände oder Begriffe. Sie können z. B. ein Produktmodell erstellen, das produktbezogene Daten enthält, oder ein Kundenmodell, das kundenbezogene Daten enthält. Finden Sie unter [Modelle (Master Data Services)](http://msdn.microsoft.com/library/ee633746.aspx) Weitere Details.  
  
 Ein Modell kann eine oder mehrere Entitäten enthalten. Jede Entität hat Attribute (Spalten) und Elemente (Zeilen). Die Zeilen enthalten die Masterdaten. In dieser Lektion erstellen Sie ein Lieferantenmodell (Suppliers) mit zwei Entitäten namens "Supplier" und "State". Die Entität "Supplier" verfügt über die folgenden Attribute: Code, Name, Kontakt-Vorname, Kontakt-Nachname, Kontakt-E-Mail-Adresse, Adresszeile, Ort, Bundesland, PLZ und Land. Finden Sie unter [Attribute (Master Data Services)](http://msdn.microsoft.com/library/ee633745.aspx) für Weitere Informationen zu Attributen in der Regel. Die Attribute "Code" und "Name" entsprechen den Spalten "SupplierID" und "Supplier Name" in der Excel-Datei "Cleansed and Matched Suppliers".  
  
 Ein domänenbasiertes Attribut weist Werte auf, die mit Elementen einer anderen Entität aufgefüllt werden. Domänenbasierte Attribute verhindern, dass Benutzer ungültige Attributwerte eingeben. Ein Attributwert kann nur aus der Dropdownliste ausgewählt werden, die von einer anderen Entität aufgefüllt wird. In diesem Lernprogramm ist das Attribut "State" der Entität "Supplier" ein domänenbasiertes Attribut mit Werten aus der Entität "State". Sie können den Wert des Attributs "State" der Entität "Supplier" nur in einen der Werte in der Entität "State" ändern. Finden Sie unter [domänenbasierte Attribute](http://msdn.microsoft.com/library/ff487058.aspx) Weitere Details.  
  
 Eine abgeleitete Hierarchie in MDS wird von der domänenbasierten Attributbeziehung im Modell abgeleitet. In diesem Lernprogramm erstellen Sie eine abgeleitete Hierarchie zwischen der Entität "Supplier" und der Entität "State". Nachdem Sie die abgeleitete Hierarchie erstellt habe, wird eine Liste von Bundesstaaten im Browser von Master Data Manager angezeigt. Wenn Sie in der Liste auf einen Bundesstaat klicken, werden die Lieferanten in diesem Bundesstaat im rechten Bereich angezeigt. Sie werden später eine abgeleitete Hierarchie auf Grundlage dieser Beziehung erstellen. Finden Sie unter [abgeleitete Hierarchien](http://msdn.microsoft.com/library/ee633747.aspx) Weitere Details.  
  
 Sie haben eine Wissensdatenbank in DQS erstellt und verwendet, um Lieferantendaten zu bereinigen und abzugleichen; die Ergebnisse haben Sie in der Datei "Cleansed and Matched Supplier Data.xls" gespeichert. In dieser Lektion laden Sie die bereinigten und abgeglichenen Daten in MDS hoch. DQS enthält nur Informationen zu den Daten (Metadaten), während MDS die Daten selbst speichert (Mastersatz). Beispiel: DQS enthält Informationen über mehrere Lieferanten, aber MDS verwaltet nur die Lieferanten, die ein Unternehmen verwendet.  
  
 In dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
1.  Erstellen der **Lieferanten** -Modell im **MDS** mithilfe der **Master Data Manager Web Application**.  
  
2.  Open **Cleansed and Matched Supplier Data.xls** in Excel, und verwenden die **MDS-Add-in für Excel** So erstellen Sie eine Entität mit dem Namen **Lieferanten** und die Daten in MDS hochladen.  
  
3.  Stellen Sie sicher, dass die Daten in MDS, mithilfe erstellt werden der **Master Data Manager**.  
  
4.  Erstellen Sie eine Entität mit dem Namen **Status** und Aktualisieren der **Status** Attribut des **Lieferanten** Entität ein domänenbasiertes Attribut abhängig sein der **Zustand** Entität. Sie müssen diese alle mit der **MDS-Add-in für Excel**.  
  
5.  Stellen Sie sicher, dass das domänenbasierte Attribut erstellt wird **Master Data Manager** und aktualisieren Sie die Werte für die **Namen** Attribut von der **Zustand** Entität.  
  
6.  Zeigen Sie die Updates, die Sie vorgenommen haben, mit **Master Data Manager** in **Excel**.  
  
7.  Laden Sie Werte aus der **Status** Entität in **Excel** und fügen Sie einen Wert ein, und überprüfen Sie die Hinzufügung mit **Master Data Manager**.  
  
8.  Erstellen und verwenden eine abgeleitete Hierarchie mithilfe der domänenbasierten attributbeziehung zwischen der **Lieferanten** Entität und die **Zustand** Entität (dem Statusattribut von der Entität "Supplier" ist vom Typ State-Entität ) mit **Master Data Manager**.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 1: Erstellen des Modells „Suppliers“ mit Master Data Manager](../../2014/tutorials/task-1-creating-suppliers-model-using-master-data-manager.md)  
  
  