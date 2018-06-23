---
title: Verarbeitungsoptionen (Eigenschaftenseite) (Berichts-Manager) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 28f07c70-7132-4d15-9505-4fdf31dc9cc0
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 17db40e24318fad194ec21ca30e6394f3fe607e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060646"
---
# <a name="processing-options-properties-page-report-manager"></a>Verarbeitungsoptionen (Eigenschaftenseite) (Berichts-Manager)
  Mithilfe der Eigenschaftenseite Verarbeitungsoptionen können Sie Eigenschaften der Berichtsausführung für den aktuell ausgewählten Bericht festlegen. Mit diesen Optionen wird der Zeitpunkt der Verarbeitung von Daten für den Bericht bestimmt. Sie können diese Optionen festlegen, um die Berichtsdaten außerhalb der Spitzenbetriebszeiten abzurufen. Wenn ein Bericht häufig verwendet wird, können Sie auch vorübergehend Kopien des Berichts zwischenspeichern, um Wartezeiten zu vermeiden, falls mehrere Benutzer innerhalb von Minuten auf denselben Bericht zugreifen.  
  
> [!NOTE]  
>  Folgende Funktionen sind nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar: Berichtsverlauf, Ausführungsmomentaufnahmen und Funktionen zum Zwischenspeichern. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-processing-options-properties-page"></a>So öffnen Sie die Eigenschaftenseite "Verarbeitungsoptionen"  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie Verarbeitungseigenschaften festlegen möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für den Bericht geöffnet.  
  
4.  Wählen Sie die Registerkarte **Verarbeitungsoptionen** aus.  
  
## <a name="options"></a>Tastatur  
 **Diesen Bericht ausführen immer mit den neuesten Daten**  
 Verwenden Sie diese Option, wenn die Berichtsdaten abgerufen werden sollen, sobald der Benutzer den Bericht auswählt. Wenn eine zwischengespeicherte Kopie des Berichts verfügbar ist, wird diese an den Benutzer zurückgegeben; andernfalls erfolgt das Abrufen und Rendern der Daten, wenn ein Benutzer den Bericht auswählt.  
  
 Wählen Sie die Option **Keine temporären Kopien dieses Berichts zwischenspeichern** aus, wenn der Bericht immer mit den neuesten Daten ausgeführt werden soll. Jeder Benutzer, der den Bericht öffnet, löst eine Abfrage in der Datenquelle aus, in der die im Bericht verwendeten Daten enthalten sind.  
  
 Wählen Sie die Option **Eine temporäre Kopie des Berichts zwischenspeichern**aus, um eine temporäre Kopie des Berichts in einen Cache zu platzieren, wenn der erste Benutzer den Bericht öffnet. Nachfolgende Benutzer, die den Bericht innerhalb des Zeitraums der Zwischenspeicherung ausführen, erhalten die zwischengespeicherte Kopie des Berichts. Die Zwischenspeicherung erhöht in der Regel die Leistung, da der Bericht aus dem Cache zurückgegeben wird und nicht erneut verarbeitet werden muss.  
  
 Der Zeitraum der Zwischenspeicherung muss irgendwann ablaufen. Geben Sie die Zeitdauer in Minuten an, während derer die zwischengespeicherte Kopie des Berichts erhalten bleibt. Sobald eine temporäre Kopie abgelaufen ist, wird sie nicht mehr aus dem Cache zurückgegeben. Wenn der Benutzer den Bericht das nächste Mal öffnet, verarbeitet der Berichtsserver den Bericht erneut und platziert eine neue Kopie des aktualisierten Berichts im Cache.  
  
 Es kann auch ein Ablaufzeitplan mit einer anderen Angabe als Minuten für einen zwischengespeicherten Bericht verwendet werden. Um beispielsweise einen zwischengespeicherten Bericht am Ende des Tages ablaufen zu lassen, können Sie eine bestimmte Uhrzeit in der Nacht angeben, nach der die Kopie ungültig wird.  
  
 **Diesen Bericht aus einer ausführungsmomentaufnahme Rendern**  
 Verwenden Sie diese Option, um einen Bericht abzurufen, der zu einem von Ihnen geplanten Zeitpunkt als Momentaufnahme gespeichert wurde. Wenn Sie diese Option auswählen, können Sie die Datenverarbeitung so planen, dass sie außerhalb der Spitzenbetriebszeiten auftritt. Anders als bei zwischengespeicherten Kopien, die beim Öffnen des Berichts durch einen Benutzer erstellt werden, wird eine Momentaufnahme erstellt und anschließend gemäß einem Zeitplan aktualisiert. Momentaufnahmen haben kein Ablaufdatum, sie können verwendet werden, bis sie durch neuere Versionen ersetzt werden.  
  
 Momentaufnahmen, die als Ergebnis von Berichtsausführungseinstellungen generiert werden, weisen dieselben Merkmale auf wie Momentaufnahmen zum Berichtsverlauf. Sie unterscheiden sich darin, dass nur eine Momentaufnahme zur Berichtsausführung und möglicherweise zahlreiche Momentaufnahmen zum Berichtsverlauf vorhanden sind. Auf Momentaufnahmen zum Berichtsverlauf wird über die Seite Verlauf des Berichts zugegriffen, auf der zahlreiche Instanzen eines Berichts gespeichert sind, so wie sie zu unterschiedlichen Zeitpunkten vorhanden waren. Auf Momentaufnahmen zur Berichtsausführung greifen Benutzer dagegen genau wie beim Zugriff auf Liveberichte von Ordnern aus zu. Bei den Momentaufnahmen zur Berichtsausführung erhalten Benutzer keinen grafischen Hinweis, dass es sich bei dem Bericht um eine Momentaufnahme handelt.  
  
 Wählen Sie die verwandte Option **Erstellen Sie eine Momentaufnahme des Berichts, wenn Sie auf dieser Seite auf die Schaltfläche 'Anwenden' klicken** , damit beim Klicken auf Anwenden eine Momentaufnahme des Berichts erstellt wird. Dadurch wird die Berichtsmomentaufnahme sofort erstellt und vor dem geplanten Anfangsdatum verfügbar gemacht.  
  
 **Timeout für Berichtsausführung**  
 Geben Sie eine bestimmte Anzahl von Sekunden als Timeoutwert für die Berichtsverarbeitung an. Wenn Sie die Standardeinstellung auswählen, wird die auf der Seite Siteeinstellungen angegebene Timeouteinstellung für diesen Bericht verwendet.  
  
 Dieser Wert gilt für die Berichtsverarbeitung auf einem Berichtsserver. Durch diesen Wert wird kein Timeout für die Datenverarbeitung auf dem Datenbankserver festgelegt, der die Daten für den Bericht zur Verfügung stellt. Wenn Sie diesen Wert festlegen, müssen Sie jedoch genügend Zeit sowohl für die Daten- als auch für die Berichtsverarbeitung zur Verfügung stellen. Die Zählung für die Berichtsverarbeitung beginnt mit der Auswahl des Berichts und endet mit dem Öffnen des Berichts.  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen von Berichtsverarbeitungseigenschaften](report-server/set-report-processing-properties.md)   
 [Zwischenspeichern von Berichten (SSRS)](report-server/caching-reports-ssrs.md)   
 [Erstellen, Ändern oder Löschen von Zeitplänen](subscriptions/create-modify-and-delete-schedules.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  