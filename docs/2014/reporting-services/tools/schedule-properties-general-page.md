---
title: Zeitplaneigenschaften (Allgemeine Seite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.general.f1
ms.assetid: 20e43966-6caf-4972-a2e2-0d9131ac8f51
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98d013126fe1db1b8101d5ae451f658546f6d1f9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099742"
---
# <a name="schedule-properties-general-page"></a>Zeitplaneigenschaften (Registerkarte Allgemein)
  Auf dieser Seite können Sie einen freigegebenen Zeitplan anzeigen oder ändern. Feigegebene Zeitpläne können anstelle berichts- oder abonnementspezifischer Zeitpläne verwendet werden. Änderungen am Zeitplan werden übernommen, nachdem Sie den Zeitplan gespeichert haben. Die Bearbeitung eines Zeitplans hat keine Auswirkungen auf Aufträge, die gerade ausgeführt werden. Wenn Sie einen Zeitplan bearbeiten, der gerade verwendet wird, wird allen aktuell verarbeiteten Berichten und Abonnements, die durch den Zeitplan ausgelöst wurden, die Fertigstellung ermöglicht.  
  
 Nicht alle Kombinationen der Häufigkeit können in einem einzelnen Zeitplan unterstützt werden. Wenn ein Bericht z. B. um 00:00 Uhr und um 16:00 Uhr an jedem Freitag ausgeführt werden soll, müssen Sie zwei Tageszeitpläne erstellen, in denen der Freitag als Ausführungstag angegeben ist. Der erste Zeitplan hat eine Startzeit von 00:00 Uhr, und für den zweiten ist eine Startzeit von 16:00 Uhr festgelegt.  
  
 Die Verarbeitung von Zeitplänen basiert auf der Ortszeit des Berichtsservers, auf dem der Zeitplan gehostet und verarbeitet wird.  
  
 Um diese Seite zu öffnen, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten Sie, stellen eine Verbindung mit einem Berichts Server her, öffnen Sie den Ordner frei **gegebene Zeitpläne** , klicken mit der rechten Maustaste auf einen freigegebenen Zeitplan, **und wählen Sie**  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar, und diese Seite wird nicht angezeigt, wenn Sie eine Edition ausführen, die nicht über diese Funktion verfügt. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2012-Editionen unterstützte Funktionen](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Gibt den Namen des freigegebenen Zeitplans an.  
  
 **Diesen Zeitplan ausführen ab**  
 Gibt ein Startdatum für diesen Zeitplan an.  
  
 **Dieser Zeitplan endet am**  
 Gibt ein Ablaufdatum für diesen Zeitplan an.  
  
 **Typ**  
 Gibt an, ob die Wiederholungsoption hauptsächlich auf Stunden, Tagen, Wochen oder Monaten basiert oder nur einmal ausgeführt wird.  
  
 **Stunde (Serienmuster)**  
 Gibt die Optionen zum Ausführen eines geplanten Vorgangs in Intervallen von einer Stunde an (z. B., dass ein Bericht alle 6 Stunden ausgeführt wird). Das Intervall kann in Stunden und Minuten angegeben werden.  
  
 **Tag (Serienmuster)**  
 Gibt die Optionen zum Ausführen eines geplanten Vorgangs in Intervallen von Tagen an (z. B., dass ein Bericht alle 2 Tage ausgeführt wird). Sie können das Intervall in Tagen und mit der Stunde und Minute der Ausführung des Zeitplans angeben.  
  
 **Woche (Serienmuster)**  
 Gibt die Optionen zum Ausführen eines geplanten Vorgangs in Intervallen von einer Woche oder gemäß einem zu wiederholenden Muster an, das auf Wochenangaben basiert (z. B., dass ein Bericht jede zweite Woche ausgeführt wird). Sie können bei einem wöchentlichen Zeitplan den Tag, die Stunde und die Minute für die Ausführung des Zeitplans angeben.  
  
 **Monat (Serienmuster)**  
 Gibt die Optionen zum Ausführen eines geplanten Vorgangs in Intervallen von einem Monat oder gemäß einem zu wiederholenden Muster an, das auf Monatsangaben basiert. Sie können bei einem monatlichen Zeitplan den Tag, die Stunde und die Minute für die Ausführung des Zeitplans angeben. Sie können im Zeitplan bestimmte Monate auslassen.  
  
 **Einmal**  
 Gibt einen Zeitplan an, der nur einmal an einem bestimmten Datum und zu einer bestimmten Uhrzeit ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Erstellen, Ändern oder Löschen von Zeitplänen](../subscriptions/create-modify-and-delete-schedules.md)   
 [Zeitpläne](../subscriptions/schedules.md)  
  
  
