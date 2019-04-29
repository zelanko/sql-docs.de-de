---
title: SandDance für Azure Data Studio
titleSuffix: Azure Data Studio
description: Verwenden von SandDance in Azure Data Studio
ms.custom: seodec18
ms.date: 04/18/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 8fe968185f05c7a48415e5e158a20f4dc61b28c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63142192"
---
# <a name="sanddance-for-azure-data-studio-preview"></a>SandDance für Azure Data Studio (Vorschau)
Azure Data Studio bietet nun eine Möglichkeit, schnelle Visualisierungen für die CSV und TSV-Dateien zu erstellen, an dem Sie arbeiten. Dies schließt lokale Dateien oder Dateien in HDFS in den SQL Server 2019 Big Data-Cluster an. Diese Erweiterung ist hilfreich, wenn Sie versuchen, Sie haben eine kurze, sehen Sie sich die Daten und zu verstehen, was vor sich geht. Wir verwenden eine Technologie namens SandDance von Microsoft Research, die für ein direktes Visualisierungen der Daten generieren können.

![sanddance-animation](https://user-images.githubusercontent.com/11507384/54236654-52d42800-44d1-11e9-859e-6c5d297a46d2.gif)

Leicht verständliche Ansichten SandDance können Sie zu Ihren Daten, die in der deaktivieren-Hilfe, die Sie Erzählen Sie Geschichten, die von den Daten, unterstützt Fälle basierend auf den Beweis zu erstellen Erkenntnisse, verwenden Hypothesen zu testen, tiefer in die Oberfläche Erklärungen, Unterstützung von Entscheidungen für Käufe, oder Verknüpfen Sie Daten in eine größere, praktische-Kontext.

SandDance verwendet Einheit Visualisierungen, die eine 1: 1-Zuordnung zwischen Zeilen in der Datenbank und Markierungen auf dem Bildschirm zu gelten.
Smooth animierten Übergänge zwischen den Ansichten können Sie Kontext beibehalten, während Sie sich mit Ihren Daten interagieren.

## <a name="usage"></a>Verwendung

Verwenden Sie beginnend mit dem Menü "Datei" Ordner öffnen "oder" [STRG + K, STRG + O], öffnen Sie das Verzeichnis mit der. CSV-Datei.  Als Nächstes von innerhalb des Bereichs Explorer mit der rechten Maustaste auf das CSV- oder TSV-Datei und *Ansicht SandDance*.

Mit der rechten Maustaste auf eine CSV- oder TSV-Datei in HDFS an, wenn Sie mit SQL Server 2019 Big Data-Cluster verbunden sind, und wählen Sie *Ansicht SandDance*.

## <a name="known-issues"></a>Bekannte Probleme

Aktuell müssen Ihre Daten die erste Spalte als eindeutiger Bezeichner.

Wir sind derzeit nicht die Anzahl der Zeilen begrenzen, die sichtbar gemacht wird. Jedoch steigt Arbeitsspeicherverbrauch proportional auf die Anzahl der Zeilen, daher wird empfohlen, dass das Dataset oder die Sicht auf ungefähr 100 k Zeilen beschränkt ist.

Finden Sie unter [bekannte Probleme](https://microsoft.github.io/SandDance/#known-issues)

## <a name="release-notes"></a>Versionsanmerkungen

### <a name="100"></a>1.0.0

Erste Version von Azdata-sanddance

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen, [finden Sie auf das GitHub-Repository.](https://github.com/Microsoft/SandDance)
