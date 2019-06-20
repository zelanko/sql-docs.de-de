---
title: Erstellen, Ändern und Löschen von Zeitplänen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services]
- modifying schedules
- removing schedules
- shared schedules [Reporting Services], creating
- shared schedules [Reporting Services], modifying
- schedules [Reporting Services], deleting
- deleting schedules
- schedules [Reporting Services], creating
- schedules [Reporting Services], modifying
- shared schedules [Reporting Services], deleting
ms.assetid: 05da5f3d-9222-43a9-893b-aa10f0f690f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4e04f3f9a89fef9c00312ae1622f74fc0a279314
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66100881"
---
# <a name="create-modify-and-delete-schedules"></a>Create, Modify, and Delete Schedules
  In diesem Hilfethema erhalten Sie Informationen zum Erstellen, Ändern und Löschen von Zeitplänen.  
  
 In diesem Thema:  
  
-   [Übersicht über das Verwalten von freigegebenen Zeitplänen](#bkmk_overview)  
  
-   [Erstellen und Verwalten von freigegebenen Zeitplänen (SharePoint-Modus)](#bkmk_sharepoint)  
  
-   [Erstellen und Verwalten von freigegebenen Zeitplänen (einheitlicher Modus)](#bkmk_native)  
  
##  <a name="bkmk_overview"></a> Übersicht über das Verwalten von freigegebenen Zeitplänen  
 Freigegebene Zeitpläne für den einheitlichen Modus werden auf der Seite Zeitpläne des Berichts-Managers oder im Ordner Freigegebene Zeitpläne in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]verwaltet. Verwenden Sie für den SharePoint-Modus die Verwaltungsseiten für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung.  
  
 Sie können alle freigegebenen Zeitpläne anzeigen, die für den Berichtsserver definiert sind, Zeitpläne anhalten und fortsetzen (nur für Berichts-Manager) sowie Zeitpläne zum Ändern oder Löschen auswählen. Auf der Seite "Freigegebene Zeitpläne" sind die folgenden Informationen zum Status jedes Zeitplans zusammengefasst: Häufigkeit, Besitzer, Ablaufzeitpunkt und Status.  
  
 Auf folgende Weise können Sie feststellen, ob ein freigegebener Zeitplan aktiv verwendet wird:  
  
-   Überprüfen der Werte in den Feldern "Letzte Ausführung", "Nächste Ausführung" und "Status" auf der Seite "Freigegebene Zeitpläne". Wenn ein Zeitplan nicht mehr ausgeführt wird, weil er abgelaufen ist, wird das Ablaufdatum im Feld Status angezeigt.  
  
-   Anzeigen der Seite "Berichte" eines bestimmten freigegebenen Zeitplans. Auf dieser Seite werden alle Berichte und freigegebenen Datasets aufgeführt, die den freigegebenen Zeitplan verwenden.  
  
-   Anzeigen der Protokolldateien oder Ablaufverfolgungsprotokolle der Berichtsausführung, um zu ermitteln, ob Berichte zu den im Zeitplan angegebenen Zeiten ausgeführt wurden. Weitere Informationen finden Sie unter [Reporting Services-Protokolldateien und Quellen](../report-server/reporting-services-log-files-and-sources.md).  
  
##  <a name="bkmk_sharepoint"></a> Erstellen und Verwalten von freigegebenen Zeitplänen (SharePoint-Modus)  
 Bei einem freigegebenen Zeitplan handelt es sich um einen Zeitplan für verschiedene Zwecke, der sofort verwendbare Zeitplaninformationen zu einer beliebigen Anzahl von Berichten oder Abonnements bietet. Einen freigegebenen Zeitplan erstellen Sie einmal und verweisen dann in einem Abonnement oder auf einer Eigenschaftenseite darauf, wenn Sie Zeitplaninformationen benötigen. Freigegebene Zeitpläne können zentral verwaltet, angehalten und fortgesetzt werden. Einen benutzerdefinierten Zeitplan müssen Sie dagegen manuell bearbeiten, um zu verhindern, dass ein Bericht oder ein Abonnement ausgeführt wird.  
  
 Sie müssen ein Websiteadministrator sein, um freigegebene Zeitpläne auf einer SharePoint-Website erstellen, ändern oder löschen zu können.  
  
 Sie können einen bestimmten Zeitplan an seinem beschreibenden Namen identifizieren. Wenn kein Name angegeben ist, wird ein Standardname erstellt, der auf Fakten zum Zeitplan (z. B. sein Serienmuster oder Datum und Uhrzeit der Ausführung) basiert.  
  
> [!NOTE]  
>  Die Erstellung freigegebener Zeitpläne erfordert den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst.  
  
### <a name="create-shared-schedules-sharepoint"></a>Erstellen von freigegebenen Zeitplänen (SharePoint)  
  
##### <a name="to-create-shared-schedules"></a>So erstellen Sie freigegebene Zeitpläne  
  
1.  Klicken Sie auf **Websiteaktionen**.  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie im Abschnitt **Reporting Services**auf Freigegebene Zeitpläne verwalten.  
  
4.  Klicken Sie auf **Zeitplan hinzufügen** , um die Seite Zeitplaneigenschaften zu öffnen.  
  
5.  Geben Sie einen beschreibenden Namen für den Zeitplan ein. Auf den Anwendungsseiten, die für das Arbeiten mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichten verwendet werden, wird dieser Name in Dropdownlisten auf Seiten für Zeitplandefinitionen auf der gesamten Website angezeigt. Vermeiden Sie lange Namen, die schwer lesbar sind. Folgen Sie einer Benennungskonvention, bei der die meisten Beschreibungsinformationen an den Anfang des Namens gestellt werden.  
  
6.  Wählen Sie eine Häufigkeit aus. In Abhängigkeit von der von Ihnen ausgewählten Häufigkeit werden auf der Seite möglicherweise unterschiedliche Zeitplanoptionen angezeigt, mit denen die entsprechende Häufigkeit unterstützt wird. Wenn Sie beispielsweise **Monat**auswählen, werden alle Monatsnamen auf der Seite angezeigt.  
  
7.  Definieren Sie den Zeitplan. Nicht alle Zeitplankombinationen können in einem einzelnen Zeitplan unterstützt werden.  
  
8.  Legen Sie ein Start- und Enddatum fest.  
  
9. Klicken Sie auf **OK**.  
  
### <a name="delete-shared-schedules-sharepoint"></a>Löschen von freigegebenen Zeitplänen (SharePoint)  
 Alle Zeitpläne, ob freigegeben oder berichtsspezifisch, müssen manuell gelöscht werden. Wenn Sie einen freigegebenen Zeitplan löschen, der gerade verwendet wird, werden allen Verweise auf ihn durch benutzerdefinierte Zeitpläne ohne Angabe ersetzt (d. h. durch einen benutzerdefinierten Bericht, für den keine Datums- oder Uhrzeitinformationen verfügbar sind).  
  
 Das Löschen eines Zeitplans und das Ablaufen eines Zeitplans sind zwei unterschiedliche Dinge. Mithilfe eines Ablaufzeitpunktes wird ein Zeitplan beendet, aber nicht gelöscht. Da Zeitpläne zum Automatisieren von Berichtsservervorgängen verwendet werden, werden sie nie automatisch gelöscht. Abgelaufene Zeitpläne stellen Berichtsserveradministratoren Hinweise bereit, weshalb ein automatisierter Prozess plötzlich beendet wurde. Ohne den abgelaufenen Zeitplan könnte der Berichtsserveradministrator eine falsche Diagnose des Problems stellen oder unnötig Zeit mit der Problembehandlung eines voll funktionsfähigen Prozesses verschwenden.  
  
 Ein abgelaufener benutzerdefinierter Zeitplan bleibt weiterhin mit dem Bericht verbunden. Durch Überprüfen des Enddatums können Sie ermitteln, ob ein Zeitplan abgelaufen ist. Ein abgelaufener freigegebener Zeitplan verbleibt in der Liste mit freigegebenen Zeitplänen. Das Feld Status zeigt an, ob der Zeitplan abgelaufen ist. Sie können den Zeitplan wiederherstellen, indem Sie das Enddatum des Zeitplans verlängern, oder Sie löschen den Zeitplanverweis, wenn er nicht mehr benötigt wird.  
  
##### <a name="to-delete-a-shared-schedule"></a>So löschen Sie einen freigegebenen Zeitplan  
  
1.  Klicken Sie auf **Websiteaktionen**.  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie im Abschnitt **Reporting Services**auf Freigegebene Zeitpläne verwalten.  
  
4.  Wählen Sie den Zeitplan aus, und klicken Sie auf **Löschen**.  
  
##  <a name="bkmk_native"></a> Erstellen und Verwalten von freigegebenen Zeitplänen (einheitlicher Modus)  
 Freigegebene Zeitpläne müssen mit der Zeitplanseite des Berichts-Managers oder dem Ordner mit den freigegebenen Zeitplänen in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]manuell gelöscht werden. Wenn Sie einen freigegebenen Zeitplan löschen, der verwendet wird, werden alle Verweise darauf durch berichtsspezifische Zeitpläne ersetzt.  
  
 Berichts- und abonnementspezifische Zeitpläne werden beim Löschen eines Berichts oder Abonnements oder bei der Auswahl einer anderen Vorgehensweise zum Ausführen des Berichts bzw. des Abonnements gelöscht. So wird beispielsweise mit **Diesen Bericht immer mit den neuesten Daten ausführen** ein berichtsspezifischer Zeitplan gelöscht, den Sie für die Ausführung eines Berichts als Berichtsausführungs-Momentaufnahme erstellt haben.  
  
 Das Löschen eines Zeitplans und das Ablaufen eines Zeitplans sind zwei unterschiedliche Dinge. Mithilfe eines Ablaufzeitpunktes wird ein Zeitplan beendet, aber nicht gelöscht. Da Zeitpläne für die Automatisierung vieler Funktionen verwendet werden, werden sie niemals automatisch gelöscht. Abgelaufene Zeitpläne stellen Berichtsserveradministratoren Hinweise bereit, weshalb ein automatisierter Prozess plötzlich beendet wurde. Ohne den abgelaufenen Zeitplan könnte der Berichtsserveradministrator eine falsche Diagnose des Problems stellen oder unnötig Zeit mit der Problembehandlung eines voll funktionsfähigen Prozesses verschwenden.  
  
 Ein abgelaufener berichtsspezifischer Zeitplan bleibt weiterhin mit dem Bericht verbunden. Durch Überprüfen des Enddatums können Sie ermitteln, ob ein Zeitplan abgelaufen ist. Ein abgelaufener freigegebener Zeitplan verbleibt in der Liste Freigegebene Zeitpläne. Das Feld Status zeigt an, ob der Zeitplan abgelaufen ist. Sie können den Zeitplan wiederherstellen, indem Sie das Enddatum des Zeitplans verlängern, oder Sie löschen den Zeitplanverweis, wenn er nicht mehr benötigt wird.  
  
### <a name="create-delete-or-modify-a-shared-schedule-report-manager"></a>Erstellen, Löschen oder Ändern eines freigegebenen Zeitplans (Berichts-Manager)  
 Beim Erstellen und Ändern eines Zeitplans werden Optionen festgelegt, die bestimmen, wann der Zeitplan ausgeführt wird.  
  
-   Freigegebene Zeitpläne werden als separate Elemente erstellt. Auf die erstellten freigegebenen Zeitpläne verweisen Sie beim Definieren eines Abonnements oder eines anderen geplanten Vorgangs.  
  
-   Berichtsspezifische Zeitpläne werden erstellt, wenn Sie ein Abonnement definieren oder Eigenschaften zur Berichtsausführung festlegen. Das Eingeben der Zeitplaninformationen gehört zum Definieren eines Abonnements oder zum Festlegen von Eigenschaften. Zum Definieren eines berichtsspezifischen Zeitplans öffnen Sie den Bericht oder das Abonnement, der bzw. das diesen verwendet.  
  
 Ein freigegebener Zeitplan enthält Informationen zum Zeitplan und zu Wiederholungen, die von einer beliebigen Anzahl veröffentlichter Berichte und Abonnements verwendet werden können, die auf einem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver ausgeführt werden. Werden zahlreiche Berichte und Abonnements gleichzeitig ausgeführt, können Sie für diese Aufträge einen freigegebenen Zeitplan erstellen. Soll zu einem späteren Zeitpunkt das Wiederholungsmuster oder das Enddatum geändert werden, können Sie diese Änderung für alle Berichte und Abonnements an einer Stelle vornehmen.  
  
 Freigegebene Zeitpläne sind leichter zu verwalten und ermöglichen Ihnen eine größere Flexibilität in der Verwaltung geplanter Vorgänge. So besteht beispielsweise die Möglichkeit, freigegebene Zeitpläne zu beenden und fortzusetzen. Wenn Sie der Ansicht sind, dass zu viele geplante Vorgänge gleichzeitig ausgeführt werden, können Sie mehrere freigegebene Zeitpläne erstellen, die zu verschiedenen Zeitpunkten ausgeführt werden, und anschließend die Zeitplaninformationen entsprechend der Verarbeitungslast auf dem Berichtsserver anpassen.  
  
 Einen Zeitplan können Sie jederzeit erstellen oder ändern. Wenn jedoch ein Zeitplan vor Abschluss Ihrer Änderungen ausgeführt wird, wird die vorherige Version des Zeitplans verwendet. Der geänderte Zeitplan wird erst nach dem Speichern wirksam.  
  
 Wenn Sie einen freigegebenen Zeitplan ändern, können Sie ihn anhalten, bevor Sie Änderungen daran vornehmen. Die Änderungen werden wirksam, wenn Sie den Zeitplan fortsetzen.  
  
##### <a name="to-create-or-modify-a-shared-schedule-report-manager"></a>So erstellen oder ändern Sie einen freigegebenen Zeitplan (Berichts-Manager)  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Klicken Sie im Berichts-Manager auf der globalen Symbolleiste auf **Siteeinstellungen**.  
  
3.  Klicken Sie auf **Zeitpläne**.  
  
4.  Klicken Sie auf **Neuer Zeitplan**. Klicken Sie zum Ändern eines vorhandenen Zeitplans auf den Namen des Zeitplans.  
  
5.  Geben Sie einen beschreibenden Namen für den Zeitplan ein.  
  
6.  Wählen Sie **Stunde**, **Tag**, **Woche**oder **Monat**aus. Klicken Sie auf **Einmal** , um einen einmaligen Zeitplan zu erstellen. Wenn Sie die Basis Ihres Zeitplans angeben, werden zusätzliche Optionen angezeigt.  
  
7.  Wählen Sie optional ein Datum aus, an dem der Zeitplan starten soll. Der Standardwert ist der aktuelle Tag. Sie können den Startzeitpunkt des Zeitplans verschieben, indem Sie ein späteres Datum auswählen.  
  
8.  Wählen Sie optional ein Datum aus, an dem der Zeitplan enden soll. An diesem Datum wird die Ausführung des Zeitplans angehalten, der Zeitplan wird jedoch nicht gelöscht.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-report-manager"></a>So löschen Sie einen freigegebenen Zeitplan (Berichts-Manager)  
  
1.  Klicken Sie im Berichts-Manager auf der globalen Symbolleiste auf **Siteeinstellungen**.  
  
    > [!NOTE]  
    >  Falls die Option **Siteeinstellungen** nicht verfügbar ist, haben Sie keine Zugriffsberechtigung für die Siteeinstellungen.  
  
2.  Klicken Sie auf der Seite im Bereich **Sonstige** auf **Freigegebene Zeitpläne verwalten**.  
  
3.  Aktivieren Sie das Kontrollkästchen neben dem zu löschenden Zeitplan, und klicken Sie dann auf **Löschen**.  
  
 Wenn Sie einen freigegebenen Zeitplan löschen, der von mehreren Berichten und Abonnements verwendet wird, erstellt der Berichtsserver für Berichte und Abonnements, die vorher den freigegebenen Zeitplan verwendet haben, eigene Zeitpläne. Jeder dieser neuen Zeitpläne enthält das Datum, die Zeit und die Wiederholungsoption, die in dem freigegebenen Zeitplan angegeben wurden. Beachten Sie, dass [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] keine zentrale Verwaltung für einzelne Zeitpläne bereitstellt. Wenn Sie einen freigegebenen Zeitplan löschen, müssen Sie jetzt die Zeitplaninformationen für jedes einzelne Element verwalten.  
  
 Wenn Sie nicht sicher sind, ob ein freigegebener Zeitplan verwendet wird, sollten Sie diesen ggf. stattdessen in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] löschen. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] bietet die gleichen Verwaltungsfunktionen für freigegebene Zeitpläne wie der Berichts-Manager, verfügt aber zusätzlich über eine Berichtsseite mit dem Namen jedes Bericht, der den Zeitplan verwendet.  
  
