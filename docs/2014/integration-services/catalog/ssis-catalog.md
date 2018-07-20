---
title: SSIS-Katalog | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 24bd987e-164a-48fd-b4f2-cbe16a3cd95e
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2cd6a36267065aff8995df20c79a94c0f56f1417
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084082"
---
# <a name="ssis-catalog"></a>SSIS-Katalog
  Die `SSISDB` Katalog ist der zentrale Punkt zum Arbeiten mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Projekte (SSIS), die zum Bereitstellen der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Server. Sie legen beispielsweise Projekt- und Paketparameter fest, konfigurieren Umgebungen, um Laufzeitwerte für Pakete anzugeben, führen Pakete aus, behandeln Paketprobleme und verwalten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Servervorgänge.  
  
 Die Objekte, die im rowsetcache der `SSISDB` Katalog enthalten Projekte, Pakete, Parameter, Umgebungen und verwendungsverläufe.  
  
 Sie untersuchen, Objekte, Einstellungen und operative Daten, die in gespeichert werden die `SSISDB` -Katalog durch Abfragen der Sichten in der `SSISDB` Datenbank. Sie verwalten die Objekte durch Aufrufen von gespeicherten Prozeduren in der `SSISDB` -Datenbank oder über die Benutzeroberfläche des der `SSISDB` Katalog. In vielen Fällen kann der gleiche Task in der Benutzeroberfläche oder durch das Aufrufen einer gespeicherten Prozedur ausgeführt werden.  
  
 Zur Verwaltung der Datenbank `SSISDB` wird empfohlen, Standardunternehmensrichtlinien für die Verwaltung von Benutzerdatenbanken anzuwenden. Informationen zum Erstellen von Wartungsplänen finden Sie unter [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md).  
  
 Die `SSISDB` Katalog und die `SSISDB` -Datenbank unterstützen Windows PowerShell. Weitere Informationen zum Verwenden von SQL Server mit Windows PowerShell finden Sie unter [SQL Server PowerShell](../../powershell/sql-server-powershell.md). Beispiele zur Verwendung von Windows PowerShell zum Abschließen von Tasks, z. B. zum Bereitstellen eines Projekts, finden Sie im Blogeintrag zu [SSIS und PowerShell in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=242539)auf blogs.msdn.com.  
  
 Weitere Informationen zum Anzeigen von Vorgangsdaten finden Sie unter [Überwachen von Paketausführungen und anderen Vorgängen](../performance/monitor-running-packages-and-other-operations.md).  
  
 Sie Zugriff auf die `SSISDB` im Katalog [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] durch Herstellen einer Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine und erweitert die **Integration Services-Kataloge** Knoten im Objekt-Explorer. Sie Zugriff auf die `SSISDB` Datenbank [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] durch den Datenbankknoten im Objekt-Explorer erweitern.  
  
> [!NOTE]  
>  Sie können nicht umbenannt werden die `SSISDB` Datenbank.  
  
> [!NOTE]  
>  Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz, die `SSISDB` Datenbank angefügt ist, beendet oder reagiert nicht, die ISServerExec.exe beendet. Eine Meldung wird in ein Windows-Ereignisprotokoll geschrieben.  
>   
>  Wenn für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressourcen ein Failover als Teil eines Clusterfailovers durchgeführt wird, werden die ausgeführten Pakete nicht neu gestartet. Sie können Prüfpunkte verwenden, um Pakete neu zu starten. Weitere Informationen finden Sie unter [Neustarten von Paketen mit Prüfpunkten](../packages/restart-packages-by-using-checkpoints.md).  
  
## <a name="catalog-object-identifiers"></a>Katalogobjektbezeichner  
 Wenn Sie im Katalog ein neues Objekt erstellen, weisen Sie dem Objekt einen Namen zu. Der Objektname ist der Bezeichner. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bestimmt Regeln, welche Zeichen in einem Bezeichner verwendet werden können. Namen für die folgenden Objekte müssen den Regeln für Bezeichner entsprechen.  
  
-   Ordner  
  
-   Projekt  
  
-   Umgebung  
  
-   Parameter  
  
-   Umgebungsvariable  
  
### <a name="folder-project-environment"></a>Ordner, Projekt, Umgebung  
 Beachten Sie die folgenden Regeln, wenn Sie einen Ordner, ein Projekt oder eine Umgebung umbenennen.  
  
