---
title: Installation von R-und python-Komponenten in der Befehlszeile
description: Führen Sie SQL Server Befehlszeilen Setup aus, um R-Sprache und python-Integration zu einer SQL Server Datenbank-Engine-Instanz hinzuzufügen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f60aa3684778a7347b1ffd613a924c3bf0b7b94a
ms.sourcegitcommit: 2f56848ec422845ee81fb84ed321a716c677aa0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71271939"
---
# <a name="install-sql-server-machine-learning-r-and-python-components-from-the-command-line"></a>Installieren von SQL Server Machine Learning-R-und python-Komponenten über die Befehlszeile
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel enthält Anweisungen zum Installieren von SQL Server Machine Learning-Komponenten über die Befehlszeile:

+ [Neue in-Database-Instanz](#indb)
+ [Zu einer vorhandenen Datenbank-Engine-Instanz hinzufügen](#add-existing)
+ [Unbeaufsichtigte Installation](#silent)
+ [Neuer eigenständiger Server](#shared-feature)

Sie können eine unbeaufsichtigte, grundlegende oder vollständige Interaktion mit der Setup Benutzeroberfläche angeben. Dieser Artikel ergänzt die [Installation von SQL Server an der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md), die die für R-und python Machine Learning-Komponenten eindeutigen Parameter abdeckt.

## <a name="pre-install-checklist"></a>Prüfliste vor der Installation

+ Führen Sie Befehle an einer Eingabeaufforderung mit erhöhten Rechten aus. 

+ Eine Datenbank-Engine-Instanz ist für in-Database-Installationen erforderlich. Sie können nicht nur R-oder python-Funktionen installieren, Sie können Sie jedoch [inkrementell zu einer vorhandenen-Instanz hinzufügen](#add-existing). Wenn Sie nur R und python ohne die Datenbank-Engine möchten, installieren Sie den [eigenständigen Server](#shared-feature).

+ Installieren Sie nicht auf einem Failovercluster. Der zum Isolieren von R-und python-Prozessen verwendete Sicherheitsmechanismus ist mit einer Windows Server-Failoverclusterumgebung nicht kompatibel.

+ Installieren Sie nicht auf einem Domänen Controller. Der Machine Learning Services Teil des-Setups schlägt fehl.

+ Vermeiden Sie die Installation eigenständiger und Daten Bank basierter Instanzen auf demselben Computer. Ein eigenständiger Server wird mit den gleichen Ressourcen konkurrieren und die Leistung beider Installationen untergraben.


## <a name="command-line-arguments"></a>Befehlszeilenargumente

Das Features-Argument ist erforderlich, ebenso wie Lizenzbedingungen. 

Wenn Sie über die Eingabeaufforderung installieren, unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des /Q-Parameters den vollständigen stillen Modus oder mithilfe des /QS-Parameters den einfachen stillen Modus. Mithilfe des /QS-Schalters wird nur der Fortschritt angezeigt, es sind jedoch keine Eingaben möglich. Außerdem werden beim Auftreten von Fehlern keine Fehlermeldungen angezeigt. Der /QS-Parameter wird nur unterstützt, wenn /Action=install angegeben wurde.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
| Argumente | Beschreibung |
|-----------|-------------|
| /Features = advancedanalytics | Installiert die in-Database-Version: SQL Server R Services (in-Database).  |
| /FEATURES = SQL_SHARED_MR | Installiert die R-Funktion für die eigenständige Version: SQL Server R Server (eigenständig). Ein eigenständiger Server ist eine "freigegebene Funktion", die nicht an eine Datenbank-Engine-Instanz gebunden ist.|
| /IACCEPTROPENLICENSETERMS  | Gibt an, dass Sie die Lizenzbedingungen für die Verwendung der Open Source-R-Komponenten akzeptiert haben. |
| /IACCEPTPYTHONLICENSETERMS | Gibt an, dass Sie die Lizenzbedingungen für die Verwendung der python-Komponenten akzeptiert haben. |
| /IACCEPTSQLSERVERLICENSETERMS | Gibt an, dass Sie die Lizenzbedingungen für die Verwendung von SQL Server akzeptiert haben.|
| MRCACHEDIRECTORY | Für das Offline-Setup wird der Ordner mit den CAB-Dateien der R-Komponente festgelegt. |
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
| Argumente | Beschreibung |
|-----------|-------------|
| /Features = advancedanalytics | Installiert die in-Database-Version: SQL Server Machine Learning Services (in-Database).  |
| /FEATURES = SQL_INST_MR | Koppeln Sie dies mit advancedanalytics. Installiert die r-Funktion (in-Database), einschließlich Microsoft r Open und der proprietären r-Pakete. |
| /FEATURES = SQL_INST_MPY | Koppeln Sie dies mit advancedanalytics. Installiert das python-Feature (in der Datenbank), einschließlich Anaconda und der proprietären Python-Pakete. |
| /FEATURES = SQL_SHARED_MR | Installiert die R-Funktion für die eigenständige Version: SQL Server Machine Learning Server (eigenständig). Ein eigenständiger Server ist eine "freigegebene Funktion", die nicht an eine Datenbank-Engine-Instanz gebunden ist.|
| /FEATURES = SQL_SHARED_MPY | Hiermit wird die python-Funktion für die eigenständige Version installiert: SQL Server Machine Learning Server (eigenständig). Ein eigenständiger Server ist eine "freigegebene Funktion", die nicht an eine Datenbank-Engine-Instanz gebunden ist.|
| /IACCEPTROPENLICENSETERMS  | Gibt an, dass Sie die Lizenzbedingungen für die Verwendung der Open Source-R-Komponenten akzeptiert haben. |
| /IACCEPTPYTHONLICENSETERMS | Gibt an, dass Sie die Lizenzbedingungen für die Verwendung der python-Komponenten akzeptiert haben. |
| /IACCEPTSQLSERVERLICENSETERMS | Gibt an, dass Sie die Lizenzbedingungen für die Verwendung von SQL Server akzeptiert haben.|
| MRCACHEDIRECTORY | Für das Offline-Setup wird der Ordner mit den CAB-Dateien der R-Komponente festgelegt. |
| /MPYCACHEDIRECTORY | Zur künftigen Verwendung reserviert. Verwenden Sie% Temp%, um die CAB-Dateien von python-Komponenten für die Installation auf Computern zu speichern, die keine Internetverbindung haben. |
::: moniker-end

## <a name="indb"></a>Installationen in der Daten Bank Instanz

Datenbankmodul Instanzen, die zum Hinzufügen des **advancedanalytics** -Features zur Installation erforderlich sind, sind in-Database-Analysen verfügbar. Sie können eine Datenbank-Engine-Instanz mit Advanced Analytics installieren oder einer [vorhandenen Instanz hinzufügen](#add-existing). 

Verwenden Sie das/QS-Argument, um Statusinformationen ohne interaktive Aufforderungen auf dem Bildschirm anzuzeigen.

> [!IMPORTANT]
> Nach der Installation bleiben zwei zusätzliche Konfigurationsschritte aus. Die Integration ist nicht fertiggestellt, bis diese Aufgaben ausgeführt werden. Anweisungen hierzu finden Sie unter [Aufgaben nach der Installation](#post-install) .

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
### <a name="sql-server-machine-learning-services-database-engine-advanced-analytics-with-python-and-r"></a>SQL Server Machine Learning Services: Datenbank-Engine, erweiterte Analysen mit Python und R

Geben Sie für eine parallele Installation der Datenbank-Engine-Instanz den Instanznamen und einen Administrator (Windows)-Anmelde Namen an. Integrieren Sie Features zum Installieren von Kern-und Sprachkomponenten sowie die Annahme aller Lizenzbedingungen.

```cmd
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Dabei handelt es sich um denselben Befehl, aber mit einer SQL Server Anmeldung bei einer Datenbank-Engine mit gemischter Authentifizierung.

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<sql-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Dieses Beispiel ist nur python und zeigt, dass Sie eine Sprache hinzufügen können, indem Sie ein Feature weglassen.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTPYTHONLICENSETERMS
```
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
### <a name="sql-server-r-services-database-engine-and-advanced-analytics-with-r"></a>SQL Server R Services: Datenbank-Engine und erweiterte Analysen mit R

Geben Sie für eine parallele Installation der Datenbank-Engine-Instanz den Instanznamen und einen Administrator (Windows)-Anmelde Namen an. Integrieren Sie Features zum Installieren von Kern-und Sprachkomponenten sowie die Annahme aller Lizenzbedingungen.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS 
```
::: moniker-end

## <a name="post-install"></a>Konfiguration nach der Installation (erforderlich)

Gilt nur für in-Database-Installationen.

Wenn das Setup abgeschlossen ist, verfügen Sie über eine Instanz der Datenbank-Engine mit R und Python, den Microsoft r-und Python-Paketen, Microsoft r Open, Anaconda, Tools, Beispielen und Skripts, die Teil der Verteilung sind. 

Zum Abschluss der Installation sind zwei weitere Aufgaben erforderlich:


::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
1. Starten Sie den Datenbank-Engine-Dienst neu.

1. SQL Server Machine Learning Services: Aktivieren Sie externe Skripts, bevor Sie die Funktion verwenden können. Befolgen Sie die Anweisungen unter [Installieren von SQL Server Machine Learning Services (in-Database)](sql-machine-learning-services-windows-install.md) im nächsten Schritt. 
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
1. Starten Sie den Datenbank-Engine-Dienst neu.

1. SQL Server R Services: Aktivieren Sie externe Skripts, bevor Sie die Funktion verwenden können. Befolgen Sie die Anweisungen unter [Installieren von SQL Server R Services (in-Database)](sql-r-services-windows-install.md) im nächsten Schritt. 
::: moniker-end

## <a name="add-existing"></a>Hinzufügen von erweiterten Analysen zu einer vorhandenen Datenbank-Engine-Instanz

Wenn Sie einer vorhandenen Datenbank-Engine-Instanz in-Database Advanced Analytics hinzufügen, geben Sie den Instanznamen an. Wenn Sie z. b. zuvor eine SQL Server 2017-Datenbank-Engine und Python installiert haben, können Sie mit diesem Befehl R hinzufügen.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQL_INST_MR /INSTANCENAME=MSSQLSERVER 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTROPENLICENSETERMS
```

## <a name="silent"></a>Unbeaufsichtigte Installation

Bei einer automatischen Installation wird die Prüfung auf CAB-Dateispeicher Orte unterdrückt. Aus diesem Grund müssen Sie den Speicherort angeben, an dem CAB-Dateien entpackt werden. Für python müssen sich die CAB-Dateien in% Temp * befinden. Für R können Sie den Ordner Pfad mit dem temporären Verzeichnis für dieses festlegen.
 
```cmd  
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS 
/MRCACHEDIRECTORY=%temp% 
```

## <a name="shared-feature"></a>Eigenständige Serverinstallationen

Ein eigenständiger Server ist eine "freigegebene Funktion", die nicht an eine Datenbank-Engine-Instanz gebunden ist. In den folgenden Beispielen wird die gültige Syntax für die Installation des eigenständigen Servers veranschaulicht.

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
SQL Server Machine Learning Server unterstützt python und R auf einem eigenständigen Server:

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR,SQL_SHARED_MPY  
/IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
SQL Server R Server ist nur R:

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR 
/IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```
::: moniker-end

Wenn das Setup abgeschlossen ist, verfügen Sie über einen Server, Microsoft-Pakete, Open-Source-Distributionen von R und Python, Tools, Beispiele und Skripts, die Teil der Verteilung sind. 

Um ein Fenster der R-Konsole zu öffnen `\Program files\Microsoft SQL Server\150 (or 140/130)\R_SERVER\bin\x64` , navigieren Sie zu, und doppelklicken Sie auf **rgui. exe**. Haben Sie noch keine Erfahrung mit R? Testen Sie dieses Tutorial: [Grundlegende R-Befehle und revoscaler-Funktionen: 25 gängige Beispiele](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler).

Um einen python-Befehl zu öffnen, `\Program files\Microsoft SQL Server\150 (or 140)\PYTHON_SERVER\bin\x64` navigieren Sie zu, und doppelklicken Sie auf " **python. exe**".

## <a name="get-help"></a>Hilfe

Benötigen Sie Hilfe bei der Installation oder beim Upgrade? Antworten auf häufig gestellte Fragen und bekannte Probleme finden Sie im folgenden Artikel:

* [FAQ zu Upgrade und Installation-Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Um den Installationsstatus der-Instanz zu überprüfen und häufige Probleme zu beheben, probieren Sie diese benutzerdefinierten Berichte aus.

* [Benutzerdefinierte Berichte für SQL Server](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen loslegen und die Grundlagen der Funktionen von R unter SQL Server kennenlernen. Informationen zu den nächsten Schritten finden Sie unter den folgenden Links:

+ [Tutorial: Ausführen von R in T-SQL](../tutorials/quickstart-r-create-script.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python-Entwickler können in den folgenden Tutorials erfahren, wie Python mit SQL Server verwendet werden kann:

+ [Tutorial: Ausführen von Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutorial: Datenbankinterne Analysen für Python-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Praxisbeispiele für die Verwendung von Machine Learning finden Sie unter [Tutorials für Machine Learning](../tutorials/machine-learning-services-tutorials.md).