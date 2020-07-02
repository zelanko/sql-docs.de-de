---
title: Einführung in den SQLXMLOLEDB-Anbieter (SQLXML)
description: Erfahren Sie mehr über den SQLXMLOLEDB-Anbieter, einen OLE DB Anbieters, der SQLXML-Funktionen über ActiveX Data Objects (ADO) verfügbar macht.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, properties
- adExecuteStream flag
- SQLXMLOLEDB Provider, about SQLXMLOLEDB Provider
ms.assetid: 2e3f3817-4209-4bf4-9f46-248c95bc6f1b
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: aafc93dd9cf83a648cc4eecfe9301ad6e3ab24c6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85650080"
---
# <a name="introduction-to-the-sqlxmloledb-provider-sqlxml-40"></a>Einführung in den SQLXMLOLEDB-Anbieter (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Der SQLXMLOLEDB-Anbieter ist ein OLE DB-Anbieter, der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML-Funktionalität durch ADO (ActiveX Data Objects) verfügbar macht. Der Anbieter kann Befehle jedoch nur im ADO-Modus zum Schreiben in einen Ausgabedatenstrom ausführen. Der SQLXMLOLEDB-Anbieter ist kein Rowsetanbieter. Wenn Sie einen Befehl ausführen, müssen Sie das Flag adExecuteStream angeben, das ADO anweist, den von Ihnen angegebenen Ausgabestream zu verwenden.  
  
 Das folgende Beispiel zeigt die Syntax für den Execute-Befehl, in dem das adExecuteStream-Flag angegeben ist:  
  
```  
Dim oTestCommand As New ADODB.Command  
...  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Execute , , adExecuteStream  
...  
```  
  
## <a name="sqlxmloledb-provider-specific-properties"></a>Anbieterspezifische SQLXMLOLEDB-Eigenschaften  
 Der SQLXMLOLEDB-Anbieter stellt die folgenden anbieterspezifischen Verbindungseigenschaften zur Verfügung.  
  
