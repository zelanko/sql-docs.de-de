---
title: Open-Methode (ADO-Verbindung) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::raw_Open
- Connection15::Open
- _Connection::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 663defab-5545-4973-9036-24d5882c9737
author: rothja
ms.author: jroth
ms.openlocfilehash: 31ce05ce069e0eb3e7d6431b296f40824a8acd3a
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762201"
---
# <a name="open-method-ado-connection"></a>Open-Methode (ADO-Verbindung)
Öffnet eine Verbindung mit einer Datenquelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
connection.Open ConnectionString, UserID, Password, Options  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Dies ist optional. Ein **Zeichen** folgen Wert, der Verbindungsinformationen enthält. Ausführliche Informationen zu gültigen Einstellungen finden Sie in der [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft.  
  
 *UserID*  
 Dies ist optional. Ein **Zeichen** folgen Wert, der einen Benutzernamen enthält, der beim Herstellen der Verbindung verwendet werden soll.  
  
 *Kennwort*  
 Dies ist optional. Ein **Zeichen** folgen Wert, der ein Kennwort enthält, das beim Herstellen der Verbindung verwendet werden soll.  
  
 *Optionen*  
 Dies ist optional. Ein [ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md) -Wert, der bestimmt, ob diese Methode zurückgeben soll (synchron) oder bevor (asynchron) die Verbindung hergestellt wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Verwendung der **Open** -Methode für ein [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt stellt die physische Verbindung zu einer Datenquelle her. Nachdem diese Methode erfolgreich abgeschlossen wurde, wird die Verbindung Live hergestellt, und Sie können Befehle für diese Methode ausgeben und die Ergebnisse verarbeiten.  
  
 Verwenden Sie das optionale *ConnectionString* -Argument, um entweder eine Verbindungs Zeichenfolge mit einer Reihe von *Argument* *= value* -Anweisungen, die durch Semikolons getrennt sind, oder eine Datei-oder Verzeichnis Ressource anzugeben, die mit einer URL identifiziert wird Die **ConnectionString** -Eigenschaft erbt automatisch den Wert, der für das *ConnectionString* -Argument verwendet wird. Daher können Sie entweder die **ConnectionString** -Eigenschaft des **Verbindungs** Objekts vor dem Öffnen festlegen oder das *ConnectionString* -Argument verwenden, um die aktuellen Verbindungsparameter **während des Aufrufes Aufrufes** aufzurufen oder zu überschreiben.  
  
 Wenn Sie Benutzer-und Kenn Wort Informationen sowohl im *ConnectionString* -Argument als auch in den optionalen *UserID* -und *Password* -Argumenten übergeben, überschreiben die Argumente " *UserID* " und *"Password"* die Werte, die in *ConnectionString*angegeben werden.  
  
 Wenn Sie Ihre Vorgänge über eine geöffnete **Verbindung**abgeschlossen haben, verwenden Sie die [Close](../../../ado/reference/ado-api/close-method-ado.md) -Methode, um alle zugeordneten Systemressourcen freizugeben. Durch das Schließen eines Objekts wird es nicht aus dem Arbeitsspeicher entfernt. Sie können die Eigenschafts Einstellungen ändern und die **Open** -Methode verwenden, um Sie zu einem späteren Zeitpunkt erneut zu öffnen. Wenn Sie ein Objekt vollständig aus dem Arbeitsspeicher entfernen möchten, legen Sie die Objekt Variable auf *Nothing*fest.  
  
> [!NOTE]
>  **Verwendung von Remote Datendiensten** Wenn die **Open** -Methode für ein Client seitiges **Verbindungs** Objekt verwendet wird, stellt Sie keine Verbindung mit dem Server her, bis ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) für das **Verbindungs** Objekt geöffnet ist.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Open-und Close-Methoden Beispiel (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Open-und Close-Methoden Beispiel (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Open-und Close-Methoden Beispiel (VC + +)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open-Methode (ADO-Datensatz)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open-Methode (ADO-Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open-Methode (ADO-Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema-Methode](../../../ado/reference/ado-api/openschema-method.md)
