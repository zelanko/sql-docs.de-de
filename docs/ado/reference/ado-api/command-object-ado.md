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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 089a261eaea2701354af6082827c12491810b74c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699004"
---
# <a name="command-object-ado"></a>Command-Objekt (ADO)
Definiert einen bestimmten Befehl, den Sie für eine Datenquelle ausführen möchten.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden einer **Befehl** Objekt, das Abfragen einer Datenbank und zum Zurückgeben von Datensätzen in einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt, um einen Massenvorgang ausführen oder die Struktur einer Datenbank zu bearbeiten. Die Funktionalität des Anbieters abhängig sind, einige **Befehl** Auflistungen, Methoden oder Eigenschaften möglicherweise einen Fehler generieren, wenn auf sie verwiesen werden.  
  
 Mit den Auflistungen, Methoden und Eigenschaften einer **Befehl** -Objekts können Sie folgende Möglichkeiten:  
  
-   Definieren Sie die ausführbare Datei Text des Befehls (z. B. eine SQL­Anweisung), mit der [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) Eigenschaft. Sie können auch für Befehl oder Abfrage, die andere als einfache Strukturen Zeichenfolgen (z. B. XML-Vorlageabfragen) definieren, den Befehl mit der [' CommandStream '](../../../ado/reference/ado-api/commandstream-property-ado.md) Eigenschaft.  
  
-   Der Befehlsdialekt verwendet optional angeben der **CommandText** oder **' CommandStream '** mit der [Dialekt](../../../ado/reference/ado-api/dialect-property.md) Eigenschaft.  
  
-   Definieren Sie parametrisierte Abfragen oder gespeicherten Prozedur Argumente mit [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekte und die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung.  
  
-   Gibt an, ob Parameternamen übergeben werden sollen, an den Anbieter bei der [NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) Eigenschaft.  
  
-   Ausführen ein Befehls und zum Zurückgeben einer **Recordset** Objekt bei Bedarf mit der [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) Methode.  
  
-   Geben Sie den Typ des Befehls mit der die [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) Eigenschaft vor der Ausführung, um die Leistung optimieren.  
  
-   Steuern, ob der Anbieter eine vorbereitete (oder kompilierte) Version des Befehls vor der Ausführung mit speichert die [Prepared](../../../ado/reference/ado-api/prepared-property-ado.md) Eigenschaft.  
  
-   Legen Sie die Anzahl der Sekunden, die ein Anbieter wartet, bis ein Befehl zum Ausführen von mit der ["CommandTimeout"](../../../ado/reference/ado-api/commandtimeout-property-ado.md) Eigenschaft.  
  
-   Ordnen Sie eine offene Verbindung mit einem **Befehl** Objekt durch Festlegen seiner [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) Eigenschaft.  
  
-   Legen Sie die [Namen](../../../ado/reference/ado-api/name-property-ado.md) Eigenschaft zum Identifizieren der **Befehl** Objekt als Methode für das zugeordnete [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt.  
  
-   Übergeben einer **Befehl** -Objekt an die [Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md) Eigenschaft eine **Recordset** zum Abrufen von Daten.  
  
-   Zugreifen auf Anbieter-spezifischen Attribute mit den [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
> [!NOTE]
>  Zum Ausführen einer Abfrage ohne eine **Befehl** Objekt, und übergeben Sie eine Abfragezeichenfolge enthält, die die [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) -Methode der ein **Verbindung** Objekt oder die [Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md)Methode eine **Recordset** Objekt. Allerdings eine **Befehl** Objekt ist erforderlich, wenn den Befehlstext beibehalten und erneut ausführen oder Verwenden von Abfrageparametern werden sollen.  
  
 Zum Erstellen einer **Befehl** Objekt unabhängig von einem zuvor definierten **Verbindung** -Objekts seine **ActiveConnection** Eigenschaft, um eine gültige Verbindungszeichenfolge. ADO erstellt dennoch eine **Verbindung** -Objekt, aber es nicht das Objekt einer Objektvariablen zuweisen. Jedoch wenn Sie mehrere zuordnen **Befehl** Objekte mit derselben Verbindung, sollten Sie explizit erstellen und öffnen Sie eine **Verbindung** Objekt; dieser weist den **Verbindung** Objekt einer Objektvariablen. Stellen Sie sicher, dass die **Verbindung** Objekt wurde erfolgreich geöffnet, bevor Sie sie zum Zuweisen der **ActiveConnection** Eigenschaft der **Befehl** Objekt, weil Zuweisen einer geschlossen **Verbindung** Objekt verursacht einen Fehler. Wenn Sie nicht Festlegen der **ActiveConnection** Eigenschaft der **Befehl** Objekt auf diese Objektvariable ADO erstellt ein neues **Verbindung** Objekt für jede  **Befehl** Objekt, auch wenn Sie dieselbe Verbindungszeichenfolge verwenden.  
  
 Zum Ausführen einer **Befehl**, durch Aufrufen der [Namen](../../../ado/reference/ado-api/name-property-ado.md) Eigenschaft für das zugeordnete **Verbindung** Objekt. Die **Befehl** müssen die **ActiveConnection** -Eigenschaftensatz auf die **Verbindung** Objekt. Wenn die **Befehl** verfügt über Parameter, deren Werte als Argumente an die Methode übergeben.  
  
 Wenn zwei oder mehr **Befehl** Objekte ausgeführt werden, auf die gleiche Verbindung und entweder **Befehl** Objekt ist eine gespeicherte Prozedur mit Output-Parameter, ein Fehler auftritt. Jede auszuführende **Befehl** Objekt verwenden Sie separate Verbindungen oder trennen Sie alle anderen **Befehl** Objekte von der Verbindung.  
  
 Die **Parameter** Auflistung ist das Standardelement der **Befehl** Objekt. Daher sind der Code für die folgenden beiden Anweisungen äquivalent.  
  
```  
objCmd.Parameters.Item(0)  
objCmd(0)  
```  
  
-   Die **Befehl** Objekt ist nicht sicher für Skripting.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Befehls-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/command-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Parameters-Auflistung (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
