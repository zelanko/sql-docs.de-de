---
title: Volltextkatalog-Eigenschaften (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: be73ed98700ef261ccee026469dddd22017998e0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779663"
---
# <a name="full-text-catalog-properties-general-page"></a>Volltextkatalog-Eigenschaften (Seite 'Allgemein')
  In diesem Abschnitt sind die auf der Seite **Allgemein** des Dialogfelds **Volltextkatalog-Eigenschaften** verfügbaren Optionen und ihre Funktionen aufgeführt.  
  
> [!NOTE]  
>  Im Zusammenhang mit [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] -Datenbanken ist ein Volltextkatalog ein logisches Konzept, das auf eine Gruppe von Volltextindizes verweist. Ein Volltextkatalog ist ein virtuelles Objekt und gehört keiner Dateigruppe an.  
  
## <a name="options"></a>Optionen  
  
### <a name="properties"></a>Eigenschaften  
 **Standardkatalog**  
 Zeigt an, ob es sich bei dem Katalog um den Standardkatalog der Datenbank handelt.  
  
 **Auffüllungsstatus**  
 Zeigt den Status des Katalogs an. Dabei sind folgende Werte möglich:  
  
-   **Im Leerlauf**  
  
-   **Durchforstung wird ausgeführt**  
  
-   **Angehalten**  
  
-   **Throttled**  
  
-   **Wiederherstellen von**  
  
-   **Herunterfahren**  
  
-   **Inkrementelles Auffüllen wird ausgeführt**  
  
-   **Index wird erstellt**  
  
-   **Datenträger ist voll-angehalten**  
  
-   **Change tracking**  
  
 **Elementanzahl**  
 Zeigt die Anzahl der Volltextelemente im Katalog an.  
  
 **Kataloggröße**  
 Zeigt die Größe des Volltextkatalogs in Megabyte an.  
  
 **Name**  
 Name des Volltextkatalogs.  
  
 **Unterscheidung nach Akzent**  
 Dient zum Anzeigen oder Ändern, ob bei dem Katalog eine Unterscheidung anhand von diakritischen Zeichen wie Tilde (**~**), Akut-Akzentzeichen (**´**) oder Umlaut (**¨**) erfolgt oder nicht. Gültige Werte sind:  
  
-   **Nein**  
  
-   **ja**  
  
-   Weitere Informationen zu diakritischen Zeichen, finden Sie unter [diakritischer](https://www.merriam-webster.com/dictionary/diacritic) im Nitsche-Webster Wörterbuch.  
  
 **Letzte Auffüllung am**  
 Zeigt das Datum an, an dem der Katalog zuletzt aufgefüllt wurde.  
  
 **Besitzer**  
 Der Besitzer des Volltextkatalogs.  
  
 **Anzahl eindeutiger Schlüssel**  
 Anzahl eindeutiger Wörter, aus denen der Volltextindex für den Katalog besteht.  
  
### <a name="catalog-action"></a>Katalogaktion  
  
|||  
|-|-|  
|**Keine**|Führt keinen der folgenden Vorgänge aus: **Katalog optimieren**, **Katalog neu erstellen**und **Katalog neu auffüllen** .|  
|**Katalog optimieren**|Optimiert die Speicherplatzausnutzung des Katalogs und verbessert die Abfrageleistung. Erhöht außerdem die Genauigkeit der Relevanzbewertung von Suchergebnissen.<br /><br /> Diese Aktion führt ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE aus.|  
|**Katalog neu erstellen**|Löscht den Volltextkatalog und erstellt ihn neu. Dieser Vorgang muss bei der Änderung einer grundlegenden Katalogeigenschaft, z. B. der Akzentunterscheidung, ausgeführt werden.<br /><br /> Damit die Neuerstellung erfolgreich ist, muss die Dateigruppe, in der sich der Volltextkatalog befindet, online oder les- und beschreibbar sein. Nach der Neuerstellung wird der Volltextindex neu aufgefüllt.<br /><br /> Diese Aktion führt ALTER FULLTEXT CATALOG *catalog_name* REBUILD aus.|  
|**Katalog neu auffüllen**|Aktualisiert den Katalog entsprechend den kürzlich vorgenommenen Datenänderungen. Diese Option hat keine Katalogausfallzeit zur Folge.|  
  
## <a name="see-also"></a>Siehe auch  
 [Auffüllen von Volltextindizes](../relational-databases/indexes/indexes.md)  
  
  
