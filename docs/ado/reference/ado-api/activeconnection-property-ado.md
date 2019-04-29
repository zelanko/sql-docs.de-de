---
title: ActiveConnection-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::ActiveConnection
- Recordset15::get_ActiveConnection
- _Record::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO]
ms.assetid: 52d0a96c-14fb-4ad9-b004-4d821bc0a6db
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 951f43a2842162aa00f664dc83b754d06d8aafb2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065538"
---
# <a name="activeconnection-property-ado"></a>ActiveConnection-Eigenschaft (ADO)
Gibt an, zu dem [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt das angegebene [Befehl](../../../ado/reference/ado-api/command-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), oder [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt derzeit gehört.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Zeichenfolge** Wert, der eine Definition für eine Verbindung enthält, wenn die Verbindung geschlossen wird, oder ein **Variant** mit dem aktuellen **Verbindung** Objekt, wenn die Verbindung ist geöffnet. Standardwert ist ein null-Objektverweis. Finden Sie unter den ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) Eigenschaft.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **ActiveConnection** Eigenschaft, um zu bestimmen, die **Verbindung** Objekt über den angegebenen **Befehl** Objekt ausgeführt wird oder die angegebene  **Recordset** wird geöffnet.  
  
## <a name="command"></a>Befehl  
 Für **Befehl** Objekte, die **ActiveConnection** Eigenschaft schreibgeschützt ist.  
  
 Wenn Sie versuchen, rufen Sie die [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) Methode für eine **Befehl** Objekt vor dem Festlegen dieser Eigenschaft auf ein offenes **Verbindung** Objekt oder eine gültige Verbindungszeichenfolge, ein Fehler auftritt.  
  
 Wenn eine **Verbindung** Objekt zugewiesen wird die **ActiveConnection** -Eigenschaft des Objekts muss geöffnet sein. Zuweisen eines geschlossenen Verbindungsobjekts verursacht einen Fehler.  
  
### <a name="note"></a>Hinweis  
 **Microsoft Visual Basic** Einstellung der **ActiveConnection** Eigenschaft *nichts* hebt die Zuordnung der **Befehl** Objekt aus dem aktuellen **Verbindung** und bewirkt, dass den Anbieter für die Datenquelle zugeordneten Ressourcen freizugeben. Sie können dann Zuordnen der **Befehl** Objekt mit der gleichen oder einem anderen **Verbindung** Objekt. Einige Anbieter ermöglichen es Ihnen, ändern Sie die Einstellung der Eigenschaft von einem **Verbindung** in eine andere, ohne zuerst die Eigenschaft auf festgelegt *nichts*.  
  
 Wenn die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung von der **Befehl** Objekt enthält Parameter, die vom Anbieter bereitgestellten, die die Auflistung wird gelöscht, wenn Sie festlegen, die **ActiveConnection** Eigenschaft, um *nichts* oder einem anderen **Verbindung** Objekt. Bei der Erstellung manuell [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekte aus, und verwenden sie zum Füllen der **Parameter** Auflistung von der **Befehl** Objekt, und legen die **ActiveConnection**  Eigenschaft *nichts* oder einem anderen **Verbindung** Objekt / / Blätter der **Parameter** Auflistung intakt.  
  
 Schließen der **Verbindung** Objekt, mit dem eine **Befehl** Objekt wird verknüpft legt die **ActiveConnection** Eigenschaft *"Nothing"*. Wenn diese Eigenschaft auf ein geschlossenes **Verbindung** Objekt wird ein Fehler generiert.  
  
## <a name="recordset"></a>Recordset  
 Für offene **Recordset** Objekte oder **Recordset** Objekte, deren [Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md) -Eigenschaftensatz auf einen gültigen **Befehl** -Objekt, das **ActiveConnection** Eigenschaft ist schreibgeschützt. Andernfalls ist sie Lese-/Schreibzugriff.  
  
 Sie können diese Eigenschaft festlegen, um eine gültige **Verbindung** Objekt oder eine gültige Verbindungszeichenfolge. In diesem Fall erstellt der Anbieter eine neue **Verbindung** Objekt mit dieser Definition und öffnet die Verbindung. Darüber hinaus kann der Anbieter diese Eigenschaft festlegen, mit dem neuen **Verbindung** Objekt, das Sie bieten eine Möglichkeit zum Zugriff auf die **Verbindung** -Objekt für erweiterte Fehlerinformationen oder andere Befehle ausführen.  
  
 Bei Verwendung der *ActiveConnection* Argument der [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methode zum Öffnen eine **Recordset** -Objekt, die **ActiveConnection** Eigenschaft wird erben Sie den Wert des Arguments.  
  
 Setzen Sie die **Quelle** Eigenschaft der **Recordset** Objekt auf eine gültige **Befehl** Objektvariable, die **ActiveConnection** Eigenschaft die **Recordset** erbt von der Einstellung der **Befehl** des Objekts **ActiveConnection** Eigenschaft.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** bei Verwendung für eine clientseitige **Recordset** Objekt, diese Eigenschaft kann nur auf eine Verbindungszeichenfolge oder (in Microsoft Visual Basic oder Visual Basic Scripting Edition) festgelegt werden *"Nothing"* .  
  
## <a name="record"></a>Datensatz  
 Diese Eigenschaft ist Lese-/Schreibzugriff bei der **Datensatz** -Objekt geschlossen ist, und eventuell eine Verbindungszeichenfolge oder einen Verweis auf ein offenes **Verbindung** Objekt. Diese Eigenschaft ist schreibgeschützt und wann die **Datensatz** Objekt geöffnet ist, und enthält einen Verweis auf ein offenes **Verbindung** Objekt.  
  
 Ein **Verbindung** Objekt wird implizit erstellt, wenn die **Datensatz** Objekt über eine URL geöffnet wird. Öffnen der **Datensatz** öffnen Sie mit einem vorhandenen **Verbindung** Objekt durch Zuweisen der **Verbindung** Objekt für diese Eigenschaft oder mithilfe der **Verbindung** Objekt als Parameter in der [öffnen](../../../ado/reference/ado-api/open-method-ado-record.md) Methodenaufruf. Wenn die **Datensatz** wird geöffnet, aus einer vorhandenen **Datensatz** oder [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), ist es automatisch zugeordnet **Datensatz** oder  **Recordset** des Objekts **Verbindung** Objekt.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText-Eigenschaft, "CommandTimeout", Befehlstyp (CommandType), Größe und Richtung Eigenschaften – Beispiel (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [ConnectionString-Eigenschaft (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)
