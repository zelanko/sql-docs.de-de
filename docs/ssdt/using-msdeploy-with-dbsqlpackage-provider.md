---
title: Verwenden von MSDeploy mit dem dbSqlPackage-Anbieter | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 04/26/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 213b91ab-03e9-431a-80f0-17eed8335abe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 128e1feeb3b344a21dbb682d4d41d402060ab1ff
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54256945"
---
# <a name="using-msdeploy-with-dbsqlpackage-provider"></a>Verwenden von MSDeploy mit dem dbSqlPackage-Anbieter
**dbSqlPackage** ist ein **MSDeploy**-Anbieter, der Ihnen die Interaktion mit SQL Server- oder SQL Azure-Datenbanken ermöglicht. **dbSqlPackage** unterstützt die folgenden Aktionen:  
  
-   **Extract:** Erstellt eine Datenbankmomentaufnahme (DACPAC-Datei) von einer SQL Server- oder SQL Azure-Livedatenbank  
  
-   **Publish:** Aktualisiert ein Datenbankschema inkrementell, sodass dieses dem Schema einer DACPAC-Quelldatei entspricht  
  
-   **DeployReport:** Erstellt einen XML-Bericht der Änderungen, die durch eine Veröffentlichungsaktion vorgenommen würden  
  
-   **Script:** Erstellt ein Transact\-SQL-Skript, das dem von der Veröffentlichungsaktion ausgeführten Skript entspricht  
  
