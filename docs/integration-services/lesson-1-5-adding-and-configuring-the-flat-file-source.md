---
description: 'Lektion 1.5: Hinzufügen und Konfigurieren der Flatfilequelle'
title: 'Schritt 5: Hinzufügen und Konfigurieren der Flatfilequelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfc6ffa21bf3f6c1205b1c9c667cc6e75868cece
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88390866"
---
# <a name="lesson-1-5-add-and-configure-the-flat-file-source"></a>Lektion 1.5: Hinzufügen und Konfigurieren der Flatfilequelle

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


In dieser Aufgabe fügen Sie Ihrem Paket eine Flatfilequelle hinzu und konfigurieren diese. Eine Flatfilequelle ist eine Datenflusskomponente, die vom Verbindungs-Manager für Flatfiles definierte Metadaten verwendet. Diese Metadaten geben das Format und die Struktur der Daten an, die durch einen Transformationsprozess aus der Flatfile extrahiert werden können. Die Flatfilequelle kann zum Extrahieren von Daten aus einer einzigen Flatfile konfiguriert werden, indem die Formatdefinition des Verbindungs-Managers für Flatfiles verwendet wird.  
  
Für diese Aufgabe konfigurieren Sie die Flatfilequelle zum Verwenden von der Verbindungs-Manager-Instanz **Sample Flat File Source Data** (Beispieldaten aus der Flatfilequelle), die Sie vorher erstellt haben.  
  
## <a name="add-a-flat-file-source-component"></a>Hinzufügen einer Flatfilequellenkomponente  
  
1.  Öffnen Sie den **Datenfluss**-Designer, indem Sie entweder auf den Datenflusstask **Extract Sample Currency Data** (Währungsdaten aus dem Beispiel extrahieren) doppelklicken oder auf die Registerkarte **Datenfluss** klicken.  
  
2.  Erweitern Sie in der **SSIS-Toolbox**die Option **Weitere Quellen**, und ziehen Sie anschließend **Flatfilequelle** auf die Entwurfsoberfläche der Registerkarte **Datenfluss** .  
  
3.  Klicken Sie auf der **Datenfluss**-Entwurfsoberfläche mit der rechten Maustaste auf die neu hinzugefügte **Flatfilequelle**, klicken Sie auf **Umbenennen**, und ändern Sie den Namen in **Extract Sample Currency Data** (Währungsdaten aus dem Beispiel extrahieren).  
  
4.  Doppelklicken Sie auf die Flatfilequelle, um das Dialogfeld **Quellen-Editor für Flatfiles** zu öffnen.  
  
5.  Klicken Sie im Feld **Verbindungs-Manager für Flatfiles** auf den Eintrag **Sample Flat File Source Data** (Beispieldaten aus der Flatfilequelle).  
  
6.  Klicken Sie auf **Spalten**, und überprüfen Sie, ob die Namen der Spalten richtig sind.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie erst mit der rechten Maustaste auf die Flatfilequelle, und klicken Sie anschließend auf **Eigenschaften**.  
  
9. Überprüfen Sie im Fenster **Eigenschaften**, ob die Eigenschaft **LocaleID** auf **Englisch (USA)** festgelegt ist.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Schritt 6: Hinzufügen und Konfigurieren von Suchtransformationen](../integration-services/lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>Siehe auch  
[Flatfilequelle](../integration-services/data-flow/flat-file-source.md)  
[Verbindungs-Manager für Flatfiles](../integration-services/connection-manager/flat-file-connection-manager.md)  
  
  
  
