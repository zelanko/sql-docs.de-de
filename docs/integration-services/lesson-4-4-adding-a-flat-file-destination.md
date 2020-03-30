---
title: 'Schritt 4: Hinzufügen eines Flatfileziels | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ae02b9188ecc9917d26532633e4d5a253d4f326b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "71295947"
---
# <a name="lesson-4-4-add-a-flat-file-destination"></a>Lektion 4.4: Hinzufügen eines Flatfileziels

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Die Fehlerausgabe der Lookup Currency Key-Transformation leitet alle Datenzeilen, für die beim Suchvorgang keine Übereinstimmung gefunden wurde, zum Skripttransformationsvorgang um. Um mehr Informationen zu den aufgetretenen Fehlern bereitzustellen, führt die Skripttransformation ein Skript aus, mit dem die Beschreibung jedes Fehlers abgerufen wird.  
  
In dieser Aufgabe speichern Sie alle Informationen zu den fehlerhaften Zeilen zur späteren Verarbeitung in einer durch Trennzeichen getrennten Textdatei. Um die fehlerhaften Zeilen zu speichern, fügen Sie einen Flatfile-Verbindungs-Manager für die Textdatei, die die Fehlerdaten enthält, sowie ein Flatfileziel hinzu und konfigurieren diese. Durch Festlegen von Eigenschaften im Verbindungs-Manager für Flatfiles, der vom Flatfileziel verwendet wird, können Sie angeben, wie das Flatfileziel die Textdatei formatiert und schreibt. Weitere Informationen finden Sie unter [Verbindungs-Manager für Flatfiles](../integration-services/connection-manager/flat-file-connection-manager.md) und [Flatfileziel](../integration-services/data-flow/flat-file-destination.md).  
  
## <a name="add-and-configure-a-flat-file-destination"></a>Hinzufügen und Konfigurieren eines Flatfileziels  
  
1.  Klicken Sie auf die Registerkarte **Datenfluss**.  
  
2.  Erweitern Sie in der **SSIS-Toolbox** die Option **Weitere Ziele**, und ziehen Sie **Flatfileziel** auf die Datenfluss-Entwurfsoberfläche. Setzen Sie das **Flatfileziel** direkt unter die **Get Error Description** -Transformation.  
  
3.  Wählen Sie die Transformation **Get Error Description** (Fehlerbeschreibung abrufen) aus, und ziehen Sie anschließend den blauen Pfeil auf das neue **Flatfileziel**.  
  
4.  Wählen Sie auf der **Datenfluss**-Entwurfsoberfläche den Namen **Flatfileziel** in der neuen Transformation **Flatfileziel** aus, und ändern Sie den Namen in **Failed Rows** (Fehlerhafte Zeilen).  
  
5.  Klicken Sie mit der rechten Maustaste auf die Transformation **Failed Rows** (Fehlerhafte Zeilen), wählen Sie **Bearbeiten** und anschließend im **Ziel-Editor für Flatfiles** die Option **Neu** aus.  
  
6.  Überprüfen Sie im Dialogfeld **Flatfileformat**, ob **Mit Trennzeichen** ausgewählt ist, und wählen Sie anschließend **OK** aus.  
  
7.  Geben Sie im **Verbindungs-Manager-Editor für Flatfiles** im Feld **Name des Verbindungs-Managers** die Zeichenfolge *Error Data* (Fehlerdaten) ein.  
  
8.  Wählen Sie im Dialogfeld **Verbindungs-Manager-Editor für Flatfiles** die Option **Durchsuchen** aus, und suchen Sie den Ordner, in dem die Datei gespeichert werden soll.  
  
9. Geben Sie im Dialogfeld **Öffnen** für **Dateiname** den Namen *ErrorOutput.txt* ein, und wählen Sie anschließend **Öffnen** aus.  
  
10. Überprüfen Sie im Dialogfeld **Verbindungs-Manager-Editor für Flatfiles**, ob **Gebietsschema** auf **Englisch (USA)** und **Codepage** auf **1252 (ANSI-Latin I)** festgelegt ist.  
  
11. Wählen Sie im Optionsbereich **Spalten** aus.  
  
    Zusätzlich zu den Spalten aus der Quelldatendatei sind drei neue Spalten vorhanden: ErrorCode, ErrorColumn und ErrorDescription. Diese Spalten sind die Fehlerausgabe der Lookup Currency Key-Transformation und des Skripts in der Get Error Description-Transformation (Fehlerbeschreibung abrufen). Sie können diese Spalten verwenden, um die Ursache für das Fehlschlagen der Zeile zu beheben.  
  
12. Klicken Sie auf **OK**.  
  
13. Deaktivieren Sie im **Ziel-Editor für Flatfiles**das Kontrollkästchen **Daten in der Datei überschreiben** .  
  
    Wenn Sie dieses Kontrollkästchen deaktivieren, werden die Fehler durch Anfügen der Fehlerausgabe für jede neue Ausführung über mehrere Paketausführungen beibehalten.
  
14. Wählen Sie im **Ziel-Editor für Flatfiles** die Option **Zuordnungen** aus, um zu überprüfen, ob alle Spalten ordnungsgemäß sind. Optional können Sie die Spalten im Ziel umbenennen.  
  
15. Klicken Sie auf **OK**.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Schritt 5: Testen des Tutorialpakets aus Lektion 4](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  
  
