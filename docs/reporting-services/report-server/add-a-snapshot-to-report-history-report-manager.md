---
title: Hinzufügen einer Momentaufnahme zum Berichtsverlauf (Reporting Services) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie eine Momentaufnahme manuell zum Berichtsverlauf in SQL Server Reporting Services (SSRS) hinzufügen.
ms.prod: reporting-services
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 06/26/2019
ms.openlocfilehash: 1effcdd44d04b3125cdeaf9983372cdcb00bd429
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245733"
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
    > Der Administrator muss den Berichtsverlauf auf **Berichtsverlauf kann manuell erstellt werden** konfigurieren, um das Erstellen von Momentaufnahmen zu ermöglichen. Weitere Informationen finden Sie unter [Einschränken des Berichtsverlaufs &#40;Berichts-Manager&#41;](../reports/limit-report-history-report-manager.md).

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
  
4. Aktivieren Sie das Kontrollkästchen für **Folgenden Zeitplan verwenden, um dem Berichtsverlauf Momentaufnahmen hinzuzufügen**. Führen Sie einen der folgenden Schritte aus:  
  
    - Wählen Sie **Berichtsspezifischer Zeitplan**aus. Geben Sie die Zeitplandetails ein, wählen Sie Start- und Enddatum für den Zeitplan aus, und klicken Sie dann auf **OK**.  

    - Wählen Sie **Freigegebener Zeitplan**aus. Wählen Sie aus der Liste den gewünschten Zeitplan aus.  

5. Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Weitere Informationen

- [Konfigurieren von Ausführungseigenschaften für einen Bericht &#40;Berichts-Manager&#41;](../../reporting-services/reports/configure-execution-properties-for-a-report-report-manager.md)
- [Einschränken des Berichtsverlaufs (Berichts-Manager)](../../reporting-services/reports/limit-report-history-report-manager.md)
- [Zeitpläne](../../reporting-services/subscriptions/schedules.md)   
- [Berichts-Manager (einheitlicher SSRS-Modus)](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

## <a name="to-manually-add-snapshots-to-report-history"></a>So fügen Sie dem Berichtsverlauf manuell Momentaufnahmen hinzu
  
1. Navigieren Sie im Webportal zu dem Element, für das Sie den Verlauf anzeigen möchten, und klicken Sie mit der rechten Maustaste darauf.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Klicken Sie auf die Registerkarte **Verlaufsmomentaufnahmen**.  
  
4. Klicken Sie auf der Registerkarte **Verlaufsmomentaufnahmen** auf **Neue Verlaufsmomentaufnahme**. Es wird eine neue Momentaufnahme erstellt und unten in der Spalte **Erstellt** mit dem aktuellen Datum und der Uhrzeit angezeigt.  
  
    > [!NOTE]
    > Der Administrator muss den Berichtsverlauf auf **Berichtsverlauf kann manuell erstellt werden** konfigurieren, um das Erstellen von Momentaufnahmen zu ermöglichen. Weitere Informationen finden Sie unter [Einschränken des Berichtsverlaufs (Webportal)](../../reporting-services/reports/limit-report-history-report-manager.md).

## <a name="to-add-snapshots-via-a-schedule-to-report-history"></a>Hinzufügen von Momentaufnahmen zum Berichtsverlauf über einen Zeitplan

1. Navigieren Sie im Webportal zu dem Element, für das Sie den Verlauf anzeigen möchten, und klicken Sie mit der rechten Maustaste darauf.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Klicken Sie auf die Registerkarte **Verlaufsmomentaufnahmen**.  
  
4. Klicken Sie auf der Seite **Berichtsmomentaufnahmen** auf die Schaltfläche **Zeitplan und Einstellungen**.  
  
5. Wählen Sie im Abschnitt **Zeitplan** eine oder beide der folgenden Optionen aus, wenn nicht bereits mindestens eine Option ausgewählt ist:
    - **Verlaufsmomentaufnahmen nach Zeitplan erstellen**  
    - **Benutzern das manuelle Erstellen von Momentaufnahmen gestatten**  
  
6. Klicken Sie im Abschnitt **Erweitert** auf **Alle Verlaufsmomentaufnahmen beibehalten**.  
  
7. Optional können Sie das Kontrollkästchen für **Cachemomentaufnahmen auch in Berichtsverlauf speichern**  aktivieren.  
  
8.  Klicken Sie auf **Anwenden**, um die Einstellungen zu speichern.  

    > [!NOTE]  
    > Der Administrator muss den Berichtsverlauf auf **Berichtsverlauf kann manuell erstellt werden** konfigurieren, um das Erstellen von Momentaufnahmen zu ermöglichen. Weitere Informationen finden Sie unter [Einschränken des Berichtsverlaufs (Webportal)](../../reporting-services/reports/limit-report-history-report-manager.md).

9.  Klicken Sie auf **Anwenden**.

## <a name="to-automatically-add-all-snapshots-to-report-history"></a>So fügen Sie dem Berichtsverlauf automatisch alle Momentaufnahmen hinzu  
  
1. Für einen Bericht, der bereits für die Ausführung als Berichtsausführungs-Momentaufnahme konfiguriert ist, können Sie zusätzliche Eigenschaften festlegen, um bei jeder Aktualisierung der Momentaufnahme eine Kopie der Momentaufnahme im Berichtsverlauf zu speichern.  
  
2. Navigieren Sie im Webportal zu dem Element, für das Sie den Verlauf anzeigen möchten, und klicken Sie mit der rechten Maustaste darauf.  
  
3. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
4. Klicken Sie auf die Registerkarte **Verlaufsmomentaufnahmen**.  
  
5. Klicken Sie auf der Seite **Berichtsmomentaufnahmen** auf die Schaltfläche **Zeitplan und Einstellungen**.  
  
6. Wählen Sie im Abschnitt **Zeitplan** eine oder beide der folgenden Optionen aus, wenn nicht bereits mindestens eine Option ausgewählt ist:
    - **Verlaufsmomentaufnahmen nach Zeitplan erstellen**  
    - **Benutzern das manuelle Erstellen von Momentaufnahmen gestatten**  
  
7. Klicken Sie im Abschnitt **Erweitert** auf **Alle Verlaufsmomentaufnahmen beibehalten**.  
  
8. Optional können Sie das Kontrollkästchen für **Cachemomentaufnahmen auch in Berichtsverlauf speichern**  aktivieren.  
  
9. Klicken Sie auf **Anwenden**, um die Einstellungen zu speichern.  
  
## <a name="to-automatically-add-snapshots-to-report-history-based-on-a-schedule"></a>So fügen Sie basierend auf einem Zeitplan automatisch Momentaufnahmen zum Berichtsverlauf hinzu  
  
1. Navigieren Sie im Webportal zu dem Element, für das Sie den Verlauf anzeigen möchten, und klicken Sie mit der rechten Maustaste darauf.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Klicken Sie auf die Registerkarte **Verlaufsmomentaufnahmen**.  
  
4. Klicken Sie auf der Seite **Berichtsmomentaufnahmen** auf die Schaltfläche **Zeitplan und Einstellungen**.  
  
5. Aktivieren Sie das Kontrollkästchen für **Folgenden Zeitplan verwenden, um dem Berichtsverlauf Momentaufnahmen hinzuzufügen**. Führen Sie einen der folgenden Schritte aus:  
  
    - Wählen Sie **Berichtsspezifischer Zeitplan**aus. Geben Sie die Zeitplandetails ein, wählen Sie Start- und Enddatum für den Zeitplan aus, und klicken Sie dann auf **OK**.  

    - Wählen Sie **Freigegebener Zeitplan**aus. Wählen Sie aus der Liste den gewünschten Zeitplan aus.  

5. Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Weitere Informationen

- [Configure Execution Properties for a Report (Konfigurieren von Ausführungseigenschaften für einen Bericht (Webportal))](../../reporting-services/reports/configure-execution-properties-for-a-report-report-manager.md)
- [Einschränken des Berichtsverlaufs (Webportal)](../../reporting-services/reports/limit-report-history-report-manager.md)
- [Zeitpläne](../../reporting-services/subscriptions/schedules.md)   
- [Webportal &#40;einheitlicher SSRS-Modus&#41;](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)

::: moniker-end