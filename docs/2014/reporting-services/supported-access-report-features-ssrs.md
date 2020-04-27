---
title: Unterstützte Access-Berichtsfunktionen (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], Access reports
- functions [Reporting Services]
- controls [Reporting Services]
- Access reports [Reporting Services]
- properties [Reporting Services], Access reports
- importing reports
- modules [Reporting Services]
ms.assetid: 7ffec331-6365-4c13-8e58-b77a48cffb44
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9088ab3e90b4fb341cc8125e45d498783953039d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66100575"
---
# <a name="supported-access-report-features-ssrs"></a>Unterstützte Access-Berichtsfunktionen (SSRS)
  Wenn Sie einen Bericht in den Berichts-Designer importieren, wird der [!INCLUDE[msCoName](../includes/msconame-md.md)] Access-bericht während des Importvorgangs in eine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Definition Language (RDL)-Datei konvertiert. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt zahlreiche Funktionen von Access. Aufgrund der Unterschiede zwischen Access und [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] werden einige Elemente jedoch leicht angewandelt oder nicht unterstützt. In diesem Thema wird beschrieben, auf welche Weise Access-Berichtsfunktionen in RDL konvertiert werden.  
  
## <a name="importing-access-reports"></a>Importieren von Access-Berichten  
 Einige Abfragen enthalten für Access spezifischen Code. Access-Code wird nicht mit dem Bericht importiert. Auch wenn eine Abfrage eingebettete Zeichenfolgen enthält, wird der Bericht möglicherweise nicht ordnungsgemäß importiert. Um dies zu korrigieren, ersetzen Sie die Zeichenfolgen durch einen Zeichencode. Ersetzen Sie beispielsweise das Komma (,) durch CHAR(34).  
  
 Beim Import Vorgang wird das Semikolon nicht ordnungsgemäß übergeben (;) oder XML-Markup Zeichen\<(, > usw.) in den Informationen zur Verbindungs Zeichenfolge. Enthält eine Verbindungszeichenfolge ein Semikolon oder XML-Markupzeichen, müssen Sie das Kennwort im neuen Bericht nach dem Import manuell festlegen.  
  
 Beim Importieren werden die Verbindungs- oder allgemeinen Timeouteinstellungen in der Verbindungszeichenfolge nicht importiert. Möglicherweise müssen Sie nach dem Importieren des Berichts diese Einstellungen anpassen.  
  
 Wenn die Abfrage des importierten Berichts Abfrageparameter enthält, wird die Abfrage beim Import nicht konvertiert. Um die Abfrage zusammen mit dem Bericht zu importieren, ersetzen Sie die Abfrageparameter im Access-Bericht vorübergehend durch hartcodierte Werte, und ersetzen Sie sie nach dem Import des Berichts durch Abfrageparameter.  
  
