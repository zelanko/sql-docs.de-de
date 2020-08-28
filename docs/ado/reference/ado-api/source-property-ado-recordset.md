---
description: Source-Eigenschaft (ADO-Recordset)
title: Source-Eigenschaft (ADO-Recordset) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3a71efe111a58ab8f799db512e77da4365ba5f48
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988901"
---
# <a name="source-property-ado-recordset"></a>Source-Eigenschaft (ADO-Recordset)
Gibt die Datenquelle für ein [Recordset](./recordset-object-ado.md) -Objekt an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert oder einen [Befehls](./command-object-ado.md) Objekt Verweis fest. gibt nur einen **Zeichen** folgen Wert zurück, der die Quelle des **Recordsets**angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Source** -Eigenschaft zum Angeben einer Datenquelle für ein **Recordset** -Objekt, indem Sie eine der folgenden Aktionen verwenden: eine **Befehls** Objekt Variable, eine SQL-Anweisung, eine gespeicherte Prozedur oder ein Tabellenname.  
  
 Wenn Sie die **Source** -Eigenschaft auf ein **Befehls** Objekt festlegen, erbt die [ActiveConnection](./activeconnection-property-ado.md) -Eigenschaft des **Recordset** -Objekts den Wert der **ActiveConnection** -Eigenschaft für das angegebene **Befehls** Objekt. Beim Lesen der **Source** -Eigenschaft wird jedoch kein **Befehls** Objekt zurückgegeben. Stattdessen wird die [CommandText](./commandtext-property-ado.md) -Eigenschaft des **Command** -Objekts zurückgegeben, für das Sie die **Source** -Eigenschaft festlegen.  
  
 Wenn die **Source** -Eigenschaft eine SQL-Anweisung, eine gespeicherte Prozedur oder ein Tabellenname ist, können Sie die Leistung optimieren, indem Sie das entsprechende *options* Argument mit dem [Open](./open-method-ado-recordset.md) -Methoden-Befehl übergeben.  
  
 Die **Source** -Eigenschaft ist Lese-/Schreibzugriff für geschlossene **Recordset** -Objekte und für geöffnete **Recordset** -Objekte schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für eine Quell Eigenschaft (VB)](./source-property-example-vb.md)   
 [Source-Eigenschaft (ADO-Fehler)](./source-property-ado-error.md)   
 [Source-Eigenschaft (ADO-Datensatz)](./source-property-ado-record.md)