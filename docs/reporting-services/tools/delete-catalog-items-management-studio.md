---
title: Löschen von Katalogelementen (Management Studio) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.deleteitems.f1
ms.assetid: b0599e01-6dc3-4484-80d4-022a412e0ebd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b8576a1946368c7adc1a32aa66ce44e28603616a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65573937"
---
# <a name="delete-catalog-items-management-studio"></a>Katalogelemente löschen (Management Studio)
  Verwenden Sie diese Seite, um freigegebene Zeitpläne und Rollendefinitionen zu löschen.  
  
 Wenn Sie einen freigegebenen Zeitplan löschen, der von mehreren Berichten und Abonnements verwendet wird, erstellt der Berichtsserver für Berichte und Abonnements, die vorher den freigegebenen Zeitplan verwendet haben, eigene Zeitpläne. Jeder dieser neuen Zeitpläne enthält das Datum, die Zeit und die Wiederholungsoption, die in dem freigegebenen Zeitplan angegeben wurden. Beachten Sie, dass [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] keine zentrale Verwaltung für einzelne Zeitpläne bereitstellt. Wenn Sie einen freigegebenen Zeitplan löschen, müssen Sie jetzt die Zeitplaninformationen für jedes einzelne Element verwalten. Bevor Sie einen freigegebenen Zeitplan löschen, verwenden Sie die [Seite Berichte](../../reporting-services/tools/schedule-properties-reports-page.md) , um zu ermitteln, welche Berichte den freigegebenen Zeitplan gerade verwenden.  
  
 Von den Rollendefinitionen können Sie nur jene löschen, die aktuell nicht in einer Rollenzuweisung verwendet werden. Wenn Sie versuchen, eine Rolle zu löschen, die gerade verwendet wird, weist der Berichtsserver diesen Löschversuch ab und zeigt stattdessen eine Fehlermeldung an. Wenn die Seite eine einzelne Rollendefinition enthält, die aktuell nicht verwendet wird, wird diese gelöscht, sobald Sie auf **OK**klicken. Wenn diese Seite mehrere Rollen enthält, können Sie nicht auswählen, welche Rollen gelöscht und welche beibehalten werden sollen. Alle nicht verwendeten Rollendefinitionen werden gelöscht, wenn Sie auf **OK**klicken.  
  
 Einen Löschvorgang können Sie nicht rückgängig machen. Wenn Sie ein bereits gelöschtes Element wiederherstellen möchten, müssen Sie dieses entweder erneut erstellen oder eine Sicherungskopie der Berichtsserver-Datenbank wiederherstellen.  
  
## <a name="options"></a>enthalten  
 **Name**  
 Gibt den Namen des Elements an, das Sie gerade löschen.  
  
 **Typ**  
 Zeigt den Typ des Elements an, das Sie gerade löschen.  
  
 **Besitzer**  
 Zeigt den Namen des Besitzers an. In den meisten Fällen lautet dieser System.  
  
 **Status**  
 Zeigt die Fortschrittsinformationen für einen Löschvorgang an.  
  
 **Fehler**  
 Zeigt einen Fehlercode an, wenn beim Löschen eines Elements ein Fehler auftritt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Löschen eines Elements &#40;Management Studio&#41;](../../reporting-services/tools/delete-an-item-management-studio.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Erstellen, Ändern oder Löschen von Zeitplänen](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md)  
  
  
