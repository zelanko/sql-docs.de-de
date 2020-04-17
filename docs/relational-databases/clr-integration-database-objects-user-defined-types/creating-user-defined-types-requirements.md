---
title: Benutzerdefinierte Typanforderungen | Microsoft Docs
description: In diesem Artikel werden wichtige Entwurfsentscheidungen beschrieben, die Sie beim Erstellen einer UDT für die Installation auf SQL Server treffen müssen.
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486969"
---
# <a name="creating-user-defined-types---requirements"></a>Erstellen benutzerdefinierter Typen: Anforderungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Sie müssen mehrere wichtige Entwurfsentscheidungen treffen, wenn Sie einen benutzerdefinierten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Typ (UDT) erstellen, der in installiert werden soll. Für die meisten UDTs wird das Erstellen als Struktur empfohlen, obwohl auch das Erstellen als Klasse möglich ist. Die UDT-Definition muss den Spezifikationen für das Erstellen von UDTs entsprechen, um mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert werden zu können.  
  
## <a name="requirements-for-implementing-udts"></a>Anforderungen für das Implementieren von UDTs  
 Um in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt zu werden, muss der UDT die folgenden Anforderungen in der UDT-Definition implementieren:  
  
 Die UDT muss die **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**angeben. Die Verwendung von **System.SerializableAttribute** ist optional, wird jedoch empfohlen.  
  
-   Die UDT muss die **System.Data.SqlTypes.INullable-Schnittstelle** in der Klasse oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Struktur implementieren, indem eine öffentliche **statische** (in Visual Basic**freigegebene)** **Null-Methode** erstellt wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkennt standardmäßig NULL-Werte. Dies ist notwendig für Code, der im UDT ausgeführt wird, um in der Lage zu sein, einen NULL-Wert zu erkennen.  
  
-   Die UDT muss eine öffentliche **statische** (oder **freigegebene**) **Parse-Methode** enthalten, die das Analysieren von unterstützt, und eine öffentliche **ToString-Methode** zum Konvertieren in eine Zeichenfolgendarstellung des Objekts.  
  
-   Eine UDT mit einem benutzerdefinierten Serialisierungsformat muss die **Schnittstelle System.Data.IBinarySerialize** implementieren und eine **Read-** und eine **Write-Methode** bereitstellen.  
  
-   Die UDT muss **System.Xml.Serialization.IXmlSerializable**implementieren, oder alle öffentlichen Felder und Eigenschaften müssen von Typen sein, die XML serialisierbar sind oder mit dem **XmlIgnore-Attribut** versehen sind, wenn eine überschreibende Standardserialisierung erforderlich ist.  
  
-   Es darf nur eine Serialisierung eines UDT-Objekts geben. Die Überprüfung schlägt fehl, wenn die Serialisierungs- oder Deserialisierungsroutinen mehr als eine Darstellung eines bestimmten Objekts erkennen.  
  
-   **SqlUserDefinedTypeAttribute.IsByteOrdered** muss **true** sein, um Daten in Bytereihenfolge zu vergleichen. Wenn die IComparable-Schnittstelle nicht implementiert ist und **SqlUserDefinedTypeAttribute.IsByteOrdered** **false**ist, schlagen Bytereihenfolgevergleiche fehl.  
  
-   Ein in einer Klasse definierter UDT muss über einen öffentlichen Konstruktor verfügen, der keine Argumente verwendet. Sie können optional zusätzliche überladene Klassenkonstruktoren erstellen.  
  
-   Der UDT muss Datenelemente als öffentliche Felder oder Eigenschaftenprozeduren verfügbar machen.  
  
-   Öffentliche Namen dürfen nicht länger als 128 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeichen sein und müssen den Namensregeln für Bezeichner entsprechen, wie in [Datenbankbezeichnern](../../relational-databases/databases/database-identifiers.md)definiert.  
  
-   **sql_variant** Spalten dürfen keine Instanzen einer UDT enthalten.  
  
-   Auf vererbte Member kann nicht von [!INCLUDE[tsql](../../includes/tsql-md.md)] aus zugegriffen werden, da das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typsystem die Vererbungshierarchie zwischen UDTs nicht kennt. Sie können Vererbung allerdings verwenden, wenn Sie Klassen strukturieren, und Sie können diese Methoden in der verwalteten Codeimplementierung des Typs aufrufen.  
  
