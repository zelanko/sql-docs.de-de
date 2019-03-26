---
title: 'Schritt 2: Aktivieren und Konfigurieren von Paketkonfigurationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 005218ab-8dd5-48e9-a185-6bc60cd43a7a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b65e44de58e2aeea21485b1a2875fa7f00349dc5
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58271690"
---
# <a name="lesson-5-2-enable-and-configure-package-configurations"></a>Lektion 5.2: Aktivieren und Konfigurieren von Paketkonfigurationen

In dieser Aufgabe konvertieren Sie das Projekt in das Paketbereitstellungsmodell und aktivieren Paketkonfigurationen mithilfe des Paketkonfigurations-Assistenten. Sie verwenden diesen Assistenten zum Generieren einer XML-Konfigurationsdatei, die Konfigurationseinstellungen für die **Directory**-Eigenschaft des Foreach-Schleifencontainers enthält. Der Wert der **Directory**-Eigenschaft wird durch eine neue Variable auf Paketebene bereitgestellt, die Sie zur Laufzeit aktualisieren können. Zudem füllen Sie einen neuen Beispieldatenordner, den Sie zum Testen verwenden.  
  
## <a name="create-a-package-level-variable-mapped-to-the-directory-property"></a>Erstellen Sie eine Variable auf Paketebene, die der Directory-Eigenschaft zugeordnet ist.  
  
1.  Wählen Sie den Hintergrund der Registerkarte **Ablaufsteuerung** im [!INCLUDE[ssIS](../includes/ssis-md.md)]-Designer aus. Durch diese Auswahl wird der Bereich für die Variable, die Sie erstellen, auf das Paket festgelegt.  
  
2.  Wählen Sie im Menü [!INCLUDE[ssIS](../includes/ssis-md.md)] den Befehl **Variablen**aus.  
  
3.  Wählen Sie im Fenster **Variablen** das Symbol **Variable hinzufügen** aus.  
  
4.  Geben Sie im Feld **Name** den Namen **varFolderName** ein.  
  
    > [!IMPORTANT]  
    > Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.  
  
5.  Überprüfen Sie, ob im Feld **Bereich** der Name des Pakets **Lesson 5** (Lektion 5) angezeigt wird.  
  
6.  Legen Sie den Wert des Felds **Datentyp** der `varFolderName` -Variable auf **String**fest.  
  
7.  Kehren Sie zur Registerkarte **Ablaufsteuerung** zurück, und doppelklicken Sie auf den **Foreach File in Folder** -Container.  
  
8.  Klicken Sie auf der Seite **Sammlung** des **Foreach-Schleifen-Editors** auf **Ausdrücke** und anschließend auf die Schaltfläche mit den Auslassungspunkten **(...)**.  
  
9. Wählen Sie im **Eigenschaftsausdrucks-Editor** in die Liste **Eigenschaft** die Option **Verzeichnis** aus.  
  
10. Klicken Sie im Feld **Ausdruck** auf die Schaltfläche mit den Auslassungspunkten **(...)**.  
  
11. Erweitern Sie im **Ausdrucks-Generator** den Ordner **Variablen und Parameter**, und ziehen Sie die Variable **User::varFolderName** in das Feld **Ausdruck**.  
  
12. Klicken Sie auf **OK**, um den **Ausdrucks-Generator** zu beenden.  
  
13. Klicken Sie auf **OK**, um den **Eigenschaftsausdrucks-Editor** zu beenden.  
  
14. Klicken Sie auf **OK**, um den **Foreach-Schleifen-Editor** zu beenden.  
  
## <a name="enable-package-configurations"></a>Paketkonfigurationen aktivieren  
  
1.  Wählen Sie im **Menü „Projekt“** die Option **In Paketbereitstellungsmodell konvertieren** aus.  
  
2.  Klicken Sie in der Warnmeldung auf **OK**, nachdem die Konvertierung abgeschlossen ist, und klicken Sie im Dialogfeld **In Paketbereitstellungsmodell konvertieren** auf **OK**.  
  
3.  Wählen Sie den Hintergrund der Registerkarte **Ablaufsteuerung** im [!INCLUDE[ssIS](../includes/ssis-md.md)]-Designer aus.  
  
4.  Wählen Sie im Menü **SSIS** die Option **Paketkonfigurationen** aus.  
  
5.  Klicken Sie im Dialogfeld **Paketkonfigurationsplaner** auf **Paketkonfigurationen aktivieren** und anschließend auf **Hinzufügen**.  
  
6.  Klicken Sie auf der Willkommensseite des **Paketkonfigurations-Assistenten** auf **Weiter**.  
  
7.  Überprüfen Sie auf der Seite **Konfigurationstyp auswählen** , ob **Konfigurationstyp** auf **XML-Konfigurationsdatei**festgelegt ist.  
  
8.  Klicken Sie auf der Seite **Konfigurationstyp auswählen** auf **Durchsuchen**.  
  
9. Das Dialogfeld **Speicherort der Konfigurationsdatei auswählen** mit dem Projektordner wird geöffnet.  
  
10. Geben Sie im Dialogfeld **Speicherort der Konfigurationsdatei auswählen** als **Dateinamen** **SSISTutorial**ein, und klicken Sie auf **Speichern**.  
  
11. Klicken Sie auf der Seite **Konfigurationstyp auswählen** auf **Weiter**.
  
12. Erweitern Sie **Variablen** auf der Seite **Eigenschaften für den Exportvorgang auswählen** im Bereich **Objekte**, erweitern Sie **varFolderName** und **Eigenschaften**, und wählen Sie anschließend **Wert**aus.  
  
13. Klicken Sie auf der Seite **Eigenschaften für den Exportvorgang auswählen** auf **Weiter**.  
  
14. Geben Sie auf der Seite **Assistenten abschließen** einen Konfigurationsnamen für die Konfiguration ein, beispielsweise **SSIS Tutorial Directory configuration**. Der Konfigurationsname wird im Dialogfeld **Paketkonfigurationsplaner** angezeigt.  
  
15. Wählen Sie **Fertig stellen** aus.  
  
16. Klicken Sie auf **Schließen**.  
  
17. Vom Assistenten wird eine Konfigurationsdatei mit dem Namen **SSISTutorial.dtsConfig** erstellt, die die Konfigurationseinstellungen für den Wert **Value** der Variablen enthält, durch die wiederum die **Directory**-Eigenschaft des Enumerators festgelegt wird.  
  
    > [!NOTE]  
    > Eine Konfigurationsdatei enthält typischerweise komplexe Informationen zu den Paketeigenschaften. In diesem Tutorial sollte die einzige Konfigurationsinformation allerdings Folgende sein:

    ```
    <Configuration 
        ConfiguredType="Property"  
        Path="\Package.Variables[User::varFolderName].Properties[Value]" 
        ValueType="String">  
      <ConfiguredValue></ConfiguredValue>  
    </Configuration>
    ```
  
## <a name="create-and-populate-a-new-sample-data-folder"></a>Erstellen und Füllen eines neuen Beispieldatenordners  
  
1.  Erstellen Sie im Windows-Explorer im Stammverzeichnis Ihres Laufwerks (beispielsweise **C:\\**) einen Ordner mit dem Namen **Neue Beispieldaten**.  
  
2.  Suchen Sie die Beispieldateien auf dem Computer, und kopieren Sie drei der Dateien aus dem Ordner.  
  
3.  Fügen Sie die kopierten Dateien in den Ordner **Neue Beispieldaten** ein.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe  
[Schritt 3: Ändern des Directory-Eigenschaftskonfigurationswerts](../integration-services/lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
