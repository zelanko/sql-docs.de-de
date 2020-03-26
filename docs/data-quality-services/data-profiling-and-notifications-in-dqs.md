---
title: Datenprofilerstellung und Benachrichtigungen in DQS
ms.date: 03/15/2020
ms.prod: sql
ms.reviewer: jroth
ms.technology: data-quality-services
ms.topic: conceptual
author: swinarko
ms.author: sawinark
ms.openlocfilehash: e0bd9585a48ee30368d145c79f8431e922801a9c
ms.sourcegitcommit: c30a2def43c86860aeec69d3e3029f2296544b13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/25/2020
ms.locfileid: "80243400"
---
# <a name="data-profiling-and-notifications-in-data-quality-services-dqs"></a>Datenprofil Erstellung und Benachrichtigungen in Data Quality Services (DQS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)](DQS) ist ein Datenprofilerstellungs-Dienst. DQS analysiert Daten aus einer Quelle und zeigt Statistiken zu den Daten in DQS-Aktivitäten an.

## <a name="attributes-goals-benefits"></a>Attribute, Ziele, Vorteile

### <a name="attributes-of-dqs"></a>Attribute von DQS

Die DQS-Profilerstellung weist die folgenden Attribute auf:

- Bietet automatisierte Messungen der Datenqualität.
- Ist in DQS-Wissensverwaltung und Data Quality-Projekte integriert.
- Ist dynamisch und anpassbar.

### <a name="goals-of-dqs"></a>DQS-Ziele

Die Profilerstellung mit DQS hat die folgenden zwei Hauptziele:

- , Um Sie durch Data Quality-Prozesse zu führen und ihre Entscheidungen zu unterstützen.
- Um die Effektivität der Prozesse zu bewerten.

### <a name="benefits-of-dqs"></a>Vorteile von DQS

Die DQS-Profilerstellung bietet die folgenden Vorteile:

- Bietet Einblicke in die Qualität der Quelldaten und hilft Ihnen, Probleme mit der Datenqualität zu identifizieren.

- Bewertet die Data Quality-Prozesse und führt Sie durch die folgenden Schritte:
  - Wissens Ermittlung
  - Datenbereinigung
  - Abgleichsrichtlinie
  - Übereinstimmende Arbeit

- Enthält die relevantesten Informationen zum relevantesten Zeitpunkt.

- Generiert Benachrichtigungen, die wichtige Statistiken oder Ereignisse hervorheben, die möglicherweise Aktionen rechtfertigen. DQS-Benachrichtigungen weisen häufig auf eine Bedingung hin und empfehlen Korrekturmaßnahmen.

Die DQS-Profilerstellung bietet Wissens Ermittlung, Datenbereinigung und Datenabgleich. DQS ist auch ein Datenanalyse Tool. Sie können eine Wissensdatenbank für die Analyse erstellen. Anschließend können Sie die Wissens Ermittlung mithilfe der Wissensdatenbank ausführen. Die Wissens Ermittlung verwendet Profil Erstellungs Statistiken, um zu bestimmen, ob die Wissensdatenbank Ihren Anforderungen für Ermittlung, Bereinigung und Abgleich entspricht.

## <a name="how-dqs-profiling-works"></a><a name="How"></a>Funktionsweise der DQS-Profilerstellung

Die DQS-Profilerstellung misst nicht die Qualität der Wissensdatenbank. Die Profilerstellung misst die Qualität der Quelldaten. Die Profilerstellung bietet Statistiken, die die Auswirkung der folgenden Maßnahmen angeben:

- Ihr spezifischer Vorgang in der Wissensverwaltung.
- Ein Data Quality-Projekt für die Quelldaten.

### <a name="activity-context"></a>Aktivitäts Kontext

Die Profilerstellung geschieht immer im Kontext der bestimmten Aktivität, die Sie ausführen. Sie können auf der Registerkarte Profilerstellung auf einem Bildschirm auf die Profil Erstellungs Daten klicken. Durch diesen Klick gelangen Sie nicht mehr von der Stufe der Aktivität, die Sie ausführen. Die Profil Erstellungs Tabelle wird in Echtzeit aufgefüllt, wenn der Prozess ausgeführt wird. Daher können Sie Data Quality-Aufgaben während ihrer Ausführung bewerten.

Sie können bestimmen, ob Quelldaten nach Bereinigung oder Deduplizierung besser sind und um wie viel besser sie sind.

### <a name="profiling-is-based-on-counts"></a>Profilerstellung basiert auf Zählungen

