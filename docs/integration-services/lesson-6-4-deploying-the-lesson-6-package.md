---
title: 'Schritt 4: Bereitstellen des Pakets aus Lektion 6 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: b613cef7-7993-4d89-a429-a8251d74d435
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2a16cd38eef12584f8d876e610bfda5d602c3076
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "71283014"
---
# <a name="lesson-6-4-deploy-the-lesson-6-package"></a>Lektion 6.4: Bereitstellen des Pakets aus Lektion 6

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Zum Bereitstellen des Pakets muss das Paket dem SSISDB-Katalog in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in einer SQL Server-Instanz hinzugefügt werden. In dieser Lektion werden Sie dem SSISDB-Katalog das Paket aus Lektion 6 hinzufügen, den neuen Parameter festlegen und das Paket ausführen. Für diese Lektion werden Sie mithilfe von SQL Server Management Studio dem SSISDB-Katalog das Paket aus Lektion 6 hinzufügen und das Paket bereitstellen. Nach dem Bereitstellen des Pakets, ändern Sie den Parameter, um auf einen neuen Speicherort zu verweisen, und führen dann das Paket aus.   
Diese Aufgabe umfasst folgende Schritte:  

1. Hinzufügen des Pakets zum SSISDB-Katalog im SSIS-Knoten in SQL Server.  
  
2. Bereitstellen des Pakets.  
  
3. Festlegen des Paketparameterwerts.  

4. Ausführen des Pakets in SSMS.  
  
## <a name="locate-or-add-the-ssisdb-catalog"></a>Suchen oder Hinzufügen des SSISDB-Katalogs  
  
1.  Wählen Sie **Start** > **Programme** > **Microsoft SQL Server 2017** und dann **SQL Management Studio** aus.  
  
2.  Überprüfen Sie im Dialogfeld **Mit Server verbinden** die Standardeinstellungen, und wählen Sie dann **Verbinden** aus. Damit die Verbindung hergestellt werden kann, muss der Name des **Servers** den Namen des Computers enthalten, auf dem SQL Server installiert ist. Wenn es sich bei der **Datenbank-Engine** um eine benannte Instanz handelt, muss im Namen des **Servers** der Instanzname im Format *\<Computername>\\\<Instanzname>* enthalten sein. 
  
3.  Erweitern Sie im **Objekt-Explorer** **Integration Services-Kataloge**.  
  
4.  Wenn unter **Integration Services-Kataloge** keine Kataloge aufgeführt sind, fügen Sie den SSISDB-Katalog hinzu.  
  
5.  Um den SSISDB-Katalog hinzuzufügen, klicken Sie mit der rechten Maustaste auf **Integration Services-Kataloge**, und wählen Sie dann **Katalog erstellen** aus.  
  
6.  Klicken Sie im Dialogfeld **Katalog erstellen** auf **CLR-Integration aktivieren**.  
  
7.  Geben Sie im Feld **Kennwort** ein Kennwort ein, und geben Sie es erneut im Feld **Kennwort erneut eingeben** ein. 
  
8.  Klicken Sie auf **OK**, um den SSISDB-Katalog hinzuzufügen.  
  
## <a name="add-the-package-to-the-ssisdb-catalog"></a>Hinzufügen des Pakets zum SSISDB-Katalog  
  
1.  Klicken Sie im **Objekt-Explorer** mit der rechten Maustaste auf **SSISDB**, und wählen Sie **Ordner erstellen** aus.  
  
2.  Geben Sie im Dialogfeld **Ordner erstellen** in das Feld „Ordnername“ den Namen „SSIS-Tutorial“ ein, und klicken Sie auf **OK**.  
  
3.  Erweitern Sie den Ordner **SSIS-Tutorial**, klicken Sie mit der rechten Maustaste auf **Projekte** und dann auf **Pakete importieren**.  
  
4.  Klicken Sie auf der Seite **Einführung**des**Assistenten zum Konvertieren von Integration Services-Projekten** auf **Weiter**.  
  
5.  Stellen Sie auf der Seite **Pakete suchen** sicher, dass das **Dateisystem** in der Liste **Quelle** ausgewählt ist, und klicken Sie auf **Durchsuchen**.  
  
6.  Navigieren Sie im Dialogfeld **Nach Ordner suchen** zum Ordner mit dem Projekt „SSIS-Tutorial“, und klicken Sie dann auf **OK**.  
  
7.  Wählen Sie **Weiter** aus.  
  
8.  Auf der Seite „Pakete auswählen“ sollten alle sechs Pakete aus dem SSIS-Tutorial angezeigt werden. Wählen Sie in der Liste **Pakete** die Datei **Lesson 6.dtsx** aus, und klicken Sie dann auf **Weiter**.  
  
9. Geben Sie auf der Seite **Ziel auswählen** in das Feld **Projektname** **SSIS-Tutorialbereitstellung** ein, und klicken Sie auf **Weiter**.

