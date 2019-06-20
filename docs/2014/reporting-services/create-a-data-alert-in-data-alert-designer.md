---
title: Erstellen einer Datenwarnung im Datenwarnungs-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8464ab9d-afe1-4490-955f-9f3319bcbf8d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e2b54bbbd6b989890c1d31a545c95117c4b6cbe2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66109707"
---
# <a name="create-a-data-alert-in-data-alert-designer"></a>Erstellen einer Datenwarnung im Datenwarnungs-Designer
  Sie können Datenwarnungsdefinitionen im Datenwarnungs-Designer erstellen. Nach dem Speichern der Warnungsdefinitionen können Sie diese im Datenwarnungs-Designer erneut öffnen, bearbeiten und dann erneut speichern. Weitere Informationen zum Bearbeiten von Warnungsdefinitionen finden Sie unter [Verwalten meiner Datenwarnungen im Datenwarnungs-Manager](manage-my-data-alerts-in-data-alert-manager.md) und [Bearbeiten einer Datenwarnung im Warnungs-Designer](edit-a-data-alert-in-alert-designer.md).  
  
### <a name="to-create-a-data-alert-definition"></a>So erstellen Sie eine Datenwarnungsdefinition  
  
1.  Wechseln Sie zur SharePoint-Bibliothek mit dem Bericht, für den Sie eine Datenwarnungsdefinition erstellen möchten.  
  
2.  Klicken Sie auf den Bericht.  
  
     Der Bericht wird ausgeführt. Wenn der Bericht parametrisiert ist, überprüfen Sie, ob der Bericht die Daten enthält, für die Sie Warnmeldungen erhalten möchten. Wenn Sie die Spalten oder die Werte nicht sehen, an denen Sie interessiert sind, können Sie den Bericht mit anderen Parameterwerten erneut ausführen.  
  
    > [!NOTE]  
    >  Die zum Ausführen des Berichts ausgewählten Parameterwerte werden in der Warnungsdefinition gespeichert und verwendet, wenn der Bericht als Schritt der Verarbeitung der Warnungsdefinition erneut ausgeführt wird. Um andere Parameterwerte zu verwenden, müssen Sie eine neue Warnungsdefinition erstellen.  
  
3.  Klicken Sie im Menü **Aktionen** auf **Neue Datenwarnung**.  
  
     Das folgende Bild zeigt das Menü **Aktionen** an.  
  
     ![Warnungs-Designer aus SharePoint-Bibliothek öffnen](media/rs-openalertdesigneriw.gif "Open Alert Designer from SharePoint library")  
  
     Der Datenwarnungs-Designer wird geöffnet und zeigt die ersten 100 Zeilen des ersten Datenfeeds an, den der Bericht in einer Tabelle generiert.  
  
    > [!NOTE]  
    >  Wenn Sie die Option **Neue Datenwarnung** nicht sehen, ist der Warndienst nicht auf der SharePoint-Website konfiguriert, oder die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Edition umfasst keine Datenwarnungen. Weitere Informationen finden Sie unter [Reporting Services-SharePoint-Dienst und -Dienstanwendungen](../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md).  
    >   
    >  Ist die Option **Neue Datenwarnung** ausgegraut, ist die Berichtsdatenquelle so konfiguriert, dass integrierte Sicherheitsanmeldeinformationen verwendet werden oder eine Eingabeaufforderung für Anmeldeinformationen angezeigt wird. Zur Bereitstellung der Option **Neue Datenwarnung** müssen Sie die Datenquelle so aktualisieren, dass entweder gespeicherte Anmeldeinformationen oder keine Anmeldeinformationen zu verwenden sind.  
  
     Der Name des Datenfeeds wird in der Dropdownliste **Berichtsdatenname** angezeigt.  
  
