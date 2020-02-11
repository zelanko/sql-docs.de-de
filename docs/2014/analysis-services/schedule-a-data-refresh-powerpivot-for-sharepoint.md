---
title: Planen einer Datenaktualisierung (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 8571208f-6aae-4058-83c6-9f916f5e2f9b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 429b35f6865deb5c0c3dd79e21cfe16cac7fae91
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070010"
---
# <a name="schedule-a-data-refresh-powerpivot-for-sharepoint"></a>Planen einer Datenaktualisierung (PowerPivot für SharePoint)
  Sie können die Datenaktualisierung planen, um PowerPivot-Daten in einer Excel-Arbeitsmappe, die Sie auf einer SharePoint-Website veröffentlicht haben, automatisch aktualisieren zu lassen.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010  
  
 **In diesem Thema:**  
  
 [Voraussetzungen](#prereq)  
  
 [Übersicht über die Datenaktualisierung](#intro)  
  
 [Aktivieren und Planen der Datenaktualisierung](#drenablesched)  
  
 [Überprüfen der Datenaktualisierung](#drverify)  
  
> [!NOTE]  
>  Die PowerPivot-Datenaktualisierung wird von Analysis Services-Serverinstanzen in der SharePoint-Farm ausgeführt. Sie ist nicht mit der Datenaktualisierungsfunktion in Excel Services verwandt. Die planmäßige PowerPivot-Datenaktualisierungsfunktion aktualisiert keine Daten, die nicht in PowerPivot sind.  
  
##  <a name="prereq"></a> Voraussetzungen  
 Sie benötigen mindestens die Berechtigungsstufe Teilnehmen für die Arbeitsmappe, um einen Zeitplan zur Datenaktualisierung zu erstellen.  
  
 Externe Datenquellen, auf die während der Datenaktualisierung zugegriffen wird, müssen verfügbar sein, und die Anmeldeinformationen, die Sie im Zeitplan angeben, müssen Zugriffsberechtigungen für diese Datenquellen beinhalten. Die geplante Datenaktualisierung erfordert einen Datenquellenspeicherort, auf den über eine Netzwerkverbindung zugegriffen werden kann (z. B. über eine Netzwerkdateifreigabe und nicht über einen lokalen Ordner auf der Arbeitsstation).  
  
 Die Datenquelle kann kein Office-Dokument und keine Access-Datenbank sein. Office unterstützt die Verwendung der Office-Datenkonnektivitätskomponenten in einer Serverumgebung nicht. Wenn die Arbeitsmappe Daten aus diesen Quellen enthält, müssen Sie die Quellen aus der Datenquellenliste im Datenaktualisierungszeitplan entfernen.  
  
 Die Arbeitsmappe muss eine [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] -Version sein. Wenn Sie Arbeitsmappen verwenden, die in der vorherigen Version von PowerPivot für Excel erstellt wurden, funktioniert die Zeitplandatenaktualisierung nicht, außer wenn Sie die Datenbank auf die letzte Version aktualisieren.  
  
 Die Arbeitsmappe muss nach Abschluss des Aktualisierungsvorgangs eingecheckt werden. Eine Arbeitsmappensperre wird am Ende der Datenaktualisierung, wenn die Datei gespeichert wird, und nicht zu Beginn der Aktualisierung für die Datei aktiviert.  
  
> [!NOTE]  
>  Die Arbeitsmappe wird vom Server nicht gesperrt, während die Datenaktualisierung ausgeführt wird. Die Datei wird jedoch am Ende der Datenaktualisierung zum Einchecken der aktualisierten Datei gesperrt. Wenn die Datei zu diesem Zeitpunkt an einen anderen Benutzer ausgecheckt wird, werden die aktualisierten Daten ausgelöst. Analog dazu werden die aktualisierten Daten verworfen, wenn die Datei eingeglichen wird, Sie sich jedoch erheblich von der vom Server abgerufenen Kopie unterscheidet.  
  
##  <a name="intro"></a>Übersicht über die Datenaktualisierung  
 PowerPivot-Daten in einer Excel-Arbeitsmappe können aus mehreren externen Datenquellen stammen. Dabei kann es sich um externe Datenbanken oder Datendateien handeln, auf die Sie von Remoteservern oder Netzwerkdateifreigaben zugreifen. Für PowerPivot-Arbeitsmappen, die importierte Daten aus verbundenen oder externen Datenquellen enthalten, können Sie die Datenaktualisierung so planen, dass automatisch aktualisierte Daten aus diesen ursprünglichen Quellen importiert werden.  
  
 Auf eine externe Datenquelle wird über eine eingebettete Verbindungszeichenfolge, eine URL oder einen UNC-Pfad zugegriffen, die Sie beim Importieren der ursprünglichen Daten unter Verwendung der PowerPivot-Clientanwendung in die Arbeitsmappe angegeben haben. Die ursprünglichen, in der PowerPivot-Arbeitsmappe gespeicherten Verbindungsinformationen werden für nachfolgende Datenaktualisierungsvorgänge wiederverwendet. Sie können Anmeldeinformationen überschreiben, um eine Verbindung mit Datenquellen herzustellen. Verbindungszeichenfolgen können zur Datenaktualisierung jedoch nicht überschrieben werden. Es werden nur vorhandene Verbindungsinformationen verwendet.  
  
 Für jede Arbeitsmappe gibt es nur eine Seite mit einem Zeitplan für die Datenaktualisierung, und alle Zeitplaninformationen werden auf dieser Seite angegeben. In der Regel wird der Zeitplan von der Person definiert, die die Arbeitsmappe erstellt hat.  
  
 Der Zeitplanbesitzer führt folgende Aufgaben aus:  
  
-   Definieren des Standardzeitplans. Dieser Zeitplan wird verwendet, wenn keine Zeitpläne auf Datenquellenebene definiert wurden.  
  
-   Angeben der zum Ausführen der Datenaktualisierung verwendeten Anmeldeinformationen  
  
-   Wählen Sie aus, welche Datenquellen in den Aktualisierungsvorgang eingeschlossen werden sollen.  
  
-   Optional können Sie einzelne Zeitpläne und Anmeldeinformationen für jede Datenquelle, die während der Datenaktualisierung abgefragt wird, inline angeben. Jede Datenquelle kann unabhängig aktualisiert werden. Wenn Sie benutzerdefinierte Zeitpläne für die einzelnen Datenquellen erstellen, wird der Standardzeitplan ignoriert.  
  
 Durch die Erstellung eines präzisen Zeitplans für einzelne Datenquellen sind Sie in der Lage, den Aktualisierungszeitplan an Schwankungen in den externen Datenquellen anzupassen. Wenn eine externe Datenquelle z. B. über den Tag erzeugte Transaktionsdaten enthält, können Sie einen einzelnen Zeitplan zur Datenaktualisierung für diese Datenquelle erstellen, um die aktualisierten Informationen jede Nacht abzurufen.  
  
##  <a name="drenablesched"></a>Aktivieren und Planen der Datenaktualisierung  
 Mithilfe der folgenden Anweisungen können Sie die Datenaktualisierung für PowerPivot-Daten in einer Excel-Arbeitsmappe planen, die in einer SharePoint-Bibliothek veröffentlicht wird.  
  
1.  Wählen Sie die Arbeitsmappe in der Bibliothek aus, die die Arbeitsmappe enthält, und klicken Sie dann auf den Pfeil nach unten, um eine Liste mit Befehlen anzuzeigen.  
  
2.  Klicken Sie auf **PowerPivot Datenaktualisierung verwalten**. Wenn bereits ein Zeitplan zur Datenaktualisierung definiert wurde, wird stattdessen die Seite Datenaktualisierungsverlauf anzeigen angezeigt. Sie können auf **Datenaktualisierung konfigurieren** klicken, um die Seite zum Definieren des Zeitplans zu öffnen.  
  
3.  Aktivieren Sie auf der Zeitplandefinitionsseite das Kontrollkästchen **Aktivieren** .  
  
4.  Geben Sie unter Zeitplandetails den Typ des Zeitplans an, und geben Sie seine Details an. Durch diesen Schritt wird der Standardzeitplan erstellt.  
  
    > [!IMPORTANT]  
    >  Stellen Sie sicher, dass das Kontrollkästchen **Führen Sie zudem sobald wie möglich eine Aktualisierung durch** aktiviert ist. Hierdurch können Sie überprüfen, ob die Datenaktualisierung für diese Arbeitsmappe funktionsfähig ist. Beachten Sie, dass es nach dem Speichern des Zeitplans bis zu einer Minute dauern kann, bis die Datenaktualisierung beginnt.  
  
5.  Wählen Sie unter Früheste Startzeit einen der folgenden Werte aus:  
  
    1.  **Nachdem die Geschäftszeiten** einen Verarbeitungs Zeitraum von außerhalb der Geschäftszeiten festgelegt haben, werden die Datenbankserver wahrscheinlich über aktuelle Daten verfügen, die während des gesamten Geschäfts Tags generiert wurden.  
  
    2.  Eine **bestimmte früheste Startzeit** ist die Stunde und Minuten der frühesten Tageszeit, zu der die Daten Aktualisierungs Anforderung einer Verarbeitungs Warteschlange hinzugefügt wird. Sie können die Minuten in 15-Minuten-Intervallen angeben. Die Einstellung gilt für den heutigen Tag sowie zukünftige Tage. Wenn Sie beispielsweise 06:30 angeben und die aktuelle Uhrzeit 16:30 ist, wird die Aktualisierungsanforderung der Warteschlange für den heutigen Tag hinzugefügt, da 16:30 später als 06:30 ist.  
  
     Die früheste Startzeit definiert, wann der Verarbeitungswarteschlange eine Anforderung hinzugefügt wird. Die tatsächliche Verarbeitung erfolgt, sobald der Server über ausreichende Ressourcen zum Starten der Datenverarbeitung verfügt. Die tatsächliche Verarbeitungszeit wird im Datenaktualisierungsverlauf aufgezeichnet, nachdem die Verarbeitung abgeschlossen ist.  
  
6.  Aktivieren Sie das Kontrollkästchen **Führen Sie zudem sobald wie möglich eine Aktualisierung durch.** , um eine Datenaktualisierung auszuführen, sobald sie vom Server verarbeitet werden kann. Bei einem erfolgreichen Ergebnis eines Datenaktualisierungsauftrags wird überprüft, ob die Datenquellen verfügbar sind und ob Berechtigungen und Serverkonfiguration richtig festgelegt sind.  
  
7.  Geben Sie in E-Mail-Benachrichtigungen die E-Mail-Adresse der Person ein, die im Fall eines Verarbeitungsfehlers benachrichtigt werden soll.  
  
8.  Geben Sie in den Anmeldeinformationen ein Konto zum Ausführen des Datenaktualisierungsauftrags an. Das Konto muss über Teilnahmeberechtigungen für die Arbeitsmappe verfügen, damit die Arbeitsmappe zum Aktualisieren der Daten geöffnet werden kann. und ein Windows-Domänenbenutzerkonto sein. In vielen Fällen muss dieses Konto auch über Leseberechtigungen für die während der Datenaktualisierung verwendeten externen Datenquellen verfügen. Konkret wird dann, wenn Sie die Daten ursprünglich mithilfe der Option "Windows-Authentifizierung verwenden" importiert haben, die Verbindungszeichenfolge erstellt, um die Windows-Anmeldeinformationen des aktuellen Benutzers zu verwenden. Wenn der aktuelle Benutzer das Datenaktualisierungskonto ist, muss dieses Konto über Leseberechtigungen für die externe Datenquelle verfügen, um die Datenaktualisierung erfolgreich ausführen zu können. Wählen Sie eine der folgenden Optionen:  
  
    1.  Wählen Sie **Vom Administrator konfiguriertes Datenaktualisierungskonto verwenden** aus, um die Datenaktualisierung mit dem unbeaufsichtigten Datenaktualisierungskonto für PowerPivot durchzuführen.  
  
    2.  Wählen Sie **Verbinden mit den folgenden Windows-Benutzeranmeldeinformationen** aus, wenn Sie einen Benutzernamen und ein Kennwort eingeben möchten. Geben Sie die Kontoinformationen im Format domain\Benutzer ein.  
  
    3.  Wählen **Mit den in Secure Store Service gespeicherten Anmeldeinformationen verbinden** aus, wenn Sie die ID einer Zielanwendung kennen, die zuvor gespeicherte Anmeldeinformationen enthält, die Sie verwenden möchten.  
  
     Weitere Informationen zu diesen Optionen finden Sie unter [Konfigurieren gespeicherter Anmelde Informationen für die Power Pivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md) und [Konfigurieren des unbeaufsichtigten Power Pivot-Daten Aktualisierungs Kontos &#40;PowerPivot für SharePoint&#41;](configure-unattended-data-refresh-account-powerpivot-sharepoint.md).  
  
9. Aktivieren Sie unter Datenquellen das Kontrollkästchen **Alle Datenquellen** , wenn bei der Datenaktualisierung alle ursprünglichen Datenquellen erneut abgefragt werden sollen.  
  
     Wenn Sie diese Option aktivieren, wird jede externe Datenquelle, die Daten für die PowerPivot-Datenquelle bereitstellt, automatisch in die Aktualisierung einbezogen. Dies gilt selbst dann, wenn sich die Liste der Datenquellen mit der Zeit ändert, weil in der Arbeitsmappe verwendete Datenquellen hinzugefügt oder entfernt werden.  
  
     Deaktivieren Sie das Kontrollkästchen **Alle Datenquellen** , wenn Sie die einzubeziehenden Datenquellen manuell auswählen möchten. Wenn Sie die Arbeitsmappe später ändern, indem Sie eine neue Datenquelle hinzufügen, achten Sie darauf, die Datenquellenliste im Zeitplan zu aktualisieren. Andernfalls werden neuere Datenquellen nicht im Aktualisierungsvorgang berücksichtigt.  
  
     Die Liste der Datenquellen, aus der Sie auswählen können, wird beim Öffnen der Seite PowerPivot Datenaktualisierung verwalten für die Arbeitsmappe aus der PowerPivot-Arbeitsmappe abgerufen.  
  
     Sie sollten nur Datenquellen auswählen, die die folgenden Kriterien erfüllen:  
  
    -   Die Datenquelle muss zum Zeitpunkt der Datenaktualisierung sowie am angegebenen Speicherort verfügbar sein. Wenn sich die ursprüngliche Datenquelle auf einem lokalen Laufwerk des Benutzers befindet, der die Arbeitsmappe erstellt hat, müssen Sie diese Datenquelle entweder aus dem Datenaktualisierungsvorgang ausschließen oder eine Möglichkeit finden, die Datenquelle an einem Speicherort zu veröffentlichen, auf den über eine Netzwerkverbindung zugegriffen werden kann. Wenn Sie eine Datenquelle an einen Netzwerkspeicherort verschieben, müssen Sie die Arbeitsmappe im [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] öffnen und die Datenquellen-Verbindungsinformationen aktualisieren. Dies ist notwendig, um die in der PowerPivot-Arbeitsmappe gespeicherten Verbindungsinformationen wiederherzustellen.  
  
    -   Auf die Datenquelle muss mithilfe der Anmeldeinformationen zugegriffen werden können, die in die PowerPivot-Arbeitsmappe eingebettet oder im Zeitplan angegeben sind. Eingebettete Anmeldeinformationen werden in der PowerPivot-Arbeitsmappe gespeichert, wenn Sie Daten mit PowerPivot für Excel importieren. Eingebettete Anmeldeinformationen sind oft SSPI=IntegratedSecurity oder SSPI=TrustedConnection. Dies bedeutet, das die Verbindung mit der Datenquelle mithilfe der Anmeldeinformationen des aktuellen Benutzers hergestellt wird. Wenn Sie die Anmeldeinformationen im Datenaktualisierungszeitplan überschreiben möchten, können Sie vordefinierte, gespeicherte Anmeldeinformationen angeben. Weitere Informationen finden Sie unter [Konfigurieren gespeicherter Anmelde Informationen für die Power Pivot-Datenaktualisierung &#40;PowerPivot für SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
    -   Die Datenaktualisierung muss für alle angegebenen Datenquellen erfolgreich verlaufen. Andernfalls werden die aktualisierten Daten verworfen und die zuletzt gespeicherte Version der Arbeitsmappe verwendet. Schließen Sie alle Datenquellen, bei denen Sie unsicher sind, aus.  
  
    -   Durch die Datenaktualisierung dürfen keine anderen Daten in der Arbeitsmappe ungültig werden. Wenn Sie eine Teilmenge der Daten aktualisieren, ist es wichtig, zu wissen, ob die Arbeitsmappe weiterhin gültig ist, sobald neuere Daten mit statischen Daten aggregiert werden, die nicht aus dem gleichen Zeitraum stammen. Als Arbeitsmappenautor sollten Sie die Datenabhängigkeiten genau kennen und sicherstellen, dass die Datenaktualisierung auch für die Arbeitsmappe geeignet ist.  
  
10. Optional können Sie individuelle Zeitpläne für bestimmte Datenquellen definieren. Dies ist bei ursprünglichen Datenquellen hilfreich, die selbst nach einem Zeitplan aktualisiert werden. Wenn eine PowerPivot-Datenquelle z. B. Daten aus einem Data Mart verwendet, der jeden Montag um 02:00 Uhr aktualisiert wird, können Sie einen Inlinezeitplan für den Data Mart definieren, mit dem dessen aktualisierte Daten jeden Montag um 04:00 Uhr abgerufen werden.  
  
11. Klicken Sie auf **OK** , um den Zeitplan zu speichern.  
  
##  <a name="drverify"></a>Überprüfen der Datenaktualisierung  
 Die beste Methode zum Überprüfen der Datenaktualisierung besteht darin, die Datenaktualisierung sofort auszuführen und dann auf der Verlaufsseite zu prüfen, ob sie erfolgreich abgeschlossen wurde. Durch das Aktivieren des Kontrollkästchens **Führen Sie zudem sobald wie möglich eine Aktualisierung durch.** für den Zeitplan wird die Überprüfung bereitgestellt, ob die Datenaktualisierung funktionstüchtig ist.  
  
 Sie können den aktuellen und vorherigen Datensatz mit Datenaktualisierungsvorgängen auf der Seite Verlauf der Datenaktualisierung der Arbeitsmappe anzeigen. Diese Seite wird nur angezeigt, wenn die Datenaktualisierung für eine Arbeitsmappe geplant wurde. Wenn kein Zeitplan zur Datenaktualisierung vorhanden ist, wird stattdessen die Seite zum Definieren des Zeitplans angezeigt.  
  
 Zum Anzeigen des Datenaktualisierungsverlaufs müssen Sie mindestens über Teilnahmeberechtigungen verfügen.  
  
1.  Öffnen Sie auf der SharePoint-Website die Bibliothek, die eine PowerPivot-Arbeitsmappe enthält.  
  
     Es gibt keinen visuellen Indikator dafür, welche Arbeitsmappen in einer SharePoint-Bibliothek PowerPivot-Daten enthalten. Sie müssen im Voraus wissen, welche Arbeitsmappen aktualisierbare PowerPivot-Daten enthalten.  
  
2.  Wählen Sie das Dokument aus, und klicken Sie dann auf den rechts angezeigten Pfeil nach unten.  
  
3.  Wählen Sie **PowerPivot-Datenaktualisierung verwalten**aus.  
  
 Die Verlaufsseite wird mit einem vollständigen Datensatz aller Aktualisierungsaktivitäten für PowerPivot-Daten in der aktuellen Excel-Arbeitsmappe angezeigt, einschließlich des Status des letzten Datenaktualisierungsvorgangs.  
  
 In einigen Fällen können tatsächliche Verarbeitungszeiten angezeigt werden, die von den angegebenen Zeiten abweichen. Dies kann vorkommen, wenn der Server stark ausgelastet ist. Bei einer starken Auslastung wird die Datenaktualisierung von der [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] -Dienstinstanz erst gestartet, wenn wieder genügend Systemressourcen zur Verfügung stehen.  
  
 Die Arbeitsmappe muss nach Abschluss des Aktualisierungsvorgangs eingecheckt werden. Zu diesem Zeitpunkt wird die Arbeitsmappe mit den aktualisierten Daten gespeichert. Wenn die Datei ausgecheckt ist, wird die Datenaktualisierung bis zum nächsten geplanten Termin übersprungen.  
  
 Wenn eine unerwartete Statusmeldung angezeigt wird (wenn ein Aktualisierungsvorgang z. B. fehlgeschlagen ist oder abgebrochen wurde), können Sie das Problem untersuchen, indem Sie die Berechtigungen und Serververfügbarkeit überprüfen.  
  
 Hilfe zum Lösen von Problemen bei der Aktualisierung von PowerPivot-Daten finden Sie auf der entsprechenden TechNet-WIKI-Website. Weitere Informationen finden Sie unter [Problembehandlung bei der PowerPivot-Datenaktualisierung](https://go.microsoft.com/fwlink/?LinkId=251594).  
  
> [!NOTE]  
>  SharePoint-Administratoren können Ihnen helfen, Datenaktualisierungsprobleme zu lösen, indem sie die konsolidierten Datenaktualisierungsberichte im PowerPivot-Management-Dashboard in der zentralen Verwaltung anzeigen. Weitere Informationen finden Sie unter [PowerPivot Management Dashboard and Usage Data](power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Power Pivot-Datenaktualisierung mit SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)   
 [Anzeigen des Daten Aktualisierungs Verlaufs &#40;PowerPivot für SharePoint&#41;](power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)   
 [Gespeicherte Anmelde Informationen für die Power Pivot-Datenaktualisierung &#40;PowerPivot für SharePoint konfigurieren&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
  
