---
title: CommandText-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandText
helpviewer_keywords:
- CommandText property [ADO]
ms.assetid: 4dd7e82a-8da5-4a4e-b439-11a29286fa0e
author: rothja
ms.author: jroth
ms.openlocfilehash: 0fea58e679e11ac068189ad622b3dce627fc8a63
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760436"
---
# <a name="commandtext-property-ado"></a>CommandText-Eigenschaft (ADO)
Gibt den Text eines Befehls an, der für einen Anbieter ausgegeben werden soll.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Ruft einen **Zeichen** folgen Wert ab, der einen Anbieter Befehl enthält, z. b. eine SQL-Anweisung, einen Tabellennamen, einen relative URL oder einen gespeicherten Prozedur Aufruf, oder legt diesen fest. Der Standardwert ist eine leere Zeichenfolge ("").  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **CommandText** -Eigenschaft, um den Text eines Befehls festzulegen oder zurückzugeben, der von einem [Command](../../../ado/reference/ado-api/command-object-ado.md) -Objekt dargestellt wird. In der Regel handelt es sich hierbei um eine SQL-Anweisung, aber es kann sich auch um eine beliebige andere Art von Befehls Anweisung handeln, die vom Anbieter erkannt wird Eine SQL-Anweisung muss einen bestimmten Dialekt oder eine bestimmte Version aufweisen, die vom Abfrage Prozessor des Anbieters unterstützt wird.  
  
 Wenn die [vorbereitete](../../../ado/reference/ado-api/prepared-property-ado.md) -Eigenschaft des **Command** -Objekts auf **true** festgelegt ist und das **Command** -Objekt beim Festlegen der **CommandText** -Eigenschaft an eine geöffnete Verbindung gebunden ist, bereitet ADO die Abfrage (d. h. eine kompilierte Form der Abfrage, die vom Anbieter gespeichert wird) vor, wenn Sie die [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) -oder [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) -Methode aufzurufen.  
  
 Abhängig von der [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) -Eigenschafts Einstellung kann ADO die **CommandText** -Eigenschaft ändern. Sie können die **CommandText** -Eigenschaft jederzeit lesen, um den eigentlichen Befehls Text anzuzeigen, der von ADO während der Ausführung verwendet wird.  
  
 Verwenden Sie die **CommandText** -Eigenschaft, um eine relative URL festzulegen oder zurückzugeben, die eine Ressource angibt, z. b. eine Datei oder ein Verzeichnis. Die Ressource ist relativ zu einem Speicherort, der explizit von einem absolute URL oder implizit durch ein geöffnetes [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt angegeben wird.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Requery-Methode](../../../ado/reference/ado-api/requery-method.md)   
 [Beispiel für ActiveConnection, CommandText, CommandTimeout, CommandType, Size und Direction Properties (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
