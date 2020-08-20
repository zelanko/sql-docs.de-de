---
description: Absolute und relative URLs
title: Absolute und relative URLs | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 43fc1a32428f54682b8fde5dea0f0140568c482e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453912"
---
# <a name="absolute-and-relative-urls"></a>Absolute und relative URLs
Eine URL gibt den Speicherort eines Ziels an, das auf einem lokalen Computer oder einem vernetzten Computer gespeichert ist. Bei dem Ziel kann es sich um eine Datei, ein Verzeichnis, eine HTML-Seite, ein Bild, ein Programm usw. handeln.  
  
 Eine *absolute URL* die alle Informationen enthält, die erforderlich sind, um eine Ressource zu suchen.  
  
 Eine *relative URL* die eine Ressource mit einem absolute URL als Ausgangspunkt verwendet. Tatsächlich wird die "Complete URL" des Ziels durch Verkettung der absoluten und relativen URLs angegeben.  
  
 Ein *absolute URL* verwendet das folgende Format: *Scheme://Server/Path/Resource*  
  
 Ein relative URL besteht in der Regel nur aus dem *Pfad*und optional der *Ressource*, aber keinem *Schema* oder *Server*. In den folgenden Tabellen werden die einzelnen Teile des gesamten URL-Formats definiert.  
  
 *Schema*  
 Gibt an, wie auf die *Ressource* zugegriffen werden soll.  
  
 *server*  
 Gibt den Namen des Computers an, auf dem sich die *Ressource* befindet.  
  
 *path*  
 Gibt die Sequenz von Verzeichnissen an, die zum Ziel führen. Wenn *Resource* weggelassen wird, ist das Ziel das letzte Verzeichnis im *Pfad*.  
  
 *resource*  
 Wenn dieses enthalten ist, ist die *Ressource* das Ziel und in der Regel der Name einer Datei. Dabei kann es sich um eine *einfache Datei handeln,* die einen einzelnen binären Stream von Bytes enthält, oder um ein *strukturiertes Dokument,* das mindestens ein Speicher und binäre Streams von Bytes enthält.  
  
## <a name="url-scheme-registration"></a>URL-Schema Registrierung  
 Wenn ein Anbieter URLs unterstützt, registriert der Anbieter mindestens ein URL-Schema. Die Registrierung bedeutet, dass alle URLs, die das Schema verwenden, automatisch den registrierten Anbieter aufrufen. Beispielsweise wird das *http* -Schema beim [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)registriert. ADO geht davon aus, dass alle URLs mit dem Präfix "http" Webordner oder Dateien darstellen, die mit dem Internet Publishing Provider verwendet werden sollen. Informationen zu den Schemas, die von Ihrem Anbieter registriert werden, finden Sie in der Dokumentation Ihres Anbieters.  
  
## <a name="defining-context-with-a-url"></a>Definieren von Kontext mit einer URL  
 Eine Funktion einer geöffneten Verbindung, die durch ein [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt dargestellt wird, besteht darin, nachfolgende Vorgänge auf die Datenquelle zu beschränken, die durch diese Verbindung repräsentiert wird. Das heißt, die Verbindung definiert den Kontext für nachfolgende Vorgänge.  
  
 Mit ADO 2,7 oder höher kann ein absolute URL auch einen Kontext definieren. Wenn z. b. ein [Daten Satz](../../../ado/reference/ado-api/record-object-ado.md) Objekt mit einem absolute URL geöffnet wird, wird implizit ein **Verbindungs** Objekt erstellt, das die durch die URL angegebene Ressource darstellt.  
  
 Eine absolute URL, die einen Kontext definiert, kann im *ActiveConnection* -Parameter der [Open](../../../ado/reference/ado-api/open-method-ado-record.md) -Methode des **Datensatz** -Objekts angegeben werden. Eine absolute URL kann auch als Wert des Schlüssel Worts "URL =" in der **Verbindungs** [Objekt-](../../../ado/reference/ado-api/open-method-ado-connection.md) Methode " *ConnectionString* " und des " [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Object [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) method *ActiveConnection* "-Parameters angegeben werden.  
  
 Der Kontext kann auch definiert werden, indem ein **Datensatz** -oder **Recordset** -Objekt geöffnet wird, das ein Verzeichnis darstellt, da diese Objekte bereits über ein implizit oder explizit deklariertes **Verbindungs** Objekt verfügen, das den Kontext angibt.  
  
## <a name="scoped-operations"></a>Bereichs bezogene Vorgänge  
 Der Kontext definiert auch den Bereich, d. h. das Verzeichnis und seine Unterverzeichnisse, die an nachfolgenden Vorgängen teilnehmen können. Das **Datensatz** -Objekt verfügt über mehrere Bereichs bezogene Methoden, die für ein Verzeichnis und alle Unterverzeichnisse ausgeführt werden. Zu diesen Methoden gehören [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), " [muverecord](../../../ado/reference/ado-api/moverecord-method-ado.md)" und " [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)".  
  
## <a name="relative-urls-as-command-text"></a>Relative URLs als Befehls Text  
 Sie können einen Befehl angeben, der für die Datenquelle ausgeführt werden soll, indem Sie eine Zeichenfolge in den *CommandText* -Parameter der [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) -Methode des **Verbindungs** Objekts eingeben und im *Source* -Parameter der [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode des **Recordset** -Objekts.  
  
 Eine relative URL kann im *CommandText* -Parameter oder im *Source* -Parameter angegeben werden. Der relative URL stellt keinen Befehl dar, wie z. b. einen SQL-Befehl. Sie gibt lediglich die Parameter an. Der Kontext der aktiven Verbindung muss ein absolute URL sein, und der *Option* -Parameter muss auf **adCmdTableDirect**festgelegt sein.  
  
 Im folgenden Codebeispiel wird z. b. gezeigt, wie ein **Recordset** für die Readme25.txt-Datei im Verzeichnis winnt/system32 geöffnet wird:  
  
```  
recordset.Open "system32/Readme25.txt", "URL=https://YourServer/Winnt/",,,adCmdTableDirect  
```  
  
 Der absolute URL in der Verbindungs Zeichenfolge gibt den Server ( `YourServer` ) und den Pfad ( `Winnt` ) an. Diese URL definiert auch den Kontext.  
  
 Der relative URL im Befehls Text verwendet die absolute URL als Ausgangspunkt und gibt den Rest des Pfads ( `system32` ) und die zu öffnende Datei an ( `Readme25.txt` ).  
  
 Das Optionsfeld ( `adCmdTableDirect` ) gibt an, dass der Befehlstyp eine relative URL ist.  
  
 Ein weiteres Beispiel: der folgende Code öffnet ein **Recordset** für den Inhalt des `Winnt` Verzeichnisses:  
  
```  
recordset.Open "", "URL=https://YourServer/Winnt/",,,adCmdTableDirect  
```  
  
## <a name="ole-db-provider-supplied-url-schemes"></a>Vom Anbieter bereitgestellte URL-Schemas OLE DB  
 Der führende Teil einer voll qualifizierten URL ist das *Schema* , das für den Zugriff auf die Ressource verwendet wird, die durch den Rest der URL identifiziert wird. Beispiele hierfür sind http (Hypertext Transfer Protocol) und FTP (Dateiübertragungsprotokoll).  
  
 ADO unterstützt OLE DB Anbietern, die eigene URL-Schemas erkennen. Beispielsweise erkennt der [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)*,* der auf "veröffentlichte" Windows 2000-Dateien zugreift, das vorhandene http-Schema.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
