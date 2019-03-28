---
title: Eingabeaufforderungs-Installation von R und Python-Komponenten – SQL Server-Machine Learning
description: Führen Sie SQL Server-Setup-Befehlszeile zum Hinzufügen von R-Sprache und die Integration von Python auf SQL Server-Datenbank-Engine-Instanz.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: d852cc745578d852b2c8235ebcaf3614020a1bb8
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511747"
---
# <a name="install-sql-server-machine-learning-r-and-python-components-from-the-command-line"></a>Installieren von SQL Server-Machine learning-R und Python-Komponenten über die Befehlszeile
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel enthält Anweisungen zum Installieren wollte SQL Server Machine learning-Komponenten über die Befehlszeile an:

+ [Neue In-Database-Instanz](#indb)
+ [Fügen Sie zu einer vorhandenen Datenbank-Engine-Instanz hinzu](#add-existing)
+ [Unbeaufsichtigte Installation](#silent)
+ [Neuer eigenständiger server](#shared-feature)

Sie können automatische, Standard- oder vollständige Interaktion mit der Setup-Benutzeroberfläche angeben. Dieser Artikel ergänzt [Installieren von SQL Server über die Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md), behandelt die Parameter, die nur für R und Python-Machine-Learning-Komponenten.

## <a name="pre-install-checklist"></a>Checkliste für die vor der Installation

+ Ausführen von Befehlen an einer Eingabeaufforderung mit erhöhten Rechten aus. 

+ Eine Instanz der Datenbank-Engine ist für die Installation der in der Datenbank erforderlich. Nur R oder Python-Funktionen, kann nicht installiert werden, jedoch Sie können [inkrementell zu einer vorhandenen Instanz hinzufügen](#add-existing). Installieren Sie nur R und Python ohne die Datenbank-Engine können die [eigenständiger Server](#shared-feature).

+ Installieren Sie nicht in einem Failovercluster installieren. Der Sicherheitsmechanismus, der zum Isolieren von R und Python-Prozessen verwendet, ist nicht mit einer Windows Server-Failoverclusterumgebung kompatibel.

+ Installieren Sie nicht auf einem Domänencontroller. Der Machine Learning-Dienste Teil der Installation schlägt fehl.

+ Vermeiden Sie die eigenständige und in der Datenbank-Instanzen auf demselben Computer installieren. Ein eigenständigen Server konkurrieren um dieselben Ressourcen, die Leistung der beiden Installationen unterminieren.


## <a name="command-line-arguments"></a>Befehlszeilenargumente

Das Argument Funktionen ist es erforderlich, Begriff Vereinbarungen lizenzieren. 

Wenn Sie über die Eingabeaufforderung installieren, unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des /Q-Parameters den vollständigen stillen Modus oder mithilfe des /QS-Parameters den einfachen stillen Modus. Mithilfe des /QS-Schalters wird nur der Fortschritt angezeigt, es sind jedoch keine Eingaben möglich. Außerdem werden beim Auftreten von Fehlern keine Fehlermeldungen angezeigt. Der /QS-Parameter wird nur unterstützt, wenn /Action=install angegeben wurde.

| Argumente | Description |
|-----------|-------------|
| / FEATURES = AdvancedAnalytics | Die in der Datenbank-Version installiert: SQL Server 2017-Machine-Learning-Services (Datenbankintern) oder SQL Server 2016 R Services (Datenbankintern).  |
| /FEATURES = SQL_INST_MR | Gilt nur für SQLServer 2017. Koppeln Sie dies mit AdvancedAnalytics. Installiert die (In-Database) R-Funktion, einschließlich Microsoft R Open und proprietären R-Pakete. Das SQL Server 2016 R Services-Feature ist R nur, damit kein Parameter für diese Version vorhanden ist.|
| /FEATURES = SQL_INST_MPY | Gilt nur für SQLServer 2017. Koppeln Sie dies mit AdvancedAnalytics. Installiert die (In-Database) Python-Funktion, einschließlich Anaconda und den proprietären Python-Paketen. |
| /FEATURES = SQL_SHARED_MR | Die R-Funktion für die eigenständige Version wird installiert: SQL Server 2017-Machine-Learning-Server (eigenständig) oder SQL Server 2016 R Server (eigenständig). Ein eigenständigen Server ist eine "freigegebene Funktion" nicht an eine Datenbank-Engine-Instanz gebunden.|
| /FEATURES = SQL_SHARED_MPY | Gilt nur für SQLServer 2017. Die Python-Funktion für die eigenständige Version wird installiert: SQL Server 2017 Machine Learning Server (eigenständig). Ein eigenständigen Server ist eine "freigegebene Funktion" nicht an eine Datenbank-Engine-Instanz gebunden.|
| /IACCEPTROPENLICENSETERMS  | Gibt an, dass Sie die Lizenzbedingungen für die Verwendung der open-Source-R-Komponenten akzeptiert haben. |
| /IACCEPTPYTHONLICENSETERMS | Gibt an, dass Sie die Lizenzbedingungen für die Verwendung der Python-Komponenten akzeptiert haben. |
| /IACCEPTSQLSERVERLICENSETERMS | Gibt an, dass Sie die für die Verwendung von SQL Server-Lizenzbedingungen akzeptiert haben.|
| /MRCACHEDIRECTORY | Für offline-Setup festgelegt den, enthält die CAB-Dateien der R-Komponenten. |
| /MPYCACHEDIRECTORY | Zur künftigen Verwendung reserviert. Verwenden Sie % Temp%, um die CAB-Dateien der Python-Komponenten für die Installation auf Computern zu speichern, die nicht über eine Internetverbindung verfügen. |


## <a name="indb"></a> In-Database-Instanzen

Datenbankinterne Analysen stehen für die Datenbank-Engine-Instanzen, die erforderlich sind, für das Hinzufügen der **AdvancedAnalytics** Feature für Ihre Installation. Sie können eine Instanz der Datenbank-Engine mithilfe erweiterter Analysefunktionen installieren oder [zu einer vorhandenen Instanz hinzufügen](#add-existing). 

Verwenden Sie das/QS-Argument, um Statusinformationen, ohne die interaktive eingabeaufforderungen auf dem Bildschirm anzuzeigen.

> [!IMPORTANT]
> Bleiben nach der Installation zwei zusätzliche Konfigurationsschritte erforderlich. Integration ist nicht abgeschlossen werden, bis diese Tasks ausgeführt werden. Finden Sie unter [Aufgaben nach der Installation](#post-install) Anweisungen.

### <a name="sql-server-2017-database-engine-advanced-analytics-with-python-and-r"></a>SQLServer 2017: Datenbank-Engine, Erweiterte Analysen mit Python und R

Geben Sie für eine parallele Installation der Datenbank-Engine-Instanz den Namen der Instanz sowie eine administratoranmeldung (Windows). Enthalten Sie Funktionen für die Installation von Core und Sprachkomponenten sowie alle Lizenzbedingungen akzeptieren.

```cmd
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Diese denselben Befehl ein, aber mit einer SQL Server-Anmeldung auf einer Datenbank-Engine mit gemischten Authentifizierung.

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<sql-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

In diesem Beispiel wird Python nur anzeigt, dass Sie eine Sprache hinzufügen können, durch das Auslassen einer Funktion.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTPYTHONLICENSETERMS
```

### <a name="sql-server-2016-database-engine-and-advanced-analytics-with-r"></a>SQLServer 2016: Datenbank-Engine und erweiterte Analysen mit R

Dieser Befehl ist identisch zu SQL Server 2017, jedoch ohne die Python-Elemente, nicht verfügbar sind in SQL Server 2016-Setup.

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS 
```

## <a name="post-install"></a> (Erforderlich) Konfiguration nach der Installation

Um datenbankinterne nur Installationen gilt.

Wenn Setup abgeschlossen ist, müssen Sie eine Datenbank-Engine-Instanz mit R und Python, die Microsoft R und Python-Pakete, Microsoft R Open, Anaconda, Tools, Beispiele und Skripts, die Teil der Verteilung sind. 

Zwei weitere Aufgaben sind erforderlich, um die Installation abzuschließen:

1. Starten Sie den Datenbank-Engine-Dienst neu.

1. Aktivieren Sie externer Skripts, bevor Sie das Feature verwenden können. Befolgen Sie die Anweisungen in [installieren Sie SQL Server 2017 Machine Learning Services (Datenbankintern)](sql-machine-learning-services-windows-install.md) im nächsten Schritt. 

Für SQL Server 2016, in diesem Artikel verwenden Sie stattdessen [Installieren von SQL Server 2016 R Services (Datenbankintern)](sql-r-services-windows-install.md).

## <a name="add-existing"></a> Hinzufügen von erweiterten Analysen zu einer vorhandenen Datenbank-Engine-Instanz

Wenn Sie erweiterte Analysen in der Datenbank zu einer vorhandenen Datenbank-Engine-Instanz hinzufügen, geben Sie den Instanznamen an. Z. B. Wenn Sie eine SQL Server 2017-Datenbank-Engine und Python bereits installiert haben, können Sie mit diesem Befehl verwenden r hinzufügen

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQL_INST_MR /INSTANCENAME=MSSQLSERVER 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTROPENLICENSETERMS
```



## <a name="silent"></a> Unbeaufsichtigte Installation

Eine automatische Installation unterdrückt die Prüfung auf Speicherorte für CAB-Datei. Aus diesem Grund müssen Sie den Speicherort angeben, in dem CAB-Dateien werden entpackt. Für Python müssen die CAB-Dateien im % TEMP * befinden. Für R, können Sie den Ordner festlegen berichtspfaden, Sie können das temporäre Verzeichnis für diese.
 
```cmd  
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS 
/MRCACHEDIRECTORY=%temp% 
```

## <a name="shared-feature"></a> Eigenständige Serverinstallationen

Ein eigenständigen Server ist eine "freigegebene Funktion" nicht an eine Datenbank-Engine-Instanz gebunden. Die folgenden Beispiele zeigen gültigen Syntax für beide Versionen.

SQL Server 2017 unterstützt Python und R auf einem eigenständigen Server:

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR,SQL_SHARED_MPY  
/IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

SQL Server 2016 ist nur für R-:

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR 
/IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

Wenn Setup abgeschlossen ist, müssen Sie einen Server, Microsoft-Pakete, Open-Source-Verteilungen von R und Python-Tools, Beispiele und Skripts, die Teil der Verteilung sind. 

Öffnen ein R-Konsolenfenster, wechseln Sie zu \Programme\Microsoft SQL Server\140 (oder 130) \R_SERVER\bin\x64, und doppelklicken Sie auf **RGui.exe**. Haben Sie noch keine Erfahrung mit R? Dieses Tutorial ansehen: [Grundlegende R-Befehle und RevoScaleR-Funktionen: 25 häufige](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler).

Klicken Sie zum Öffnen eines Python-Befehls wechseln Sie zu \Programme\Microsoft SQL Server\140\PYTHON_SERVER\bin\x64, und doppelklicken Sie auf **python.exe**.

## <a name="get-help"></a>Hilfe

Benötigen Sie Hilfe bei der Installation oder Aktualisierung? Finden Sie Antworten auf häufig gestellte Fragen und bekannte Probleme finden Sie im folgenden Artikel:

* [Upgrade und Installation – häufig gestellte Fragen – Machine Learning-Dienste](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Versuchen Sie diese benutzerdefinierten Berichte, um den Installationsstatus der Instanz zu überprüfen und Behandeln häufig auftretender Probleme.

* [Benutzerdefinierte Berichte für SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen beginnen, und die Grundlagen der Funktionsweise von R mit SQL Server. Der nächste Schritt ist finden Sie in den folgenden Links:

+ [Tutorial: Run R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python-Entwickler erfahren, wie Python mit SQL Server verwenden, indem Sie die folgenden in diesen Tutorials:

+ [Tutorial: Ausführen von Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutorial: Datenbankinterne Analysen für Python-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Beispiele für Machine Learning, die auf realen Szenarien basieren, finden Sie unter [Machine learning-Tutorials](../tutorials/machine-learning-services-tutorials.md).