---
title: Angeben von Datentyp und Inhaltstyp (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 72484d27-3ef1-4f16-813c-2f43231fc2da
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 583a6fda2dbb4698405a3d69f33955531b3c1c10
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62720054"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a>Angeben des Datentyps und des Inhaltstyps (Lernprogramm zu Data Mining-Grundlagen)
  Nachdem Sie die Spalten zum Erstellen der Struktur und zum Trainieren der Modelle ausgewählt haben, können Sie erforderliche Änderungen an den Standarddaten und Inhaltstypen vornehmen, die vom Assistenten festgelegt wurden.  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a>Überprüfen und Ändern von Inhaltstyp und Datentyp für jede Spalte  
  
1.  Klicken Sie auf der Seite **Inhalt und Datentyp der Spalten angeben** auf **Erkennen** , um einen Algorithmus zur Bestimmung der Standarddaten und Inhaltstypen für die einzelnen Spalten auszuführen.  
  
2.  Überprüfen die Einträge in den Spalten **Inhaltstyp** und **Datentyp** . Ändern Sie die Einträge bei Bedarf, um sicherzustellen, dass die Einstellungen den in der folgenden Tabelle aufgeführten Einstellungen entsprechen.  
  
     Der Assistent erkennt normalerweise Zahlen und weist einen entsprechenden numerischen Datentyp zu. In vielen Szenarien bietet es sich jedoch an, eine Zahl stattdessen als Text zu behandeln. Beispielsweise sollte **GeographyKey** als Text behandelt werden, da mathematische Operationen sich für diese ID nicht eignen.  
  
    |Column|Inhaltstyp|Datentyp|  
    |------------|------------------|---------------|  
    |**Address Line1**|**Discrete**|**Text**|  
    |**Address Line2**|**Discrete**|**Text**|  
    |**Eder**|**Fortlaufend**|**Lange**|  
    |**Bike Buyer**|**Discrete**|**Lange**|  
    |**Commute Distance**|**Discrete**|**Text**|  
    |**CustomerKey**|**Schlüssel**|**Lange**|  
    |**DateLastPurchase**|**Fortlaufend**|**Date**|  
    |**E-Mail Adresse**|**Discrete**|**Text**|  
    |**EnglishEducation**|**Discrete**|**Text**|  
    |**English Occupation**|**Discrete**|**Text**|  
    |**FirstName**|**Discrete**|**Text**|  
    |**Geschlecht**|**Discrete**|**Text**|  
    |**Geography Key**|**Discrete**|**Text**|  
    |**House Owner Flag**|**Discrete**|**Text**|  
    |**Nachname**|**Discrete**|**Text**|  
    |**Marital Status**|**Discrete**|**Text**|  
    |**Number Cars Owned**|**Discrete**|**Lange**|  
    |**Anzahl der Kinder zu Hause**|**Discrete**|**Lange**|  
    |**Region**|**Discrete**|**Text**|  
    |**Total Children**|**Discrete**|**Lange**|  
    |**Yearly Income**|**Fortlaufend**|**Double**|  
  
3.  Klicken Sie auf **Weiter**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Angeben eines Test Datasets für die Struktur &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Erstellen einer zielgerichteten Mailing-Mining Modellstruktur &#40;grundlegenden Data Mining-Lernprogramm&#41;](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Inhaltstypen &#40;Data Mining-&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)   
 [Datentypen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  
