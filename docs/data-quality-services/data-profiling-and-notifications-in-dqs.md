---
title: Datenprofilerstellung und Benachrichtigungen in DQS
ms.date: 04/01/2020
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a778bb5b-8e35-4a7b-b04a-ae2b46dec21b
author: swinarko
ms.author: sawinark
ms.openlocfilehash: af0464a307d77531c5d11624dc86a836ddf77711
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882549"
---
# <a name="data-profiling-and-notifications-in-dqs"></a>Datenprofilerstellung und Benachrichtigungen in DQS

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  Datenprofilerstellung in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ist der Prozess des Analysierens der Daten in einer vorhandenen Datenquelle und des Anzeigens von Statistiken zu den Daten in DQS-Aktivitäten. Sie versorgt Sie mit automatischen Messungen der Datenqualität. DQS-Profilerstellung wird in DQS-Wissensverwaltung und Data Quality-Projekte integriert. Es ist dynamisch und anpassbar. Die Profilerstellung hat zwei Hauptziele: erstens, Sie durch Data Quality-Prozesse zu führen und Ihre Entscheidungen zu unterstützen, und zweitens, die Effektivität der Prozesse zu bewerten. Der DQS-Profilerstellungsprozess hat die folgenden Vorteile:  
  
-   Die Profilerstellung stellt einen Einblick in die Qualität der Quelldaten bereit und hilft Ihnen, Data Quality-Probleme zu identifizieren.  
  
-   Die Profilerstellung bewertet die Effektivität von Data Quality-Prozessen und leitet Sie bei der Wissensermittlung, der Datenbereinigung, der Abgleichsrichtlinie und der Abgleichsarbeit.  
  
-   Die Profilerstellung gibt Ihnen die relevantesten Informationen zum relevantesten Zeitpunkt.  
  
-   Der Profil Erstellungs Prozess generiert Benachrichtigungen, die wichtige Statistiken oder Ereignisse hervorheben, die möglicherweise eine Aktion verdienen. In vielen Fällen geben DQS-Benachrichtigungen eine Bedingung an und empfehlen die Aktion, die Sie ergreifen können, um diese Bedingung zu beheben.  
  
 Die Profilerstellung ermöglicht es Ihnen, Data Quality Services nicht nur zur Wissensermittlung, Bereinigung und zum Abgleich zu verwenden, sondern auch als Analysetool. Möglicherweise möchten Sie eine Wissensdatenbank für die Analyse erstellen und die Wissensermittlung mithilfe dieser Wissensdatenbank ausführen, um aus den Profilerstellungsstatistiken zu bestimmen, ob die Wissensdatenbank Ihren Anforderungen für Ermittlung, Bereinigung und Abgleich gerecht wird.  
  
##  <a name="how-profiling-works"></a><a name="How"></a> Funktionsweise der Profilerstellung  
 Die Profilerstellung misst nicht die Qualität der Wissensdatenbank. Sie misst die Qualität der Quelldaten. Die Profilerstellung stellt Ihnen Statistiken zur Verfügung, die den Effekt des bestimmten Vorgangs angeben, den Sie in der Wissensverwaltung oder einem Data Quality-Projekt für Ihre Quelldaten durchführen. Die Profilerstellung erfolgt immer im Kontext der jeweiligen Aktivität, die Sie gerade durchgeführt haben. Sie können auf die Registerkarte Profilerstellung auf einem Bildschirm klicken, um Profil Erstellungs Daten anzuzeigen, ohne die Phase der Aktivität zu übernehmen. Die Profil Erstellungs Tabelle wird in Echtzeit aufgefüllt, während der Prozess ausgeführt wird, sodass Sie Data Quality-Aufgaben während ihrer Ausführung bewerten können. Sie können bestimmen, ob Quelldaten nach Bereinigung oder Deduplizierung besser sind und um wie viel besser sie sind.  
  
 Alle Profil Erstellungs Nummern verweisen auf die Anzahl der Vorkommen eines Werts und in vielen Fällen auf den Prozentsatz des Gesamtwerts, mit Ausnahme der Eindeutigkeits Metriken. Eindeutigkeitsmetrik verweist auf die absolute Anzahl von Werten, unabhängig davon, wie häufig diese Werte vorkommen.  
  
 Die Profilerstellung ist Teil des wissensgesteuerten DQS-Lösung. Sie stellt Informationen zu einer Wissensdatenbank, einem Abgleichs- oder einem Datenbereinigungsprozess basierend auf der Zuordnung zwischen Datenquellenfeldern und Wissensdatenbankdomänen bereit. Das Profil wird erst nach Abschluss der Zuordnung ausgeführt. während der Mapping-Phase einer Aktivität wird keine Profilerstellung durchgeführt. Die Profilerstellung wird immer an eine Aktivität angefügt. Der Profil Erstellungs Prozess wird für die Daten ausgeführt, die Domänen zugeordnet sind, nicht für die Daten in den Domänen. Es ist in die folgenden Schritte von Aktivitäten integriert:  
  
