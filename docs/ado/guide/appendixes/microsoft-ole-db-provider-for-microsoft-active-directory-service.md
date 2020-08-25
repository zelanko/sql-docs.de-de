---
description: Microsoft OLE DB-Anbieter für Microsoft Active Directory Service
title: Microsoft OLE DB-Anbieter für Microsoft Active Directory Service | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: c196b790299c4c241e5c8eda762b43115b71a038
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806576"
---
# <a name="microsoft-ole-db-provider-for-microsoft-active-directory-service"></a>Microsoft OLE DB-Anbieter für Microsoft Active Directory Service
Der ADSI-Anbieter (Active Directory Service Interfaces) ermöglicht ADO das Herstellen einer Verbindung mit heterogenen Verzeichnisdiensten über ADSI. Dies ermöglicht ADO-Anwendungen einen schreibgeschützten Zugriff auf die Verzeichnisdienste Microsoft Windows NT 4,0 und Microsoft Windows 2000, zusätzlich zu allen LDAP-kompatiblen Verzeichnisdienst-und Novell-Verzeichnisdiensten. ADSI selbst basiert auf einem Anbieter Modell. wenn es also einen neuen Anbieter gibt, der Zugriff auf ein anderes Verzeichnis bietet, kann die ADO-Anwendung nahtlos darauf zugreifen. Der ADSI-Anbieter ist frei Thread-und Unicode-fähig.  
  
## <a name="connection-string-parameters"></a>Parameter der Verbindungszeichenfolge  
 Legen Sie das **Provider** -Argument der [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) -Eigenschaft auf Folgendes fest, um eine Verbindung mit diesem Anbieter herzustellen:  
  
```vb
ADSDSOObject  
```  
  
 Wenn Sie die [Provider](../../reference/ado-api/provider-property-ado.md) -Eigenschaft lesen, wird auch diese Zeichenfolge zurückgegeben.  
  
## <a name="typical-connection-string"></a>Typische Verbindungs Zeichenfolge  
 Eine typische Verbindungs Zeichenfolge für diesen Anbieter lautet wie folgt:  
  
```vb
"Provider=ADSDSOObject;User ID=MyUserID;Password=MyPassword;"  
```  
  
 Die Zeichenfolge besteht aus den folgenden Schlüsselwörtern.  
  
|Schlüsselwort|Beschreibung|  
|-------------|-----------------|  
|**Anbieter**|Gibt den OLE DB Anbieter für Active Directory Dienst an.|  
|**Benutzer-ID**|Gibt den Benutzernamen an. Wenn dieses Schlüsselwort weggelassen wird, wird die aktuelle Anmeldung verwendet.|  
|**Kennwort**|Gibt das Benutzer Kennwort an. , Wenn dieses Schlüsselwort ausgelassen wird. Anschließend wird die aktuelle Anmeldung verwendet.|  
  
> [!NOTE]
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unterstützt, sollten Sie in der Verbindungs Zeichenfolge **Trusted_Connection = yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort angeben.  
  
## <a name="command-text"></a>Befehlstext  
 Eine vierteilige Befehls Text Zeichenfolge wird vom Anbieter in der folgenden Syntax erkannt:  
  
```vb
"Root; Filter; Attributes[; Scope]"  
```  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|*Fasst*|Gibt das **ADsPath** -Objekt an, aus dem die Suche gestartet werden soll (d. h. der Stamm der Suche).|  
|*Filter*|Gibt den Suchfilter im RFC 1960-Format an.|  
|*Attribute*|Gibt eine durch Trennzeichen getrennte Liste von Attributen an, die zurückgegeben werden sollen.|  
|*Bereich*|Optional. Eine **Zeichenfolge** , die den Suchbereich angibt. Dabei kann es sich um eine der folgenden Methoden handeln:<br /><br /> -Base: sucht nur nach dem Basisobjekt (Stamm der Suche).<br />-Onelevel-nur eine Ebene suchen.<br />-Subtree: Durchsuchen Sie die gesamte Unterstruktur.|  
  
 Beispiel:  
  
```vb
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree"  
```  
  
 Der Anbieter unterstützt auch SQL SELECT für den Befehls Text. Beispiel:  
  
