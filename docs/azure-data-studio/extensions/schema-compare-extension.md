---
title: Schemavergleich-Erweiterung
description: Erfahren Sie, wie Sie die Schemavergleich-Erweiterung für Azure Data Studio installieren, um zwei Datenbanken mühelos zu vergleichen und eine selektiv zu ändern, damit diese mit der anderen Datenbank übereinstimmt.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.reviewer: maghan, sstein
ms.custom: ''
ms.date: 11/04/2019
ms.openlocfilehash: 35afe56806ad1c24b1fa6ae1f03978d7f6558af4
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91123352"
---
# <a name="schema-compare-extension"></a>Schemavergleich-Erweiterung

Die Schemavergleicherweiterung bietet eine benutzerfreundliche Umgebung, in der zwei Datenbankdefinitionen verglichen und die Unterschiede aus der Quelle auf das Ziel angewendet werden können.

## <a name="features"></a>Features

* Vergleichen von Schemas von zwei DACPAC-Dateien oder -Datenbanken
* Anzeigen von Ergebnissen als Aktionen, die für das Ziel durchgeführt werden müssen, damit dieses der Quelle entspricht
* Selektives Ausschließen von in den Ergebnissen aufgeführten Aktionen
* Festlegen von Optionen, die den Bereich des Vergleichs steuern
* Anwenden von Änderungen auf das Ziel oder Generieren eines Skripts mit der gleichen Auswirkung
* Speichern des Vergleichs

![Schemavergleich: Beispielvergleich](media/schema-compare-extension/schema-compare.png)

## <a name="why-would-i-use-the-schema-compare-extension"></a>Warum sollte ich die Schemavergleicherweiterung verwenden?

Es kann mühsam sein, unterschiedliche Datenbankversionen manuell zu verwalten und zu synchronisieren. Mit der Schemavergleicherweiterung wird der Vergleichsprozess von Datenbanken vereinfacht, und Sie erhalten volle Kontrolle beim Synchronisieren dieser Datenbanken. Sie können nach bestimmten Unterschieden und Unterschiedkategorien filtern, bevor Sie die Änderungen anwenden. Die Schemavergleicherweiterung ist ein zuverlässiges Tool, mit dem Sie Zeit und Code sparen.

![Schemavergleich: Dialogfeld „Optionen“](media/schema-compare-extension/schema-compare-options.png)

## <a name="install-the-extension"></a>Installieren der Erweiterung

1. Klicken Sie auf das Symbol „Erweiterungen“, um die verfügbaren Erweiterungen anzuzeigen.

    ![Erweiterungs-Manager-Symbol](media/add-extensions/extension-manager-icon.png)

2. Suchen Sie nach der Erweiterung **Schemavergleich**, und wählen Sie sie aus, um die Details anzuzeigen. Wählen Sie **Installieren** aus, um die Erweiterung hinzuzufügen.

3. Klicken Sie nach der Installation auf **Erneut laden**, um die Erweiterung in Azure Data Studio zu aktivieren (nur bei der ersten Installation einer Erweiterung erforderlich).

## <a name="launch-a-schema-compare"></a>Starten des Schemavergleichs

1. **Klicken Sie mit der rechten Maustaste** auf eine Datenbank im Objekt-Explorer, und wählen Sie dann **Schemavergleich** aus, um das Dialogfeld „Schemavergleich“ zu öffnen. Die Datenbank, die Sie auswählen, wird als Quelldatenbank im Vergleich festgelegt.

    ![Menü zum Starten des Schemavergleichs](media/schema-compare-extension/schema-compare-launch.png)

2. Klicken Sie auf jeweiligen Auslassungspunkte (...) neben Quelle und Ziel, um die Quelle und das Ziel Ihres Schemavergleichs zu ändern, und wählen Sie dann „OK“ aus.

    ![Auswahl von Schemavergleichsquelle- und ziel](media/schema-compare-extension/schema-compare-select-source-target.png)

3. Wählen Sie die Schaltfläche **Optionen** in der Symbolleiste aus, um Ihren Vergleich anzupassen.

4. Wählen Sie **Vergleichen** aus, um die Ergebnisse des Vergleichs anzuzeigen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Schemavergleich finden Sie unter [Verwenden des Schemavergleichs zum Vergleichen verschiedener Datenbankdefinitionen](../../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md).
Probleme und Featureanforderungen können Sie [hier](https://github.com/microsoft/azuredatastudio/issues) mitteilen.