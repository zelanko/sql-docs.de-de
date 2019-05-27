---
title: XML-Editor (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.editorxml.f1
- sql12.swb.xmleditor.f1
- vs.xmleditor
- sql12.swb.editor.xml.f1
helpviewer_keywords:
- XML Designer [SQL Server Management Studio]
ms.assetid: 0824a5ce-e67b-4b53-98d9-d371faf2d23c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 28d0de4233147ae0a0dd5f0874d281a4697d93d0
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66063201"
---
# <a name="xml-editor-sql-server-management-studio"></a>XML-Editor (SQL Server Management Studio)
  Stellt eine Anzahl visueller Tools zur Arbeit mit XML-Schemas, ADO.NET-Datasets und XML-Dokumenten bereit. Der XML-Designer unterstützt die vom World Wide Web Consortium (W3C) definierte XSD-Sprache (XML Schema Definition). DTDs (Document Type Definitions) oder andere XML-Schemasprachen, wie XDR (XML-Data Reduced), werden vom Designer nicht unterstützt.  
  
 Fügen Sie zum Anzeigen des Designers ein Dataset, XML-Schema oder eine XML-Datei dem Projekt hinzu, oder öffnen Sie einen der in der folgenden Tabelle aufgeführten Dateitypen.  
  
> [!CAUTION]  
>  Bei der Arbeit in der Schemasicht steht kein Befehl **Rückgängig** zur Verfügung. Planen Sie die Arbeit sorgfältig, und speichern Sie die Dateien regelmäßig.  
  
 Für die Arbeit an XML-Dateien, XML-Schemas und Datasets stehen im Designer die folgenden drei Sichten (oder Modi) zur Verfügung:  
  
|Sicht|Description|Unterstützte Dateitypen|  
|----------|-----------------|--------------------------|  
|**Schema**|Zum visuellen Erstellen und Ändern von XML-Schemas und ADO.NET-Datasets.|*.xsd|  
|**Daten**|Zum visuellen Ändern von XML-Datendateien in einem strukturierten Datenraster.|*.xml|  
|**XML**|Zum Bearbeiten von XML. Der Quellen-Editor stellt Funktionen wie Farbcodierung und IntelliSense bereit, einschließlich Wort vervollständigen und Member auflisten.|.xml .xsd .xslt .wsdl.web.resx.tdl.wsf.hta.disco.vsdisco.config|  
|**Showplan**|Zeigt mithilfe der Option SET SHOWPLAN_XML ON erstellte XML-Abfragepläne an.|*.showplan|  
  
## <a name="schema-view"></a>Schemasicht  
 Die Schemasicht bietet eine visuelle Darstellung der Elemente, Attribute, Typen usw., aus denen XML-Schemas und ADO.NET-Datasets bestehen.  
  
 In der Schemasicht können Sie Schemas und Datasets erstellen, indem Sie Elemente entweder aus der Toolbox der Registerkarte XML-Schema oder aus dem Server-Explorer per Drag und Drop auf die Entwurfsoberfläche ziehen. Darüber hinaus können Sie Elemente zum Designer hinzufügen, indem Sie mit der rechten Maustaste auf die Entwurfsoberfläche klicken und aus dem Kontextmenü die Option Hinzufügen auswählen.  
  
 In der Schemasicht können Sie folgende Aktionen ausführen:  
  
-   Vorhandene XML-Schemas und ADO.NET-Datasets erstellen und ändern  
  
-   Beziehungen zwischen Tabellen erstellen und bearbeiten  
  
-   Schlüssel erstellen und bearbeiten  
  
-   ADO.NET-Datasets aus XML-Schemas generieren  
  
> [!NOTE]  
>  Das Layout der Elemente in der Schemasicht wird in der XSX-Datei gespeichert. Sie können die Datei anzeigen, indem Sie auf der Symbolleiste Projektmappen-Explorer auf **Alle Dateien anzeigen** klicken und dann die XSD-Datei erweitern. Wenn keine XSX-Datei vorhanden ist, bedeutet dies, dass die XSD-Datei zuvor noch nie im XML-Designer geöffnet wurde.  
  
### <a name="customizing-schema-view"></a>Anpassen der Schemasicht  
 Mithilfe der folgenden Funktionen können Sie das visuelle Layout der Elemente in der Schemasicht ändern:  
  
-   Zoomen  
  
-   Erweitern oder Reduzieren verschachtelter Elemente  
  
-   Automatisches Anordnen des Layouts der Elemente  
  
-   Wiederherstellen des Standardstatus der reduzierten Elemente  
  
##### <a name="to-expand-hidden-nested-elements"></a>So erweitern Sie ausgeblendete verschachtelte Elemente  
  
-   Klicken Sie auf das Plussymbol unten am Element.  
  
##### <a name="to-collapse-nested-elements"></a>So reduzieren Sie verschachtelte Elemente  
  
-   Klicken Sie auf das Minussymbol für das am weitesten unten gelegene Element, das im Designer angezeigt werden soll.  
  
## <a name="data-view"></a>Datensicht  
 Die Datensicht bietet einen Datenraster, der zum Ändern von XML-Dateien verwendet werden kann. In der Datensicht kann nur der Inhalt (nicht jedoch die Struktur und die Tags) einer XML-Datei bearbeitet werden.  
  
 Es gibt zwei separate Bereiche in der Datensicht: **Datentabellen** und **Daten**. Der Bereich **Datentabellen** stellt eine Liste der in der XML-Datei definierten Beziehungen in der Reihenfolge ihrer Verschachtelung (von außen nach innen) dar. Der Bereich **Daten** ist ein Datenraster, das Daten basierend auf der Auswahl im Bereich Datentabellen anzeigt.  
  
> [!NOTE]  
>  Neu erstellte XML-Dateien enthalten keine Daten und können daher in der Datensicht nicht angezeigt werden. Es gibt auch einige Instanzen von XML-Dokumenten, bei denen die Datensicht nicht aufgerufen werden kann. Selbst der XML-Code wohlgeformt, werden würde, wenn sie nicht strukturierte Daten ist möchten, wechseln Sie auf Daten Ansicht die folgende Meldung generiert: "Obwohl dieses Dokument wohlgeformt ist, enthält es-Struktur, die Datenansicht anzeigen kann."  
  
 In der Datensicht können Sie folgende Aktionen ausführen:  
  
-   Manuell Datentabellen auffüllen  
  
-   Vorhandene Datentabellen bearbeiten  
  
-   Ein XML-Schema aus einem XML-Dokument generieren  
  
## <a name="xml-view"></a>XML-Ansicht  
 Die XML-Ansicht bietet einen Editor zum Bearbeiten von Roh-XML sowie darüber hinaus IntelliSense und Farbcodierung. Bei der Arbeit an XSD- und XML-Dateien mit zugehörigem Schema steht der Anweisungsabschluss zur Verfügung. Typ \< initiieren Sie ein Tag, und Sie wird mit einer Liste von Elementen, die an dieser Stelle gültig sind angezeigt werden. Nachdem Sie den Elementnamen eingegeben und die LEERTASTE gedrückt haben, wird Ihnen eine Liste mit Attributen vorgeschlagen, die von dem Element unterstützt werden.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense stehen auf der Symbolleiste nicht zur Verfügung. Wenn Sie im XML-Editor auf die Optionen zugreifen möchten, klicken Sie im Menü **Bearbeiten** auf **IntelliSense**.  
  
## <a name="showplan-view"></a>SHOWPLAN-Sicht  
 Abfragepläne können im XML-Format gespeichert werden, wenn sie mithilfe der Option SET SHOWPLAN_XML ON erstellt wurden. Doppelklicken Sie auf eine Datei mit der Erweiterung .showplan, um den Abfrageplan zu öffnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Speichern eines Ausführungsplans im XML-Format](../performance/save-an-execution-plan-in-xml-format.md)  
  
  
