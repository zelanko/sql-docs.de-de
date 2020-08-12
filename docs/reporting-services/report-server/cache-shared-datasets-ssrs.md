---
title: Zwischenspeichern von freigegebenen Datasets | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über das Zwischenspeichern von freigegebenen Datasets im SQL Server Berichts-Manager, durch das die Antwortzeit verbessert wird und konsistente Daten für Berichte bereitgestellt werden, die das betreffende Dataset verwenden.
ms.date: 05/14/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
ms.assetid: 4acb1bbe-1c04-4979-b893-dc1b1c5039b6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0b256074f441dd2160298fe7840af4f6fca13eaf
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545599"
---
# <a name="cache-shared-datasets-ssrs"></a>Zwischenspeichern von freigegebenen Datasets (SSRS)
  Abfrageergebnisse für ein freigegebenes Dataset können in einen Cache kopiert werden, um konsistente Daten für mehrere Berichte bereitzustellen und die Antwortzeit für die Datasetabfrage zu verbessern. Freigegebene Datasets können ähnlich wie Berichte so konfiguriert werden, dass sie bei der erstmaligen Verwendung oder nach einem angegebenen Zeitplan zwischengespeichert werden.  
  
 Ein freigegebenes Dataset kann in mehreren Berichten enthalten oder Teil einer Komponentendefinition sein. Indem Sie das freigegebene Dataset zwischenspeichern, stellen Sie für alle Berichte, die das Dataset verwenden, konsistente Daten bereit und reduzieren gleichzeitig die Anzahl der in der externen Datenquelle ausgeführten Datasetabfragen.  
  
 Die folgende Liste enthält Beispiele dafür, wann ein freigegebenes Dataset zwischengespeichert werden sollte:  
  
-   Die Ausführung der Abfrage nimmt viel Zeit in Anspruch.  
  
-   Die Abfrage verwendet Parameter, die Anzahl der Parameterkombinationen ist jedoch meist klein. Durch jede Kombination werden zwischengespeicherte Abfrageergebnisse generiert.  
  
-   Die Abfrage wird täglich, wöchentlich oder monatlich zu festen Zeiten ausgeführt.  
  
-   Die Abfrage wird in Reaktion auf einen Verweis auf ein freigegebenes Dataset in einem Bericht ausgeführt, der per E-Mail übermittelt wird, und es wird erwartet, dass eine große Anzahl von Personen in kurzer Zeit auf den Link klicken wird.  
  
 Die folgende Liste enthält Beispiele dafür, wann ein freigegebenes Dataset nicht zwischengespeichert werden sollte:  
  
-   Die Abfrageergebnisse müssen immer die neuesten Daten enthalten.  
  
-   Die Abfrage wird schnell ausgeführt.  
  
-   Die Abfrage wird selten ausgeführt.  
  
-   Die Abfrage verwendet Parameter, die Anzahl der Parameterkombinationen ist groß, und keine Kombination ist wahrscheinlicher als eine andere.  
  
-   Für die Datenquelle, auf der das freigegebene Dataset basiert, werden Anmeldeinformationen angefordert oder integrierte Windows-Anmeldeinformationen verwendet.  
  
-   Der Filter für das freigegebene Dataset oder die Abfrage enthält einen Ausdruck mit einem Verweis auf die globale User-Auflistung.  
  
 Wenn ein Benutzer Berichtsparameterwerte auswählt, die sich von den Standardwerten unterscheiden, die für das zwischengespeicherte Resultset angegeben wurden, wird die Datasetabfrage aktiv ausgeführt, und die zwischengespeicherten Ergebnisse werden nicht für diese Abfrage verwendet.  
  
## <a name="caching-shared-datasets"></a>Zwischenspeichern freigegebener Datasets  
 Um das Zwischenspeichern für ein freigegebenes Dataset zu aktivieren, müssen Sie die Cacheoption für das freigegebene Dataset auswählen. Nachdem das Zwischenspeichern aktiviert wurde, werden die Abfrageergebnisse für ein freigegebenes Dataset bei der ersten Verwendung in den Cache kopiert. Wenn das freigegebene Dataset über Parameter verfügt, wird durch jede Parameterkombination ein neuer Eintrag im Cache erstellt.  
  
 Während die Abfrageergebnisse für eine bestimmte Parameterkombination im Cache enthalten sind, verwendet jeder Bericht, dessen Verarbeitung gestartet wird und der einen Verweis auf das freigegebene Dataset mit den jeweiligen Parameterwerten enthält, die zwischengespeicherten Daten.  
  
 Sie können angeben, wie lange die Daten im Cache beibehalten werden, bevor sie ungültig werden. Weitere Informationen finden Sie unter [Arbeiten mit freigegebenen Datasets](../../reporting-services/work-with-shared-datasets-web-portal.md).  
  
