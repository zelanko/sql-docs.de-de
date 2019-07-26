---
title: Hinzufügen einer Momentaufnahme zum Berichts Verlauf-Reporting Services | Microsoft-Dokumentation
ms.prod: reporting-services
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 06/26/2019
ms.openlocfilehash: 2ada64f14c3564bd1e6c9846f890fdd8b287cb6f
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68251929"
---
# <a name="add-a-snapshot-to-report-history"></a>Hinzufügen einer Momentaufnahme zum Berichtsverlauf

Der Berichtsverlauf stellt eine Auflistung von Berichtsmomentaufnahmen dar, die Sie im Laufe der Zeit erstellen. Ein Berichtsmomentaufnahme ist ein Bericht, der Layoutinformationen und Abfrageergebnisse enthält, die zu einem bestimmten Zeitpunkt abgerufen wurden. Während für bedarfsgesteuerte Berichte aktuelle Abfrageergebnisse abgerufen werden, wenn Sie den Bericht auswählen, werden Berichtsmomentaufnahmen anhand eines Zeitplans verarbeitet und anschließend auf einem Berichtsserver gespeichert. Wenn Sie eine Berichtsmomentaufnahme zum Anzeigen auswählen, ruft der Berichtsserver den gespeicherten Bericht aus der Berichtsserver-Datenbank ab und zeigt die Daten und das Layout an, die zum Zeitpunkt der Momentaufnahmeerstellung für den Bericht aktuell waren.  
  
Berichtsmomentaufnahmen werden in keinem speziellen Renderingformat gespeichert. Stattdessen werden Berichtsmomentaufnahmen erst dann in einem endgültigen Anzeigeformat (wie HTML) gerendert, wenn sie von einem Benutzer oder einer Anwendung angefordert werden. Durch das verzögerte Rendering wird eine Momentaufnahme portabel. Der Bericht kann jeweils im richtigen Format für das anfordernde Gerät oder den anfordernden Webbrowser gerendert werden.  
  
## <a name="to-manually-add-snapshots-to-report-history"></a>So fügen Sie dem Berichtsverlauf manuell Momentaufnahmen hinzu
  
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

1. Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und zeigen Sie auf das Element, dessen Verlauf angezeigt werden soll, und klicken Sie auf den Dropdownpfeil.
  
2. Klicken Sie im Dropdownmenü auf **Berichtsverlauf anzeigen**.  
  
