---
title: Paket ausführen (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executepackagetask.f1
helpviewer_keywords:
- Execution Package task [Integration Services]
- child packages
- parent packages [Integration Services]
ms.assetid: 042d4ec0-0668-401c-bb3a-a25fe2602eac
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 59b623076e86f3bacf5ae8c6e24b48774e33f670
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62831909"
---
# <a name="execute-package-task"></a>Paket ausführen (Task)
  Der Task Paket ausführen erweitert die Unternehmensfunktionen von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , indem Paketen das Ausführen anderer Pakete als Teil eines Workflows ermöglicht wird.  
  
 Der Task Paket ausführen kann für folgende Zwecke verwendet werden:  
  
-   Unterteilen eines komplexen Paketworkflows. Mit diesem Task können Sie Workflow in mehrere Pakete unterteilen, die einfacher zu lesen, zu testen und zu warten sind. Wenn Sie z. B. Daten in ein Sternschema laden, können Sie ein separates Paket erstellen, um jede Dimension und die Faktentabelle aufzufüllen.  
  
-   Wiederverwenden von Paketteilen. Andere Pakete können Teile eines Paketworkflows wiederverwenden. Sie können z. B. ein Modul zum Extrahieren von Daten erstellen, das von verschiedenen Paketen aus aufgerufen werden kann. Jedes Paket, das das Modul zum Extrahieren aufruft, kann verschiedene Datenbereinigungs-, Filter- oder Aggregationsvorgänge ausführen.  
  
-   Gruppieren von Arbeitseinheiten. Arbeitseinheiten können in separaten Paketen gekapselt und als Transaktionskomponenten mit dem Workflow eines übergeordneten Pakets verknüpft werden. Beispielsweise führt das übergeordnete Paket die zusätzlichen Pakete aus und führt basierend auf dem Erfolg oder dem Fehlschlagen der zusätzlichen Pakete, einen Commit oder ein Rollback der Transaktion aus.  
  
-   Steuern der Paketsicherheit. Paketersteller benötigen Zugriff auf nur einen Teil einer Multipaketlösung. Das Aufteilen eines Pakets in mehrere Pakete stellt mehr Sicherheit bereit, weil Sie einem Ersteller Zugriff nur auf die relevanten Pakete erteilen können.  
  
 Ein Paket, das andere Pakete ausführt, wird im Allgemeinen als übergeordnetes Paket bezeichnet, und die Pakete, die von einem übergeordneten Workflow ausgeführt werden, werden als untergeordnete Pakete bezeichnet.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthält Tasks, die Workflowvorgänge ausführen, z. B. das Ausführen von ausführbaren Dateien und Batchdateien. Weitere Informationen finden Sie unter [Execute Process Task](execute-process-task.md).  
  
## <a name="running-packages"></a>Ausführen von Paketen  
 Der Task "Paket ausführen" kann untergeordnete Pakete ausführen, die im gleichen Projekt enthalten sind, das auch das übergeordnete Paket enthält. Sie wählen ein untergeordnetes Paket vom Projekt aus, indem Sie die **ReferenceType** -Eigenschaft auf **Projektverweis**und dann die **PackageNameFromProjectReference** -Eigenschaft entsprechend festlegen.  
  
> [!NOTE]  
>  Die Option **ReferenceType** ist schreibgeschützt und auf **Externer Verweis** festgelegt, wenn das Projekt, das das Paket enthält, nicht in das Projektbereitstellungsmodell konvertiert wurde. Weitere Informationen über die Konvertierung finden Sie unter [Bereitstellen von Projekten auf dem Integration Services-Server](../deploy-projects-to-integration-services-server.md).  
  
 Mit dem Task „Paket ausführen“ können Pakete ausgeführt werden, die in der msdb-Datenbank von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert sind, sowie im Dateisystem gespeicherte Pakete. Der Task stellt mithilfe eines OLE DB-Verbindungs-Managers eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder mit einem Dateiverbindungs-Manager her, um auf das Dateisystem zuzugreifen. Weitere Informationen finden Sie unter [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md) und [Flat File Connection Manager](../connection-manager/flat-file-connection-manager.md).  
  
 Mit dem Task Paket ausführen kann auch ein Datenbankwartungsplan ausgeführt werden. Auf diese Weise können [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Pakete und Datenbankwartungspläne in derselben [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Lösung verwaltet werden. Ein Datenbankwartungsplan ist mit einem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paket zu vergleichen. Ein Plan kann jedoch nur Datenbankwartungstasks enthalten und wird immer in der msdb-Datenbank gespeichert.  
  
 Wenn Sie ein im Dateisystem gespeichertes Paket auswählen, müssen Sie den Namen und den Speicherort des Pakets angeben. Das Paket kann überall im Dateisystem gespeichert sein. Es muss sich nicht in demselben Ordner wie das übergeordnete Paket befinden.  
  
 Das untergeordnete Paket kann im Prozess des übergeordneten Pakets oder als eigener Prozess ausgeführt werden. Das Ausführen des untergeordneten Pakets als eigener Prozess erfordert mehr Arbeitsspeicher, bietet allerdings mehr Flexibilität. Beispielsweise kann bei einem Fehler des untergeordneten Prozesses der übergeordnete Prozess weiterhin ausgeführt werden.  
  
 Alternativ kann es vorkommen, dass in bestimmten Situationen das übergeordnete und das untergeordnete Paket gemeinsam einen Fehler erzeugen sollen, oder Sie möchten den zusätzlichen Verarbeitungsaufwand eines anderen Prozesses übernehmen. Wenn z. B. bei einem untergeordneten Prozess ein Fehler auftritt und die nachfolgende Verarbeitung im übergeordneten Prozess des Pakets vom Erfolg des untergeordneten Prozesses abhängt, sollte das untergeordnete Paket im Prozess des übergeordneten Pakets ausgeführt werden.  
  
 In der Standardeinstellung die ExecuteOutOfProcess-Eigenschaft des Tasks Paket ausführen festgelegt ist, um `False`, und das untergeordnete Paket ausgeführt wird, im selben Prozess wie das übergeordnete Paket. Wenn Sie diese Eigenschaft auf `True` festlegen, wird das untergeordnete Paket in einem separaten Prozess ausgeführt. Dadurch kann sich der Start des untergeordneten Pakets verlangsamen. Wenn Sie die Eigenschaft auf `True` festlegen, ist das Debuggen des Pakets in einer Installation, die nur die Tools enthält, außerdem nicht möglich. Sie müssen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]installieren. Weitere Informationen finden Sie unter [Installieren von Integration Services](../install-windows/install-integration-services.md).  
  
## <a name="extending-transactions"></a>Erweitern von Transaktionen  
 Die vom übergeordneten Paket verwendete Transaktion kann auf das untergeordnete Paket erweitert werden. Deshalb kann für die von beiden Paketen ausgeführte Arbeit ein Commit oder Rollback ausgeführt werden. Beispielsweise kann für Datenbankeinfügungen, die vom übergeordneten Paket ausgeführt werden, ein Commit oder Rollback ausgeführt werden, und zwar in Abhängigkeit von den vom untergeordneten Paket ausgeführten Datenbankeinfügungen und umgekehrt. Weitere Informationen finden Sie unter [Inherited Transactions](../inherited-transactions.md).  
  
## <a name="propagating-logging-details"></a>Weitergeben von Protokollierungsdetails  
 Für das untergeordnete Paket, das der Task Paket ausführen ausführt, ist möglicherweise die Verwendung der Protokollierung konfiguriert. Das untergeordnete Paket leitet jedoch die Protokolldetails stets an das übergeordnete Paket weiter. Falls für den Task Paket ausführen die Verwendung der Protokollierung konfiguriert ist, protokolliert der Task die Protokolldetails des untergeordneten Pakets. Weitere Informationen finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md).  
  
## <a name="passing-values-to-child-packages"></a>Übergeben von Werten an untergeordnete Pakete  
 Häufig verwendet ein untergeordnetes Paket Werte, die von einem anderen Paket übergeben werden, das das untergeordnete Paket aufruft. Normalerweise handelt es sich dabei um das übergeordnete Paket. Das Verwenden von Werten eines übergeordneten Pakets ist in folgenden Szenarien hilfreich:  
  
-   Teile eines größeren Workflows sind verschiedenen Paketen zugewiesen. Beispielsweise könnte ein Paket jede Nacht Daten herunterladen, die Daten zusammenfassen, Zusammenfassungsdatenwerte Variablen zuweisen und dann die Werte an ein anderes Paket zum weiteren Verarbeiten der Daten übergeben.  
  
-   Das übergeordnete Paket koordiniert Tasks in einem untergeordneten Paket dynamisch. Beispielsweise könnte das übergeordnete Paket die Anzahl von Tagen im aktuellen Monat bestimmen und diesen Wert einer Variablen zuweisen. Das untergeordnete Paket führt dann einen Task entsprechend oft aus.  
  
-   Ein untergeordnetes Paket benötigt Zugriff auf Daten, die vom übergeordneten Paket dynamisch abgeleitet werden. Beispielsweise könnte das übergeordnete Paket Daten aus einer Tabelle extrahieren und das Rowset in eine Variable laden, und das untergeordnete Paket könnte zusätzliche Vorgänge für die Daten ausführen.  
  
 Sie mithilfe der folgenden Methoden Werte an ein untergeordnetes Paket übergeben:  
  
-   **Paketkonfigurationen**  
  
     [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] bietet einen Konfigurationstyp, die Variablenkonfiguration für übergeordnete Pakete, mit dem Werte von übergeordneten an untergeordnete Pakete übergeben werden können. Diese Konfiguration basiert auf dem untergeordneten Paket und verwendet eine Variable im untergeordneten Paket. Die Konfiguration wird einer Variablen im untergeordneten Paket zugeordnet oder der Eigenschaft eines Objekts im untergeordneten Paket. Die Variable kann auch in den Skripts verwendet werden, die vom Skripttask oder der Skriptkomponente verwendet werden.  
  
-   **Parameter**  
  
     Sie können den Task "Paket ausführen" konfigurieren, um Variablen für übergeordnete Pakete oder Parameter untergeordneten Paketparametern zuzuordnen. Das Projekt muss das Projektbereitstellungsmodell verwenden, und das untergeordnete Paket muss im gleichen Projekt enthalten sein wie das übergeordnete Paket. Weitere Informationen finden Sie unter [Execute Package Task Editor](../execute-package-task-editor.md).  
  
    > [!NOTE]  
    >  Wenn der untergeordnete Paketparameter nicht vertraulich ist und einem übergeordneten Parameter zugeordnet wird, der vertraulich ist, wird das untergeordnete Paket nicht ausgeführt.  
    >   
    >  Die folgenden Zuordnungsbedingungen unterstützt.  
    >   
    >  -   Vertraulich, ein untergeordneten Paketparameter wird einem vertraulichen übergeordneten Parameter zugeordnet  
    > -   Vertraulich, ein untergeordneten Paketparameter wird einem nicht vertraulichen übergeordneten Parameter zugeordnet  
    > -   Nicht vertraulich, ein untergeordneten Paketparameter wird einem nicht vertraulichen übergeordneten Parameter zugeordnet  
  
 Die Variable für das untergeordnete Paket kann im Bereich des Tasks "Paket ausführen" oder in einem übergeordneten Container wie dem Paket definiert werden. Falls mehrere gleichnamige Variablen vorhanden sind, wird die im Bereich des Tasks Paket ausführen definierte Variable verwendet oder die Variable, die im Bereich dem Task am nächsten liegt.  
  
 Weitere Informationen finden Sie unter [Verwenden der Werte von Variablen und Parametern in einem untergeordneten Paket](../use-the-values-of-variables-and-parameters-in-a-child-package.md).  
  
### <a name="accessing-parent-package-variables"></a>Zugriff auf Variablen für übergeordnete Pakete  
 Untergeordnete Pakete greifen über den Skripttask auf Variablen für übergeordnete Pakete zu. Wenn Sie im **Skripttask-Editor** auf der Seite **Skript** den Namen der Variablen für das übergeordnete Paket eingeben, lassen Sie **Benutzer:** im Variablennamen aus. Andernfalls wird die Variable beim Ausführen des übergeordneten Pakets vom untergeordneten Paket nicht gesucht. Weitere Informationen zu den Skripttask auf Variablen für übergeordnete Pakete verwenden, finden Sie unter diesem Blogeintrag [SSIS: Zugriff auf Variablen in einem übergeordneten Paket](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/).  
  
## <a name="configuring-the-execute-package-task"></a>Konfigurieren des Tasks Paket ausführen  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Execute Package Task Editor](../execute-package-task-editor.md)  
  
-   [Seite Ausdrücke](../expressions/expressions-page.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-tasks"></a>Related Tasks  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Blogeintrag, [SSIS: Untergeordnete Pakete prozessintern oder Out-of-Process ausgeführt werden soll? ](https://go.microsoft.com/fwlink/?LinkId=220819), auf consultingblogs.emc.com.  
  
-   Blogeintrag, [SSIS: Zugriff auf Variablen in einem übergeordneten Paket](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/), auf andyleonard.blog. 
  
  