-   Mit Ausnahme des Klassenkonstruktors können Member nicht überladen werden. Wenn Sie eine überladene Methode erstellen, wird kein Fehler ausgelöst, wenn Sie die Assembly registrieren oder den Typ in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellen Erkennung der überladenen Methode tritt zur Laufzeit auf, nicht beim Erstellen des Typs. Überladene Methoden können in der Klasse vorhanden sein, solange sie nie aufgerufen werden. Sobald Sie eine überladene Methode aufrufen, wird ein Fehler ausgelöst.  
  
-   **Alle statischen** (oder **freigegebenen**) Member müssen als Konstanten oder als schreibgeschützt deklariert werden. Statische Member können nicht änderbar sein.  
  
-   Wenn das Feld **SqlUserDefinedTypeAttribute.MaxByteSize** auf -1 festgelegt ist, kann die serialisierte UDT so groß sein wie die Größenbeschränkung für große Objekte (LOB) (derzeit 2 GB). Die Größe der UDT darf den im Feld **MaxByteSized** angegebenen Wert nicht überschreiten.  
  
> [!NOTE]  
>  Obwohl es vom Server nicht für Vergleiche verwendet wird, können Sie optional die **System.IComparable-Schnittstelle** implementieren, die eine einzelne Methode verfügbar macht, **CompareTo**. Diese Methode wird auf Clientseite in Situationen verwendet, in denen UDT-Werte präzise verglichen oder geordnet werden sollen.  
  
## <a name="native-serialization"></a>Systemeigene Serialisierung  
 Die Auswahl der richtigen Serialisierungsattribute für den UDT hängt vom Typ des UDTs ab, den Sie erstellen möchten. Das **native** Serialisierungsformat verwendet eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sehr einfache Struktur, die es ermöglicht, eine effiziente systemeigene Darstellung der UDT auf dem Datenträger zu speichern. Das **native** Format wird empfohlen, wenn die UDT einfach ist und nur Felder der folgenden Typen enthält:  
  
 **bool**, **byte**, **sbyte**, **short**, **ushort**, **int**, **uint**, **long**, **ulong**, **float**, **double**, **SqlByte**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**, **SqlDouble**, SqlMoney , **SqlMoney**, **SqlBoolean**  
  
 Werttypen, die aus Feldern der oben genannten Typen bestehen, sind gute Kandidaten für das **systemeigene** Format, z. B. **Strukturen** in Visual C(oder **Strukturen,** wie sie in Visual Basic bekannt sind). Beispielsweise kann eine UDT, die mit dem **nativen** Serialisierungsformat angegeben ist, ein Feld einer anderen UDT enthalten, die ebenfalls mit dem **nativen** Format angegeben wurde. Wenn die UDT-Definition komplexer ist und Datentypen enthält, die **UserDefined** nicht in der obigen Liste aufgeführt sind, müssen Sie stattdessen das UserDefined-Serialisierungsformat angeben.  
  
 Das **native** Format hat die folgenden Anforderungen:  
  
-   Der Typ darf keinen Wert für **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.MaxByteSize**angeben.  
  
-   Alle Felder müssen serialisierbar sein.  
  
