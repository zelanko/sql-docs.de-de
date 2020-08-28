---
description: Source-Eigenschaft (ADO-Datensatz)
title: Source-Eigenschaft (ADO-Datensatz) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::Source
- _Record::PutRefSource
- _Record::GetSource
- _Record::put_Source
- _Record::putref_Source
- _Record::get_Source
helpviewer_keywords:
- Source property [ADO Record]
ms.assetid: 2c18279e-6f35-4af0-b12e-8f1543d9ed20
author: rothja
ms.author: jroth
ms.openlocfilehash: b9c551e52864caca8834350d5107b76aed88700d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988941"
---
# <a name="source-property-ado-record"></a>Source-Eigenschaft (ADO-Datensatz)
Gibt die Datenquelle oder das Objekt an, das durch den [Datensatz](./record-object-ado.md)dargestellt wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Variant** -Wert fest, der die vom **Datensatz**dargestellte Entität angibt, oder gibt diesen zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Source** -Eigenschaft gibt das *Quell* Argument der [Open](./open-method-ado-record.md) -Methode des **Datensatz** -Objekts zurück. Sie kann eine absolute oder relative URL Zeichenfolge enthalten. Eine absolute URL kann ohne Festlegen der [ActiveConnection](./activeconnection-property-ado.md) -Eigenschaft verwendet werden, um das **Datensatz** -Objekt direkt zu öffnen. In diesem Fall wird ein implizites **Verbindungs** Objekt erstellt.  
  
 Die **Source** -Eigenschaft kann auch einen Verweis auf ein bereits geöffnetes **Recordset**enthalten, das ein **Daten Satz** Objekt öffnet, das die aktuelle Zeile im **Recordset**darstellt.  
  
 Die **Source** -Eigenschaft könnte auch einen Verweis auf ein [Befehls](./command-object-ado.md) Objekt enthalten, das eine einzelne Daten Zeile vom Anbieter zurückgibt.  
  
 Wenn die **ActiveConnection** -Eigenschaft ebenfalls festgelegt ist, muss die **Source** -Eigenschaft auf ein Objekt verweisen, das im Gültigkeitsbereich dieser Verbindung vorhanden ist. Wenn z. b. in Struktur strukturierten Namespaces die **Quell** Eigenschaft eine absolute URL enthält, muss Sie auf einen Knoten zeigen, der im Bereich des Knotens vorhanden ist, der durch die URL in der Verbindungs Zeichenfolge identifiziert wird. Wenn die **Source** -Eigenschaft eine relative URL enthält, wird Sie innerhalb des durch die **ActiveConnection** -Eigenschaft festgelegten Kontexts überprüft.  
  
 Die **Source** -Eigenschaft ist Lese-/Schreibzugriff, während das **Datensatz** -Objekt geschlossen wird. Sie ist schreibgeschützt, während das **Datensatz** -Objekt geöffnet ist.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](./record-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Source-Eigenschaft (ADO-Fehler)](./source-property-ado-error.md)   
 [Source-Eigenschaft (ADO-Recordset)](./source-property-ado-recordset.md)