---
description: Reshape Name – dynamische Eigenschaft (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: f5b7f98d4ba18533342e3fa2c45270b332d4bbc2
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777699"
---
# <a name="reshape-name-property-dynamic-ado"></a>Reshape Name – dynamische Eigenschaft (ADO)
Gibt einen Namen für das [Recordset](./recordset-object-ado.md) -Objekt an.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **Zeichen** folgen Wert zurück, der dem Namen des **Recordsets**entspricht.  
  
## <a name="remarks"></a>Bemerkungen  
 Namen bleiben für die Dauer der Verbindung oder bis zum Schließen des **Recordsets** erhalten.  
  
 Die Eigenschaft " **Name Umformen** " ist hauptsächlich für die Verwendung mit der Umgestaltung der Funktion des Microsoft-Daten Strukturierungs [Dienstanbieters für OLE DB](../../guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) Dienstanbieter vorgesehen. Namen müssen eindeutig sein, um an der Umgestaltung beteiligt werden zu können.  
  
 Diese Eigenschaft ist schreibgeschützt, kann aber indirekt festgelegt werden, wenn ein **Recordset** erstellt wird. Wenn z. b. eine-Klausel eines Shape-Befehls ein **Recordset** erstellt und ihm einen Aliasnamen mit dem **As** -Schlüsselwort übergibt, wird der Alias der Eigenschaft **Reshape-Name** zugewiesen. Wenn kein Alias deklariert ist, wird der Eigenschaft **Name neu** strukturieren ein eindeutiger Name zugewiesen, der vom Daten Strukturierungs Dienst generiert wurde. Wenn der Aliasname mit dem Namen eines vorhandenen **Recordsets**identisch ist, kann keines der **Recordsets** umgestaltet werden, bis einer von Ihnen freigegeben wird. Das Standardverhalten kann geändert werden, indem Sie einen eindeutigen Namen in der Eigenschaft " [Name Umformen]() " in der ADO-Verbindung auf " **true**" festlegen. Durch Festlegen dieser Eigenschaft erhält der Daten Strukturierungs Dienst die Berechtigung, den vom Benutzer zugewiesenen Namen ggf. zu ändern, um die Eindeutigkeit sicherzustellen. Weitere Informationen zur Umgestaltung finden Sie unter [Microsoft Data Strukturierung Service for OLE DB (ADO Service Provider)](../../guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md).  
  
 Verwenden Sie die Eigenschaft **Name Umformen** , wenn Sie auf ein **Recordset** in einem Shape-Befehl verweisen möchten oder wenn Sie den Namen nicht kennen, weil er vom Daten Strukturierungs Dienst generiert wurde. In diesem Fall können Sie einen Shape-Befehl generieren, indem Sie den Befehl um die Zeichenfolge verketten, die von der Eigenschaft " **Name reshape** " zurückgegeben wird.  
  
 **Reshape Name** ist eine dynamische Eigenschaft, die an die [Properties](./properties-collection-ado.md) -Auflistung des **Recordset** -Objekts angehängt wird, wenn die [Cursor Location](./cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft-Daten Strukturierungs Dienst für OLE DB (ADO-Dienstanbieter)](../../guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [Shape-Befehle im allgemeinen](../../guide/data/shape-commands-in-general.md)   
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)