10. Klicken Sie auf jeder der verbleibenden Seiten des Assistenten auf **Weiter**, bis Sie zur Seite **Überprüfung** gelangen.  
  
11. Klicken Sie auf der Seite **Überprüfung** auf **Konvertieren**.  
  
12. Klicken Sie nach der Konvertierung auf **Schließen**.  
  
Wenn Sie den Assistenten zum Konvertieren von Integration Services-Projekten schließen, zeigt SSIS den Bereitstellungs-Assistenten für Integration Services an. Verwenden Sie diesen Assistenten jetzt zur Bereitstellung des Pakets aus Lektion 6.  
  
1.  Überprüfen Sie auf der Seite **Einführung** des **Bereitstellungs-Assistenten für Integration Services** die Schritte zum Bereitstellen des Projekts, und klicken Sie dann auf **Weiter**.  
  
2.  Stellen Sie auf der Seite **Ziel auswählen** sicher, dass der Servername der SQL Server-Instanz mit dem SSISDB-Katalog entspricht und dass der Pfad **SSIS-Tutorialbereitstellung** zeigt. Klicken Sie dann auf **Weiter**.  
  
3.  Überprüfen Sie auf der Seite **Überprüfung** die **Zusammenfassung**, und klicken Sie auf **Bereitstellen**.  
  
4.  Wenn die Bereitstellung abgeschlossen ist, klicken Sie auf **Schließen**.  
  
5.  Klicken Sie mit der rechten Maustaste im **Objekt-Explorer** auf **Integration Services-Kataloge** und dann auf **Aktualisieren**.  
  
6.  Erweitern Sie **Integration Services-Kataloge** und dann **SSISDB**. Klappen Sie die Struktur unter **SSIS-Tutorial** soweit auf, bis Sie das Projekt vollständig erweitert haben. Unter dem Knoten **Pakete** des Knotens **SSIS-Tutorialbereitstellung** sollte **Lesson 6.dtsx** angezeigt werden.  
  
7.  Um sicherzustellen, dass das Paket abgeschlossen ist, klicken Sie mit der rechten Maustaste auf **Lesson 6.dtsx** und wählen dann **Konfigurieren** aus. Wählen Sie im Dialogfeld **Konfigurieren** die Option **Parameter** aus, und überprüfen Sie, ob es einen Eintrag mit **Lesson 6.dtsx** als **Container**, **VarFolderName** als **Name** und dem Pfad zu **Neue Beispieldaten** als Wert vorhanden ist. Klicken Sie dann auf **Schließen**.  
  
## <a name="create-and-populate-a-new-sample-data-folder"></a>Erstellen und Füllen eines neuen Beispieldatenordners  
  
1.  Erstellen Sie im **Windows-Explorer** im Stammverzeichnis Ihres Laufwerks (beispielsweise **C:\\** ) einen neuen Ordner mit dem Namen **Beispieldaten Zwei**.  
  
2.  Öffnen Sie den Ordner **Beispieldaten** aus [Lektion 1 – Voraussetzungen](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites), und kopieren Sie alle drei Beispieldateien.  
  
3.  Navigieren Sie zum Ordner **Beispieldaten Zwei**, und fügen Sie die kopierten Dateien ein.  
  
## <a name="change-the-package-parameter-to-point-to-the-new-sample-data"></a>Ändern des Paketparameters für den Verweis auf die neuen Beispieldaten  
  
1.  Klicken Sie im **Objekt-Explorer** mit der rechten Maustaste auf **Lesson 6.dtsx** und wählen dann **Konfigurieren** aus.  
  
2.  Ändern Sie im Dialogfeld **Konfigurieren** den Parameterwert in den Pfad zu **Beispieldaten Zwei** (z.B. **C:\\Beispieldaten Zwei**).  
  
3.  Klicken Sie auf **OK**, um das Dialogfeld **Konfigurieren** zu schließen.  
  
## <a name="test-the-lesson-6-package-deployment"></a>Testen der Bereitstellung des Pakets aus Lektion 6  
  
1.  Klicken Sie im **Objekt-Explorer** mit der rechten Maustaste auf **Lesson 6.dtsx** und wählen dann **Ausführen** aus.  
  
2.  Klicken Sie im Dialogfeld **Paket ausführen** auf **OK**.  
  
3.  Klicken Sie in der angezeigten Meldung auf **Ja**, um den **Übersichtsbericht** zu öffnen.  
  
Der **Übersichtsbericht** für das Paket wird mit dem Namen des Pakets und einer Statuszusammenfassung angezeigt. Im Abschnitt **Übersicht über die Ausführung** wird das Ergebnis jeder Aufgabe im Paket angezeigt. Der Abschnitt **Verwendete Parameter** enthält die Namen und Werte aller Parameter, die bei der Ausführung des Pakets verwendet werden, einschließlich **VarFolderName**.  
  
