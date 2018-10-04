---
title: VDI-Spezifikation Backup - SQLServer unter Linux | Microsoft-Dokumentation
description: SQL Server Virtual Interface Sicherungsmediumspezifikation.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 0250ba2b-8cdd-450e-9109-bf74f70e1247
ms.openlocfilehash: f29a133ce422b5e6fd04bcd6a78bd036e1f447ee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806178"
---
# <a name="sql-server-on-linux-vdi-client-sdk-specification"></a>SQL Server unter Linux VDI-Client-SDK-Spezifikation

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieses Dokument behandelt die Schnittstellen, die von den SQL Server auf Linux virtual Device Interface (VDI)-Client-SDK bereitgestellt. Unabhängige Softwarehersteller (ISVs) können, dass der Virtual Backup Device Schnittstelle API (Application Programming) SQL Server in ihre Produkte integrieren können. Im Allgemeinen verhält sich VDI für Linux auf ähnliche Weise zu VDI unter Windows mit den folgenden Änderungen:

- Windows-Shared Memory wird POSIX freigegebenen Speicher.
- Windows-Semaphoren sind POSIX-Semaphoren.
- Windows-Typen wie HRESULT und DWORD-Entsprechungen für ganze Zahl geändert werden.
- Die COM-Schnittstellen werden entfernt und ersetzt, die mit einem Paar von C++-Klassen.
- SQL Server unter Linux unterstützt benannte Instanzen nicht, damit Verweise auf die Instanznamen entfernt wurden. 
- Die freigegebene Bibliothek ist in libsqlvdi.so /opt/mssql/lib/libsqlvdi.so installiert implementiert.

