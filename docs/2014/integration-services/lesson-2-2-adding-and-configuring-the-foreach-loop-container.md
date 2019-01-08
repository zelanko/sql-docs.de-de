---
title: 'Schritt 2: Hinzufügen und Konfigurieren des Foreach-Schleifencontainer | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 88a973cc-0f23-4ecf-adb6-5b06279c2df6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2aa42ac9ab25c9765aac2afa10abdd50f2df4cb7
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360113"
---
# <a name="step-2-adding-and-configuring-the-foreach-loop-container"></a>Schritt 2: Hinzufügen und Konfigurieren des Foreach-Schleifencontainers
  In dieser Aufgabe fügen Sie die Möglichkeit zum Schleifendurchlauf für einen Ordner von Flatfiles hinzu und wenden die auch in Lektion 1 verwendete Datenflusstransformation auf jede dieser Flatfiles an. Dies geschieht durch das Hinzufügen eines Foreach-Schleifencontainers zur Ablaufsteuerung und dessen Konfigurierung.  
  
 Für den von Ihnen hinzugefügten Foreach-Schleifencontainer muss es möglich sein, eine Verbindung mit jeder Flatfile im Ordner herzustellen. Da alle Dateien im Ordner das gleiche Format aufweisen, kann vom Foreach-Schleifencontainer der gleiche Flatfile-Verbindungs-Manager zum Herstellen einer Verbindung mit jeder dieser Dateien verwendet werden. Der vom Container verwendete Flatfile-Verbindungs-Manager ist der gleiche Flatfile-Verbindungs-Manager, den Sie in Lektion 1 erstellt haben.  
  
 Zurzeit wird vom Flatfile-Verbindungs-Manager aus der Lektion 1 nur eine Verbindung mit einer bestimmten Flatfile hergestellt. Um iterativ Verbindungen mit jedem Flatfile im Ordner herzustellen, müssen Sie sowohl den Foreach-Schleifencontainer als auch den Flatfile-Verbindungs-Manager wie folgt konfigurieren:  
  
-   **Foreach-Schleifen-Container:** Sie ordnen den aufgeführten Wert des Containers einer benutzerdefinierten Paketvariable. Vom Container wird dann diese benutzerdefinierte Variable verwendet, um die `ConnectionString`-Eigenschaft des Flatfile-Verbindungs-Managers dynamisch zu ändern und iterativ Verbindungen mit jeder Flatfile im Ordner herzustellen.  
  
-   **Verbindungs-Manager für Flatfiles:** Ändern Sie den Verbindungs-Manager, der in Lektion 1 erstellt wurde, eine benutzerdefinierte Variable zum Auffüllen der Verbindungs-Manager mit `ConnectionString` Eigenschaft.  
  
 Die Vorgänge in diesem Task verdeutlichen, wie Sie den Foreach-Schleifencontainer erstellen und ändern, um eine benutzerdefinierte Paketvariable zu verwenden, und wie der Schleife der Datenflusstask hinzugefügt wird. Sie lernen, wie der Flatfile-Verbindungs-Manager geändert wird, um eine benutzerdefinierte Variable in der nächsten Aufgabe zu verwenden.  
  
 Nachdem Sie diese Änderungen am Paket vorgenommen haben, iteriert der Foreach-Schleifencontainer beim Ausführen des Pakets durch die Auflistung der Dateien im Ordner Sample Data. Jedes Mal, wenn eine mit dem Kriterium übereinstimmende Datei gefunden wird, wird die benutzerdefinierte Variable vom Foreach-Schleifencontainer mit dem Dateinamen aufgefüllt, die benutzerdefinierte Variable der `ConnectionString`-Eigenschaft des Sample Currency Data-Flatfile-Verbindungs-Managers zugeordnet und dann der Datenfluss gegen diese Datei ausgeführt. Dadurch wird in jeder Iteration der Foreach-Schleife vom Datenflusstask eine andere Flatfile verarbeitet.  
  
> [!NOTE]  
>  Weil [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] die Ablaufsteuerung vom Datenfluss trennt, erfordert keine der Schleifen, die Sie der Ablaufsteuerung hinzufügen, Änderungen am Datenfluss. Deshalb muss der von Ihnen in Lektion 1 erstellte Datenfluss nicht geändert werden.  
  
