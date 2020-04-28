---
title: Anforderungen an den benutzerdefinierten Typ | Microsoft-Dokumentation
description: Dieser Artikel beschreibt wichtige Entwurfsentscheidungen, die Sie treffen müssen, wenn Sie einen UDT erstellen, um auf SQL Server zu installieren.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UDTs [CLR integration], requirements
- serialization
- Native serialization format [CLR integration]
- attributes [CLR integration]
- XML serialization [CLR integration]
- user-defined types [CLR integration], requirements
- user-defined serialization [CLR integration]
- user-defined types [CLR integration], Native serialization
- UDTs [CLR integration], Native serialization
ms.assetid: bedc3372-50eb-40f2-bcf2-d6db6a63b7e6
author: rothja
ms.author: jroth
ms.openlocfilehash: 2b19a9179cba2225a2209255ce48220669e4bbef
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81486969"
---
# <a name="creating-user-defined-types---requirements"></a>Erstellen benutzerdefinierter Typen: Anforderungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Beim Erstellen eines benutzerdefinierten Typs (User-Defined Type, UDT), der in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert werden soll, müssen Sie einige wichtige Entwurfsentscheidungen treffen. Für die meisten UDTs wird das Erstellen als Struktur empfohlen, obwohl auch das Erstellen als Klasse möglich ist. Die UDT-Definition muss den Spezifikationen für das Erstellen von UDTs entsprechen, um mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert werden zu können.  
  
## <a name="requirements-for-implementing-udts"></a>Anforderungen für das Implementieren von UDTs  
 Um in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt zu werden, muss der UDT die folgenden Anforderungen in der UDT-Definition implementieren:  
  
 Der UDT muss das **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute-Attribut**angeben. Die Verwendung von **System. SerializableAttribute** ist optional, wird jedoch empfohlen.  
  
-   Der UDT muss die **System. Data. SqlTypes. INullable** -Schnittstelle in der Klasse oder Struktur implementieren, indem er eine öffentliche **statische** (**Shared** in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic) **null** -Methode erstellt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkennt standardmäßig NULL-Werte. Dies ist notwendig für Code, der im UDT ausgeführt wird, um in der Lage zu sein, einen NULL-Wert zu erkennen.  
  
-   Der UDT muss eine öffentliche **statische** (oder frei **gegebene**) Analysemethode enthalten, die die Analyse von unterstützt, sowie eine öffentliche **ToString** **-Methode für** die Typumwandlung in eine Zeichen folgen Darstellung des Objekts.  
  
-   Ein UDT mit einem benutzerdefinierten Serialisierungsformat muss die **System. Data. IBinarySerialize** -Schnittstelle implementieren und eine **Read** -und **Write** -Methode bereitstellen.  
  
-   Der UDT muss **System. Xml. Serialisierung. ixmlserialisierbar**implementieren, oder alle öffentlichen Felder und Eigenschaften müssen von Typen sein, die XML-serialisierbar sind oder mit dem **XmlIgnore** -Attribut ergänzt werden, wenn das Überschreiben der Standardserialisierung erforderlich ist.  
  
-   Es darf nur eine Serialisierung eines UDT-Objekts geben. Die Überprüfung schlägt fehl, wenn die Serialisierungs- oder Deserialisierungsroutinen mehr als eine Darstellung eines bestimmten Objekts erkennen.  
  
-   **SqlUserDefinedTypeAttribute. isbyteordermuss** " **true** " sein, um Daten in Byte Reihenfolge vergleichen zu können. Wenn die ivergleichbare Schnittstelle nicht implementiert ist und **SqlUserDefinedTypeAttribute. isbyteorder** auf **false**festgelegt ist, schlagen Byte Reihen folgen Vergleiche fehl.  
  
-   Ein in einer Klasse definierter UDT muss über einen öffentlichen Konstruktor verfügen, der keine Argumente verwendet. Sie können optional zusätzliche überladene Klassenkonstruktoren erstellen.  
  
-   Der UDT muss Datenelemente als öffentliche Felder oder Eigenschaftenprozeduren verfügbar machen.  
  
-   Öffentliche Namen dürfen nicht länger als 128 Zeichen sein, und Sie müssen den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Benennungs Regeln für Bezeichner entsprechen, wie in [Daten Bank bezeichnerdaten](../../relational-databases/databases/database-identifiers.md)definiert.  
  
-   **sql_variant** Spalten können keine Instanzen eines UDT enthalten.  
  