```vb
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE   
objectClass='user' AND objectCategory='Person'"  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Der Anbieter akzeptiert keine Aufrufe gespeicherter Prozeduren oder einfache Tabellennamen (die [CommandType](../../reference/ado-api/commandtype-property-ado.md) -Eigenschaft ist z. b. immer **adCmdText**). Eine ausführlichere Beschreibung der Befehls Textelemente finden Sie in der Dokumentation zu den Active Directory-Dienst Schnittstellen.  
  
## <a name="recordset-behavior"></a>Recordsetverhalten  
 In der folgenden Tabelle sind die verfügbaren Funktionen für ein [Recordset](../../reference/ado-api/recordset-object-ado.md) -Objekt aufgeführt, das mit diesem Anbieter geöffnet wurde. Nur der statische Cursortyp (**adopdestatic**) ist verfügbar.  
  
 Weitere Informationen zum **recordsetverhalten** ihrer Anbieter Konfiguration erhalten Sie, wenn Sie die [unterstützte](../../reference/ado-api/supports-method.md) Methode ausführen und die [Properties](../../reference/ado-api/properties-collection-ado.md) -Auflistung des **Recordsets** auflisten, um zu bestimmen, ob anbieterspezifische dynamische Eigenschaften vorhanden sind.  
  
 **Verfügbarkeit von Eigenschaften des Standard-ADO-Recordsets:**  
  
|Eigenschaft|Verfügbarkeit|  
|--------------|------------------|  
|[AbsolutePage](../../reference/ado-api/absolutepage-property-ado.md)|Lesen/Schreiben|  
|[AbsolutePosition](../../reference/ado-api/absoluteposition-property-ado.md)|Lesen/Schreiben|  
|[ActiveConnection](../../reference/ado-api/activeconnection-property-ado.md)|schreibgeschützt|  
|[BOF](../../reference/ado-api/bof-eof-properties-ado.md)|schreibgeschützt|  
|[Lesezeichen](../../reference/ado-api/bookmark-property-ado.md)|Lesen/Schreiben|  
|[CacheSize](../../reference/ado-api/cachesize-property-ado.md)|Lesen/Schreiben|  
|[CursorLocation –](../../reference/ado-api/cursorlocation-property-ado.md)|immer **AD-eServer**|  
|[CursorType](../../reference/ado-api/cursortype-property-ado.md)|Always **adop-static**|  
|[EditMode](../../reference/ado-api/editmode-property.md)|immer **adEditNone**|  
|[EOF](../../reference/ado-api/bof-eof-properties-ado.md)|schreibgeschützt|  
|[Filter](../../reference/ado-api/filter-property.md)|Lesen/Schreiben|  
|[LockType](../../reference/ado-api/locktype-property-ado.md)|Lesen/Schreiben|  
|[MarshalOptions](../../reference/ado-api/marshaloptions-property-ado.md)|nicht verfügbar|  
|[MaxRecords](../../reference/ado-api/maxrecords-property-ado.md)|Lesen/Schreiben|  
|[PageCount](../../reference/ado-api/pagecount-property-ado.md)|schreibgeschützt|  
|[PageSize](../../reference/ado-api/pagesize-property-ado.md)|Lesen/Schreiben|  
|[RecordCount](../../reference/ado-api/recordcount-property-ado.md)|schreibgeschützt|  
|[Quelle](../../reference/ado-api/source-property-ado-recordset.md)|Lesen/Schreiben|  
|[State](../../reference/ado-api/state-property-ado.md)|schreibgeschützt|  
|[Status](../../reference/ado-api/status-property-ado-recordset.md)|schreibgeschützt|  
  
 **Verfügbarkeit der standardmäßigen ADO-recordsetmethoden:**  
  
|Methode|Verfügbar?|  
|------------|----------------|  
|[AddNew](../../reference/ado-api/addnew-method-ado.md)|Nein|  
|[Abbrechen](../../reference/ado-api/cancel-method-ado.md)|Nein|  
|[CancelBatch](../../reference/ado-api/cancelbatch-method-ado.md)|Nein|  
|[CancelUpdate](../../reference/ado-api/cancelupdate-method-ado.md)|Nein|  
|[Klonen](../../reference/ado-api/clone-method-ado.md)|Ja|  
|[Schließen](../../reference/ado-api/close-method-ado.md)|Ja|  
|[Löschen](../../reference/ado-api/delete-method-ado-recordset.md)|Nein|  
|[GetRows](../../reference/ado-api/getrows-method-ado.md)|Ja|  
|[Verschieben](../../reference/ado-api/move-method-ado.md)|Ja|  
|[MoveFirst](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[MoveLast](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[MoveNext](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[MovePrevious](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[NextRecordset](../../reference/ado-api/nextrecordset-method-ado.md)|Ja|  
|[Öffnen](../../reference/ado-api/open-method-ado-recordset.md)|Ja|  
|[Requery](../../reference/ado-api/requery-method.md)|Ja|  
|[Erneut synchronisieren](../../reference/ado-api/resync-method.md)|Ja|  
|[Unterstützt](../../reference/ado-api/supports-method.md)|Ja|  
|[Aktualisieren](../../reference/ado-api/update-method.md)|Nein|  
|[Update Batch](../../reference/ado-api/updatebatch-method.md)|Nein|  
  
 Weitere Informationen zu ADSI und den Besonderheiten des Anbieters finden Sie in der Dokumentation zu den Active Directory-Dienst Schnittstellen oder auf der ADSI-Webseite.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CommandType-Eigenschaft (ADO)](../../reference/ado-api/commandtype-property-ado.md)   
 [ConnectionString-Eigenschaft (ADO)](../../reference/ado-api/connectionstring-property-ado.md)   
 [Properties-Auflistung (ADO)](../../reference/ado-api/properties-collection-ado.md)   
 [Provider-Eigenschaft (ADO)](../../reference/ado-api/provider-property-ado.md)   
 [Recordset-Objekt (ADO)](../../reference/ado-api/recordset-object-ado.md)   
 [Supports-Methode](../../reference/ado-api/supports-method.md)