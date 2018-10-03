---
title: 'Schritt 5: Hinzufügen und Konfigurieren der Flatfilequelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3417579b121d4680b18cfd896bb3ddd676eca920
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600448"
---
# <a name="lesson-1-5---adding-and-configuring-the-flat-file-source"></a>Lektion 1-5: Hinzufügen und Konfigurieren der Flatfilequelle
In dieser Aufgabe fügen Sie Ihrem Paket eine Flatfilequelle hinzu und konfigurieren sie. Eine Flatfilequelle ist eine Datenflusskomponente, die Metadaten verwendet, die durch einen Flatfile-Verbindungs-Manager definiert werden, um das Format und die Struktur der Daten anzugeben, die aus der Flatfile durch einen Transformationsprozess extrahiert werden. Die Flatfilequelle kann zum Extrahieren von Daten aus einer einzigen Flatfile konfiguriert werden, indem die Dateiformatdefinition verwendet wird, die durch den Flatfile-Verbindungs-Manager zur Verfügung gestellt wird.  
  
Für dieses Lernprogramm konfigurieren Sie die Flatfilequelle zum Verwenden des **Sample Flat File Source Data** -Verbindungs-Managers, den Sie vorher erstellt haben.  
  
### <a name="to-add-a-flat-file-source-component"></a>So fügen Sie eine Flatfilequellen-Komponente hinzu  
  
1.  Öffnen Sie den **Datenfluss** -Designer, indem Sie entweder auf den **Extract Sample Currency Data** -Datenflusstask doppelklicken, oder indem Sie auf die Registerkarte **Datenfluss**klicken.  
  
2.  Erweitern Sie in der **SSIS-Toolbox**die Option **Weitere Quellen**, und ziehen Sie anschließend **Flatfilequelle** auf die Entwurfsoberfläche der Registerkarte **Datenfluss** .  
  
3.  Klicken Sie auf der **Datenfluss** -Entwurfsoberfläche mit der rechten Maustaste auf die neu hinzugefügte **Flatfilequelle**, klicken Sie auf **Umbenennen**, und ändern Sie den Namen zu **Extract Sample Currency Data**.  
  
4.  Doppelklicken Sie auf die Flatfilequelle, um das Dialogfeld Quellen-Editor für Flatfiles zu öffnen.  
  
5.  Wählen Sie im Feld **Verbindungs-Manager für Flatfiles** den Eintrag **Sample Flat File Source Data**aus.  
  
6.  Klicken Sie auf **Spalten** , und überprüfen Sie, ob die Namen der Spalten ordnungsgemäß sind.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie mit der rechten Maustaste auf die Flatfilequelle, und klicken Sie auf **Eigenschaften**.  
  
9. Überprüfen Sie im Eigenschaftenfenster, ob die **LocaleID** -Eigenschaft auf **Englisch (USA)** festgelegt ist.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
[Schritt 6: Hinzufügen und Konfigurieren von Suchtransformationen](../integration-services/lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Flatfilequelle](../integration-services/data-flow/flat-file-source.md)  
[Verbindungs-Manager-Editor für Flatfiles &#40;Seite „Allgemein“&#41;](../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md)  
  
  
  
