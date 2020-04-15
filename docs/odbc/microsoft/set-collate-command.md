---
title: SET COLLATE Befehl | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set collate command [ODBC]
ms.assetid: 00efbcd4-fea8-4061-86a5-82de413cb753
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a9c1dfd59c00ad0ac0b7bd8b8f1cdfccc84d9b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300890"
---
# <a name="set-collate-command"></a>SET COLLATE-Befehl
Gibt eine Sortierungssequenz für Zeichenfelder in nachfolgenden Indizierungs- und Sortiervorgängen an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET COLLATE TO cSequenceName  
```  
  
## <a name="arguments"></a>Argumente  
 *cSequenceName*  
 Gibt eine Sortierungssequenz an. Die verfügbaren Sortierungssequenzoptionen werden in der folgenden Tabelle beschrieben.  
  
|Tastatur|Sprache|  
|-------------|--------------|  
|Holländisch|Niederländisch|  
|GENERAL|Englisch, Französisch, Deutsch, Modernes Spanisch, Portugiesisch und andere westeuropäische Sprachen|  
|Deutsch|Deutsche Telefonbuchbestellung (DIN)|  
|Island|Isländisch|  
|Maschine|Machine (die Standard-Sortierungssequenz für frühere FoxPro-Versionen)|  
|NORDAN|Norwegisch, Dänisch|  
|Spanisch|Traditionelles Spanisch|  
|SWEFIN|Schwedisch, Finnisch|  
|UNIQWT|Einzigartiges Gewicht|  
  
> [!NOTE]  
>  Wenn Sie die Option SPANISH angeben, ist *ch* ein einzelner Buchstabe, der zwischen *c* und *d*sortiert, und *ll* sortiert zwischen *l* und *m*.  
  
 Wenn Sie eine Sortierungssequenzoption als Literalzeichenfolge angeben, müssen Sie die Option in Anführungszeichen einschließen:  
  
```  
SET COLLATE TO "SWEFIN"  
```  
  
 MACHINE ist die Standard-Sortierungssequenzoption und ist die Sequenz, mit der Xbase-Benutzer vertraut sind. Zeichen werden so sortiert, wie sie auf der aktuellen Codepage angezeigt werden.  
  
 GENERAL kann für US- und westeuropäische Nutzer vorzuziehen sein. Zeichen werden so sortiert, wie sie auf der aktuellen Codepage angezeigt werden. In FoxPro-Versionen vor 2.5 wurden Indizes möglicherweise mit den Funktionen **UPPER**( ) oder **LOWER**( ) erstellt, um Zeichenfelder in eine konsistente Groß-/Kleinschreibung zu konvertieren. In FoxPro-Versionen nach 2.5 können Sie stattdessen die Option ALLGEMEINE Sortierungssequenz angeben und die **UPPER**- Konvertierung weglassen.  
  
 Wenn Sie eine andere Sortierungssequenzoption als MACHINE angeben und eine .idx-Datei erstellen, wird immer eine kompakte .idx erstellt.  
  
 Verwenden Sie SET("COLLATE"), um die aktuelle Sortierungssequenz zurückzugeben.  
  
 Sie können eine Sortiersequenz für eine Datenquelle angeben, indem Sie das [ODBC Visual FoxPro Setup DialogFeld](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) oder das Sammelschlüsselwort in Ihrer Verbindungszeichenfolge mit [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)verwenden. Dies ist identisch mit der Ausgabe des folgenden Befehls:  
  
```  
SET COLLATE TO cSequenceName  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Mit SET COLLATE können Sie Tabellen mit akzentuierten Zeichen für jede der unterstützten Sprachen bestellen. Das Ändern der Einstellung von SET COLLATE wirkt sich nicht auf die Sortierreihenfolge zuvor geöffneter Indizes aus. Visual FoxPro verwaltet automatisch vorhandene Indizes und bietet die Flexibilität, viele verschiedene Arten von Indizes zu erstellen, selbst für dasselbe Feld.  
  
 Wenn z. B. ein Index erstellt wird, bei dem SET COLLATE auf GENERAL festgelegt ist und die Einstellung SET COLLATE später in SPANISH geändert wird, behält der Index die ALLGEMEINE Sortierungssequenz bei.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einrichten von ODBC-Visual FoxPro (Dialogfeld)](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
