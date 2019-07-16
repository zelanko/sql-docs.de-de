---
title: Eine benutzerdefinierte Typanforderungen | Microsoft-Dokumentation
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
ms.openlocfilehash: 7fc3da1474546f0719af20c52f44248baa8ce5da
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028259"
---
# <a name="creating-user-defined-types---requirements"></a>Erstellen benutzerdefinierter Typen: Anforderungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Sie müssen mehrere wichtige entwurfsentscheidungen beim Erstellen eines benutzerdefinierten Typs (UDT), für die Installation in, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Für die meisten UDTs wird das Erstellen als Struktur empfohlen, obwohl auch das Erstellen als Klasse möglich ist. Die UDT-Definition muss den Spezifikationen für das Erstellen von UDTs entsprechen, um mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert werden zu können.  
  
## <a name="requirements-for-implementing-udts"></a>Anforderungen für das Implementieren von UDTs  
 Um in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt zu werden, muss der UDT die folgenden Anforderungen in der UDT-Definition implementieren:  
  
 Geben Sie der UDT muss die **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**. Die Verwendung der **System.SerializableAttribute** ist optional, jedoch empfohlen.  
  
-   Muss der UDT implementieren die **System.Data.SqlTypes.INullable** -Schnittstelle in der Klasse oder Struktur durch Erstellen einer öffentlichen **statische** (**Shared** in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic) **Null** Methode. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkennt standardmäßig NULL-Werte. Dies ist notwendig für Code, der im UDT ausgeführt wird, um in der Lage zu sein, einen NULL-Wert zu erkennen.  
  
-   Der UDT muss eine öffentliche enthalten **statische** (oder **Shared**) **analysieren** -Methode, die Analysen unterstützt, sowie eine öffentliche **ToString** -Methode für Konvertieren in eine Zeichenfolgendarstellung des Objekts.  
  
-   Für ein benutzerdefiniertes Serialisierungsformat, das ein UDT muss implementieren die **System.Data.IBinarySerialize** Schnittstelle, und geben Sie einen **lesen** und ein **schreiben** Methode.  
  
-   Muss der UDT implementieren **System.Xml.Serialization.IXmlSerializable**, oder alle öffentlichen Felder und Eigenschaften von Typen, die XML-serialisierbar sind oder mit müssen die **XmlIgnore** Attribut, wenn Überschreiben einer Standardserialisierung ist erforderlich.  
  
-   Es darf nur eine Serialisierung eines UDT-Objekts geben. Die Überprüfung schlägt fehl, wenn die Serialisierungs- oder Deserialisierungsroutinen mehr als eine Darstellung eines bestimmten Objekts erkennen.  
  
-   **SqlUserDefinedTypeAttribute.IsByteOrdered** muss **"true"** , Daten in Bytereihenfolge zu vergleichen. Wenn die IComparable-Schnittstelle nicht implementiert ist und **SqlUserDefinedTypeAttribute.IsByteOrdered** ist **"false"** , Vergleiche in Bytereihenfolge fehl.  
  
-   Ein in einer Klasse definierter UDT muss über einen öffentlichen Konstruktor verfügen, der keine Argumente verwendet. Sie können optional zusätzliche überladene Klassenkonstruktoren erstellen.  
  
-   Der UDT muss Datenelemente als öffentliche Felder oder Eigenschaftenprozeduren verfügbar machen.  
  
