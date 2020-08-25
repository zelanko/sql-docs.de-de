---
description: Connection-Objekt (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ce6a6e3c2e665c57b9a82d968dac3cf3c74a731
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775959"
---
# <a name="connection-object-ado"></a>Connection-Objekt (ADO)
Stellt eine offene Verbindung mit einer Datenquelle dar.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **Verbindungs** Objekt stellt eine eindeutige Sitzung mit einer Datenquelle dar. In einem Client/Server-Datenbanksystem ist es möglicherweise Äquivalent zu einer tatsächlichen Netzwerkverbindung mit dem Server. Abhängig von der vom Anbieter unterstützten Funktionalität sind einige Sammlungen, Methoden oder Eigenschaften eines **Verbindungs** Objekts möglicherweise nicht verfügbar.  
  
 Mit den Auflistungen, Methoden und Eigenschaften eines **Verbindungs** Objekts können Sie folgende Aufgaben ausführen:  
  
-   Konfigurieren Sie die Verbindung, bevor Sie Sie mit den Eigenschaften [ConnectionString](./connectionstring-property-ado.md), [ConnectionTimeout](./connectiontimeout-property-ado.md)und [Mode](./mode-property-ado.md) öffnen. **ConnectionString** ist die Standard Eigenschaft des **Connection** -Objekts.  
  
-   Legen Sie die [CursorLocation](./cursorlocation-property-ado.md) -Eigenschaft auf Client fest, um den [Microsoft-Cursor Dienst für OLE DB](../../guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)aufzurufen, der Batch Aktualisierungen unterstützt.  
  
-   Legen Sie die Standarddatenbank für die Verbindung mit der [DefaultDatabase](./defaultdatabase-property.md) -Eigenschaft fest.  
  
-   Legen Sie den Isolations Grad für die für die Verbindung geöffneten Transaktionen mit der [IsolationLevel](./isolationlevel-property.md) -Eigenschaft fest.  
  
-   Geben Sie einen OLE DB-Anbieter mit der [Provider](./provider-property-ado.md) -Eigenschaft an.  
  
-   Richten Sie die physische Verbindung mit der Datenquelle mit den [Open](./open-method-ado-connection.md) -und [Close](./close-method-ado.md) -Methoden ein, und unterbrechen Sie Sie später.  
  
-   Führen Sie einen Befehl für die Verbindung mit der [Execute](./execute-method-ado-connection.md) -Methode aus, und konfigurieren Sie die Ausführung mit der [CommandTimeout](./commandtimeout-property-ado.md) -Eigenschaft.  
  
    > [!NOTE]
    >  Wenn Sie eine Abfrage ohne ein Befehls Objekt ausführen möchten, übergeben Sie eine Abfrage Zeichenfolge an die **Execute** -Methode eines **Verbindungs** Objekts. Ein [Command](./command-object-ado.md) -Objekt ist jedoch erforderlich, wenn Sie den Befehls Text persistent speichern und erneut ausführen oder Abfrage Parameter verwenden möchten.  
  
-   Verwalten Sie Transaktionen auf der geöffneten Verbindung, einschließlich der durch den Anbieter unterstützten Transaktionen, mit den Methoden [BeginTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md), [CommitTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md)und [RollbackTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md) und der Eigenschaft [Attribute](./attributes-property-ado.md) .  
  
-   Untersuchen Sie die von der Datenquelle zurückgegebenen Fehler mit der [Fehler](./errors-collection-ado.md) Auflistung.  
  
-   Lesen Sie die Version aus der ADO-Implementierung, die mit der [Version](./version-property-ado.md) -Eigenschaft verwendet wird.  
  
-   Abrufen von Schema Informationen über Ihre Datenbank mit der [OpenSchema](./openschema-method.md) -Methode.  
  
 **Verbindungs** Objekte können unabhängig von anderen zuvor definierten Objekten erstellt werden.  
  
 Sie können benannte Befehle oder gespeicherte Prozeduren so ausführen, als wären Sie Native Methoden für ein **Verbindungs** Objekt, wie im nächsten Abschnitt gezeigt. Wenn ein benannter Befehl denselben Namen wie eine gespeicherte Prozedur hat, rufen Sie den "systemeigenen Methodenaufruf" für ein **Verbindungs** Objekt auf, und führen Sie immer den benannten Befehl anstelle der gespeicherten Prozedur aus.  
  
> [!NOTE]
>  Verwenden Sie diese Funktion nicht (Aufrufen eines benannten Befehls oder einer gespeicherten Prozedur, als ob es sich um eine systemeigene Methode des **Connection** -Objekts handelt) in einer Microsoft® .NET Framework-Anwendung, da die zugrunde liegende Implementierung des Features mit der Art und Weise in Konflikt steht, in der die .NET Framework mit com interagiert.  
  
## <a name="execute-a-command-as-a-native-method-of-a-connection-object"></a>Ausführen eines Befehls als native Methode eines Verbindungs Objekts  
 Um einen Befehl auszuführen, benennen Sie den Befehl mithilfe der Eigenschaft **Befehls** Objekt [Name](./name-property-ado.md) . Legen Sie die **ActiveConnection** -Eigenschaft des **Befehls** Objekts auf die Verbindung fest. Geben Sie dann eine-Anweisung aus, bei der der Befehls Name verwendet wird, als ob es sich um eine Methode für das **Verbindungs** Objekt, gefolgt von allen Parametern und ein **Recordset** -Objekt handelt, wenn Zeilen zurückgegeben werden. Legen Sie die **Recordseteigenschaften** so fest, dass das resultierende **Recordset**angepasst wird. Zum Beispiel:  
  
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
  
## <a name="execute-a-stored-procedure-as-a-native-method-of-a-connection-object"></a>Ausführen einer gespeicherten Prozedur als native Methode eines Verbindungs Objekts  
 Um eine gespeicherte Prozedur auszuführen, geben Sie eine-Anweisung aus, bei der der Name der gespeicherten Prozedur verwendet wird, als ob es sich um eine Methode für das **Verbindungs** Objekt handelt, gefolgt von Parametern. ADO stellt eine "beste Vermutung" der Parametertypen dar. Zum Beispiel:  
  
```  
Dim cnn As New ADODB.Connection  
...  
'Your stored procedure name and any parameters.  
cnn. "parameter"  
```  
  
 Das **Verbindungs** Objekt ist für die Skripterstellung sicher.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Verbindungs Objekteigenschaften,-Methoden und-Ereignisse](./connection-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Command-Objekt (ADO)](./command-object-ado.md)   
 [Fehlersammlung (ADO)](./errors-collection-ado.md)   
 [Properties-Auflistung (ADO)](./properties-collection-ado.md)   
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)   
 [Anhang A: Anbieter](../../guide/appendixes/appendix-a-providers.md)