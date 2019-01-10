---
title: ADO-Verlauf | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, what's new
ms.assetid: 667673f2-3151-432b-894a-3fc60b704ea4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e00a1ff652e3f1463d37e2cd5457965968b4ba4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47709558"
---
# <a name="ado-features-for-each-release"></a>ADO-Features für jede Version
In diesem Thema werden die neuen Funktionen, die von den einzelnen Releases des ADO, ADO MD und ADOX aufgelistet.

## <a name="ado-60"></a>ADO 6.0
 ADO 6.0 ist in Windows Vista als Teil der Windows Data Access Components (Windows DAC) 6.0 enthalten. ADO 6.0 ist funktionell gleichwertig mit ADO 2.8.

## <a name="ado-28"></a>ADO 2.8
 ADO 2.8 wurde in Windows XP und Windows Server 2003, als Teil der Microsoft Data Access Components (MDAC) 2.8 enthalten. Eine verteilbare Version von MDAC 2.8 ist ebenfalls verfügbar. Beachten Sie, dass dieses verteilbare Version nur auf Windows 2000 installiert werden soll. ADO 2.8 behandelt einige sicherheitsbezogenen bedenken:

 *Festplatte Zugriff ist nicht außerhalb einer vertrauenswürdigen Zone zulässig.*
In der domänenübergreifende Skripterstellung im Zusammenhang mit nicht vertrauenswürdigen Websites, die folgenden Vorgänge sind deaktiviert: **Stream.SaveToFile**, **Stream.LoadFromFile**, **Recordset.Save**, und **Recordset.Open**, zusammen mit den **AdCmdFile** Kennzeichen oder mit der Microsoft OLE DB-Persistenz-Anbieter (MSPersist).

 **Recordset.Open** *,* **Recordset.Save** *,* **Stream.SaveToFile** *, und* **Stream.LoadFromFile** *für nur physische Dateien verwendet werden.*
Diese Methoden überprüfen nun, dass Dateihandles auf nur physische Dateien verweisen.

 **Recordset.ActiveCommand** *gibt einen Fehler beim Aufrufen aus einer HTML-/ ASP-Seite zurück.*
Dies verhindert, dass die **Befehl** Objekt firmenhardware missbräuchlich verwendet werden.

 *Die Anzahl der***Recordsets***zurückgegeben wird, indem Sie eine geschachtelte***Form***Befehl verfügt über eine Obergrenze.* 
Ein geschachtelte Shape-Befehl gibt jetzt maximal 512 **Recordsets**. Dies bedeutet, dass eine **Form** Befehl kann nicht mehr in jeder beliebigen Tiefe geschachtelt werden. Stattdessen wird die maximale Tiefe der Ebene 512, wenn jeder Befehl in einer einzelnen (untergeordnet) führt **Recordset**. IF, auf jeder Ebene, ein **Form** Befehl gibt mehrere **Recordsets**, die maximale Tiefe der Ebene werden weniger als 512.

## <a name="ado-27"></a>ADO 2.7
 *64-Bit-plattformunterstützung* ADO 2.7 wird Unterstützung für 64-Bit-Prozessoren eingeführt.

