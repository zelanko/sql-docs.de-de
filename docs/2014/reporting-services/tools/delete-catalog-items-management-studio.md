---
title: Löschen von Katalogelementen (Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.deleteitems.f1
ms.assetid: b0599e01-6dc3-4484-80d4-022a412e0ebd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 089bd1fbfeaf86c2f5a96e2cfcf790a90431a452
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56036531"
---
# <a name="delete-catalog-items-management-studio"></a>Katalogelemente löschen (Management Studio)
  Verwenden Sie diese Seite, um freigegebene Zeitpläne und Rollendefinitionen zu löschen.  
  
 Wenn Sie einen freigegebenen Zeitplan löschen, der von mehreren Berichten und Abonnements verwendet wird, erstellt der Berichtsserver für Berichte und Abonnements, die vorher den freigegebenen Zeitplan verwendet haben, eigene Zeitpläne. Jeder dieser neuen Zeitpläne enthält das Datum, die Zeit und die Wiederholungsoption, die in dem freigegebenen Zeitplan angegeben wurden. Beachten Sie, dass [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] keine zentrale Verwaltung für einzelne Zeitpläne bereitstellt. Wenn Sie einen freigegebenen Zeitplan löschen, müssen Sie jetzt die Zeitplaninformationen für jedes einzelne Element verwalten. Bevor Sie einen freigegebenen Zeitplan löschen, verwenden Sie die [Seite Berichte](schedule-properties-reports-page.md) , um zu ermitteln, welche Berichte den freigegebenen Zeitplan gerade verwenden.  
  
 Von den Rollendefinitionen können Sie nur jene löschen, die aktuell nicht in einer Rollenzuweisung verwendet werden. Wenn Sie versuchen, eine Rolle zu löschen, die gerade verwendet wird, weist der Berichtsserver diesen Löschversuch ab und zeigt stattdessen eine Fehlermeldung an. Wenn die Seite eine einzelne Rollendefinition enthält, die aktuell nicht verwendet wird, wird diese gelöscht, sobald Sie auf **OK**klicken. Wenn diese Seite mehrere Rollen enthält, können Sie nicht auswählen, welche Rollen gelöscht und welche beibehalten werden sollen. Alle nicht verwendeten Rollendefinitionen werden gelöscht, wenn Sie auf **OK**klicken.  
  
 Einen Löschvorgang können Sie nicht rückgängig machen. Wenn Sie ein bereits gelöschtes Element wiederherstellen möchten, müssen Sie dieses entweder erneut erstellen oder eine Sicherungskopie der Berichtsserver-Datenbank wiederherstellen.  
  
## <a name="options"></a>Optionen  
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
  
## <a name="see-also"></a>Siehe auch  
 [Löschen eines Elements &#40;Management Studio&#41;](delete-an-item-management-studio.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Erstellen, Ändern oder Löschen von Zeitplänen](../subscriptions/create-modify-and-delete-schedules.md)  
  
  