-   Die **System.Runtime.InteropServices.StructLayoutAttribute** müssen als **StructLayout.LayoutKindSequential** angegeben werden, wenn die UDT in einer Klasse und nicht in einer Struktur definiert ist. Dieses Attribut steuert das physische Layout der Datenfelder und wird verwendet, um zu erzwingen, dass die Elemente in der Reihenfolge angeordnet werden, in der sie erscheinen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bestimmt anhand dieses Attributs die Feldreihenfolge für UDTs mit mehreren Werten.  
  
 Ein Beispiel für eine UDT, die mit **nativer** Serialisierung definiert ist, finden Sie im Point UDT in [Coding User-Defined Types](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
## <a name="userdefined-serialization"></a>UserDefined-Serialisierung  
 Die **UserDefined-Formateinstellung** für das **Attribut Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** gibt dem Entwickler die volle Kontrolle über das Binärformat. Wenn Sie **Format** die Format-Attributeigenschaft als **UserDefined**angeben, müssen Sie im Code Folgendes tun:  
  
-   Geben Sie die optionale **IsByteOrdered-Attributeigenschaft** an. Der Standardwert ist **false**.  
  
-   Geben Sie die **MaxByteSize-Eigenschaft** der **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**an.  
  
-   Schreiben Sie Code, um **Lese-** und **Schreibmethoden** für die UDT zu implementieren, indem Sie die **Schnittstelle System.Data.Sql.IBinarySerialize** implementieren.  
  
 Ein Beispiel für eine UDT, die mit **UserDefined-Serialisierung** definiert ist, finden Sie unter Currency UDT in [Coding Benutzerdefinierte Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
> [!NOTE]  
>  Für UDT-Felder muss die systemeigene Serialisierung verwendet werden, oder die Felder müssen erhalten bleiben, um indiziert zu werden.  
  
## <a name="serialization-attributes"></a>Serialisierungsattribute  
 Attribute bestimmen, wie die Serialisierung verwendet wird, um die Speicherdarstellung von UDTs zu erstellen und um UDTs durch Werte an den Client zu übertragen. Sie müssen beim Erstellen der UDT **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** angeben. Das **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute-Attribut** gibt an, dass es sich bei der Klasse um eine UDT handelt, und gibt den Speicher für die UDT an. Sie können optional das **Serialisierbar-Attribut** angeben, erfordern dies jedoch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht.  
  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** verfügt über die folgenden Eigenschaften.  
  
 **Format**  
 Gibt das Serialisierungsformat an, das **systemativ** oder **UserDefined**sein kann, abhängig von den Datentypen der UDT.  
  
 **IsByteOrdered**  
 Ein **boolescher** Wert, der bestimmt, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binäre Vergleiche für die UDT durchgeführt werden.  
  
 **IsFixedLength**  
 Gibt an, ob alle Instanzen dieses UDTs dieselbe Länge haben.  
  
 **MaxByteSize**  
 Die maximale Größe der Instanz in Byte. Sie müssen **MaxByteSize** mit dem UserDefined-Serialisierungsformat angeben. **UserDefined** Für eine UDT mit benutzerdefinierter Serialisierung, die angegeben ist, bezieht sich **MaxByteSize** auf die Gesamtgröße der UDT in ihrer serialisierten Form, wie vom Benutzer definiert. Der Wert von **MaxByteSize** muss im Bereich von 1 bis 8000 liegen oder auf -1 festgelegt sein, um anzugeben, dass die UDT größer als 8000 Byte ist (die Gesamtgröße darf die maximale Lobgröße nicht überschreiten). Betrachten Sie eine UDT mit einer Eigenschaft von 10 Zeichen (**System.Char**). Wenn der UDT anhand eines BinaryWriter serialisiert wird, beträgt die Gesamtgröße der serialisierten Zeichenfolge 22 Byte: 2 Byte pro Unicode-UTF-16-Zeichen, multipliziert mit der maximalen Anzahl von Zeichen, plus 2 Kontrollzeichen, die beim Serialisieren eines binären Datenstroms zusätzlich anfallen. Daher muss bei der Bestimmung des Werts von **MaxByteSize**die Gesamtgröße der serialisierten UDT berücksichtigt werden: die Größe der in binärer Form serialisierten Daten zuzüglich des Durchstehens, der durch die Serialisierung entsteht.  
  
 **ValidationMethodName**  
 Der Name der Methode, mit der Instanzen des UDTs überprüft werden.  
  
### <a name="setting-isbyteordered"></a>Einstellung 'IsByteOrdered'  
 Wenn die **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.IsByteOrdered-Eigenschaft** auf **true**festgelegt ist, garantieren Sie, dass die serialisierten Binärdaten für die semantische Sortierung der Informationen verwendet werden können. So kann jede Instanz eines UDT-Objekts mit Bytereihenfolge nur eine einzige serialisierte Darstellung haben. Die Ausführung eines Vergleichsvorgangs für die serialisierten Bytes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollte zu denselben Resultaten führen wie der entsprechende Vergleichsvorgang für verwalteten Code. Die folgenden Funktionen werden auch unterstützt, wenn **IsByteOrdered** auf **true**festgelegt ist:  
  
-   Die Fähigkeit zum Erstellen von Indizes für Spalten dieses Typs  
  
-   Die Fähigkeit, für Spalten dieses Typs Primär- und Fremdschlüssel sowie die Einschränkungen CHECK und UNIQUE zu erstellen  
  
-   Die Fähigkeit, [!INCLUDE[tsql](../../includes/tsql-md.md)]-ORDER BY-, GROUP BY- und PARTITION BY-Klauseln zu verwenden. In diesen Fällen wird die binäre Darstellung des Typs verwendet, um die Reihenfolge zu bestimmen  
  
-   Die Fähigkeit, Vergleichsoperatoren in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen zu verwenden  
  
-   Die Fähigkeit, berechnete Spalten dieses Typs persistent zu speichern  
  
 Beachten Sie, dass sowohl die Serialisierungsformate **Native als** auch **UserDefined** die folgenden Vergleichsoperatoren unterstützen, wenn **IsByteOrdered** auf **true**festgelegt ist:  
  
-   Gleich (=)  
  
-   Ungleich (!=)  
  
-   Größer als (>)  
  
-   Kleiner als (\<)  
  
-   Größer als oder gleich (>=)  
  
-   Kleiner oder gleich (<=)  
  
### <a name="implementing-nullability"></a>Implementieren von NULL-Zulässigkeit  
 Zusätzlich zum ordnungsgemäßen Angeben der Attribute für die Assemblys muss die Klasse auch NULL-Zulässigkeit unterstützen. UDTs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die in geladen werden, sind null-fähig, aber damit die UDT einen NULL-Wert erkennen kann, muss die Klasse die **INullable-Schnittstelle** implementieren. Weitere Informationen und ein Beispiel für die Implementierung der null-Zulässigkeit in einer UDT finden Sie unter [Codieren benutzerdefinierter Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
### <a name="string-conversions"></a>Zeichenfolgenkonvertierungen  
 Um die Zeichenfolgenkonvertierung in und aus der UDT zu unterstützen, müssen Sie in Ihrer Klasse eine **Parse-Methode** und eine **ToString-Methode** bereitstellen. Mit der **Parse-Methode** kann eine Zeichenfolge in eine UDT konvertiert werden. Sie muss als **statisch** (oder **freigegeben** in Visual Basic) deklariert werden und einen Parameter vom Typ **System.Data.SqlTypes.SqlString**annehmen. Weitere Informationen und ein Beispiel zum Implementieren der **Parse-** und **ToString-Methoden** finden Sie unter [Codieren benutzerdefinierter Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
## <a name="xml-serialization"></a>XML-Serialisierung  
 UDTs müssen die Konvertierung in und aus dem **XML-Datentyp** unterstützen, indem sie dem Vertrag für die XML-Serialisierung entsprechen. Der **Namespace System.Xml.Serialization** enthält Klassen, die zum Serialisieren von Objekten in Dokumente oder Streams im XML-Format verwendet werden. Sie können die **XML-Serialisierung** mithilfe der **IXmlSerializable-Schnittstelle** implementieren, die benutzerdefinierte Formatierungen für die XML-Serialisierung und Deserialisierung bereitstellt.  
  
 Zusätzlich zur Durchführung expliziter Konvertierungen von UDT in **XML**ermöglicht Ihnen die XML-Serialisierung:  
  
-   Verwenden Sie **Xquery** over-Werte von UDT-Instanzen nach der Konvertierung in den **XML-Datentyp.**  
  
-   Verwenden von UDTs in parametrisierten Abfragen und Webmethoden mit systemeigenen XML-Webdiensten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Verwenden von UDTs, um ein Massenladen von XML-Daten durchzuführen.  
  
-   Serialisieren von DataSets, die Tabellen mit UDT-Spalten enthalten.  
  
 UDTs werden nicht in FOR XML-Abfragen serialisiert. Um eine FOR XML-Abfrage auszuführen, die die XML-Serialisierung von UDTs anzeigt, konvertieren Sie explizit jede UDT-Spalte in den **XML-Datentyp** in der SELECT-Anweisung. Sie können die Spalten auch explizit in **varbinary**, **varchar**oder **nvarchar**konvertieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines benutzerdefinierten Typs](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