-   Zu ungültige Zeichen zählen die ASCII/Unicode-Zeichen 1 bis 31, Anführungszeichen ("), kleiner als (\<), größer als (>), senkrechter Strich (|), Rücktaste (\b), NULL (\0) und Tab (\t).  
  
-   Der Name darf keine führenden oder nachgestellten Leerzeichen enthalten.  
  
-   \@ kann nicht als erstes Zeichen, aber nachfolgende Zeichen können \@.  
  
-   Die Länge des Namens muss größer als oder gleich 0 und kleiner als oder gleich 128 sein.  
  
### <a name="parameter"></a>Parameter  
 Beachten Sie die folgenden Regeln, wenn Sie einen Parameter benennen.  
  
-   Das erste Zeichen des Namens muss ein Buchstabe gemäß Unicode-Standard 2.0 oder ein Unterstrich (_) sein.  
  
-   Bei nachfolgenden Zeichen kann es sich um Buchstaben oder Zahlen gemäß Unicode-Standard 2.0 oder um einen Unterstrich (_) handeln.  
  
### <a name="environment-variable"></a>Umgebungsvariable  
 Beachten Sie die folgenden Regeln, wenn Sie eine Umgebungsvariable benennen.  
  
-   Zu ungültige Zeichen zählen die ASCII/Unicode-Zeichen 1 bis 31, Anführungszeichen ("), kleiner als (\<), größer als (>), senkrechter Strich (|), Rücktaste (\b), NULL (\0) und Tab (\t).  
  
-   Der Name darf keine führenden oder nachgestellten Leerzeichen enthalten.  
  
-   \@ kann nicht als erstes Zeichen, aber nachfolgende Zeichen können \@.  
  
-   Die Länge des Namens muss größer als oder gleich 0 und kleiner als oder gleich 128 sein.  
  
-   Das erste Zeichen des Namens muss ein Buchstabe gemäß Unicode-Standard 2.0 oder ein Unterstrich (_) sein.  
  
-   Bei nachfolgenden Zeichen kann es sich um Buchstaben oder Zahlen gemäß Unicode-Standard 2.0 oder um einen Unterstrich (_) handeln.  
  
## <a name="catalog-configuration"></a>Katalogkonfiguration  
 Sie können anpassen, wie sich der Katalog verhält, indem Sie die Katalogeigenschaften einstellen. Die Katalogeigenschaften definieren, wie sensible Daten verschlüsselt werden und wie Vorgänge und Versionsdaten für Projekte beibehalten werden. Verwenden Sie das Dialogfeld **Katalogeigenschaften**, oder rufen Sie die gespeicherte [catalog.configure_catalog &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database)-Prozedur auf, um Katalogeigenschaften festzulegen. Verwenden Sie zum Anzeigen der Eigenschaft das Dialogfeld, oder fragen Sie [catalog.catalog_properties &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database) ab. Sie greifen auf das Dialogfeld zu, indem Sie im Objekt-Explorer mit der rechten Maustaste auf `SSISDB` klicken.  
  
### <a name="operations-and-project-version-cleanup"></a>Bereinigung von Projektversionen und Vorgängen  
 Statusdaten für viele der Vorgänge im Katalog werden in internen Datenbanktabellen gespeichert. Beispielsweise wird im Katalog der Status von Paketausführungen und Projektbereitstellungen nachverfolgt. Um die Größe der Vorgangsdaten zu verwalten, wird der **SSIS-Server-Wartungsauftrag** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwendet, um alte Daten zu entfernen. Dieser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentauftrag wird bei der Installation von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] erstellt.  
  
 Sie können ein [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt durch das Bereitstellen unter dem gleichen Namen im gleichen Ordner im Katalog aktualisieren oder erneut bereitstellen. Standardmäßig immer Sie ein Projekt erneut bereitstellen, die `SSISDB` Katalog behält die vorherige Version des Projekts. Um die Größe der Vorgangsdaten zu verwalten, wird der **SSIS-Server-Wartungsauftrag** verwendet, um alte Versionen von Projekten zu entfernen.  
  
 Die folgenden `SSISDB` Katalogeigenschaften definieren, wie sich dieser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentauftrag verhält. Sie können die Eigenschaften anzeigen oder ändern, indem Sie das Dialogfeld **Katalogeigenschaften** verwenden, oder [catalog.catalog_properties &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database) und [catalog.configure_catalog &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).  
  
 **Protokolle regelmäßig bereinigen**  
 Der Auftragsschritt für die vorgangsbereinigung wird ausgeführt, wenn diese Eigenschaft, um festgelegt wird `True`.  
  
 **Beibehaltungsdauer (Tage)**  
 Definiert das maximale Alter von zulässigen Vorgangsdaten (in Tagen). Ältere Daten werden entfernt.  
  
 Der Mindestwert ist ein Tag. Der Höchstwert wird nur durch den maximalen Wert von beschränkt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `int` Daten. Informationen zu diesem Datentyp finden Sie unter [int, bigint, smallint und tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql).  
  
 **Alte Versionen regelmäßig entfernen**  
 Der Auftragsschritt für die Bereinigung von Projektversionen, das ausgeführt wird, wenn diese Eigenschaft, um festgelegt wird `True`.  
  
 **Maximale Anzahl der Versionen pro Projekt**  
 Definiert, wie viele Versionen eines Projekts im Katalog gespeichert sind. Frühere Versionen von Projekten werden entfernt.  
  
### <a name="encryption-algorithm"></a>Verschlüsselungsalgorithmus  
 Die Eigenschaft **Verschlüsselungsalgorithmus** gibt den Verschlüsselungstyp an, der zur Verschlüsselung der sensiblen Parameterwerte verwendet wird. Sie haben die Wahl zwischen den folgenden Verschlüsselungstypen:  
  
-   AES_256 (Standard)  
  
-   AES_192  
  
-   AES_128  
  
-   DESX  
  
-   TRIPLE_DES_3KEY  
  
-   TRIPLE_DES  
  
-   DES  
  
 Wenn Sie ein [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server bereitstellen, werden die Paketdaten und sensible Werte automatisch vom Katalog verschlüsselt. Die Daten werden vom Katalog auch automatisch entschlüsselt, wenn Sie sie abrufen. Der SSISDB-Katalog verwendet die `ServerStorage` Schutzebene. Weitere Informationen finden Sie unter [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md).  
  
 Eine Änderung des Verschlüsselungsalgorithmus ist sehr aufwändig. Der Server muss zuerst alle Konfigurationswerte mithilfe des zuvor angegebenen Algorithmus entschlüsseln. Anschließend müssen die Werte vom Server mithilfe des neuen Algorithmus wieder verschlüsselt werden. In diesem Zeitraum können keine anderen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Vorgänge auf dem Server ausgeführt werden. Damit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Vorgänge weiterhin ohne Unterbrechung ausgeführt werden können, ist der Wert für den Verschlüsselungsalgorithmus im [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]-Dialogfeld schreibgeschützt.  
  
 So ändern Sie die **Verschlüsselungsalgorithmus** legen Sie die Einstellung der Eigenschaft, die `SSISDB` -Datenbank in den Einzelbenutzermodus, und klicken Sie dann rufen Sie die gespeicherten Catalog. configure_catalog-Prozedur. Verwenden Sie ENCRYPTION_ALGORITHM für das *property_name* -Argument. Die unterstützten Eigenschaftswerte finden Sie unter [catalog.catalog_properties &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database). Weitere Informationen zur gespeicherten Prozedur finden Sie unter [catalog.configure_catalog &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).  
  
 Weitere Informationen zum Einzelbenutzermodus finden Sie unter [Festlegen des Einzelbenutzermodus für eine Datenbank](../../relational-databases/databases/set-a-database-to-single-user-mode.md). Informationen zur Verschlüsselung sowie zu Algorithmen für die Verschlüsselung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]finden Sie in den Themen im Abschnitt [SQL Server-Verschlüsselung](../../relational-databases/security/encryption/sql-server-encryption.md).  
  
 Ein Datenbank-Hauptschlüssel wird für die Verschlüsselung verwendet. Der Schlüssel wird erstellt, wenn Sie den Katalog erstellen. Weitere Informationen finden Sie unter [Erstellen des SSIS-Katalogs](ssis-catalog.md).  
  
 In der folgenden Tabelle sind die im Dialogfeld **Katalogeigenschaften** aufgeführten Eigenschaftsnamen und die zugehörigen Eigenschaften in der Datenbanksicht aufgelistet.  
  
|Eigenschaftsname (Dialogfeld**Katalogeigenschaften** )|Eigenschaftsname (Datenbanksicht)|  
|---------------------------------------------------------|-------------------------------------|  
|Name des Verschlüsselungsalgorithmus|ENCRYPTION_ALGORITHM|  
|Protokolle regelmäßig bereinigen|OPERATION_CLEANUP_ENABLED|  
|Beibehaltungsdauer (Tage)|RETENTION_WINDOW|  
|Alte Versionen regelmäßig entfernen|VERSION_CLEANUP_ENABLED|  
|Maximale Anzahl der Versionen pro Projekt|MAX_PROJECT_VERSIONS|  
|Serverweiter Standardprotokolliergrad|SERVER_LOGGING_LEVEL|  
  
## <a name="permissions"></a>Berechtigungen  
 Projekte, Umgebungen und Pakete sind in Ordnern enthalten, bei denen es sich um sicherungsfähige Objekte handelt. Sie können einem Ordner Berechtigungen gewähren, einschließlich der MANAGE_OBJECT_PERMISSIONS-Berechtigung. MANAGE_OBJECT_PERMISSIONS ermöglicht es Ihnen, die Verwaltung von Ordnerinhalten an einen Benutzer zu delegieren, ohne dass Sie dem Benutzer die Mitgliedschaft in der ssis_admin-Rolle erteilen müssen. Sie haben auch die Möglichkeit, Projekten, Umgebungen und Vorgängen Berechtigungen zu erteilen. Vorgänge schließen das Initialisieren [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]Bereitstellen von Projekten, erstellen und Starten von Ausführungen, Überprüfen von Projekten und Paketen, und Konfigurieren der `SSISDB` Katalog.  
  
 Weitere Informationen zu Datenbankrollen finden Sie unter [Rollen auf Datenbankebene](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
 Der SSISDB-Katalog erzwingt die Integrität der Berechtigungsinformationen für SSIS-sicherungsfähige Elemente mithilfe eines DDL-Triggers, ddl_cleanup_object_permissions. Der Trigger wird ausgelöst, wenn ein Datenbankprinzipal, z. B. ein Datenbankbenutzer, eine Datenbankrolle oder eine Datenbankanwendungsrolle, aus der SSISDB-Datenbank entfernt wird.  
  
 Wenn der Prinzipal anderen Prinzipalen Berechtigungen erteilt oder verweigert hat, widerrufen Sie die vom Berechtigenden erteilten Berechtigungen, bevor der Prinzipal entfernt werden kann. Andernfalls wird eine Fehlermeldung zurückgegeben, wenn das System versucht, den Prinzipal zu entfernen. Der Trigger entfernt alle Berechtigungsdatensätze, bei denen der Datenbankprinzipal ein Empfänger ist.  
  
 Es wird empfohlen, dass der Trigger nicht deaktiviert ist, da dadurch sichergestellt wird, die keine verwaisten Berechtigungsdatensätze vorhanden sind, nachdem ein Datenbankprinzipal aus gelöscht wurde die `SSISDB` Datenbank.  
  
### <a name="managing-permissions"></a>Verwalten von Berechtigungen  
 Sie können Berechtigungen mit der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] -Benutzeroberfläche, gespeicherten Prozeduren und dem <xref:Microsoft.SqlServer.Management.IntegrationServices> -Namespace verwalten.  
  
 Um Berechtigungen mithilfe der Benutzeroberfläche von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zu verwalten, verwenden Sie die folgenden Dialogfelder.  
  
-   Verwenden Sie für einen Ordner die Seite **Berechtigungen** im [Folder Properties Dialog Box](folder-properties-dialog-box.md).  
  
-   Verwenden Sie für ein Projekt die Seite **Berechtigungen** im [Project Properties Dialog Box](project-properties-dialog-box.md).  
  
 Rufen Sie zum Verwalten von Berechtigungen mithilfe von Transact-SQL [catalog.grant_permission &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database), [catalog.deny_permission &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-deny-permission-ssisdb-database) und [catalog.revoke_permission &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-revoke-permission-ssisdb-database) auf. Fragen Sie [catalog.effective_object_permissions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-effective-object-permissions-ssisdb-database) ab, um effektive Berechtigungen für das aktuelle Prinzipal für alle Objekte anzuzeigen. Dieses Thema enthält Beschreibungen der verschiedenen Berechtigungstypen. Fragen Sie [catalog.explicit_object_permissions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-explicit-object-permissions-ssisdb-database) ab, um Berechtigungen anzuzeigen, die explizit dem Benutzer zugewiesen wurden.  
  
## <a name="folders"></a>Ordner  
 Ein Ordner enthält eine oder mehrere Projekte und Umgebungen im der `SSISDB` Katalog. Sie können die Ansicht [catalog.folders &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-folders-ssisdb-database) verwenden, um auf Informationen über Ordner im Katalog zuzugreifen. Sie können folgende gespeicherte Prozeduren zum Verwalten von Ordnern verwenden.  
  
-   [catalog.create_folder &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-create-folder-ssisdb-database)  
  
-   [catalog.delete_folder &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-delete-folder-ssisdb-database)  
  
-   [catalog.rename_folder &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-rename-folder-ssisdb-database)  
  
-   [catalog.set_folder_description &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-folder-description-ssisdb-database)  
  
## <a name="projects-and-packages"></a>Projekte und Pakete  
 Jedes Projekt kann mehrere Pakete enthalten. Sowohl Projekte als auch Pakete können Parameter und Umgebungsverweise enthalten. Sie können über das [Configure Dialog Box](configure-dialog-box.md)auf die Parameter und die Umgebungsverweise zugreifen.  
  
 Sie können weitere Projekttasks ausführen, indem Sie die folgenden gespeicherten Prozeduren aufrufen.  
  
-   [catalog.delete_project &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-delete-project-ssisdb-database)  
  
-   [catalog.deploy_project &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database)  
  
-   [catalog.get_project &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database)  
  
-   [catalog.move_project &#40;&#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-move-project-ssisdb-database)  
  
-   [catalog.restore_project &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database)  
  
 Diese Sichten enthalten Details zu Paketen, Projekten und Projektversionen.  
  
-   [catalog.projects &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-projects-ssisdb-database)  
  
-   [catalog.packages &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-packages-ssisdb-database)  
  
-   [catalog.object_versions &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database)  
  
## <a name="parameters"></a>Parameter  
 Mit Parametern können Sie Paketeigenschaften zum Zeitpunkt der Paketausführung Werte zuweisen. Rufen Sie [catalog.set_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) und [catalog.clear_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database) auf, um den Wert des Paket- oder Projektparameters festzulegen und den Wert zu löschen. Rufen Sie zum Festlegen des Wert eines Parameters für eine Instanz der Ausführung [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) auf. Sie können Standardparameterwerte abrufen, indem Sie [catalog.get_parameter_values &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database) aufrufen.  
  
 Diese Sichten zeigen die Parameter für alle Pakete und Projekte sowie Parameterwerte, die für eine Instanz der Ausführung verwendet werden, an.  
  
-   [catalog.object_parameters &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database)  
  
-   [catalog.execution_parameter_values &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-execution-parameter-values-ssisdb-database)  
  
## <a name="server-environments-server-variables-and-server-environment-references"></a>Serverumgebungen, Servervariablen und Serverumgebungsverweise  
 Serverumgebungen enthalten Servervariablen. Die Variablenwerte können verwendet werden, wenn ein Paket ausgeführt wird oder auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server überprüft wird.  
  
 Die folgenden gespeicherten Prozeduren ermöglichen es Ihnen, zahlreiche weitere Verwaltungstasks für Umgebungen und Variablen auszuführen.  
  
-   [catalog.create_environment &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-create-environment-ssisdb-database)  
  
-   [catalog.delete_environment &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-delete-environment-ssisdb-database)  
  
-   [catalog.move_environment &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-move-environment-ssisdb-database)  
  
-   [catalog.rename_environment &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-rename-environment-ssisdb-database)  
  
-   [catalog.set_environment_property &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-environment-property-ssisdb-database)  
  
-   [catalog.create_environment_variable &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-create-environment-variable-ssisdb-database)  
  
-   [catalog.delete_environment_variable &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-delete-environment-variable-ssisdb-database)  
  
-   [catalog.set_environment_variable_property &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-environment-variable-property-ssisdb-database)  
  
-   [catalog.set_environment_variable_value &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-environment-variable-value-ssisdb-database)  
  
 Durch Aufrufen der gespeicherten Prozedur [catalog.set_environment_variable_protection &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-environment-variable-protection-ssisdb-database) können Sie das Vertraulichkeitsbit für eine Variable festlegen.  
  
 Um den Wert einer Servervariablen zu verwenden, geben Sie den Verweis zwischen dem Projekt und der Serverumgebung an. Sie können die folgenden gespeicherten Prozeduren verwenden, um Verweise zu erstellen und zu löschen. Sie können auch angeben, ob sich die Umgebung im selben Ordner wie das Projekt oder in einem anderen Ordner befinden kann.  
  
-   [catalog.create_environment_reference &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-create-environment-reference-ssisdb-database)  
  
-   [catalog.delete_environment_reference &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-delete-environment-reference-ssisdb-database)  
  
-   [catalog.set_environment_reference_type &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-environment-reference-type-ssisdb-database)  
  
 Weitere Details zu Umgebungen und Variablen können Sie aus diesen Sichten abfragen.  
  
-   [catalog.environments &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-environments-ssisdb-database)  
  
-   [catalog.environment_variables &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-environment-variables-ssisdb-database)  
  
-   [catalog.environment_references &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-environment-references-ssisdb-database)  
  
## <a name="executions-and-validations"></a>Ausführungen und Überprüfungen  
 Eine Ausführung ist eine Instanz einer Paketausführung. Rufen Sie [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) und [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) auf, um eine Ausführung zu erstellen und zu starten. Rufen Sie [catalog.stop_operation &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database) auf, um eine Ausführung oder eine Paket-/Projektüberprüfung zu beenden.  
  
 Rufen Sie die gespeicherte Prozedur catalog.create_execution_dump auf, um ein ausgeführtes Paket anzuhalten und eine Dumpdatei zu erstellen. Eine Dumpdatei enthält Informationen zur Ausführung eines Pakets, die Ihnen helfen können, Ausführungsprobleme zu beheben. Weitere Informationen zum Erstellen und Konfigurieren von Dumpdateien finden Sie unter [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md).  
  
 Details zu Ausführungen, Überprüfungen, Meldungen, die während der Vorgänge protokolliert werden, und Kontextinformationen zu Fehlern können Sie aus diesen Sichten abfragen.  
  
-   [catalog.executions &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)  
  
-   [catalog.operations &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database)  
  
-   [catalog.operation_messages &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database)  
  
-   [catalog.extended_operation_info &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-extended-operation-info-ssisdb-database)  
  
-   [catalog.event_messages](/sql/integration-services/system-views/catalog-event-messages)  
  
-   [catalog.event_message_context](/sql/integration-services/system-views/catalog-event-message-context)  
  
 Sie können Projekte und Pakete überprüfen, indem Sie die gespeicherten Prozeduren [catalog.validate_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-validate-project-ssisdb-database) und [catalog.validate_package &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-validate-package-ssisdb-database) aufrufen. Die [catalog.validations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database)-Sicht enthält Details zu Überprüfungen, z.B. die Serverumgebungsverweise, die in der Überprüfung berücksichtigt werden, ob es eine Abhängigkeitsüberprüfung oder eine vollständige Überprüfung ist, und ob die 32-Bit-Laufzeit oder die 64-Bit-Laufzeit verwendet wird, um das Paket auszuführen.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Erstellen des SSIS-Katalogs](ssis-catalog.md)  
  
-   [Sichern, Wiederherstellen und Verschieben des SSIS-Katalogs](../backup-restore-and-move-the-ssis-catalog.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Blogeintrag zu [SSIS und PowerShell in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=242539), auf blogs.msdn.com.  
  
-   Blogeintrag zu [SSIS Catalog Access Control Tips](http://go.microsoft.com/fwlink/?LinkId=246669)(Tipps zur SSIS-Katalogzugriffssteuerung) auf blogs.msdn.com.  
  
-   Blogeintrag zu [Überblick über das SSIS-Katalogmodell verwalteter Objekte](http://go.microsoft.com/fwlink/?LinkId=254267)auf blogs.msdn.com.  
  
  
