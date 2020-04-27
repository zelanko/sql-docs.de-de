---
title: Voll Text Katalog-Eigenschaften (Seite "Allgemein") | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
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
 Zeigt den Status des Katalogs an. Mögliche Werte:  
  
-   **Idle**  
  
-   **Durchforstung wird ausgeführt**  
  
-   **Angehalten**  
  
-   **Gedrosselt**  
  
-   **Wiederherstellen**  
  
-   **Shutdown**  
  
-   **Inkrementelles Auffüllen wird ausgeführt**  
  
-   **Index wird erstellt**  
  
-   **Der Datenträger ist vollständig angehalten.**  
  
-   **Änderungs Nachverfolgung**  
  
 **Anzahl der Elemente**  
 Zeigt die Anzahl der Volltextelemente im Katalog an.  
  
 **Kataloggröße**  
 Zeigt die Größe des Volltextkatalogs in Megabyte an.  
  
 **Name**  
 Name des Volltextkatalogs.  
  
 **Unterscheidung nach Akzent**  
 Anzeigen oder ändern, ob der Katalog von diakritischen Zeichen unterschieden wird, z. b.**~** eine Tilde (), ein akritisches Akzentzeichen (.**) oder Umlaut ("**.**").** Gültige Werte sind:  
  
-   **Nein**  
  
-   **Ja**  
  
-   Informationen zu diakritischen Markierungen finden Sie unter [diakritische](https://www.merriam-webster.com/dictionary/diacritic) Zeichen im Merriam-Webster-Wörterbuch.  
  
 **Letzte Auffüllung am**  
 Zeigt das Datum an, an dem der Katalog zuletzt aufgefüllt wurde.  
  
 **Besitzer**  
 Der Besitzer des Volltextkatalogs.  
  
 **Anzahl eindeutiger Schlüssel**  
 Anzahl eindeutiger Wörter, aus denen der Volltextindex für den Katalog besteht.  
  
### <a name="catalog-action"></a>Katalogaktion  
  
|||  
|-|-|  
|**None**|Führt keinen der folgenden Vorgänge aus: **Katalog optimieren**, **Katalog neu erstellen**und **Katalog neu auffüllen** .|  
|**Katalog optimieren**|Optimiert die Speicherplatzausnutzung des Katalogs und verbessert die Abfrageleistung. Erhöht außerdem die Genauigkeit der Relevanzbewertung von Suchergebnissen.<br /><br /> Diese Aktion führt ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE aus.|  
|**Katalog neu erstellen**|Löscht den Volltextkatalog und erstellt ihn neu. Dieser Vorgang muss bei der Änderung einer grundlegenden Katalogeigenschaft, z. B. der Akzentunterscheidung, ausgeführt werden.<br /><br /> Damit die Neuerstellung erfolgreich ist, muss die Dateigruppe, in der sich der Volltextkatalog befindet, online oder les- und beschreibbar sein. Nach der Neuerstellung wird der Volltextindex neu aufgefüllt.<br /><br /> Diese Aktion führt ALTER FULLTEXT CATALOG *catalog_name* REBUILD aus.|  
|**Katalog neu auffüllen**|Aktualisiert den Katalog entsprechend den kürzlich vorgenommenen Datenänderungen. Diese Option hat keine Katalogausfallzeit zur Folge.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auffüllen von Volltextindizes](../relational-databases/indexes/indexes.md)  
  
  