-   In die Schritte **Ermitteln** und **Domänenwerte verwalten** der Wissensermittlungsaktivität  
  
-   In die Schritte **Bereinigen** und **Ergebnisse verwalten und anzeigen** der Bereinigungsaktivität  
  
-   In die Schritte **Abgleichsrichtlinie** und **Abgleichsergebnisse** der Abgleichsrichtlinienaktivität  
  
-   In die Schritte **Abgleich** und **Exportieren** der Abgleichsaktivität  
  
 DQS stellt keine Profil Erstellungs Statistiken für die Domänen Verwaltungs Aktivität bereit.  
  
##  <a name="profiling-data-by-activity"></a><a name="Activity"></a>Profil Erstellungs Daten nach Aktivität  
 DQS-Profilerstellung verwendet standardmäßige Data Quality-Dimensionen, um die Qualität der Daten darzustellen: Vollständigkeit (das Ausmaß des Vorhandenseins von Daten), Genauigkeit (das Ausmaß, in dem Daten für den beabsichtigten Zweck verwendet werden können) und Eindeutigkeit (das Ausmaß, in dem verschiedene Werte verschiedene Entitäten darstellen). Standardmäßig werden NULL-Werte und leere Werte als fehlend betrachtet oder verringern den Vollständigkeits Prozentsatz. Sie können jedoch auch andere Werte so definieren, dass Sie NULL-äquivalent sind. in diesem Fall werden Sie auch als fehlend betrachtet.  
  
 Die Profilerstellung stellt Ihnen die Statistiken bereit, die Sie benötigen, um die Prozesse zu bewerten. Die Statistiken müssen Sie allerdings interpretieren. Verstehen Sie, was Ihnen die Profilerstellung mitteilt, indem Sie sich die Statistiken spaltenweise ansehen.  
  
 Die DQS-Aktivitäten verfügen über andere Sätze von Profilerstellungsstatistiken, nämliche folgende:  
  
-   Nur die Bereinigungsaktivität weist Profilerstellungsstatistiken für Genauigkeit (in Prozent nach Domäne) auf. Genauigkeit wird durch Gültigkeit, Konsistenz, Syntaxfehler und Domänenregeln beeinflusst.  
  
-   Nur die Bereinigungsaktivität weist Profilerstellungsstatistiken für richtig, korrigiert und vorgeschlagen in der Quelle sowie für korrigierte und vorgeschlagene Werte nach Domäne (Zahlen und Prozentwerte) auf.  
  
-   Die Bereinigungs und Wissensermittlungsaktivitäten weisen Profilerstellungsstatistiken für Gültigkeit (Reinigen nach Datensatz, Wissensermittlung nach Datensatz und Domäne) auf. Die abgleichsrichtlinie und die abgleichsaktivitäten weisen keine Statistiken für Gültigkeit auf  
  
-   Die Bereinigungs Aktivität weist keine Profil Erstellungs Statistiken für Eindeutigkeit auf Die Wissensermittlungs-, Abgleichsrichtlinien- und Abgleichsaktivitäten weisen Profilerstellungsstatistiken für Eindeutigkeit in Zahlen und Prozent für die Quelle und die Domäne auf.  
  
 Weitere Informationen zu den spezifischen Profil Erstellungs Statistiken für eine Aktivität finden Sie in den folgenden Artikeln in den Abschnitten zur Profilerstellung:  
  
-   [Durchführen der Wissensermittlung](../data-quality-services/perform-knowledge-discovery.md)  
  
