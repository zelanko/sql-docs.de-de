---
title: Sichern, wiederherstellen und Synchronisieren von Datenbanken (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 19d311a07eb11f1c5119a3c20d7536b5a2986b49
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62719890"
---
# <a name="backing-up-restoring-and-synchronizing-databases-xmla"></a>Sichern, Wiederherstellen und Synchronisieren von Datenbanken (XMLA)
  In XML for Analysis gibt es drei Befehle für das Sichern, Wiederherstellen und Synchronisieren von Datenbanken:  
  
-   Die [Sicherung](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) Befehl sichert eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank mithilfe einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Sicherungsdatei (.abf), wie im Abschnitt beschrieben [Sichern von Datenbanken](#backing_up_databases).  
  
-   Die [wiederherstellen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) -Befehl wird eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank aus einer ABF-Datei, klicken Sie im Abschnitt beschriebenen [Wiederherstellen von Datenbanken](#restoring_databases).  
  
-   Die [synchronisierende](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) -Befehl synchronisiert eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mit den Daten und Metadaten einer anderen Datenbank, Datenbank, wie im Abschnitt beschrieben [Synchronisieren von Datenbanken](#synchronizing_databases).  
  
##  <a name="backing_up_databases"></a> Sichern von Datenbanken  
 Wie bereits erwähnt die **Backup** Befehl sichert ein angegebenes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank in einer Sicherungsdatei. Die **Backup** -Befehl weist mehrere Eigenschaften, mit denen Sie angeben, dass die Datenbank gesichert werden, können die Sicherungsdatei zu verwenden, wie Sie von sicherheitsdefinitionen sowie die zu sichernden Remotepartitionen sichern.  
  
> [!IMPORTANT]  
>  Das Analysis Services-Dienstkonto muss über die Berechtigung zum Schreiben von Daten in den für jede Datei angegebenen Sicherungsspeicherort verfügen. Dem Benutzer muss zudem eine der folgenden Rollen zugewiesen worden sein: Administratorrolle für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz oder Mitglied einer Datenbankrolle mit der Berechtigung Vollzugriff (Administrator) für die wiederherzustellende Datenbank.  
  
### <a name="specifying-the-database-and-backup-file"></a>Angeben der Datenbank und der Sicherungsdatei  
 Um die Datenbank gesichert werden, anzugeben, legen Sie die [Objekt](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) Eigenschaft der **Sicherung** Befehl. Die **Objekt** Eigenschaft muss einen Objektbezeichner für eine Datenbank enthalten, oder ein Fehler auftritt.  
  
 Um die Datei anzugeben, die erstellt und der im Sicherungsprozess verwendet werden, legen Sie die [Datei](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/file-element-xmla) Eigenschaft der **Backup** Befehl. Die **Datei** Eigenschaft muss festgelegt werden, auf einen UNC-Pfad und Dateinamen für die Sicherungsdatei erstellt werden.  
  
 Sie können nicht nur angeben, welche Datei für die Sicherung verwendet werden soll, sondern Sie können auch die folgenden Optionen für die angegebene Sicherungsdatei festlegen:  
  
-   Setzen Sie die [AllowOverwrite](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/allowoverwrite-element-xmla) Eigenschaft auf "true", die **Backup** Befehl überschreibt die Sicherungsdatei aus, wenn die angegebene Datei bereits vorhanden ist. Setzen Sie die **AllowOverwrite** -Eigenschaft auf "false", ein Fehler auftritt, wenn die angegebene Sicherungsdatei bereits vorhanden ist.  
  
-   Setzen Sie die [ApplyCompression](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/applycompression-element-xmla) Eigenschaft auf "true", die Sicherungsdatei komprimiert wird, nachdem die Datei erstellt wird.  
  
-   Setzen Sie die [Kennwort](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/password-element-xmla) Eigenschaft auf einen nicht leeren Wert, der Sicherungsdatei wird unter Verwendung des angegebenen Kennworts verschlüsselt.  
  
    > [!IMPORTANT]  
    >  Wenn **ApplyCompression** und **Kennwort** Eigenschaften sind nicht angegeben ist, speichert die Sicherungsdatei Benutzernamen und Kennwörter, die enthalten sind, in Verbindungszeichenfolgen in Klartext. Daten, die in Klartext gespeichert werden, können abgerufen werden. Verwenden Sie zur Erhöhung der Sicherheit der **ApplyCompression** und **Kennwort** Einstellungen zum Komprimieren und verschlüsseln die Sicherungsdatei.  
  
### <a name="backing-up-security-settings"></a>Sichern von Sicherheitseinstellungen  
 Die [Sicherheit](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla) Eigenschaft bestimmt, ob die **Sicherung** Befehl sichert die sicherheitsdefinitionen wie Rollen und Berechtigungen definiert werden, auf eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank. Die **Sicherheit** -Eigenschaft bestimmt auch, ob die Sicherungsdatei enthält, die Windows-Benutzerkonten und Gruppen als Mitglieder der sicherheitsdefinitionen definiert.  
  
 Der Wert des der **Sicherheit** Eigenschaft ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*SkipMembership*|Einbeziehen von Sicherheitsdefinitionen und Ausschließen von Informationen zur Mitgliedschaft in der Sicherungsdatei.|  
|*CopyAll*|Einbeziehen von Sicherheitsdefinitionen und Informationen zur Mitgliedschaft in der Sicherungsdatei.|  
|*IgnoreSecurity*|Ausschließen von Sicherheitsdefinitionen aus der Sicherungsdatei.|  
  
### <a name="backing-up-remote-partitions"></a>Sichern von Remotepartitionen  
 Zum Sichern von Remotepartitionen in der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank Festlegen der [BackupRemotePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/backupremotepartitions-element-xmla) Eigenschaft der **Sicherung** -Befehls auf true fest. Diese Einstellung bewirkt, dass die **Backup** Befehl aus, um eine remotesicherungsdatei für jede Remotedatenquelle zu erstellen, die zum Speichern von Remotepartitionen für die Datenbank verwendet wird.  
  
 Für jede Remotedatenquelle gesichert werden müssen, können Sie eine entsprechende Sicherungsdatei angeben, mit einer [Speicherort](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/location-element-xmla) Element in der [Speicherorte](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/locations-element-xmla) Eigenschaft der **Backup** -Befehl. Die **Speicherort** Element verfügen die **Datei** -Eigenschaft festgelegt wird, auf den UNC-Pfad und Dateinamen der remotesicherungsdatei und die zugehörige [DataSourceID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceid-element-xmla) -Eigenschaft auf den Bezeichner der die Remotedatenquelle, die in der Datenbank definiert.  
  
##  <a name="restoring_databases"></a> Wiederherstellen von Datenbanken  
 Die **wiederherstellen** Befehl wird ein angegebenes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank aus einer Sicherungsdatei. Die **wiederherstellen** -Befehl weist mehrere Eigenschaften, mit denen Sie angeben, dass die Datenbank wiederherstellen, die Sicherungsdatei zu verwenden, wie Sie zum Wiederherstellen von sicherheitsdefinitionen, die zu speichernden Remotepartitionen und das Verschieben relationaler OLAP (ROLAP) -Objekte.  
  
> [!IMPORTANT]  
>  Für jede Sicherungsdatei muss der Benutzer, der den Wiederherstellungsbefehl ausführt, über die Berechtigung zum Lesen von dem für jede Datei angegebenen Sicherungsspeicherort verfügen. Zum Wiederherstellen einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank, die nicht auf dem Server installiert ist, muss der Benutzer zusätzlich Mitglied der Serverrolle für die betreffende [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz sein. Zum Überschreiben einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank muss der Benutzer entweder Mitglied der Serverrolle für die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz oder Mitglied einer Datenbankrolle mit den Berechtigungen Vollzugriff (Administrator) für die wiederherzustellende Datenbank sein.  
  
> [!NOTE]  
>  Nach dem Wiederherstellen einer vorhandenen Datenbank verliert der Benutzer, der die Datenbank wiederhergestellt hat, möglicherweise den Zugriff auf diese Datenbank. Dies ist u. U. der Fall, wenn der Benutzer zum Zeitpunkt der Sicherung kein Mitglied der Serverrolle oder der Datenbankrolle mit der Berechtigung "Vollzugriff (Administrator)" war.  
  
### <a name="specifying-the-database-and-backup-file"></a>Angeben der Datenbank und der Sicherungsdatei  
 Die **DatabaseName** Eigenschaft der **wiederherstellen** -Befehls muss einen Objektbezeichner für eine Datenbank enthalten, oder ein Fehler auftritt. Wenn die angegebene Datenbank bereits vorhanden ist, die **AllowOverwrite** Eigenschaft bestimmt, ob die vorhandene Datenbank überschrieben wird. Wenn die **AllowOverwrite** Eigenschaft auf "false" festgelegt ist und die angegebene Datenbank bereits vorhanden ist, ein Fehler auftritt.  
  
 Legen Sie die **Datei** Eigenschaft der **wiederherstellen** Befehl auf einem UNC-Pfad und Dateinamen für die Sicherungsdatei in der angegebenen Datenbank wiederhergestellt werden. Sie können auch Festlegen der **Kennwort** -Eigenschaft für die angegebene Sicherungsdatei. Wenn die **Kennwort** Eigenschaft auf einen nicht leeren Wert festgelegt ist, wird die Sicherungsdatei mithilfe des angegebenen Kennworts entschlüsselt. Wenn die Sicherungsdatei nicht verschlüsselt ist oder wenn das angegebene Kennwort nicht mit dem für die Entschlüsselung der Sicherungsdatei verwendeten Kennwort übereinstimmt, tritt ein Fehler auf.  
  
### <a name="restoring-security-settings"></a>Wiederherstellen von Sicherheitseinstellungen  
 Die **Sicherheit** Eigenschaft bestimmt, ob die **wiederherstellen** Befehl wird die sicherheitsdefinitionen wie Rollen und Berechtigungen, die definiert, die auf eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank. Die **Sicherheit** -Eigenschaft bestimmt auch, ob die **wiederherstellen** -Befehl enthält, die Windows-Benutzerkonten und Gruppen als Mitglieder der sicherheitsdefinitionen definiert sind, im Rahmen des Wiederherstellungsvorgangs.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*SkipMembership*|Einbeziehen von Sicherheitsdefinitionen und Ausschließen von Informationen zur Mitgliedschaft in der Datenbank.|  
|*CopyAll*|Einbeziehen von Sicherheitsdefinitionen und Informationen zur Mitgliedschaft in der Datenbank.|  
|*IgnoreSecurity*|Ausschließen von Sicherheitsdefinitionen aus der Datenbank.|  
  
### <a name="restoring-remote-partitions"></a>Wiederherstellen von Remotepartitionen  
 Für jede remotesicherungsdatei erstellt, die während eines zuvor ausgeführten **Sicherung** Befehl können Sie die zugeordnete Remotepartition wiederherstellen, dazu einen **Speicherort** Element in der **Speicherorte**Eigenschaft der **wiederherstellen** Befehl. Die [DataSourceType](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourcetype-element-xmla) -Eigenschaft für jedes **Speicherort** -Element muss ausgeschlossen oder explizit auf festgelegt *Remote*.  
  
 Für jedes angegebene **Speicherort** -Element, das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz kontaktiert der Remotedatenquelle, die im angegebenen die **DataSourceID** Eigenschaft zum Wiederherstellen der Partitionen, die in der remotesicherungsdatei definiert Angabe in der **Datei** Eigenschaft. Neben der **DataSourceID** und **Datei** Eigenschaften, die folgenden Eigenschaften stehen für die einzelnen **Speicherort** , das zum Wiederherstellen einer Remotepartition verwendet:  
  
-   Überschreiben Sie die Verbindungszeichenfolge für die Remotedatenquelle, die im angegebenen **DataSourceID**, können Sie festlegen der **"ConnectionString"** Eigenschaft der **Speicherort** Element ein andere Verbindungszeichenfolge. Die **wiederherstellen** Befehl verwendet die Verbindungszeichenfolge, die in enthalten ist dann der **"ConnectionString"** Eigenschaft. Wenn **"ConnectionString"** nicht angegeben ist, die **wiederherstellen** Befehl verwendet die Verbindungszeichenfolge, die in der Sicherungsdatei für die angegebene Remotedatenquelle gespeichert. Sie können die **"ConnectionString"** Einstellung aus, um eine Remotepartition auf einer anderen Remoteinstanz zu verschieben. Allerdings können keine der **"ConnectionString"** Einstellung aus, um eine Remotepartition auf die gleiche Instanz wiederherstellen, die die wiederhergestellte Datenbank enthält. Das heißt, Sie können keine der **"ConnectionString"** Eigenschaft, um eine Remotepartition in eine lokale Partition umzuwandeln.  
  
-   Für jeden ursprünglichen Ordner zum Speichern von Remotepartitionen auf der Remotedatenquelle verwendet wird, können Sie angeben einer [Ordner](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/folder-element-xmla) Element an den neuen Ordner, in dem alle im ursprünglichen Ordner gespeicherte Remotepartitionen wiederherzustellen. Wenn eine **Ordner** Element nicht angegeben ist, die **wiederherstellen** Befehl verwendet den ursprünglichen Ordner, die für die in der remotesicherungsdatei enthaltenen Remotepartitionen angegeben.  
  
### <a name="relocating-rolap-objects"></a>Verschieben von ROLAP-Objekten  
 Die **wiederherstellen** Befehl kann nicht wiederhergestellt, Aggregationen oder Daten für Objekte, die ROLAP-Speichermodus verwenden, da solche Informationen in Tabellen in einer zugrunde liegenden relationalen Datenquelle gespeichert werden. Jedoch können die Metadaten für ROLAP-Objekte wiederhergestellt werden. Die Metadaten für ROLAP-Objekte Wiederherstellen der **wiederherstellen** Befehl wird erneut die Tabellenstruktur in einer relationalen Datenquelle erstellt.  
  
 Können Sie die **Speicherort** Element in einem **wiederherstellen** Befehl aus, um ROLAP-Objekte zu verschieben. Für jede **Speicherort** Element zum Verschieben einer Datenquelle verwendet die **DataSourceType** Eigenschaft muss explizit festgelegt werden, um *lokalen*. Außerdem müssen Sie festlegen der **"ConnectionString"** Eigenschaft der **Speicherort** Element an der Verbindungszeichenfolge für den neuen Speicherort. Während der Wiederherstellung der **wiederherstellen** Befehl ersetzt die Verbindungszeichenfolge für die Datenquelle, die durch identifiziert die **DataSourceID** Eigenschaft der **Speicherort** Element mit dem Wert der **"ConnectionString"** Eigenschaft der **Speicherort** Element.  
  
##  <a name="synchronizing_databases"></a> Synchronisieren von Datenbanken  
 Die **synchronisieren** -Befehl synchronisiert die Daten und Metadaten eines angegebenen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank mit einer anderen Datenbank. Die **synchronisieren** -Befehl weist mehrere Eigenschaften, mit denen Sie die Quelldatenbank angeben, wie sicherheitsdefinitionen, die zu synchronisierenden Remotepartitionen und die Synchronisierung von ROLAP-Objekte synchronisiert.  
  
> [!NOTE]  
>  Die **synchronisierende** -Befehl kann nur von Serveradministratoren und Datenbankadministratoren ausgeführt werden. Sowohl die Quell- als auch die Zieldatenbank müssen den gleichen Datenbank-Kompatibilitätsgrad besitzen.  
  
### <a name="specifying-the-source-database"></a>Angeben der Quelldatenbank  
 Die [Quelle](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) Eigenschaft der **synchronisieren** -Befehl enthält zwei Eigenschaften, **"ConnectionString"** und **Objekt**. Die **"ConnectionString"** Eigenschaft enthält die Verbindungszeichenfolge der Instanz, die die Quelldatenbank enthält und die **Objekt** Eigenschaft enthält den Objektbezeichner für die Quelldatenbank.  
  
 Die Zieldatenbank ist die aktuelle Datenbank für die Sitzung, in dem die **synchronisieren** -Befehl ausgeführt wird.  
  
 Wenn die **ApplyCompression** Eigenschaft der **synchronisieren** Befehl festgelegt ist auf "true", die aus der Quelle gesendete Informationen wird die Datenbank in die Zieldatenbank vor dem Senden komprimiert.  
  
### <a name="synchronizing-security-settings"></a>Synchronisieren von Sicherheitseinstellungen  
 Die [SynchronizeSecurity](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla) Eigenschaft bestimmt, ob die **synchronisieren** -Befehl synchronisiert die sicherheitsdefinitionen wie Rollen und Berechtigungen, die für die Quelldatenbank definiert. Die **SynchronizeSecurity** -Eigenschaft bestimmt auch, ob die **zusammenarbeitsszenarien konzipiert sind** -Befehl enthält, die Windows-Benutzerkonten und Gruppen als Mitglieder der sicherheitsdefinitionen definiert.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*SkipMembership*|Einbeziehen von Sicherheitsdefinitionen und Ausschließen von Informationen zur Mitgliedschaft in der Zieldatenbank.|  
|*CopyAll*|Einbeziehen von Sicherheitsdefinitionen und Informationen zur Mitgliedschaft in der Zieldatenbank.|  
|*IgnoreSecurity*|Ausschließen von Sicherheitsdefinitionen aus der Zieldatenbank.|  
  
### <a name="synchronizing-remote-partitions"></a>Synchronisieren von Remotepartitionen  
 Für jede Remotedatenquelle, die in der Quelldatenbank vorhanden ist, können Sie jede zugeordnete Remotepartition synchronisieren, indem einschließlich einer **Speicherort** Element in der **Speicherorte** Eigenschaft der  **Synchronisieren von** Befehl. Für jede **Speicherort** -Element, das **DataSourceType** Eigenschaft muss ausgeschlossen oder explizit auf festgelegt *Remote*.  
  
 Definieren, und eine Verbindung mit einer Remotedatenquelle in der Zieldatenbank, die **synchronisieren** Befehl verwendet die Verbindungszeichenfolge, die definiert, der **"ConnectionString"** Eigenschaft der **Speicherort**  Element. Die **synchronisieren** -Befehl verwendet dann die **DataSourceID** Eigenschaft der **Speicherort** Element, um die zu synchronisierenden Remotepartitionen zu identifizieren. Die **synchronisieren**-Befehl synchronisiert die Remotepartitionen in der Remotedatenquelle, die im angegebenen die **DataSourceID** Eigenschaft für die Quelldatenbank mit der Remotedatenquelle, die in der angegeben **DataSourceID** Eigenschaft in der Zieldatenbank.  
  
 Sie können auch angeben, für die einzelnen ursprünglichen Ordner zum Speichern von Remotepartitionen auf der Remotedatenquelle der Quelldatenbank verwendet wird, eine **Ordner** Element in der **Speicherort** Element. Die **Ordner** -Element gibt an, den neuen Ordner für die Zieldatenbank, in dem alle im ursprünglichen Ordner in der Remotedatenquelle gespeicherten Remotepartitionen synchronisiert. Wenn eine **Ordner** Element nicht angegeben wird, der Synchronize-Befehl verwendet die ursprünglichen Ordner angegeben wird, für die remote-Partitionen, die in der Quelldatenbank enthalten sind.  
  
### <a name="synchronizing-rolap-objects"></a>Synchronisieren von ROLAP-Objekten  
 Die **synchronisierende** Befehl kann nicht synchronisiert, Aggregationen oder Daten für Objekte, die ROLAP-Speichermodus verwenden, da solche Informationen in Tabellen in einer zugrunde liegenden relationalen Datenquelle gespeichert werden. Jedoch können die Metadaten für ROLAP-Objekte synchronisiert werden. Zum Synchronisieren der Metadaten, die **synchronisieren** Befehl erstellt die Tabellenstruktur in einer relationalen Datenquelle.  
  
 Sie können die **Speicherort** Element in einem Synchronize-Befehl zum Synchronisieren von ROLAP-Objekten. Für jede **Speicherort** Element zum Verschieben einer Datenquelle verwendet die **DataSourceType** Eigenschaft muss explizit festgelegt werden, um *lokalen*. . Außerdem müssen Sie festlegen der **"ConnectionString"** Eigenschaft der **Speicherort** Element an der Verbindungszeichenfolge für den neuen Speicherort. Während der Synchronisierung der **synchronisieren** Befehl ersetzt die Verbindungszeichenfolge für die Datenquelle, die durch identifiziert die **DataSourceID** Eigenschaft der **Speicherort** Element mit dem Wert, der die **"ConnectionString"** Eigenschaft der **Speicherort** Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Backup-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [Restore-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)   
 [Synchronize-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
