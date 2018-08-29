---
title: CAB-Datei für den kumulativen Updates für SQL Server-downloads | Microsoft-Dokumentation
description: CAB-Downloads für SQL Server 2017-Machine Learning Services und SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 57481eaee3ee6de5816e69edda2936d4ee30fc49
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118283"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>CAB-downloads für kumulative Updates Analysefunktionen von SQL Server in der Datenbank-Instanzen

SQL Server-Instanzen, die für in-Database-Analyse konfiguriert einschließen, R und Python-Funktionen, die in CAB-Dateien installiert ist und über serviced SQL Server-Setup enthalten sind. 

Auf Servern, die mit dem Internet verbunden werden werden die CAB-Updates über Windows Update in der Regel angewendet. Nicht verbundene Server müssen manuell aktualisiert werden. Eine Anleitung zum offline-Installation finden Sie unter [Installieren von SQL Server-Machine learning-Komponenten ohne Internetzugang](sql-ml-component-install-without-internet-access.md).

Dieser Artikel enthält Links zum Herunterladen der CAB-Dateien für die kumulativen Updates von SQL Server 2017 Machine Learning Services (R- und Python) – oder SQL Server 2016 R Services –, damit Sie vom Internet getrennt Server manuell aktualisieren. 

## <a name="prerequisites"></a>Erforderliche Komponenten

Beginnen Sie mit einer Basisinstallation.

+ Auf SQL Server 2017 Machine Learning Services ist die erste Version die Baseline-Installation. 
+ Auf SQL Server 2016 R Services können Sie mit der ersten Version, SP1 oder SP2 starten. 

Als Nächstes wenden [kumulativen Updates](https://support.microsoft.com/help/4047329) für SQL Server-Datenbank-Engine-Instanz.

Wenn Sie eine Basisinstallation und kumulativen Updates auf SQL Server angewendet haben, können Sie Ausführen einer [slipstream-Upgrade](sql-ml-component-install-without-internet-access.md#slipstream-upgrades) Installieren der CAB-Dateien mit Machine Learning-Features aktualisiert.

CAB-Dateien werden in umgekehrter chronologischer Reihenfolge aufgeführt. Wenn Sie die CAB-Dateien herunterladen und auf den Zielcomputer übertragen, sie in einem geeigneten Ordner speichern wie z. B. **Downloads** oder des Setup-Benutzers % temp %-Ordner.

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 CAB-Dateien

Release  |Downloadlink  | Problembehebungen | 
---------|---------------|-------|
**[CU10](https://support.microsoft.com/help/4342123)** |  |  |
Microsoft R Open     |keine Änderung; Verwenden der vorherigen [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| |
R Server      |[SRS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006287&clcid=1033)| Einige kleinere Korrekturen.|
Öffnen Sie Microsoft-Python     |keine Änderung; Verwenden der vorherigen [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| |
Python-Server    |[SPS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006805&clcid=1033)| Python-Rx_data_step verliert Reihenfolge der Zeilen an, wenn Duplikate entfernt werden. <br/>Python-SPEE schlägt fehl, das Abrufen des Datentyps von gruppierten columnstore-Index unter bestimmten Bedingungen. <br/>Python wird eine leere Tabelle zurückgibt, wenn Spalten alle null-Werte enthalten. |
**[CU8](https://support.microsoft.com/help/4338363)-[CU9](https://support.microsoft.com/help/4341265)** |
Microsoft R Open     |keine Änderung; Verwenden der vorherigen [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
Öffnen Sie Microsoft-Python     |keine Änderung; Verwenden der vorherigen [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Python-Server    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)]|
**[CU6](https://support.microsoft.com/help/4101464)-[CU7](https://support.microsoft.com/help/4229789)** |
Microsoft R Open     |keine Änderung; Verwenden der vorherigen [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
Öffnen Sie Microsoft-Python     |keine Änderung; Verwenden der vorherigen [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Python-Server    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)|
**[CU5](https://support.microsoft.com/help/4092643)** |
Microsoft R Open     |keine Änderung; Verwenden der vorherigen [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)|
Öffnen Sie Microsoft-Python     |keine Änderung; Verwenden der vorherigen [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Python-Server    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)|
**[CU4](https://support.microsoft.com/help/4056498)** |
Microsoft R Open     |keine Änderung; Verwenden der vorherigen [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Öffnen Sie Microsoft-Python     |keine Änderung; Verwenden der vorherigen [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
 Python-Server    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
**[CU3](https://support.microsoft.com/help/4052987)** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Öffnen Sie Microsoft-Python     |keine Änderung; Verwenden der vorherigen [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Python-Server    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|
**[CU1](https://support.microsoft.com/help/4038634)-[CU2](https://support.microsoft.com/help/4052574)** |
Microsoft R Open     |keine Änderung; Verwenden der vorherigen [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Öffnen Sie Microsoft-Python     |keine Änderung; Verwenden der vorherigen [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Python-Server    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**Erste Version** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Öffnen Sie Microsoft-Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Python-Server    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |


<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016 CAB-Dateien

Sind für SQL Server 2016 R Services Baseline-Releases, entweder die RTM-Version oder ein Service Pack-Version.

Release  |Downloadlink  |
---------|---------------|
**SQL Server 2016 SP2 CU1-CU2**     |
Microsoft R Open     |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039)|
Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
**SQL Server 2016 SP1 CU4-CU10**     |
Microsoft R Open     |keine Änderung; Verwenden der vorherigen [SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**SQL Server 2016 SP1 CU1-CU3**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 SP1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)=
**SQL Server 2016 CU4-CU9**     |
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
**SQL Server 2016 CU2-CU3**     |
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)
**SQL Server 2016 CU1**     |
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)
**SQL Server 2016 RTM**     |
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)

> [!NOTE]
> 
> Wenn Sie SQL Server 2016 SP1 CU4 oder SP1 CU5 offline zu installieren, laden Sie SRO_3.2.2.16000_1033.cab herunter. Wenn Sie SRO_3.2.2.13000_1033.cab von FWLINK 831785 heruntergeladen, gemäß der einrichten (Dialogfeld), benennen Sie die Datei als SRO_3.2.2.16000_1033.cab vor der Installation des kumulativen Updates.

Wenn Sie den Quellcode für Microsoft R anzeigen möchten, es ist zum Download zur Verfügung als eines Archivs in TAR-Datei vor: [Installationsprogramme für R Server herunterladen](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

# <a name="see-also"></a>Siehe auch

[Installieren von SQL Server-Machine learning-Komponenten ohne Internetzugang](sql-ml-component-install-without-internet-access.md)