-   Öffentliche Namen darf nicht länger als 128 Zeichen lang sein und muss entsprechen den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benennungsregeln für Bezeichner gemäß [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
-   **Sql_variant** -Spalten können keine Instanzen eines UDTS enthalten.  
  
-   Auf vererbte Member kann nicht von [!INCLUDE[tsql](../../includes/tsql-md.md)] aus zugegriffen werden, da das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typsystem die Vererbungshierarchie zwischen UDTs nicht kennt. Sie können Vererbung allerdings verwenden, wenn Sie Klassen strukturieren, und Sie können diese Methoden in der verwalteten Codeimplementierung des Typs aufrufen.  
  
-   Mit Ausnahme des Klassenkonstruktors können Member nicht überladen werden. Wenn Sie eine überladene Methode erstellen, wird kein Fehler ausgelöst, wenn Sie die Assembly registrieren oder den Typ in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellen Erkennung der überladenen Methode tritt zur Laufzeit auf, nicht beim Erstellen des Typs. Überladene Methoden können in der Klasse vorhanden sein, solange sie nie aufgerufen werden. Sobald Sie eine überladene Methode aufrufen, wird ein Fehler ausgelöst.  
  
-   Alle **statische** (oder **Shared**) Member müssen als Konstanten deklariert oder als schreibgeschützt sein. Statische Member können nicht änderbar sein.  
  
-   Wenn die **SqlUserDefinedTypeAttribute.MaxByteSize** -Feld auf-1 festgelegt ist, die serialisierte UDT so groß wie die größenbeschränkung für große Objekte (LOB) (zurzeit 2 GB) möglich ist. Die Größe des UDT kann nicht den im angegebenen Wert überschreitet den **MaxByteSized** Feld.  
  
> [!NOTE]  
>  Obwohl es vom Server zum Durchführen von Vergleichen nicht verwendet wird, können Sie optional implementieren die **System.IComparable** -Schnittstelle, die eine einzelne Methode verfügbar macht, **"CompareTo"** . Diese Methode wird auf Clientseite in Situationen verwendet, in denen UDT-Werte präzise verglichen oder geordnet werden sollen.  
  
## <a name="native-serialization"></a>Systemeigene Serialisierung  
 Die Auswahl der richtigen Serialisierungsattribute für den UDT hängt vom Typ des UDTs ab, den Sie erstellen möchten. Die **Native** Serialisierungsformat nutzt eine sehr einfache Struktur, die es ermöglicht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um eine effiziente systemeigene Darstellung des UDTS auf dem Datenträger zu speichern. Die **Native** Format wird empfohlen, wenn der UDT einfach ist, und enthält nur die Felder der folgenden Typen:  
  
 **"bool"** , **Byte**, **Sbyte**, **kurze**, **Ushort**, **Int**,  **Uint**, **lange**, **Ulong**, **"float"** , **doppelte**, **Value**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**,  **SqlDouble**, **SqlMoney**, **SqlBoolean**  
  
 Werttypen, die zusammengesetzt sind Felder, die oben genannten Typen eignen sich gut für **Native** format, z. B. **Strukturen** in Visual c# (oder **Strukturen** wie in der sie bekannt sind Visual Basic). Ein UDT beispielsweise angegeben, mit der **Native** Serialisierungsformat darf auf ein Feld eines anderen UDTS, die auch mit angegeben wurde der **Native** Format. Wenn die UDT-Definition komplexer ist und Datentypen, die nicht in der obigen Liste enthält, geben Sie die **UserDefined** Serialisierungsformat stattdessen.  
  
 Die **Native** Format hat die folgenden Anforderungen:  
  
-   Der Typ muss keinen Wert für **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.MaxByteSize**.  
  
-   Alle Felder müssen serialisierbar sein.  
  
-   Die **System.Runtime.InteropServices.StructLayoutAttribute** muss angegeben werden, als **StructLayout.LayoutKindSequential** ist der UDT in einer Klasse und nicht in einer Struktur definiert wird. Dieses Attribut steuert das physische Layout der Datenfelder und wird verwendet, um zu erzwingen, dass die Elemente in der Reihenfolge angeordnet werden, in der sie erscheinen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bestimmt anhand dieses Attributs die Feldreihenfolge für UDTs mit mehreren Werten.  
  
 Ein Beispiel für einen UDT mit definierten **Native** Serialisierung finden Sie unter der Point-UDT in [Codieren benutzerdefinierter Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
## <a name="userdefined-serialization"></a>UserDefined-Serialisierung  
 Die **UserDefined** -formateinstellung für das **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** -Attribut gibt dem Entwickler volle Kontrolle über das Binärformat. Beim Angeben der **Format** -Attributeigenschaft als **UserDefined**, müssen Sie Folgendes in Ihrem Code:  
  
-   Geben Sie den optionalen **IsByteOrdered** Attributeigenschaft. Der Standardwert ist **false**.  
  
-   Geben Sie die **MaxByteSize** Eigenschaft der **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**.  
  
-   Schreiben Sie Code zum Implementieren von **lesen** und **schreiben** Methoden für den UDT durch die Implementierung der **System.Data.Sql.IBinarySerialize** Schnittstelle.  
  
 Ein Beispiel für einen UDT mit definierten **UserDefined** Serialisierung finden Sie im Currency-UDT in [Codieren benutzerdefinierter Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
> [!NOTE]  
>  Für UDT-Felder muss die systemeigene Serialisierung verwendet werden, oder die Felder müssen erhalten bleiben, um indiziert zu werden.  
  
## <a name="serialization-attributes"></a>Serialisierungsattribute  
 Attribute bestimmen, wie die Serialisierung verwendet wird, um die Speicherdarstellung von UDTs zu erstellen und um UDTs durch Werte an den Client zu übertragen. Sie müssen sich an den **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** beim Erstellen des UDTS. Die **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** Attribut gibt an, dass die Klasse ein UDT ist, und den Speicher für den UDT gibt. Sie können optional angeben, die **Serializable** Attribut, obwohl [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dieses nicht erfordert.  
  
 Die **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** hat die folgenden Eigenschaften.  
  
 **Format**  
 Gibt das Serialisierungsformat an, die möglicherweise **Native** oder **UserDefined**, je nachdem, auf den Datentypen des UDTS.  
  
 **IsByteOrdered**  
 Ein **booleschen** -Wert, der bestimmt, wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binäre Vergleiche auf dem UDT ausführt.  
  
 **IsFixedLength**  
 Gibt an, ob alle Instanzen dieses UDTs dieselbe Länge haben.  
  
 **MaxByteSize**  
 Die maximale Größe der Instanz in Byte. Sie müssen angeben, **MaxByteSize** mit der **UserDefined** Serialisierungsformat. Für einen UDT mit der eine benutzerdefinierte Serialisierung festgelegt ist **MaxByteSize** bezieht sich auf die Gesamtgröße des UDTS in seiner serialisierten Form, wie vom Benutzer definiert. Der Wert des **MaxByteSize** muss zwischen 1 und 8000 liegen oder auf-1 festgelegt wird, um anzugeben, dass der UDT größer als 8000 Bytes (die Gesamtgröße darf nicht die maximale LOB-Größe nicht überschreiten). Angenommen, ein UDT mit einer Eigenschaft eine Zeichenfolge von 10 Zeichen (**System.Char**). Wenn der UDT anhand ein BinaryWriter serialisiert wird, ist die Gesamtgröße der serialisierten Zeichenfolge 22 Bytes: 2 Bytes pro Unicode UTF-16-Zeichen, multipliziert die maximale Anzahl von Zeichen, plus 2 muss das Steuerelement Bytes Kontrollzeichen Serialisieren eines binären Datenstroms zusätzlich anfallen. Aus diesem Grund beim Bestimmen des Werts des **MaxByteSize**, beträgt die Gesamtgröße der serialisierten UDT berücksichtigt werden muss: die Größe der ins Binärformat serialisierten Daten plus der anfallenden für die Serialisierung.  
  
 **ValidationMethodName**  
 Der Name der Methode, mit der Instanzen des UDTs überprüft werden.  
  
### <a name="setting-isbyteordered"></a>Einstellung 'IsByteOrdered'  
 Wenn die **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.IsByteOrdered** -Eigenschaftensatz auf **"true"** , Sie sind sicher, dass die serialisierten Binärdaten für verwendet werden können semantische Sortierung der Informationen. So kann jede Instanz eines UDT-Objekts mit Bytereihenfolge nur eine einzige serialisierte Darstellung haben. Die Ausführung eines Vergleichsvorgangs für die serialisierten Bytes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sollte zu denselben Resultaten führen wie der entsprechende Vergleichsvorgang für verwalteten Code. Die folgenden Funktionen werden ebenfalls unterstützt, wenn **IsByteOrdered** nastaven NA hodnotu **"true"** :  
  
-   Die Fähigkeit zum Erstellen von Indizes für Spalten dieses Typs  
  
-   Die Fähigkeit, für Spalten dieses Typs Primär- und Fremdschlüssel sowie die Einschränkungen CHECK und UNIQUE zu erstellen  
  
-   Die Fähigkeit, [!INCLUDE[tsql](../../includes/tsql-md.md)]-ORDER BY-, GROUP BY- und PARTITION BY-Klauseln zu verwenden. In diesen Fällen wird die binäre Darstellung des Typs verwendet, um die Reihenfolge zu bestimmen  
  
-   Die Fähigkeit, Vergleichsoperatoren in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen zu verwenden  
  
-   Die Fähigkeit, berechnete Spalten dieses Typs persistent zu speichern  
  
 Beachten Sie, dass sowohl die **Native** und **UserDefined** Serialisierungsformate unterstützen die folgenden Vergleichsoperatoren beim **IsByteOrdered** nastaven NA hodnotu **"true"** :  
  
-   Gleich (=)  
  
-   Ungleich (!=)  
  
-   Größer als (>)  
  
-   Kleiner als (\<)  
  
-   Größer als oder gleich (> =)  
  
-   Kleiner als oder gleich (< =)  
  
### <a name="implementing-nullability"></a>Implementieren von NULL-Zulässigkeit  
 Zusätzlich zum ordnungsgemäßen Angeben der Attribute für die Assemblys muss die Klasse auch NULL-Zulässigkeit unterstützen. UDTs, die geladenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Nullwerte, aber in der Reihenfolge der UDT einen Nullwert erkennt, muss die Klasse implementieren die **INullable** Schnittstelle. Weitere Informationen und ein Beispiel dafür, wie NULL-Zulässigkeit in einem UDT zu implementieren, finden Sie unter [Codieren benutzerdefinierter Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
### <a name="string-conversions"></a>Zeichenfolgenkonvertierungen  
 Zur Unterstützung der zeichenfolgenkonvertierung in und aus UDTS müssen Sie angeben einer **analysieren** Methode und eine **ToString** -Methode in der Klasse. Die **analysieren** -Methode ermöglicht es, eine Zeichenfolge in einen UDT konvertiert werden soll. Es muss deklariert werden, als **statische** (oder **Shared** in Visual Basic), und einen Parameter vom Typ **System.Data.SqlTypes.SqlString**. Weitere Informationen und ein Beispiel zum Implementieren der **analysieren** und **ToString** Methoden finden Sie unter [Codieren benutzerdefinierter Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
## <a name="xml-serialization"></a>XML-Serialisierung  
 UDTs Konvertierung unterstützen müssen, in und aus der **Xml** -Datentyp gemäß dem Vertrag für die XML-Serialisierung. Die **System.Xml.Serialization** -Namespace enthält Klassen, die zum Serialisieren von Objekten in XML-Format Dokumente oder Streams im verwendet werden. Sie können auch implementieren **Xml** Serialisierung unter Verwendung der **IXmlSerializable** -Schnittstelle, die benutzerdefinierte Formatierung bereitstellt, für die XML-Serialisierung und Deserialisierung.  
  
 Zusätzlich zum Durchführen expliziter Konvertierungen von UDT **Xml**, XML-Serialisierung können Sie:  
  
-   Verwendung **Xquery** für Werte von UDT-Instanzen nach der Konvertierung in den **Xml** -Datentyp.  
  
-   Verwenden von UDTs in parametrisierten Abfragen und Webmethoden mit systemeigenen XML-Webdiensten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Verwenden von UDTs, um ein Massenladen von XML-Daten durchzuführen.  
  
-   Serialisieren von DataSets, die Tabellen mit UDT-Spalten enthalten.  
  
 UDTs werden nicht in FOR XML-Abfragen serialisiert. Um eine FOR XML-Abfrage auszuführen, die die XML-Serialisierung von UDTs anzeigt, explizit zu konvertieren jede UDT-Spalte in der **Xml** -Datentyp in der SELECT-Anweisung. Sie können die Spalten, die auch explizit konvertieren **Varbinary**, **Varchar**, oder **Nvarchar**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines benutzerdefinierten Typs](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
