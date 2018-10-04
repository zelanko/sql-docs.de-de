---
title: 'Schritt 5: Hinzufügen und Konfigurieren der Flatfilequelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4037b33f1668333d54f160eade5f5ad24c4dffe6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134800"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a>Schritt 5: Hinzufügen und Konfigurieren der Flatfilequelle
  In dieser Aufgabe fügen Sie Ihrem Paket eine Flatfilequelle hinzu und konfigurieren sie. Eine Flatfilequelle ist eine Datenflusskomponente, die Metadaten verwendet, die durch einen Flatfile-Verbindungs-Manager definiert werden, um das Format und die Struktur der Daten anzugeben, die aus der Flatfile durch einen Transformationsprozess extrahiert werden. Die Flatfilequelle kann zum Extrahieren von Daten aus einer einzigen Flatfile konfiguriert werden, indem die Dateiformatdefinition verwendet wird, die durch den Flatfile-Verbindungs-Manager zur Verfügung gestellt wird.  
  
 In diesem Tutorial konfigurieren Sie die Flatfilequelle zum Verwenden der `Sample Flat File Source Data` Verbindungs-Manager, die Sie zuvor erstellt haben.  
  
### <a name="to-add-a-flat-file-source-component"></a>So fügen Sie eine Flatfilequellen-Komponente hinzu  
  
1.  Öffnen der **Datenfluss** -Designer, entweder durch Doppelklicken auf die `Extract Sample Currency Data` Datenflusstask oder durch Klicken auf die **Registerkarte Datenfluss**.  
  
2.  Erweitern Sie in der **SSIS-Toolbox**die Option **Weitere Quellen**, und ziehen Sie anschließend **Flatfilequelle** auf die Entwurfsoberfläche der Registerkarte **Datenfluss** .  
  
3.  Auf der **Datenfluss** Entwurfsoberfläche zum Entwickeln der rechten Maustaste auf die neu hinzugefügte **Flat File Source**, klicken Sie auf **umbenennen**, und ändern Sie den Namen in `Extract Sample Currency Data`.  
  
4.  Doppelklicken Sie auf die Flatfilequelle, um das Dialogfeld Quellen-Editor für Flatfiles zu öffnen.  
  
5.  In der **Flatfile-Verbindungs-Manager** Kontrollkästchen `Sample Flat File Source Data`.  
  
6.  Klicken Sie auf **Spalten** , und überprüfen Sie, ob die Namen der Spalten ordnungsgemäß sind.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie mit der rechten Maustaste auf die Flatfilequelle, und klicken Sie auf **Eigenschaften**.  
  
9. Überprüfen Sie im Eigenschaftenfenster, ob die `LocaleID` -Eigenschaftensatz auf **Englisch (Vereinigte Staaten)**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Schritt 6: Hinzufügen und Konfigurieren von Suchtransformationen](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Flatfile-Datenquelle](data-flow/flat-file-source.md)   
 [Verbindungs-Manager-Editor für Flatfiles &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)  
  
  
