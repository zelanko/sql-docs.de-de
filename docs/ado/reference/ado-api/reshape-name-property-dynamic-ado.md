---
title: Reshape Name Property-Dynamic (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reshape Name property [ADO]
ms.assetid: 690229d1-46cc-42e6-a57d-4438251fe248
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ec72b2b1908f967caee4610e27315acaab787ac9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917170"
---
# <a name="reshape-name-property-dynamic-ado"></a>Reshape Name – dynamische Eigenschaft (ADO)
Gibt einen Namen für das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt an.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **Zeichen** folgen Wert zurück, der dem Namen des **Recordsets**entspricht.  
  
## <a name="remarks"></a>Hinweise  
 Namen bleiben für die Dauer der Verbindung oder bis zum Schließen des **Recordsets** erhalten.  
  
 Die Eigenschaft " **Name Umformen** " ist hauptsächlich für die Verwendung mit der Umgestaltung der Funktion des Microsoft-Daten Strukturierungs [Dienstanbieters für OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) Dienstanbieter vorgesehen. Namen müssen eindeutig sein, um an der Umgestaltung beteiligt werden zu können.  
  
 Diese Eigenschaft ist schreibgeschützt, kann aber indirekt festgelegt werden, wenn ein **Recordset** erstellt wird. Wenn z. b. eine-Klausel eines Shape-Befehls ein **Recordset** erstellt und ihm einen Aliasnamen mit dem **As** -Schlüsselwort übergibt, wird der Alias der Eigenschaft **Reshape-Name** zugewiesen. Wenn kein Alias deklariert ist, wird der Eigenschaft **Name neu** strukturieren ein eindeutiger Name zugewiesen, der vom Daten Strukturierungs Dienst generiert wurde. Wenn der Aliasname mit dem Namen eines vorhandenen **Recordsets**identisch ist, kann keines der **Recordsets** umgestaltet werden, bis einer von Ihnen freigegeben wird. Das Standardverhalten kann geändert werden, indem Sie einen eindeutigen Namen in der Eigenschaft " [Name Umformen](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md) " in der ADO-Verbindung auf " **true**" festlegen. Durch Festlegen dieser Eigenschaft erhält der Daten Strukturierungs Dienst die Berechtigung, den vom Benutzer zugewiesenen Namen ggf. zu ändern, um die Eindeutigkeit sicherzustellen. Weitere Informationen zur Umgestaltung finden Sie unter [Microsoft Data Strukturierung Service for OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md).  
  
 Verwenden Sie die Eigenschaft **Name Umformen** , wenn Sie auf ein **Recordset** in einem Shape-Befehl verweisen möchten oder wenn Sie den Namen nicht kennen, weil er vom Daten Strukturierungs Dienst generiert wurde. In diesem Fall können Sie einen Shape-Befehl generieren, indem Sie den Befehl um die Zeichenfolge verketten, die von der Eigenschaft " **Name reshape** " zurückgegeben wird.  
  
 **Reshape Name** ist eine dynamische Eigenschaft, die an die [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung des **Recordset** -Objekts angehängt wird, wenn die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft-Daten Strukturierungs Dienst für OLE DB (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [Shape-Befehle im allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
