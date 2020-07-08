---
title: Auftragsaktivitätsmonitor (Filtereinstellungen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.jobactivitymon.filter.f1
ms.assetid: 89cb0055-5262-447f-8464-7203d4caba78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d143c4c52c122c159e7c80dd58d8cee847849360
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85666935"
---
# <a name="job-activity-monitor-filter-settings"></a>Auftragsaktivitätsmonitor (Filtereinstellungen)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Mithilfe dieser Seite können Sie die Anzahl der eingeblendeten Zeilen im Auftragsaktivitätsmonitor verringern. Geben Sie die Kriterien in die verfügbaren Felder ein, damit nur die Zeilen angezeigt werden, die den festgelegten Werten entsprechen. Einige der Felder, z. B. **Status** oder **Blockierungstyp** , bieten eine vorgegebene Anzahl von möglichen Werten, die in einer Dropdownliste verfügbar sind. Andere, z. B. **Anwendung** , ermöglichen die Eingabe beliebiger Werte in beliebiger Anzahl in Form einer Liste mit durch Trennzeichen getrennten Angaben. Symbole auf der Symbolleiste ermöglichen das Sortieren der verfügbaren Felder nach Kategorie oder alphabetisch. Klicken Sie auf die Kriterien, um eine kurze Beschreibung zu ihnen anzuzeigen.  
  
 Geben Sie zum Filtern des Auftragsaktivitätsmonitors alle gewünschten Filterkriterien an, klicken Sie auf **Filter anwenden**, und dann auf **OK**.  
  
## <a name="all-jobs"></a>Alle Aufträge  
 Diese Gruppe von Filterkriterien ist beim Filtern des Auftragsaktivitätsmonitors verfügbar.  
  
 **Name**  
 Filtert Aufträge nach Namen.  
  
 **Nächste Ausführung**  
 Filtert nach dem Datum der nächsten geplanten Ausführung.  
  
 **Ausführbar**  
 Zeigt Aufträge an, die ausgeführt werden können oder nicht ausgeführt werden können. Wählen Sie **Ja** aus, um nur Aufträge anzuzeigen, die ausgeführt werden können. Wählen Sie **Nein** aus, um nur Aufträge anzuzeigen, die nicht ausgeführt werden können, oder wählen Sie **Alle** aus, um sowohl Aufträge anzuzeigen, die ausgeführt werden können, als auch solche, die nicht ausgeführt werden können.  
  
 **Zuletzt ausgeführt**  
 Filtert nach dem Datum der letzten Ausführung.  
  
 **Ergebnis der letzten Ausführung**  
 Filtert Aufträge nach dem Status, der nach der letzten Ausführung gegeben war.  
  
 **Aktiviert**  
 Zeigt nur aktivierte bzw. nicht aktivierte Aufträge an.  
  
 **Kategorie**  
 Filtert Aufträge nach der Auftragskategorie.  
  
 **Geplant**  
 Zeigt alle Aufträge mit bzw. ohne Zeitpläne an.  
  
 **Status**  
 Filtert die Aufträge nach Status.  
  
## <a name="description-area"></a>Beschreibungsbereich  
 **Beschreibungsfeld**  
 Dieses unbenannte Feld stellt eine Kurzbeschreibung der Kriterien bereit, die ausgewählt wurden.  
  
 **Filter anwenden**  
 Klicken Sie auf **Filter anwenden**, und klicken Sie dann auf **OK**, um den Filter anzuwenden. Wenn Sie die Filtereinstellungen im Dialogfeld **Filtereinstellungen** beibehalten, aber nicht anwenden möchten, deaktivieren Sie **Filter anwenden**, und klicken Sie auf **OK**, um alle Zeilen anzuzeigen.  
  
 **Clear**  
 Setzt die Filtereinstellungen auf die Standardeinstellungen zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Auftragsaktivität](../../ssms/agent/monitor-job-activity.md)  
  
  
