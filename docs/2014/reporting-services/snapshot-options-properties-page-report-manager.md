---
title: Momentaufnahmeoptionen (Eigenschaftenseite) (Berichts-Manager) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f6641f59-5267-4f57-8957-63b93d1a9679
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: b89de53a1e17413f8ebe6869122ea9d4b61af6dc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059519"
---
# <a name="snapshot-options-properties-page-report-manager"></a>Momentaufnahmeoptionen (Eigenschaftenseite) (Berichts-Manager)
  Mithilfe der Eigenschaftenseite Momentaufnahmeoptionen können Sie das Hinzufügen von Berichtsmomentaufnahmen zum Berichtsverlauf planen und die Anzahl von Berichtsmomentaufnahmen begrenzen, die im Berichtsverlauf gespeichert werden.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen unterstützt werden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], finden Sie unter [zusätzliche Datenbankdienste](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
### <a name="to-open-the-snapshot-options-properties-page-for-a-report"></a>So öffnen Sie die Eigenschaftenseite Momentaufnahmeoptionen für einen Bericht  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie Eigenschaften von Berichtsmomentaufnahmen konfigurieren möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für den Bericht geöffnet.  
  
4.  Wählen Sie die Registerkarte **Momentaufnahmeoptionen** aus.  
  
## <a name="options"></a>Tastatur  
 **Berichtsverlauf kann manuell erstellt werden**  
 Aktivieren Sie dieses Kontrollkästchen, um nach Bedarf dem Berichtsverlauf Momentaufnahmen hinzuzufügen. Wenn Sie dieses Kontrollkästchen aktivieren, wird die Schaltfläche **Neue Momentaufnahme** auf der Seite Verlauf angezeigt.  
  
 **Alle berichtsausführungs-Momentaufnahmen im Berichtsverlauf speichern**  
 Aktivieren Sie dieses Kontrollkästchen, um eine Berichtsmomentaufnahme, die auf der Grundlage von Berichtsausführungseigenschaften generiert wird, in den Berichtsverlauf zu kopieren. Sie können Berichtsausführungseigenschaften festlegen, um einen Bericht aus einer generierten Momentaufnahme auszuführen. Wenn Sie diese Eigenschaft für den Berichtsverlauf festlegen, können Sie einen Datensatz mit allen im Laufe der Zeit generierten Berichtsmomentaufnahmen speichern, indem Sie die Kopien der Berichtsmomentaufnahmen im Berichtsverlauf platzieren.  
  
 **Verwenden Sie folgenden Zeitplan, um Momentaufnahmen dem Berichtsverlauf hinzuzufügen**  
 Aktivieren Sie dieses Kontrollkästchen, um dem Berichtsverlauf Momentaufnahmen auf der Basis eines Zeitplans hinzuzufügen. Sie können einen nur für diesen Zweck verwendeten Zeitplan erstellen oder einen vordefinierten freigegebenen Zeitplan auswählen, falls ein Zeitplan mit den gewünschten Informationen verfügbar ist.  
  
 **Wählen Sie die Anzahl von Momentaufnahmen im Verlauf**  
 Wählen Sie eine der folgenden Optionen aus, um die Anzahl von Berichten zu steuern, die im Berichtsverlauf gespeichert werden. In jedem Bericht können andere Einstellungen für den Berichtsverlauf festgelegt sein.  
  
-   Wählen Sie die Option **Die Standardeinstellung verwenden** aus, um die Standardeinstellung zu übernehmen. Der Berichtsserveradministrator steuert eine Mastereinstellung für die Speicherung des Berichtsverlaufs. Bei Auswahl dieser Option wird die Anzahl von gespeicherten Momentaufnahmen durch diese Mastereinstellung ermittelt.  
  
-   Wählen Sie die Option **Beliebig viele Momentaufnahmen im Berichtsverlauf speichern** aus, um alle Momentaufnahmen zum Berichtsverlauf zu speichern. Sie müssen die Momentaufnahmen manuell löschen, um die Größe des Berichtsverlaufs zu verringern.  
  
-   Wählen Sie die Option **Max. Anzahl von Kopien des Berichtsverlaufs** aus, um eine bestimmte Anzahl von Momentaufnahmen zu speichern. Wenn der Grenzwert erreicht ist, werden ältere Kopien aus dem Berichtsverlauf entfernt, um Platz für neue Kopien zu erhalten.  
  
 Der Berichtsverlauf wird in der Berichtsserverdatenbank gespeichert. Wenn Sie umfangreiche oder sehr viele Berichte haben, deren Verlauf Sie speichern möchten, dann erwägen Sie, die Menge der Berichtsverläufe zu beschränken, damit die Speicherplatzanforderungen für die Berichtsserver-Datenbank nicht allzu hoch werden.  
  
 **Anwenden**  
 Klicken Sie auf diese Schaltfläche, um die Änderungen zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen einer Momentaufnahme zum Berichtsverlauf &#40;Berichts-Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Berichts-Manager &#40;SSRS im einheitlichen Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Erstellen, ändern und Löschen von Momentaufnahmen im Berichtsverlauf](report-server/create-modify-and-delete-snapshots-in-report-history.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  