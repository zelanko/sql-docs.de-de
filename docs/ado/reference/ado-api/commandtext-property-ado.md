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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7ebc6a783aa8520c3ab16465143acdf1a6bf6628
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698946"
---
# <a name="commandtext-property-ado"></a>CommandText-Eigenschaft (ADO)
Gibt den Text eines Befehls für einen Anbieter ausgestellt werden.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Ruft ab oder legt einen **Zeichenfolge** -Wert, der ein Anbieterbefehl, z. B. eine SQL-Anweisung, einen Tabellennamen an, eine relative URL oder Aufruf einer gespeicherten Prozedur enthält. Der Standardwert ist eine leere Zeichenfolge ("").  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **CommandText** -Eigenschaft festlegen oder Zurückgeben des Texts eines Befehls, dargestellt durch eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt. In der Regel wird eine SQL-Anweisung werden dies kann auch jede andere Art von Command-Anweisung, die vom Anbieter, z. B. der Aufruf einer gespeicherten Prozedur erkannt werden. Eine SQL-Anweisung muss der bestimmten Dialekt oder Version des Anbieters Abfrageprozessor unterstützt.  
  
 Wenn die [Prepared](../../../ado/reference/ado-api/prepared-property-ado.md) Eigenschaft der **Befehl** Objekt nastaven NA hodnotu **"true"** und **Befehl** Objekt an eine offene Verbindung gebunden ist, wenn Sie festlegen die **CommandText** Eigenschaft ADO bereitet die Abfrage (d. h. eine kompilierte Form der Abfrage, die vom Anbieter gespeichert ist) beim Aufrufen der [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) oder [Öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md)Methoden.  
  
 Je die [Befehlstyp (CommandType)](../../../ado/reference/ado-api/commandtype-property-ado.md) eigenschafteneinstellung ADO kann alter der **CommandText** Eigenschaft. Erhalten Sie die **CommandText** Eigenschaft zu einem beliebigen Zeitpunkt aus, um den eigentlichen Befehlstext anzuzeigen, ADO wird während der Ausführung verwenden.  
  
 Verwenden der **CommandText** Eigenschaft so festlegen oder zurückgeben eine relative URL, die eine Ressource, z. B. eine Datei oder ein Verzeichnis angibt. Die Ressource ist relativ zu einem Speicherort, die explizit angegeben werden, indem Sie eine absolute URL oder implizit eine offene [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Requery-Methode](../../../ado/reference/ado-api/requery-method.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