## <a name="page-layout"></a>Seitenlayout  
 Das Seitenlayout in Access unterscheidet sich von dem in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Access ordnet Elemente auf der Seite mithilfe von "Streifen" an, also in vertikal auf der Seite platzierten Abschnitten. Diese Abschnitte können Berichtskopfzeilen und -fußzeilen, Seitenkopfzeilen und -fußzeilen, Gruppen und Details enthalten. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] bietet ein flexibleres Layout. Datenbereiche bieten Gruppierung und Details, und Sie können mehrere Datenbereiche beliebig im Hauptteil des Berichts platzieren, sogar nebeneinander. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enthält auch Abschnitte für Kopf- und Fußzeilen, ähnlich wie Access.  
  
 Beim Importieren eines Berichts aus Access in den Berichts-Designer werden die Seitenkopf- und -fußzeilen aus dem Access-Bericht in Seitenkopf- und -fußzeilen eines [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Berichts konvertiert. Gruppen und Details werden in einen Listendatenbereich konvertiert. Die Berichtskopf- und -fußzeilen werden statt in einem separaten Streifen im Hauptteil des Berichts platziert. Dies kann zu einer leicht unterschiedlichen Platzierung der Elemente gegenüber dem Access-Bericht führen.  
  
> [!NOTE]  
>  In einigen Access-Berichten werden Berichtselemente möglicherweise nebeneinander angezeigt, obwohl sie sich tatsächlich überlappen. Beim Importieren des Berichts mithilfe des Berichts-Designers wird diese Überlappung nicht korrigiert und kann beim Ausführen des Berichts zu unerwarteten Ergebnissen führen.  
  
## <a name="data-sources"></a>Projektmappen-Explorer  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt OLE DB-Datenquellen wie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Wenn Sie Berichte aus einer Access-Projektdatei (ADP) importieren, wird als Verbindungszeichenfolge für die Datenquelle die Verbindungszeichenfolge in der ADP-Datei übernommen. Wenn Sie Berichte aus einer Access-Datenbankdatei (MDB oder ACCDB) importieren, verweist die Verbindungszeichenfolge möglicherweise auf die Access-Datenbank, und Sie müssen sie nach dem Import der Berichte korrigieren. Handelt es sich bei der Datenquelle für den Access-Bericht um eine Abfrage, werden die Abfrageinformationen ohne Änderung in der RDL-Datei gespeichert. Handelt es sich bei der Datenquelle für den Access-Bericht um eine Tabelle, wird durch den Konvertierungsprozess eine Abfrage erstellt, die auf dem Tabellennamen und den Feldern der Tabelle basiert.  
  
## <a name="reports-with-custom-modules"></a>Berichte mit benutzerdefinierten Modulen  
 Wenn ein benutzerdefinierter [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Code in Modulen enthalten ist, wird er nicht konvertiert. Wenn Berichts-Designer während des Import Vorgangs auf Code stößt, wird eine Warnung generiert und im **Aufgabenliste** Fenster angezeigt.  
  
## <a name="report-controls"></a>Berichtssteuerelemente  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Access-Steuerelemente und schließt sie in konvertierte Berichtsdefinitionen ein.  
  
|||||  
|-|-|-|-|  
|Bild|Bezeichnung|Zeile|Rechteck|  
|Unterformular|Unter Bericht<br /><br /> **Hinweis** Während ein unter Berichts-Steuerelement innerhalb des Hauptberichts konvertiert wird, wird der unter Bericht selbst separat konvertiert.|TextBox||  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Steuerelemente nicht:  
  
|||||  
|-|-|-|-|  
|Gebundenes Objektfeld|CheckBox|ComboBox|Befehlsschaltfläche|  
|Benutzerdefiniertes Steuerelement|ListBox|Objektfeld|OptionButton|  
|TabControl|Umschaltfläche|||  
  
 Wenn Berichts-Designer während des Import Vorgangs eines dieser Steuerelemente findet, wird eine Warnung generiert und im **Aufgabenliste** Fenster angezeigt.  
  
 Andere Steuerelemente, wie ActiveX und Office Web Components, werden nicht importiert. Enthält ein Access-Bericht beispielsweise ein OWC-Diagramm-Steuerelement, wird dieses beim Import des Berichts nicht konvertiert.  
  
## <a name="report-properties"></a>Berichtseigenschaften  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Eigenschaften, die über die Access-Benutzeroberfläche zur Verfügung stehen. Eigenschaften, die nur in Code verfügbar sind, werden nicht unterstützt und sind hier nicht aufgeführt.  
  
|||||  
|-|-|-|-|  
|BackColor|Hintergrundart|BorderColor|Rahmenart|  
|Rahmenbreite|BottomMargin|Vergrößerbar (Textfeld)|Verkleinerbar (Textfeld)|  
|Caption|SchriftFett|FontItalic|FontName|  
|FontSize|Fontunter Streichung|Schriftbreite|NeueSeite|  
|ForeColor|Höhe|HideDuplicates|Link|  
|IsHyperlink|Sichtbar|Zusammenhalten (Gruppe)|Left|  
|LeftMargin|Neigung|Zeilenabstand|VerknüpfenVon|  
|VerknüpfenNach|NeueZeileOderSpalte|PageFooter|PageHeader|  
|Seiten|Bild|BildNebeneinander (Bericht)|Lesefolge|  
|BereichWiederholen|RechterRand|LaufendeSumme|Größenanpassung|  
|Textausrichtung|TOP|ObererRand|Breite|  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Eigenschaften, die über die Access-Benutzeroberfläche zur Verfügung stehen, nicht:  
  
|||||  
|-|-|-|-|  
|Vergrößerbar (Abschnitt)|Verkleinerbar (Abschnitt)|Dezimalstellenanzeige|SchnellerLaserdruck|  
|Filtern|FilterAktiv|Format|FormatBedingungen|  
|GruppeZusammenhalten|Zusammenhalten (Abschnitt)|Zifferntyp|Ausrichtung|  
|Pinsel|Palettenherkunft|Bildausrichtung|Bildseiten|  
|Bildgrößenmodus|BildNebeneinander (Bild)|ScrollBars|Spezialeffekt|  
|Vertical||||  
  
## <a name="grouping"></a>Gruppierung  
 In Access wird eine Gruppenebene durch eine Kombination aus drei Eigenschaften definiert: Gruppenausdruck, `GroupOn`-Eigenschaft und `GroupInterval`-Eigenschaft. Eine Gruppe ohne Gruppenkopf oder -fuß wird mit der darin enthaltenen Gruppe zusammengeführt. Enthält die Gruppe keine andere Gruppe, wird der Detailabschnitt sortiert und die Gruppe gelöscht.  
  
## <a name="expressions"></a>Ausdrücke  
 In Access werden Ausdrücke zur Angabe von Werten verwendet, die in Textfeldern angezeigt werden. Als Sprache für Ausdrücke wird in Access neben einigen Aggregatfunktionen [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] verwendet. Der Berichts-Designer konvertiert diese Access-Ausdrücke in Berichtsausdrücke.  
  
### <a name="functions"></a>Functions  
 Für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Berichtsdefinitionen wird [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET als systemeigene Sprache für Ausdrücke verwendet, während in Access 2002 Visual Basic verwendet wird. In den folgenden Listen sind die von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützten Funktionen beschrieben.  
  
#### <a name="array-functions"></a>Arrayfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Arrayfunktionen:  
  
-   LBound  
  
-   UBound  
  
#### <a name="conversion-functions"></a>Konvertierungsfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Konvertierungsfunktionen:  
  
|||||  
|-|-|-|-|  
|Asc|ZBool|ZByte|ZCurrrency|  
|ZDate|CDbl|ZDec|Zchn|  
|Zchn$|ZInteger|ZLong|ZSingle|  
|CStr|ZVariant|ZVarDat|Format|  
|FormatWährung|FormatDatumZeit|FormatZahl|FormatProzent|  
|Hexadezimal|Hex$|Nz|Okt|  
|Oktal$|Str|Str$|StrKonv|  
|Ster||||  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Konvertierungsfunktionen nicht:  
  
-   GUIDFromString  
  
-   StringFromGUID  
  
#### <a name="database-functions"></a>Datenbankfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Datenbankfunktionen:  
  
|||||  
|-|-|-|-|  
|CreateReport|GetObject|HyperlinkPart|Partition|  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Datenbankfunktionen nicht:  
  
|||||  
|-|-|-|-|  
|CodeDb|CreateControl|CreateForm|CreateGroupLevel|  
|CreateObject|CreateReportControl|CurrentDb|CurrentUser|  
|DeleteControl|DeleteReportControl|Eval|IMEStatus|  
|SysCmd||||  
  
#### <a name="datetime-functions"></a>Datum/Uhrzeit-Funktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Datum/Uhrzeit-Funktionen:  
  
|||||  
|-|-|-|-|  
|Datum|Datum$|DateAdd|DateDiff|  
|DatTeil|DatSeriell|DatWert|Day (Tag)|  
|Hour|Minute|Monat|MonthName|  
|jetzt|Sekunde|Zeit|Time$|  
|Zeitgeber|ZeitSeriell|ZeitSeriellStr|Wochentag|  
|WeekdayName|Jahr|||  
  
#### <a name="ddeole-functions"></a>DDE/OLE-Funktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden DDE/OLE-Funktionen nicht:  
  
|||||  
|-|-|-|-|  
|DDE|DDEIntitate|DDERequest|DDESend|  
|LoadPicture||||  
  
#### <a name="domain-aggregate-functions"></a>Domänenaggregatfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Domänenaggregatfunktionen nicht:  
  
|||||  
|-|-|-|-|  
|DomMittelwert|DomAnzahl|DomErsterWert|DomLetzterWert|  
|DomWert|DomMax|DomMin|DomStAbw|  
|DomStAbwn|DomSumme|DomVarianz|DomVarianzen|  
  
#### <a name="error-handling-functions"></a>Fehlerbehandlungsfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Fehlerbehandlungsfunktionen:  
  
|||||  
|-|-|-|-|  
|Err|Fehler|Error$|IsError|  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgende Fehlerbehandlungsfunktion nicht:  
  
-   CVErr  
  
#### <a name="financial-functions"></a>Finanzmathematische Funktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden finanzmathematischen Funktionen:  
  
|||||  
|-|-|-|-|  
|GDA|ZW|ZINSZ|IKV|  
|QIKV|ZZR|NBW|RMZ|  
|KAPZ|BW|Rate|LIA|  
|DIA||||  
  
#### <a name="interaction-functions"></a>Interaktionsfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Interaktionsfunktionen:  
  
|||||  
|-|-|-|-|  
|Befehl|Command$|CurDir|CurDir$|  
|DeleteSetting|Dir|Dir$|Environ|  
|Environ$|EOF|FileAttr|FileDateTime|  
|FileLen|FreeFile|GetAllSettings|GetAttr|  
|GetSetting|Loc|LOF|QBColor|  
|RGB|SaveSetting|Seek|SetAttr|  
|Shell|Spc|Registerkarte||  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Interaktionsfunktionen nicht:  
  
|||||  
|-|-|-|-|  
|DoEvents|Geben Sie in|Eingabe|Input$|  
  
#### <a name="inspection-functions"></a>Inspektionsfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Inspektionsfunktionen:  
  
|||||  
|-|-|-|-|  
|IsArray|IsDate|IsEmpty|IsError|  
|IsNull|IsNumeric|IsObject|TypName|  
|VarType||||  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Inspektionsfunktionen nicht:  
  
-   IsMissing  
  
#### <a name="math-functions"></a>Mathematische Funktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden mathematischen Funktionen:  
  
|||||  
|-|-|-|-|  
|Abs|ArcTan|Cos|Exp|  
|Fix|Int|Log|ZZG|  
|Round|Vorzchn|Sin|QWurzel|  
|Tan||||  
  
#### <a name="message-functions"></a>Nachrichtenfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Nachrichtenfunktionen nicht:  
  
|||||  
|-|-|-|-|  
|Eingabefeld|Eingabefeld$|Meldung||  
  
#### <a name="program-flow-functions"></a>Programmflussfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Programmflussfunktionen:  
  
|||||  
|-|-|-|-|  
|Wählen Sie|IIf|Schalter||  
  
#### <a name="sql-aggregate-functions"></a>SQL-Aggregatfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden SQL-Aggregatfunktionen:  
  
|||||  
|-|-|-|-|  
|Avg|Anzahl|Max|Min|  
|StDev|StDevP|SUM|Var|  
|VarP||||  
  
#### <a name="text-functions"></a>Textfunktionen  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die folgenden Textfunktionen:  
  
|||||  
|-|-|-|-|  
|Format|Format$|InStr|InStrRev|  
|Kleinbst|Kleinbst$|Left|Links$|  
|Len|LGlätten|LGlätten$|Mid|  
|Teil$|Replace|Right|Rechts$|  
|RGlätten|LeerZchn|LeerZchn$|StrVgl|  
|StrKonv|Zeichenfolge|String$|StrReverse|  
|Glätten|Glätten$|Großbst|Großbst$|  
  
### <a name="constants"></a>Konstanten  
 Access unterstützt spezielle [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Konstanten (z. B. `vbTrue`) in Ausdrücken nicht, daher ist keine Konvertierung erforderlich. Es gibt jedoch eine Ausnahme: das Schlüsselwort `Null` wird in `System.DbNull.Value` konvertiert.  
  
### <a name="parameters"></a>Parameter  
 Beim Importprozess wird jeder Ausdruck in einem Bericht vom Berichts-Designer auf Variablen überprüft, die keinen Feldnamen oder Steuerelementen entsprechen. Diese Variablen werden zu Berichtsparametern hinzugefügt.  
  
 Der Datentyp für Parameter gespeicherter Prozeduren wird immer als Zeichenfolge importiert. Nach dem Import des Berichts müssen Sie den Parameter manuell ändern, sodass der richtige Datentyp verwendet wird.  
  
### <a name="object-names"></a>Objektnamen  
 In Access können Felder denselben Namen wie Steuerelemente haben; in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ist dies nicht zulässig. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 6.0 lässt Leerzeichen in Variablennamen zu; Visual Basic .NET nicht. Beim Importprozess werden die Namen aller dieser Objekte durch gültige Namen ersetzt, und falls mehrere Objekte denselben Namen haben, werden diesen eindeutige Namen zugewiesen. Jeder Ausdruck wird überprüft, und die Namen von Variablen, die umbenannten Objekten entsprechen, werden durch die neuen Namen ersetzt.  
  
## <a name="rectangles-and-containment"></a>Rechtecke und enthaltene Elemente  
 In einer [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Berichtsdefinition können Rechtecke andere Berichtselemente enthalten. Jedes Rechteck, das größer ist als das Berichtselement und das mehr als 90 Prozent von dessen Fläche überdeckt, wird zu einem Container für das Berichtselement.  
  
## <a name="bitmaps"></a>Bitmaps  
 Alle in einen Bericht eingebetteten Bitmaps werden beim Import des Berichts unabhängig von ihrem ursprünglichen Format in das BMP-Format konvertiert. Enthält ein Bericht z. B. JPG- und GIF-Dateien, handelt es sich bei den resultierenden Ressourcen, die mit dem Bericht importiert werden, um BMP-Dateien. Die Bitmaps werden als eingebettete Bilder im Bericht gespeichert. Informationen zu eingebetteten Bildern finden Sie unter [Images &#40;Berichts-Generator und SSRS&#41;](report-design/images-report-builder-and-ssrs.md).  
  
## <a name="other-considerations"></a>Weitere Überlegungen  
 Neben den genannten Aspekten gilt für aus Access importierte Berichte Folgendes:  
  
-   Bedingte Formatierung wird nicht konvertiert.  
  
-   Das Beschreibungsfeld in den Berichtseigenschaften in Access wird nicht konvertiert.  
  
  