### <a name="create-delete-or-modify-a-shared-schedule-management-studio"></a>Erstellen, Löschen oder Ändern eines freigegebenen Zeitplans (Management Studio)  
 Ein freigegebener Zeitplan enthält Informationen zum Zeitplan und zu Wiederholungen, die von einer beliebigen Anzahl veröffentlichter Berichte und Abonnements verwendet werden können, die auf einem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver ausgeführt werden. Werden zahlreiche Berichte und Abonnements gleichzeitig ausgeführt, können Sie für diese Aufträge einen freigegebenen Zeitplan erstellen. Soll zu einem späteren Zeitpunkt das Wiederholungsmuster oder das Enddatum geändert werden, können Sie diese Änderung für alle Berichte und Abonnements an einer Stelle vornehmen.  
  
 Freigegebene Zeitpläne sind leichter zu verwalten und ermöglichen Ihnen eine größere Flexibilität in der Verwaltung geplanter Vorgänge. So besteht beispielsweise die Möglichkeit, freigegebene Zeitpläne zu beenden und fortzusetzen. Wenn Sie der Ansicht sind, dass zu viele geplante Vorgänge gleichzeitig ausgeführt werden, können Sie mehrere freigegebene Zeitpläne erstellen, die zu verschiedenen Zeitpunkten ausgeführt werden, und anschließend die Zeitplaninformationen entsprechend der Verarbeitungslast auf dem Berichtsserver anpassen.  
  
