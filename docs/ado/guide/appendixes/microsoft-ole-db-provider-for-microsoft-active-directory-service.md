---
title: Microsoft OLE DB-Anbieter für Microsoft Active Directory-Dienst | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADSI provider [ADO]
- Active Directory Service Interfaces provider [ADO]
- providers [ADO], OLE DB provider for Active Directory service
- OLE DB provider for Active Directory service [ADO]
ms.assetid: f9e81452-5675-4cfc-9949-cfbd2fe57534
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 25a076118df9f85ff2449c35dc0273db8a499fac
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52538161"
---
# <a name="microsoft-ole-db-provider-for-microsoft-active-directory-service"></a>Microsoft OLE DB-Anbieter für Microsoft Active Directory-Dienst
Die Active Directory Service Interfaces (ADSI)-Anbieter ermöglicht ADO zur Verbindung mit heterogenen Verzeichnisdiensten über ADSI. Dadurch erhält der ADO-Anwendungen nur-Lese Zugriff auf der Microsoft Windows NT 4.0 und Microsoft Windows 2000-Verzeichnisdienste, zusätzlich zu der alle LDAP-kompatiblen Verzeichnisdienst und Novell-Verzeichnisdienste. ADSI selbst basiert auf ein Anbietermodell, so dass bei ein neuen Anbieter haben Zugriff auf ein anderes Verzeichnis wird die ADO-Anwendung können sie problemlos darauf zugreifen kann. Der ADSI-Anbieter Freethread- und Unicode aktiviert ist.  
  
## <a name="connection-string-parameters"></a>Parameter für Verbindungszeichenfolgen  
 Legen Sie zum Verbinden mit diesem Anbieter die **Anbieter** Argument der ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft auf Folgendes:  
  
