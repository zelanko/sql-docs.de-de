---
title: Benutzerdefinierte Eigenschaften der Flatfile | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0a0516d2e038f206c140f010c2ca4a459f79956a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62902047"
---
# <a name="flat-file-custom-properties"></a>Benutzerdefinierte Eigenschaften der Flatfile
  **Benutzerdefinierte Eigenschaften von Quellen**  
  
 Die Flatfilequelle verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 In der folgenden Tabelle werden die benutzerdefinierten Eigenschaften der Flatfilequelle beschrieben. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Beschreibung|  
|-------------------|---------------|-----------------|  
|FileNameColumnName|Zeichenfolge|Der Name einer Ausgabespalte, die den Dateinamen enthält. Wenn kein Name angegeben wird, wird keine Ausgabespalte generiert, die den Dateinamen enthält.<br /><br /> Hinweis: Diese Eigenschaft ist nicht im **Quellen-Editor für Flatfiles** verfügbar, kann jedoch im Dialogfeld **Erweiterter Editor** festgelegt werden.|  
|RetainNulls|Boolean|Ein Wert, der angibt, ob NULL-Werte aus der Quelldatei als NULL-Werte beibehalten werden sollen, wenn die Daten von der Data Transformation-Pipeline-Engine verarbeitet werden. Der Standardwert dieser Eigenschaft ist `False`.|  
  
 Die Ausgabe der Flatfilequelle verfügt nicht über benutzerdefinierte Eigenschaften.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften der Ausgabespalten der Flatfilequelle. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Beschreibung|  
|-------------------|---------------|-----------------|  
|FastParse|Boolean|Ein Wert, der angibt, ob die Spalte die schnelleren gebietsschemaneutralen Analyseroutinen von DTS oder die gebietsschemabezogenen Standardanalyseroutinen verwendet. Weitere Informationen finden Sie unter [Fast Parse](../fast-parse.md) und [Standard Parse](../standard-parse.md). Der Standardwert dieser Eigenschaft ist `False`.<br /><br /> Hinweis: Diese Eigenschaft ist nicht im **Quellen-Editor für Flatfiles** verfügbar, kann jedoch im Dialogfeld **Erweiterter Editor** festgelegt werden.|  
  
 Weitere Informationen finden Sie unter [Flat File Source](flat-file-source.md).  
  
 **Benutzerdefinierte Eigenschaften von Zielen**  
  
 Das Flatfileziel verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Flatfileziels. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|Beschreibung|  
|-------------------|---------------|-----------------|  
|Header|Zeichenfolge|Ein Textblock, der in die Datei eingefügt wird, bevor Daten geschrieben werden.<br /><br /> Der Wert dieser Eigenschaft kann mithilfe eines Eigenschaftsausdrucks angegeben werden.|  
|Overwrite|Boolean|Ein Wert, der angibt, ob eine vorhandene Zieldatei mit demselben Namen überschrieben werden soll oder ob an diese Datei angehängt werden soll. Der Standardwert dieser Eigenschaft ist `True`.|  
  
 Die Eingabe und die Eingabespalten des Flatfileziels verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Flat File Destination](flat-file-destination.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Common Properties](../common-properties.md)  
  
  
