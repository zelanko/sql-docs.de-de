---
title: Execute-Methode (ADO-Verbindung) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Execute
- Connection15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 03c69320-96b2-4d85-8d49-a13b13e31578
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0489bb43ee3b41ebf4334da0d6b8045e117acc39
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695378"
---
# <a name="execute-method-ado-connection"></a>Execute-Methode (ADO-Verbindung)
Führt die angegebene Abfrage, SQL-Anweisung, gespeicherte Prozedur oder Anbieter-spezifischen Text.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) Objektverweis.  
  
#### <a name="parameters"></a>Parameter  
 *CommandText*  
 Ein **Zeichenfolge** Wert, der die SQL-Anweisung, gespeicherte Prozedur, eine URL oder Anbieter-spezifischen Text zum Ausführen enthält. **Optional**, Tabellennamen können jedoch nur verwendet werden, wenn der Anbieter SQL bewusst ist. Wenn z. B. einen Tabellennamen "Kunden" verwendet wird, voranstellen ADO die SQL-Select-Standardsyntax bilden, und übergeben "SELECT * FROM Customers" als eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] Anweisung an den Anbieter.  
  
 *RecordsAffected*  
 Optional. Ein **lange** Variablen zu dem der Anbieter gibt die Anzahl der Datensätze, die der Vorgang betroffen.  
  
 *Options*  
 Optional. Ein **lange** Wert, der angibt, wie der Anbieter die CommandText-Argument ausgewertet werden soll. Eine Bitmaske aus einem oder mehreren möglich [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) oder [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) Werte.  
  
 **Beachten Sie** verwenden die **ExecuteOptionEnum** Wert **AdExecuteNoRecords** zur Verbesserung der Leistung durch Minimierung der internen Verarbeitung und für Anwendungen, die Sie von Visual Basic 6.0 portieren.  
  
 Verwenden Sie keine **AdExecuteStream** mit der **Execute** Methode eine **Verbindung** Objekt.  
  
 Verwenden Sie nicht die Werte CommandTypeEnum AdCmdFile oder AdCmdTableDirect mit Execute. Diese Werte können nur verwendet werden, als Optionen, mit der [Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) und [Requery-Methode](../../../ado/reference/ado-api/requery-method.md) Methoden eine **Recordset**.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe der **Execute** Methode für eine [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) Objekt wird eine Abfrage, die Sie an die Methode in der CommandText-Argument, für die angegebene Verbindung übergeben ausgeführt. Wenn die CommandText-Argument gibt an, eine Abfrage Zeilen zurückgeben, werden alle Ergebnisse, die die Ausführung generiert gespeichert, in einem neuen **Recordset** Objekt. Der Anbieter gibt zurück, wenn der Befehl nicht beabsichtigt ist, Zurückgeben von Ergebnissen (z. B. ein UPDATE für SQL-Abfrage) **nichts** so lange wie die Option **AdExecuteNoRecords** angegeben ist; andernfalls ausführen gibt ein geschlossen **Recordset**.  
  
 Das zurückgegebene **Recordset** Objekt ist immer einen schreibgeschützten, nur vorwärts gerichteten Cursor. Bei Bedarf eine **Recordset** Objekt mit mehr Funktionalität, erstellen Sie zunächst eine **Recordset** Objekt, mit den Einstellungen für die gewünschte Eigenschaft der **Recordset** des Objekts [ Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methode, um die Abfrage auszuführen und den gewünschten Cursor-Typ zurück.  
  
 Den Inhalt der *CommandText* Argument für den Anbieter spezifisch sind und kann SQL-Standardsyntax oder alle besonderen Befehlsformat, das der Anbieter unterstützt.  
  
 Ein ExecuteComplete-Ereignis wird ausgelöst, wenn dieser Vorgang abgeschlossen ist.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