3. Klicken Sie auf **Neue Momentaufnahme**. In der Spalte **Ausführungszeitpunkt** wird eine neue Momentaufnahme erstellt.  
    > [!NOTE]
    > Um das Erstellen von Momentaufnahmen zu ermöglichen, muss der Administrator den Berichts Verlauf so konfigurieren, **dass der Verlauf manuell erstellt werden kann**. Weitere Informationen finden Sie unter [Einschränken des Berichtsverlaufs &#40;Berichts-Manager&#41;](../reports/limit-report-history-report-manager.md).

4. Klicken Sie auf **Anwenden**.
  
## <a name="to-automatically-add-all-snapshots-to-report-history"></a>So fügen Sie dem Berichtsverlauf automatisch alle Momentaufnahmen hinzu  
  
1. Für einen Bericht, der bereits für die Ausführung als Berichtsausführungs-Momentaufnahme konfiguriert ist, können Sie zusätzliche Eigenschaften festlegen, um bei jeder Aktualisierung der Momentaufnahme eine Kopie der Momentaufnahme im Berichtsverlauf zu speichern.  
  
2. Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , zeigen Sie auf das Element, dessen Verlauf angezeigt werden soll, und klicken Sie auf den Dropdownpfeil.  
  
3. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
4. Klicken Sie auf **Momentaufnahmeoptionen**.  
  
5. Aktivieren Sie das Kontrollkästchen **Alle Berichtsausführungs-Momentaufnahmen im Verlauf speichern**.  
  
6. Klicken Sie auf **Anwenden**.  
  
## <a name="to-automatically-add-snapshots-to-report-history-based-on-a-schedule"></a>So fügen Sie basierend auf einem Zeitplan automatisch Momentaufnahmen zum Berichtsverlauf hinzu  
  
1. Navigieren Sie im Berichts-Manager zur Seite **Inhalt** , und zeigen Sie auf das Element, dessen Verlauf angezeigt werden soll, und klicken Sie auf den Dropdownpfeil.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Klicken Sie auf **Momentaufnahmeoptionen**.  
  
4. Aktivieren Sie das Kontrollkästchen für **Folgenden Zeitplan verwenden, um dem Berichtsverlauf Momentaufnahmen hinzuzufügen**. Führen Sie eine der folgenden Aktionen aus:  
  
    - Wählen Sie **Berichtsspezifischer Zeitplan**aus. Geben Sie die Zeitplandetails ein, wählen Sie Start- und Enddatum für den Zeitplan aus, und klicken Sie dann auf **OK**.  

    - Wählen Sie **Freigegebener Zeitplan**aus. Wählen Sie aus der Liste den gewünschten Zeitplan aus.  

5. Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Siehe auch

- [Konfigurieren von Ausführungseigenschaften für einen Bericht &#40;Berichts-Manager&#41;](../../reporting-services/reports/configure-execution-properties-for-a-report-report-manager.md)
- [Einschränken des Berichtsverlaufs (Berichts-Manager)](../../reporting-services/reports/limit-report-history-report-manager.md)
- [Zeitpläne](../../reporting-services/subscriptions/schedules.md)   
- [Berichts-Manager (einheitlicher SSRS-Modus)](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

## <a name="to-manually-add-snapshots-to-report-history"></a>So fügen Sie dem Berichtsverlauf manuell Momentaufnahmen hinzu
  
1. Navigieren Sie im Webportal zu dem Element, für das Sie den Verlauf anzeigen möchten, und klicken Sie mit der rechten Maustaste darauf.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Wählen Sie die Registerkarte **Verlaufs Momentaufnahmen**.  
  
4. Wählen Sie auf der Seite **Verlaufs Momentaufnahmen** die **neue**Verlaufs Momentaufnahme aus. Eine neue Momentaufnahme wird erstellt und unten mit dem aktuellen Datum und der aktuellen Uhrzeit in der **erstellten** Spalte angezeigt.  
  
    > [!NOTE]
    > Um das Erstellen von Momentaufnahmen zu ermöglichen, muss der Administrator den Berichts Verlauf so konfigurieren, **dass der Verlauf manuell erstellt werden kann**. Weitere Informationen finden Sie unter [Einschränken des Berichts Verlaufs (Webportal)](../../reporting-services/reports/limit-report-history-report-manager.md).

## <a name="to-add-snapshots-via-a-schedule-to-report-history"></a>So fügen Sie Momentaufnahmen über einen Zeitplan zum Berichts Verlauf hinzu

1. Navigieren Sie im Webportal zu dem Element, für das Sie den Verlauf anzeigen möchten, und klicken Sie mit der rechten Maustaste darauf.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Wählen Sie die Registerkarte **Verlaufs Momentaufnahmen**.  
  
4. Wählen Sie auf der Seite **Verlaufs Momentaufnahmen** die Schaltfläche **Zeitplan und Einstellungen** aus.  
  
5. Wählen Sie im Abschnitt **Zeitplan** mindestens eine der folgenden Optionen aus, wenn mindestens eine Auswahl nicht bereits ausgewählt ist:
    - **Verlaufsmomentaufnahmen nach Zeitplan erstellen**  
    - **Benutzern das manuelle Erstellen von Momentaufnahmen gestatten**  
  
6. Wählen Sie im Abschnitt **erweitert** die Option Alle Verlaufs **Momentaufnahmen beibehalten**aus.  
  
7. Aktivieren Sie optional auch das Kontrollkästchen **Cache Momentaufnahmen im Berichts Verlauf speichern**.  
  
8.  Klicken Sie auf **Anwenden**, um die Einstellungen zu speichern.  

    > [!NOTE]  
    > Um das Erstellen von Momentaufnahmen zu ermöglichen, muss der Administrator den Berichts Verlauf so konfigurieren, **dass der Verlauf manuell erstellt werden kann**. Weitere Informationen finden Sie unter [Einschränken des Berichts Verlaufs (Webportal)](../../reporting-services/reports/limit-report-history-report-manager.md).

9.  Klicken Sie auf **Anwenden**.

## <a name="to-automatically-add-all-snapshots-to-report-history"></a>So fügen Sie dem Berichtsverlauf automatisch alle Momentaufnahmen hinzu  
  
1. Für einen Bericht, der bereits für die Ausführung als Berichtsausführungs-Momentaufnahme konfiguriert ist, können Sie zusätzliche Eigenschaften festlegen, um bei jeder Aktualisierung der Momentaufnahme eine Kopie der Momentaufnahme im Berichtsverlauf zu speichern.  
  
2. Navigieren Sie im Webportal zu dem Element, für das Sie den Verlauf anzeigen möchten, und klicken Sie mit der rechten Maustaste darauf.  
  
3. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
4. Wählen Sie die Registerkarte **Verlaufs Momentaufnahmen**.  
  
5. Wählen Sie auf der Seite **Verlaufs Momentaufnahmen** die Schaltfläche **Zeitplan und Einstellungen** aus.  
  
6. Wählen Sie im Abschnitt **Zeitplan** mindestens eine der folgenden Optionen aus, wenn mindestens eine Auswahl nicht bereits ausgewählt ist:
    - **Verlaufsmomentaufnahmen nach Zeitplan erstellen**  
    - **Benutzern das manuelle Erstellen von Momentaufnahmen gestatten**  
  
7. Wählen Sie im Abschnitt **erweitert** die Option Alle Verlaufs **Momentaufnahmen beibehalten**aus.  
  
8. Aktivieren Sie optional auch das Kontrollkästchen **Cache Momentaufnahmen im Berichts Verlauf speichern**.  
  
9. Klicken Sie auf **Anwenden**, um die Einstellungen zu speichern.  
  
## <a name="to-automatically-add-snapshots-to-report-history-based-on-a-schedule"></a>So fügen Sie basierend auf einem Zeitplan automatisch Momentaufnahmen zum Berichtsverlauf hinzu  
  
1. Navigieren Sie im Webportal zu dem Element, für das Sie den Verlauf anzeigen möchten, und klicken Sie mit der rechten Maustaste darauf.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Wählen Sie die Registerkarte **Verlaufs Momentaufnahmen**.  
  
4. Wählen Sie auf der Seite **Verlaufs Momentaufnahmen** die Schaltfläche **Zeitplan und Einstellungen** aus.  
  
5. Aktivieren Sie das Kontrollkästchen für **Folgenden Zeitplan verwenden, um dem Berichtsverlauf Momentaufnahmen hinzuzufügen**. Führen Sie eine der folgenden Aktionen aus:  
  
    - Wählen Sie **Berichtsspezifischer Zeitplan**aus. Geben Sie die Zeitplandetails ein, wählen Sie Start- und Enddatum für den Zeitplan aus, und klicken Sie dann auf **OK**.  

    - Wählen Sie **Freigegebener Zeitplan**aus. Wählen Sie aus der Liste den gewünschten Zeitplan aus.  

5. Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Siehe auch

- [Configure Execution Properties for a Report (Konfigurieren von Ausführungseigenschaften für einen Bericht (Webportal))](../../reporting-services/reports/configure-execution-properties-for-a-report-report-manager.md)
- [Einschränken des Berichts Verlaufs (Webportal)](../../reporting-services/reports/limit-report-history-report-manager.md)
- [Zeitpläne](../../reporting-services/subscriptions/schedules.md)   
- [Webportal &#40;einheitlicher SSRS-Modus&#41;](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)

::: moniker-end