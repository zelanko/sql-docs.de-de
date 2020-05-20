---
title: Command-Objekt (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command
helpviewer_keywords:
- Command object [ADO]
ms.assetid: a02c22fb-542d-465e-a629-30fd59dcbebf
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f6b2e68947959ecd497645d2290bb7acaa03f86
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760404"
---
# <a name="command-object-ado"></a>Command-Objekt (ADO)
Definiert einen bestimmten Befehl, den Sie für eine Datenquelle ausführen möchten.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie ein **Command** -Objekt zum Abfragen einer Datenbank und zum Zurückgeben von Datensätzen in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt, zum Ausführen eines Massen Vorgangs oder zum Bearbeiten der Struktur einer Datenbank. Abhängig von der Funktionalität des Anbieters können einige **Befehls** Auflistungen, Methoden oder Eigenschaften einen Fehler generieren, wenn auf Sie verwiesen wird.  
  
 Mit den Auflistungen, Methoden und Eigenschaften eines **Befehls** Objekts können Sie folgende Aufgaben ausführen:  
  
-   Definieren Sie den ausführbaren Text des Befehls (z. b. eine SQL-Anweisung) mit der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) -Eigenschaft. Alternativ können Sie für andere Befehls-oder Abfrage Strukturen als einfache Zeichen folgen (z. b. XML-Vorlagen Abfragen) den Befehl mit der [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) -Eigenschaft definieren.  
  
-   Geben Sie optional den Befehls Dialekt an, der in **CommandText** oder **CommandStream** mit der [Dialekt](../../../ado/reference/ado-api/dialect-property.md) -Eigenschaft verwendet wird.  
  
-   Definieren Sie parametrisierte Abfragen oder Argumente für gespeicherte Prozeduren mit [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekten und der [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung.  
  
-   Geben Sie an, ob Parameternamen mit der [namedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) -Eigenschaft an den Anbieter übergeben werden sollen.  
  
-   Führen Sie einen Befehl aus, und geben Sie bei Bedarf ein **Recordset** -Objekt mit der [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) -Methode zurück.  
  
-   Geben Sie den Typ des Befehls mit der [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) -Eigenschaft vor der Ausführung an, um die Leistung zu optimieren.  
  
-   Steuert, ob der Anbieter vor der Ausführung mit der [vorbereiteten](../../../ado/reference/ado-api/prepared-property-ado.md) Eigenschaft eine vorbereitete (oder kompilierte) Version des Befehls speichert.  
  
-   Legen Sie die Anzahl von Sekunden fest, die ein Anbieter darauf wartet, dass ein Befehl mit der [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md) -Eigenschaft ausgeführt wird.  
  
-   Ordnen Sie eine geöffnete Verbindung einem **Befehls** Objekt zu, indem Sie die zugehörige [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) -Eigenschaft festlegen.  
  
-   Legen Sie die [Name](../../../ado/reference/ado-api/name-property-ado.md) -Eigenschaft fest, um das **Command** -Objekt als Methode für das zugeordnete [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt zu identifizieren.  
  
-   Übergeben Sie ein **Command** -Objekt an die [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) -Eigenschaft eines **Recordsets** , um Daten abzurufen.  
  
-   Greifen Sie mit der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung auf anbieterspezifische Attribute zu.  
  
> [!NOTE]
>  Wenn Sie eine Abfrage ohne ein **Befehls** Objekt ausführen möchten, übergeben Sie eine Abfrage Zeichenfolge an die [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) -Methode eines **Verbindungs** Objekts oder an die [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode eines **Recordset** -Objekts. Ein **Command** -Objekt ist jedoch erforderlich, wenn Sie den Befehls Text persistent speichern und erneut ausführen oder Abfrage Parameter verwenden möchten.  
  
 Wenn Sie ein **Befehls** Objekt unabhängig von einem zuvor definierten **Verbindungs** Objekt erstellen möchten, legen Sie die zugehörige **ActiveConnection** -Eigenschaft auf eine gültige Verbindungs Zeichenfolge fest. ADO erstellt weiterhin ein **Verbindungs** Objekt, weist dieses Objekt jedoch nicht einer Objektvariablen zu. Wenn Sie jedoch mehrere **Befehls** Objekte derselben Verbindung zuordnen, sollten Sie explizit ein **Verbindungs** Objekt erstellen und öffnen. Dadurch wird das **Verbindungs** Objekt einer Objektvariablen zugewiesen. Stellen Sie sicher, dass das **Verbindungs** Objekt erfolgreich geöffnet wurde, bevor Sie es der **ActiveConnection** -Eigenschaft des **Befehls** Objekts zuweisen, da das Zuweisen eines geschlossenen **Verbindungs** Objekts einen Fehler verursacht. Wenn Sie die **ActiveConnection** -Eigenschaft des **Command** -Objekts nicht auf diese Objekt Variable festlegen, erstellt ADO ein neues **Verbindungs** Objekt für jedes **Befehls** Objekt, auch wenn Sie dieselbe Verbindungs Zeichenfolge verwenden.  
  
 Um einen **Befehl**auszuführen, nennen Sie ihn anhand seiner [Name](../../../ado/reference/ado-api/name-property-ado.md) -Eigenschaft für das zugeordnete **Verbindungs** Objekt. Für den **Befehl** muss die **ActiveConnection** -Eigenschaft auf das **Verbindungs** Objekt festgelegt sein. Wenn der **Befehl** über Parameter verfügt, übergeben Sie seine Werte als Argumente an die-Methode.  
  
 Wenn zwei oder mehr **Befehls** Objekte für dieselbe Verbindung ausgeführt werden und ein **Befehls** Objekt eine gespeicherte Prozedur mit Ausgabeparametern ist, tritt ein Fehler auf. Verwenden Sie separate Verbindungen, oder trennen Sie alle anderen **Befehls** Objekte von der Verbindung, um jedes **Befehls** Objekt auszuführen.  
  
 Die **Parameters** -Auflistung ist das Standardelement des **Command** -Objekts. Folglich sind die folgenden zwei Code Anweisungen Äquivalent.  
  
```  
objCmd.Parameters.Item(0)  
objCmd(0)  
```  
  
-   Das **Command** -Objekt ist für die Skripterstellung nicht sicher.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Befehls Objekteigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/command-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Parameter Auflistung (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
