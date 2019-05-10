---
title: Aktivieren Sie oder deaktivieren Sie die Sammlung von Verwendungsdaten und berichterstellung von Abstürzen
titleSuffix: Azure Data Studio
description: In diesem Artikel wird erläutert, wie Sie steuern, wenn die nutzungs- und Absturzberichten Berichtsdaten gesammelt und an Microsoft gesendet.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 7eeebe22f73815b053c0b9d1adfb53259732695f
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089535"
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
