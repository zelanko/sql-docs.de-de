---
title: Befehl SET COLLATE | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 372d3b2df79d66084f5599b4ac098b8c273ee78a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127833"
---
# <a name="set-collate-command"></a>SET COLLATE-Befehl
Gibt eine Sortierreihenfolge für Zeichenfelder in nachfolgenden indizierungs- und Sortiervorgänge an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET COLLATE TO cSequenceName  
```  
  
## <a name="arguments"></a>Argumente  
 *cSequenceName*  
 Gibt eine Sortierreihenfolge an. Die verfügbaren Sortierungsoptionen für die Sequenz werden in der folgenden Tabelle beschrieben.  
  
|Optionen|Sprache|  
|-------------|--------------|  
|DUTCH|Niederländisch|  
|GENERAL|Englisch, Französisch, Deutsch, moderne Spanisch, Portugiesisch und andere westeuropäischen Sprachen|  
|GERMAN|Reihenfolge der deutschen Telefonbuch (DIN)|  
|ISLAND|Isländisch|  
|COMPUTER|Computer (die Standardsortierreihenfolge für frühere Versionen von FoxPro)|  
|NORDAN|Norwegisch, Dänisch|  
|SPANISCH|Spanisch (traditionell)|  
|SWEFIN|Schwedisch, Finnisch|  
|UNIQWT|Eindeutig Gewichtung|  
  
> [!NOTE]  
>  Bei der Angabe der Option Spanisch *ch* ist ein einzelner Buchstabe verwendet, die zwischen sortiert *c* und *d*, und *ll* zwischen sortiert  *l* und *m*.  
  
 Wenn Sie eine Sortierung sequenzoption als Literalzeichen Zeichenfolge angeben, achten Sie darauf, dass Sie die Option in Anführungszeichen einschließen:  
  
```  
SET COLLATE TO "SWEFIN"  
```  
  
 Computer ist die Standardoption für Sortierung Sequenz und ist, dass die Sequenz Xbase-Benutzer mit vertraut sind. Zeichen sind sortiert, wie sie in der aktuellen Codepage angezeigt werden.  
  
 Allgemeine kann sich vorzugsweise für USA und westeuropäische Benutzer sein. Zeichen sind sortiert, wie sie in der aktuellen Codepage angezeigt werden. In FoxPro-Versionen vor 2.5 Indizes wurde u. u. mit der **oberen**() oder **NIEDRIGERE**()-Funktionen für Zeichenfelder in einem konsistente Groß-/Kleinschreibung zu konvertieren. In Versionen höher als 2.5 FoxPro, Sie können stattdessen Geben Sie die allgemeine Sequenz Sortierungsoption und lassen die **oberen**()-Konvertierung.  
  
 Bei Angabe einer Sequenz Sortierungsoption als dem Computer, und wenn Sie eine IDX-Datei erstellen, wird eine kompakte IDX immer erstellt.  
  
 Verwenden Sie SET("COLLATE"), um die aktuelle Sortierreihenfolge zurückzugeben.  
  
 Sie können eine Sortierreihenfolge für eine Datenquelle angeben, indem die [ODBC-Visual FoxPro-Setupdialogfeld](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) oder mithilfe der Collate-Schlüsselworts in der Verbindungszeichenfolge mit [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md). Dies ist identisch mit dem folgenden Befehl:  
  
```  
SET COLLATE TO cSequenceName  
```  
  
## <a name="remarks"></a>Hinweise  
 COLLATE festlegen, können Sie Order-Tabellen, die Zeichen mit Akzent für alle unterstützten Sprachen enthält. Ändern der Einstellung der COLLATE-festlegen wirkt sich nicht auf die Sortierreihenfolge von zuvor geöffneten Indizes aus. Visual FoxPro verwaltet automatisch vorhandene Indizes, bieten die Flexibilität, um viele verschiedene Arten von Indizes, auch für das gleiche Feld zu erstellen.  
  
 Wenn ein Index, mit der COLLATE-legen Sie in "Allgemein" festgelegt erstellt wird, und die COLLATE-festlegen-Einstellung auf Spanisch später geändert wird, behält der Index die allgemeine Sortierreihenfolge.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten von ODBC-Visual FoxPro (Dialogfeld)](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
