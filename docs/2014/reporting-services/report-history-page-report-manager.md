---
title: Melden Sie die Seite "Verlauf" (Berichts-Manager) | Microsoft-Dokumentation
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 0b0841e031ee1a98f4f678406f790996a709e90f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66104481"
---
# <a name="report-history-page-report-manager"></a>Berichtsverlauf (Seite, Berichts-Manager)

Mithilfe der Seite Berichtsverlauf können Sie die im Laufe der Zeit generierten und gespeicherten Berichtsmomentaufnahmen anzeigen. Abhängig von den für den Berichtsserver festgelegten Optionen enthält der Berichtsverlauf möglicherweise nur die neuesten Momentaufnahmen.  
  

Der Berichtsverlauf wird immer im Kontext des Berichts angezeigt, aus dem er stammt. Es ist nicht möglich, den Verlauf aller Berichte auf einem Berichtsserver zentral anzuzeigen.  
  
Wenn Sie den Berichtsverlauf generieren möchten, muss der Bericht unbeaufsichtigt ausgeführt werden können, d. h., er muss gespeicherte Anmeldeinformationen verwenden, und parametrisierte Berichte müssen Standardparameterwerte für alle Parameter enthalten. Der Berichtsverlauf kann manuell oder als geplante Operation generiert werden. Verlaufseigenschaften im Bericht bestimmen die Art und Weise, in der der Berichtsverlauf erstellt werden kann.  
  
Klicken Sie auf eine Momentaufnahme zum Berichtsverlauf, um diese anzuzeigen. Die im Berichtsverlauf angezeigten Momentaufnahmen unterscheiden sich nur durch das Datum und die Uhrzeit ihrer Erstellung. Es gibt keinen grafischen Hinweis, ob eine Momentaufnahme als Folge eines Zeitplans oder durch einen manuellen Vorgang generiert wurde.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgendes Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
### <a name="to-open-the-report-history-page"></a>So öffnen Sie die Seite 'Berichtsverlauf'  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie den Bericht, für den Sie Berichtsmomentaufnahmen anzeigen möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Berichtsverlauf anzeigen**.  
  
## <a name="options"></a>Optionen  
 **Löschen**  
 Klicken Sie auf diese Schaltfläche, um eine oder mehrere Momentaufnahmen zu löschen. Bevor Sie auf **Löschen**klicken, aktivieren Sie das Kontrollkästchen neben den zu löschenden Momentaufnahmen.  
  
 **Neue Momentaufnahme**  
 Klicken Sie auf diese Schaltfläche, um eine Momentaufnahme zum Berichtsverlauf hinzuzufügen. Diese Schaltfläche ist verfügbar, wenn Sie auf der Seite mit den Verlaufseigenschaften des Berichts die Option **Berichtsverlauf kann manuell erstellt werden** ausgewählt haben.  
  
 **Zuletzt ausgeführt**  
 Zeigt das Datum und die Uhrzeit der Erstellung der Momentaufnahme an. Klicken Sie auf eine Beschreibung, um eine bestimmten Momentaufnahme anzuzeigen.  
  
 **Größe**  
 Zeigt die Größe der Berichtsdefinition und der Daten im Bericht an. Dieser Wert gibt an, wie viel Speicherplatz in der Berichtsserver-Datenbank durch die Berichtsdefinition und Daten verwendet wird. Die Größe des dargestellten Berichts einschließlich der Formatierung ist tatsächlich höher. Die in Klammern angegebene Gesamtgröße enthält die Summe der Größe aller Momentaufnahmen im Berichtsverlauf des aktuellen Berichts.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen oder Löschen des Berichtsverlaufs &#40;Berichts-Manager&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md)   
 [Hinzufügen einer Momentaufnahme zum Berichtsverlauf &#40;Berichts-Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Allgemeine Eigenschaften (Seite) (Berichte, Berichts-Manager)](../../2014/reporting-services/general-properties-page-reports-report-manager.md)   
 [Berichts-Manager-F1-Hilfe](../../2014/reporting-services/report-manager-f1-help.md)   
 [Momentaufnahmeoptionen Eigenschaftenseite &#40;Berichts-Manager&#41;](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)