```vb
ADSDSOObject  
```  
  
 Lesen der [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft auch dieser Zeichenfolge zurück.  
  
## <a name="typical-connection-string"></a>Typische Verbindungszeichenfolge  
 Eine typische Verbindungszeichenfolge für diesen Anbieter lautet wie folgt aus:  
  
```vb
"Provider=ADSDSOObject;User ID=MyUserID;Password=MyPassword;"  
```  
  
 Die Zeichenfolge besteht aus der folgenden Schlüsselwörter.  
  
|Schlüsselwort|Description|  
|-------------|-----------------|  
|**Anbieter**|Gibt die OLE DB-Anbieter für Active Directory-Dienst an.|  
|**Benutzer-ID**|Gibt den Benutzernamen an. Wenn dieses Schlüsselwort ausgelassen wird, wird die aktuelle Anmeldung verwendet.|  
|**Kennwort**|Gibt das Kennwort des Benutzers an. Wenn dieses Schlüsselwort ausgelassen wird. Anschließend wird die aktuelle Anmeldung verwendet.|  
  
> [!NOTE]
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben **Trusted_Connection = Yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort die Informationen in der Verbindungszeichenfolge.  
  
## <a name="command-text"></a>Befehlstext  
 Eine Zeichenfolge aus vier Teilen bestehenden Befehl wird vom Anbieter in der folgenden Syntax erkannt:  
  
```vb
"Root; Filter; Attributes[; Scope]"  
```  
  
|Wert|Description|  
|-----------|-----------------|  
|*Root*|Gibt an, die **ADsPath** Objekt aus, das zum Starten des Suchvorgangs (d. h. der Stamm der Suche).|  
|*Filter*|Gibt den Suchfilter im Format RFC 1960 an.|  
|*Attribute*|Gibt eine durch Trennzeichen getrennte Liste von Attributen, die zurückgegeben werden soll.|  
|*Bereich*|Dies ist optional. Ein **Zeichenfolge** den Bereich der Suche angibt. Kann einen der folgenden Werte annehmen:<br /><br /> -Base - Suche nur das Basisobjekt (Stamm der Suche).<br />-OneLevel - Suche nur eine Ebene.<br />-Unterstruktur – suchen Sie die gesamte Teilstruktur.|  
  
 Zum Beispiel:  
  
```vb
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree"  
```  
  
 Der Anbieter unterstützt auch SQL-SELECT für Befehlstext. Zum Beispiel:  
  
```vb
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE   
objectClass='user' AND objectCategory='Person'"  
```  
  
## <a name="remarks"></a>Hinweise  
 Der Anbieter akzeptiert keine Aufrufe von gespeicherten Prozeduren oder einfache Tabellennamen (z. B. die [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) Eigenschaft werden immer **AdCmdText**). Finden Sie in den Active Directory Service Interfaces-Dokumentation für eine ausführlichere Beschreibung von Textelementen Befehl.  
  
## <a name="recordset-behavior"></a>Recordset-Verhalten  
 Die folgenden Tabellen enthalten die Features auf einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt mit diesem Anbieter geöffnet. Nur der statische Cursor-Datentyp (**"adOpenStatic"**) verfügbar ist.  
  
 Weitere Informationen zu **Recordset** Verhalten für die Anbieterkonfiguration, und führen Sie die [unterstützt](../../../ado/reference/ado-api/supports-method.md) Methode eine Aufzählung der [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung von der  **Recordset** zu bestimmen, ob die anbieterspezifische dynamische Eigenschaften vorhanden sind.  
  
 **Verfügbarkeit der standard-ADO-Recordset-Eigenschaften:**  
  
|Eigenschaft|Verfügbarkeit|  
|--------------|------------------|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|Lese-/Schreibzugriff|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|Lese-/Schreibzugriff|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|Schreibgeschützt|  
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Schreibgeschützt|  
|[Lesezeichen](../../../ado/reference/ado-api/bookmark-property-ado.md)|Lese-/Schreibzugriff|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|Lese-/Schreibzugriff|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|immer **AdUseServer**|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|immer **"adOpenStatic"**|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|immer **AdEditNone**|  
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Schreibgeschützt|  
|[Filter](../../../ado/reference/ado-api/filter-property.md)|Lese-/Schreibzugriff|  
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Lese-/Schreibzugriff|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|Nicht verfügbar.|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|Lese-/Schreibzugriff|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|Schreibgeschützt|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|Lese-/Schreibzugriff|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|Schreibgeschützt|  
|[Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md)|Lese-/Schreibzugriff|  
|[Zustand](../../../ado/reference/ado-api/state-property-ado.md)|Schreibgeschützt|  
|[Status](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Schreibgeschützt|  
  
 **Verfügbarkeit des standard-ADO-Recordset-Methoden:**  
  
|Methode|Verfügbar?|  
|------------|----------------|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Nein|  
|[Abbrechen](../../../ado/reference/ado-api/cancel-method-ado.md)|Nein|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Nein|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Nein|  
|[Klonen](../../../ado/reference/ado-api/clone-method-ado.md)|Ja|  
|[Schließen](../../../ado/reference/ado-api/close-method-ado.md)|Ja|  
|[Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Nein|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Ja|  
|[Verschieben](../../../ado/reference/ado-api/move-method-ado.md)|Ja|  
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Ja|  
|[Datei](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Ja|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Ja|  
|[Erneute Synchronisierung](../../../ado/reference/ado-api/resync-method.md)|Ja|  
|[Unterstützt](../../../ado/reference/ado-api/supports-method.md)|Ja|  
|[Update](../../../ado/reference/ado-api/update-method.md)|Nein|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Nein|  
  
 Weitere Informationen zu ADSI sowie die Einzelheiten des Anbieters finden Sie in der Dokumentation der Active Directory Service Interfaces oder besuchen Sie die ADSI-Webseite.  
  
## <a name="see-also"></a>Siehe auch  
 [CommandType-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [ConnectionString-Eigenschaft (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Provider-Eigenschaft (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Supports-Methode](../../../ado/reference/ado-api/supports-method.md)
