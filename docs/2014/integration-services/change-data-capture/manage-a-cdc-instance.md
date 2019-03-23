---
title: Verwalten einer CDC-Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- manIns
ms.assetid: cfed22c8-c666-40ca-9e73-24d93e85ba92
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3215f28615511f3c35fcc6cc3ea80209c7c44d41
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378818"
---
# <a name="manage-a-cdc-instance"></a>Verwalten einer CDC-Instanz
  Sie können die CDC Designer Console zum Anzeigen von Informationen zu den erstellten Instanzen und zum Verwalten des Betriebs der Instanzen verwenden.  
  
 Klicken Sie im linken Bereich auf den Namen einer Instanz, um die Informationen zur Instanz anzuzeigen.  
  
> [!NOTE]  
>  Wenn Sie im linken Bereich einen Dienst auswählen, wird die Liste der verfügbaren Instanzen auch im mittleren Bereich der CDC Designer Console angezeigt. Wenn Sie eine der Instanzen in diesem Abschnitt auswählen, können Sie die Tasks im rechten Bereich ausführen. Sie können jedoch nicht die Informationen auf den Registerkarten mit den Eigenschaften anzeigen.  
  
## <a name="what-you-can-do-when-you-display-the-cdc-instance-information"></a>Optionen beim Anzeigen der Informationen zur CDC-Instanz  
 Die folgenden Aktionen werden im rechten Bereich ausgeführt:  
  
 **Start**  
 Klicken Sie auf **Start** , um die Aufzeichnung der Änderungen für die ausgewählte CDC-Instanz zu starten.  
  
 **Beenden**  
 Klicken Sie auf **Beenden** , um die Aufzeichnung für die ausgewählte CDC-Instanz zu beenden. Wenn Sie die CDC-Instanz beenden, gehen die Änderungen, die bis zu diesem Punkt aufgezeichnet wurden, nicht verloren und werden übermittelt, wenn die CDC-Instanz fortgesetzt wird.  
  
 **Zurücksetzen**  
 Klicken Sie auf **Zurücksetzen** , um die CDC-Instanz auf ihren ursprünglichen (leeren) Zustand zurückzusetzen. Diese Option ist verfügbar, wenn die CDC-Instanz beendet wurde. Alle Änderungen in den Änderungstabellen und der interne Status der CDC-Instanz werden gelöscht. Wenn die CDC-Instanz später dann gestartet wird, beginnt die Änderungsaufzeichnung ab diesem Zeitpunkt und schließt nur Transaktionen ein, die nach dem Starten der CDC-Instanz gestartet wurden.  
  
 Klicken Sie im Bestätigungsdialogfeld auf **OK** , um zu bestätigen, dass Sie die CDC-Instanz zurücksetzen und die in die Änderungstabellen geschriebenen Änderungen löschen möchten.  
  
 **Delete**  
 Klicken Sie auf **Löschen** , um die CDC-Instanz dauerhaft zu löschen. Diese Option ist nur verfügbar, wenn die CDC-Instanz beendet wurde.  
  
 Klicken Sie im Bestätigungsdialogfeld auf **OK** , um zu bestätigen, dass Sie die CDC-Instanz löschen möchten.  
  
 **Oracle Logging Script**  
 Klicken Sie auf diesen Link, um das Dialogfeld Oracle Logging Script mit dem ergänzenden Oracle-Protokollierungsskript anzuzeigen. Informationen zu den Schritten, die Sie in diesem Dialogfeld ausführen können, finden Sie unter [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md).  
  
> [!NOTE]  
>  Wenn Sie die ergänzenden Protokollierungsskripts ausführen, wird das Dialogfeld Oracle Credentials for Running Script geöffnet, in dem Sie einen gültigen Oracle-Benutzernamen und das dazugehörige Kennwort angeben können. Informationen zum Bereitstellen der richtigen Oracle-Anmeldeinformationen finden Sie unter [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).  
  
 **CDC Instance Deployment Script**  
 Klicken Sie auf diesen Link, um das Dialogfeld CDC Instance Deployment Script zu öffnen, in dem das Bereitstellungsskript für die CDC-Instanz angezeigt wird. Informationen zu diesem Dialogfeld finden Sie unter [CDC Instance Deployment Script](cdc-instance-deployment-script.md).  
  
 **Eigenschaften**  
 Klicken Sie auf diesen Link, um den Eigenschaften-Editor zu öffnen. Sie bearbeiten die CDC-Instanzkonfiguration mithilfe des Eigenschaften-Editors. Weitere Informationen zum Bearbeiten der Eigenschaften für eine CDC-Instanz finden Sie unter [Edit Instance Properties](edit-instance-properties.md).  
  
 **Viewer-Registerkarten**  
  
 Die folgenden Viewer-Registerkarten sind verfügbar, wenn Sie Informationen für die CDC-Instanz anzeigen. Die Informationen auf diesen Registerkarten sind schreibgeschützt.  
  
 **Status**  
 Diese Registerkarte enthält Informationen und Statistiken zum aktuellen Status der CDC-Instanz. Sie liefert die folgenden Informationen.  
  
