---
title: VBA-Funktionen in MDX und DAX | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 39a0db181f3b1d1a40af1a5fa27ba78366a9d2b3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68135021"
---
# <a name="vba-functions-in-mdx-and-dax"></a>VBA-Funktionen in MDX und DAX


  Dieses Dokument enthält einen über kreuzten Verweis auf alle VBA-Funktionen, die in [Visual Basic for Applications Funktionen](https://msdn.microsoft.com/vba/language-reference-vba/articles/functions-visual-basic-for-applications) verfügbar sind, die in MDX unterstützt werden. Außerdem enthält die Liste eine Notiz, wenn funktionale Äquivalenz mit der DAX-Sprache vorliegt.  
  
## <a name="visual-basic-for-applications-functions-reference"></a>Referenz zu VBA (Visual Basic für Applikationen)-Funktionen  
  
|Funktionsname|Unterstützt|Hinweise|  
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
|Get-Help|Nicht unterstützt||  
|Cos|Nur MDX||  
|CreateObject|Nicht unterstützt||  
|ZSingle|Nur MDX||  
|CStr|Nur MDX||  
|CurDir|Nicht unterstützt||  
|ZVariant|Nur MDX||  
|CVErr|Nicht unterstützt||  
|Datum|Nur MDX|**Warnung** DAX implementiert eine andere Funktion mit demselben Namen. die Funktion Date (Year, month, Day), mit der ein Date-Type-Wert aus den angegebenen Argumenten generiert wird.|  
|DateAdd|Nur MDX|**Warnung** DAX implementiert eine andere Funktion mit demselben Namen. die DATEADD (\<dates>, <number_of_intervals>,\<Interval>)-Funktion, die verwendet wird, um die angegebenen Datumsangaben um eine bestimmte Anzahl von Intervallen zu verschieben.|  
|DateDiff|Nur MDX||  
|DatTeil|Nur MDX||  
|DatSeriell|Nur MDX||  
|DatWert|DAX, MDX||  
|Day (Tag)|DAX, MDX||  
|GDA|Nur MDX||  
|Dir|Nicht unterstützt||  
|DoEvents|Nicht unterstützt||  
|Environ|Nicht unterstützt||  
|EOF|Nicht unterstützt||  
|Fehler|Nicht unterstützt||  
|Exp|DAX, MDX||  
|FileAttr|Nicht unterstützt||  
|FileDateTime|Nicht unterstützt||  
|FileLen|Nicht unterstützt||  
|Filtern|Nicht unterstützt|**Warnung** MDX implementiert eine andere Funktion mit demselben Namen. die Filter (set_expression Logical_Expression)-Funktion gibt die Menge zurück, die sich aus dem Filtern einer angegebenen Menge basierend auf einer Such Bedingung aus den angegebenen Argumenten ergibt.<br /><br /> **Warnung** DAX implementiert eine andere Funktion mit demselben Namen. die Filter (\<Table>,\<Filter>)-Funktion gibt eine Tabelle zurück, die eine Teilmenge einer anderen Tabelle oder eines Ausdrucks aus den angegebenen Argumenten darstellt.|  
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
|Hexadezimal|Nur MDX||  
|Hour|DAX, MDX||  
|Iif|Nur MDX|**Warnung** DAX implementiert eine ähnliche Funktion mit dem Namen: if (logical_test, value_if_true value_if_false)-Funktion.|  
|IMEStatus|Nicht unterstützt||  
|Eingabe|Nicht unterstützt||  
|Eingabefeld|Nicht unterstützt||  
|InStr|Nur MDX||  
|InStrRev|Nicht unterstützt||  
|Int|DAX, MDX||  
|ZINSZ|Nur MDX||  
|IKV|Nur MDX||  
|IsArray|Nur MDX||  
|Nur isdatemdx||  
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
|Protokoll|Nur MDX|**Wichtig** DAX implementiert eine andere Funktion mit demselben Namen. die Log (Number, Base)-Funktion. Gibt den Logarithmus einer Zahl zu der Basis zurück, die anhand bestimmter Argumente angegeben wird.|  
|LGlätten|Nur MDX||  
|MacID|Nicht unterstützt||  
|MacScript|Nicht unterstützt||  
|Mid|DAX, MDX||  
|Minute|DAX, MDX||  
|QIKV|Nur MDX||  
|Monat|DAX, MDX||  
|MonthName|Nicht unterstützt||  
|Meldung|Nicht unterstützt||  
|jetzt|DAX, MDX||  
|ZZR|Nur MDX||  
|NBW|Nur MDX||  
|Okt|Nur MDX||  
|Partition|Nur MDX||  
|RMZ|Nur MDX||  
|KAPZ|Nur MDX||  
|BW|Nur MDX||  
|QBColor|Nur MDX||  
|Rate|Nur MDX||  
|Replace|Nicht unterstützt||  
|RGB|Nur MDX||  
|Right|DAX, MDX||  
|ZZG|Nur MDX||  
|Round|DAX, MDX||  
|RGlätten|Nur MDX||  
|Sekunde|DAX, MDX||  
|Seek|Nicht unterstützt||  
|Vorzchn|DAX, MDX||  
|Shell|Nicht unterstützt||  
|Sin|Nur MDX||  
|LIA|Nur MDX||  
|LeerZchn|Nur MDX||  
|Spc|Nicht unterstützt||  
|Split|Nicht unterstützt||  
|QWurzel|Nur MDX||  
|Str|Nur MDX||  
|StrVgl|Nur MDX||  
|StrKonv|Nur MDX||  
|String|Nur MDX||  
|StrReverse|Nicht unterstützt||  
|Schalter|Nur MDX||  
|DIA|Nur MDX||  
|Registerkarte|Nicht unterstützt||  
|Tan|Nur MDX||  
|Zeit|Nicht unterstützt||  
|Zeitgeber|Nur MDX||  
|ZeitSeriell|Nur MDX||  
|ZeitSeriellStr|DAX, MDX||  
|Glätten|DAX, MDX||  
|TypName|Nur MDX||  
|UBound|Nicht unterstützt||  
|Großbst|Nur MDX||  
|Ster|Nur MDX||  
|VarType|Nicht unterstützt||  
|Wochentag|DAX, MDX||  
|WeekdayName|Nicht unterstützt||  
|Jahr|DAX, MDX||  
  
  
