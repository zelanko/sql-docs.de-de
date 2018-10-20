---
title: Aktivieren oder Deaktivieren der Sammlung von Verwendungsdaten und Absturzberichte für Azure Data Studio | Microsoft-Dokumentation
description: In diesem Artikel wird erläutert, wie Sie steuern, wenn die nutzungs- und Absturzberichten Berichtsdaten gesammelt und an Microsoft gesendet.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b0a5adf802ab07e05f1041b1385044e2d580db32
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356481"
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

## <a name="additional-resources"></a>Weitere Ressourcen
- [Arbeitsbereich und benutzereinstellungen](settings.md)