-   **Status:** Ein Symbol, das den aktuellen Status für die CDC-Instanz angibt. Die Status sind unten beschrieben.  
  
    |||  
    |-|-|  
    |![Fehler](../media/error.gif "Fehler")|**Fehler**: Die Oracle CDC-Instanz wird nicht ausgeführt, da ein nicht wiederholbarer Fehler aufgetreten ist. Die folgenden Unterstatus sind verfügbar:<br /><br /> **Falsch konfigurierte**: Ein Konfigurationsfehler aufgetreten ist, die manuellen Eingriff erfordert.<br /><br /> **Erforderliche Kennwort**: Für die Oracle CDC-Instanz wurde kein Kennwort festgelegt, oder das Kennwort ist ungültig.<br /><br /> **Unerwartet**: Alle anderen nicht behebbaren Fehler.|  
    |![OK](../media/okay.gif "OK")|**Wird ausgeführt:** Die CDC-Instanz wird ausgeführt und verarbeitet Änderungsdatensätze. Die folgenden Unterstatus sind verfügbar.<br /><br /> **Idle**: Alle Änderungsdatensätze wurden verarbeitet und in den zieländerungstabellen gespeichert. Es sind keine aktiven Transaktionen mehr vorhanden.<br /><br /> **Verarbeiten von**: Es gibt wird der Prozess Änderungsdatensätze, die noch nicht in die Änderungstabellen geschrieben wurden.|  
    |![Beenden](../media/stop.gif "Beenden")|**Beendet:** Die CDC-Instanz wird nicht ausgeführt. Der Status Beendet gibt an, dass die CDC-Instanz auf normale Weise beendet wurde.|  
    |![Angehalten](../media/paused.gif "Angehalten")|**Angehalten**: Die CDC-Instanz ausgeführt wird, aber Verarbeitung wurde aufgrund eines wiederholbaren Fehlers angehalten. Die folgenden Unterstatus sind verfügbar:<br /><br /> **Die Verbindung getrennt**: Die Verbindung mit Oracle-Quelldatenbank kann nicht hergestellt werden. Die Verarbeitung wird fortgesetzt, nachdem die Verbindung wiederhergestellt wurde.<br /><br /> **Storage**: Der Speicher ist voll. Die Verarbeitung wird fortgesetzt, wenn zusätzlicher Speicher verfügbar wird.<br /><br /> **Logger**: Die Protokollierung ist mit Oracle verbunden, aber die Oracle-Transaktionsprotokolle aufgrund eines vorübergehenden Problems kann nicht gelesen werden, z. B. ein erforderliches Transaktionsprotokoll nicht verfügbar.|  
  
-   **Detaillierter Status der**: Der aktuelle Unterstatus.  
  
-   **Statusmeldung**: Weitere Informationen zu den aktuellen Status.  
  
-   **Zeitstempel**: Die UTC-Zeit für die bei der CDC-Status zuletzt aus der Statustabelle gelesen wurde.  
  
