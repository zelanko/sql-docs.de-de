---
title: ADO-Verlauf | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2019
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
ms.openlocfilehash: a84ccbb97c26ea92f31212933aac79bde2784b72
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67927166"
---
# <a name="ado-features-for-each-release"></a>ADO-Features für die einzelnen Releases

In diesem Thema werden die neuen Features aufgelistet, die von den einzelnen Versionen von ADO, ADO MD und ADOX eingeführt werden.

## <a name="ado-60"></a>ADO 6,0

 ADO 6,0 ist in Windows Vista als Teil der Windows Data Access Components (Windows DAC) 6,0 enthalten. ADO 6,0 ist funktional äquivalent zu ADO 2,8.

## <a name="ado-28"></a>ADO 2,8

 ADO 2,8 ist in Windows XP und Windows Server 2003 als Teil der Microsoft Data Access Components (MDAC) 2,8 enthalten. Außerdem ist eine verteilbare Version von MDAC 2,8 verfügbar. Beachten Sie, dass diese verteilbare Version nur unter Windows 2000 installiert werden sollte. ADO 2,8 behandelt verschiedene sicherheitsrelevante Aspekte:

 *Der Festplattenzugriff ist außerhalb einer vertrauenswürdigen Zone nicht zulässig.*
In Domänen übergreifenden Skripts, die nicht vertrauenswürdige Sites betreffen, sind die folgenden Vorgänge deaktiviert: **Stream. SaveToFile**, **Stream. LoadFromFile**, **Recordset. Save**und **Recordset. Open**, die in Verbindung mit dem **adcmdfile** -Flag oder mit dem Microsoft OLE DB Dauerhaftigkeits Anbieter (MSPersist) verwendet werden.

 " **Recordset. Open** " _,_"**Recordset. Save** " _,_"**Stream. SaveToFile** " _und_"**Stream. LoadFromFile**" werden_nur auf physische Dateien angewendet._        
Diese Methoden überprüfen jetzt, ob Datei Handles nur auf physische Dateien zeigen.

 **Recordset. ActiveCommand**  _gibt einen Fehler zurück, wenn er von einer HTML/ASP-Seite aufgerufen wird._
Dadurch wird verhindert, dass das **Befehls** Objekt missbraucht wird.

 _Die Anzahl der_**Recordsets**, die von einem Befehl für eine**Form der Form "Form**"_zurückgegeben werden_,_weist eine_        
Ein Befehl für eine Form der Form "Form" gibt jetzt maximal 512 **Recordsets**zurück. Dies bedeutet, dass ein **Shape** -Befehl nicht mehr in beliebiger Tiefe schachtelt werden kann. Stattdessen ist die maximale **Ebenentiefe**512, wenn jeder Befehl ein einzelnes (untergeordnetes) Recordset ergibt. Wenn ein **Shape** -Befehl auf jeder Ebene mehrere **Recordsets**zurückgibt, ist die maximale Tiefe geringer als 512.

## <a name="ado-27"></a>ADO 2,7

 *64-Bit-Platt Form Unterstützung* ADO 2,7 bietet Unterstützung für 64-Bit-Prozessoren.