4.  Wählen Sie in der Dropdownliste **Berichtsdatenname** optional einen anderen Datenfeed aus.  
  
     Wenn kein Datenfeed aus dem Bericht generiert wird, können Sie für den Bericht keine Warnungsdefinition erstellen. Das Layout des Berichts bestimmt den Inhalt jedes Datenfeeds. Weitere Informationen finden Sie unter [Generieren von Datenfeeds aus Berichten (Berichts-Generator und SSRS)](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
5.  Sie können im Textfeld **Warnungsname** den Standardnamen in einen sinnvolleren Namen ändern.  
  
     Der Standardname der Warnungsdefinition entspricht dem Namen des Berichts. Warnungsdefinitionsnamen müssen nicht eindeutig sind, sodass sie schwer voneinander zu unterscheiden sind, wenn Sie die Liste der Warnungen später im Datenwarnungs-Manager anzeigen. Es empfiehlt sich, sinnvolle und eindeutige Namen für die Warnungsdefinitionen zu verwenden.  
  
6.  Ändern Sie die Standarddatenoption optional von **die Daten im Datenfeed Folgendes enthalten** in **die Daten im Datenfeed Folgendes nicht enthalten**.  
  
7.  Klicken Sie auf **Regel hinzufügen**.  
  
     Eine Liste der Spalten im Datenfeed wird angezeigt.  
  
8.  Wählen Sie aus der Liste die Spalte aus, die Sie in der Regel verwenden möchten. Wählen Sie dann einen Vergleichsoperator aus, und geben Sie den Schwellenwert ein.  
  
     Abhängig vom Datentyp der ausgewählten Spalte sind andere Vergleichsoperatoren aufgeführt. Wenn die Spalte einen Datumsdatentyp aufweist, wird ein Kalendersymbol neben dem Schwellenwert für die Regel angezeigt. Sie können Daten eingeben, indem Sie auf ein Datum im Kalender klicken oder das Datum eingeben.  
  
     Der Datenwarnungs-Designer bietet zwei Vergleichsmodi: **Werteingabemodus** und **Feldauswahlmodus**. Der Standardmodus ist der **Werteingabemodus**. Sie können OR-Klauseln nur hinzufügen, wenn der **Werteingabemodus** aktiviert ist und Sie den Vergleich **ist** verwenden.  
  
9. Um eine OR-Klausel hinzuzufügen, klicken Sie auf den Pfeil nach unten und anschließend auf **Werteingabemodus**.  
  
10. Geben Sie den Vergleichswert ein.  
  
11. Klicken Sie optional erneut auf die Auslassungspunkte **(...)** .  
  
     Die Auslassungspunkte **(...)** werden in der Zeile mit der ersten Klausel angezeigt.  
  
     Eine OR-Klausel wird unten und innerhalb der AND-Regel hinzugefügt.  
  
12. Klicken Sie optional auf den Pfeil nach unten, wählen Sie **Feldauswahlmodus**und anschließend eine Spalte in der Liste aus.  
  
     Die Auslassungspunkte **(...)** , auf die Sie zum Hinzufügen von OR-Klauseln klicken, werden nicht mehr angezeigt.  
  
13. Klicken Sie optional erneut auf **Regel hinzufügen** , um weitere Regeln hinzuzufügen.  
  
     Die Regeln werden mithilfe des logischen AND-Operators kombiniert.  
  
14. Wählen Sie in der Wiederholungsliste eine Option aus. Geben Sie abhängig vom Typ der Wiederholung ein Intervall ein.  
  
15. Klicken Sie optional auf **Erweitert**.  
  
16. Ändern Sie optional das Startdatum der Warnmeldung, indem Sie ein anderes Datum eingeben oder den Kalender öffnen und auf ein Datum im Kalender klicken.  
  
     Das Standardstartdatum ist das aktuelle Datum.  
  
17. Aktivieren Sie optional das Kontrollkästchen neben **Warnung beenden**, und wählen Sie dann ein Datum aus, an dem die Warnmeldung enden soll.  
  
     Standardmäßig hat eine Warnmeldung kein Enddatum.  
  
    > [!NOTE]  
    >  Durch das Beenden einer Warnmeldung wird die Warnungsdefinition nicht gelöscht. Nach dem Beenden einer Warnmeldung können Sie diese durch Aktualisieren des Start- und Enddatums erneut starten. Weitere Informationen zum Löschen von Warnungsdefinitionen finden Sie unter [Verwalten meiner Datenwarnungen im Datenwarnungs-Manager](manage-my-data-alerts-in-data-alert-manager.md).  
  
18. Deaktivieren Sie optional das Kontrollkästchen zum **Senden von Meldungen nur bei Ergebnisänderungen**.  
  
     Wenn Sie Warnmeldungen häufig senden, sind redundante Informationen u. U. nicht erwünscht, und Sie sollten das Kontrollkästchen nicht deaktivieren.  
  
19. Geben Sie die E-Mail-Adressen von Warnmeldungsempfängern ein. Trennen Sie Adressen mit Semikolons.  
  
     Ist die E-Mail-Adresse des Erstellers der Warnungsdefinition verfügbar, wird sie dem Feld **Empfänger** hinzugefügt.  
  
20. Aktualisieren Sie optional im Textfeld **Betreff** die Betreffzeile der Warnmeldung.  
  
     Der Standardbetreff lautet **Datenwarnung für \<Name der Datenwarnung>** .  
  
21. Geben Sie optional im Textfeld **Beschreibung** eine Beschreibung der Warnmeldung ein.  
  
22. Klicken Sie auf **Speichern**.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenwarnungs-Designer](../../2014/reporting-services/data-alert-designer.md)   
 [Datenwarnungs-Manager für Warnungsadministratoren](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Reporting Services-Datenwarnungen](../ssms/agent/alerts.md)  
  
  
