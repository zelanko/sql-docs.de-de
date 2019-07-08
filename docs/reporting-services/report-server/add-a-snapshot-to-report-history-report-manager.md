---
title: Hinzufügen einer Momentaufnahme zum Berichtsverlauf - Reporting Services | Microsoft-Dokumentation
ms.prod: reporting-services
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/26/2019
ms.openlocfilehash: e7244e66ec8f6aabd7684bbcd5c22e8d2604d1cb
ms.sourcegitcommit: c0e48b643385ce19c65ca6e348ce83b2d22b6514
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2019
ms.locfileid: "67492834"
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
    > Der Administrator muss zum Erstellen von Snapshots zu aktivieren, den Berichtsverlauf konfigurieren **Berichtsverlauf kann manuell erstellt werden**. Weitere Informationen finden Sie unter [Einschränken des Berichtsverlaufs &#40;Berichts-Manager&#41;](../reports/limit-report-history-report-manager.md).

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
  
1. Die Web-Portal navigieren Sie zu das Element, das Sie verwenden möchten, Verlauf angezeigt, und der rechten Maustaste darauf.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Wählen Sie die **Berichtsverlaufs-Momentaufnahmen** Registerkarte.  
  
4. Auf der **Berichtsverlaufs-Momentaufnahmen** Seite die **neue verlaufsmomentaufnahme**. Eine neue Momentaufnahme wird erstellt, und unten angezeigt werden, mit dem aktuellen Datum und Uhrzeit in der **erstellt** Spalte.  
  
    > [!NOTE]
    > Der Administrator muss zum Erstellen von Snapshots zu aktivieren, den Berichtsverlauf konfigurieren **Berichtsverlauf kann manuell erstellt werden**. Weitere Informationen finden Sie unter [Einschränken des Berichtsverlaufs (Webportal)](../../reporting-services/reports/limit-report-history-report-manager.md).

## <a name="to-add-snapshots-via-a-schedule-to-report-history"></a>Momentaufnahmen über einen Zeitplan zum Berichtsverlauf hinzuzufügen

1. Die Web-Portal navigieren Sie zu das Element, das Sie verwenden möchten, Verlauf angezeigt, und der rechten Maustaste darauf.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Wählen Sie die **Berichtsverlaufs-Momentaufnahmen** Registerkarte.  
  
4. Auf der **Berichtsverlaufs-Momentaufnahmen** Seite die **Zeitplan und Einstellungen** Schaltfläche.  
  
5. In der **Zeitplan** Abschnitt, wählen Sie eine oder beide der folgenden Optionen ein, wenn mindestens eine Auswahl nicht bereits ausgewählt ist:
    - **Erstellen von Berichtsverlaufs-Momentaufnahmen nach einem Zeitplan**.  
    - **Benutzern das manuelle Erstellen von Momentaufnahmen gestatten**.  
  
6. In der **erweitert** wählen Sie im Abschnitt **alle Momentaufnahmen beibehalten**.  
  
7. Wählen Sie optional das Kontrollkästchen für **cachemomentaufnahmen im Berichtsverlauf sowie speichern**.  
  
8.  Klicken Sie auf **Anwenden**, um die Einstellungen zu speichern.  

    > [!NOTE]  
    > Der Administrator muss zum Erstellen von Snapshots zu aktivieren, den Berichtsverlauf konfigurieren **Berichtsverlauf kann manuell erstellt werden**. Weitere Informationen finden Sie unter [Einschränken des Berichtsverlaufs (Webportal)](../../reporting-services/reports/limit-report-history-report-manager.md).

9.  Klicken Sie auf **Anwenden**.

## <a name="to-automatically-add-all-snapshots-to-report-history"></a>So fügen Sie dem Berichtsverlauf automatisch alle Momentaufnahmen hinzu  
  
1. Für einen Bericht, der bereits für die Ausführung als Berichtsausführungs-Momentaufnahme konfiguriert ist, können Sie zusätzliche Eigenschaften festlegen, um bei jeder Aktualisierung der Momentaufnahme eine Kopie der Momentaufnahme im Berichtsverlauf zu speichern.  
  
2. Die Web-Portal navigieren Sie zu das Element, das Sie verwenden möchten, Verlauf angezeigt, und der rechten Maustaste darauf.  
  
3. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
4. Wählen Sie die **Berichtsverlaufs-Momentaufnahmen** Registerkarte.  
  
5. Auf der **Berichtsverlaufs-Momentaufnahmen** Seite die **Zeitplan und Einstellungen** Schaltfläche.  
  
6. In der **Zeitplan** Abschnitt, wählen Sie eine oder beide der folgenden Optionen ein, wenn mindestens eine Auswahl nicht bereits ausgewählt ist:
    - **Erstellen von Berichtsverlaufs-Momentaufnahmen nach einem Zeitplan**.  
    - **Benutzern das manuelle Erstellen von Momentaufnahmen gestatten**.  
  
7. In der **erweitert** wählen Sie im Abschnitt **alle Momentaufnahmen beibehalten**.  
  
8. Wählen Sie optional das Kontrollkästchen für **cachemomentaufnahmen im Berichtsverlauf sowie speichern**.  
  
9. Klicken Sie auf **Anwenden**, um die Einstellungen zu speichern.  
  
## <a name="to-automatically-add-snapshots-to-report-history-based-on-a-schedule"></a>So fügen Sie basierend auf einem Zeitplan automatisch Momentaufnahmen zum Berichtsverlauf hinzu  
  
1. Die Web-Portal navigieren Sie zu das Element, das Sie verwenden möchten, Verlauf angezeigt, und der rechten Maustaste darauf.  
  
2. Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
3. Wählen Sie die **Berichtsverlaufs-Momentaufnahmen** Registerkarte.  
  
4. Auf der **Berichtsverlaufs-Momentaufnahmen** Seite die **Zeitplan und Einstellungen** Schaltfläche.  
  
5. Aktivieren Sie das Kontrollkästchen für **Folgenden Zeitplan verwenden, um dem Berichtsverlauf Momentaufnahmen hinzuzufügen**. Führen Sie eine der folgenden Aktionen aus:  
  
    - Wählen Sie **Berichtsspezifischer Zeitplan**aus. Geben Sie die Zeitplandetails ein, wählen Sie Start- und Enddatum für den Zeitplan aus, und klicken Sie dann auf **OK**.  

    - Wählen Sie **Freigegebener Zeitplan**aus. Wählen Sie aus der Liste den gewünschten Zeitplan aus.  

5. Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Siehe auch

- [Configure Execution Properties for a Report (Konfigurieren von Ausführungseigenschaften für einen Bericht (Webportal))](../../reporting-services/reports/configure-execution-properties-for-a-report-report-manager.md)
- [Einschränken des Berichtsverlaufs (Webportal)](../../reporting-services/reports/limit-report-history-report-manager.md)
- [Zeitpläne](../../reporting-services/subscriptions/schedules.md)   
- [Webportal &#40;einheitlicher SSRS-Modus&#41;](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)

::: moniker-end