-   **Gerade verarbeitet,**: Sie überwachen die folgende Informationen in diesem Abschnitt.  
  
    -   **Transaktionszeitstempel der letzten**: Die lokale Zeit des letzten in die Änderungstabellen geschriebenen Transaktion.  
  
    -   **Letzte Änderung Zeitstempel**: Die lokale Zeit der letzten Änderung, von Oracle CDC-Instanz in den Transaktionsprotokollen Oracle Source sichtbar. Hierbei werden Informationen zur aktuellen Latenzzeit der CDC-Instanz beim Lesen des Oracle-Transaktionsprotokolls bereitgestellt.  
  
    -   **Transaction Log Head CN**: Die letzte Änderungsnummer (CN), die aus dem Oracle-Transaktionsprotokoll gelesen wurde.  
  
    -   **Transaction Log Tail CN**: Die Änderungsnummer zur Wiederherstellung oder zum Neustarten der CDC-Instanz. Die Oracle CDC-Instanz greift auf diese Position zurück, falls ein Neustart durchgeführt wird oder ein anderer Fehler auftritt (einschließlich Clusterfailover).  
  
    -   **Current CN**: Die letzte Änderungsnummer (SCN) in der Oracle-Quelldatenbank (nicht das Transaktionsprotokoll).  
  
    -   **Aktive Transaktionen**: Die aktuelle Anzahl von Oracle-quelltransaktionen, die von der Oracle CDC-Instanz verarbeitet werden und sind nicht entschieden noch (Commit/Rollback).  
  
    -   **Bereitgestellte Transaktionen**: Die aktuelle Anzahl Oracle-quelltransaktionen, die auf bereitgestellt werden die [xdbcdc_staged_transactions](the-oracle-cdc-databases.md#BKMK_cdcxdbcdc_staged_transactions) Tabelle.  
  
-   **Leistungsindikatoren**: Sie überwachen die folgende Informationen in diesem Abschnitt.  
  
    -   **Abschluss von Transaktionen**: Die Anzahl der Transaktionen, die seit der letzten Zurücksetzung der CDC-Instanz wurde abgeschlossen. Dies schließt keine Transaktionen ein, die keine relevanten Tabellen enthalten.  
  
    -   **Geschrieben von Änderungen**: Die Anzahl der Änderungen, die geschrieben werden, mit der SQL Server-Änderungstabellen.  
  
 **Oracle**  
 Zeigt Informationen zur CDC-Instanz und zu ihrer Verbindung mit der Oracle-Datenbank an. Diese Registerkarte ist schreibgeschützt. Klicken Sie zum Bearbeiten dieser Eigenschaften im linken Bereich mit der rechten Maustaste auf die Instanz, und wählen Sie **Eigenschaften** aus, oder klicken Sie im rechten Bereich auf **Eigenschaften**, um das Dialogfeld mit den „Eigenschaften von \<Instanz>“ zu öffnen.  
  
 Informationen zu diesen Eigenschaften und zu deren Bearbeitung finden Sie unter [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).  
  
 **Tabellen**  
 Zeigt Informationen zu den in der CDC-Instanz enthaltenen Tabellen an. Spalteninformationen sind ebenfalls verfügbar. Diese Registerkarte ist schreibgeschützt. Klicken Sie zum Bearbeiten dieser Eigenschaften im linken Bereich mit der rechten Maustaste auf die Instanz, und wählen Sie **Eigenschaften** aus, oder klicken Sie im rechten Bereich auf **Eigenschaften**, um das Dialogfeld mit den „Eigenschaften von \<Instanz>“ zu öffnen.  
  
 Informationen zu diesen Eigenschaften und zu deren Bearbeitung finden Sie unter [Edit Tables](edit-tables.md).  
  
 **Erweitert:**  
 Zeigt die erweiterten Eigenschaften für die CDC-Instanz und die Eigenschaftswerte an. Diese Registerkarte ist schreibgeschützt. Klicken Sie zum Bearbeiten dieser Eigenschaften im linken Bereich mit der rechten Maustaste auf die Instanz, und wählen Sie **Eigenschaften** aus, oder klicken Sie im rechten Bereich auf **Eigenschaften**, um das Dialogfeld mit den „Eigenschaften von \<Instanz>“ zu öffnen.  
  
 Informationen zu diesen Eigenschaften und zu deren Bearbeitung finden Sie unter [Edit the Advanced Properties](edit-the-advanced-properties.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen der Instanz für die SQL Server-Änderungsdatenbank](how-to-create-the-sql-server-change-database-instance.md)   
 [Anzeigen der CDC-Instanzeigenschaften](how-to-view-the-cdc-instance-properties.md)   
 [Bearbeiten der CDC-Instanzeigenschaften](how-to-edit-the-cdc-instance-properties.md)   
 [Verwenden des Assistenten für neue Instanzen](use-the-new-instance-wizard.md)  
  
  
