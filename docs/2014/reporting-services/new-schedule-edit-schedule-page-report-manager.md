---
title: 'Neuen Zeitplan: Zeitplan bearbeiten (Seite (Berichts-Manager) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 52a4d250-e185-4116-a29c-d809940a00fb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a43744243713fb522356814df8fa80a3e11197bd
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59967916"
---
# <a name="new-schedule-edit-schedule-page-report-manager"></a>Neuen Zeitplan: Bearbeiten Sie die Zeitplanseite (Berichts-Manager)
  Verwenden Sie die Seite Neuer Zeitplan oder Zeitplan bearbeiten zum Erstellen eines Zeitplans für einen Bericht. Zeitpläne werden im Zusammenhang mit Abonnements, zum Aktualisieren zwischengespeicherter Berichte und zum Erstellen von Momentaufnahmen als eigenständige Elemente oder im Berichtsverlauf verwendet.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Zeitpläne können nur für Berichte erstellt werden, die unbeaufsichtigt ausgeführt werden können. Für das Ausführen eines Berichts im unbeaufsichtigten Modus müssen Anmeldeinformationen für Berichtsdatenquellen in der Berichtsserver-Datenbank gespeichert sein. Weitere Informationen finden Sie unter [Data Sources – Seite "Eigenschaften" &#40;Berichts-Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).  
  
 Nicht alle Kombinationen der Häufigkeit können in einem einzelnen Zeitplan unterstützt werden. Wenn ein Bericht z. B. um 00:00 Uhr und um 16:00 Uhr an jedem Freitag ausgeführt werden soll, müssen Sie zwei Tageszeitpläne erstellen, in denen der Freitag als Ausführungstag angegeben ist. Der erste Zeitplan hat eine Startzeit von 00:00 Uhr, und für den zweiten ist eine Startzeit von 16:00 Uhr festgelegt.  
  
 Die Verarbeitung von Zeitplänen basiert auf der Ortszeit des Berichtsservers, auf dem der Zeitplan gehostet und verarbeitet wird.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgende Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-execution-properties-page-of-a-report"></a>So öffnen Sie die Seite Neuer Zeitplan oder Zeitplan bearbeiten über die Eigenschaftenseite 'Ausführung' eines Berichts  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie einen Zeitplan konfigurieren möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für das Modell geöffnet.  
  
4.  Wählen Sie die Registerkarte **Eigenschaften** aus.  
  
5.  Wählen Sie die Option **Diesen Bericht aus einer Berichtsausführungs-Momentaufnahme rendern**. Wählen Sie dann **Folgenden Zeitplan verwenden, um dem Berichtsverlauf Momentaufnahmen hinzuzufügen**und anschließend **Berichtsspezifischer Zeitplan**aus. Klicken Sie dann auf **Konfigurieren**.  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-history-properties-page-of-a-report"></a>So öffnen Sie die Seite 'Neuer Zeitplan' oder 'Zeitplan bearbeiten' über die Eigenschaftenseite 'Verlauf' eines Berichts  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie einen Zeitplan konfigurieren möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für das Modell geöffnet.  
  
4.  Wählen Sie die Registerkarte **Verlauf** .  
  
5.  Wählen Sie **Folgenden Zeitplan verwenden, um dem Berichtsverlauf Momentaufnahmen hinzuzufügen**und **Berichtsspezifischer Zeitplan**aus. Klicken Sie dann auf **Konfigurieren**.  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-subscriptions-page"></a>So öffnen Sie die Seite 'Neuer Zeitplan' oder 'Zeitplan bearbeiten' über die Seite 'Abonnements'  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie einen Zeitplan konfigurieren möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Führen Sie im Dropdownmenü folgende Aktionen aus:  
  
    -   Klicken Sie auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für den Bericht geöffnet. Wählen Sie dann die Registerkarte **Abonnements** aus.  
  
    -   Klicken Sie auf **Abonnieren**. Dadurch wird die Eigenschaftenseite **Abonnements** für den Bericht geöffnet.  
  
4.  Klicken Sie auf der Symbolleiste auf **Neues Abonnement** , oder wählen Sie ein vorhandenes Abonnement zur Bearbeitung aus.  
  
5.  Klicken Sie unter **Optionen für die Abonnementverarbeitung**auf **Neuer Zeitplan**.  
  
## <a name="options"></a>Optionen  
 **Details zum Zeitplan**  
 Wählen Sie Optionen aus, um den Zeitpunkt und die Häufigkeit der Berichtsausführung zu bestimmen. Die Optionen für die Häufigkeit sind überlagernd. Die erste Gruppe von Optionen gibt eine Kategorie der Häufigkeit an (Stunde, Tag, Woche usw.). Die zweite Gruppe von Optionen, die angezeigt wird, basiert auf der ersten Auswahl.  
  
-   Durch**Stunde** definieren Sie einen Zeitplan mit stündlicher Ausführung. Im Abschnitt **Anfangs- und Enddatum** können Sie den Tag angeben, an dem der Zeitplan ausgeführt werden soll.  
  
-   Durch**Tag** definieren Sie einen Zeitplan, der an den von Ihnen angegebenen Tagen zu einer bestimmten Uhrzeit (Stunde und Minute) ausgeführt wird. Sie können Tage auf folgende Weise angeben: Jede \< *Tag*>, an jedem Arbeitstag und alle \< *Anzahl*> Tag. Wenn eine Option ausgewählt ist, stehen die anderen nicht zur Verfügung, auch wenn es so aussieht, als seien die anderen Tage ebenfalls ausgewählt.  
  
-   Durch**Woche** definieren Sie einen Zeitplan, der zu der von Ihnen angegebenen Uhrzeit (Stunde und Minute) wöchentlich ausgeführt wird. Der Zeitabstand kann vollständige Wochen betragen (z. B. alle zwei Wochen) oder Tage innerhalb einer Woche.  
  
-   Durch**Monat** definieren Sie einen Zeitplan mit monatlicher Ausführung. Innerhalb eines Monats können Sie einen Tag auf der Grundlage eines Musters auswählen (z. B. den letzten Sonntag jeden Monats) oder spezifische Kalenderdaten angeben (z. B. den 1. und 15., um den ersten und fünfzehnten Tag jeden Monats anzugeben). Mithilfe von Kommas und Bindestrichen können Sie mehrere Tage und Bereiche angeben (Beispiel: 1, 5, 7-12, 21).  
  
-   Durch**Einmal** definieren Sie einen Zeitplan mit einmaliger Ausführung. Im Abschnitt **Anfangs- und Enddatum** können Sie den Tag angeben, an dem der Zeitplan ausgeführt werden soll. Dieser Zeitplan läuft unmittelbar nach seiner Verarbeitung ab.  
  
 **Start- und Enddatum**  
 Geben Sie das Anfangsdatum für den Beginn der Gültigkeit des Zeitplans und das Enddatum für den Ablauf des Zeitplans an.  
  
 Zeitpläne laufen ohne Benachrichtigung ab. Nach dem Enddatum können sie nicht mehr ausgeführt werden. Abgelaufene Zeitpläne werden nicht gelöscht. Zeitpläne können nur manuell gelöscht werden. Daher können Sie das Enddatum entsprechend ändern, wenn Sie den Zeitplan fortsetzen möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Erstellen, Ändern oder Löschen von Zeitplänen](subscriptions/create-modify-and-delete-schedules.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
