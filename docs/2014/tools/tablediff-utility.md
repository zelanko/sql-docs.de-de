---
title: Hilfsprogramm tablediff-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- comparing data
- tablediff utility
- tables [SQL Server replication]
- table comparisons [SQL Server]
- command prompt utilities [SQL Server], tablediff
- troubleshooting [SQL Server replication], non-convergence
- non-convergence [SQL Server]
ms.assetid: 3c3cb865-7a4d-4d66-98f2-5935e28929fc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cb8b8bec38b428ca7b2eea5166867141b34a2405
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "68185973"
---
# <a name="tablediff-utility"></a>tablediff (Hilfsprogramm)
  Mit dem Hilfsprogramm **tablediff** wird verglichen, ob die Daten in zwei Tabellen konvergent sind. Das Hilfsprogramm eignet sich besonders zur Problembehandlung bei mangelnder Konvergenz in einer Replikationstopologie. Dieses Hilfsprogramm kann an der Eingabeaufforderung oder in einer Batchdatei verwendet werden, um die folgenden Aufgaben auszuführen:  
  
-   Durchführen eines zeilenweisen Vergleichs einer Quelltabelle in einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz, die als Replikationsherausgeber fungiert, mit der Zieltabelle in einer oder mehreren [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanzen, die als Replikationsabonnenten fungieren.  
  
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
  
 **-sourceServer** *source_server_name*[**\\**_instance_name_]  
 Der Name des Quellservers. Geben Sie den _\_Quell Server\_Namen_ für die Standard [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Instanz von an. Geben Sie den**\\**_Instanznamen\__ des _\_Quell Server\_namens_für eine benannte Instanz von an. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
 **-sourcedatabase** *source_database*  
 Der Name der Quelldatenbank.  
  
 **-sourcetable** *source_table_name*  
 Der Name der zu überprüfenden Quelldatenbank.  
  
 **-sourceschema** *source_schema_name*  
 Der Schemabesitzer der Quelltabelle. Standardmäßig wird dbo als Tabellenbesitzer angenommen.  
  
 **-sourcepassword** *source_password*  
 Das Kennwort für den Anmeldenamen, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Quellserver herzustellen.  
  
> [!IMPORTANT]  
>  Anmeldeinformationen sollten, sofern möglich, zur Laufzeit angegeben werden. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, sollten Sie die Datei an einem sicheren Ort speichern, um den unbefugten Zugriff zu vermeiden.  
  
 **-sourceuser** *source_login*  
 Der Anmeldename, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Quellserver herzustellen. Wenn *Quellanmeldename* nicht angegeben wird, wird die Windows-Authentifizierung zum Herstellen der Verbindung mit dem Quellserver verwendet. [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 **-sourcelocked**  
 Die Quelltabelle wird während des Vergleichs mit den Tabellenhinweisen TABLOCK und HOLDLOCK gesperrt.  
  
 **-DestinationServer** *destination_server_name*[**\\**_Instanzname\__]  
 Der Name des Zielservers. Angeben von *Zielservername* für die Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Geben Sie den _Namen der Ziel\_Server\_Namen_**\\**-_Instanz\__ für eine benannte Instanz von an. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
 **-destinationdatabase** *subscription_database*  
 Der Name der Zieldatenbank.  
  
 **-destinationtable** *destination_table*  
 Entspricht dem Namen der Zieltabelle.  
  
 **-destinationschema** *destination_schema_name*  
 Der Schemabesitzer der Zieltabelle. Standardmäßig wird dbo als Tabellenbesitzer angenommen.  
  
 **-destinationpassword** *destination_password*  
 Das Kennwort für den Anmeldenamen, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Zielserver herzustellen.  
  
> [!IMPORTANT]  
>  Anmeldeinformationen sollten, sofern möglich, zur Laufzeit angegeben werden. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, sollten Sie die Datei an einem sicheren Ort speichern, um den unbefugten Zugriff zu vermeiden.  
  
 **-destinationuser** *destination_login*  
 Der Anmeldename, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Zielserver herzustellen. Wenn *Zielanmeldename* nicht angegeben wird, wird die Windows-Authentifizierung zum Herstellen der Verbindung mit dem Server verwendet. [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 **-destinationlocked**  
 Die Zieltabelle wird während des Vergleichs mit den Tabellenhinweisen TABLOCK und HOLDLOCK gesperrt.  
  
 **-b** *large_object_bytes*  
 Ist die Anzahl von Bytes, die für LOB-Datentyp-Spalten verglichen werden sollen, darunter: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)` und `varbinary(max)`. *large_object_bytes* wird standardmäßig auf die Größe der Spalte festgelegt. Alle Daten über *large_object_bytes* werden nicht überprüft.  
  
 **-bf** *number_of_statements*  
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
  
 **-ri** *retry_interval*  
 Gibt das Intervall (in Sekunden) zwischen den Wiederholungen an.  
  
 **-strict**  
 Für Quell- und Zielschema wird ein strenger Vergleich durchgeführt.  
  
 **-t** *connection_timeouts*  
 Legt das Verbindungstimeout (in Sekunden) für Verbindungen zwischen dem Quellserver und dem Zielserver fest.  
  
## <a name="return-value"></a>Rückgabewert  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Erfolg|  
|**1**|Schwerwiegender Fehler|  
|**2**|Tabellenunterschiede|  
  
## <a name="remarks"></a>Bemerkungen  
 Das Hilfsprogramm **tablediff** kann für Server, auf denen[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nicht installiert ist, nicht verwendet werden.  
  
 Tabellen, die Spalten des Datentyps `sql_variant` enthalten, werden nicht unterstützt.  
  
 Standardmäßig unterstützt das Hilfsprogramm **tablediff** die folgenden Datentypzuordnungen zwischen Quell- und Zielspalten.  
  
|Quelldatentyp|Zieldatentyp|  
|----------------------|---------------------------|  
|`tinyint`|`smallint`, `int`oder `bigint`|  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Überprüfen replizierter Tabellen auf Unterschiede &#40;Replikationsprogrammierung&#41;](../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)  
  
  
