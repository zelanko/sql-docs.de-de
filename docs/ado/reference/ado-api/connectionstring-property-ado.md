---
title: ConnectionString-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::ConnectionString
helpviewer_keywords:
- ConnectionString property [ADO]
ms.assetid: 3be75b75-4d36-4479-ab64-9a456869252a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01a930bc571e84c6ecfd38ce8415493c90ebd377
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828899"
---
# <a name="connectionstring-property-ado"></a>ConnectionString-Eigenschaft (ADO)
Gibt an, die Informationen, die zum Herstellen einer Verbindung mit einer Datenquelle verwendet.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Zeichenfolge** Wert.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **"ConnectionString"** Eigenschaft, um eine Datenquelle angeben, indem Sie eine ausführliche Verbindungszeichenfolge, die mit einer Reihe von übergeben *Argument* *= Value* Anweisungen durch getrennt ein Semikolon.  
  
 ADO unterstützt fünf Argumente für die **"ConnectionString"** Eigenschaft; alle anderen Argumente übergeben direkt an den Anbieter ohne jede Verarbeitung von ADO. Die Argumente ADO unterstützt lauten wie folgt aus.  
  
|Argument|Description|  
|--------------|-----------------|  
|*Provider=*|Gibt den Namen eines Anbieters für die Verbindung verwendet.|  
|*Dateiname =*|Gibt den Namen einer anbieterspezifischen-Datei (z. B. eine persistente Daten Quellobjekt), die vordefinierten Verbindungsinformationen enthält.|  
|*Remoteanbieter =*|Gibt den Namen eines Anbieters verwenden, wenn eine Client-Side-Verbindung öffnen. (Nur Remotedaten-Dienst.)|  
|*Remoteserver =*|Gibt den Pfadnamen des Servers, verwenden Sie beim Öffnen einer Client-Side-Verbindung an. (Nur Remotedaten-Dienst.)|  
|*URL =*|Gibt die Verbindungszeichenfolge als eine absolute URL identifiziert eine Ressource, z. B. eine Datei oder ein Verzeichnis an.|  
  
 Nach dem Festlegen der **"ConnectionString"** -Eigenschaft, und öffnen Sie die [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt ist, wird der Anbieter ändert ggf. den Inhalt der Eigenschaft, z. B. durch Zuordnen von ADO definierten Argumentnamen zu ihren Entsprechungen für den bestimmten Anbieter.  
  
 Die **"ConnectionString"** -Eigenschaft erbt automatisch den Wert für die *"ConnectionString"* Argument der [öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) Methode, sodass Sie die aktuelle außerKraftsetzenkönnen **"ConnectionString"** -Eigenschaft während der **öffnen** Methodenaufruf.  
  
 Da die *Dateiname* Argument wird ADO, um die zugeordneten Anbieter zu laden, kann nicht übergeben werden, sowohl die *Anbieter* und *Dateiname* Argumente.  
  
 Die **"ConnectionString"** Eigenschaft ist Lese-/Schreibzugriff auf, wenn die Verbindung ist geschlossen und Read-only, wenn er geöffnet ist.  
  
 Duplikate eines Arguments in den **"ConnectionString"** Eigenschaft ignoriert werden. Die letzte Instanz von jedem Argument wird verwendet.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** bei Verwendung für eine clientseitige **Verbindung** -Objekt, das **"ConnectionString"** Eigenschaft enthalten kann, nur die *Remoteanbieter* und *Remoteserver* Parameter.  
  
 Die folgende Tabelle enthält die Standard-ADO-Anbieter für jedes Windows-Betriebssystem:  
  
|Standard-ADO-Anbieter|Windows-Betriebssystem|  
|--------------------------|------------------------------|  
|MSDASQL<br /><br /> (Um die Lesbarkeit des Quellcodes zu verbessern, explizit angeben der Name des Anbieters in der Verbindungszeichenfolge angegeben.)|Windows 2000 (32-Bit)<br /><br /> Windows XP (32-Bit)<br /><br /> Windows 2003 Server (32-Bit)<br /><br /> Windows Vista (32-Bit)<br /><br /> Windows Vista Service Pack 1 oder höher (32-Bit- und 64-Bit)<br /><br /> Windows-Versionen nach Windows Vista (32-Bit- und 64-Bit)|  
|Keine Standardeinstellung.<br /><br /> Wenn eine ADO-Anwendung auf eins der folgenden Betriebssysteme ausgeführt wird, und den Anbieter nicht explizit geben, ADO folgender Fehler zurückgegeben: "ADODB. Verbindung: Anbieter wird nicht angegeben, und es wurde kein angegebene Standardanbieter "|Windows 2000 (64-Bit)<br /><br /> Windows XP (64-Bit)<br /><br /> Windows 2003 Server (64-Bit)<br /><br /> Windows Vista (64-Bit)|  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ConnectionString und ConnectionTimeout State-Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString und ConnectionTimeout State-Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Anhang A: Daten und Dienstanbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