Weitere Informationen über DACFx finden Sie in der Dokumentation zur verwalteten DACFx-API unter [https://msdn.microsoft.com/library/microsoft.sqlserver.dac.aspx](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.aspx) oder in [SqlPackage.exe](../tools/sqlpackage.md) (DACFx-Befehlszeilentool).  
  
> [!IMPORTANT]  
> Die „dbSqlPackage“-Anbieterfunktion wird aus der nächsten Hauptversion von Visual Studio entfernt. Informationen zur Datenbankveröffentlichung mithilfe von Web Deploy finden Sie unter [dbDacFx-Anbieter für die inkrementelle Datenbankveröffentlichung](https://www.iis.net/learn/publish/using-web-deploy/dbdacfx-provider-for-incremental-database-publishing).  
  
## <a name="command-line-syntax"></a>Befehlszeilensyntax  
**MSDeploy** mit dem **dbSqlPackage**-Anbieter verwendet eine Befehlszeile im folgenden Format:  
  
```  
  
MSDeploy -verb: MSDeploy-verb -source:dbSqlPackage="Input"[,dbSqlPackage-source-parameters] -dest:dpSqlPackage="Input"[,dbSqlPackage-target-parameters]  
```  
  
## <a name="ms-deploy-verbs"></a>MS-Deploy-Verben  
Sie verwenden den Switch **-verb** in der MS Deploy-Befehlszeile, um MS Deploy-Verben anzugeben. Der **dbSqlPackage**-Anbieter unterstützt die folgenden **MSDeploy**-Verben:  
  
|Verb|und Beschreibung|  
|--------|---------------|  
|dump|Stellt Informationen über eine in einer DACPAC-Datei enthaltene Quelldatenbank bereit, z. B. Namen, Versionsnummer und Beschreibung. Geben Sie die Quelldatenbank im folgenden Format in der Befehlszeile an:<br /><br />**msdeploy -verb:dump -source:dbSqlPackage="**_DACPAC-Dateipfad_**"**|  
|sync|Gibt die dbSqlPackage-Aktionen im folgenden Format in der Befehlszeile an:<br /><br />**msdeploy -verb:sync -source:dbSqlPackage**="Eingabe" _[,DbSqlPackage-source-parameters] -_**dest:dbSqlPackage**="Eingabe" *[,DbSqlPackage-destination-parameters]*<br /><br />Weitere Informationen finden Sie in den folgenden Abschnitten zu den gültigen Quell- und Zielparametern für das sync-Verb.|  
  
## <a name="dbsqlpackage-source"></a>dbSqlPackage-Quelle  
Der **dbSqlPackage**-Anbieter akzeptiert eine Eingabe, die entweder einer gültigen SQL Server- oder SQL Azure-Verbindungszeichenfolge bzw. einem Pfad zu einer DACPAC-Datei auf dem Datenträger entspricht.  Die Syntax zum Angeben der Eingabequelle für den Anbieter lautet wie folgt:  
  
|Eingabe|Default|und Beschreibung|  
|---------|-----------|---------------|  
|**-source:dbSqlPackage=**{*input*}|**N/V**|*input* ist eine gültige SQL Server- oder SQL Azure-Verbindungszeichenfolge bzw. ein Pfad zu einer DACPAC-Datei auf dem Datenträger.<br /><br />**HINWEIS:** Die einzigen Verbindungszeichenfolgen-Eigenschaften, die bei der Verwendung einer Verbindungszeichenfolge als Eingabequelle unterstützt werden, sind *InitialCatalog, DataSource, UserID, Password, IntegratedSecurity, Encrypt, TrustServerCertificate* und *ConnectionTimeout*.|  
  
Wenn die Eingabequelle eine Verbindungszeichenfolge zu einer SQL Server- oder Azure SQL-Livedatenbank ist, extrahiert **dbSqlPackage** eine Datenbankmomentaufnahme in Form einer DACPAC-Datei aus einer SQL Server- oder SQL Azure-Livedatenbank.  
  
Die **Source**-Parameter sind Folgende:  
  
|Parameter|Default|und Beschreibung|  
|-------------|-----------|---------------|  
|**Profil**:{ *string*}|–|Gibt den Dateipfad zu einem DAC-Veröffentlichungsprofil an. Im Profil ist eine Auflistung von Eigenschaften und Variablen definiert, die beim Generieren der resultierenden DACPAC-Datei verwendet werden. Das Veröffentlichungsprofil wird an das Ziel übergeben und beim Ausführen von einer der Aktionen **Publish**, **Script** oder **DeployReport** verwendet.|  
|**DacApplicationName**={ *string* }|Datenbankname|Definiert den in den DACPAC-Metadaten zu speichernden Anwendungsnamen. Die Standardzeichenfolge entspricht dem Datenbanknamen.|  
|**DacMajorVersion** ={*integer*}|**1**|Definiert die in den DACPAC-Metadaten zu speichernde Hauptversion.|  
|**DacMinorVersion**={*integer*}|**0**|Definiert die in den DACPAC-Metadaten zu speichernde Nebenversion.|  
|**DacApplicationDescription**={ *string* }|–|Definiert die in den DACPAC-Metadaten zu speichernde Anwendungsbeschreibung.|  
|**ExtractApplicationScopedObjectsOnly={True &#124; False}**|**Wahr**|Beim Wert **True** werden nur Objekte im Anwendungsbereich aus der Quelle extrahiert. Beim Wert **False** werden sowohl Objekte im Anwendungsbereich als auch Objekte außerhalb des Anwendungsbereichs extrahiert.|  
|**ExtractReferencedServerScopedElements={True &#124; False}**|**Wahr**|Beim Wert **True** werden Anmelde-, Serverüberwachungs- und Anmeldeinformationsobjekte extrahiert, auf die von Quelldatenbankobjekten verwiesen wird.|  
|**ExtractIgnorePermissions={True &#124; False}**|**False**|Bei **True** wird das Extrahieren von Berechtigungen für alle extrahierten Objekte ignoriert; bei **False** geschieht dies nicht.|  
|**ExtractStorage={File&#124;Memory}**|**File**|Gibt den Typ des Hintergrundspeichers an, der während der Extraktion für das Schemamodell verwendet wird.|  
|**ExtractIgnoreExtendedProperties={True&#124;False}**|**False**|Gibt an, ob erweiterte Eigenschaften ignoriert werden sollen.|  
|**VerifyExtraction = {True&#124;False}**|**False**|Gibt an, ob die extrahierte DACPAC-Datei überprüft werden soll.|  
  
## <a name="dbsqlpackage-destination"></a>DbSqlPackage-Ziel  
Der **dbSqlPackage**-Anbieter akzeptiert eine gültige SQL Server- oder SQL Azure-Verbindungszeichenfolge bzw. einen Pfad zu einer DACPAC-Datei auf dem Datenträger als Zieleingabe.  Die Syntax zum Angeben des Ziels für den Anbieter lautet wie folgt:  
  
|Eingabe|Default|und Beschreibung|  
|---------|-----------|---------------|  
|-**dest:dbSqlPackage**={*input*}|–|*input* ist eine gültige SQL Server- oder SQL Azure-Verbindungszeichenfolge bzw. ein vollständiger oder teilweiser Pfad zu einer DACPAC-Datei auf dem Datenträger. Wenn *input* einem Dateipfad entspricht, können keine weiteren Parameter angegeben werden.|  
  
Die folgenden **Destination**-Parameter sind für alle **dbSqlPackage**-Vorgänge verfügbar:  
  
|Eigenschaft|Default|und Beschreibung|  
|------------|-----------|---------------|  
|**Action={Publish&#124;DeployReport&#124;Script}**|–|Ein optionaler Parameter, der die für **Destination** auszuführende Aktion angibt.|  
|**AllowDropBlockingAssemblies ={True &#124; False}**|**False**|Gibt an, ob blockierende Assemblys durch die **SqlClr**-Veröffentlichung im Rahmen des Bereitstellungsplans gelöscht werden. Wenn die verweisende Assembly gelöscht werden muss, werden Assemblyupdates durch blockierende oder verweisende Assemblys standardmäßig blockiert.|  
|**AllowIncompatiblePlatform={True &#124; False}**|**False**|Gibt an, ob die Veröffentlichungsaktion trotz möglicherweise inkompatibler SQL Server-Plattformen fortgesetzt werden soll.|  
|**BackupDatabaseBeforeChanges={True &#124; False}**|**False**|Sichert die Datenbank, bevor Änderungen bereitgestellt werden.|  
|**BlockOnPossibleDataLoss={ True &#124; False}**|**Wahr**|Gibt an, ob die Veröffentlichungssequenz beendet wird, wenn durch den Veröffentlichungsvorgang ein Datenverlust verursacht werden könnte.|  
|**BlockWhenDriftDetected={ True &#124; False}**|**Wahr**|Gibt an, ob die Aktualisierung einer Datenbank, deren Schema nicht mehr mit der Registrierung übereinstimmt oder aus der Registrierung entfernt wurde, blockiert wird.|  
|**CommentOutSetVarDeclarations= {True &#124; False}**|**False**|Gibt an, ob **SETVAR**-Variablendeklarationen im generierten Veröffentlichungsskript auskommentiert werden. Dies empfiehlt sich beispielsweise, wenn Sie ein Tool wie **SQLCMD.exe** verwenden möchten, um die Werte bei der Veröffentlichung in der Befehlszeile anzugeben.|  
|**CompareUsingTargetCollation={ True &#124; False}**|**False**|Diese Einstellung bestimmt, wie die Datenbanksortierung während der Bereitstellung behandelt wird. Standardmäßig wird die Sortierung der Zieldatenbank aktualisiert, wenn sie nicht mit der durch die Quelle angegebenen Sortierung übereinstimmt.  Wenn diese Option festgelegt ist, sollte die Sortierung der Zieldatenbank (oder des Servers) verwendet werden.|  
|**CreateNewDatabase={ True &#124; False}**|**False**|Gibt an, ob die Zieldatenbank beim Veröffentlichen in einer Datenbank aktualisiert bzw. gelöscht und neu erstellt werden soll.|  
|**DeployDatabaseInSingleUserMode={ True &#124; False}**|**False**|Beim Wert **True** wird die Datenbank vor der Bereitstellung in den Einzelbenutzermodus geschaltet.|  
|**DisableAndReenableDdlTriggers={True &#124; False}**|**Wahr**|Gibt an, ob DDL-Trigger (Data Definition Language) am Anfang des Veröffentlichungsprozesses deaktiviert und am Ende der Veröffentlichungsaktion erneut aktiviert werden.|  
|**DoNotAlterChangeDataCaptureObjects={ True &#124; False}**|**Wahr**|Beim Wert **True** werden Change Data Capture-Objekte nicht geändert.|  
|**DoNotAlterReplicatedObjects=( True &#124; False}**|**Wahr**|Gibt an, ob replizierte Objekte während der Überprüfung identifiziert werden.|  
|**DropConstraintsNotInSource= {True &#124; False}**|**Wahr**|Gibt an, ob durch die Veröffentlichungsaktion Einschränkungen, die in der Datenbankmomentaufnahme (DACPAC-Datei) nicht vorhanden sind, bei der Veröffentlichung in einer Datenbank aus der Zieldatenbank gelöscht werden.|  
|**DropDmlTriggersNotInSource= {True &#124; False}**|**Wahr**|Gibt an, ob durch die Veröffentlichungsaktion DML-Trigger (Data Manipulation Language), die in der Datenbankmomentaufnahme (DACPAC-Datei) nicht vorhanden sind, bei der Veröffentlichung in einer Datenbank aus der Zieldatenbank gelöscht werden.|  
|**DropExtendedPropertiesNotInSource= {True &#124; False}**|**Wahr**|Gibt an, ob durch die Veröffentlichungsaktion erweiterte Eigenschaften, die in der Datenbankmomentaufnahme (DACPAC-Datei) nicht vorhanden sind, bei der Veröffentlichung in einer Datenbank aus der Zieldatenbank gelöscht werden.|  
|**DropIndexesNotInSource= {True &#124; False}**|**Wahr**|Gibt an, ob durch die Veröffentlichungsaktion Indizes, die in der Datenbankmomentaufnahme (DACPAC-Datei) nicht vorhanden sind, bei der Veröffentlichung in einer Datenbank aus der Zieldatenbank gelöscht werden.|  
|**DropObjectsNotInSource= {True &#124; False}**|**False**|Gibt an, ob Objekte, die in der Datenbankmomentaufnahme (DACPAC-Datei) nicht vorhanden sind, bei der Veröffentlichung in einer Datenbank aus der Zieldatenbank gelöscht werden.|  
|**DropPermissionsNotInSource= {True &#124; False}**|**False**|Gibt an, ob durch die Veröffentlichungsaktion Berechtigungen, die in der Datenbankmomentaufnahme (DACPAC-Datei) nicht vorhanden sind, bei der Veröffentlichung in einer Datenbank aus der Zieldatenbank gelöscht werden.|  
|**DropRoleMembersNotInSource= {True &#124; False}**|**False**|Gibt an, ob durch die Veröffentlichungsaktion Rollenmitglieder, die in der Datenbankmomentaufnahme (DACPAC-Datei) nicht vorhanden sind, bei der Veröffentlichung in einer Datenbank aus der Zieldatenbank gelöscht werden.|  
|**GenerateSmartDefaults={True &#124; False}**|**False**|Gibt an, ob **SqlPackage.exe** automatisch einen Standardwert bereitstellt, wenn eine Tabelle mit Daten anhand einer Spalte aktualisiert wird, die keine NULL-Werte zulässt.|  
|**IgnoreAnsiNulls= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in der **ANSI NULLS**-Einstellung beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreAuthorizer= {True &#124; False}**|**False**|Gibt an, ob Authorizer-Unterschiede beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreColumnCollation= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in der Spaltensortierung beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreComments= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in der Kommentarreihenfolge beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreCryptographicProviderFile= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede im Dateipfad für einen kryptografischen Anbieter beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreDdlTriggerOrder= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in der Reihenfolge der DDL-Trigger (Data Definition Language) beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreDdlTriggerState={True &#124; False}**|**False**|Gibt an, ob Unterschiede im aktivierten oder deaktivierten Status von DDL-Triggern beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreDefaultSchema={True &#124; False}**|**False**|Gibt an, ob Unterschiede im Standardschema beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreDmlTriggerOrder= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in der Reihenfolge von DML-Triggern beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreDmlTriggerState= {True &#124; False}**|**False**|Gibt an, ob Unterschiede im aktivierten oder deaktivierten Status von DML-Triggern beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreExtendedProperties= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in den erweiterten Eigenschaften beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreFileAndLogFilePath={True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede im Datei- und Protokolldateipfad beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreFilegroupPlacement= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede in der **FILEGROUP**-Platzierung beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreFileSize= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede in der Dateigröße beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreFillFactor= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede in den Füllfaktoren beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
  
|Eigenschaft|Default|und Beschreibung|  
|------------|-----------|---------------|  
|**IgnoreFullTextCatalogFilePath= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede im Pfad zu Volltext-Indexdateien beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreIdentitySeed= {True &#124; False}**|**False**|Gibt an, ob Unterschiede im Ausgangswert für eine Identitätsspalte beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreIncrement= {True &#124; False}**|**False**|Gibt an, ob Unterschiede im Inkrement für eine Identitätsspalte beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreIndexOptions ={True &#124; False}**|**False**|Gibt an, ob Unterschiede in den Indexoptionen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreIndexPadding= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede im Auffüllen von Indizes beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreKeywordCasing= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede in der Groß-/Kleinschreibung für Schlüsselwörter beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreLockHintsOnIndexes= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in den Sperrhinweisen für Indizes beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreLoginSids= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede in der Sicherheits-ID (SID) beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreNotForReplication= {True &#124; False}**|**False**|Gibt an, ob die "not-for-replication"-Einstellung beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert wird.|  
|**IgnoreObjectPlacementOnPartitionScheme= {True &#124; False}**|**Wahr**|Gibt an, ob die Platzierung eines Objekts in einem Partitionsschema beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert wird.|  
|**IgnorePartitionSchemes= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in Partitionsschemas und Funktionen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnorePermissions= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in Berechtigungen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreQuotedIdentifiers= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in den Einstellungen für Bezeichner in Anführungszeichen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreRoleMembership={True &#124; False}**|**False**|Gibt an, ob Unterschiede in den Rollenmitgliedschaften von Anmeldenamen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden sollen.|  
|**IgnoreRouteLifetime= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede in den Rollenmitgliedschaften von Anmeldenamen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreSemicolonBetweenState= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede hinsichtlich Semikolons zwischen Transact-SQL-Anweisungen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreTableOptions= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in den Tabellenoptionen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreUserSettingsObjects= {True &#124; False}**|**False**|Gibt an, ob Unterschiede in den Benutzereinstellungsoptionen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreWhitespace= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede in Leerzeichen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreWithNocheckOnCheckConstraints={True &#124; False}**|**False**|Gibt an, ob Unterschiede im Wert der **WITH NOCHECK**-Klausel für CHECK-Einschränkungen beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IgnoreWithNocheckOnForeignKeys={True &#124; False}**|**False**|Gibt an, ob Unterschiede im Wert der **WITH NOCHECK**-Klausel für Fremdschlüssel beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**IncludeCompositeObjects= {True &#124; False}**|**False**|Gibt an, ob alle zusammengesetzten Elemente im Rahmen eines einzelnen Veröffentlichungsvorgangs eingeschlossen werden.|  
|**IncludeTransactionalScripts={True &#124; False}**|**False**|Gibt an, ob beim Veröffentlichen in einer Datenbank nach Möglichkeit Transaktionsanweisungen verwendet werden sollen.|  
|**NoAlterStatementsToChangeClrTypes={True &#124; False}**|**False**|Gibt an, dass eine Assembly bei einer Abweichung von der Veröffentlichungsaktion immer gelöscht und neu erstellt werden soll, anstatt eine ALTER ASSEMBLY-Anweisung auszugeben.|  
|**PopulateFilesOnFilegroups= {True &#124; False}**|**Wahr**|Gibt an, ob beim Erstellen einer neuen **FileGroup** in der Zieldatenbank ebenfalls eine neue Datei erstellt werden soll.|  
|**RegisterDataTierApplication={True &#124; False}**|**False**|Gibt an, ob das Schema beim Datenbankserver registriert wird.|  
|**ScriptDatabaseCollation {True &#124; False}**|**False**|Gibt an, ob Unterschiede in der Datenbanksortierung beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**ScriptDatabaseCompatibility= {True &#124; False}**|**Wahr**|Gibt an, ob Unterschiede in der Datenbankkompatibilität beim Veröffentlichen in einer Datenbank ignoriert oder aktualisiert werden.|  
|**ScriptDatabaseOptions= {True &#124; False}**|**Wahr**|Gibt an, ob die Eigenschaften der Zieldatenbank beim Veröffentlichen in einer Datenbank festgelegt oder aktualisiert werden.|  
|**ScriptFileSize={True &#124; False}**|**False**|Steuert, ob beim Hinzufügen einer Datei zu einer Dateigruppe die Größe angegeben wird.|  
|**ScriptNewConstraintValidation= {True &#124; False}**|**Wahr**|Gibt an, ob alle Einschränkungen am Ende der Veröffentlichung als ein Satz überprüft werden sollen, wodurch Datenfehler vermieden werden, die durch eine CHECK- oder FOREIGN KEY-Einschränkung mitten in der Veröffentlichungsaktion verursacht werden. Wenn diese Option **False** lautet, werden Einschränkungen ohne Überprüfung der entsprechenden Daten veröffentlicht.|  
|**ScriptDeployStateChecks={True &#124; False}**|**False**|Gibt an, ob Anweisungen im Veröffentlichungsskript generiert werden, um zu überprüfen, ob Datenbank- und Servername den im Datenbankprojekt angegebenen Namen entsprechen.|  
|**ScriptRefreshModule= {True &#124; False}**|**Wahr**|Gibt an, ob am Ende des Veröffentlichungsskripts Aktualisierungsanweisungen eingeschlossen werden.|  
|**Storage={File&#124;Memory}**|**Speicher**|Gibt an, wie Elemente gespeichert werden, wenn das Datenbankmodell erstellt wird. Die Standardeinstellung lautet aus Leistungsgründen **Memory**. Für sehr umfangreiche Datenbanken ist die Speicherung auf der Grundlage von Dateien erforderlich.|  
|**TreatVerificationErrorsAsWarnings= {True &#124; False}**|**False**|Gibt an, ob Fehler, die während der Veröffentlichungsüberprüfung auftreten, als Warnungen behandelt werden. Die Überprüfung wird für den generierten Bereitstellungsplan ausgeführt, bevor der Plan für die Zieldatenbank ausgeführt wird. Bei der Planüberprüfung werden Probleme erkannt, z. B. der Verlust von reinen Zielobjekten (z. B. Indizes), die gelöscht werden müssen, um eine Änderung vorzunehmen. Bei der Überprüfung werden auch Situationen erkannt, in denen Abhängigkeiten (z. B. Tabellen oder Sichten) aufgrund eines Verweises auf ein zusammengesetztes Projekt vorhanden sind, jedoch nicht in der Zieldatenbank vorkommen. Es empfiehlt sich beispielsweise, Überprüfungsfehler als Warnungen zu behandeln, um eine vollständige Problemliste zu erhalten, anstatt zuzulassen, dass die Veröffentlichungsaktion beim ersten Fehler beendet wird.|  
|**UnmodifiableObjectWarnings= {True &#124; False}**|**Wahr**|Gibt an, ob Warnungen generiert werden, wenn Unterschiede in Objekten gefunden werden, die nicht änderbar sind (z. B. wenn die Dateigröße oder Dateipfade für eine Datei unterschiedlich sind).|  
|**VerifyCollationCompatibility={True &#124; False}**|**Wahr**|Gibt an, ob die Kompatibilität von Sortierungen überprüft wird.|  
|**VerifyDeployment={True &#124; False}**|**Wahr**|Gibt an, ob vor der Veröffentlichung Überprüfungen ausgeführt werden sollen, durch die die Veröffentlichungsaktion beendet wird, wenn Probleme vorliegen, die eine erfolgreiche Veröffentlichung blockieren könnten. Die Veröffentlichungsaktion könnte beispielsweise beendet werden, wenn während der Veröffentlichung Fehler auftreten, weil Fremdschlüssel aus der Zieldatenbank nicht im Datenprojekt vorhanden sind.|  
  
> [!NOTE]  
> Alle angegebenen Zielparameter überschreiben die im Veröffentlichungsprofil der Quelle angegebenen Parameter.  
  
> [!NOTE]  
> **SQLCMD**-Variablen und -Werte müssen im Quellparameter des Veröffentlichungsprofils angegeben werden, weil sie nicht als Zielparameter festgelegt werden können.  
  
Die folgenden **Destination**-Parameter sind nur für die Vorgänge **DeployReport** und **Script** verfügbar:  
  
|Parameter|Default|und Beschreibung|  
|-------------|-----------|---------------|  
|**OutputPath**={ *string* }|–|Ein optionaler Parameter, der **dbSqlPackage** anweist, die XML-Ausgabedatei von DeployReport oder die SQL-Ausgabedatei von Script an einem Ort auf dem Datenträger zu erstellen, der durch *string* vorgegeben wird. Durch diese Aktion werden Skripts überschrieben, die sich derzeit an einem von string angegebenen Ort befinden.|  
  
> [!NOTE]  
> Wenn der **OutputPath**-Parameter für eine **DeployReport**- oder eine **Script**-Aktion nicht angegeben ist, wird die Ausgabe als Meldung zurückgegeben.  
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel wird die Syntax für einen **Extract**-Vorgang veranschaulicht, bei dem **dbSqlPackage** verwendet wird:  
  
```  
MSDeploy.exe -verb:sync -source:dbSqlPackage="<source connection string>",<source parameter> -dest:dbSqlPackage="<target dacpac file path>"  
```  
  
Im folgenden Beispiel wird die Syntax für einen **Publish**-Vorgang veranschaulicht, bei dem **dbSqlPackage** verwendet wird:  
  
```  
MSDeploy.exe -verb:sync -source:dbSqlPackage="<source dacpac file path>" -dest:dbSqlPackage="<target SQL Server/SQL Azure connection string>",Action=Publish,<destination parameters>  
```  
  
Im folgenden Beispiel wird die Syntax für einen **DeployReport**-Vorgang veranschaulicht, bei dem **dbSqlPackage** verwendet wird:  
  
```  
MSDeploy.exe -verb:sync -source:dbSqlPackage="<source dacpac file path>" -dest:dbSqlPackage="<target SQL Server/SQL Azure connection string>",Action=DeployReport,OutputPath="<path to output XML file>",<destination parameters>  
```  
  
Im folgenden Beispiel wird die Syntax für einen **Script**-Vorgang veranschaulicht, bei dem **dbSqlPackage** verwendet wird:  
  
```  
MSDeploy.exe -verb:sync -source:dbSqlPackage="<source dacpac file path>" -dest:dbSqlPackage="<target SQL Server/SQL Azure connection string>",Action=Script,OutputPath="<path to output sql script>",<destination parameters>  
```  
  