Alle Profil Erstellungs Nummern verweisen auf die Anzahl der Vorkommen bestimmter Werte. In vielen Fällen beziehen sich die Zahlen auf den Prozentsatz des Gesamtwerts. Die Eindeutigkeits Metrik ist eine Ausnahme. Eindeutigkeits Metriken verweisen auf die absolute Anzahl von Werten, unabhängig von der Anzahl der Vorkommen dieser Werte.

### <a name="knowledge-driven-solution"></a>Wissens gesteuerte Lösung

Die Profilerstellung ist Teil des wissensgesteuerten DQS-Lösung. Die Profilerstellung stellt Informationen zu einer Wissensdatenbank, einem Abgleich oder einem Daten Bereinigungs Prozess bereit. Die Informationen basieren auf der Zuordnung zwischen Datenquellen Feldern und Wissens Daten Bank Domänen. Die Profilerstellung wird erst ausgeführt, nachdem die Zuordnung fertiggestellt wurde. Während der Zuordnungsphase einer Aktivität wird keine Profilerstellung durchgeführt.

Die Profilerstellung wird immer an eine Aktivität angefügt. Der Profil Erstellungs Prozess wird für die Daten ausgeführt, die Domänen _zugeordnet_ sind, nicht für die Daten _in_ den Domänen.

Die Profilerstellung wird in die folgenden Schritte von Aktivitäten integriert:

- Die Schritte zum **ermitteln** und **Verwalten von Domänen Werten** der Wissens Ermittlungs Aktivität.

- Die **Schritte** zum Bereinigen und **Verwalten und Anzeigen von Ergebnissen** der Bereinigungs Aktivität.

- Die **abgleichsrichtlinie** und die Abgleichsergebnisse der abgleichsrichtlinien-Aktivität **Matching results**

- Die Abgleichs-und **Export** **Schritte der** abgleichsaktivität.

DQS stellt keine Profilerstellungsstatistiken für die Domänenverwaltungsaktivität bereit.

## <a name="profiling-data-by-activity"></a><a name="Activity"></a>Profil Erstellungs Daten nach Aktivität

Die DQS-Profilerstellung verwendet die folgenden standardmäßigen Data Quality-Dimensionen, um die Qualität der Daten darzustellen:

- Vollständigkeit: der Umfang, in dem Daten vorhanden sind.
- Genauigkeit: das Ausmaß, in dem Daten für den vorgesehenen Verwendungszweck verwendet werden können.
- Eindeutigkeit: das Ausmaß, in dem verschiedene Werte verschiedene Entitäten darstellen.

Standardmäßig werden NULL-Werte und leere Werte als fehlend betrachtet oder verringern den Vollständigkeits Prozentsatz. Sie können jedoch andere Werte definieren, die NULL-äquivalent sind. Diese Werte werden auch als fehlend betrachtet.

Die Profilerstellung stellt Ihnen die Statistiken bereit, die Sie benötigen, um die Prozesse zu bewerten. Die Statistiken müssen Sie allerdings interpretieren. Verstehen Sie, was Ihnen die Profilerstellung mitteilt, indem Sie sich die Statistiken spaltenweise ansehen.

### <a name="differing-sets-of-profiling-statistics"></a>Abweichende Sätze von Profil Erstellungs Statistiken

Die DQS-Aktivitäten verfügen über andere Sätze von Profilerstellungsstatistiken, nämliche folgende:

- Nur die Bereinigungsaktivität weist Profilerstellungsstatistiken für Genauigkeit (in Prozent nach Domäne) auf. Genauigkeit wird durch Gültigkeit, Konsistenz, Syntaxfehler und Domänenregeln beeinflusst.

- Nur die Bereinigungsaktivität weist Profilerstellungsstatistiken für richtig, korrigiert und vorgeschlagen in der Quelle sowie für korrigierte und vorgeschlagene Werte nach Domäne (Zahlen und Prozentwerte) auf.

- Die Bereinigungs und Wissensermittlungsaktivitäten weisen Profilerstellungsstatistiken für Gültigkeit (Reinigen nach Datensatz, Wissensermittlung nach Datensatz und Domäne) auf. Die Abgleichsrichtlinie und die Abgleichsaktivitäten weisen keine Statistiken für Gültigkeit auf.

- Profil Erstellungs Statistiken werden aus Gründen der Eindeutigkeit für die Quelle und die Domäne bereitgestellt. Diese Anweisung gilt für die folgenden Aktivitäten:
  - Wissens Ermittlung.
  - Abgleichsrichtlinie.
  - Indem.
  - Aber _nicht_ für die Bereinigungs Aktivität.

DQS bietet spezifische Profil Erstellungs Statistiken, die sich auf eine Aktivität beziehen. Weitere Informationen finden Sie in den Abschnitten zur **Profilerstellung** in den folgenden Themen:

