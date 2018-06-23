---
title: Volltextkatalog-Eigenschaften (Seite Allgemein) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fc774b0dfd87ae4f63e9332dd6813d92f79e4a5c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159827"
---
# <a name="full-text-catalog-properties-general-page"></a>Volltextkatalog-Eigenschaften (Seite 'Allgemein')
  In diesem Abschnitt sind die auf der Seite **Allgemein** des Dialogfelds **Volltextkatalog-Eigenschaften** verfügbaren Optionen und ihre Funktionen aufgeführt.  
  
> [!NOTE]  
>  Für [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Datenbanken ein Volltextkatalog ist ein logisches Konzept, das auf eine Gruppe von Volltextindizes verweist. Ein Volltextkatalog ist ein virtuelles Objekt und gehört keiner Dateigruppe an.  
  
## <a name="options"></a>Tastatur  
  
### <a name="properties"></a>Eigenschaften  
 **Standardkatalog**  
 Zeigt an, ob es sich bei dem Katalog um den Standardkatalog der Datenbank handelt.  
  
 **Auffüllungsstatus**  
 Zeigt den Status des Katalogs an. Folgende Werte sind möglich:  
  
-   **Im Leerlauf**  
  
-   **Durchforstung wird ausgeführt**  
  
-   **Angehalten**  
  
-   **Gedrosselt**  
  
-   **Wiederherstellen von**  
  
-   **Herunterfahren**  
  
-   **Inkrementelles Auffüllen wird ausgeführt**  
  
-   **Index wird erstellt**  
  
-   **Der Datenträger ist voll, angehalten**  
  
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
  
-   Informationen zu diakritischen Zeichen finden Sie unter [diakritisches](http://go.microsoft.com/fwlink/?LinkId=154091) in der MSN Encarta-Enzyklopädie.  
  
 **Datum der letzten Auffüllung**  
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
  
  