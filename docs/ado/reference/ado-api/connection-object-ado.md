---
title: Connection-Objekt (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection
helpviewer_keywords:
- Connection object [ADO]
ms.assetid: ef6b1824-5b12-43db-89d7-8f3d13896d4d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a3b13402f20c149c438aa5a2c678afb068fb0f3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140228"
---
# <a name="connection-object-ado"></a>Connection-Objekt (ADO)
Stellt eine offene Verbindung mit einer Datenquelle dar.  
  
## <a name="remarks"></a>Hinweise  
 Ein **Verbindung** -Objekt stellt eine eindeutige Sitzung mit einer Datenquelle dar. In einem System für den Client/Server-Datenbank können sie eine tatsächliche Netzwerk-Verbindung mit dem Server entsprechen. Abhängig von den Funktionen, die von der Anbieter, einige Auflistungen, Methoden oder Eigenschaften unterstützt eine **Verbindung** Objekt möglicherweise nicht zur Verfügung.  
  
 Mit den Auflistungen, Methoden und Eigenschaften einer **Verbindung** -Objekts können Sie folgende Möglichkeiten:  
  
-   Konfigurieren Sie die Verbindung vor dem Öffnen mit der ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md), [ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md), und [Modus](../../../ado/reference/ado-api/mode-property-ado.md) Eigenschaften. **"ConnectionString"** ist die Standardeigenschaft der **Verbindung** Objekt.  
  
-   Festlegen der [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf den Client zum Aufrufen der [Microsoft Cursor Service für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md), welche Aktualisierungen in Batches unterstützt.  
  
-   Legen Sie die Standarddatenbank für die Verbindung mit der [DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md) Eigenschaft.  
  
-   Der Grad an Isolierung für die Transaktionen, auf die Verbindung mit dem geöffnet Satz der [IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md) Eigenschaft.  
  
-   Geben Sie einen OLE DB-Anbieter mit der [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft.  
  
-   Einrichten und später zu unterbrechen, die physische Verbindung mit der Datenquelle mit dem [öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) und [schließen](../../../ado/reference/ado-api/close-method-ado.md) Methoden.  
  
-   Ausführen eines Befehls für die Verbindung mit der [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) Methode und konfigurieren Sie die Ausführung mit der ["CommandTimeout"](../../../ado/reference/ado-api/commandtimeout-property-ado.md) Eigenschaft.  
  
    > [!NOTE]
    >  Zum Ausführen einer Abfrage, ohne ein Command-Objekt, übergeben Sie eine Abfragezeichenfolge enthält, die die **Execute** Methode eine **Verbindung** Objekt. Allerdings eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt ist erforderlich, wenn den Befehlstext beibehalten und erneut ausführen oder Verwenden von Abfrageparametern werden sollen.  
  
-   Verwalten von Transaktionen zum Öffnen einer Verbindung, einschließlich geschachtelter Transaktionen an, wenn der Anbieter unterstützt werden, mit der [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md), [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md), und [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) Methoden und die [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) Eigenschaft.  
  
-   Untersuchen Sie Fehler, die zurückgegeben werden, aus der Datenquelle mit dem [Fehler](../../../ado/reference/ado-api/errors-collection-ado.md) Auflistung.  
  
-   Lesen die Version von der ADO-Implementierung verwendet, mit der [Version](../../../ado/reference/ado-api/version-property-ado.md) Eigenschaft.  
  
-   Abrufen von Schemainformationen über die Datenbank mit der [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) Methode.  
  
 Sie können erstellen **Verbindung** Objekte unabhängig von der zuvor definierten andere Objekte.  
  
 Sie können benannte Befehle oder gespeicherte Prozeduren ausführen, als wären sie systemeigene Methoden auf einem **Verbindung** Objekt, wie im nächsten Abschnitt gezeigt. Wenn Sie ein benannter Befehl, den gleichen Namen wie die, die einer gespeicherten Prozedur verfügt, rufen Sie "systemeigene Aufruf der Methode" auf einem **Verbindung** Objekt immer den genannte Befehl anstelle der gespeicherten Prozedur ausgeführt.  
  
> [!NOTE]
>  Diese Funktion nicht verwenden (einen benannten Befehl oder gespeicherte Prozedur aufrufen, als wäre es eine systemeigene Methode für die **Verbindung** Objekt) in einer Microsoft® .NET Framework-Anwendung, da die zugrunde liegende Implementierung der Funktion verursacht einen Konflikt mit der Funktionsweise interagiert der .NET Framework mit COM  
  
## <a name="execute-a-command-as-a-native-method-of-a-connection-object"></a>Ausführen eines Befehls als systemeigene Methode eines Verbindungsobjekts  
 Benennen Sie zum Ausführen eines Befehls dem Befehl mit der **Befehl** Objekt [Namen](../../../ado/reference/ado-api/name-property-ado.md) Eigenschaft. Legen Sie die **ActiveConnection** Eigenschaft der **Befehl** Objekt, das die Verbindung. Geben Sie dann eine Anweisung, in dem der Befehlsname verwendet wird, als wäre es eine Methode auf, die **Verbindung** Objekts, gefolgt von alle Parameter, und ein **Recordset** Objekt, wenn Zeilen zurückgegeben werden. Legen Sie die **Recordset** Eigenschaften zum Anpassen der resultierenden **Recordset**. Zum Beispiel:  
  
```  
Dim cnn As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
...  
cnn.Open "..."  
cmd.Name = "yourCommandName"  
cmd.ActiveConnection = cnn  
...  
'Your command name, any parameters, and an optional Recordset.  
cnn. "parameter", rst  
```  
  
## <a name="execute-a-stored-procedure-as-a-native-method-of-a-connection-object"></a>Ausführen einer gespeicherten Prozedur als systemeigene Methode eines Verbindungsobjekts  
 Um eine gespeicherte Prozedur auszuführen, geben Sie eine Anweisung, die, in dem Namen der gespeicherten Prozedur verwendet wird, als wäre es eine Methode für, die **Verbindung** Objekts, gefolgt von beliebigen Parametern. ADO wird auf "erraten" von Parametertypen stellen. Zum Beispiel:  
  
```  
Dim cnn As New ADODB.Connection  
...  
'Your stored procedure name and any parameters.  
cnn. "parameter"  
```  
  
 Die **Verbindung** Objekt für die Skripterstellung sicher ist.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Verbindung Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Errors-Auflistung (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset Object (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md)
