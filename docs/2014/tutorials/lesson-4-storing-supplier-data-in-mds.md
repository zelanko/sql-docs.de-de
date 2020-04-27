---
title: 'Lektion 4: Speichern von Lieferantendaten in MDS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: bacd9eaf-4d12-4f25-aec7-d785dec1b623
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 678a7d6ce075e6a1082856aa7962bb3f6eec522d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65489710"
---
# <a name="lesson-4-storing-supplier-data-in-mds"></a>Lektion 4: Speichern von Lieferantendaten in MDS
  Master Data Services (MDS) sind die SQL Server-Lösung für die Masterdatenverwaltung. Master Data Management (MDM) beschreibt die Anstrengungen einer Organisation, nicht transaktionale Listen mit Daten zu ermitteln und zu definieren.  
  
 Modelle stellen die höchste Organisationsebene in Master Data Services dar und organisieren die Struktur der Masterdaten. Eine MDS-Implementierung kann ein oder viele Modelle aufweisen, wobei jedes Modell ähnliche Daten gruppiert. Die Masterdaten werden im Allgemeinen in vier Kategorien unterteilt: Personen, Orte, Gegenstände oder Begriffe. Sie können z. B. ein Produktmodell erstellen, das produktbezogene Daten enthält, oder ein Kundenmodell, das kundenbezogene Daten enthält. Weitere Informationen finden Sie unter [Models (Master Data Services)](https://msdn.microsoft.com/library/ee633746.aspx) .  
  
 Ein Modell kann eine oder mehrere Entitäten enthalten. Jede Entität hat Attribute (Spalten) und Elemente (Zeilen). Die Zeilen enthalten die Masterdaten. In dieser Lektion erstellen Sie ein Lieferantenmodell (Suppliers) mit zwei Entitäten namens "Supplier" und "State". Die Entität "Supplier" verfügt über die folgenden Attribute: Code, Name, Kontakt-Vorname, Kontakt-Nachname, Kontakt-E-Mail-Adresse, Adresszeile, Ort, Bundesland, PLZ und Land. Weitere Informationen zu Attributen finden Sie unter [Attribute (Master Data Services)](https://msdn.microsoft.com/library/ee633745.aspx) . Die Attribute "Code" und "Name" entsprechen den Spalten "SupplierID" und "Supplier Name" in der Excel-Datei "Cleansed and Matched Suppliers".  
  
 Ein domänenbasiertes Attribut weist Werte auf, die mit Elementen einer anderen Entität aufgefüllt werden. Domänenbasierte Attribute verhindern, dass Benutzer ungültige Attributwerte eingeben. Ein Attributwert kann nur aus der Dropdownliste ausgewählt werden, die von einer anderen Entität aufgefüllt wird. In diesem Lernprogramm ist das Attribut "State" der Entität "Supplier" ein domänenbasiertes Attribut mit Werten aus der Entität "State". Sie können den Wert des Attributs "State" der Entität "Supplier" nur in einen der Werte in der Entität "State" ändern. Weitere Informationen finden Sie unter [Domänen basierte Attribute](../master-data-services/domain-based-attributes-master-data-services.md) .  
  
 Eine abgeleitete Hierarchie in MDS wird von der domänenbasierten Attributbeziehung im Modell abgeleitet. In diesem Lernprogramm erstellen Sie eine abgeleitete Hierarchie zwischen der Entität "Supplier" und der Entität "State". Nachdem Sie die abgeleitete Hierarchie erstellt habe, wird eine Liste von Bundesstaaten im Browser von Master Data Manager angezeigt. Wenn Sie in der Liste auf einen Bundesstaat klicken, werden die Lieferanten in diesem Bundesstaat im rechten Bereich angezeigt. Sie werden später eine abgeleitete Hierarchie auf Grundlage dieser Beziehung erstellen. Weitere Informationen finden Sie unter [abgeleitete Hierarchien](../master-data-services/derived-hierarchies-master-data-services.md) .  
  
 Sie haben eine Wissensdatenbank in DQS erstellt und verwendet, um Lieferantendaten zu bereinigen und abzugleichen; die Ergebnisse haben Sie in der Datei "Cleansed and Matched Supplier Data.xls" gespeichert. In dieser Lektion laden Sie die bereinigten und abgeglichenen Daten in MDS hoch. DQS enthält nur Informationen zu den Daten (Metadaten), während MDS die Daten selbst speichert (Mastersatz). Beispiel: DQS enthält Informationen über mehrere Lieferanten, aber MDS verwaltet nur die Lieferanten, die ein Unternehmen verwendet.  
  
 In dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
1.  Erstellen Sie das Modell **Suppliers** in **MDS** mithilfe der **Master Data Manager-Webanwendung**.  
  
2.  Öffnen Sie **bereinigt und übereinstimmende Lieferantendaten. xls** in Excel, und verwenden Sie die **MDS-Add-in für Excel** , um eine Entität namens **Supplier** zu erstellen und die Daten in MDS hochzuladen.  
  
3.  Überprüfen Sie, ob die Daten in MDS erstellt wurden, indem Sie die **Master Data Manager**verwenden.  
  
4.  Erstellen Sie eine Entität mit dem Namen **State** , und aktualisieren Sie das **State** -Attribut der Entität **Supplier** in Abhängigkeit von der **State** -Entität auf ein domänenbasiertes Attribut Dazu verwenden Sie die **MDS-Add-in für Excel**.  
  
5.  Überprüfen Sie, ob das Domänen basierte Attribut mit **Master Data Manager** erstellt wurde, und aktualisieren Sie die Werte für das Attribut " **Name** " der Entität " **State** ".  
  
6.  Zeigen Sie die Updates an, die Sie mithilfe **Master Data Manager** in **Excel**vorgenommen haben.  
  
7.  Laden Sie Werte aus der Entität **State** in **Excel** , und fügen Sie einen Wert hinzu, und überprüfen Sie die Addition mithilfe **Master Data Manager**.  
  
8.  Erstellen und verwenden Sie eine abgeleitete Hierarchie mithilfe der domänenbasierten Attribut Beziehung zwischen der Entität " **Supplier** " und der Entität " **State** " (das State-Attribut der Entität "Supplier" ist vom Typ "State Entity") mithilfe von **Master Data Manager**  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 1: Erstellen des Modells „Suppliers“ mit dem Master Data Manager](../../2014/tutorials/task-1-creating-suppliers-model-using-master-data-manager.md)  
  
  
