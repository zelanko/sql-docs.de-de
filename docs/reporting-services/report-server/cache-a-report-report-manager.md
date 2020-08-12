---
title: Zwischenspeichern eines Berichts (Berichts-Manager) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie den Ablauf eines zwischengespeicherten Berichts im Berichts-Manager planen. Das Zwischenspeichern ermöglicht ein schnelleres Anzeigen des Berichts, solange er zwischengespeichert ist.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- cached reports [Reporting Services]
- schedules [Reporting Services], report expiration
- expiration [Reporting Services]
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 67a423a34d0b641e15daf5828748d572e504e329
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547900"
---
# <a name="cache-a-report-report-manager"></a>Zwischenspeichern eines Berichts (Berichts-Manager)
  Eine Möglichkeit, die Leistung zu verbessern, ist die Konfiguration von Zwischenspeichereigenschaften für einen Bericht. Beim Zwischenspeichern eines Berichts wird eine Kopie des gerenderten Berichts für einen kurzen Zeitraum gespeichert. Der erste Benutzer, der den Bericht anfordert, muss warten, bis die gesamte Verarbeitung abgeschlossen ist, bevor er den Bericht anzeigen kann. Nachfolgende Benutzer, die den Bericht innerhalb des Zeitraums der Zwischenspeicherung anfordern, können ihn sofort anzeigen, da die Verarbeitung bereits durchgeführt wurde.  
  
 Es gibt Einschränkungen in Bezug auf die Berichtstypen, die Sie zwischenspeichern können. Ein Bericht kann z. B. nicht zwischengespeichert werden, wenn die Berichtsausgabe je nach Benutzeridentität variiert oder wenn Daten mithilfe des Sicherheitstokens des Benutzers abgerufen werden, der den Bericht anfordert. Weitere Informationen finden Sie unter [Zwischenspeichern von Berichten &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)bestand darin die einzige Möglichkeit, den Cache vorab zu laden.  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a>So planen Sie den Ablauf eines zwischengespeicherten Berichts  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896).  
  
2.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** . Navigieren Sie zum Bericht, für den Sie Zwischenspeichereigenschaften festlegen möchten, zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
4.  Klicken Sie im linken Bereich auf **Verarbeitungsoptionen**.  
  
5.  Wählen Sie auf der Seite die Option **Diesen Bericht immer mit den neuesten Daten ausführen**.  
  
6.  Wählen Sie eine der folgenden zwei Cacheoptionen aus, und konfigurieren Sie den Ablauf wie folgt:  
  
    -   Wenn die zwischengespeicherte Kopie nach einem bestimmten Zeitraum ablaufen soll, klicken Sie auf **Eine temporäre Kopie des Berichts zwischenspeichern. Diese Kopie soll nach der folgenden Anzahl von Minuten ablaufen**. Geben Sie die Anzahl von Minuten für den Berichtsablauf ein.  
  
    -   Wenn eine zwischengespeicherte Kopie nach einem bestimmten Zeitplan ablaufen soll, klicken Sie auf **Eine temporäre Kopie des Berichts zwischenspeichern. Diese Kopie soll gemäß dem folgenden Zeitplan ablaufen.** Klicken Sie auf **Konfigurieren**, oder wählen Sie einen freigegebenen Zeitplan für die Steuerung des Berichtsablaufs aus.  
  
7.  Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Berichtsverarbeitungseigenschaften](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Zwischenspeichern von Berichten &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)  
  
  
