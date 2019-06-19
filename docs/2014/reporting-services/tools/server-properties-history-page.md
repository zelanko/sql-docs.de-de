---
title: Servereigenschaften (Seite „Verlauf“)|Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.history.f1
ms.assetid: be9d8018-a46f-4625-9ae1-138ebe6b38ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5ce48c964ec756668aa12566c494d9ae9a1e5372
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66099575"
---
# <a name="server-properties-history-page"></a>Servereigenschaften (Seite Verlauf)
  Verwenden Sie diese Seite als Standardwert für die Anzahl von Kopien der Berichtsverläufe, die Sie beibehalten möchten. Mithilfe eines Standardwertes werden erste Grenzwerte für den Berichtsverlauf für alle Berichte festgelegt. Sie können diese Werte für die jeweiligen Berichte anpassen.  
  
 Der Berichtsverlauf ist eine Auflistung von Berichtsmomentaufnahmen, die die zum Zeitpunkt der Erstellung der Momentaufnahme aktuellen Berichtsdaten und die Layouts enthalten. Mithilfe des Berichtsverlaufs können Sie die Kopie eines Berichts, so wie er zu einem bestimmten Zeitpunkt erstellt wurde, aufbewahren. Sie können den Berichtsverlauf für einzelne Berichte erstellen und verwalten, die auf einem Berichtsserver ausgeführt werden, der für den einheitlichen Modus oder den integrierten SharePoint-Modus konfiguriert ist.  
  
 Die Momentaufnahmen des Berichtsverlaufs werden in der Berichtsserverdatenbank gespeichert. Wenn Sie eine unbegrenzte Zahl von Momentaufnahmen speichern, müssen Sie regelmäßig die Größe der Datenbank überprüfen, um sicherzustellen, dass ihre Größe nicht allzu schnell wächst oder zu viel Speicherplatz belegt wird.  
  
 Öffnen Sie diese Seite, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] starten und eine Verbindung mit einer Berichtsserverinstanz herstellen. Klicken Sie mit der rechten Maustaste auf den Namen des Berichtsservers, und wählen Sie anschließend **Eigenschaften** aus. Klicken Sie auf **Verlauf** , um diese Seite zu öffnen.  
  
## <a name="options"></a>Optionen  
 **Beliebig viele Momentaufnahmen im Berichtsverlauf speichern**  
 Alle Berichtsverlaufs-Momentaufnahmen werden beibehalten. Sie müssen die Momentaufnahmen manuell löschen, um die Größe des Berichtsverlaufs zu verringern.  
  
 **Max. Anzahl von Kopien des Berichtsverlaufs**  
 Es wird eine festgelegte Anzahl von Berichtsverlaufs-Momentaufnahmen beibehalten. Wenn der Grenzwert erreicht ist, werden ältere Kopien aus dem Berichtsverlauf entfernt, um Platz für neue Kopien zu erhalten.  
  
 Wenn Sie den Berichtsverlauf zu einem späteren Zeitpunkt einschränken und der vorhandene Berichtsverlauf den angegebenen Grenzwert übersteigt, verringert der Berichtsserver den vorhandenen Berichtsverlauf auf den neuen Grenzwert. Die ältesten Berichtsmomentaufnahmen werden zuerst gelöscht. Falls der Berichtsverlauf leer ist oder unter dem Grenzwert liegt, werden neue Berichtsmomentaufnahmen hinzugefügt. Ist der Grenzwert erreicht, wird die älteste Momentaufnahme gelöscht, sobald eine neue Berichtsmomentaufnahme hinzugefügt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)  
  
  