-   [Bereinigen von Daten mit &#40;internem&#41; DQS-Wissen](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
-   [Erstellen einer Abgleichsrichtlinie](../data-quality-services/create-a-matching-policy.md)  
  
-   [Ausführen eines Abgleichsprojekts](../data-quality-services/run-a-matching-project.md)  
  
##  <a name="profiling-data-in-activity-monitoring"></a><a name="Monitoring"></a> Profilerstellungsdaten bei der Aktivitätsüberwachung  
 Profil Erstellungs Informationen für die Wissens Ermittlung, abgleichsrichtlinien-, Abgleichs-und Bereinigungs Aktivitäten sind nicht nur auf den Aktivitätsseiten im Data Quality-Client verfügbar, sondern auch in der Aktivitäts Überwachung. Die Aktivitätsüberwachung stellt Ihnen eine Übersicht über aktuelle und vergangene Aktivitäten bereit. Zusätzlich zu den Eigenschaften und verknüpften Berechnungsprozessen von Aktivitäten können Sie die für jede Aktivität an einem Speicherort generierten Profilerstellungsinformationen anzeigen. Sie wählen eine Aktivität in der Aktivitätstabelle aus, um Profilerstellungsergebnisse in einer Tabelle weiter unten anzuzeigen. Sie können die Profilerstellungsergebnisse auch exportieren. Weitere Informationen finden Sie unter [DQS Administration](../data-quality-services/dqs-administration.md).  
  
##  <a name="notifications"></a><a name="Notifications"></a> Benachrichtigungen  
 Zusätzlich zum Sammeln und Anzeigen von wichtigen Statistiken und wichtiger Metrik durch die Profilerstellung generiert DQS Benachrichtigungen (wenn aktiviert), um anzugeben, wann Sie auf Grundlage der angezeigten Profilerstellungsstatistiken eine Aktion ausführen können. DQS verwendet Benachrichtigungen, um wichtige Fakten zur Datenquelle hervorzuheben und die Effektivität der aktuellen Aktivität im Vergleich zum Zweck der Ausführung anzuzeigen. Benachrichtigungen stellen Tipps und Empfehlungen bereit, die eine Bedingung angeben und empfehlen, wie Sie eine Wissensermittlungs-, Datenbereinigungs- oder Datenabgleichsaktivität verbessern können.  
  
 Eine DQS-Benachrichtigung wird verwendet, um ein Problem auszulösen, das Sie möglicherweise interessiert, oder um ein potenzielles Problem zu behandeln. Ob Sie auf die Benachrichtigung reagieren, hängt davon ab, ob Sie für Ihre Zwecke relevant ist. Nehmen Sie zum Beispiel an, dass DQS eine Benachrichtigung ausgibt, wenn die Datenbereinigung keine korrigierten Werte oder vorgeschlagenen Werte erzeugt, während Vollständigkeit und Genauigkeit beide bei 100 % sind. Diese Benachrichtigung würde angeben, dass die Aktivität möglicherweise nicht ausgeführt werden muss. Ob Sie die Aktivität ausführen, ist jedoch Ihre Entscheidung.  
  
 Eine Benachrichtigung wird von einer QuickInfo mit einem Ausrufezeichen auf der Registerkarte **Profilerstellung** angegeben. der Benachrichtigung zugeordnete Statistiken werden rot dargestellt, um die statistische Begründung für die Benachrichtigung anzugeben.  
  
 Sie können Benachrichtigungen auf der Registerkarte **Allgemeine Einstellungen** des Abschnitts **Verwaltung** der Data Quality-Clientstartseite aktivieren (Standard) oder deaktivieren. Wenn die Benachrichtigung deaktiviert ist, werden keine Quick Infos angezeigt, und Statistiken werden nicht rot gefärbt. Durch das Deaktivieren von Benachrichtigungen entsteht keine deutliche Verbesserung der Leistung. Die Profilerstellung ist immer noch funktionstüchtig, wenn Sie Benachrichtigungen deaktivieren.  
  
 Informationen zu bestimmten Bedingungen, die Benachrichtigungen für eine Aktivität zugeordnet sind, finden Sie in den folgenden Artikeln:  
  
-   [Durchführen der Wissensermittlung](../data-quality-services/perform-knowledge-discovery.md)  
  
-   [Bereinigen von Daten mit &#40;internem&#41; DQS-Wissen](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)  
  
-   [Erstellen einer Abgleichsrichtlinie](../data-quality-services/create-a-matching-policy.md)  
  
-   [Ausführen eines Abgleichsprojekts](../data-quality-services/run-a-matching-project.md)  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Artikel|  
|----------------------|-----------|  
|Beschreibt, wie Benachrichtigungen in DQS aktiviert und deaktiviert werden.|[Aktivieren oder Deaktivieren von Profilerstellungsbenachrichtigungen in DQS](../data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md)|  
  
  
