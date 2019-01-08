---
title: Aktivieren Sie oder deaktivieren Sie die Sammlung von Verwendungsdaten und berichterstellung von Abstürzen
titleSuffix: Azure Data Studio
description: In diesem Artikel wird erläutert, wie Sie steuern, wenn die nutzungs- und Absturzberichten Berichtsdaten gesammelt und an Microsoft gesendet.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1f9dd29edf2474ab8db0e3dc7ad7dc2ff78016d1
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030104"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Aktivieren Sie oder deaktivieren Sie der Sammlung von Verwendungsdaten für [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Gewusst wie: Deaktivieren Sie die Telemetriedaten melden

[!INCLUDE[name-sos](../includes/name-sos-short.md)] erfasst Nutzungsdaten und sendet sie an Microsoft zur Verbesserung unserer Produkte und Dienste. Um mehr zu erfahren, lesen die [Datenschutzbestimmungen](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Wenn Sie keine Nutzungsdaten an Microsoft senden möchten, legen Sie die *telemetry.enableTelemetry* auf *"false"*.

Zum Unterdrücken von alle telemetrieereignisse aus [!INCLUDE[name-sos](../includes/name-sos-short.md)], von **Datei** > **Voreinstellungen** > **Einstellungen**, fügen Sie die folgende Option:

```json
    "telemetry.enableTelemetry": false
```

**Wichtiger Hinweis**: Diese Option erfordert einen Neustart des [!INCLUDE[name-sos](../includes/name-sos-short.md)] wirksam werden. 

## <a name="how-to-disable-crash-reporting"></a>Gewusst wie: Deaktivieren Sie die berichterstellung von Abstürzen

So deaktivieren Sie die berichterstellung von Abstürzen von **Datei** > **Voreinstellungen** > **Einstellungen**, fügen Sie die folgende Option:

```json
    "telemetry.enableCrashReporter": false
```

**Wichtiger Hinweis**: Diese Option erfordert einen Neustart des [!INCLUDE[name-sos](../includes/name-sos-short.md)] wirksam werden.

## <a name="additional-resources"></a>Zusätzliche Ressourcen
- [Arbeitsbereich und benutzereinstellungen](settings.md)
