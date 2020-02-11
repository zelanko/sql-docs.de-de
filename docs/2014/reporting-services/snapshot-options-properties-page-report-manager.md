---
title: Eigenschaften Seite "Momentaufnahme Optionen" (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f6641f59-5267-4f57-8957-63b93d1a9679
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7a73f3be75a7f0cadf633943aeafffb7217d8e29
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101161"
---
# <a name="snapshot-options-properties-page-report-manager"></a>Momentaufnahmeoptionen (Eigenschaftenseite) (Berichts-Manager)
  Mithilfe der Eigenschaftenseite Momentaufnahmeoptionen können Sie das Hinzufügen von Berichtsmomentaufnahmen zum Berichtsverlauf planen und die Anzahl von Berichtsmomentaufnahmen begrenzen, die im Berichtsverlauf gespeichert werden.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], die von den-Editionen unterstützt werden, finden Sie unter [zusätzliche Datenbankdienste](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
### <a name="to-open-the-snapshot-options-properties-page-for-a-report"></a>So öffnen Sie die Eigenschaftenseite Momentaufnahmeoptionen für einen Bericht  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie Eigenschaften von Berichtsmomentaufnahmen konfigurieren möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für den Bericht geöffnet.  
  
4.  Wählen Sie die Registerkarte **Momentaufnahmeoptionen** aus.  
  
## <a name="options"></a>Tastatur  
 **"Berichtsverlauf" kann manuell erstellt werden**  
 Aktivieren Sie dieses Kontrollkästchen, um nach Bedarf dem Berichtsverlauf Momentaufnahmen hinzuzufügen. Wenn Sie dieses Kontrollkästchen aktivieren, wird die Schaltfläche **Neue Momentaufnahme** auf der Seite Verlauf angezeigt.  
  
 **Alle Momentaufnahmen zur Berichtsausführung im Verlauf speichern**  
 Aktivieren Sie dieses Kontrollkästchen, um eine Berichtsmomentaufnahme, die auf der Grundlage von Berichtsausführungseigenschaften generiert wird, in den Berichtsverlauf zu kopieren. Sie können Berichtsausführungseigenschaften festlegen, um einen Bericht aus einer generierten Momentaufnahme auszuführen. Wenn Sie diese Eigenschaft für den Berichtsverlauf festlegen, können Sie einen Datensatz mit allen im Laufe der Zeit generierten Berichtsmomentaufnahmen speichern, indem Sie die Kopien der Berichtsmomentaufnahmen im Berichtsverlauf platzieren.  
  
 **Folgenden Zeitplan verwenden, um Momentaufnahmen dem Berichtsverlauf hinzuzufügen**  
 Aktivieren Sie dieses Kontrollkästchen, um dem Berichtsverlauf Momentaufnahmen auf der Basis eines Zeitplans hinzuzufügen. Sie können einen nur für diesen Zweck verwendeten Zeitplan erstellen oder einen vordefinierten freigegebenen Zeitplan auswählen, falls ein Zeitplan mit den gewünschten Informationen verfügbar ist.  
  
 **Maximale Anzahl von Momentaufnahmen im Verlauf**  
 Wählen Sie eine der folgenden Optionen aus, um die Anzahl von Berichten zu steuern, die im Berichtsverlauf gespeichert werden. In jedem Bericht können andere Einstellungen für den Berichtsverlauf festgelegt sein.  
  
-   Wählen Sie die Option **Die Standardeinstellung verwenden** aus, um die Standardeinstellung zu übernehmen. Der Berichtsserveradministrator steuert eine Mastereinstellung für die Speicherung des Berichtsverlaufs. Bei Auswahl dieser Option wird die Anzahl von gespeicherten Momentaufnahmen durch diese Mastereinstellung ermittelt.  
  
-   Wählen Sie die Option **Beliebig viele Momentaufnahmen im Berichtsverlauf speichern** aus, um alle Momentaufnahmen zum Berichtsverlauf zu speichern. Sie müssen die Momentaufnahmen manuell löschen, um die Größe des Berichtsverlaufs zu verringern.  
  
-   Wählen Sie die Option **Max. Anzahl von Kopien des Berichtsverlaufs** aus, um eine bestimmte Anzahl von Momentaufnahmen zu speichern. Wenn der Grenzwert erreicht ist, werden ältere Kopien aus dem Berichtsverlauf entfernt, um Platz für neue Kopien zu erhalten.  
  
 Der Berichtsverlauf wird in der Berichtsserverdatenbank gespeichert. Wenn Sie umfangreiche oder sehr viele Berichte haben, deren Verlauf Sie speichern möchten, dann erwägen Sie, die Menge der Berichtsverläufe zu beschränken, damit die Speicherplatzanforderungen für die Berichtsserver-Datenbank nicht allzu hoch werden.  
  
 **Anwenden**  
 Klicken Sie auf diese Schaltfläche, um die Änderungen zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen einer Momentaufnahme zum Berichtsverlauf &#40;Berichts-Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Erstellen, Ändern und Löschen von Momentaufnahmen im Berichtsverlauf](report-server/create-modify-and-delete-snapshots-in-report-history.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
