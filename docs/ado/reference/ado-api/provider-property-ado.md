---
description: Provider-Eigenschaft (ADO)
title: Provider-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::get_Provider
- Connection15::PutProvider
- Connection15::put_Provider
- Connection15::GetProvider
- Connection15::Provider
helpviewer_keywords:
- Provider property [ADO]
ms.assetid: 0ff70e72-0061-4ffc-90fb-e3ea23129bb2
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c3f45e8652568bd0440121e27ee6ee0c116e676
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989911"
---
# <a name="provider-property-ado"></a>Provider-Eigenschaft (ADO)
Gibt den Namen des Anbieters für ein [Verbindungs](./connection-object-ado.md) Objekt an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest, der den Anbieter Namen angibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Provider** -Eigenschaft, um den Namen des Anbieters für eine Verbindung festzulegen oder zurückzugeben. Diese Eigenschaft kann auch durch den Inhalt der [ConnectionString](./connectionstring-property-ado.md) -Eigenschaft oder das *ConnectionString* -Argument der [Open](./open-method-ado-connection.md) -Methode festgelegt werden. Wenn Sie jedoch einen Anbieter an mehr als einem Ort angeben, während Sie die **Open** -Methode aufrufen, kann dies zu unvorhersehbaren Ergebnissen führen. Wenn kein Anbieter angegeben wird, wird die-Eigenschaft standardmäßig auf msdasql ([Microsoft OLE DB-Anbieter für ODBC](../../guide/appendixes/microsoft-ole-db-provider-for-odbc.md)) festgelegt.  
  
 Die **Provider** -Eigenschaft ist Lese-/Schreibzugriff, wenn die Verbindung geschlossen und schreibgeschützt ist, wenn Sie geöffnet ist. Die Einstellung wird erst wirksam, wenn Sie das **Verbindungs** Objekt öffnen oder auf die [Properties](./properties-collection-ado.md) -Auflistung des **Connection** -Objekts zugreifen. Wenn die Einstellung ungültig ist, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](./connection-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Anbieter und DefaultDatabase-Eigenschaften (VB)](./provider-and-defaultdatabase-properties-example-vb.md)   
 [Beispiel für Anbieter und DefaultDatabase-Eigenschaften (VB)](./provider-and-defaultdatabase-properties-example-vb.md)   
 [Microsoft OLE DB-Anbieter für ODBC](../../guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [Anhang A: Anbieter](../../guide/appendixes/appendix-a-providers.md)