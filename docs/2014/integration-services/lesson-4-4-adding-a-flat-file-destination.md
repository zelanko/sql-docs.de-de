---
title: 'Schritt 4: Hinzufügen eines Flatfileziels | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 66533fb63a76bc92bcb45e7cb8feb058467e6583
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968186"
---
# <a name="step-4-adding-a-flat-file-destination"></a>Schritt 4: Hinzufügen eines Flatfileziels
  Die Fehlerausgabe der "Lookup Currency Key"-Transformation leitet alle Datenzeilen, für die im Suchvorgang keine Übereinstimmung gefunden wurde, zur Skripttransformation um. Um die zu den Fehlern angezeigten Informationen zu verbessern, führt die Skripttransformation ein Skript aus, mit dem die Fehlerbeschreibung abgerufen wird.  
  
 In dieser Aufgabe speichern Sie alle Informationen zu den fehlerhaften Zeilen für eine spätere Verarbeitung in einer Datei mit Trennzeichen. Um die fehlerhaften Zeilen zu speichern, müssen Sie einen Flatfile-Verbindungs-Manager für die Textdatei, die die Fehlerdaten enthalten wird, und ein Flatfileziel hinzufügen und konfigurieren. Durch Festlegen von Eigenschaften im Verbindungs-Manager für Flatfiles, der vom Flatfileziel verwendet wird, können Sie angeben, wie das Flatfileziel die Textdatei formatiert und schreibt. Weitere Informationen finden Sie unter [Verbindungs-Manager für Flatfiles](connection-manager/file-connection-manager.md) und [Flatfileziel](data-flow/flat-file-destination.md).  
  
### <a name="to-add-and-configure-a-flat-file-destination"></a>So fügen Sie ein Flatfileziel hinzu und konfigurieren es  
  
1.  Klicken Sie auf die Registerkarte **Datenfluss** .  
  
2.  Erweitern Sie in der **SSIS-Toolbox**die Option **Weitere**, und ziehen Sie **Flatfileziel** auf die Datenfluss-Entwurfsoberfläche. Setzen Sie das **Flatfileziel** direkt unter die **Get Error Description** -Transformation.  
  
3.  Klicken Sie auf die **Get Error Description** -Transformation, und ziehen Sie anschließend den grünen Pfeil auf das neue **Flatfileziel**.  
  
4.  Klicken Sie auf der **Datenfluss** -Entwurfsoberfläche in der neu hinzugefügten **Flatfileziel** -Transformation auf **Flatfileziel** , und ändern Sie den Namen in **Failed Rows**.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Transformation **Failed Rows** , klicken Sie auf **Bearbeiten**und anschließend im **Ziel-Editor für Flatfiles**auf **Neu**.  
  
6.  Überprüfen Sie im Dialogfeld **Flatfileformat** , ob **Mit Trennzeichen** ausgewählt ist, und klicken Sie anschließend auf **OK**.  
  
7.  Geben Sie im **Verbindungs-Manager-Editor für Flatfiles**im Feld Name des Verbindungs-Managers den **Namen** ein `Error Data` .  
  
8.  Klicken Sie im Dialogfeld **Verbindungs-Manager-Editor für Flatfiles** auf **Durchsuchen**, und suchen Sie den Ordner, in dem die Datei gespeichert werden soll.  
  
9. Geben Sie im Dialogfeld **Öffnen** für **Dateiname den Namen**ein `ErrorOutput.txt` , und klicken Sie dann auf **Öffnen**.  
  
10. Prüfen Sie im Dialogfeld **Verbindungs-Manager-Editor für Flatfiles** , ob das Feld **Gebietsschema** den Wert Englisch (USA) und das Feld **Codepage** den Wert 1252 (ANSI -Latin I) enthält.  
  
11. Klicken Sie im Optionen-Bereich auf **Spalten**.  
  
     Beachten Sie, dass zusätzlich zu den Spalten aus der Quelldatendatei drei neue Spalten vorhanden sind: ErrorCode, ErrorColumn und ErrorDescription. Diese Spalten werden von der Fehlerausgabe der Lookup Currency Key-Transformation und vom Skript in der Get Error Description-Transformation generiert und können dazu verwendet werden, die Ursache für das Fehlschlagen der Zeile zu beheben.  
  
12. Klicken Sie auf **OK**.  
  
13. Deaktivieren Sie im **Ziel-Editor für Flatfiles**das Kontrollkästchen **Daten in der Datei überschreiben** .  
  
     Wenn Sie dieses Kontrollkästchen deaktivieren, werden die Fehler über mehrere Paketausführungen beibehalten.  
  
14. Klicken Sie im **Ziel-Editor für Flatfiles**auf **Zuordnungen** um zu überprüfen, ob alle Spalten ordnungsgemäß sind. Optional können Sie die Spalten im Ziel umbenennen.  
  
15. Klicken Sie auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Schritt 5: Testen des Tutorialpakets aus Lektion 4](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  
