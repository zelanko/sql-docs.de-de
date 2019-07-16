---
title: Absolute und Relative URLs | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- relative URLs [ADO]
- absolute URLs [ADO]
- URLs [ADO]
ms.assetid: 6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f15c5890300687a2d587a58a586d00bf2c8d0fd8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67926364"
---
# <a name="absolute-and-relative-urls"></a>Absolute und relative URLs
Eine URL gibt den Speicherort eines Ziels, das auf einem Computer lokal oder im Netzwerk gespeichert. Das Ziel kann es sich um eine Datei, Verzeichnis, HTML-Seite, Image, Programm usw. sein.  
  
 Ein *absolute URL* enthält alle Informationen, die erforderlich sind, um eine Ressource zu suchen.  
  
 Ein *relativen URL* sucht eine Ressource mit der eine absolute URL als Ausgangspunkt. Aktiviert ist, die "vollständige URL" des Ziels, werden angegeben durch die Verkettung der absolute und relative URLs.  
  
 Ein *absolute URL* verwendet das folgende Format: *Scheme://server/path/resource*  
  
 Eine relative URL in der Regel besteht aus nur die *Pfad*, und optional die *Ressource*, aber kein *Schema* oder *Server*. In den folgenden Tabellen definieren die einzelnen Bestandteile von der vollständigen URL-Format.  
  
 *scheme*  
 Gibt an, wie die *Ressource* zugegriffen werden soll.  
  
 *server*  
 Gibt den Namen des Computers, in denen die *Ressource* befindet.  
  
 *path*  
 Gibt die Sequenz von Verzeichnissen, die an das Ziel führt. Wenn *Ressource* wird ausgelassen, ist das Ziel der letzten Verzeichnisses in *Pfad*.  
  
 *resource*  
 Wenn enthalten, *Ressource* ist das Ziel, und ist üblicherweise der Name einer Datei. Möglicherweise eine *einfache Datei,* mit einem einzelnen binären Stream von Bytes, oder ein *strukturierte Dokument* , die eine oder mehrere Speicher und binären Datenströmen von Bytes enthält.  
  
## <a name="url-scheme-registration"></a>URL-Schema-Registrierung  
 Wenn ein Anbieter auf URLs unterstützt, wird der Anbieter eine oder mehrere URL-Schemas registriert. Registrierung bedeutet, dass alle URLs, die mithilfe des Schemas der registrierte Anbieter automatisch aufgerufen werden. Z. B. die *http* Schema registriert ist, um die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). ADO wird davon ausgegangen, dass alle URLs, die mit dem Präfix "http" Web-Ordner oder Dateien mit dem Internet-Publishing-Anbieter darstellen. Informationen zu den Schemas, die von Ihrem Anbieter registriert wurden finden Sie unter der Dokumentation Ihres Anbieters.  
  
## <a name="defining-context-with-a-url"></a>Definieren von Kontext mit einer URL  
 Eine offene Verbindung, dargestellt durch die Funktion eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt werden zum Einschränken der nachfolgende Vorgänge mit der Datenquelle dargestellt, über diese Verbindung. Die Verbindung definiert, also den Kontext für nachfolgende Vorgänge.  
  
 Bei ADO 2.7 oder höher kann eine absolute URL auch einen Kontext definieren. Z. B., wenn eine [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt wird geöffnet, mit einer absoluten URL, eine **Verbindung** -Objekt implizit erstellt, um die durch die URL angegebene Ressource darstellen.  
  
 Eine absolute URL, die einen Kontext definiert kann angegeben werden, der *ActiveConnection* Parameter, der die **Datensatz** Objekt [öffnen](../../../ado/reference/ado-api/open-method-ado-record.md) Methode. Eine absolute URL kann auch angegeben werden, als Wert für die "URL ="-Schlüsselwort in der **Verbindung** Objekt [öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) Methode *"ConnectionString"* -Parameter und die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methode *ActiveConnection* Parameter.  
  
 Kontext kann auch definiert werden, indem Sie öffnen ein **Datensatz** oder **Recordset** -Objekt, ein Verzeichnis darstellt, da diese Objekte bereits über einen implizit oder explizit deklarierten verfügen **Verbindung**  -Objekt, das Kontext gibt.  
  
## <a name="scoped-operations"></a>Bereichsbezogene Vorgänge  
 Der Kontext definiert auch Bereich –, also das Verzeichnis und seinen Unterverzeichnissen ein, die in nachfolgenden Vorgängen teilnehmen kann. Die **Datensatz** Objekt verfügt über mehrere Bereichsbezogene Methoden, die in einem Verzeichnis ausgeführt werden und alle Unterverzeichnisse. Dazu gehören das [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md), und [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md).  
  
## <a name="relative-urls-as-command-text"></a>Relative URLs als Befehlstext  
 Können Sie angeben, einen Befehl für die Datenquelle ausgeführt werden, durch Eingabe einer Zeichenfolge in die *CommandText* Parameter der **Verbindung** des Objekts [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) -Methode, und in der  *Quelle* Parameter, der die **Recordset** des Objekts [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methode.  
  
 Eine relative URL kann angegeben werden, der *CommandText* oder *Quelle* Parameter. Die relative URL stellt einen Befehl, z. B. einen SQL-Befehl keine tatsächlich dar; Es gibt lediglich die Parameter. Der Kontext der aktiven Verbindung muss eine absolute URL sein und die *Option* -Parameter muss festgelegt werden, um **AdCmdTableDirect**.  
  
 Das folgende Codebeispiel zeigt z. B. zum Öffnen einer **Recordset** auf die Datei ///Readme25.txt von Winnt/system32-Verzeichnis:  
  
```  
recordset.Open "system32/Readme25.txt", "URL=https://YourServer/Winnt/",,,adCmdTableDirect  
```  
  
 Die absolute URL in der Verbindungszeichenfolge gibt den Server (`YourServer`) und den Pfad (`Winnt`). Diese URL definiert auch den Kontext.  
  
 Die relative URL im Befehlstext die absolute URL als Ausgangspunkt verwendet und gibt an, der Rest des Pfads (`system32`) und die Datei zu öffnen (`Readme25.txt`).  
  
 Das Feld "Options" (`adCmdTableDirect`) gibt an, dass der Typ eine relative URL.  
  
 Wenn Sie beispielsweise der folgende Code wird geöffnet eine **Recordset** auf dem Inhalt der `Winnt` Verzeichnis:  
  
```  
recordset.Open "", "URL=https://YourServer/Winnt/",,,adCmdTableDirect  
```  
  
## <a name="ole-db-provider-supplied-url-schemes"></a>OLE DB-Anbieter bereitgestellte URL-Schemas  
 Der erste Teil einer vollqualifizierten URL ist die *Schema* , die Zugriff auf die Ressource identifiziert, nach dem Rest der URL verwendet wird. Beispiele sind HTTP (Hypertext Transfer Protocol) und FTP (File Transfer Protocol).  
  
 ADO unterstützt OLE DB-Anbieter, die ihre eigenen URL-Schemas zu erkennen. Z. B. die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md) *,* die "veröffentlicht" Windows 2000-Dateien, greift auf das vorhandene HTTP-Schema erkannt.  
  
## <a name="see-also"></a>Siehe auch  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
