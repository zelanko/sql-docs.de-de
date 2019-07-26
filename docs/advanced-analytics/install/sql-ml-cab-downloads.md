---
title: CAB-Downloads für SQL Server kumulative Updates
description: R und python CAB und Paket Downloads für SQL Server 2017 Machine Learning Services und SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: ab87112d20d2571936fa7d61c34c5910859f2642
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470317"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>CAB-Downloads für kumulative Updates von SQL Server in-Database-Analyse Instanzen

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server Instanzen, die für Daten bankübergreifende Analysen konfiguriert sind, umfassen R-und Python-Funktionen. Diese Features werden in CAB-Dateien ausgeliefert, installiert und über SQL Server-Setup gewartet. Bei Geräten, die mit dem Internet verbunden sind, werden CAB-Updates normalerweise über Windows Update angewendet. Auf getrennten Servern müssen CAB-Dateien heruntergeladen und manuell angewendet werden. 

Dieser Artikel stellt Download Links zu CAB-Dateien für jedes kumulative Update bereit. Links werden sowohl für SQL Server 2017 Machine Learning Services (R und python) als auch für SQL Server 2016 R-Dienste bereitgestellt. Weitere Informationen zu Offline Installationen finden Sie unter [Installieren von SQL Server Machine Learning-Komponenten ohne Internetzugang](sql-ml-component-install-without-internet-access.md#apply-cu).

## <a name="prerequisites"></a>Vorraussetzungen

Beginnen Sie mit einer Baselineversion.

+ Auf SQL Server 2017 Machine Learning Services ist die erste Version die grundlegende Installation. 
+ Auf SQL Server 2016 R-Diensten können Sie mit der ersten Version von SP1 oder SP2 beginnen. 

Außerdem können Sie kumulative Updates auf einen eigenständigen Server anwenden.

## <a name="sql-server-2017-cabs"></a>SQL Server 2017-Cabs

CAB-Dateien werden in umgekehrter chronologischer Reihenfolge aufgelistet. Wenn Sie die CAB-Dateien herunterladen und auf den Zielcomputer übertragen, platzieren Sie Sie in einem bequemen Ordner, z. b. **Downloads** oder im Ordner "% Temp%" des Setup Benutzers.

|Release  |Komponente | Downloadlink  | Adressierte Probleme | 
|---------|----------|----------------|------------------|
|**[SQL Server 2017 CU14](https://support.microsoft.com/help/4484710/)-[CU15](https://support.microsoft.com/help/4498951/)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2073898&clcid=1033)| Binärdateien im Paket sind nun signiert. |
| | R Server      |[SRS_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2069739&clcid=1033)| Binärdateien im Paket sind nun signiert. |
| | Microsoft python Open     | [SPO_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2073897&clcid=1033)| Binärdateien im Paket sind nun signiert. |
| | Python-Server    |[SPS_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2071421&clcid=1033)| Binärdateien im Paket sind nun signiert.  |
|**[SQL Server 2017 CU13](https://support.microsoft.com/help/4466404)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Änderung gegenüber früheren Versionen. |
| | R Server      |[SRS_9.2.0.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2038263&clcid=1033)| Enthält eine Korrektur zum Aktualisieren eines [operationalisierten eigenständigen R Server](https://docs.microsoft.com/machine-learning-server/what-is-operationalization), wie durch SQL Server Setup installiert. Verwenden Sie die CU13 Cabs, und befolgen Sie [diese Anweisungen](sql-machine-learning-standalone-windows-install.md#apply-cu) , um das Update anzuwenden. |
| | Microsoft python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Änderung gegenüber früheren Versionen. |
| | Python-Server    |[SPS_9.2.0.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2038197&clcid=1033)| Enthält eine Korrektur für das Upgrade eines [operationalisierten eigenständigen python-Servers](https://docs.microsoft.com/machine-learning-server/what-is-operationalization), der über SQL Server-Setup installiert wurde. Verwenden Sie die CU13 Cabs, und befolgen Sie [diese Anweisungen](sql-machine-learning-standalone-windows-install.md#apply-cu) , um das Update anzuwenden. |
|**[SQL Server 2017 CU10](https://support.microsoft.com/help/4342123)-[CU11](https://support.microsoft.com/help/4462262)-[CU12](https://support.microsoft.com/help/4464082)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Änderung gegenüber früheren Versionen. |
| | R Server      |[SRS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006287&clcid=1033)| Einige kleinere Korrekturen.|
| | Microsoft python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Änderung gegenüber früheren Versionen. |
| | Python-Server    |[SPS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006805&clcid=1033)| Python rx_data_step verliert die Zeilen Reihenfolge, wenn Duplikate entfernt werden. <br/>Fehler bei der Datentyp-Erkennung für einen gruppierten columnstore--Index. <br/>Gibt eine leere Tabelle zurück, wenn Spalten alle NULL-Werte enthalten. |
|**[SQL Server 2017 CU8](https://support.microsoft.com/help/4338363)-[CU9](https://support.microsoft.com/help/4341265)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Änderung gegenüber früheren Versionen. |
| | R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
| | Microsoft python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Änderung gegenüber früheren Versionen. |
| | Python-Server    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)|
|**[SQL Server 2017 CU6](https://support.microsoft.com/help/4101464)-[CU7](https://support.microsoft.com/help/4229789)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Änderung gegenüber früheren Versionen. |
| | R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
| | Microsoft python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Änderung gegenüber früheren Versionen. |
| | Python-Server    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)| DateTime-Datentypen in der Abfrage.<br/>Verbesserte Fehlermeldungen in microsoftml, wenn vorab trainierte Modelle fehlen.<br/> Korrekturen für die revoscalepy-Transformations Funktionen und-Variablen.|
|**[SQL Server 2017 CU5](https://support.microsoft.com/help/4092643)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Änderung gegenüber früheren Versionen. |
| | R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)| Lange Pfad bezogene Fehler in rxinstallpackages.<br/>Verbindungen in einem Loopback für rxexec.
| | Microsoft python Open    | Keine Änderung gegenüber früheren Versionen. |
| | Python-Server    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)| <br/>Verbindungen in einem Loopback für rx_exec.
|**[SQL Server 2017 CU4](https://support.microsoft.com/help/4056498)** |  |   |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Änderung gegenüber früheren Versionen. |
| | R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
| | Microsoft python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Änderung gegenüber früheren Versionen. |
| |  Python-Server    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
|**[SQL Server 2017 CU3](https://support.microsoft.com/help/4052987)** |  |  |  |
| | Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
| | R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
| | Microsoft python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Änderung gegenüber früheren Versionen. |
| | Python-Server    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)| Python-modellserialisierung in revoscalepy mithilfe der [rx_serialize_model-Funktion](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/>[Native](../sql-native-scoring.md) Bewertungs Unterstützung sowie Verbesserungen bei der [Echtzeitbewertung](../real-time-scoring.md). 
|**[SQL Server 2017 CU1](https://support.microsoft.com/help/4038634)-[Cu2](https://support.microsoft.com/help/4052574)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)| Keine Änderung gegenüber früheren Versionen. |
| | R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
| | Microsoft python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Änderung gegenüber früheren Versionen. | 
| | Python-Server    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) | Fügt rx_create_col_info zum Zurückgeben von Schema Informationen hinzu. <br/>Verbesserungen an [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) zur Unterstützung paralleler Szenarien mithilfe des `RxLocalParallel` computekontexts.|
|**Anfängliche Version** |  |  |
| | Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
| | R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
| | Microsoft python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
| | Python-Server    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |


<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016-Cabs

Bei SQL Server 2016 R-Diensten sind baselinereleases entweder die RTM-Version oder eine Service Pack Version.

|Release  |Downloadlink  |
|---------|---------------|
|**SQL Server 2016 SP2 CU6**     |
|Microsoft R Open     |[SRO_3.2.2.20100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079936&clcid=1033)|
|Microsoft R Server    |[SRS_8.0.3.20100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079933&clcid=1033)|
|**SQL Server 2016 SP2 CU1-CU5**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
|**SQL Server 2016 SP2**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)|
|**SQL Server 2016 SP1 CU14**     |
|Microsoft R Open     |[SRO_3.2.2.16100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2080130&clcid=1033)|
|Microsoft R Server    |[SRS_8.0.3.17200_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079935&clcid=1033)|
|**SQL Server 2016 SP1 CU1-CU13**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
|**SQL Server 2016 SP1**     |
|Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)|
|Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)|
|**SQL Server 2016 CU4-CU9**     |
|Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
|Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
|**SQL Server 2016 Cu2-CU3**     |
|Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)|
|Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)|
|**SQL Server 2016 CU1**     |
|Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)|
|Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)|
|**SQL Server 2016 RTM**     |
|Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)|
|Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)|

> [!NOTE]
> 
> Wenn Sie SQL Server 2016 SP1 CU4 oder SP1 CU5 Offline installieren, laden Sie sro_ 3.2.2.16000 _1033. cab herunter. Wenn Sie sro_ 3.2.2.13000 _1033. cab von fwlink 831785 heruntergeladen haben, wie im Setup Dialogfeld angegeben, benennen Sie die Datei in sro_ 3.2.2.16000 _1033. cab um, bevor Sie das kumulative Update installieren.

Wenn Sie den Quellcode für Microsoft R anzeigen möchten, können Sie ihn als Archiv im tar-Format herunterladen: [Herunterladen R Server Installationsprogramme](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

## <a name="see-also"></a>Siehe auch

[Anwenden von kumulativen Updates auf Computern ohne Internet Zugriff](sql-ml-component-install-without-internet-access.md#apply-cu)

[Anwenden von kumulativen Updates auf Computern mit Internetverbindung](sql-ml-component-install-without-internet-access.md#apply-cu)

[Anwenden von kumulativen Updates auf einen eigenständigen Server](sql-machine-learning-standalone-windows-install.md#apply-cu)
