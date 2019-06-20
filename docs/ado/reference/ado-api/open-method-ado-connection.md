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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 01d18e643dd769daa22309bb6c3df6407ab9043f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66719170"
---
# <a name="open-method-ado-connection"></a>Open-Methode (ADO-Verbindung)
Öffnet eine Verbindung mit einer Datenquelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
connection.Open ConnectionString, UserID, Password, Options  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Optional. Ein **Zeichenfolge** -Wert, der Verbindungsinformationen enthält. Finden Sie unter den ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft für Informationen zu gültigen Einstellungen.  
  
 *UserID*  
 Optional. Ein **Zeichenfolge** Wert, der einen Benutzernamen ein, verwenden Sie beim Herstellen der Verbindung enthält.  
  
 *Kennwort*  
 Optional. Ein **Zeichenfolge** -Wert, ein Kennwort beim Herstellen der Verbindung enthält.  
  
 *Options*  
 Optional. Ein [ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md) Wert, der bestimmt, ob diese Methode nach dem zurückgeben soll (synchron) oder vor (asynchron) die Verbindung hergestellt wird.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe der **öffnen** Methode für eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt stellt die physische Verbindung mit einer Datenquelle her. Nach dem erfolgreichen dieser Methode Abschluss ist die Verbindung, und Sie können Befehle für diese und die Ergebnisse zu verarbeiten.  
  
 Verwenden Sie das optionale *"ConnectionString"* Argument entweder eine Verbindungszeichenfolge mit einer Reihe von *Argument* *= Value* durch Semikolons getrennte Anweisungen oder ein Datei oder ein Verzeichnis mit einer URL bezeichnete Ressource. Die **"ConnectionString"** -Eigenschaft erbt automatisch den Wert für die *"ConnectionString"* Argument. Aus diesem Grund können Sie entweder die **"ConnectionString"** Eigenschaft der **Verbindung** Objekt vor dem Öffnen, oder verwenden Sie die *"ConnectionString"* Argument festzulegen oder zu überschreiben die aktuellen Parameter während der **öffnen** Methodenaufruf.  
  
 Wenn Sie den Benutzernamen und Kennwort des Informationen sowohl in übergeben die *"ConnectionString"* Argument und den optionalen *"UserID"* und *Kennwort* Argumente, die *"UserID"*  und *Kennwort* Argumente überschreiben die Werte im angegebenen *"ConnectionString"* .  
  
 Wenn Sie Ihre Vorgänge über ein offenes geschlossen haben **Verbindung**, verwenden Sie die [schließen](../../../ado/reference/ado-api/close-method-ado.md) Methode, um eine kostenlose zugeordnete Systemressourcen. Schließen ein Objekt entfernt es nicht aus dem Arbeitsspeicher. Sie können die Einstellungen zu ändern und die **öffnen** Methode, um sie später erneut öffnen. Um ein Objekt vom Arbeitsspeicher vollständig zu vermeiden, legen Sie die Objektvariable auf *nichts*.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** bei Verwendung für eine clientseitige **Verbindung** -Objekt, das **öffnen** Methode nicht tatsächlich eine Verbindung mit dem Server bis Herstellen einer [Recordset ](../../../ado/reference/ado-api/recordset-object-ado.md) wird geöffnet, auf die **Verbindung** Objekt.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Öffnen Sie und schließen Sie die Methode – Beispiel (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Öffnen Sie und schließen Sie die Methode – Beispiel (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Öffnen Sie und schließen Sie die Methode – Beispiel (VC++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open Sie-Methode (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open Sie-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open Sie-Methode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema-Methode](../../../ado/reference/ado-api/openschema-method.md)
