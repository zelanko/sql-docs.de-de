---
title: 'Azure Data Studio: Problembehandlung'
description: Erfahren Sie, wie Sie Protokolle abrufen und Probleme in Azure Data Studio behandeln, was für Berichte zum Melden von Fehlern hilfreich ist.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.reviewer: hanqin, maghan
ms.custom: seodec18
ms.date: 11/24/2020
ms.openlocfilehash: 1d2483532589cd840f1120cfb0ac3273b41e0bb5
ms.sourcegitcommit: 2e7154475ba1f31d1aeebc8f48ac05846f793736
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95920210"
---
# <a name="azure-data-studio-troubleshooting"></a>Azure Data Studio: Problembehandlung
Azure Data Studio verfolgt Probleme und Featurevorschläge in einem [GitHub-Repository zur Problemverfolgung](https://github.com/Microsoft/azuredatastudio/issues) für das Repository `azuredatastudio` nach. 

## <a name="if-youve-experienced-any-issue"></a>Wenn Sie Probleme haben

Melden Sie Probleme bei der [GitHub-Problemverfolung](https://github.com/Microsoft/azuredatastudio/issues), und informieren Sie uns über alle Details, die bei der Reproduktion des Fehlers helfen. Fügen Sie sämtliche [Protokollinformationen](#how-to-set-the-logging-level) aus der Protokolldatei ein.

## <a name="writing-good-bug-reports-and-feature-requests"></a>Schreiben nützlicher Fehlerberichte und Featureanfragen

Protokollieren Sie ein einzelnes Issue pro Problem und Anfrage.

* Listen Sie nicht mehrere Fehler oder Featureanfragen im selben Issue auf.
* Sofern es sich nicht um die identische Eingabe handelt, fügen Sie Ihr Issue nicht als Kommentar zu einem vorhandenen Issue hinzu. Viele Probleme sehen ähnlich aus, haben aber unterschiedliche Ursachen.

Je mehr Informationen Sie bereitstellen können, desto wahrscheinlicher ist es, dass jemand das Problem erfolgreich reproduzieren und eine Lösung finden kann. 

Beziehen Sie folgende Informationen in jedes Issue ein:

* Version von Azure Data Studio
* Reproduzierbare Schritte (1... 2... 3...) und was Sie erwartet haben, im Vergleich zu dem, was Sie tatsächlich erlebt haben. 
* Bilder, Animationen oder ein Link zu einem Video: Bilder und Animationen veranschaulichen die reproduzierbaren Schritte, ersetzen diese jedoch nicht.
* Ein Codeausschnitt, der das Problem aufzeigt, oder ein Link zu einem Coderepository, das wir einfach auf unseren Computer herunterziehen können, um das Problem zu reproduzieren. 

> [!NOTE]
>  Da wir den Codeausschnitt kopieren und einfügen müssen, reicht es nicht aus, einen Codeausschnitt als Mediendatei (z. B. als GIF-Datei) einzufügen. 

* Fehler in der Konsole „Entwicklertools“ (Hilfe | Entwicklertools umschalten)

Beachten Sie Folgendes:

* Durchsuchen Sie das Repository des Issues, um festzustellen, ob ein Duplikat vorhanden ist. 
* Vereinfachen Sie Ihren Code rund um den Fehler, sodass wir diesen besser isolieren können. 

Machen Sie sich kein schlechtes Gewissen, wenn wir das Issue nicht reproduzieren können und um mehr Informationen bitten!

## <a name="how-to-set-the-logging-level"></a>Festlegen des Protokolliergrads

### <a name="azure-data-studio"></a>Azure Data Studio
Führen Sie den Befehl `Developer: Set Log Level...` aus, um den Protokolliergrad für die aktuelle Sitzung auszuwählen. Dieser Wert wird NICHT über mehrere Sitzungen beibehalten. Wenn Sie also Azure Data Studio neu starten, wird er auf den Standardgrad `Info` zurückgesetzt. 

Wenn Sie die Debugprotokollierung für den Start aktivieren möchten, müssen Sie den Protokolliergrad auf `Debug` festlegen und den Befehl `Developer: Reload Window` ausführen.

### <a name="mssql-built-in-extension"></a>MSSQL (integrierte Erweiterung)

Wenn die Benutzereinstellung `Mssql: Log Debug Info` auf TRUE festgelegt ist, werden Debugprotokollinformationen an den Ausgabekanal `MSSQL` gesendet.

Die Benutzereinstellung `Mssql: Tracing Level` dient zum Steuern der Ausführlichkeit der Protokollierung.

## <a name="debug-log-location"></a>Speicherort des Debugprotokolls
Führen Sie in Azure Data Studio den Befehl `Developer: Open Logs Folder` aus, um den Pfad zu den Protokollen zu öffnen. Es gibt viele verschiedene Arten von Protokolldateien, die dort abgelegt werden. Einige der am häufigsten verwendeten sind u. a.:

1. `renderer#.log` (Beispiel: renderer1.log): Diese Datei ist die Protokolldatei für den Hauptprozess.
1. `telemetry.log`:Wenn der Protokolliergrad auf `Trace` festgelegt ist, enthält diese Datei die von Azure Data Studio gesendeten Telemetrieereignisse.
1. `exthost#/exthost.log`: Protokolldatei für den Erweiterungshostprozess (nur für den Prozess selbst, nicht für die darin ausgeführten Erweiterungen).
1. `exthost#/Microsoft.mssql`:Protokolle für die MSSQL-Erweiterung, die einen Großteil der Kernlogik für MSSQL-bezogene Features enthält.
   * „sqltools.log“ ist das Protokoll des Diensts „SQL-Tools“.
1. `exthost#/output_logging_#######`: Diese Ordner enthalten die Meldungen, die in Azure Data Studio im Panel `Output` angezeigt werden. Jede Datei hat den Namen `#-<Channel Name>`, sodass z. B. der Ausgabekanal `Notebooks` in eine Datei mit dem Namen `3-Notebooks.log` ausgegeben werden kann.

Wenn Sie aufgefordert werden, Protokolle bereitzustellen, komprimieren Sie den gesamten Ordner im ZIP-Format, um sicherzustellen, dass die richtigen Protokolle eingeschlossen werden. 

## <a name="next-steps"></a>Nächste Schritte
- [Melden eines Problems](https://github.com/Microsoft/azuredatastudio/issues)
- [What is Azure Data Studio (Was ist Azure Data Studio?)](what-is-azure-data-studio.md)