##### <a name="to-create-or-modify-a-shared-schedule-management-studio"></a>So erstellen oder ändern Sie einen freigegebenen Zeitplan (Management Studio)  
  
1.  Rufen Sie SQL Server Management Studio auf, und stellen Sie eine Verbindung mit einer Berichtsserverinstanz her.  
  
2.  Erweitern Sie im Objekt-Explorer einen Berichtsserverknoten.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner Freigegebene Zeitpläne, und klicken Sie dann auf **Neuer Zeitplan**. Die Seite Allgemein im Dialogfeld **Neuer freigegebener Zeitplan** wird angezeigt.  
  
     Erweitern Sie zum Ändern eines vorhandenen freigegebenen Zeitplans den Ordner „Freigegebene Zeitpläne“, klicken Sie mit der rechten Maustaste auf den gewünschten Zeitplan, und klicken Sie anschließend auf **Eigenschaften**.  
  
4.  Geben Sie einen beschreibenden Namen für den Zeitplan ein.  
  
5.  Wählen Sie optional ein Datum aus, an dem der Zeitplan starten soll. Der Standardwert ist der aktuelle Tag.  
  
6.  Wählen Sie optional ein Datum aus, an dem der Zeitplan enden soll. An diesem Datum wird die Ausführung des Zeitplans angehalten, der Zeitplan wird jedoch nicht gelöscht.  
  
