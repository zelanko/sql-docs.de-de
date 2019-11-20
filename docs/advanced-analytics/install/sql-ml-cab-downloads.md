---
title: Herunterladen von Updates für die Offlineinstallation
description: Laden Sie CAB- und Paketdateien in R und Python für SQL Server Machine Learning Services und SQL Server 2016 R Services herunter.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e7266d90e04071c242145fc0df2e59ce86d86a16
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727624"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>CAB-Dateidownloads für kumulative Updates für SQL Server-Instanzen für datenbankinterne Analysen

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server-Instanzen, die für datenbankinterne Analysen konfiguriert sind, beinhalten R- und Python-Funktionen. Diese Funktionen sind in CAB-Dateien enthalten und werden über das SQL Server-Setup installiert und gewartet. Auf Geräten, die mit dem Internet verbunden sind, werden CAB-Updates in der Regel über Windows Update angewendet. Auf nicht verbundenen Servern müssen CAB-Dateien heruntergeladen und manuell angewendet werden. 

Dieser Artikel enthält Downloadlinks für CAB-Dateien für alle kumulativen Updates. Weitere Informationen zur Offlineinstallation finden Sie unter [Installieren von SQL Server-Machine Learning-Komponenten ohne Internetzugang](sql-ml-component-install-without-internet-access.md#apply-cu).

## <a name="prerequisites"></a>Voraussetzungen

Beginnen Sie mit einer Baselineinstallation.

+ Bei SQL Server Machine Learning Services ist das erste Release die Baselineinstallation. 
+ Bei SQL Server 2016 R Services können Sie mit dem ersten Release, SP1 oder SP2 beginnen. 

Sie können kumulative Updates auch auf einen eigenständigen Server anwenden.

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

## <a name="sql-server-2017-cabs"></a>CAB-Dateien für SQL Server 2017

CAB-Dateien werden in umgekehrter chronologischer Reihenfolge aufgelistet. Wenn Sie die CAB-Dateien herunterladen und auf den Zielcomputer übertragen, speichern Sie diese in einem passenden Ordner wie etwa **Downloads** oder im Setup-Ordner „%temp%“ des Benutzers.

|Release  |Komponente | Downloadlink  | Behobene Probleme | 
|---------|----------|----------------|------------------|
|**[SQL Server 2017 CU14](https://support.microsoft.com/help/4484710/)-[CU15](https://support.microsoft.com/help/4498951/)-[CU16](https://support.microsoft.com/help/4508218/)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2073898&clcid=1033)| Im Paket enthaltene Binärdateien sind jetzt signiert. |
| | R Server      |[SRS_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2069739&clcid=1033)| Im Paket enthaltene Binärdateien sind jetzt signiert. |
| | Microsoft Python Open     | [SPO_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2073897&clcid=1033)| Im Paket enthaltene Binärdateien sind jetzt signiert. |
| | Python-Server    |[SPS_9.2.0.1400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2071421&clcid=1033)| Im Paket enthaltene Binärdateien sind jetzt signiert.  |
|**[SQL Server 2017 CU13](https://support.microsoft.com/help/4466404)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | R Server      |[SRS_9.2.0.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2038263&clcid=1033)| Enthält die Korrektur eines Problems beim Aktualisieren eines [operationalisierten eigenständigen R-Servers](https://docs.microsoft.com/machine-learning-server/what-is-operationalization) bei der Installation durch das SQL Server-Setup. Verwenden Sie die CAB-Dateien von CU13, und führen Sie [diese Anweisungen](sql-machine-learning-standalone-windows-install.md#apply-cu) aus, um das Update anzuwenden. |
| | Microsoft Python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | Python-Server    |[SPS_9.2.0.1300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2038197&clcid=1033)| Enthält die Korrektur eines Problems beim Aktualisieren eines [operationalisierten eigenständigen Python-Servers](https://docs.microsoft.com/machine-learning-server/what-is-operationalization) bei der Installation durch das SQL Server-Setup. Verwenden Sie die CAB-Dateien von CU13, und führen Sie [diese Anweisungen](sql-machine-learning-standalone-windows-install.md#apply-cu) aus, um das Update anzuwenden. |
|**[SQL Server 2017 CU10](https://support.microsoft.com/help/4342123)-[CU11](https://support.microsoft.com/help/4462262)-[CU12](https://support.microsoft.com/help/4464082)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | R Server      |[SRS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006287&clcid=1033)| Einige kleinere Korrekturen.|
| | Microsoft Python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | Python-Server    |[SPS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006805&clcid=1033)| Die Python-Funktion „rx_data_step“ verliert die Zeilenreihenfolge, wenn Duplikate entfernt werden. <br/>SPEE erkennt den Datentyp bei einem gruppierten Columnstore-Index nicht. <br/>Gibt eine leere Tabelle zurück, wenn alle Spalten NULL-Werte enthalten. |
|**[SQL Server 2017 CU8](https://support.microsoft.com/help/4338363)-[CU9](https://support.microsoft.com/help/4341265)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
| | Microsoft Python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | Python-Server    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)|
|**[SQL Server 2017 CU6](https://support.microsoft.com/help/4101464)-[CU7](https://support.microsoft.com/help/4229789)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
| | Microsoft Python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | Python-Server    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)| DateTime-Datentypen in der SPEES-Abfrage.<br/>Verbesserte Fehlermeldungen in MicrosoftML, wenn vortrainierte Modelle fehlen.<br/> Korrekturen für revoscalepy-Transformationsfunktionen und -Variablen.|
|**[SQL Server 2017 CU5](https://support.microsoft.com/help/4092643)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)| Lange pfadbezogene Fehler in rxInstall-Paketen.<br/>Verbindungen in einem Loopback für RxExec.
| | Microsoft Python Open    | Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | Python-Server    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)| <br/>Verbindungen in einem Loopback für „rx_exec“.
|**[SQL Server 2017 CU4](https://support.microsoft.com/help/4056498)** |  |   |  |
| | Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
| | Microsoft Python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| |  Python-Server    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
|**[SQL Server 2017 CU3](https://support.microsoft.com/help/4052987)** |  |  |  |
| | Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
| | R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
| | Microsoft Python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | Python-Server    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)| Serialisierung von Python-Modellen in revoscalepy mithilfe der [Funktion „rx_serialize_model“](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/>Unterstützung der [nativen Bewertung](../sql-native-scoring.md) und Verbesserungen bei der [Echtzeitbewertung](../real-time-scoring.md). 
|**[SQL Server 2017 CU1](https://support.microsoft.com/help/4038634)-[CU2](https://support.microsoft.com/help/4052574)** |  |  |  |
| | Microsoft R Open     | [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)| Keine Veränderungen im Vergleich zu Vorgängerversionen. |
| | R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
| | Microsoft Python Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Keine Veränderungen im Vergleich zu Vorgängerversionen. | 
| | Python-Server    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) | Fügt „rx_create_col_info“ zur Rückgabe von Schemainformationen hinzu. <br/>Verbesserungen an [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) zur Unterstützung von parallelen Szenarios mithilfe des Computekontexts `RxLocalParallel`.|
|**Erstes Release** |  |  |
| | Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
| | R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
| | Microsoft Python Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
| | Python-Server    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |

::: moniker-end

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"

<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>CAB-Dateien für SQL Server 2016

Bei SQL Server 2016 R Services stellen Baselinereleases entweder die RTM-Version oder eine Service Pack-Version dar.

|Release  |Downloadlink  |
|---------|---------------|
|**SQL Server 2016 SP2 CU6**     |
|Microsoft R Open     |[SRO_3.2.2.20100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079936&clcid=1033)|
|Microsoft R Server    |[SRS_8.0.3.20100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079933&clcid=1033)|
|**SQL Server 2016 SP2 CU1–CU5**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
|**SQL Server 2016 SP2**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)|
|**SQL Server 2016 SP1 CU14**     |
|Microsoft R Open     |[SRO_3.2.2.16100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2080130&clcid=1033)|
|Microsoft R Server    |[SRS_8.0.3.17200_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2079935&clcid=1033)|
|**SQL Server 2016 SP1 CU1–CU13**     |
|Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
|Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
|**SQL Server 2016 SP1**     |
|Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)|
|Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)|
|**SQL Server 2016 CU4–CU9**     |
|Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
|Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
|**SQL Server 2016 CU2–CU3**     |
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
> Laden Sie für die Offlineinstallation von SQL Server 2016 SP1 CU4 oder SP1 CU5 die Datei „SRO_3.2.2.16000_1033.cab“ herunter. Wenn Sie wie im Setup-Dialogfeld angegeben „SRO_3.2.2.13000_1033.cab“ von FWLINK 831785 heruntergeladen haben, benennen Sie die Datei vor der Installation des kumulativen Updates in „SRO_3.2.2.16000_1033.cab“ um.

Wenn Sie den Quellcode für Microsoft R anzeigen möchten, können Sie ihn als Archiv im TAR-Format herunterladen: [Herunterladen von R Server-Installern](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download).

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

[Anwenden kumulativer Updates auf Computern ohne Internetzugang](sql-ml-component-install-without-internet-access.md#apply-cu)

[Anwenden kumulativer Updates auf Computern mit Internetverbindung](sql-ml-component-install-without-internet-access.md#apply-cu)

[Anwenden kumulativer Updates auf einem eigenständigen Server](sql-machine-learning-standalone-windows-install.md#apply-cu)
