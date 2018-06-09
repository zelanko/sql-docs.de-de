---
title: VBA-Funktionen in MDX und DAX | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 327a801ce725987d68236efcfddbf8a4e7231ea9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743889"
---
# <a name="vba-functions-in-mdx-and-dax"></a>VBA-Funktionen in MDX und DAX


  Dieses Dokument enthält Querverweise aller VBA-Funktionen in [Visual Basic für Applikationen-Funktionen](https://msdn.microsoft.com/vba/language-reference-vba/articles/functions-visual-basic-for-applications) , die in MDX unterstützt werden; die Liste enthält zudem einen Hinweis, wenn eine funktionale Äquivalenz mit der DAX-Sprache vorhanden ist .  
  
## <a name="visual-basic-for-applications-functions-reference"></a>Referenz zu VBA (Visual Basic für Applikationen)-Funktionen  
  
|Funktionsname|Supported|Hinweise|  
|-------------------|---------------|-----------|  
|Abs|DAX, MDX||  
|Array|Nicht unterstützt||  
|Asc|Nur MDX||  
|AscW|Nur MDX||  
|ArcTan|Nur MDX||  
|CallByName|Nicht unterstützt||  
|ZBool|Nur MDX||  
|ZByte|Nur MDX||  
|ZCurrrency|Nur MDX||  
|ZDate|Nur MDX||  
|CDbl|Nur MDX||  
|ZDec|Nur MDX||  
|Wählen Sie|Nur MDX||  
|Zchn|Nur MDX||  
|ZInteger|Nur MDX||  
|ZLong|Nur MDX||  
|CLngLng|Nicht unterstützt||  
|CLngPtr|Nicht unterstützt||  
|Befehl|Nicht unterstützt||  
|Cos|Nur MDX||  
|CreateObject|Nicht unterstützt||  
|ZSingle|Nur MDX||  
|CStr|Nur MDX||  
|CurDir|Nicht unterstützt||  
|ZVariant|Nur MDX||  
|CVErr|Nicht unterstützt||  
|date|Nur MDX|**Warnung** DAX implementiert eine andere Funktion mit dem gleichen Namen; die Funktion DATE (Year, Month, Day) verwendet, um einen datumstypwert zu generieren, aus den angegebenen Argumenten|  
|DateAdd|Nur MDX|**Warnung** DAX implementiert eine andere Funktion mit dem gleichen Namen; die DATEADD (\<Datumsangaben >, < Number_of_intervals >,\<Intervall >)-Funktion wird verwendet, um bestimmten Datumsangaben verschoben um eine Anzahl von Intervallen angegeben|  
|DateDiff]|Nur MDX||  
|DatTeil|Nur MDX||  
|DatSeriell|Nur MDX||  
|DateValue]|DAX, MDX||  
|Day|DAX, MDX||  
|GDA|Nur MDX||  
|Dir|Nicht unterstützt||  
|DoEvents|Nicht unterstützt||  
|Environ|Nicht unterstützt||  
|EOF|Nicht unterstützt||  
|Fehler|Nicht unterstützt||  
|Exponential|DAX, MDX||  
|FileAttr|Nicht unterstützt||  
|FileDateTime|Nicht unterstützt||  
|FileLen|Nicht unterstützt||  
|Filtern|Nicht unterstützt|**Warnung** MDX implementiert eine andere Funktion mit dem gleichen Namen; die FILTER (Set_Expression, Logical_Expression)-Funktion gibt die Menge, die daraus resultiert einen bestimmter Satz basierend auf einer Suchbedingung aus den angegebenen Argumenten zurück.<br /><br /> **Warnung** DAX implementiert eine andere Funktion mit dem gleichen Namen; die FILTER (\<Tabelle >,\<Filter >)-Funktion gibt eine Tabelle, die einen Teil einer anderen Tabelle oder einen Ausdruck aus den angegebenen Argumenten darstellt.|  
|Fix|Nur MDX||  
|Format (Visual Basic für Applikationen)|DAX, MDX||  
|FormatWährung|Nicht unterstützt||  
|FormatDatumZeit|Nicht unterstützt||  
|FormatZahl|Nicht unterstützt||  
|FormatProzent|Nicht unterstützt||  
|FreeFile|Nicht unterstützt||  
|ZW|Nur MDX||  
|GetAllSettings|Nicht unterstützt||  
|GetAttr|Nicht unterstützt||  
|GetObject|Nicht unterstützt||  
|GetSetting|Nicht unterstützt||  
|Hex|Nur MDX||  
|Hour|DAX, MDX||  
|Iif|Nur MDX|**Warnung** DAX implementiert eine ähnliche Funktion mit dem Namen: IF (Logical_test, Value_if_true, Value_if_false) Funktion.|  
|IMEStatus|Nicht unterstützt||  
|Eingabe|Nicht unterstützt||  
|Eingabefeld|Nicht unterstützt||  
|InStr|Nur MDX||  
|InStrRev|Nicht unterstützt||  
|int|DAX, MDX||  
|ZINSZ|Nur MDX||  
|IRR|Nur MDX||  
|IsArray|Nur MDX||  
|Nur IsDateMDX||  
|IsEmpty|Nur MDX||  
|IsError|DAX, MDX||  
|IsMissing|Nur MDX||  
|IsNull|Nur MDX||  
|IsNumeric|Nur MDX||  
|IsObject|Nicht unterstützt||  
|Join|Nicht unterstützt||  
|LBound|Nicht unterstützt||  
|Kleinbst|Nur MDX||  
|Left|DAX, MDX||  
|Len|DAX, MDX||  
|Loc|Nicht unterstützt||  
|LOF|Nicht unterstützt||  
|Log|Nur MDX|**Wichtige** DAX implementiert eine andere Funktion mit dem gleichen Namen; die Funktion LOG (Number, Base). Gibt den Logarithmus einer Zahl zu der Basis zurück, die anhand bestimmter Argumente angegeben wird.|  
|LGlätten|Nur MDX||  
|MacID|Nicht unterstützt||  
|MacScript|Nicht unterstützt||  
|Mid|DAX, MDX||  
|Minute|DAX, MDX||  
|QIKV|Nur MDX||  
|Month|DAX, MDX||  
|MonthName|Nicht unterstützt||  
|Meldung|Nicht unterstützt||  
|jetzt|DAX, MDX||  
|Zzr]|Nur MDX||  
|NBW|Nur MDX||  
|Oct|Nur MDX||  
|Partition|Nur MDX||  
|RMZ|Nur MDX||  
|KAPZ|Nur MDX||  
|BW|Nur MDX||  
|QBColor|Nur MDX||  
|ZINS|Nur MDX||  
|Ersetzen|Nicht unterstützt||  
|RGB|Nur MDX||  
|Right|DAX, MDX||  
|ZZG|Nur MDX||  
|Round|DAX, MDX||  
|RGlätten|Nur MDX||  
|Zweimal|DAX, MDX||  
|Seek|Nicht unterstützt||  
|Vorzchn|DAX, MDX||  
|Shell|Nicht unterstützt||  
|Sin|Nur MDX||  
|LIA|Nur MDX||  
|LeerZchn|Nur MDX||  
|Spc|Nicht unterstützt||  
|Teilung|Nicht unterstützt||  
|QWurzel|Nur MDX||  
|Str|Nur MDX||  
|StrVgl|Nur MDX||  
|StrKonv|Nur MDX||  
|Zeichenfolge]|Nur MDX||  
|StrReverse|Nicht unterstützt||  
|Schalter|Nur MDX||  
|DIA|Nur MDX||  
|Registerkarte|Nicht unterstützt||  
|Tan|Nur MDX||  
|Uhrzeit|Nicht unterstützt||  
|Zeitgeber|Nur MDX||  
|ZeitSeriell|Nur MDX||  
|ZeitSeriellStr|DAX, MDX||  
|Trim]|DAX, MDX||  
|TypName|Nur MDX||  
|UBound|Nicht unterstützt||  
|Großbst|Nur MDX||  
|Val|Nur MDX||  
|VarType|Nicht unterstützt||  
|Arbeitstag|DAX, MDX||  
|WeekdayName|Nicht unterstützt||  
|Year|DAX, MDX||  
  
  