-   Auf vererbte Member kann nicht von [!INCLUDE[tsql](../../includes/tsql-md.md)] aus zugegriffen werden, da das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typsystem die Vererbungshierarchie zwischen UDTs nicht kennt. Sie können Vererbung allerdings verwenden, wenn Sie Klassen strukturieren, und Sie können diese Methoden in der verwalteten Codeimplementierung des Typs aufrufen.  
  
-   Mit Ausnahme des Klassenkonstruktors können Member nicht überladen werden. Wenn Sie eine überladene Methode erstellen, wird kein Fehler ausgelöst, wenn Sie die Assembly registrieren oder den Typ in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellen Erkennung der überladenen Methode tritt zur Laufzeit auf, nicht beim Erstellen des Typs. Überladene Methoden können in der Klasse vorhanden sein, solange sie nie aufgerufen werden. Sobald Sie eine überladene Methode aufrufen, wird ein Fehler ausgelöst.  
  
-   Alle **statischen** (oder frei **gegebenen**) Member müssen als Konstanten oder schreibgeschützt deklariert werden. Statische Member können nicht änderbar sein.  
  
-   Wenn das **SqlUserDefinedTypeAttribute. MaxByteSize** -Feld auf-1 festgelegt ist, kann der serialisierte UDT so groß wie das Lob-Größenlimit (Large Object) sein (aktuell 2 GB). Die Größe des UDT darf den im Feld " **MaxByteSize** " angegebenen Wert nicht überschreiten.  
  
> [!NOTE]  
>  Obwohl Sie nicht vom Server zum Durchführen von Vergleichen verwendet wird, können Sie optional die **System. ivergleichbare** -Schnittstelle implementieren, die eine einzelne Methode ( **CompareTo**) verfügbar macht. Diese Methode wird auf Clientseite in Situationen verwendet, in denen UDT-Werte präzise verglichen oder geordnet werden sollen.  
  
## <a name="native-serialization"></a>Systemeigene Serialisierung  
 Die Auswahl der richtigen Serialisierungsattribute für den UDT hängt vom Typ des UDTs ab, den Sie erstellen möchten. Das systemeigene Serialisierungsformat nutzt eine sehr einfache Struktur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mit der eine effiziente systemeigene Darstellung des UDTs **auf dem Daten** Träger gespeichert werden kann. Das **native** Format wird empfohlen, wenn der UDT einfach ist und nur Felder der folgenden Typen enthält:  
  
 **bool**, **Byte**, **SByte**, **Short**, **UShort**, **int**, **uint**, **Long**, **ulong**, **float**, **Double**, **SqlByte**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**, **SqlDouble**, **SqlMoney**, **SqlBoolean**  
  
 Werttypen, die aus Feldern der oben genannten Typen bestehen, sind gute **Kandidaten für das** systemeigene Format, z. b. Strukturen in Visual c#, (oder **Strukturen** , wie **Sie in Visual Basic** bekannt sind). Beispielsweise kann ein UDT, der mit dem systemeigenen Serialisierungsformat angegeben ist, ein Feld eines anderen UDT enthalten, **das auch** **mit dem System** eigenen Format angegeben wurde. Wenn die UDT-Definition komplexer ist und Datentypen enthält, die nicht in der obigen Liste aufgeführt sind, müssen Sie stattdessen das **benutzerdefinierte** Serialisierungsformat angeben.  
  
 Das **native** Format weist die folgenden Anforderungen auf:  
  
-   Der Typ darf keinen Wert für **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute. MaxByteSize**angeben.  
  
-   Alle Felder müssen serialisierbar sein.  
  
