---
title: Übersicht über DevOps für SQL Server Integration Services | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe von SSIS DevOps-Tools CI/CD in SQL Server Integration Services erstellen.
ms.date: 12/06/2019
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a1f903d0be82d6f5057af68dce80bda1e48238a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "78225919"
---
# <a name="sql-server-integration-services-ssis-devops-tools-preview"></a>DevOps-Tools für SQL Server Integration Services (Vorschau)

Die Erweiterung [SSIS DevOps-Tools](https://marketplace.visualstudio.com/items?itemName=SSIS.ssis-devops-tools) steht im **Azure DevOps-Marketplace** zur Verfügung.

Wenn Sie noch nicht über eine **Azure DevOps-Organisation** verfügen, registrieren Sie sich zunächst bei [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-sign-up?view=azure-devops). Fügen Sie anschließend gemäß [dieser Anleitung](https://docs.microsoft.com/azure/devops/marketplace/overview?view=azure-devops&tabs=browser#add-an-extension) die Erweiterung **SSIS DevOps-Tools** hinzu.

**SSIS DevOps-Tools** umfasst den **SSIS-Buildtask** sowie den **SSIS-Bereitstellungstask**.

- Der **SSIS-Buildtask** unterstützt das Erstellen von DTPROJ-Dateien in einem Projekt- oder Paketbereitstellungsmodell.

- Der **SSIS-Bereitstellungstask** unterstützt die Bereitstellung einzelner oder mehrerer ISPAC-Dateien für lokale SSIS-Kataloge und Azure-SSIS Integration Runtime sowie von SSISDeploymentManifest-Dateien und der zugehörigen Dateien für eine lokale oder Azure-Dateifreigabe.

## <a name="ssis-build-task"></a>SSIS-Buildtask

![Buildtask](media/ssis-build-task.png)

### <a name="properties"></a>Eigenschaften

#### <a name="project-path"></a>Projektpfad

Pfad des Projektordners oder der Projektdatei, die erstellt werden sollen. Wird ein Ordnerpfad angegeben, durchsucht der SSIS-Buildtask alle DTPROJ-Dateien in diesem Ordner rekursiv und erstellt alle.

Der Projektpfad darf nicht *leer* sein. Legen Sie ihn als **.** fest, um den Build im Stammordner des Repositorys zu erstellen.

#### <a name="project-configuration"></a>Projektkonfiguration

Name der Projektkonfiguration, die für den Build verwendet werden soll. Wird keine Projektkonfiguration angegeben, wird als Standardeinstellung die erste definierte Projektkonfiguration in jeder DTPROJ-Datei verwendet.

#### <a name="output-path"></a>Ausgabepfad

Pfad eines separaten Ordners zum Speichern von Buildergebnissen, die über den Task [Veröffentlichen von Buildartefakten](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/publish-build-artifacts?view=azure-devops) als Buildartefakt veröffentlicht werden können.

### <a name="limitations-and-known-issues"></a>Einschränkungen und bekannte Probleme

- Der SSIS-Buildtask verwendet den Visual Studio- und SSIS-Designer, der für Build-Agents obligatorisch ist. Wenn Sie den SSIS-Buildtask also in der Pipeline ausführen möchten, wählen Sie für von Microsoft gehostete Agents **vs2017-win2016** aus. Oder installieren Sie für selbstgehostete Agents den Visual Studio- und SSIS-Designer (entweder VS2017 und SSDT2017 oder VS2019 und SSIS-Projekterweiterungen).

- Wenn Sie SSIS-Projekte mit beliebigen Standardkomponenten (wie etwa SSIS Azure Feature Pack oder andere Drittanbieterkomponenten) erstellen möchten, müssen Sie diese auf dem Computer installieren, auf dem der Pipeline-Agent ausgeführt wird.  Bei von Microsoft gehosteten Agents können Benutzer einen [PowerShell-Skripttask](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/powershell?view=azure-devops) oder [Befehlszeilen-Skripttask](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/command-line?view=azure-devops) hinzufügen, um die Komponenten vor Ausführung des SSIS-Buildtasks herunterzuladen und zu installieren. Hier finden Sie das PowerShell-Beispielskript zum Installieren von Azure Feature Pack: 

```powershell
wget -Uri https://download.microsoft.com/download/E/E/0/EE0CB6A0-4105-466D-A7CA-5E39FA9AB128/SsisAzureFeaturePack_2017_x86.msi -OutFile AFP.msi

start -Wait -FilePath msiexec -Args "/i AFP.msi /quiet /l* log.txt"

cat log.txt
```

- Die Schutzebenen **EncryptSensitiveWithPassword** und **EncryptAllWithPassword** werden vom SSIS-Buildtask nicht unterstützt. Stellen Sie sicher, dass diese beiden Schutzebenen von keinem SSIS-Projekt in der Codebasis verwendet werden, da der SSIS-Buildtask ansonsten während der Ausführung nicht mehr reagiert und zu einem Timeout führt.

- **ConnectByProxy** ist eine neue Eigenschaft, die kürzlich zu SSDT hinzugefügt wurde. Auf von Microsoft gehosteten Agents installierte SSDT-Instanzen werden nicht aktualisiert. Verwenden Sie daher zur Problemumgehung einen selbstgehosteten Agent.

## <a name="ssis-deploy-task"></a>SSIS-Bereitstellungstask

![Bereitstellungstask](media/ssis-deploy-task.png)

### <a name="properties"></a>Eigenschaften

#### <a name="source-path"></a>Quellpfad

Pfad der ISPAC- oder SSISDeploymentManifest-Quelldateien, die Sie bereitstellen möchten. Bei diesem Pfad kann es sich um einen Ordner- oder Dateipfad handeln.

#### <a name="destination-type"></a>Zieltyp

Typ des Ziels. Zurzeit unterstützt der SSIS-Bereitstellungstask die folgenden beiden Zieltypen:

- *Dateisystem*: Stellen Sie SSISDeploymentManifest-Dateien und die zugehörigen Dateien für ein angegebenes Dateisystem bereit. Es werden sowohl lokale als auch Azure-Dateifreigaben unterstützt.
- *SSISDB*: Stellen Sie ISPAC-Dateien für einen angegebenen SSIS-Katalog bereit, der lokal auf SQL Server oder Azure-SSIS Integration Runtime gehostet werden kann.

#### <a name="destination-server"></a>Zielserver

Name des SQL Server-Zielservers. Dabei kann es sich um den Namen einer lokalen SQL Server-Instanz, Azure SQL-Datenbank oder verwalteten Azure SQL-Datenbank-Instanz handeln. Diese Eigenschaft ist nur sichtbar, wenn der Zieltyp „SSISDB“ lautet.

#### <a name="destination-path"></a>Zielpfad

Pfad des Zielordners, in dem die Quelldatei bereitgestellt wird. Beispiel:

- /SSISDB/\<folderName\>
- \\\\\<machineName\>\\\<shareFolderName\>\\\<optionalSubfolderName\>

Der SSIS-Bereitstellungstask erstellt den Ordner und Unterordner, sofern diese noch nicht vorhanden sind.

#### <a name="authentication-type"></a>Authentifizierungsart

Authentifizierungstyp für den Zugriff auf den angegebenen Zielserver. Diese Eigenschaft ist nur sichtbar, wenn der Zieltyp „SSISDB“ lautet. Im Allgemeinen unterstützt der SSIS-Bereitstellungstask vier Authentifizierungstypen:

- Windows-Authentifizierung
- SQL Server-Authentifizierung
- Active Directory-Kennwortauthentifizierung
- Integrierte Active Directory-Authentifizierung

Ob der jeweilige Authentifizierungstyp unterstützt wird, hängt jedoch vom Typ des Zielservers und des Agents ab. Die folgende Tabelle enthält eine detaillierte Unterstützungsmatrix:

| |Von Microsoft gehosteter Agent|Selbstgehosteter Agent|
|---------|---------|---------|
|Lokale SQL Server-Instanz oder virtueller Computer |–|Windows-Authentifizierung|
|Azure SQL|SQL Server-Authentifizierung <br> Active Directory-Kennwortauthentifizierung|SQL Server-Authentifizierung <br> Active Directory-Kennwortauthentifizierung <br> Integrierte Active Directory-Authentifizierung|

#### <a name="domain-name"></a>Domänenname

Domänenname für den Zugriff auf das angegebene Dateisystem. Diese Eigenschaft ist nur sichtbar, wenn der Zieltyp „Dateisystem“ lautet.
Verfügt das Benutzerkonto zur Ausführung des selbstgehosteten Agents über Lese-/Schreibzugriff auf den angegebenen Zielpfad, können Sie das Feld leer lassen.

#### <a name="username"></a>Username

Benutzername für den Zugriff auf das angegebene Dateisystem oder SSISDB. Diese Eigenschaft ist sichtbar, wenn der Zieltyp „Dateisystem“ oder der Authentifizierungstyp „SQL Server-Authentifizierung“ oder „Active Directory-Kennwort“ lautet.
Lautet der Zieltyp „Dateisystem“ und verfügt das Benutzerkonto zur Ausführung des selbstgehosteten Agents über Lese-/Schreibzugriff auf den angegebenen Zielpfad, können Sie das Feld leer lassen.

#### <a name="password"></a>Kennwort

Kennwort für den Zugriff auf das angegebene Dateisystem oder SSISDB. Diese Eigenschaft ist sichtbar, wenn der Zieltyp „Dateisystem“ oder der Authentifizierungstyp „SQL Server-Authentifizierung“ oder „Active Directory-Kennwort“ lautet.
Lautet der Zieltyp „Dateisystem“ und verfügt das Benutzerkonto zur Ausführung des selbstgehosteten Agents über Lese-/Schreibzugriff auf den angegebenen Zielpfad, können Sie das Feld leer lassen.

#### <a name="overwrite-existing-projects-or-ssisdeploymentmanifest-files-of-the-same-names"></a>Vorhandene Projekte oder SSISDeploymentManifest-Dateien mit demselben Namen überschreiben

Geben Sie an, ob vorhandene Projekte oder SSISDeploymentManifest-Dateien mit demselben Namen überschrieben werden sollen. Bei „Nein“ überspringt der SSIS-Bereitstellungstask die Bereitstellung dieser Projekte oder Dateien.

#### <a name="continue-deployment-when-error-occurs"></a>Bereitstellung bei Auftreten eines Fehlers fortsetzen

Geben Sie an, ob die Bereitstellung der verbleibenden Projekte oder Dateien fortgesetzt werden soll, wenn ein Fehler auftritt. Bei „Nein“ wird der SSIS-Bereitstellungstask bei einem Fehler sofort beendet.

### <a name="limitations-and-known-issues"></a>Einschränkungen und bekannte Probleme

Folgende Szenarios werden vom SSIS-Bereitstellungstask zurzeit nicht unterstützt:

- Konfigurieren der Umgebung im SSIS-Katalog
- Bereitstellen von ISPAC-Dateien in Azure SQL Server oder einer verwalteten Azure SQL-Instanz – hierbei ist nur eine mehrstufige Authentifizierung (Multi-Factor Authentication, MFA) zulässig
- Bereitstellen von Paketen für MSDB oder SSIS-Paketspeicher

## <a name="release-notes"></a>Versionshinweise

### <a name="version-013-preview"></a>Version 0.1.3 (Vorschau)

Veröffentlichungsdatum: 19. Januar 2020

- Ein Problem wurde behoben, durch das die Bereitstellung von „ispac“ verhindert wurde, wenn der ursprüngliche Dateiname geändert wurde.

### <a name="version-012-preview"></a>Version 0.1.2 (Vorschauversion)

Veröffentlichungsdatum: 13. Januar 2020

- Im Protokoll für den SSIS-Bereitstellungstask werden nun detailliertere Informationen zu Ausnahmen angezeigt, wenn das Ziel eine SSIS-Datenbank ist.
- Der fehlerhafte Beispielzielpfad im Hilfetext für die Eigenschaft „Zielpfad“ des SSIS-Bereitstellungstask wurde korrigiert.

### <a name="version-011-preview"></a>Version 0.1.1 (Vorschau)

Veröffentlichungsdatum: 6. Januar 2020

- Es wurde eine Einschränkung der Mindestanforderung für die Agent-Version hinzugefügt. Die minimale Agent-Version für dieses Produkt ist derzeit 2.144.0.
- Ein falscher Anzeigetext für den SSIS-Bereitstellungstask wurde korrigiert.
- Einige Fehlermeldungen wurden präzisiert.

### <a name="version-010-preview"></a>Version 0.1.0 (Vorschau)

Veröffentlichungsdatum: 5. Dezember 2019

Erstrelease von SSIS DevOps-Tools. Dies ist ein Vorschaurelease.

## <a name="next-steps"></a>Nächste Schritte

- Laden Sie die [SSIS DevOps-Erweiterung](https://marketplace.visualstudio.com/items?itemName=SSIS.ssis-devops-tools) herunter.
