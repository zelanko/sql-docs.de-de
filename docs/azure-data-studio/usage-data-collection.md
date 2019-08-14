---
title: Aktivieren oder Deaktivieren des Sammelns von Nutzungsdaten und des Erstellens von Absturzberichten
titleSuffix: Azure Data Studio
description: In diesem Artikel ist erläutert, wie Sie steuern, ob Nutzungs- und Absturzdaten gesammelt und an Microsoft gesendet werden.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 71ed86e9ad076a41099eaf4e56fe67a25b5f2c21
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958949"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Aktivieren oder Deaktivieren des Sammelns von Nutzungsdaten für [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>So deaktivieren Sie die Erstellung von Telemetrieberichten

[!INCLUDE[name-sos](../includes/name-sos-short.md)] sammelt Nutzungsdaten und sendet diese an Microsoft, damit wir unsere Produkte und Dienste verbessern können. Um mehr zu erfahren, lesen Sie die [Datenschutzerklärung](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Wenn Sie keine Nutzungsdaten an Microsoft senden möchten, legen Sie die Einstellung *telemetry.enableTelemetry* auf *false* fest.

Sollen alle Telemetrieereignisse von [!INCLUDE[name-sos](../includes/name-sos-short.md)] unterdrückt werden, fügen Sie über **Datei** > **Einstellungen** > **Einstellungen** die folgende Option hinzu:

```json
    "telemetry.enableTelemetry": false
```

**Wichtiger Hinweis**: Damit diese Option wirksam wird, ist ein Neustart von [!INCLUDE[name-sos](../includes/name-sos-short.md)] erforderlich. 

## <a name="how-to-disable-crash-reporting"></a>So deaktivieren Sie die Erstellung von Absturzberichten

Um die Erstellung von Absturzberichten zu deaktivieren, fügen Sie über **Datei** > **Einstellungen** > **Einstellungen** die folgende Option hinzu:

```json
    "telemetry.enableCrashReporter": false
```

**Wichtiger Hinweis**: Damit diese Option wirksam wird, ist ein Neustart von [!INCLUDE[name-sos](../includes/name-sos-short.md)] erforderlich.

## <a name="additional-resources"></a>Weitere Ressourcen
- [Arbeitsbereich- und Benutzereinstellungen](settings.md)