Dieses Dokument ist ein Nachtrag zu **vbackup.chm** mit Informationen zu den Windows-VDI-Spezifikation. Herunterladen der [Windows VDI-Spezifikation](http://www.microsoft.com/download/details.aspx?id=17282).

Überprüfen Sie auch die beispiellösung für VDI-Sicherung auf die [SQL Server Samples-GitHub-Repository](http://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sqlvdi-linux).

## <a name="user-permissions-setup"></a>Benutzereinrichtung-Berechtigungen

Unter Linux sind POSIX-primitive Besitz des Benutzers erstellen sie und ihre Standardgruppe. Für Objekte, die von SQL Server erstellt werden werden diese standardmäßig der Mssql-Benutzer und der Mssql-Gruppe gehören. Damit können die gemeinsame Datennutzung von SQL Server und die VDI-Clients, eine der beiden folgenden Methoden werden empfohlen:

1. Führen Sie den VDI-Client als dem Mssql-Benutzer
   
   Führen Sie den folgenden Befehl zum Wechseln zu Mssql-Benutzer:
   
   ```bash
   sudo su mssql
   ```

2. Der Mssql-Benutzer zu der Vdiuser Gruppe und die Vdiuser der Mssql-Gruppe hinzufügen.
   
   Führen Sie die folgenden Befehle ein:

   ```bash
   sudo useradd vdiuser
   sudo usermod -a -G mssql vdiuser
   sudo usermod -a -G vdiuser mssql
   ```

   Starten Sie den Server, um neue Gruppen für SQL Server und Vdiuser zu übernehmen.

## <a name="client-functions"></a>Clientfunktionen

Dieses Kapitel enthält eine Beschreibung der einzelnen Clientfunktionen. Die Beschreibungen enthalten die folgende Informationen an:

- Zweck der Funktion
- Funktionssyntax
- Parameterliste
- Rückgabewerte
- Hinweise

## <a name="clientvirtualdevicesetcreate"></a>ClientVirtualDeviceSet::Create

**Zweck** diese Funktion erstellt den virtuelle Gerät Satz.

**Syntax**
   ```
   int ClientVirtualDeviceSet::Create (
   char *   name,       // name for the set
   VDConfig   * cfg     // configuration for the set
   );
   ```

| Parameter | Argument | Erklärung
| ----- | ----- | ------ |
| | **name** | Dies identifiziert die virtuelle Gerät. Die Regeln für Namen von CreateFileMapping() verwendet, müssen ausgeführt werden. Jedem Zeichen außer dem umgekehrten Schrägstrich (\) kann verwendet werden. Dies ist eine Zeichenfolge. Die Zeichenfolge des Benutzers Produktwissen oder firmeninternem und Datenbanknamen vorangestellt wird empfohlen. |
| |**cfg** | Dies ist die Konfiguration für das virtuelle Gerät Satz. Weitere Informationen finden Sie weiter unten in diesem Dokument unter "Konfiguration".

| Rückgabewerte | Argument | Erklärung
| ----- | ----- | ------ |
| |**"NOERROR" ZURÜCKGEGEBEN** | Die Funktion wurde erfolgreich ausgeführt. |
| |**VD_E_NOTSUPPORTED** |Eine oder mehrere der Felder in der Konfiguration ist ungültig oder andernfalls nicht unterstützt. |
| |**VD_E_PROTOCOL** | Das virtuelle Gerät wurde bereits festgelegt ist vorhanden.

**"Hinweise"** erstellen-Methode nur einmal pro Backup- oder RESTORE-Vorgang aufgerufen werden soll. Nach dem Aufruf der Close-Methode, kann der Client die Schnittstelle, um ein anderes virtuelles Gerät erstellen wiederverwenden.

## <a name="clientvirtualdevicesetgetconfiguration"></a>ClientVirtualDeviceSet::GetConfiguration

**Zweck** diese Funktion wird verwendet, auf den Server so konfigurieren Sie den virtuelle Gerät Satz warten.
**Syntax**
   ```
   int ClientVirtualDeviceSet::GetConfiguration (
   time_t       timeout,    // in milliseconds
   VDConfig *       cfg // selected configuration
   );
   ```

| Parameter | Argument | Erklärung
| ----- | ----- | ------ |
| | **timeout** | Dies ist das Timeout in Millisekunden. Verwenden Sie UNBEGRENZT oder eine negative ganze Zahl, um Timeouts zu verhindern.
| | **cfg** | Nach erfolgreicher Ausführung enthält die Konfiguration, die vom Server ausgewählt. Weitere Informationen finden Sie weiter unten in diesem Dokument unter "Konfiguration".

| Rückgabewerte | Argument | Erklärung
| ----- | ----- | ------ |
| |**"NOERROR" ZURÜCKGEGEBEN** | Die Konfiguration wurde zurückgegeben.
| |**VD_E_ABORT** |SignalAbort wurde aufgerufen.
| |**VD_E_TIMEOUT** |Die Funktion ist ein Timeout aufgetreten.

**"Hinweise"** dieser Funktion in einem Alertable Zustand blockiert. Nach dem erfolgreichen Aufruf können die Geräte in der Menge des virtuellen Geräts geöffnet sein.


## <a name="clientvirtualdevicesetopendevice"></a>ClientVirtualDeviceSet::OpenDevice
**Zweck** dieser Funktion wird ein Gerät geöffnet, in der Menge des virtuellen Geräts.
**Syntax**
   ```
   int ClientVirtualDeviceSet::OpenDevice (
   char *           name,       // name for the set
   ClientVirtualDevice **       ppVirtualDevice // returns interface to device
   );
   ```

| Parameter | Argument | Erklärung
| ----- | ----- | ------ |
| | **name** |Dies identifiziert die virtuelle Gerät.
| | **ppVirtualDevice** |Wenn die Funktion erfolgreich ist, wird ein Zeiger auf das virtuelle Gerät zurückgegeben. Dieses Gerät wird für GetCommand-Aufruf und CompleteCommand verwendet.

| Rückgabewerte | Argument | Erklärung
| ----- | ----- | ------ |
| |**"NOERROR" ZURÜCKGEGEBEN** |Die Funktion wurde erfolgreich ausgeführt.
| |**VD_E_ABORT** | Abbruch wurde angefordert.
| |**VD_E_OPEN** |  Alle Geräte, die geöffnet sind.
| |**VD_E_PROTOCOL** |  Die Gruppe ist nicht im Zustand "Initialisieren" aus, oder dieses Gerät ist bereits geöffnet.
| |**VD_E_INVALID** |Der Gerätename ist ungültig. Es ist nicht mit den Namen, die bekannt, dass die Gruppe zu bilden.

**"Hinweise"** VD_E_OPEN kann zurückgegeben werden, ohne Problem. Der Client möglicherweise OpenDevice mithilfe einer Schleife aufrufen, bis dieser Code zurückgegeben wird.
Wenn mehr als ein Gerät so, z. B. konfiguriert ist *n* Geräte das virtuelle Gerät zurück *n* eindeutige Geräte-Schnittstellen.

Die `GetConfiguration` Funktion kann verwendet werden, warten, bis die Geräte geöffnet werden können.
Wenn diese Funktion nicht erfolgreich ist, wird ein null-Wert über die PpVirtualDevice zurückgegeben.
 
## <a name="clientvirtualdevicegetcommand"></a>ClientVirtualDevice::GetCommand

**Zweck** diese Funktion dient zum Abrufen des Nächstes Befehl in der Warteschlange auf einem Gerät. Wenn angefordert, wartet diese Funktion für den nächsten Befehl.

**Syntax**
   ```
   int ClientVirtualDevice::GetCommand (
   time_t       timeout,    // time-out in milliseconds
   VDC_Command**    ppCmd   // returns the next command
   );
   ```

| Parameter | Argument | Erklärung
| ----- | ----- | ------ |
| |**timeout** |Dies ist die Zeit, die Wartezeit in Millisekunden. Verwenden Sie UNENDLICHE, um unbegrenzt zu warten. Verwenden Sie 0 für einen Befehl abrufen. VD_E_TIMEOUT wird zurückgegeben, wenn kein Befehl derzeit verfügbar ist. Wenn das Timeout auftritt, entscheidet der Client die nächste Aktion.
| |**Timeout** |Dies ist die Zeit, die Wartezeit in Millisekunden. Verwenden Sie UNENDLICHE oder ein negativer Wert, um unbegrenzt zu warten. Verwenden Sie 0 für einen Befehl abrufen. VD_E_TIMEOUT wird zurückgegeben, wenn kein Befehl verfügbar ist, bevor das Timeout abläuft. Wenn das Timeout auftritt, entscheidet der Client die nächste Aktion.
| |**ppCmd** |Wenn ein Befehl wurde erfolgreich zurückgegeben wird, wird die Adresse eines Befehls zum Ausführen von der-Parameter zurückgegeben. Der zurückgegebene Arbeitsspeicher ist schreibgeschützt. Wenn der Befehl abgeschlossen ist, wird die this-Zeiger an die Routine CompleteCommand übergeben. Weitere Informationen zu jedem Befehl finden Sie unter "Befehle" weiter unten in diesem Dokument.
        
| Rückgabewerte | Argument | Erklärung
| ----- | ----- | ------ |
| |**"NOERROR" ZURÜCKGEGEBEN** |Ein Befehl wurde abgerufen.
| |**VD_E_CLOSE** |Das Gerät wurde vom Server geschlossen.
| |**VD_E_TIMEOUT** |Es wurde kein Befehl verfügbar, und vor dem abgelaufenen Timeoutintervall.
| |**VD_E_ABORT** |Dem Client oder dem Server wurde die SignalAbort verwendet zum Herunterfahren.

**"Hinweise"** beim VD_E_CLOSE zurückgegeben wird zurückgegeben, die SQL Server wurde geschlossen, dass das Gerät. Dies ist Teil der normal heruntergefahren wurde. Nachdem alle Geräte geschlossen wurden, ruft der Client ClientVirtualDeviceSet::Close, um den Satz virtuelles Gerät zu schließen.
Wenn diese Routine eines Befehls warten, blockiert werden muss, bleibt der Thread in einer Alertable-Bedingung.

## <a name="clientvirtualdevicecompletecommand"></a>ClientVirtualDevice::CompleteCommand

**Zweck** diese Funktion wird verwendet, um SQL Server zu informieren, die ein Befehl abgeschlossen ist. Informationen über den Abschluss des Befehls entsprechende zurückgegeben werden soll. Weitere Informationen finden Sie unter "Befehle" weiter unten in diesem Dokument.

**Syntax** 

   ```
   int ClientVirtualDevice::CompleteCommand (
   VDC_Command pCmd,        // the command
   int  completionCode,     // completion code
   unsigned long    bytesTransferred,   // bytes transferred
   int64_t  position        // current position
   );
   ```

| Parameter | Argument | Erklärung
| ----- | ----- | ------ |
| |**pCmd** |Dies ist die Adresse eines Befehls, der zuvor von ClientVirtualDevice::GetCommand zurückgegeben wird.
| |**completionCode** |Dies ist eine Statuscode, der den Abschlussstatus angibt. Dieser Parameter muss für alle Befehle zurückgegeben werden. Der Code zurückgegeben sollte für den Befehl ausgeführt wird. ERROR_SUCCESS wird in allen Fällen verwendet, um einer erfolgreich ausgeführten Befehl anzugeben. Die vollständige Liste der möglichen Fehlercodes, finden Sie in der Datei vdierror.h. Eine Liste der typischen Statuscodes für jeden Befehl wird im "Befehle" weiter unten in diesem Dokument.
| |**bytesTransferred** |Dies ist die Anzahl der erfolgreich übertragenen Bytes. Dies wird nur für die Datenübertragung zurückgegeben, Befehle lesen und schreiben.
| |**Position** |Dies ist eine Antwort auf den GetPosition-Befehl.
        
| Rückgabewerte | Argument | Erklärung
| ----- | ----- | ------ |
| |**"NOERROR" ZURÜCKGEGEBEN** |Die Vervollständigung wurde ordnungsgemäß angegeben.
| |**VD_E_INVALID** |pCmd war es sich nicht um einen aktiven Befehl.
| |**VD_E_ABORT** |Abbruch signalisiert wurde.
| |**VD_E_PROTOCOL** |Das Gerät ist nicht geöffnet werden.

**"Hinweise"** keine

## <a name="clientvirtualdevicesetsignalabort"></a>ClientVirtualDeviceSet::SignalAbort

**Zweck** diese Funktion wird verwendet, um zu signalisieren, dass eine nicht ordnungsgemäße Beendigung erfolgen soll.

**Syntax** 

   ```
   int ClientVirtualDeviceSet::SignalAbort ();
   ```

| Parameter | Argument | Erklärung
| ----- | ----- | ------ |
| |None | Nicht verfügbar
        
| Rückgabewerte | Argument | Erklärung
| ----- | ----- | ------ |
| |**"NOERROR" ZURÜCKGEGEBEN**|Die Abort-Benachrichtigung wurde erfolgreich bereitgestellt.

**"Hinweise"** zu jedem Zeitpunkt des Clients können die Backup- oder RESTORE-Vorgang abgebrochen. Diese Routine wird signalisiert, dass alle Vorgänge beenden soll. Der Status des virtuellen Geräts Satzes gibt einen Status fehlerbedingt beendet. Keine weiteren Befehle, die für alle Geräte zurückgegeben werden. Alle nicht abgeschlossenen Befehle werden automatisch ausgefüllt, ERROR_OPERATION_ABORTED als Ergebniscode zurückgegeben wird. Nachdem sie alle ausstehenden Verwendung von Puffern, die an den Client bereitgestellten sicher beendet wurde, sollte der Client ClientVirtualDeviceSet::Close aufrufen. Weitere Informationen finden Sie unter "Nicht ordnungsgemäße Beendigung" weiter oben in diesem Dokument.

## <a name="clientvirtualdevicesetclose"></a>ClientVirtualDeviceSet::Close

**Zweck** diese Funktion schließt den virtuelle Gerät Satz ClientVirtualDeviceSet::Create erstellt. Dies führt in der Version aller Ressourcen, die mit dem virtuellen Gerät verknüpft ist.

**Syntax** 

   ```
   int ClientVirtualDeviceSet::Close ();
   ```

| Parameter | Argument | Erklärung
| ----- | ----- | ------ |
| |None |Nicht verfügbar
        
| Rückgabewerte | Argument | Erklärung
| ----- | ----- | ------ |
| |**"NOERROR" ZURÜCKGEGEBEN** |Dies wird zurückgegeben, wenn die virtuellen Gerätegruppe erfolgreich geschlossen wurde.
| |**VD_E_PROTOCOL** |Da der virtuelle Gerät Satz nicht offen war, wurde keine Aktion ausgeführt.
| |**VD_E_OPEN** |Geräte waren noch geöffnet.

**"Hinweise"** des Aufrufs geschlossen ist, eine Client-Deklaration, dass alle durch die Menge des virtuellen Geräts verwendete Ressourcen freigegeben werden sollen. Der Client muss sicherstellen, dass alle Aktivitäten im Zusammenhang mit Datenpuffer und virtuelle Geräte vor dem Aufrufen von Schließen beendet wurde. Durch Schließen werden alle virtuellen Geräts-Schnittstellen, die zurückgegeben werden, indem Sie OpenDevice ungültig.
Der Client ist zulässig, einen Aufruf zum Erstellen für das virtuelle Gerät festgelegte Schnittstelle ausgeben, nachdem der Close-Aufruf zurückgegeben wurde. Solch ein Aufruf wird ein neues virtuelles Gerät, legen Sie für ein nachfolgender BACKUP oder RESTORE-Vorgang erstellen.
Wenn der Close aufgerufen wird, wenn ein oder mehrere virtuelle Geräte noch geöffnet sind, wird die VD_E_OPEN zurückgegeben. In diesem Fall wird SignalAbort intern ausgelöst, um eine ordnungsgemäße Herunterfahren nach Möglichkeit sicherzustellen. VDI-Ressourcen werden freigegeben. Der Client sollte eine Angabe VD_E_CLOSE zurückgegeben auf jedem Gerät vor dem Aufrufen von ClientVirtualDeviceSet::Close warten. Wenn der Client weiß, dass festgelegtem virtuelles Gerät ist bereits in einem Zustand fehlerbedingt beendet, und es erwarten nicht, dass eine Angabe VD_E_CLOSE zurückgegeben von GetCommand-Aufruf, und rufen möglicherweise ClientVirtualDeviceSet::Close, sobald die Aktivität auf die freigegebenen Puffer beendet wird.
Weitere Informationen finden Sie unter "Nicht ordnungsgemäße Beendigung" weiter oben in diesem Dokument.

## <a name="clientvirtualdevicesetopeninsecondary"></a>ClientVirtualDeviceSet::OpenInSecondary

**Zweck** dieser Funktion wird geöffnet, das virtuelle Gerät in einem sekundären Client festgelegt. Die primäre Client muss erstellen und GetConfiguration haben bereits verwendet, um den Satz virtuelles Gerät einzurichten.

**Syntax** 
   
   ```
   int ClientVirtualDeviceSet::OpenInSecondary (
   char *   setName         // name of the set
   );
   ```

| Parameter | Argument | Erklärung
| ----- | ----- | ------ |
| |**setName** |Damit wird den Satz identifiziert. Dieser Name wird Groß-/Kleinschreibung berücksichtigt und muss dem Namen, die vom primären Client verwendet wird, wenn sie ClientVirtualDeviceSet::Create aufgerufen entsprechen.

| Rückgabewerte | Argument | Erklärung
| ----- | ----- | ------ |
| |**"NOERROR" ZURÜCKGEGEBEN** |Die Funktion wurde erfolgreich ausgeführt.
| |**VD_E_PROTOCOL** |Der virtuelle Gerät Satz nicht erstellt wurde, ist bereits auf diesem Client oder das virtuelle Gerät geöffnet Satz ist nicht bereit für die offene Anforderungen von sekundären Clients akzeptiert.
| |**VD_E_ABORT** |Der Vorgang abgebrochen wird.

**"Hinweise"** der primäre Client ist dafür verantwortlich, normale und ungewöhnliche Beenden der sekundären Clients erkennen, wenn Sie ein Prozessmodell mit mehreren verwenden zu können,.

## <a name="clientvirtualdevicesetgetbufferhandle"></a>ClientVirtualDeviceSet::GetBufferHandle

**Zweck** einige Anwendungen erfordern möglicherweise mehr als einen Prozess für von ClientVirtualDevice::GetCommand zurückgegebene Puffer ausgeführt werden. In solchen Fällen kann der Prozess, der den Befehl empfängt GetBufferHandle verwenden, um eine unabhängige Prozesshandle zu erhalten, die den Puffer angibt. Dieses Handle kann dann an einen anderen Prozess übermittelt werden, die das gleiche virtuelle Gerät festlegen öffnen verfügt auch über. Dieser Prozess würden ClientVirtualDeviceSet::MapBufferHandle klicken Sie dann verwenden, um die Adresse des Puffers abzurufen. Die Adresse wird wahrscheinlich eine andere Adresse als seine Partner sein, da jeder Prozess Puffer an verschiedenen Adressen zugeordnet werden kann.

**Syntax** 

   ```
   int ClientVirtualDeviceSet::GetBufferHandle (
   uint8_t*     pBuffer,        // in: buffer address
   unsigned int*        pBufferHandle   // out: buffer handle
   );
   ```

| Parameter | Argument | Erklärung
| ----- | ----- | ------ |
| |**pBuffer** |Dies ist die Adresse eines Puffers, der über eine Lese- oder Schreibvorgang abgerufen.
| |**BufferHandle** |Ein eindeutiger Bezeichner für den Puffer wird zurückgegeben.

| Rückgabewerte | Argument | Erklärung
| ----- | ----- | ------ |
| |**"NOERROR" ZURÜCKGEGEBEN** |Die Funktion wurde erfolgreich ausgeführt.
| |**VD_E_PROTOCOL** |Der virtuelle festgelegte ist gerade nicht geöffnet.
| |**VD_E_INVALID** |Die pBuffer ist keine gültige Adresse.
Hinweise, dass der Prozess, der die GetBufferHandle-Funktion aufruft, ist verantwortlich für das ClientVirtualDevice::CompleteCommand aufrufen, wenn die Datenübertragung abgeschlossen ist.

## <a name="clientvirtualdevicesetmapbufferhandle"></a>ClientVirtualDeviceSet::MapBufferHandle

**Zweck** diese Funktion wird verwendet, um eine Adresse gültigen Puffer aus einem Pufferhandle abgerufen, die aus einem anderen Prozess zu erhalten. 

**Syntax** 

   ```
   int ClientVirtualDeviceSet::MapBufferHandle (
   i        nt  dwBuffer,   // in: buffer handle
   uint8_t**    ppBuffer        // out: buffer address
   );
   ```

| Parameter | Argument | Erklärung
| ----- | ----- | ------ |
| |**dwBuffer** |Dies ist das Handle von ClientVirtualDeviceSet::GetBufferHandle zurückgegeben.
| |**ppBuffer** |Dies ist die Adresse des Puffers, der im aktuellen Prozess gültig ist.

| Rückgabewerte | Argument | Erklärung
| ----- | ----- | ------ |
| |**"NOERROR" ZURÜCKGEGEBEN** |Die Funktion wurde erfolgreich ausgeführt.
| |**VD_E_PROTOCOL** |Der virtuelle festgelegte ist gerade nicht geöffnet.
| |**VD_E_INVALID** |Die PpBuffer ist ein ungültiges Handle.

**"Hinweise"** Vorsicht Handles richtig zu kommunizieren. Handles sind lokal auf ein einzelnes virtuelles Gerät. Die Partner-Prozesse, die ein Handle freigeben müssen sicherzustellen, dass Handles, nur innerhalb des Bereichs des virtuellen Geräts verwendet werden aus dem Puffer ursprünglich abgerufen wurde festgelegt.