|Verbindung<br /><br /> property|Standard<br /><br /> (ggf.)|BESCHREIBUNG|  
|-----------------------------|----------------------------|-----------------|  
|Datenanbieter||Stellt die PROGID des OLE DB-Anbieters zur Verfügung, durch die SQLXMLOLEDB die Befehle ausführt. Ab SQLXML 4.0 und [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ist dieser Anbieter in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client enthalten. Daher ist dieser Eigenschaftswert auf "SQLNCLI11" beschränkt. Weitere Informationen finden Sie unter [SQL Server Native Client-Programmierung](../../../relational-databases/native-client/sql-server-native-client-programming.md).|  
  
 Der SQLXMLOLEDB-Anbieter stellt die folgenden anbieterspezifischen Befehlseigenschaften zur Verfügung.  
  
|Befehl<br /><br /> property|Standard<br /><br /> (ggf.)|BESCHREIBUNG|  
|--------------------------|----------------------------|-----------------|  
|Basispfad|""|Gibt den Basispfad der Datei an. Der Basispfad der Datei gibt den Speicherort der XSL-Dateien (XML Stylesheet Language) oder der Zuordnungsschemadateien an. Der Basisdatei Pfad wird auch verwendet, um die relativen Pfade der XSL-Datei oder der Zuordnung von Schema Dateien aufzulösen, die in den XSL-oder Mapping-Schema Eigenschaften angegeben wurden.<br /><br /> Ein Beispiel für die Verwendung dieser Eigenschaft finden Sie unter [Ausführen von XPath-Abfragen &#40;SQLXMLOLEDB-Anbieter&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md).|  
|ClientSideXML|False|Legen Sie diese Eigenschaft auf True fest, wenn die Konvertierung des Rowsets in XLM statt auf dem Server auf dem Client erfolgen soll. Dies ist nützlich, wenn Sie die Ladeleistungslast auf die mittlere Ebene verschieben möchten.<br /><br /> Ein Beispiel für die Verwendung dieser Eigenschaft finden Sie unter [Ausführen von SQL-Abfragen &#40;SQLXMLOLEDB-Anbieter&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md) oder [Ausführen von Vorlagen, die SQL-Abfragen &#40;SQLXMLOLEDB-Anbieter&#41;enthalten ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md).|  
|Inhaltstyp||Gibt den Ausgabeinhaltstyp zurück. Dies ist eine schreibgeschützte Eigenschaft.<br /><br /> Diese Eigenschaft stellt dem Browser Informationen über den Inhaltstyp (z. B. TEXT/XML, TEXT/HTML, image/jpeg usw.) zur Verfügung. Der Wert dieser Eigenschaft wird zum Feld **Inhaltstyp** , das als Teil des HTTP-Headers an den Browser gesendet wird, der den MIME-Typ (Multipurpose Internet Mail Extensions) des Dokuments enthält, das als Text gesendet wird.|  
|Zuordnungsschema|NULL|Wenn eine Clientanwendung eine XPath-Abfrage für ein Zuordnungsschema (XDR oder XSD) ausführt, wird mit dieser Eigenschaft der Name des Zuordnungsschemas angegeben.<br /><br /> Der Pfad, der angegeben wird, kann relativ (xyz/abc/MySchema.xml) oder absolut (C:\MyFolder\abc\MySchema.xml) sein.<br /><br /> Wenn ein relativer Pfad angegeben ist, wird der durch die Basis Pfadeigenschaft angegebene Basispfad zum Auflösen des relativen Pfads verwendet. Wenn in der Basis Pfadeigenschaft kein Pfad angegeben wurde, ist der relative Pfad relativ zum aktuellen Verzeichnis.<br /><br /> Wenn Sie einen Wert für die Eigenschaft Mapping Schema angeben, können Sie einen lokalen Verzeichnispfad oder eine URL (https://...) angeben. Wenn Sie eine URL angeben, müssen Sie WinHTTP für den Zugriff auf http-und HTTPS-Server über einen Proxy Server konfigurieren. Führen Sie dazu das Hilfsprogramm Proxycfg.exe aus. Weitere Informationen finden Sie im Abschnitt über das Verwenden des WinHTTP-Proxy-Konfigurationshilfsprogramms in der MSDN Library.<br /><br /> Ein Beispiel für die Verwendung dieser Eigenschaft finden Sie unter [Ausführen von XPath-Abfragen &#40;SQLXMLOLEDB-Anbieter&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md).|  
|Namespaces||Diese Eigenschaft ermöglicht die Ausführung von XPath-Abfragen, die Namespaces verwenden. Ein Beispiel für die Verwendung dieser Eigenschaft finden Sie unter [Ausführen von XPath-Abfragen mit Namespaces &#40;SQLXMLOLEDB-Anbieter&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md).|  
|ss Stream Flags||Diese Eigenschaft wird verwendet, um bestimmte Arten von Sicherheitseinschränkungen anzugeben. Beispielsweise sollen keine URL-Verweise auf Dateien oder absolute Pfade für Dateien (wie externe Websites) zugelassen werden. Oder es sollen keine Abfragen in den Vorlagen zulässig sein.<br /><br /> Der Eigenschaft können folgende Werte zugewiesen werden:<br /><br /> 1 = STREAM_FLAGS_DISALLOW_URL 2 = STREAM_FLAGS_DISALLOW_ABSOLUTE_PATH 4 = STREAM_FLAGS_DISALLOW_QUERY 8 = STREAM_FLAGS_       DONTCACHEMAPPINGSCHEMA 16 = STREAM_FLAGS_DONTCACHETEMPLATE 32 = STREAM_FLAGS_DONTCACHEXSL<br /><br /> Weitere Informationen über diese Werte sind in der nächsten Tabelle enthalten.|  
|XML-Stamm||Diese Eigenschaft wird verwendet, um ein Stammtag für das resultierende XML zu definieren. Wenn Sie beispielsweise SQL-Abfragen für die Datenbank ausführen und das resultierende XML-Dokument kein einzelnes Stammelement hat, wird der Wert der Eigenschaft dazu verwendet, dem Dokument ein einzelnes Stammelement hinzuzufügen.<br /><br /> Ein Beispiel für die Verwendung dieser Eigenschaft finden Sie unter [Ausführen von SQL-Abfragen &#40;SQLXMLOLEDB-Anbieter&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md).|  
|XSL||Mit dieser Eigenschaft wird der XSL-Dateiname angegeben, wenn die XSL-Transformation auf das von der Abfrage zurückgegebene XML-Dokument angewendet werden soll.<br /><br /> Der Pfad, der angegeben wird, kann relativ (xyz/abc/MyXSL.xsl) oder absolut (C:\MyFolder\abc\MyXSL.xsl) sein.<br /><br /> Wenn ein relativer Pfad angegeben ist, wird der durch die Basis Pfadeigenschaft angegebene Basispfad zum Auflösen des relativen Pfads verwendet. Wenn in der Basis Pfadeigenschaft kein Pfad angegeben wurde, ist der relative Pfad relativ zum aktuellen Verzeichnis.<br /><br /> Ein Beispiel für die Verwendung dieser Eigenschaft finden Sie unter Anwenden einer XSL-Transformation (SQLXMLOLEDB-Anbieter).|  
  
 Die folgende Tabelle enthält Beschreibungen der Eigenschaftswerte der SS-Stream-Flags.  
  
|Eigenschaftswert|BESCHREIBUNG|  
|--------------------|-----------------|  
|STREAM_FLAGS_DISALLOW_URL|URLs werden nicht zum Zuordnen von Schemas oder XSL akzeptiert.|  
|STREAM_FLAGS_DISALLOW_ABSOLTE_PATH|Ein für das Zuordnungschema oder für XSL angegebener Pfad muss sich auf den Basispfad der Vorlage selbst beziehen.|  
|STREAM_FLAGS_DISALLOW_QUERY|Abfragen sind in einer Vorlage nicht zulässig.|  
|STREAM_FLAGS_DONTCACHEMAPPINGSCHEMA|Das Zuordnungsschema wird nicht zwischengespeichert. Dieser Eigenschaftswert ist während der Datenbankentwicklungsphase nützlich, wenn Datenbankschemas Änderungen unterliegen.|  
|STREAM_FLAGS_DONTCACHETEMPLATE|Vorlagen werden nicht zwischengespeichert.|  
|STREAM_FLAGS_DONTCACHEXSL|XSL wird nicht zwischengespeichert.|  
  
  
