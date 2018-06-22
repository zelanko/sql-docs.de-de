---
title: TableDiff (Hilfsprogramm) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- comparing data
- tablediff utility
- tables [SQL Server replication]
- table comparisons [SQL Server]
- command prompt utilities [SQL Server], tablediff
- troubleshooting [SQL Server replication], non-convergence
- non-convergence [SQL Server]
ms.assetid: 3c3cb865-7a4d-4d66-98f2-5935e28929fc
caps.latest.revision: 29
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 851ba198020abf234c793ad65acf3f5dbbcd8e2f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058209"
---
# <a name="tablediff-utility"></a>tablediff (Hilfsprogramm)
  Mit dem Hilfsprogramm **tablediff** wird verglichen, ob die Daten in zwei Tabellen konvergent sind. Das Hilfsprogramm eignet sich besonders zur Problembehandlung bei mangelnder Konvergenz in einer Replikationstopologie. Dieses Hilfsprogramm kann an der Eingabeaufforderung oder in einer Batchdatei verwendet werden, um die folgenden Aufgaben auszuführen:  
  
-   Zeilenweiser Vergleich einer Quelltabelle in einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz, die als Replikationsverleger agiert, mit der Zieltabelle in einer oder mehreren [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanzen, die als Replikationsabonnenten agieren.  
  
-   Ausführen eines schnellen Vergleichs, indem nur Zeilenanzahl und Schema verglichen werden.  
  
-   Ausführen spaltenweiser Vergleiche.  
  
-   Generieren eines [!INCLUDE[tsql](../includes/tsql-md.md)] -Skripts, um Abweichungen auf dem Zielserver zu beheben und auf diese Weise die Konvergenz von Quell- und Zieltabelle herzustellen.  
  
-   Protokollieren von Ergebnissen in einer Ausgabedatei oder einer Tabelle in der Zieldatenbank.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      tablediff   
[ -? ] |   
{  
        -sourceserversource_server_name[\instance_name]  
        -sourcedatabasesource_database-sourcetablesource_table_name   
    [ -sourceschemasource_schema_name ]  
    [ -sourcepasswordsource_password ]  
    [ -sourceusersource_login ]  
    [ -sourcelocked ]  
        -destinationserverdestination_server_name[\instance_name]  
        -destinationdatabasesubscription_database-destinationtabledestination_table   
    [ -destinationschemadestination_schema_name ]  
    [ -destinationpassworddestination_password ]  
    [ -destinationuserdestination_login ]  
    [ -destinationlocked ]  
    [ -blarge_object_bytes ]   
    [ -bfnumber_of_statements ]   
    [ -c ]   
    [ -dt ]   
    [ -ettable_name ]   
    [ -f [ file_name ] ]   
    [ -ooutput_file_name ]   
    [ -q ]   
    [ -rcnumber_of_retries ]   
    [ -riretry_interval ]   
    [ -strict ]  
    [ -tconnection_timeouts ]   
}  
```  
  
## <a name="arguments"></a>Argumente  
 [ **-?** ]  
 Gibt die Liste unterstützter Parameter zurück.  
  
 **-sourceserver** *source_server_name*[**\\***instance_name*]  
 Der Name des Quellservers. Geben Sie *Name des Quellservers* für die Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]an. Geben Sie *source_server_name***\\***instance_name* für eine benannte Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] an.  
  
 **-sourcedatabase** *Quelldatenbank*  
 Der Name der Quelldatenbank.  
  
 **-sourcetable** *Name der Quelltabelle*  
 Der Name der zu überprüfenden Quelldatenbank.  
  
 **-sourceschema** *Quellschemaname*  
 Der Schemabesitzer der Quelltabelle. Standardmäßig wird dbo als Tabellenbesitzer angenommen.  
  
 **-sourcepassword** *Quellkennwort*  
 Das Kennwort für den Anmeldenamen, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Quellserver herzustellen.  
  
> [!IMPORTANT]  
>  Anmeldeinformationen sollten, sofern möglich, zur Laufzeit angegeben werden. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, sollten Sie die Datei an einem sicheren Ort speichern, um den unbefugten Zugriff zu vermeiden.  
  
 **-sourceuser** *Quellanmeldename*  
 Der Anmeldename, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Quellserver herzustellen. Wenn *Quellanmeldename* nicht angegeben wird, wird die Windows-Authentifizierung zum Herstellen der Verbindung mit dem Quellserver verwendet. [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 **-sourcelocked**  
 Die Quelltabelle wird während des Vergleichs mit den Tabellenhinweisen TABLOCK und HOLDLOCK gesperrt.  
  
 **-destinationserver** *destination_server_name*[**\\instance_name*]  
 Der Name des Zielservers. Angeben von *Zielservername* für die Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Geben Sie *destination_server_name***\\***instance_name* für eine benannte Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] an.  
  
 **-destinationdatabase** *Abonnementdatenbank*  
 Der Name der Zieldatenbank.  
  
 **-destinationtable** *Zieltabelle*  
 Entspricht dem Namen der Zieltabelle.  
  
 **-destinationschema** *Zielschemaname*  
 Der Schemabesitzer der Zieltabelle. Standardmäßig wird dbo als Tabellenbesitzer angenommen.  
  
 **-destinationpassword** *Zielkennwort*  
 Das Kennwort für den Anmeldenamen, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Zielserver herzustellen.  
  
> [!IMPORTANT]  
>  Anmeldeinformationen sollten, sofern möglich, zur Laufzeit angegeben werden. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, sollten Sie die Datei an einem sicheren Ort speichern, um den unbefugten Zugriff zu vermeiden.  
  
 **-destinationuser** *Zielanmeldename*  
 Der Anmeldename, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Zielserver herzustellen. Wenn *Zielanmeldename* nicht angegeben wird, wird die Windows-Authentifizierung zum Herstellen der Verbindung mit dem Server verwendet. [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 **-destinationlocked**  
 Die Zieltabelle wird während des Vergleichs mit den Tabellenhinweisen TABLOCK und HOLDLOCK gesperrt.  
  
 **-b** *large_object_bytes*  
 Ist die Anzahl der Bytes für LOB-Datentyp-Spalten vergleichen die umfasst: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)` und `varbinary(max)`. *large_object_bytes* wird standardmäßig auf die Größe der Spalte festgelegt. Alle Daten über *large_object_bytes* werden nicht überprüft.  
  
 **-bf**  *number_of_statements*  
 Die Anzahl der [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen, die in die aktuelle [!INCLUDE[tsql](../includes/tsql-md.md)] -Skriptdatei geschrieben werden können, wenn die Option **-f** verwendet wird. Wenn die Anzahl der [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen *number_of_statements*überschreitet, wird eine neue [!INCLUDE[tsql](../includes/tsql-md.md)] -Skriptdatei erstellt.  
  
 **-c**  
 Vergleicht Unterschiede auf Spaltenebene.  
  
 **-dt**  
 Löscht die in *table_name*angegebene Ergebnistabelle, wenn die Tabelle bereits vorhanden ist.  
  
 **-et** *table_name*  
 Gibt den Namen der zu erstellenden Ergebnistabelle an. Wenn diese Tabelle bereits vorhanden ist, muss **-DT** verwendet werden; andernfalls schlägt der Vorgang fehl.  
  
 **-f** [ *file_name* ]  
 Generiert ein [!INCLUDE[tsql](../includes/tsql-md.md)] -Skript, um die Konvergenz zwischen der Tabelle auf dem Zielserver und der Tabelle auf dem Quellserver herzustellen. Optional können Sie einen Namen und einen Pfad für die generierte [!INCLUDE[tsql](../includes/tsql-md.md)] -Skriptdatei angeben. Wurde *file_name* nicht angegeben, wird die [!INCLUDE[tsql](../includes/tsql-md.md)] -Skriptdatei in dem Verzeichnis erstellt, in dem das Hilfsprogramm ausgeführt wird.  
  
 **-o** *output_file_name*  
 Gibt den vollständigen Namen und Pfad der Ausgabedatei an.  
  
 **-q**  
 Ausführen eines schnellen Vergleichs, indem nur Zeilenanzahl und Schema verglichen werden.  
  
 **-rc** *number_of_retries*  
 Gibt an, wie oft das Hilfsprogramm einen fehlgeschlagenen Vorgang wiederholt.  
  
 **-ri**  *retry_interval*  
 Gibt das Intervall (in Sekunden) zwischen den Wiederholungen an.  
  
 **-strict**  
 Für Quell- und Zielschema wird ein strenger Vergleich durchgeführt.  
  
 **-t** *connection_timeouts*  
 Legt das Verbindungstimeout (in Sekunden) für Verbindungen zwischen dem Quellserver und dem Zielserver fest.  
  
## <a name="return-value"></a>Rückgabewert  
  
|value|Description|  
|-----------|-----------------|  
|**0**|Success|  
|**1**|Schwerwiegender Fehler|  
|**2**|Tabellenunterschiede|  
  
## <a name="remarks"></a>Hinweise  
 Das Hilfsprogramm **tablediff** kann für Server, auf denen[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht installiert ist, nicht verwendet werden.  
  
 Tabellen mit `sql_variant` datentypspalten werden nicht unterstützt.  
  
 Standardmäßig unterstützt das Hilfsprogramm **tablediff** die folgenden Datentypzuordnungen zwischen Quell- und Zielspalten.  
  
|Quelldatentyp|Zieldatentyp|  
|----------------------|---------------------------|  
|`tinyint`|`smallint`, `int` oder `bigint`|  
|`smallint`|`int` oder `bigint`|  
|`int`|`bigint`|  
|`timestamp`|`varbinary`|  
|`varchar(max)`|`text`|  
|`nvarchar(max)`|`ntext`|  
|`varbinary(max)`|`image`|  
|`text`|`varchar(max)`|  
|`ntext`|`nvarchar(max)`|  
|`image`|`varbinary(max)`|  
  
 Verwenden Sie die Option **-strict** , wenn Sie diese Zuordnungen nicht zulassen und eine strenge Überprüfung durchführen möchten.  
  
 Die Quelltabelle bei dem Vergleich muss mindestens eine Primärschlüssel-, Identitäts- oder ROWGUID-Spalte enthalten. Wenn Sie die Option **-strict** verwenden, muss die Zieltabelle ebenfalls eine Primärschlüssel-, Identitäts- oder ROWGUID-Spalte enthalten.  
  
 Das [!INCLUDE[tsql](../includes/tsql-md.md)] -Skript, das generiert wurde, um die Konvergenz der Zieltabelle herzustellen, enthält die folgenden Datentypen nicht:  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `timestamp`  
  
-   **xml**  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
## <a name="permissions"></a>Berechtigungen  
 Für den Vergleich von Tabellen benötigen Sie SELECT ALL-Berechtigungen für die zu vergleichenden Tabellenobjekte.  
  
 Damit Sie die Option **-et** verwenden können, müssen Sie ein Mitglied der festen Datenbankrolle db_owner sein oder zumindest über die CREATE TABLE-Berechtigung für die Abonnementdatenbank und die ALTER-Berechtigung für das Zielbesitzerschema auf dem Zielserver verfügen.  
  
 Damit Sie die Option **-dt** verwenden können, müssen Sie ein Mitglied der festen Datenbankrolle db_owner sein oder zumindest über die ALTER-Berechtigung für das Zielbesitzerschema auf dem Zielserver verfügen.  
  
 Damit Sie die Option **-o** oder **-f** verwenden können, müssen Sie über Schreibberechtigungen für das angegebene Dateiverzeichnis verfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Überprüfen replizierter Tabellen auf Unterschiede &#40;Replikationsprogrammierung&#41;](../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)  
  
  