---
title: Sichern, wiederherstellen und Synchronisieren von Datenbanken (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- restoring databases [XML for Analysis]
- backing up databases [XML for Analysis]
- database backups [XML for Analysis]
- synchronization [XML for Analysis]
- database restores [XML for Analysis]
ms.assetid: 6c021b2e-6ad0-444e-b23f-4b5f72ce084b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 500435a585ffed84a8f16e2b3bd1c4db14509103
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545082"
---
# <a name="backing-up-restoring-and-synchronizing-databases-xmla"></a>Sichern, Wiederherstellen und Synchronisieren von Datenbanken (XMLA)
  In XML for Analysis gibt es drei Befehle für das Sichern, Wiederherstellen und Synchronisieren von Datenbanken:  
  
-   Der [Backup](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) -Befehl sichert eine- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank mithilfe einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Sicherungsdatei (. ABF), wie im Abschnitt Sichern von- [Datenbanken](#backing_up_databases)beschrieben.  
  
-   Der [Restore](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) -Befehl stellt eine- [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank aus einer ABF-Datei wieder her, wie im Abschnitt [Wiederherstellen von Datenbanken](#restoring_databases)beschrieben.  
  
-   Der Synchronisierungs [Befehl synchronisiert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank mit den Daten und Metadaten einer anderen Datenbank, wie im Abschnitt [Synchronisieren von Datenbanken](#synchronizing_databases)beschrieben.  
  
##  <a name="backing-up-databases"></a><a name="backing_up_databases"></a>Sichern von Datenbanken  
 Wie bereits erwähnt, sichert der `Backup`-Befehl eine angegebene [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank in einer Sicherungsdatei. Der `Backup`-Befehl weist mehrere Eigenschaften auf, mit denen Sie die zu sichernde Datenbank, die zu verwendende Sicherungsdatei, die Methode zum Sichern von Sicherheitsdefinitionen sowie die zu sichernden Remotepartitionen angeben können.  
  
> [!IMPORTANT]  
>  Das Analysis Services-Dienstkonto muss über die Berechtigung zum Schreiben von Daten in den für jede Datei angegebenen Sicherungsspeicherort verfügen. Dem Benutzer muss zudem eine der folgenden Rollen zugewiesen worden sein: Administratorrolle für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz oder Mitglied einer Datenbankrolle mit der Berechtigung Vollzugriff (Administrator) für die wiederherzustellende Datenbank.  
  
### <a name="specifying-the-database-and-backup-file"></a>Angeben der Datenbank und der Sicherungsdatei  
 Um die zu sichernde Datenbank anzugeben, legen Sie die [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) -Eigenschaft des- `Backup` Befehls fest. Die `Object`-Eigenschaft muss einen Objektbezeichner für eine Datenbank enthalten; andernfalls tritt ein Fehler auf.  
  
 Um die Datei anzugeben, die erstellt und vom Sicherungsprozess verwendet werden soll, legen Sie die [File](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/file-element-xmla) -Eigenschaft des- `Backup` Befehls fest. Die `File`-Eigenschaft sollte auf einen UNC-Pfad und -Dateinamen für die zu erstellende Sicherungsdatei festgelegt werden.  
  
 Sie können nicht nur angeben, welche Datei für die Sicherung verwendet werden soll, sondern Sie können auch die folgenden Optionen für die angegebene Sicherungsdatei festlegen:  
  
-   Wenn Sie die Eigenschaft " [Zuweisung](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/allowoverwrite-element-xmla) " auf "true" festlegen, `Backup` überschreibt der Befehl die Sicherungsdatei, wenn die angegebene Datei bereits vorhanden ist. Wenn Sie die `AllowOverwrite`-Eigenschaft auf den Wert FALSE festlegen, tritt ein Fehler auf, falls die angegebene Sicherungsdatei bereits vorhanden ist.  
  
-   Wenn Sie die [ApplyCompression](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/applycompression-element-xmla) -Eigenschaft auf true festlegen, wird die Sicherungsdatei nach dem Erstellen der Datei komprimiert.  
  
-   Wenn Sie für die [Password](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/password-element-xmla) -Eigenschaft einen nicht leeren Wert festlegen, wird die Sicherungsdatei mithilfe des angegebenen Kennworts verschlüsselt.  
  
    > [!IMPORTANT]  
    >  Wenn die Eigenschaften `ApplyCompression` und `Password` nicht angegeben werden, speichert die Sicherungsdatei Benutzernamen und Kennwörter, die in Verbindungszeichenfolgen in Klartext enthalten sind. Daten, die in Klartext gespeichert werden, können abgerufen werden. Verwenden Sie für erhöhte Sicherheit die Einstellungen `ApplyCompression` und `Password`, um die Sicherungsdatei sowohl zu komprimieren als auch zu verschlüsseln.  
  
### <a name="backing-up-security-settings"></a>Sichern von Sicherheitseinstellungen  
 Die [Security](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla) -Eigenschaft bestimmt, ob der `Backup` Befehl die Sicherheits Definitionen (z. b. Rollen und Berechtigungen) sichert, die für eine-Datenbank definiert sind [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Die `Security`-Eigenschaft bestimmt auch, ob die Sicherungsdatei die Windows-Benutzerkonten und -Gruppen enthält, die als Mitglieder der Sicherheitsdefinitionen definiert sind.  
  
 Der Wert der `Security`-Eigenschaft ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|*SkipMembership*|Einbeziehen von Sicherheitsdefinitionen und Ausschließen von Informationen zur Mitgliedschaft in der Sicherungsdatei.|  
|*CopyAll*|Einbeziehen von Sicherheitsdefinitionen und Informationen zur Mitgliedschaft in der Sicherungsdatei.|  
|*IgnoreSecurity*|Ausschließen von Sicherheitsdefinitionen aus der Sicherungsdatei.|  
  
### <a name="backing-up-remote-partitions"></a>Sichern von Remotepartitionen  
 Um Remote Partitionen in der-Datenbank zu sichern [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , legen Sie die [BackupRemotePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/backupremotepartitions-element-xmla) -Eigenschaft des- `Backup` Befehls auf true fest. Diese Einstellung veranlasst den `Backup`-Befehl, eine Remotesicherungsdatei für jede Remotedatenquelle zu erstellen, die zum Speichern von Remotepartitionen für die Datenbank verwendet wird.  
  
 Für jede zu sichernde Remote Datenquelle können Sie die zugehörige Sicherungsdatei angeben, indem Sie ein [Location](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/location-element-xmla) -Element in die Location [-Eigenschaft des](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/locations-element-xmla) - `Backup` Befehls einschließen. Für das- `Location` Element sollte die `File` -Eigenschaft auf den UNC-Pfad und den Dateinamen der Remote Sicherungsdatei festgelegt sein, und seine [DataSourceID-](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) Eigenschaft muss auf den Bezeichner der Remote Datenquelle festgelegt werden, die in der Datenbank definiert ist.  
  
##  <a name="restoring-databases"></a><a name="restoring_databases"></a>Daten Bank Wiederherstellung  
 Der `Restore`-Befehl stellt eine angegebene [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank mithilfe einer Sicherungsdatei wieder her. Der `Restore`-Befehl weist mehrere Eigenschaften auf, mit denen Sie die wiederherzustellende Datenbank, die zu verwendende Sicherungsdatei, die Methode zum Wiederherstellen von Sicherheitsdefinitionen sowie die zu speichernden Remotepartitionen und das Verschieben relationaler OLAP-Objekte (ROLAP-Objekte) angeben können.  
  
> [!IMPORTANT]  
>  Für jede Sicherungsdatei muss der Benutzer, der den Wiederherstellungsbefehl ausführt, über die Berechtigung zum Lesen von dem für jede Datei angegebenen Sicherungsspeicherort verfügen. Zum Wiederherstellen einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank, die nicht auf dem Server installiert ist, muss der Benutzer zusätzlich Mitglied der Serverrolle für die betreffende [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz sein. Zum Überschreiben einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank muss der Benutzer entweder Mitglied der Serverrolle für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz oder Mitglied einer Datenbankrolle mit den Berechtigungen Vollzugriff (Administrator) für die wiederherzustellende Datenbank sein.  
  
> [!NOTE]  
>  Nach dem Wiederherstellen einer vorhandenen Datenbank verliert der Benutzer, der die Datenbank wiederhergestellt hat, möglicherweise den Zugriff auf diese Datenbank. Dies ist u. U. der Fall, wenn der Benutzer zum Zeitpunkt der Sicherung kein Mitglied der Serverrolle oder der Datenbankrolle mit der Berechtigung "Vollzugriff (Administrator)" war.  
  
### <a name="specifying-the-database-and-backup-file"></a>Angeben der Datenbank und der Sicherungsdatei  
 Die `DatabaseName`-Eigenschaft des `Restore`-Befehls muss einen Objektbezeichner für eine Datenbank enthalten; andernfalls tritt ein Fehler auf. Wenn die angegebene Datenbank bereits vorhanden ist, bestimmt die `AllowOverwrite`-Eigenschaft, ob die vorhandene Datenbank überschrieben wird. Wenn Sie die `AllowOverwrite`-Eigenschaft auf den Wert FALSE festlegen und die angegebene Datenbank bereits vorhanden ist, tritt ein Fehler auf.  
  
 Die `File`-Eigenschaft des `Restore`-Befehls sollte auf einen UNC-Pfad und -Dateinamen für die Sicherungsdatei festgelegt werden, die in der angegebenen Datenbank wiederhergestellt werden soll. Sie können auch die `Password`-Eigenschaft für die angegebene Sicherungsdatei festlegen. Wenn Sie die `Password`-Eigenschaft auf einen bestimmten Wert festlegen, wird die Sicherungsdatei mithilfe des angegebenen Kennworts entschlüsselt. Wenn die Sicherungsdatei nicht verschlüsselt ist oder wenn das angegebene Kennwort nicht mit dem für die Entschlüsselung der Sicherungsdatei verwendeten Kennwort übereinstimmt, tritt ein Fehler auf.  
  
### <a name="restoring-security-settings"></a>Wiederherstellen von Sicherheitseinstellungen  
 Die `Security`-Eigenschaft bestimmt, ob mit dem `Restore`-Befehl die Sicherheitsdefinitionen wie Rollen und Berechtigungen wiederhergestellt werden, die für eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank definiert sind. Die `Security`-Eigenschaft bestimmt auch, ob der `Restore`-Befehl im Rahmen des Wiederherstellungsprozesses die Windows-Benutzerkonten und -Gruppen einschließt, die als Mitglieder der Sicherheitsdefinitionen definiert sind.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|*SkipMembership*|Einbeziehen von Sicherheitsdefinitionen und Ausschließen von Informationen zur Mitgliedschaft in der Datenbank.|  
|*CopyAll*|Einbeziehen von Sicherheitsdefinitionen und Informationen zur Mitgliedschaft in der Datenbank.|  
|*IgnoreSecurity*|Ausschließen von Sicherheitsdefinitionen aus der Datenbank.|  
  
### <a name="restoring-remote-partitions"></a>Wiederherstellen von Remotepartitionen  
 Für jede Remotesicherungsdatei, die während eines zuvor ausgeführten `Backup`-Befehls erstellt wurde, können Sie die zugeordnete Remotepartition wiederherstellen, indem Sie ein `Location`-Element in die `Locations`-Eigenschaft des `Restore`-Befehls einbeziehen. Die [DataSourceType](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) -Eigenschaft für jedes `Location` Element muss ausgeschlossen oder explizit auf " *Remote*" festgelegt werden.  
  
 Für jedes angegebene `Location`-Element kontaktiert die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz die in der `DataSourceID`-Eigenschaft angegebene Remotedatenquelle, um die Partitionen wiederherzustellen, die in der Remotesicherungsdatei definiert sind, welche in der `File`-Eigenschaft angegeben ist. Neben der `DataSourceID`- und der `File`-Eigenschaft sind die folgenden Eigenschaften für jedes `Location`-Element verfügbar, das zum Wiederherstellen einer Remotepartition verwendet wird:  
  
-   Wenn Sie die Verbindungszeichenfolge für die in `DataSourceID` angegebene Remotedatenquelle überschreiben möchten, können Sie die `ConnectionString`-Eigenschaft für das `Location`-Element auf eine andere Verbindungszeichenfolge festlegen. Der Befehl `Restore` verwendet dann die Verbindungszeichenfolge, die in der `ConnectionString`-Eigenschaft enthalten ist. Wenn `ConnectionString` nicht angegeben ist, verwendet der Befehl `Restore` die Verbindungszeichenfolge, die in der Sicherungsdatei für die angegebene Remotedatenquelle gespeichert ist. Sie können die Einstellung `ConnectionString` verwenden, um eine Remotepartition auf eine andere Remoteinstanz zu verschieben. Sie können jedoch die Einstellung `ConnectionString` nicht verwenden, um eine Remotepartition auf der gleichen Instanz wiederherzustellen, die auch die wiederhergestellt Datenbank enthält. Sie können die Eigenschaft `ConnectionString` also nicht verwenden, um eine Remotepartition in eine lokale Partition umzuwandeln.  
  
-   Für jeden Originalordner, der zum Speichern der Remote Partitionen in der Remote Datenquelle verwendet wird, können Sie ein [Ordner](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/folder-element-xmla) Element angeben, um den neuen Ordner anzugeben, in dem alle im ursprünglichen Ordner gespeicherten Remote Partitionen wieder hergestellt werden sollen. Wenn ein `Folder`-Element nicht angegeben ist, verwendet der `Restore`-Befehl die ursprünglichen Ordner, die für die in der Remotesicherungsdatei enthaltenen Remotepartitionen angegeben sind.  
  
### <a name="relocating-rolap-objects"></a>Verschieben von ROLAP-Objekten  
 Mit dem `Restore`-Befehl können keine Aggregationen oder Daten für Objekte wiederhergestellt werden, die den ROLAP-Speichermodus verwenden, da solche Informationen in Tabellen in einer zugrunde liegenden relationalen Datenquelle gespeichert werden. Jedoch können die Metadaten für ROLAP-Objekte wiederhergestellt werden. Zum Wiederherstellen der Metadaten für ROLAP-Objekte erstellt der `Restore`-Befehl die Tabellenstruktur in einer relationalen Datenbank neu.  
  
 Sie können das `Location`-Element in einem `Restore`-Befehl verwenden, um ROLAP-Objekte zu verschieben. Für jedes `Location` Element, das zum Verschieben einer Datenquelle verwendet wird, muss die- `DataSourceType` Eigenschaft explizit auf *local*festgelegt werden. Sie müssen auch die `ConnectionString`-Eigenschaft des `Location`-Elements auf die Verbindungszeichenfolge für den neuen Speicherort festlegen. Während der Wiederherstellung ersetzt der `Restore`-Befehl die Verbindungszeichenfolge für die Datenquelle, die von der `DataSourceID`-Eigenschaft des `Location`-Elements identifiziert wird, durch den Wert der `ConnectionString`-Eigenschaft des `Location`-Elements.  
  
##  <a name="synchronizing-databases"></a><a name="synchronizing_databases"></a>Synchronisieren von Datenbanken  
 Der Befehl `Synchronize` synchronisiert die Daten und die Metadaten einer angegebenen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank mit denen einer anderen Datenbank. Der `Synchronize`-Befehl weist verschiedene Eigenschaften auf, mit denen Sie die Quelldatenbank, die Methode zur Synchronisierung von Sicherheitsdefinitionen, die zu synchronisierenden Remotepartitionen und die Synchronisierung von ROLAP-Objekten angeben können.  
  
> [!NOTE]  
>  Der `Synchronize`-Befehl kann nur von Serveradministratoren und Datenbankadministratoren ausgeführt werden. Sowohl die Quell- als auch die Zieldatenbank müssen den gleichen Datenbank-Kompatibilitätsgrad besitzen.  
  
### <a name="specifying-the-source-database"></a>Angeben der Quelldatenbank  
 Die [Source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) -Eigenschaft des `Synchronize` Befehls enthält zwei Eigenschaften: `ConnectionString` und `Object` . Die `ConnectionString`-Eigenschaft enthält die Verbindungszeichenfolge der Instanz, die die Quelldatenbank enthält, und die `Object`-Eigenschaft enthält den Objektbezeichner für die Quelldatenbank.  
  
 Die Zieldatenbank ist die aktuelle Datenbank für die Sitzung, in der der `Synchronize`-Befehl ausgeführt wird.  
  
 Wenn die `ApplyCompression`-Eigenschaft des `Synchronize`-Befehls auf den Wert TRUE festgelegt ist, werden die von der Quelldatenbank an die Zieldatenbank gesendeten Informationen vor dem Senden komprimiert.  
  
### <a name="synchronizing-security-settings"></a>Synchronisieren von Sicherheitseinstellungen  
 Die [SynchronizeSecurity](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla) -Eigenschaft bestimmt, ob der `Synchronize` Befehl die Sicherheits Definitionen (z. b. Rollen und Berechtigungen) synchronisiert, die in der Quelldatenbank definiert sind. Die `SynchronizeSecurity`-Eigenschaft bestimmt auch, ob der `Sychronize`-Befehl die Windows-Benutzerkonten und -Gruppen enthält, die als Mitglieder der Sicherheitsdefinitionen definiert sind.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|*SkipMembership*|Einbeziehen von Sicherheitsdefinitionen und Ausschließen von Informationen zur Mitgliedschaft in der Zieldatenbank.|  
|*CopyAll*|Einbeziehen von Sicherheitsdefinitionen und Informationen zur Mitgliedschaft in der Zieldatenbank.|  
|*IgnoreSecurity*|Ausschließen von Sicherheitsdefinitionen aus der Zieldatenbank.|  
  
### <a name="synchronizing-remote-partitions"></a>Synchronisieren von Remotepartitionen  
 Für jede Remotedatenbank, die in der Zieldatenbank vorhanden ist, können Sie jede zugeordnete Remotepartition synchronisieren, indem Sie ein `Location`-Element in die `Locations`-Eigenschaft des `Synchronize`-Befehls einbeziehen. Für jedes- `Location` Element muss die- `DataSourceType` Eigenschaft ausgeschlossen oder explizit auf " *Remote*" festgelegt werden.  
  
 Zum Definieren und Herstellen einer Verbindung zu einer Remotedatenquelle in der Zieldatenbank verwendet der `Synchronize`-Befehl die Verbindungszeichenfolge, die in der `ConnectionString`-Eigenschaft des `Location`-Elements definiert ist. Der `Synchronize`-Befehl verwendet dann die `DataSourceID`-Eigenschaft des `Location`-Elements, um die zu synchronisierenden Remotepartitionen zu identifizieren. Der- `Synchronize` Befehl synchronisiert die Remote Partitionen der Remote Datenquelle, die in der-Eigenschaft der Quelldatenbank angegeben sind, `DataSourceID` mit der Remote Datenquelle, die in der- `DataSourceID` Eigenschaft der Zieldatenbank angegeben ist.  
  
 Für jeden ursprünglich zum Speichern der Remotepartitionen in der Remotedatenquelle der Quelldatenbank verwendeten Ordner können Sie auch ein `Folder`-Element im `Location`-Element verwenden. Das `Folder`-Element gibt den neuen Ordner für die Zieldatenbank an, in dem alle im ursprünglichen Ordner in der Remotedatenquelle gespeicherten Remotepartitionen synchronisiert werden sollen. Wenn ein `Folder`-Element nicht angegeben ist, verwendet der Synchronize-Befehl die ursprünglichen Ordner, die für die in der Quelldatenbank enthaltenen Remotepartitionen angegeben sind.  
  
### <a name="synchronizing-rolap-objects"></a>Synchronisieren von ROLAP-Objekten  
 Mit dem `Synchronize`-Befehl können keine Aggregationen oder Daten für Objekte synchronisiert werden, die den ROLAP-Speichermodus verwenden, da solche Informationen in Tabellen in einer zugrunde liegenden relationalen Datenquelle gespeichert werden. Jedoch können die Metadaten für ROLAP-Objekte synchronisiert werden. Zum Synchronisieren der Metadaten stellt der `Synchronize`-Befehl die Tabellenstruktur für eine relationale Datenbank wieder her.  
  
 Sie können das `Location`-Element in einem Synchronize-Befehl verwenden, um ROLAP-Objekte zu synchronisieren. Für jedes `Location` Element, das zum Verschieben einer Datenquelle verwendet wird, muss die- `DataSourceType` Eigenschaft explizit auf *local*festgelegt werden. . Sie müssen auch die `ConnectionString`-Eigenschaft des `Location`-Elements auf die Verbindungszeichenfolge für den neuen Speicherort festlegen. Während der Synchronisierung ersetzt der `Synchronize`-Befehl die Verbindungszeichenfolge für die Datenquelle, die von der `DataSourceID`-Eigenschaft des `Location`-Elements identifiziert wird, durch den Wert der `ConnectionString`-Eigenschaft des `Location`-Elements.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Backup-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [Restore-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)   
 [Element &#40;XMLA synchronisieren&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
