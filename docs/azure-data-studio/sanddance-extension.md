---
title: SandDance für Azure Data Studio
titleSuffix: Azure Data Studio
description: Verwenden von SandDance in Azure Data Studio
ms.custom: seodec18
ms.date: 07/03/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: a96bde6a66642bf02cc076c3d4d4f3ac44e02a3f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959335"
---
# <a name="sanddance-for-azure-data-studio-preview"></a>SandDance für Azure Data Studio (Vorschau)
Azure Data Studio bietet nun eine Möglichkeit, schnelle Visualisierungen für die CSV- und TSV-Dateien zu erstellen, an denen Sie arbeiten. Dies gilt für lokale Dateien oder Dateien auf HDFS in Ihrem SQL Server 2019-Big Data-Cluster. Diese Erweiterung ist nützlich, wenn Sie einen schnellen Blick auf die Daten haben und verstehen möchten, was vor sich geht. Dazu wird eine Technologie namens SandDance von Microsoft Research verwendet, mit der direkte Visualisierungen der jeweiligen Daten generiert werden können.

![SandDance-Animation](https://user-images.githubusercontent.com/11507384/54236654-52d42800-44d1-11e9-859e-6c5d297a46d2.gif)

Durch Verwenden von leicht verständlichen Ansichten hilft SandDance Ihnen, Erkenntnisse über Ihre Daten zu gewinnen. Diese Erkenntnisse ermöglichen es Ihnen wiederum, datengestützte Analysen zu formulieren, Fälle auf der Grundlage von Beweisen zu erstellen, Hypothesen zu testen, tiefer in Oberflächenerläuterungen einzutauchen, Kaufentscheidungen zu unterstützen oder Daten in einen breiteren, realen Kontext einzubeziehen.

SandDance verwendet einheitenbezogene Visualisierungen, bei denen eine Eins-zu-eins-Zuordnung zwischen Zeilen in Ihrer Datenbank und Markierungen auf dem Bildschirm angewendet wird.
Sanfte animierte Übergänge zwischen Ansichten helfen Ihnen, den Kontext beizubehalten, während Sie mit den Daten arbeiten.

## <a name="usage"></a>Verwendung

Wählen Sie im Menü „Datei“ den Befehl „Ordner öffnen“ aus, oder drücken Sie [STRG+K STRG+O], um das Verzeichnis zu öffnen, in dem sich die CSV-Datei befindet.  Klicken Sie anschließend im Explorer-Bereich mit der rechten Maustaste auf die CSV- oder TSV-Datei, und wählen Sie *In SandDance anzeigen* aus.

Klicken Sie mit der rechten Maustaste auf eine CSV- oder TSV-Datei in HDFS, wenn es eine Verbindung mit einem SQL Server 2019 Big Data-Cluster gibt, und wählen Sie *In SandDance anzeigen* aus.

## <a name="known-issues"></a>Bekannte Probleme

Aktuell müssen Ihre Daten die erste Spalte als eindeutigen Bezeichner haben.

Derzeit wird die Anzahl der Zeilen, die visualisiert werden, nicht begrenzt. Da die Arbeitsspeichernutzung jedoch proportional zur Anzahl der Zeilen steigt, empfiehlt es sich, das Dataset oder die Ansicht auf etwa 100.000 Zeilen zu beschränken.

Weitere Informationen finden Sie unter [Bekannte Probleme](https://microsoft.github.io/SandDance/#known-issues).

## <a name="release-notes"></a>Versionsanmerkungen

### <a name="100"></a>1.0.0

Erste Version von „azdata-sanddance“

## <a name="next-steps"></a>Next Steps
Um mehr zu erfahren, [besuchen Sie das GitHub-Repository](https://github.com/Microsoft/SandDance).