7.  Sie können Wiederholungen des Zeitplans konfigurieren, indem Sie **Stunde**, **Tag**, **Woche**oder **Monat**auswählen. Es werden zusätzliche Optionen angezeigt. Verwenden Sie diese Zusatzoptionen, um die Häufigkeit der Zeitplanausführung auf der Grundlage der von Ihnen bevorzugten Angabe für Stunde, Tag, Woche oder Monat zu konfigurieren.  
  
     Oder geben Sie einen einmaligen (nicht wiederkehrenden) Zeitplan an, indem Sie **Einmal**auswählen und anschließend eine **Startzeit**angeben.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-management-studio"></a>So löschen Sie einen freigegebenen Zeitplan (Management Studio)  
  
1.  Erweitern Sie im Objekt-Explorer einen Berichtsserverknoten.  
  
2.  Erweitern Sie den Ordner Freigegebene Zeitpläne, klicken Sie mit der rechten Maustaste auf den zu löschenden Zeitplan, und klicken Sie dann auf **Löschen**. Das Dialogfeld **Katalogelemente löschen** wird angezeigt.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 Wenn Sie einen freigegebenen Zeitplan löschen, der von mehreren Berichten und Abonnements verwendet wird, erstellt der Berichtsserver für Berichte und Abonnements, die vorher den freigegebenen Zeitplan verwendet haben, eigene Zeitpläne. Jeder dieser neuen Zeitpläne enthält das Datum, die Zeit und die Wiederholungsoption, die in dem freigegebenen Zeitplan angegeben wurden. Beachten Sie, dass [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] keine zentrale Verwaltung für einzelne Zeitpläne bereitstellt. Wenn Sie einen freigegebenen Zeitplan löschen, müssen Sie jetzt die Zeitplaninformationen für jedes einzelne Element verwalten. Ermitteln Sie vor dem Löschen eines freigegebenen Zeitplans mit der [Seite Berichte](../tools/schedule-properties-reports-page.md) , welche Berichte derzeit mit einem freigegebenen Zeitplan arbeiten.  
  
## <a name="see-also"></a>Siehe auch  
 [Schedules](schedules.md)   
 [Anhalten und Fortsetzen von freigegebenen Zeitplänen](pause-and-resume-shared-schedules.md)   
 [Zwischenspeichern eines Berichts &#40;Berichts-Manager&#41;](../report-server/cache-a-report-report-manager.md)   
 [Hinzufügen einer Momentaufnahme zum Berichtsverlauf &#40;Berichts-Manager&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md)  
  
  