- [Durchführen der Wissensermittlung](../data-quality-services/perform-knowledge-discovery.md)

- [Bereinigen von Daten mit DQS-&#40;interner&#41; wissen](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)

- [Erstellen einer Abgleichsrichtlinie](../data-quality-services/create-a-matching-policy.md)

- [Ausführen eines Abgleichsprojekts](../data-quality-services/run-a-matching-project.md)

## <a name="profiling-data-in-activity-monitoring"></a><a name="Monitoring"></a>Profil Erstellungs Daten bei der Aktivitäts Überwachung

Profil Erstellungs Informationen sind nicht nur auf den Aktivitätsseiten des Data Quality-Clients verfügbar, sondern auch in der Aktivitäts Überwachung. Die Informationen betreffen die Wissens Ermittlung, abgleichsrichtlinie, Abgleich und Bereinigungs Aktivitäten. Die Informationen sind auf den Aktivitätsseiten im Data Quality-Client und in der Aktivitäts Überwachung verfügbar.

Sie können alle folgenden Elemente an einem Ort anzeigen:

- Eigenschaften
- Verwandte Rechenprozesse von Aktivitäten
- Profil Erstellungs Informationen für jede Aktivität generiert

Sie wählen eine Aktivität in der Aktivitäts Tabelle aus, um die Profil Erstellungs Ergebnisse in der zweiten Tabelle anzuzeigen. Sie können die Profilerstellungsergebnisse auch exportieren.

Weitere Informationen finden Sie unter [DQS Administration](../data-quality-services/dqs-administration.md).

## <a name="notifications"></a><a name="Notifications"></a>Anbot

DQS generiert Benachrichtigungen, um anzugeben, wann Sie möglicherweise eine Aktion basierend auf profilierten Statistiken durchführen möchten. DQS verwendet Benachrichtigungen für wichtige Fakten zur Datenquelle. Diese Fakten zeigen die Effektivität der aktuellen Aktivität relativ zum Zweck, für den Sie ausgeführt wurde. Benachrichtigungen stellen Tipps und Empfehlungen bereit, die auf eine Bedingung hinweisen. Benachrichtigungen können auch empfehlen, wie Sie eine Wissens Ermittlung, Datenbereinigung oder Daten abgleichsaktivität verbessern können.

DQS sendet eine Benachrichtigung, wenn ein Problem erkannt wird, das für Sie von Bedeutung ist. Wenn z. b. Vollständigkeit und Genauigkeit 100% betragen, werden bei der Daten Bereinigungs Aktivität möglicherweise keine korrigierten oder vorgeschlagenen Werte erzeugt. DQS kann eine Benachrichtigung für diese Situation veröffentlichen. Diese Benachrichtigung würde darauf hindeuten, dass die Aktivität möglicherweise nicht erforderlich ist. Ob die Aktivität ausgeführt werden soll, bleibt die Entscheidung.

Eine Benachrichtigung wird von einer QuickInfo mit einem Ausrufezeichen auf der Registerkarte **Profilerstellung** angezeigt. die der Benachrichtigung zugeordneten Statistiken werden rot dargestellt, um die statistische Begründung für die Benachrichtigung anzugeben.

### <a name="disable-notifications"></a>Benachrichtigungen deaktivieren

Benachrichtigungen sind standardmäßig aktiviert. Sie können Benachrichtigungen jedoch auf der Data Quality-Client-Startseite deaktivieren. Verwenden Sie im Abschnitt **Verwaltung** die Registerkarte **Allgemeine Einstellungen** .

Wenn Benachrichtigungen deaktiviert sind, werden keine Quick Infos angezeigt, und Statistiken werden nicht rot gefärbt. Die Profilerstellung bleibt funktionsfähig, während Benachrichtigungen deaktiviert werden. Die Leistung kann durch das Deaktivieren von Benachrichtigungen nicht verbessert werden.

Informationen zu bestimmten Bedingungen, die Benachrichtigungen für eine Aktivität zugeordnet sind, finden Sie hier:

- [Durchführen der Wissensermittlung](../data-quality-services/perform-knowledge-discovery.md)

- [Bereinigen von Daten mit DQS-&#40;interner&#41; wissen](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)

- [Erstellen einer Abgleichsrichtlinie](../data-quality-services/create-a-matching-policy.md)

- [Ausführen eines Abgleichsprojekts](../data-quality-services/run-a-matching-project.md)

## <a name="related-tasks"></a>Related Tasks

| Taskbeschreibung | Thema |
| :--------------- | :---- |
| Beschreibt, wie Benachrichtigungen in DQS aktiviert und deaktiviert werden. | [Aktivieren oder Deaktivieren von Profilerstellungsbenachrichtigungen in DQS](../data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md) |
|||