## <a name="preloading-the-cache"></a>Vorabladen des Caches  
 Sie können den Cache vorab laden, indem Sie einen Cacheaktualisierungsplan erstellen. Mit einem Aktualisierungsplan können Sie unter Verwendung eines elementspezifischen Zeitplans oder eines freigegebenen Zeitplans angeben, wie oft der Cache aktualisiert werden soll. Damit nicht mehrere Cacheeinträge für das gleiche Element gespeichert werden, sollte der angegebene Zeitplan genügend Zeit zur Abfrageverarbeitung in der externen Datenquelle vorsehen. Wenn die Abfrageausführung z. B. 20 Minuten benötigt, sollte der Aktualisierungszeitplan größer als 20 Minuten sein. Weitere Informationen finden Sie unter [Schedules](../../reporting-services/subscriptions/schedules.md).  
  
 Beim Erstellen eines Cacheaktualisierungsplans für ein freigegebenes Dataset gelten die folgenden Bedingungen.  
  
-   Für das freigegebene Dataset muss das Zwischenspeichern aktiviert sein.  
  
-   Von der freigegebenen Datenquelle, von der das freigegebene Dataset abhängig ist, dürfen keine Anmeldeinformationen angefordert bzw. integrierte Windows-Anmeldeinformationen verwendet werden.  
  
-   Wenn das freigegebene Dataset über Parameter verfügt, müssen Sie statische Standardwerte für alle Parameter angeben, die nicht als schreibgeschützt gekennzeichnet sind. Schreibgeschützte Parameter verwenden immer den Standardwert. Um ein freigegebenes Dataset für mehrere Parameterkombinationen zwischenzuspeichern, müssen Sie einen separaten Cacheaktualisierungsplan für jede Kombination von Werten erstellen. Parameter können keine Verweise auf andere Datasets enthalten.  
  
-   Jeder Cacheaktualisierungsplan ist nur einem freigegebenen Dataset oder Bericht zugeordnet.  
  
-   Sie benötigen die ReadPolicy-Berechtigung und UpdatePolicy-Berechtigung für das freigegebene Dataset.  
  
 Cacheaktualisierungspläne können sowohl auf freigegebene Datasets als auch auf Berichte angewendet werden. Weitere Informationen finden Sie unter [Zwischenspeichern von Berichten &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)bestand darin die einzige Möglichkeit, den Cache vorab zu laden.  
  
## <a name="conditions-that-cause-cache-expiration"></a>Bedingungen, die zum Ablaufen des Caches führen  
 Die folgenden Bedingungen können bewirken, dass ein Cache für ein freigegebenes Dataset ungültig wird.  
  
-   Eine Zeitplanbedingung läuft ab. Das Timeout für den Cache oder die Ablaufzeit wird erreicht.  
  
-   Ein freigegebener Zeitplan wird gelöscht.  
  
-   Änderungen an einem freigegebenen Zeitplan. Freigegebene Zeitpläne können angehalten werden, was sich auch auf die Ablaufzeit eines Caches auswirkt.  
  
-   Die Abfragedefinition für das freigegebene Dataset wird geändert.  
  
-   Die Anmeldeinformationen für die freigegebene Datenquelle, von der das freigegebene Dataset abhängig ist, werden geändert.  
  
-   Die Cacheoptionen für das freigegebene Dataset werden geändert.  
  
-   Die Standardwerte für schreibgeschützte Parameter für das freigegebene Dataset werden geändert.  
  
-   Die Filter, die Teil der Definition für das freigegebene Dataset sind, werden geändert.  
  
-   Das freigegebene Dataset wird vom Berichtsserver gelöscht. Wenn ein freigegebenes Dataset gelöscht wird, werden zugeordnete zwischengespeicherte Kopien und Cacheaktualisierungspläne ebenfalls gelöscht.  
  
 Aktualisierungen an Cacheaktualisierungsplänen für freigegebene Datasets haben keinen Einfluss auf Berichte, die bereits verarbeitet werden. Aktualisierungen an einem Cacheaktualisierungsplan wirken sich nur auf zukünftig gestartete Berichte aus, die auf das freigegebene Dataset verweisen.  
  
## <a name="see-also"></a>Weitere Informationen
  
 [Verwalten von freigegebenen Datasets](../../reporting-services/report-data/manage-shared-datasets.md)  
  