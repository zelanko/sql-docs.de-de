---
title: 'Schritt 2: Konvertieren des Projekts in das Projektbereitstellungsmodell | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0563ceff3185f856692292884fe63e79c16e4216
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295875"
---
# <a name="lesson-6-2-convert-the-project-to-the-project-deployment-model"></a>Lektion 6.2: Konvertieren des Projekts in das Projektbereitstellungsmodell

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



In dieser Aufgabe verwenden Sie den Assistenten zum Konvertieren von Integration Services-Projekten, um das Projekt in das Projektbereitstellungsmodell zu konvertieren.  
  
1.  Wählen Sie im Menü **Projekt** die Option **Paketbereitstellungsmodell konvertieren** aus.  
  
2.  Überprüfen Sie die Schritte auf der **Einführungsseite** des **Assistenten zum Konvertieren von Integration Services-Projekten**, und klicken Sie auf **Weiter**.  
  
3.  Deaktivieren Sie auf der Seite **Pakete auswählen** in der Liste **Pakete** alle Kontrollkästchen außer **Lesson 6.dtsx**, und klicken Sie dann auf **Weiter**.  
  
4.  Klicken Sie auf der Seite **Projekteigenschaften angeben** auf **Weiter**.  
  
5.  Klicken Sie auf der Seite **Task „Paket ausführen“ aktualisieren** auf **Weiter**.  
  
6.  Stellen Sie auf der Seite **Konfigurationen auswählen** sicher, dass das Paket **Lesson 6.dtsx** in der Liste **Konfigurationen** aktiviert ist, und klicken Sie dann auf **Weiter**.  
  
7.  Stellen Sie auf der Seite **Parameter erstellen** sicher, dass das Paket **Lesson 6.dtsx** ausgewählt ist.  Achten Sie darauf, dass in der Liste **Konfigurationseigenschaften** für **Bereich** die Option **Paket** festgelegt ist, und klicken Sie dann auf **Weiter**.  
  
8.  Stellen Sie auf der Seite **Parameter konfigurieren** sicher, dass die Werte für **Name** und **Wert** demselben Namen und Wert entsprechen, den Sie in der Lektion 5 für den Variablen- und Konfigurationswert angegeben haben. Wählen Sie dann **Weiter** aus.  
  
9. Beachten Sie auf der Seite **Überprüfung** im Bereich **Zusammenfassung**, dass der Assistent die Informationen aus der Konfigurationsdatei verwendet hat, um die zu konvertierenden **Eigenschaften** festzulegen.  
  
10. Wählen Sie **Konvertieren** aus.  
  
    Nach der Konvertierung wird eine Warnmeldung angezeigt, die darauf hinweist, dass die Änderungen erst gespeichert werden, wenn Sie das Projekt speichern. Klicken Sie auf **OK**, um die Warnung zu schließen.  
  
11. Klicken Sie im **Assistent zum Konvertieren von Integration Services-Projekten** auf **Schließen**.  
  
12. Wählen Sie in **SQL Server Data Tools** im Menü **Datei** die Option **Speichern** aus, um das konvertierte Paket zu speichern.  
  
13. Wählen Sie die Registerkarte **Parameter** aus, und überprüfen Sie, ob das Paket jetzt einen Parameter für **VarFolderName** enthält. Bei diesem Parameterwert handelt es sich um denselben Pfad, der für den Ordner **Neue Beispieldaten** in der Konfigurationsdatei aus Lektion 5 angegebenen wurde.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Schritt 3: Testen des Pakets aus Lektion 6](../integration-services/lesson-6-3-testing-the-lesson-6-package.md)  
  
  
  
