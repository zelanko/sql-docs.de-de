---
title: 'Lektion 4: Speichern von Lieferantendaten in MDS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: bacd9eaf-4d12-4f25-aec7-d785dec1b623
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 6eea9f96939f61da77262b549e2ec966ae9a957b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63137438"
---
# <a name="lesson-4-storing-supplier-data-in-mds"></a>Lektion 4: Speichern von Lieferantendaten in MDS
  Master Data Services (MDS) sind die SQL Server-Lösung für die Masterdatenverwaltung. Master Data Management (MDM) beschreibt die Anstrengungen einer Organisation, nicht transaktionale Listen mit Daten zu ermitteln und zu definieren.  
  
 Modelle stellen die höchste Organisationsebene in Master Data Services dar und organisieren die Struktur der Masterdaten. Eine MDS-Implementierung kann ein oder viele Modelle aufweisen, wobei jedes Modell ähnliche Daten gruppiert. Die Masterdaten werden im Allgemeinen in vier Kategorien unterteilt: Personen, Orte, Gegenstände oder Begriffe. Sie können z. B. ein Produktmodell erstellen, das produktbezogene Daten enthält, oder ein Kundenmodell, das kundenbezogene Daten enthält. Finden Sie unter [Modelle (Master Data Services)](https://msdn.microsoft.com/library/ee633746.aspx) Weitere Details.  
  
 Ein Modell kann eine oder mehrere Entitäten enthalten. Jede Entität hat Attribute (Spalten) und Elemente (Zeilen). Die Zeilen enthalten die Masterdaten. In dieser Lektion erstellen Sie ein Lieferantenmodell (Suppliers) mit zwei Entitäten namens "Supplier" und "State". Die Entität "Supplier" werden die folgenden Attribute verfügen: Code, Name, Kontakt-Vorname, Nachname des Kontakts, wenden Sie sich an e-Mail-Adresse, Adresszeile, Ort, Bundesland, PLZ und Land. Finden Sie unter [Attribute (Master Data Services)](https://msdn.microsoft.com/library/ee633745.aspx) Weitere Informationen zu Attributen in der Regel. Die Attribute "Code" und "Name" entsprechen den Spalten "SupplierID" und "Supplier Name" in der Excel-Datei "Cleansed and Matched Suppliers".  
  
 Ein domänenbasiertes Attribut weist Werte auf, die mit Elementen einer anderen Entität aufgefüllt werden. Domänenbasierte Attribute verhindern, dass Benutzer ungültige Attributwerte eingeben. Ein Attributwert kann nur aus der Dropdownliste ausgewählt werden, die von einer anderen Entität aufgefüllt wird. In diesem Lernprogramm ist das Attribut "State" der Entität "Supplier" ein domänenbasiertes Attribut mit Werten aus der Entität "State". Sie können den Wert des Attributs "State" der Entität "Supplier" nur in einen der Werte in der Entität "State" ändern. Finden Sie unter [domänenbasierte Attribute](../master-data-services/domain-based-attributes-master-data-services.md) Weitere Details.  
  
 Eine abgeleitete Hierarchie in MDS wird von der domänenbasierten Attributbeziehung im Modell abgeleitet. In diesem Lernprogramm erstellen Sie eine abgeleitete Hierarchie zwischen der Entität "Supplier" und der Entität "State". Nachdem Sie die abgeleitete Hierarchie erstellt habe, wird eine Liste von Bundesstaaten im Browser von Master Data Manager angezeigt. Wenn Sie in der Liste auf einen Bundesstaat klicken, werden die Lieferanten in diesem Bundesstaat im rechten Bereich angezeigt. Sie werden später eine abgeleitete Hierarchie auf Grundlage dieser Beziehung erstellen. Finden Sie unter [abgeleitete Hierarchien](../master-data-services/derived-hierarchies-master-data-services.md) Weitere Details.  
  
 Sie haben eine Wissensdatenbank in DQS erstellt und verwendet, um Lieferantendaten zu bereinigen und abzugleichen; die Ergebnisse haben Sie in der Datei "Cleansed and Matched Supplier Data.xls" gespeichert. In dieser Lektion laden Sie die bereinigten und abgeglichenen Daten in MDS hoch. DQS enthält nur Informationen zu den Daten (Metadaten), während MDS die Daten selbst speichert (Mastersatz). Zum Beispiel: DQS enthält Informationen über mehrere Lieferanten, aber MDS verwaltet nur die Lieferanten, die ein Unternehmen verwendet.  
  
 In dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
1.  Erstellen der **Lieferanten** Modell **MDS** mithilfe der **Master Data Manager-Webanwendung**.  
  
2.  Open **Cleansed and Matched Supplier Data.xls** in Excel, und Verwenden der **MDS-Add-in für Excel** auf eine Entität namens **Lieferanten** und die Daten in MDS hochzuladen.  
  
3.  Stellen Sie sicher, dass die Daten in MDS, mithilfe erstellt werden der **Master Data Manager**.  
  
4.  Erstellen Sie eine Entität mit dem Namen **Zustand** und aktualisieren Sie die **Zustand** Attribut **Lieferanten** Entität ein domänenbasiertes Attribut abhängig sein der **Zustand** Entität. Erreichen Sie diese alle mit der **MDS-Add-in für Excel**.  
  
5.  Stellen Sie sicher, dass das domänenbasierte Attribut erstellt wird **Master Data Manager** und aktualisieren Sie die Werte für die **Namen** Attribut der **Zustand** Entität.  
  
6.  Anzeigen der Updates, die Sie vorgenommen, mithilfe von haben **Master Data Manager** in **Excel**.  
  
7.  Laden Sie Werte aus der **Zustand** Entität in **Excel** und fügen Sie einen Wert aus, und überprüfen Sie die Hinzufügung mithilfe **Master Data Manager**.  
  
8.  Erstellen und verwenden eine abgeleitete Hierarchie mithilfe der domänenbasierten attributbeziehung zwischen der **Lieferanten** Entität und die **Zustand** Entität (dem Statusattribut von der Entität "Supplier" ist vom Typ State-Entität ) mithilfe von **Master Data Manager**.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 1: Erstellen des Modells ' Suppliers ', die mit Master Data Manager](../../2014/tutorials/task-1-creating-suppliers-model-using-master-data-manager.md)  
  
  
