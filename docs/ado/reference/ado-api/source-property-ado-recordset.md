---
title: Source-Eigenschaft (ADO Recordset) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::putref_Source
- Recordset15::Source
- Recordset15::PutSource
- Recordset15::get_Source
- Recordset15::GetSource
- Recordset15::PutRefSource
- Recordset15::put_Source
helpviewer_keywords:
- Source property [ADO Recordset]
ms.assetid: a05ba2c9-2821-4343-8607-4de9b764ec91
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 718124fce3c2ce7a1adf9e6dbdb1d54e8a834fca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655608"
---
# <a name="source-property-ado-recordset"></a>Source-Eigenschaft (ADO-Recordset)
Gibt an, die die Datenquelle für eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt eine **Zeichenfolge** Wert oder [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objektverweis ist; gibt nur eine **Zeichenfolge** -Wert, der die Quelle der gibt an die **Recordset**.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Quelle** -Eigenschaft an eine Datenquelle für eine **Recordset** -Objekt unter Verwendung eines der folgenden: eine **Befehl** Objekt-Variable, eine SQL-Anweisung, einer gespeicherten Prozedur oder einen Tabellennamen an.  
  
 Setzen Sie die **Quelle** Eigenschaft, um eine **Befehl** Objekt der [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) Eigenschaft der **Recordset** Objekt erbt die Wert, der die **ActiveConnection** -Eigenschaft für das angegebene **Befehl** Objekt. Jedoch beim Lesen der **Quelle** Eigenschaft wird nicht zurückgegeben. eine **Befehl** Objekt; stattdessen wird die [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) Eigenschaft der **Befehl** -Objekt an die Sie festlegen, die **Quelle** Eigenschaft.  
  
 Wenn die **Quelle** -Eigenschaft ist eine SQL-Anweisung, einer gespeicherten Prozedur oder einen Tabellennamen, können Sie die Leistung optimieren, übergeben Sie die entsprechende *Optionen* Argument mit den [Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md)Methodenaufruf.  
  
 Die **Quelle** Eigenschaft ist für schließen die Lese-/Schreibzugriff **Recordset** Objekte und Read-only für offene **Recordset** Objekte.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Source-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/source-property-example-vb.md)   
 [Source-Eigenschaft (ADO-Fehler)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Source-Eigenschaft (ADO Record)](../../../ado/reference/ado-api/source-property-ado-record.md)
