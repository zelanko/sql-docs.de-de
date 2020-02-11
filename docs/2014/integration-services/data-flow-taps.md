---
title: Datenfluss Abzweigungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2d847adf-4b3d-4949-a195-ef43de275077
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a1938f2389f64d7a869ae924690b8b22fa209f82
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66059905"
---
# <a name="data-flow-taps"></a>Datenflussabzweigungen
  In [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] wird eine neue Funktion eingeführt, über die Sie dem Datenflusspfad eines Pakets zur Laufzeit eine Datenabzweigung hinzufügen und die Ausgabe von der Datenabzweigung an eine externe Datei weiterleiten können. Um diese Funktion verwenden zu können, müssen Sie das SSIS-Projekt mithilfe des Projektbereitstellungsmodells auf einem SSIS-Server bereitstellen. Nachdem Sie das Paket auf dem Server bereitgestellt haben, müssen Sie T-SQL-Skripts für die SSISDB-Datenbank ausführen, um vor der Paketausführung Datenabzweigungen hinzuzufügen. Beispielszenario:  
  
1.  Erstellen Sie mithilfe der gespeicherten Prozedur [catalog.create_execution &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) eine Paketausführungsinstanz.  
  
2.  Fügen Sie mithilfe einer der gespeicherten Prozeduren [catalog.add_data_tap](/sql/integration-services/system-stored-procedures/catalog-add-data-tap) bzw. [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid) eine Datenabzweigung hinzu.  
  
3.  Starten Sie die Paketausführungsinstanz mithilfe von [catalog.start_execution &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).  
  
 Im Folgenden ein SQL-Beispielskript, durch das die im vorangehenden Szenario beschriebenen Schritte ausgeführt werden:  
  
```  
  
Declare @execid bigint  
EXEC [SSISDB].[catalog].[create_execution] @folder_name=N'ETL Folder', @project_name=N'ETL Project', @package_name=N'Package.dtsx', @execution_id=@execid OUTPUT  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt'  
EXEC [SSISDB].[catalog].[start_execution] @execid  
  
```  
  
 Die Parameter für die Ordner-, Projekt- und Paketnamen der gespeicherten Prozedur create_execution entsprechen den Ordner-, Projekt- und Paketnamen im Integration Services-Katalog. Sie können die Ordner-, Projekt- und Paketnamen, die Sie im Aufruf von create_execution verwenden möchten, wie in der folgenden Abbildung dargestellt, aus SQL Server Management Studio abrufen. Wenn das SSIS-Projekt hier nicht angezeigt wird, wurde es möglicherweise noch nicht auf dem SSIS-Server bereitgestellt. Klicken Sie in Visual Studio mit der rechten Maustaste auf das SSIS-Projekt, und klicken Sie auf Bereitstellen, um das Projekt auf dem erwarteten SSIS-Server bereitzustellen.  
  
 Anstatt die SQL-Anweisungen einzugeben, können Sie das Skript zur Paketausführung anhand der folgenden Schritte generieren:  
  
1.  Klicken Sie mit der rechten Maustaste auf **Package.dtsx** , und klicken Sie auf **Ausführen**.  
  
2.  Klicken Sie auf die Symbolleistenschaltfläche **Skript** , um das Skript zu generieren.  
  
3.  Fügen Sie dann die Anweisung add_data_tap vor dem Aufruf von start_execution hinzu.  
  
 Der Parameter task_package_path der gespeicherten Prozedur add_data_tap entspricht der Eigenschaft PackagePath des Datenflusstasks in Visual Studio. Klicken Sie in Visual Studio mit der rechten Maustaste auf **Datenflusstask**, und klicken Sie auf **Eigenschaften** , um das Eigenschaftenfenster zu öffnen.  Notieren Sie sich den Wert der Eigenschaft **PackagePath** , um sie im Aufruf der gespeicherten Prozedur „add_data_tap“ als Wert für den Parameter „task_package_path“ zu verwenden.  
  
 Der Parameter dataflow_path_id_string der gespeicherten Prozedur add_data_tap entspricht der Eigenschaft IdentificationString des Datenflusspfads, dem Sie eine Datenabzweigung hinzufügen möchten. Klicken Sie auf den Datenflusspfad (Pfeil zwischen den Tasks im Datenfluss), und notieren Sie sich den Wert der Eigenschaft **IdentificationString** im Eigenschaftenfenster, um „dataflow_path_id_string“ abzurufen.  
  
 Wenn Sie das Skript ausführen, wird die Ausgabedatei unter „\<Programme>\Microsoft SQL Server\110\DTS\DataDumps“ gespeichert. Wenn bereits eine Datei mit diesem Namen vorhanden ist, wird eine neue Datei mit einem Suffix erstellt (z. B. "output[1].txt").  
  
 Wie oben erwähnt, können Sie anstelle der gespeicherten Prozedur „add_data_tap“ auch die gespeicherte Prozedur [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid)verwenden. Diese gespeicherte Prozedur verwendet anstelle von task_package_path die ID des Datenflusstasks als Parameter. Die ID des Datenflusstasks finden Sie im Eigenschaftenfenster in Visual Studio.  
  
## <a name="removing-a-data-tap"></a>Entfernen einer Datenabzweigung  
 Bevor Sie die Ausführung starten, können Sie eine Datenabzweigung mithilfe der gespeicherten Prozedur [catalog.remove_data_tap](/sql/integration-services/system-stored-procedures/catalog-remove-data-tap) entfernen. Diese gespeicherte Prozedur verwendet die ID der Datenabzweigung als Parameter, die Sie als Ausgabe der gespeicherten Prozedur add_data_tap abrufen können.  
  
```  
  
DECLARE @tap_id bigint  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt' @data_tap_id=@tap_id OUTPUT  
EXEC [SSISDB].[catalog].remove_data_tap @tap_id  
  
```  
  
## <a name="listing-all-data-taps"></a>Auflisten aller Datenabzweigungen  
 Sie können auch alle Datenabzweigungen mithilfe der Sicht catalog.execution_data_taps auflisten. Im folgenden Beispiel werden Datenabzweigungen für die Instanz einer Spezifikationsausführung (ID: 54) extrahiert.  
  
```  
select * from [SSISDB].[catalog].execution_data_taps where execution_id=@execid  
```  
  
## <a name="performance-consideration"></a>Leistungsaspekte  
 Wenn Sie den ausführlichen Protokolliergrad aktivieren und Datenabzweigungen hinzufügen, erhöhen sich die von der Datenintegrationslösung ausgeführten E/A-Vorgänge. Daher wird empfohlen, Datenabzweigungen nur zur Problembehandlung hinzuzufügen.  
  
## <a name="video"></a>Video  
 Das [Video auf TechNet](https://technet.microsoft.com/sqlserver/dn600163) zeigt, wie Sie Datenabzweigungen im SQL Server 2012 SSISDB-Katalog hinzufügen bzw. verwenden, die das programmgesteuerte Debuggen von Paketen und die Erfassung von Teilergebnissen zur Laufzeit unterstützen. Das Video zeigt außerdem, wie Sie diese Datenabzweigungen auflisten bzw. entfernen, und welche bewährten Methoden für Datenabzweigungen in SSIS-Paketen empfohlen werden.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Debuggen des Datenflusses](troubleshooting/debugging-data-flow.md)  
  
 [Behandlung von Problemen mit Paketausführungstools](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
  