## <a name="ado-26"></a>ADO 2,6

 Die **cubdef. getschemaobject**-_Methode_ beginnend mit ADO 2,6, ADO MD Objekte können mit eindeutigen Namen abgerufen werden, wie in der [UniqueName-Eigenschaft (ADO MD)](../../ado/reference/ado-md-api/uniquename-property-ado-md.md)angegeben.   Die Namen der übergeordneten Objekte müssen nicht bekannt sein, und übergeordnete Auflistungen müssen nicht aufgefüllt werden, um ein Schema Objekt abzurufen. Weitere Informationen finden Sie unter [getschemaobject-Methode (ADO MD)](../../ado/reference/ado-md-api/getschemaobject-method-ado-md.md).

 *Befehlsdaten Ströme* Das **Command** -Objekt unterstützt Befehle im Streamformat als Alternative zur Verwendung der **CommandText** -Eigenschaft. Die [CommandStream-Eigenschaft (ADO)](../../ado/reference/ado-api/commandstream-property-ado.md) kann verwendet werden, um XML-Vorlagen oder Update grams als **Befehls** Eingabe mit dem Microsoft OLE DB-Anbieter für SQL Server anzugeben.

 Der **Dialekt-**_Eigenschafts_ [Dialekt](../../ado/reference/ado-api/dialect-property.md) ist eine neue Eigenschaft, die die Syntax und die allgemeinen Regeln definiert, die der Anbieter zum Analysieren der Zeichenfolge oder des Streams verwendet.  

 **Command. Execute**-_Methode_ die [Execute-Methode](../../ado/reference/ado-api/execute-method-ado-command.md) des ADO- **Befehls** Objekts wurde erweitert, um Streams für die Eingabe und die Ausgabe zu verwenden.  

 *Feld Statuswerte* Wenn der Benutzer beim Ändern eines **Felds** eines **Recordsets**auf einen DB_E_ERRORSOCCURRED Fehler stößt, wird die Eigenschaft **field. Status** von ADO nun mit den entsprechenden Status Informationen aufgefüllt, sodass der Benutzer weitere Informationen zu den Fehlern hat. Siehe [Status-Eigenschaft (ADO-Feld)](../../ado/reference/ado-api/status-property-ado-field.md).

 **NamedParameters**-_Eigenschaft_ [namedParameters](../../ado/reference/ado-api/namedparameters-property-ado.md) ist eine neue Eigenschaft des **Command** -Objekts, das angibt, dass der Anbieter benannte Parameter verwenden soll.  

 *Resultsets in Streams* ADO kann Resultsets aus einer Datenquelle in einem **Stream**anstelle eines **Recordset** -Objekts zurückgeben. Mithilfe der neuesten Version des Microsoft OLE DB-Anbieters für SQL Server können Sie XML-Ergebnisse vom Anbieter erhalten, indem Sie eine for XML-Abfrage ausführen. Ein Daten **Strom** , der das Resultset empfängt, kann mit einem for XML-Befehl als Quelle geöffnet werden. Weitere Informationen finden Sie unter [Abrufen von Resultsets in Streams](../../ado/guide/data/retrieving-resultsets-into-streams.md).

 *Resultset mit einer Zeile* Das ADO- **Datensatz** -Objekt kann nun in einer Befehls Zeichenfolge oder einem **Befehls** Objekt geöffnet werden, das eine Daten Zeile vom Anbieter zurückgibt. Dies führt zu einer verbesserten Leistung bei MDAC 2,6-Anbietern. Siehe [Open-Methode (ADO-Datensatz)](../../ado/reference/ado-api/open-method-ado-record.md).

## <a name="ado-25"></a>ADO 2,5

 Das **Daten Satz** _Objekt_ ADO 2,5 führt das **Daten Satz** Objekt ein, um eine Zeile aus einem **Recordset** oder einem Datenanbieter darzustellen und zu verwalten, oder ein Objekt, das eine teilweise strukturierte Daten kapselt, z. b. eine Datei oder ein Verzeichnis.

 Das Stream **-Objekt ADO** __ 2,5 führt außerdem das **Stream** -Objekt ein, um einen Stream von Binär-oder Textdaten darzustellen.

 *URL-Bindung* ADO 2,5 führt die Verwendung einer URL als Alternative zu einer Verbindungs Zeichenfolge und einem Befehls Text ein, um Datenspeicher Objekte zu benennen. Eine URL kann mit den vorhandenen **Verbindungs** -und **Recordset** -Objekten sowie mit den neuen **Datensatz** -und **Stream** -Objekten verwendet werden.

 *Unterstützende URL-Bindung für Datenanbieter* ADO 2,5 unterstützt OLE DB Anbietern, die die URL-Schemas erkennen. Dies schließt OLE DB Anbieter für die Internet Veröffentlichung ein, der auf das Windows 2000-Dateisystem zugreift und das vorhandene http-Schema erkennt.
