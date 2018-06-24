---
title: Zwischenspeichern von freigegebenen Datasets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2d8c81a-da1e-4a8a-9845-fff9a0903d24
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: af79d1381b6a2d5fc531ad5d0bb4ff7694fb12d2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056641"
---
# <a name="cache-a-shared-dataset"></a>Zwischenspeichern eines freigegebenen Datasets
  Eine Möglichkeit, die Leistung zu verbessern, ist die Konfiguration von Zwischenspeichereigenschaften für ein freigegebenes Dataset. Wenn ein freigegebenes Dataset zwischengespeichert wird, wird eine Kopie der Abfrageergebnisse für einen angegebenen Zeitraum gespeichert. Der erste Benutzer, der einen Bericht anfordert, der das freigegebene Dataset verwendet, muss auf die Abfrageergebnisse und alle Verarbeitungschritte warten, bevor er den bericht anzeigen kann. Nachfolgende Benutzer, die den Bericht innerhalb des Zeitraums der Zwischenspeicherung anfordern, erfahren eine verbesserte Leistung, da die Abfrage und die Verarbeitung bereits durchgeführt wurden. Sie können auch einen Cacheaktualisierungsplan angeben, um die Abfrage auszuführen und die Ergebnisse bis zur angegebenen Ablaufzeit für den Cache zwischenzuspeichern.  
  
 Benutzer, die Berichte auf Grundlage eines freigegebenen Datasets oder eines Cacheaktualisierungsplans durchführen, erstellen den Abfragezwischenspeicher; in beiden Fällen ist der Zwischenspeicher auf der Grundlage der Optionen für den Zwischenspeicherablauf verfügbar.  
  
 Es gibt Einschränkungen hinsichtlich der Arten freigegebener Datasets, die Sie zwischenspeichern können. Beispiel: Die Abfrageergebnisse können nicht zwischengespeichert werden, wenn die Daten je nach Benutzeridentität variieren oder wenn Daten mithilfe des Sicherheitstokens des Benutzers abgerufen werden, der den Bericht anfordert. Weitere Informationen finden Sie unter [Zwischenspeichern von freigegebenen Datasets (SSRS)](cache-shared-datasets-ssrs.md) und [Zwischenspeichern von Berichten (SSRS)](caching-reports-ssrs.md).  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a>So planen Sie den Ablauf eines zwischengespeicherten Berichts  
  
1.  Starten Sie [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Navigieren Sie im Berichts-Manager zu dem freigegebenen Dataset, für das Sie Zwischenspeichereigenschaften festlegen möchten. Zeigen Sie auf das Element, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**.  
  
4.  Klicken Sie im linken Bereich auf die Registerkarte **Zwischenspeichern**.  
  
    > [!NOTE]  
    >  Wenn Sie die Fehlermeldung **Die für die Ausführung des freigegebenen Datasets verwendeten Anmeldeinformationen sind nicht gespeichert**sehen, wird die Option für die Zwischenspeicherung freigegebener Datasets deaktiviert. Sie müssen die Datenquelle ändern, damit Anmeldeinformationen gespeichert werden oder das freigegebene Dataset ändern, damit es eine andere Datenquelle verwendet, die Anmeldeinformationen speichert.  
  
5.  Wählen Sie **Freigegebenes Dataset zwischenspeichern**aus.  
  
6.  Wählen Sie die Option, nach der der Zwischenspeicher nach 30 Minuten abläuft. Sie können auch wählen, dass der Zwischenspeicher nach einem bestimmten Zeitplan abläuft.  
  
7.  Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von freigegebenen Datasets](../report-data/manage-shared-datasets.md)  
  
  