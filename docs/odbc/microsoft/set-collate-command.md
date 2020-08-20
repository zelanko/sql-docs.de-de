---
description: SET COLLATE-Befehl
title: Befehl "COLLATE festlegen" | Microsoft-Dokumentation
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
ms.openlocfilehash: 5ca796da60adf0c432b5bbd80065e58563664bc5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466382"
---
# <a name="set-collate-command"></a>SET COLLATE-Befehl
Gibt eine Sortierreihenfolge für Zeichenfelder in nachfolgenden Indizierungs-und Sortiervorgängen an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET COLLATE TO cSequenceName  
```  
  
## <a name="arguments"></a>Argumente  
 *csequencename*  
 Gibt eine Sortierreihenfolge an. Die verfügbaren Sortierungs Sequenz Optionen werden in der folgenden Tabelle beschrieben.  
  
|Tastatur|Sprache|  
|-------------|--------------|  
|Holländisch|Niederländisch|  
|GENERAL|Englisch, Französisch, Deutsch, Spanisch, Portugiesisch und andere westeuropäische Sprachen|  
|Deutsch|Deutsche Telefonbuch Bestellung (DIN)|  
|Island|Isländisch|  
|Computer|Machine (die Standard Sortierreihenfolge für frühere FoxPro-Versionen)|  
|Nordan|Norwegisch, Dänisch|  
|Spanisch|Traditionelles Spanisch|  
|Swefin|Schwedisch, Finnisch|  
|Uniqwt|Eindeutige Gewichtung|  
  
> [!NOTE]  
>  Wenn Sie die Spanisch-Option angeben, ist *ch* ein einzelner Buchstabe, der zwischen *c* und *d*sortiert, und *ll* sortiert zwischen *l* und *m*.  
  
 Wenn Sie eine Sortierungs Sequenz Option als Literalzeichenfolge angeben, stellen Sie sicher, dass Sie die Option in Anführungszeichen einschließen:  
  
```  
SET COLLATE TO "SWEFIN"  
```  
  
 Der Computer ist die Standardoption für die Sortierreihenfolge und ist die Sequenz, mit der die xbase-Benutzer vertraut sind. Die Zeichen werden in der aktuellen Codepage angezeigt.  
  
 Allgemein ist möglicherweise für US-amerikanische und westliche Europäische Benutzer vorzuziehen. Die Zeichen werden in der aktuellen Codepage angezeigt. In FoxPro-Versionen vor 2,5 wurden möglicherweise Indizes mithilfe der Funktionen " **Upper**()" oder " **Lower**()" erstellt, um Zeichenfelder in einen konsistenten Fall zu konvertieren. In FoxPro-Versionen, die höher als 2,5 sind, können Sie stattdessen die Option "allgemeine Sortierungs Sequenz" angeben und die **obere**()-Konvertierung weglassen.  
  
 Wenn Sie eine andere Sortierungs Sequenz Option als Machine angeben und eine IDX-Datei erstellen, wird immer eine Compact. idx-Datei erstellt.  
  
 Verwenden Sie Set ("COLLATE"), um die aktuelle Sortierungs Sequenz zurückzugeben.  
  
 Sie können eine Sortierreihenfolge für eine Datenquelle angeben, indem Sie das [Visual FoxPro-Setup Dialogfeld von ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) oder das COLLATE-Schlüsselwort in der Verbindungs Zeichenfolge mit [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)verwenden. Dies ist mit der Ausgabe des folgenden Befehls identisch:  
  
```  
SET COLLATE TO cSequenceName  
```  
  
## <a name="remarks"></a>Bemerkungen  
 SET COLLATE ermöglicht Ihnen das Sortieren von Tabellen, die Zeichen mit Akzent enthalten, für jede der unterstützten Sprachen. Das Ändern der Einstellung von SET COLLATE wirkt sich nicht auf die Sortierreihenfolge der zuvor geöffneten Indizes aus. Visual FoxPro verwaltet vorhandene Indizes automatisch und bietet so die Flexibilität, viele verschiedene Arten von Indizes zu erstellen, auch für dasselbe Feld.  
  
 Wenn z. b. ein Index erstellt wird, bei dem SET COLLATE auf General festgelegt ist und die Einstellung SET COLLATE später in Spanish geändert wird, behält der Index die allgemeine Sortierreihenfolge bei.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten von ODBC-Visual FoxPro (Dialogfeld)](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