-   **System. Runtime. InteropServices. StructLayoutAttribute** muss als **StructLayout. LayoutKindSequential** angegeben werden, wenn der UDT in einer Klasse und nicht in einer Struktur definiert ist. Dieses Attribut steuert das physische Layout der Datenfelder und wird verwendet, um zu erzwingen, dass die Elemente in der Reihenfolge angeordnet werden, in der sie erscheinen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bestimmt anhand dieses Attributs die Feldreihenfolge für UDTs mit mehreren Werten.  
  
 Ein Beispiel für einen UDT, **der mit der** systemeigenen Serialisierung definiert ist, finden Sie unter Point UDT beim [Codieren von benutzerdefinierten Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
## <a name="userdefined-serialization"></a>UserDefined-Serialisierung  
 Die **benutzerdefinierte** Formateinstellung für das **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute** -Attribut ermöglicht dem Entwickler die vollständige Kontrolle über das Binärformat. Wenn Sie die **Format** Attribut Eigenschaft als **UserDefined**festlegen, müssen Sie im Code folgende Aktionen ausführen:  
  
-   Geben Sie die optionale Eigenschaft " **isbytegeordnete** Attribute" an. Der Standardwert ist **false**.  
  
-   Geben Sie die **MaxByteSize** -Eigenschaft des **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute-Attributs**an.  
  
-   Schreiben Sie Code, um Lese-und **Schreib** Methoden für den UDT zu implementieren, indem **Sie** die **System. Data. SQL. IBinarySerialize** -Schnittstelle implementieren.  
  
 Ein Beispiel für einen UDT, der mit der **benutzerdefinierten** Serialisierung definiert wird, finden Sie im Currency UDT unter Programmieren von [benutzerdefinierten Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
> [!NOTE]  
>  Für UDT-Felder muss die systemeigene Serialisierung verwendet werden, oder die Felder müssen erhalten bleiben, um indiziert zu werden.  
  
## <a name="serialization-attributes"></a>Serialisierungsattribute  
 Attribute bestimmen, wie die Serialisierung verwendet wird, um die Speicherdarstellung von UDTs zu erstellen und um UDTs durch Werte an den Client zu übertragen. Beim Erstellen des UDT müssen Sie das **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute-Attribut** angeben. Das **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute** -Attribut gibt an, dass die Klasse ein UDT ist, und gibt den Speicher für den UDT an. Sie können optional das **serialisierbare** Attribut angeben, obwohl [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dies nicht erforderlich ist.  
  
 Das **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute-Attribut** verfügt über die folgenden Eigenschaften.  
  
 **Format**  
 Gibt abhängig von den Datentypen des UDT das Serialisierungsformat an, das System **eigen oder** **Benutzer definiert**sein kann.  
  
 **IsByteOrdered**  
 Ein **boolescher** Wert, der bestimmt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wie binäre Vergleiche für den UDT ausführt.  
  
 **' IsFixedLength '**  
 Gibt an, ob alle Instanzen dieses UDTs dieselbe Länge haben.  
  
 **MaxByteSize**  
 Die maximale Größe der Instanz in Byte. Sie müssen **MaxByteSize** mit dem **benutzerdefinierten** Serialisierungsformat angeben. Für einen UDT mit der angegebenen benutzerdefinierten Serialisierung verweist **MaxByteSize** auf die Gesamtgröße des UDT in der vom benutzerdefinierten serialisierten Form. Der Wert von **MaxByteSize** muss im Bereich von 1 bis 8000 liegen, oder auf-1 festgelegt, um anzugeben, dass der UDT größer als 8000 Bytes ist (die Gesamtgröße darf die maximale Lob-Größe nicht überschreiten). Stellen Sie sich einen UDT mit einer-Eigenschaft mit einer Zeichenfolge von 10 Zeichen (**System. Char**) vor. Wenn der UDT anhand eines BinaryWriter serialisiert wird, beträgt die Gesamtgröße der serialisierten Zeichenfolge 22 Byte: 2 Byte pro Unicode-UTF-16-Zeichen, multipliziert mit der maximalen Anzahl von Zeichen, plus 2 Kontrollzeichen, die beim Serialisieren eines binären Datenstroms zusätzlich anfallen. Wenn Sie den Wert von **MaxByteSize**bestimmen, muss daher die Gesamtgröße des serialisierten UDT berücksichtigt werden: die Größe der in Binär Form serialisierten Daten zuzüglich des durch die Serialisierung verursachten Aufwands.  
  
 **ValidationMethodName**  
 Der Name der Methode, mit der Instanzen des UDTs überprüft werden.  
  
### <a name="setting-isbyteordered"></a>Einstellung 'IsByteOrdered'  
 Wenn die **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute. isbyteorder** -Eigenschaft auf **true**festgelegt ist, stellen Sie sicher, dass die serialisierten Binärdaten für die semantische Reihenfolge der Informationen verwendet werden können. So kann jede Instanz eines UDT-Objekts mit Bytereihenfolge nur eine einzige serialisierte Darstellung haben. Die Ausführung eines Vergleichsvorgangs für die serialisierten Bytes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollte zu denselben Resultaten führen wie der entsprechende Vergleichsvorgang für verwalteten Code. Die folgenden Funktionen werden ebenfalls unterstützt, wenn **isbyteorderauf** **true**festgelegt ist:  
  
-   Die Fähigkeit zum Erstellen von Indizes für Spalten dieses Typs  
  
-   Die Fähigkeit, für Spalten dieses Typs Primär- und Fremdschlüssel sowie die Einschränkungen CHECK und UNIQUE zu erstellen  
  
-   Die Fähigkeit, [!INCLUDE[tsql](../../includes/tsql-md.md)]-ORDER BY-, GROUP BY- und PARTITION BY-Klauseln zu verwenden. In diesen Fällen wird die binäre Darstellung des Typs verwendet, um die Reihenfolge zu bestimmen  
  
-   Die Fähigkeit, Vergleichsoperatoren in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen zu verwenden  
  
-   Die Fähigkeit, berechnete Spalten dieses Typs persistent zu speichern  
  
 Beachten Sie, dass sowohl das **native** als auch das **benutzerdefinierte** Serialisierungsformat die folgenden Vergleichs Operatoren unterstützen, wenn **isbyteorderauf** **true**festgelegt ist:  
  
-   Gleich (=)  
  
-   Ungleich (!=)  
  
-   Größer als (>)  
  
-   Kleiner als (\<)  
  
-   Größer als oder gleich (>=)  
  
-   Kleiner oder gleich (<=)  
  
### <a name="implementing-nullability"></a>Implementieren von NULL-Zulässigkeit  
 Zusätzlich zum ordnungsgemäßen Angeben der Attribute für die Assemblys muss die Klasse auch NULL-Zulässigkeit unterstützen. UDTs, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in geladen werden, sind NULL-fähig, aber damit der UDT einen NULL-Wert erkennt, muss die Klasse die **INullable** -Schnittstelle implementieren. Weitere Informationen und ein Beispiel für die Implementierung der NULL-Zulässigkeit in einem UDT finden Sie unter Programmieren von [benutzerdefinierten Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
### <a name="string-conversions"></a>Zeichenfolgenkonvertierungen  
 Um die Zeichen folgen Konvertierung in und aus dem UDT zu unterstützen, müssen Sie eine **Analysemethode und eine Methode "** **destring** " in der Klasse bereitstellen. Mit **der Analyse** Methode kann eine Zeichenfolge in einen UDT konvertiert werden. Er muss als **statisch** deklariert werden (oder in Visual Basic frei **gegeben** werden) und einen Parameter vom Typ **System. Data. SqlTypes. SqlString**annehmen. Weitere Informationen und ein Beispiel für die Implementierung der Methoden "Analyse" und " **ToString** " finden Sie unter Program **mieren** [benutzerdefinierter Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
## <a name="xml-serialization"></a>XML-Serialisierung  
 UDTs müssen die Konvertierung in und aus dem **XML** -Datentyp unterstützen, indem Sie dem Vertrag für die XML-Serialisierung entsprechen. Der **System. Xml. Serialization** -Namespace enthält Klassen, die zum Serialisieren von Objekten in Dokumente oder Streams im XML-Format verwendet werden. Sie können die **XML** -Serialisierung mithilfe der **ixmlserialisierbaren** -Schnittstelle implementieren, die eine benutzerdefinierte Formatierung für die XML-Serialisierung und-Deserialisierung bereitstellt.  
  
 Zusätzlich zum Ausführen expliziter Konvertierungen von UDT in **XML**ermöglicht Ihnen die XML-Serialisierung Folgendes:  
  
-   Verwenden Sie **XQuery** für Werte von UDT-Instanzen nach der Konvertierung in den **XML** -Datentyp.  
  
-   Verwenden von UDTs in parametrisierten Abfragen und Webmethoden mit systemeigenen XML-Webdiensten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Verwenden von UDTs, um ein Massenladen von XML-Daten durchzuführen.  
  
-   Serialisieren von DataSets, die Tabellen mit UDT-Spalten enthalten.  
  
 UDTs werden nicht in FOR XML-Abfragen serialisiert. Um eine for XML-Abfrage auszuführen, die die XML-Serialisierung von UDTs anzeigt, konvertieren Sie jede UDT-Spalte explizit in den **XML** -Datentyp in der SELECT-Anweisung. Sie können die Spalten auch explizit in **varbinary**, **varchar**oder **nvarchar**konvertieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines benutzerdefinierten Typs](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
