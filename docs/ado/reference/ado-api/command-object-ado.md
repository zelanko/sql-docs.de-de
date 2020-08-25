---
description: Command-Objekt (ADO)
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
ms.openlocfilehash: d876be4883844790815a0640d26cee2933ca17f2
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776159"
---
# <a name="command-object-ado"></a>Command-Objekt (ADO)
Definiert einen bestimmten Befehl, den Sie für eine Datenquelle ausführen möchten.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie ein **Command** -Objekt zum Abfragen einer Datenbank und zum Zurückgeben von Datensätzen in einem [Recordset](./recordset-object-ado.md) -Objekt, zum Ausführen eines Massen Vorgangs oder zum Bearbeiten der Struktur einer Datenbank. Abhängig von der Funktionalität des Anbieters können einige **Befehls** Auflistungen, Methoden oder Eigenschaften einen Fehler generieren, wenn auf Sie verwiesen wird.  
  
 Mit den Auflistungen, Methoden und Eigenschaften eines **Befehls** Objekts können Sie folgende Aufgaben ausführen:  
  
-   Definieren Sie den ausführbaren Text des Befehls (z. b. eine SQL-Anweisung) mit der [CommandText](./commandtext-property-ado.md) -Eigenschaft. Alternativ können Sie für andere Befehls-oder Abfrage Strukturen als einfache Zeichen folgen (z. b. XML-Vorlagen Abfragen) den Befehl mit der [CommandStream](./commandstream-property-ado.md) -Eigenschaft definieren.  
  
-   Geben Sie optional den Befehls Dialekt an, der in **CommandText** oder **CommandStream** mit der [Dialekt](./dialect-property.md) -Eigenschaft verwendet wird.  
  
-   Definieren Sie parametrisierte Abfragen oder Argumente für gespeicherte Prozeduren mit [Parameter](./parameter-object.md) Objekten und der [Parameter](./parameters-collection-ado.md) Auflistung.  
  
-   Geben Sie an, ob Parameternamen mit der [namedParameters](./namedparameters-property-ado.md) -Eigenschaft an den Anbieter übergeben werden sollen.  
  
-   Führen Sie einen Befehl aus, und geben Sie bei Bedarf ein **Recordset** -Objekt mit der [Execute](./execute-method-ado-command.md) -Methode zurück.  
  
-   Geben Sie den Typ des Befehls mit der [CommandType](./commandtype-property-ado.md) -Eigenschaft vor der Ausführung an, um die Leistung zu optimieren.  
  
-   Steuert, ob der Anbieter vor der Ausführung mit der [vorbereiteten](./prepared-property-ado.md) Eigenschaft eine vorbereitete (oder kompilierte) Version des Befehls speichert.  
  
-   Legen Sie die Anzahl von Sekunden fest, die ein Anbieter darauf wartet, dass ein Befehl mit der [CommandTimeout](./commandtimeout-property-ado.md) -Eigenschaft ausgeführt wird.  
  
-   Ordnen Sie eine geöffnete Verbindung einem **Befehls** Objekt zu, indem Sie die zugehörige [ActiveConnection](./activeconnection-property-ado.md) -Eigenschaft festlegen.  
  
-   Legen Sie die [Name](./name-property-ado.md) -Eigenschaft fest, um das **Command** -Objekt als Methode für das zugeordnete [Verbindungs](./connection-object-ado.md) Objekt zu identifizieren.  
  
-   Übergeben Sie ein **Command** -Objekt an die [Source](./source-property-ado-recordset.md) -Eigenschaft eines **Recordsets** , um Daten abzurufen.  
  
-   Greifen Sie mit der [Properties](./properties-collection-ado.md) -Auflistung auf anbieterspezifische Attribute zu.  
  
> [!NOTE]
>  Wenn Sie eine Abfrage ohne ein **Befehls** Objekt ausführen möchten, übergeben Sie eine Abfrage Zeichenfolge an die [Execute](./execute-method-ado-connection.md) -Methode eines **Verbindungs** Objekts oder an die [Open](./open-method-ado-recordset.md) -Methode eines **Recordset** -Objekts. Ein **Command** -Objekt ist jedoch erforderlich, wenn Sie den Befehls Text persistent speichern und erneut ausführen oder Abfrage Parameter verwenden möchten.  
  
 Wenn Sie ein **Befehls** Objekt unabhängig von einem zuvor definierten **Verbindungs** Objekt erstellen möchten, legen Sie die zugehörige **ActiveConnection** -Eigenschaft auf eine gültige Verbindungs Zeichenfolge fest. ADO erstellt weiterhin ein **Verbindungs** Objekt, weist dieses Objekt jedoch nicht einer Objektvariablen zu. Wenn Sie jedoch mehrere **Befehls** Objekte derselben Verbindung zuordnen, sollten Sie explizit ein **Verbindungs** Objekt erstellen und öffnen. Dadurch wird das **Verbindungs** Objekt einer Objektvariablen zugewiesen. Stellen Sie sicher, dass das **Verbindungs** Objekt erfolgreich geöffnet wurde, bevor Sie es der **ActiveConnection** -Eigenschaft des **Befehls** Objekts zuweisen, da das Zuweisen eines geschlossenen **Verbindungs** Objekts einen Fehler verursacht. Wenn Sie die **ActiveConnection** -Eigenschaft des **Command** -Objekts nicht auf diese Objekt Variable festlegen, erstellt ADO ein neues **Verbindungs** Objekt für jedes **Befehls** Objekt, auch wenn Sie dieselbe Verbindungs Zeichenfolge verwenden.  
  
 Um einen **Befehl**auszuführen, nennen Sie ihn anhand seiner [Name](./name-property-ado.md) -Eigenschaft für das zugeordnete **Verbindungs** Objekt. Für den **Befehl** muss die **ActiveConnection** -Eigenschaft auf das **Verbindungs** Objekt festgelegt sein. Wenn der **Befehl** über Parameter verfügt, übergeben Sie seine Werte als Argumente an die-Methode.  
  
 Wenn zwei oder mehr **Befehls** Objekte für dieselbe Verbindung ausgeführt werden und ein **Befehls** Objekt eine gespeicherte Prozedur mit Ausgabeparametern ist, tritt ein Fehler auf. Verwenden Sie separate Verbindungen, oder trennen Sie alle anderen **Befehls** Objekte von der Verbindung, um jedes **Befehls** Objekt auszuführen.  
  
 Die **Parameters** -Auflistung ist das Standardelement des **Command** -Objekts. Folglich sind die folgenden zwei Code Anweisungen Äquivalent.  
  
```  
objCmd.Parameters.Item(0)  
objCmd(0)  
```  
  
-   Das **Command** -Objekt ist für die Skripterstellung nicht sicher.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Befehls Objekteigenschaften, Methoden und Ereignisse](./command-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verbindungs Objekt (ADO)](./connection-object-ado.md)   
 [Parameter Auflistung (ADO)](./parameters-collection-ado.md)   
 [Properties-Auflistung (ADO)](./properties-collection-ado.md)   
 [Anhang A: Anbieter](../../guide/appendixes/appendix-a-providers.md)