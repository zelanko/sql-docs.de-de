---
title: Angeben von den Daten- und Inhaltstyp (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation
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
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56040202"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a>Angeben des Datentyps und des Inhaltstyps (Lernprogramm zu Data Mining-Grundlagen)
  Nachdem Sie die Spalten zum Erstellen der Struktur und zum Trainieren der Modelle ausgewählt haben, können Sie erforderliche Änderungen an den Standarddaten und Inhaltstypen vornehmen, die vom Assistenten festgelegt wurden.  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a>Überprüfen und Ändern von Inhaltstyp und Datentyp für jede Spalte  
  
1.  Klicken Sie auf der Seite **Inhalt und Datentyp der Spalten angeben** auf **Erkennen** , um einen Algorithmus zur Bestimmung der Standarddaten und Inhaltstypen für die einzelnen Spalten auszuführen.  
  
2.  Überprüfen die Einträge in den Spalten **Inhaltstyp** und **Datentyp** . Ändern Sie die Einträge bei Bedarf, um sicherzustellen, dass die Einstellungen den in der folgenden Tabelle aufgeführten Einstellungen entsprechen.  
  
     Der Assistent erkennt normalerweise Zahlen und weist einen entsprechenden numerischen Datentyp zu. In vielen Szenarien bietet es sich jedoch an, eine Zahl stattdessen als Text zu behandeln. Beispielsweise sollte **GeographyKey** als Text behandelt werden, da mathematische Operationen sich für diese ID nicht eignen.  
  
    |Spalte|Inhaltstyp|Datentyp|  
    |------------|------------------|---------------|  
    |**– Adresszeile 1**|**Diskrete**|**Text**|  
    |**Zeile 2**|**Diskrete**|**Text**|  
    |**ALTER**|**fortlaufende**|**Long**|  
    |**Bike Buyer**|**Diskrete**|**Long**|  
    |**Commute Distance**|**Diskrete**|**Text**|  
    |**CustomerKey**|**Key**|**Long**|  
    |**DateLastPurchase**|**fortlaufende**|**Datum**|  
    |**Email Address**|**Diskrete**|**Text**|  
    |**Englisheducation**|**Diskrete**|**Text**|  
    |**English Occupation**|**Diskrete**|**Text**|  
    |**Vorname**|**Diskrete**|**Text**|  
    |**Geschlecht**|**Diskrete**|**Text**|  
    |**Geografieschlüssel**|**Diskrete**|**Text**|  
    |**House Owner Flag**|**Diskrete**|**Text**|  
    |**Last Name**|**Diskrete**|**Text**|  
    |**Marital Status**|**Diskrete**|**Text**|  
    |**Number Cars Owned**|**Diskrete**|**Long**|  
    |**Number Children At Home**|**Diskrete**|**Long**|  
    |**Region**|**Diskrete**|**Text**|  
    |**Total Children**|**Diskrete**|**Long**|  
    |**Yearly Income**|**fortlaufende**|**Double**|  
  
3.  Klicken Sie auf **Weiter**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Angeben eines Testdatasets für die Struktur &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Erstellen der Miningmodellstruktur Targeted Mailing &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Inhaltstypen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)   
 [Datentypen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  
