---
title: Filteroperatoren (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 27914c8b-8951-4b7d-914d-1cbf528dd248
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ab3f97100c6e6c995e6eab749143ee02e6dbb51e
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53369243"
---
# <a name="filter-operators-master-data-services"></a>Filteroperatoren (Master Data Services)
  Wenn sie eine Liste von Elementen filtern, sind die folgenden Operatoren verfügbar.  
  
> [!NOTE]  
>  Wenn Sie nach mehreren Kriterien filtern, müssen alle Kriterien den Wert "true" haben, um Ergebnisse zurückzugeben. Zum Beispiel SquareFeet = 2000 **AND** Division <> 123.  
  
## <a name="filter-operators"></a>Filteroperatoren  
  
|Steuerelementname|Description|  
|------------------|-----------------|  
|**Ist gleich**|Gibt Attributwerte zurück, die den angegebenen Kriterien genau entsprechen. Um nach **Mountain-100**zu filtern, müssen Sie z.B. **Mountain-100**eingeben.|  
|**Ist nicht gleich**|Gibt Attributwerte zurück, die keine genaue Übereinstimmung mit den angegebenen Kriterien aufweisen. Die Filterkriterien müssen dem Attributwert, den Sie aus den Ergebnissen ausschließen möchten, genau entsprechen. Um Ergebnisse auszuschließen, die mit **Mountain-100**übereinstimmen, müssen Sie z.B. **Mountain-100**eingeben.<br /><br /> Hinweis: Wenn Sie eine filterbedingung mit einer "Ist nicht gleich"-Klausel auf ein Attribut anwenden, wird ein Element, das für die das Attribut NULL ist, die filterbedingung übergeben und zurückgegeben, wenn in Ihren datenbankeinstellungen SET ANSI_NULLS auf ON festgelegt ist. Um dieses Verhalten zu beenden, legen Sie SET ANSI_NULLS in den Datenbankeinstellungen auf OFF fest. Wenn SET ANSI_NULLS auf OFF festgelegt ist, werden alle Datenvergleiche mit einem NULL-Wert als TRUE ausgewertet, falls der Datenwert NULL ist. Dies hat zur Folge, dass das Element die „Ist ungleich“-Klausel nicht besteht. Weitere Informationen finden Sie unter [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql).|  
|**Ist wie**|Verwendet den LIKE-Operator aus Transact-SQL zum Filtern von Ergebnissen. Weitere Informationen finden Sie unter [LIKE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/like-transact-sql) in der SQL Server-Onlinedokumentation.|  
|**Ist nicht wie**|Verwendet den NOT-Operator aus Transact-SQL zum Filtern von Ergebnissen. Weitere Informationen finden Sie unter [NOT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/not-transact-sql) in der SQL Server-Onlinedokumentation.|  
|**Ist größer als**|Gibt Attributwerte zurück, die größer als die angegebenen Kriterien sind. Um Attributwerte zurückzugeben, die mit einem Buchstaben größer als **F**beginnen, geben Sie z. B. **F**ein.|  
|**Ist kleiner als**|Gibt Attributwerte zurück, die kleiner als die angegebenen Kriterien sind. Um Attributwerte zurückzugeben, die mit einem Buchstaben kleiner als **F**beginnen, geben Sie z. B. **F**ein.|  
|**Ist größer als oder gleich**|Gibt Attributwerte zurück, die größer oder gleich den angegebenen Kriterien sind. Um Attributwerte zurückzugeben, die mit der Zahl **3** oder einer höheren Zahl beginnen, geben Sie z. B. **3**ein.|  
|**Ist kleiner als oder gleich**|Gibt Attributwerte zurück, die kleiner oder gleich den angegebenen Kriterien sind. Um Attributwerte zurückzugeben, die mit der Zahl **3** oder einer kleineren Zahl beginnen, geben Sie z. B. **3**ein.|  
|**Stimmt überein**|Verwendet einen Fuzzysuchindex zum Filtern von Ergebnissen.<br /><br /> Geben Sie im Feld **Ähnlichkeitsgrad** an, wie genau die Abweichung der Attributwerte von den angegebenen Filterkriterien (mit einem Standardwert von „30 %“) sein muss. Wählen Sie eine der folgenden Möglichkeiten im Listenfeld **Algorithmus** aus.<br /><br /> **Levenshtein**: Eine Distanz, die auf der Anzahl von Bearbeitungen basiert (z. B. hinzugefügt oder löschungen), dass es, bis eine Zeichenfolge dauert, die eine andere übereinstimmen. Dies ist die Standardeinstellung. Erfordert keine zusätzlichen Parameter.<br /><br /> **Jaccard**: Ein Index, der am besten funktioniert, wenn Sie versuchen, mehrere Zeichenfolgen abzugleichen. Diese Suche unterstützt einen zusätzlichen Parameter der Kapselungsvorspannung (siehe unten).<br /><br /> **Jaro-Winkler**: Ein Abstand, der am besten für die Suche von doppelten Personennamen verwendet wird. Diese Methode gibt mehr Ergebnisse zurück als jede andere Methode. Unterstützt keine Kapselungsvorspannung.<br /><br /> **Längste gemeinsame Teilsequenz**: Funktioniert auf Grundlage einer teilsequenz, in dem die Buchstaben eines Musters in Reihenfolge angezeigt werden, angezeigt, obwohl sie getrennt werden können (z. B. die "MSR" eine teilsequenz von "MaSteR" ist). Diese Suche unterstützt einen zusätzlichen Parameter der Kapselungsvorspannung (siehe unten).<br /><br /> <br /><br /> Fügen Sie für den **Jaccard** - oder den **Längste gemeinsame Teilsequenz**-Algorithmus einen **Verzerrungswert für den Einschluss** hinzu. Der **Verzerrungswert für den Einschluss**ist ein Längenschwellenwert, der in einem dezimalen Prozentsatz zwischen „0“ und „1“ bereitgestellt wird, mit dem Standardwert „0,62“. Ein niedrigerer Schwellenwert vergrößert die Anzahl der möglichen zurückgegebenen Übereinstimmungen.|  
|**Stimmt nicht überein**|Verwendet einen Fuzzysuchindex zum Filtern von Ergebnissen. Geben Sie im Feld **Ähnlichkeitsgrad** an, wie genau die Abweichung der Attributwerte von den angegebenen Filterkriterien sein muss.|  
|**Enthält Muster**|Verwendet reguläre Ausdrücke von .NET Framework, um Ergebnisse nach einem angegebenen Muster zu filtern. Weitere Informationen zu regulären Ausdrücken finden Sie unter [Sprachelemente für reguläre Ausdrücke](https://go.microsoft.com/fwlink/?LinkId=164401) in der MSDN Library.|  
|**Enthält kein Muster**|Verwendet reguläre Ausdrücke von .NET Framework zum Filtern von Ergebnissen, die einem angegebenen Muster nicht entsprechen. Weitere Informationen zu regulären Ausdrücken finden Sie unter [Sprachelemente für reguläre Ausdrücke](https://go.microsoft.com/fwlink/?LinkId=164401) in der MSDN Library.|  
|**Ist NULL**|Gibt Attributwerte zurück, die NULL lauten. Das Feld **Kriterien** wird deaktiviert, wenn Sie den **Ist NULL** -Operator auswählen.|  
|**Ist nicht NULL**|Gibt Attributwerte zurück, die nicht NULL lauten. Das Feld **Kriterien** wird deaktiviert, wenn Sie den **Ist nicht NULL** -Operator auswählen.|  
  
  
