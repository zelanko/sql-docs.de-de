---
title: Schemavergleich-Erweiterung
titleSuffix: Azure Data Studio
description: Installieren und Verwenden der Schemavergleicherweiterung für Azure Data Studio
ms.custom: seodec18
ms.date: 11/04/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: f93711983eb32a979e47941883e968b52e03459c
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532543"
---
# <a name="schema-compare-extension"></a>Schemavergleich-Erweiterung
Die Schemavergleicherweiterung bietet eine benutzerfreundliche Umgebung, in der zwei Datenbankdefinitionen verglichen und die Unterschiede aus der Quelle auf das Ziel angewendet werden können.


## <a name="features"></a>Funktionen

* Vergleichen von Schemas von zwei DACPAC-Dateien oder -Datenbanken
* Anzeigen von Ergebnissen als Aktionen, die für das Ziel durchgeführt werden müssen, damit dieses der Quelle entspricht
* Selektives Ausschließen von in den Ergebnissen aufgeführten Aktionen
* Festlegen von Optionen, die den Bereich des Vergleichs steuern
* Anwenden von Änderungen auf das Ziel oder Generieren eines Skripts mit der gleichen Auswirkung
* Speichern des Vergleichs

![Schemavergleich: Beispielvergleich](media/extensions/schema-compare-extension/schema-compare.png)


## <a name="why-would-i-use-the-schema-compare-extension"></a>Warum sollte ich die Schemavergleicherweiterung verwenden?

Es kann mühsam sein, unterschiedliche Datenbankversionen manuell zu verwalten und zu synchronisieren. Mit der Schemavergleicherweiterung wird der Vergleichsprozess von Datenbanken vereinfacht, und Sie erhalten volle Kontrolle beim Synchronisieren dieser Datenbanken. Sie können nach bestimmten Unterschieden und Unterschiedkategorien filtern, bevor Sie die Änderungen anwenden. Die Schemavergleicherweiterung ist ein zuverlässiges Tool, mit dem Sie Zeit und Code sparen.

![Schemavergleich: Dialogfeld „Optionen“](media/extensions/schema-compare-extension/schema-compare-options.png)


## <a name="install-the-extension"></a>Installieren der Erweiterung

1. Klicken Sie auf das Symbol „Erweiterungen“, um die verfügbaren Erweiterungen anzuzeigen.

    ![Erweiterungs-Manager-Symbol](media/extensions/extension-manager-icon.png)

2. Suchen Sie nach der Erweiterung **Schemavergleich**, und wählen Sie sie aus, um die Details anzuzeigen. Klicken Sie auf **Installieren**, um die Erweiterung hinzuzufügen.

3. Klicken Sie nach der Installation auf **Erneut laden**, um die Erweiterung in Azure Data Studio zu aktivieren (nur bei der ersten Installation einer Erweiterung erforderlich).


## <a name="launch-a-schema-compare"></a>Starten des Schemavergleichs

1. Führen Sie einen **Rechtsklick** auf eine Datenbank im Objekt-Explorer durch, und klicken Sie dann auf **Schemavergleich**, um das Dialogfeld „Schemavergleich“ zu öffnen. Die Datenbank, die Sie auswählen, wird als Quelldatenbank im Vergleich festgelegt.

    ![Menü zum Starten des Schemavergleichs](media/extensions/schema-compare-extension/schema-compare-launch.png)


2. Klicken Sie auf jeweiligen Auslassungspunkte (...) neben Quelle und Ziel, um die Quelle und das Ziel Ihres Schemavergleichs zu ändern, und klicken Sie dann auf „OK“.

    ![Auswahl von Schemavergleichsquelle- und ziel](media/extensions/schema-compare-extension/schema-compare-select-source-target.png)

3. Klicken Sie auf die Schaltfläche **Optionen** in der Symbolleiste, um Ihren Vergleich anzupassen.

4. Klicken Sie auf **Vergleichen**, um die Ergebnisse des Vergleichs anzuzeigen.


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Schemavergleich finden Sie in der zugehörigen [Dokumentation](https://docs.microsoft.com/sql/ssdt/how-to-use-schema-compare-to-compare-different-database-definitions).
Probleme und Featureanforderungen können Sie [hier](https://github.com/microsoft/azuredatastudio/issues) mitteilen.