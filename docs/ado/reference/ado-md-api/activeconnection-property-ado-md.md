---
description: ActiveConnection-Eigenschaft (ADO MD)
title: ActiveConnection-Eigenschaft (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActiveConnection
- Cellset::ActiveConnection
- Catalog::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO MD]
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
author: rothja
ms.author: jroth
ms.openlocfilehash: ea9319e89c44b9cbb66b3acecdcbea4afa3e61c4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776778"
---
# <a name="activeconnection-property-ado-md"></a>ActiveConnection-Eigenschaft (ADO MD)
Gibt an, zu welchem ADO- [Verbindungs](../ado-api/connection-object-ado.md) Objekt das aktuelle Cellset oder der aktuelle Katalog gehört.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt eine **Variante** fest oder gibt Sie zurück, die eine Zeichenfolge enthält, die eine Verbindung oder ein **Verbindungs** Objekt definiert Der Standardwert ist leer.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können diese Eigenschaft auf ein gültiges ADO- **Verbindungs** Objekt oder auf eine gültige Verbindungs Zeichenfolge festlegen. Wenn diese Eigenschaft auf eine Verbindungs Zeichenfolge festgelegt ist, erstellt der Anbieter mithilfe dieser Definition ein neues **Verbindungs** Objekt und öffnet die Verbindung.  
  
 Wenn Sie das *ActiveConnection* -Argument der [Open](./open-method-ado-md.md) -Methode verwenden, um ein [Cellset](./cellset-object-ado-md.md) -Objekt zu öffnen, erbt die **ActiveConnection** -Eigenschaft den Wert des-Arguments.  
  
 Wenn die **ActiveConnection** -Eigenschaft eines [catalog](./catalog-object-ado-md.md) -Objekts auf **Nothing** festgelegt wird, werden die zugeordneten Daten freigegeben, einschließlich der Daten in der [CubeDefs](./cubedefs-collection-ado-md.md) -Auflistung und aller zugehörigen [Dimensions](./dimension-object-ado-md.md) [-,](./member-object-ado-md.md) [Hierarchie](./hierarchy-object-ado-md.md)-, [Ebene](./level-object-ado-md.md)-und Element Objekte Das Schließen eines **Verbindungs** Objekts, das zum Öffnen eines **Katalogs** verwendet wurde, hat dieselbe Auswirkung wie das Festlegen der **ActiveConnection** -Eigenschaft auf " **Nothing**".  
  
 Durch Ändern der Standarddatenbank der Verbindung, auf die von der **ActiveConnection** -Eigenschaft eines **Katalog** Objekts verwiesen wird, wird der Inhalt des **Katalogs**ungültig.  
  
 Wenn Sie versuchen, die **ActiveConnection** -Eigenschaft für ein geöffnetes **Cellset** -Objekt zu ändern, tritt ein Fehler auf.  
  
> [!NOTE]
>  Denken Sie in Visual Basic daran, das **Set** -Schlüsselwort zu verwenden, wenn Sie die **ActiveConnection** -Eigenschaft auf ein **Connection** -Objekt festlegen. Wenn Sie das Set-Schlüsselwort weglassen, **legen** Sie die **ActiveConnection** -Eigenschaft tatsächlich auf die Standard Eigenschaft **ConnectionString**des **Verbindungs** Objekts fest. Der Code funktioniert. Allerdings erstellen Sie eine zusätzliche Verbindung mit der Datenquelle, die negative Auswirkungen auf die Leistung haben kann.  
  
 Wenn Sie den MSOLAP-Datenanbieter verwenden, legen Sie die Datenquelle in einer Verbindungs Zeichenfolge auf einen Servernamen fest, und legen Sie den Anfangs Katalog auf den Namen eines Katalogs aus der Datenquelle fest. Legen Sie den Speicherort auf den vollständigen Pfad fest, um eine Verbindung mit einer Cube-Datei herzustellen, die von einem Server getrennt ist. CUB-Datei. Legen Sie den Anbieter in beiden Fällen auf den Anbieter Namen fest. Die folgende Zeichenfolge verwendet beispielsweise den MSOLAP-Anbieter, um eine Verbindung mit einem Katalog mit dem Namen "BOSB Video Store" auf einem Server namens "Server **Name**" herzustellen:  
  
```  
"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"  
```  
  
 Die folgende Zeichenfolge stellt eine Verbindung mit einer lokalen Cubedatei am Speicherort c:\MSDASDK\samples\oledb\olap\data\bobsvid.Cub her:  
  
```  
"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"  
```  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Catalog-Objekt (ADO MD)](./catalog-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Cellset-Objekt (ADO MD)](./cellset-object-ado-md.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Cellset-Beispiel (VB)](./cellset-example-vb.md)   
 [Verbindungs Objekt (ADO)](../ado-api/connection-object-ado.md)   
 [Open-Methode (ADO MD)](./open-method-ado-md.md)