## <a name="ado-26"></a>ADO 2.6
 **CubDef.GetSchemaObject***Methode* ADO 2.6 ab, ADO MD-Objekte können mit abgerufen werden eindeutige Namen, die gemäß der [UniqueName-Eigenschaft (ADO MD)](../../ado/reference/ado-md-api/uniquename-property-ado-md.md).   Die Namen der übergeordneten Objekte müssen nicht bekannt sein, und die übergeordnete Sammlungen müssen nicht aufgefüllt werden, um ein Objekt abzurufen. Finden Sie unter [getschemaobject-Modell (ADO MD)](../../ado/reference/ado-md-api/getschemaobject-method-ado-md.md).

 *Befehl Streams* der **Befehl** Objekt unterstützt die Befehle im Stream-Format als Alternative zur Verwendung der **CommandText** Eigenschaft. Die [CommandStream-Eigenschaft (ADO)](../../ado/reference/ado-api/commandstream-property-ado.md) können verwendet werden, um die XML-Vorlagen oder Updategrams als angeben der **Befehl** Eingabe, die mit der Microsoft OLE DB-Anbieter für SQL Server.

 **Dialekt***Eigenschaft* [Dialekt](../../ado/reference/ado-api/dialect-property.md) ist eine neue Eigenschaft, die die Syntax definiert und Allgemeine Regeln, mit denen der Anbieter verwendet, um die Zeichenfolge oder den Stream zu analysieren.  

 **Recordset.Open***Methode* der [Execute-Methode](../../ado/reference/ado-api/execute-method-ado-command.md) der ADO **Befehl** Objekt wurde verbessert, um Datenströme für ein- und Ausgaben zu verwenden.  

 *Feld Statusvalues* Wenn der Benutzer ein DB_E_ERRORSOCCURRED beim Ändern auftritt einer **Feld** von eine **Recordset**, ADO wird nun ausgefüllt. die **Field.Status**Eigenschaft mit den entsprechenden Statusinformationen, damit der Benutzer Weitere Informationen zum Problem geöffnet sein kann. Finden Sie unter [Status-Eigenschaft (ADO Field)](../../ado/reference/ado-api/status-property-ado-field.md).

 **NamedParameters***Eigenschaft* [NamedParameters](../../ado/reference/ado-api/namedparameters-property-ado.md) ist eine neue Eigenschaft der **Befehl** -Objekt, das zeigt an, dass der Anbieter sollte mit dem Namen Parameter.  

 *Resultsets in Streams* ADO kann Resultsets zurückgeben, aus einer Datenquelle in einem **Stream**, anstelle eines **Recordset** Objekt. Verwenden die neueste Version von Microsoft OLE DB-Anbieter für SQL Server, erhalten XML-Ergebnisse vom Anbieter Sie durch Ausführen einer Abfrage "Für XML". Ein **Stream** , empfängt das Resultset kann mit einem Befehl "Für XML" als Quelle geöffnet werden. Finden Sie unter [Abrufen von Resultsets in Streams](../../ado/guide/data/retrieving-resultsets-into-streams.md).

 *Einzeilige Resultset* der ADO **Datensatz** Objekt kann nun geöffnet werden, auf eine Befehlszeichenfolge oder **Befehl** Objekt, das eine Zeile mit Daten vom Anbieter zurückgegeben. Dies führt zu einer verbesserten Leistung mit MDAC 2.6-Anbieter. Finden Sie unter [Open-Methode (ADO Record)](../../ado/reference/ado-api/open-method-ado-record.md).

## <a name="ado-25"></a>ADO 2.5
 **Datensatz** *Objekt* ADO 2.5 führt die **Datensatz** Objekt zum darstellen und verwalten eine Zeile aus einer **Recordset** oder einen Datenanbieter oder ein Objekt gekapselt ein Teilweise strukturierte Daten, z. B. eine Datei oder ein Verzeichnis.

 **Stream** *Objekt* ADO 2.5 führt auch die **Stream** Objekt, das einen Datenstrom Binär oder Text darstellen.

 *URL-Bindung* ADO 2.5 führt die Verwendung einer URL, als Alternative zu einer Verbindung und der Befehlstext Text Namen Daten um Objekte zu speichern. Eine URL verwendet werden kann, mit dem vorhandenen **Verbindung** und **Recordset** auch Objekte wie bei der neuen **Datensatz** und **Stream** Objekte.

 *Datenanbieter, die Unterstützung von URL-Bindung* ADO 2.5 unterstützt OLE DB-Anbieter, die die URL-Schemas zu erkennen. Dies umfasst die OLE DB-Anbieter für Internet Publishing, greift auf das Dateisystem von Windows 2000 und erkennt die vorhandene HTTP-Schema.