### <a name="to-add-a-foreach-loop-container"></a>So fügen Sie einen Foreach-Schleifencontainer hinzu  
  
1.  Klicken Sie in **SQL Server Data Tools**auf die Registerkarte **Ablaufsteuerung** .  
  
2.  Erweitern Sie **Container**in der **SSIS-Toolbox**, und ziehen Sie anschließend **Foreach-Schleifencontainer** auf die Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** .  
  
3.  Klicken Sie mit der rechten Maustaste auf den neu hinzugefügten **Foreach-Schleifencontainer** , und wählen Sie **Bearbeiten**aus.  
  
4.  In der **Foreach-Schleifen-Editor** Dialogfeld auf die **allgemeine** Seite für **Namen**, geben Sie `Foreach File in Folder`. Klicken Sie auf **OK**.  
  
5.  Foreach-Schleifencontainer, klicken Sie auf **Eigenschaften**, und prüfen Sie im Eigenschaftenfenster, ob die `LocaleID` -Eigenschaftensatz auf **Englisch (Vereinigte Staaten)**.  
  
### <a name="to-configure-the-enumerator-for-the-foreach-loop-container"></a>So konfigurieren Sie den Enumerator für den Foreach-Schleifencontainer  
  
1.  Doppelklicken Sie auf „Foreach File in Folder“, um den **Foreach-Schleifen-Editor**erneut zu öffnen.  
  
2.  Klicken Sie auf **Sammlung**.  
  
3.  Wählen Sie auf der Seite **Sammlung** **Foreach-Dateienumerator**aus.  
  
4.  Klicken Sie in der Gruppe **Enumeratorkonfiguration** auf **Durchsuchen**.  
  
5.  Suchen Sie im Dialogfeld **Nach Ordner suchen** den Ordner auf dem Computer, der die „Currency_*.txt“-Dateien enthält.  
  
     Die Beispieldaten sind in den [!INCLUDE[ssIS](../includes/ssis-md.md)] -Lektionspaketen enthalten. Um die Beispieldaten und die Lektionspakete herunterzuladen, gehen Sie wie folgt vor.  
  
    1.  Klicken Sie [hier](https://go.microsoft.com/fwlink/?LinkId=275027), um zur Seite Integration Services Product Samples zu gelangen  
  
    2.  Klicken Sie auf die Registerkarte **DOWNLOADS** .  
  
    3.  Klicken Sie auf den Link "http://msftisprodsamples.codeplex.com/downloads/get/578097" SQL2012. Integration_Services.Create_Simple_ETL_Tutorial.Sample.ZIP-Datei.  
  
6.  Geben Sie im Feld **Dateien** **Currency_\*.txt** ein.  
  
### <a name="to-map-the-enumerator-to-a-user-defined-variable"></a>So ordnen Sie den Enumerator einer benutzerdefinierten Variablen zu  
  
1.  Klicken Sie auf **Variablenzuordnungen**.  
  
2.  Klicken Sie auf der Seite **Variablenzuordnungen** in der Spalte **Variable** auf die leere Zelle, und wählen Sie **\<Neue Variable…>** aus.  
  
3.  In der **Variable hinzufügen** im Dialogfeld für **Namen**, Typ `varFileName`.  
  
    > [!IMPORTANT]  
    >  Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Klicken Sie erneut auf **OK** , um das Dialogfeld **Foreach-Schleifen-Editor** zu schließen.  
  
### <a name="to-add-the-data-flow-task-to-the-loop"></a>So fügen Sie der Schleife den Datenflusstask hinzu  
  
-   Ziehen Sie die **Extract Sample Currency Data** -Datenflusstask zum Foreach-Schleifencontainer umbenannt `Foreach File in Folder`.  
  
## <a name="next-lesson-task"></a>Aufgabe in der nächsten Lektion  
 [Schritt 3: Ändern die Flat File Connection Manager](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren eines Foreach-Schleifencontainers](control-flow/foreach-loop-container.md)   
 [Verwenden von Variablen in Paketen](use-variables-in-packages.md)  
  
  
