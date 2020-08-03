---
title: SandDance für Azure Data Studio
description: Erfahren Sie, wie Sie eine Azure Data Studio-Erweiterung verwenden, um schnell Visualisierungen Ihrer Daten zu erstellen, die Ihnen Erkenntnisse bieten.
ms.custom: seodec18
ms.date: 07/03/2019
ms.prod: azure-data-studio
ms.technology: ''
ms.reviewer: alayu, maghan, sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: b40ad2646f1eaa1534ab84cb0d638465588f2cd2
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411236"
---
# <a name="sanddance-for-azure-data-studio-preview"></a>SandDance für Azure Data Studio (Vorschau)
Azure Data Studio bietet nun eine Möglichkeit, schnelle Visualisierungen für Ihre Daten zu erstellen. Diese Erweiterung ist nützlich, wenn Sie einen Blick auf die Daten erhalten und verstehen möchten, was vor sich geht. Dazu wird eine Technologie namens SandDance von Microsoft Research verwendet, mit der direkte Visualisierungen der jeweiligen Daten generiert werden können.

![SandDance-Animation](https://user-images.githubusercontent.com/11507384/54236654-52d42800-44d1-11e9-859e-6c5d297a46d2.gif)

Durch Verwenden von leicht verständlichen Ansichten hilft SandDance Ihnen, Erkenntnisse über Ihre Daten zu gewinnen. Diese Erkenntnisse ermöglichen es Ihnen wiederum, datengestützte Analysen zu formulieren, Fälle auf der Grundlage von Beweisen zu erstellen, Hypothesen zu testen, tiefer in Oberflächenerläuterungen einzutauchen, Kaufentscheidungen zu unterstützen oder Daten in einen breiteren, realen Kontext einzubeziehen.

SandDance verwendet einheitenbezogene Visualisierungen, bei denen eine Eins-zu-eins-Zuordnung zwischen Zeilen in Ihrer Datenbank und Markierungen auf dem Bildschirm angewendet wird.
Sanfte animierte Übergänge zwischen Ansichten helfen Ihnen, den Kontext beizubehalten, während Sie mit den Daten arbeiten.

## <a name="usage"></a>Verwendung

### <a name="view-csv-or-tsv-files"></a>Anzeigen von CSV- oder TSV-Dateien
Dies gilt für lokale Dateien oder Dateien auf HDFS in Ihrem SQL Server 2019-Big Data-Cluster.
 
Wählen Sie im Menü „Datei“ den Befehl „Ordner öffnen“ aus, oder drücken Sie [STRG+K STRG+O], um das Verzeichnis zu öffnen, in dem sich die CSV-Datei befindet.  Klicken Sie anschließend im Explorer-Bereich mit der rechten Maustaste auf die CSV- oder TSV-Datei, und wählen Sie *In SandDance anzeigen* aus.

Klicken Sie mit der rechten Maustaste auf eine CSV- oder TSV-Datei in HDFS, wenn es eine Verbindung mit einem SQL Server 2019 Big Data-Cluster gibt, und wählen Sie *In SandDance anzeigen* aus.

### <a name="view-sql-query-results"></a>Anzeigen von SQL-Abfrageergebnissen

Führen Sie in einem SQL-Abfragefenster eine Abfrage aus, um ein Ergebnisraster zu erhalten. Klicken Sie auf der rechten Seite des Ergebnisbereichs auf das Symbol „Schnellansicht“.

## <a name="known-issues"></a>Bekannte Probleme

Derzeit wird die Anzahl der Zeilen, die visualisiert werden, nicht begrenzt. Da die Arbeitsspeichernutzung jedoch proportional zur Anzahl der Zeilen steigt, empfiehlt es sich, das Dataset oder die Ansicht auf etwa 100.000 Zeilen zu beschränken.

Weitere Informationen finden Sie unter [Bekannte Probleme](https://microsoft.github.io/SandDance/#known-issues).

## <a name="release-notes"></a>Versionsinformationen

### <a name="100"></a>1.0.0

Erste Version von „azdata-sanddance“

## <a name="next-steps"></a>Nächste Schritte
Um mehr zu erfahren, [besuchen Sie das GitHub-Repository](https://github.com/Microsoft/SandDance).
